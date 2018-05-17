---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC komut dosyası kaynağı
ms.openlocfilehash: 1163d454972d8ee519d1c55b77bb85979faf3536
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-script-resource"></a>DSC komut dosyası kaynağı


> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

**Betik** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), Windows PowerShell komut dosyası blokları hedef düğümlerinde çalıştırmak için bir mekanizma sağlar. `Script` Kaynak `GetScript`, `SetScript`, ve `TestScript` özellikleri. Bu özelliklerin her hedef düğümde çalışacak komut dosyası blokları ayarlamanız gerekir.

`GetScript` Betik bloğu geçerli düğüm durumunu temsil eden bir hashtable döndürmelidir. Hashtable yalnızca bir anahtar içermelidir `Result` ve değer türü olmalıdır `String`. Herhangi bir şeyi geri dönmek için gerekli değildir. DSC çıkış bu betik bloğunun herhangi bir şey yapmaz.

`TestScript` Betik bloğu geçerli düğüm değiştirilmesi gerekip gerekmediğini belirlemek. Döndürme zorunluluğu `$true` düğümü güncel ise. Döndürme zorunluluğu `$false` düğümün yapılandırma güncel değil ve tarafından güncelleştirilmesi `SetScript` betik bloğu. `TestScript` Betik bloğu DSC tarafından çağrılır.

`SetScript` Betik bloğu düğüm değiştirmek. Buna göre DSC denir `TestScript` engelleme return `$false`.

Yapılandırma komut dosyanıza değişkenlerinden kullanmanız gerekip gerekmediğini `GetScript`, `TestScript`, veya `SetScript` komut dosyası blokları, kullanın `$using:` kapsam (bir örnek için aşağıya bakın).


## <a name="syntax"></a>Sözdizimi

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| GetScript| Çağırdığınızda, çalıştırılan Windows PowerShell komut dosyası bloğunda sağlar [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet'i. Bu bloğu bir hashtable döndürmesi gerekir. Hashtable yalnızca bir anahtar içermelidir **sonuç** ve değer türü olmalıdır **dize**.|
| SetScript| Windows PowerShell komut dosyası bloğunda sağlar. Ne zaman çağırmayı [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet'ini **TestScript** bloğu ilk çalışır. Varsa **TestScript** engelleme döndürür **$false**, **SetScript** bloğu çalıştırır. Varsa **TestScript** engelleme döndürür **$true**, **SetScript** blok çalışmaz.|
| TestScript| Windows PowerShell komut dosyası bloğunda sağlar. Ne zaman çağırmayı [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet'i, bu bloğu çalıştırır. Döndürürse **$false**, SetScript blok çalışır. Döndürürse **$true**, çalıştırılacak blok olacak SetScript. **TestScript** bloğu ayrıca çalışır çağırdığınızda [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet'i. Ancak, bu durumda, **SetScript** bloğu değil çalıştırmak, hangi TestScript değerin olsun engelle döndürür. **TestScript** gerçek yapılandırması geçerli istenen durum yapılandırması ve False eşleşirse, eşleşmiyorsa, blok True döndürmesi gerekir. (Geçerli istenen durum yapılandırması, DSC kullanarak düğümde kamulaştırılmış son yapılandırmadır.)|
| kimlik bilgisi| Bu komut dosyasını çalıştırmak için kimlik bilgileri gerekli olduğunda kullanılacak kimlik bilgilerini gösterir.|
| dependsOn| Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise **ResourceName** ve türünü **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.

## <a name="example-1"></a>Örnek 1
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript =
        {
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
    }
}
```

## <a name="example-2"></a>Örnek 2
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = {
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }
        TestScript = {
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = {
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

Bu kaynak yapılandırma sürümü bir metin dosyasına yazma. Bu sürüm, istemci bilgisayarda kullanılabilir, ancak her biri için geçirilecek sahiptir herhangi bir düğüme değil `Script` kaynağın komut dosyası blokları PowerShell'ın ile `using` kapsam. Ne zaman oluşturuluyor düğümün MOF dosyası değeri `$version` değişkeni istemci bilgisayardaki bir metin dosyasından okunur. DSC değiştirir `$using:version` her komut dosyası değişkenleri engelleme değeriyle `$version` değişkeni.