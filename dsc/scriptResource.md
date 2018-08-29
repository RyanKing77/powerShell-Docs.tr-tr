---
ms.date: 08/24/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Script kaynağı
ms.openlocfilehash: ef84239820a44aab2a028f7f0fe17653a851b72e
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2018
ms.locfileid: "43133902"
---
# <a name="dsc-script-resource"></a>DSC Script kaynağı

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.x

**Betik** kaynak olarak Windows PowerShell Desired State Configuration (DSC), Windows PowerShell komut dosyası blokları hedef düğümleri üzerinde çalışmak için bir mekanizma sağlar. **Betik** kaynak kullanan `GetScript`, `SetScript`, ve `TestScript` tanımladığınız karşılık gelen DSC gerçekleştirmek için komut dosyası blokları içeren özelliğe işlem durumu.

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

> [!NOTE]
> `GetScript`, `TestScript`, Ve `SetScript` blokları, dize olarak depolanır.

## <a name="properties"></a>Özellikler

|Özellik|Açıklama|
|--------|-----------|
|GetScript|Düğüm geçerli durumunu döndüren bir betik bloğu.|
|SetScript|DSC düğümü istenen durumda olmadığında uyumluluğu zorlamak için kullanan bir betik bloğu.|
|TestScript|Düğüm istenen durumda olup olmadığını belirten bir betik bloğu.|
|Kimlik bilgisi| Kimlik bilgileri gerekiyorsa bu betiği çalıştırmak için kullanılacak kimlik bilgilerini belirtir.|
|DependsOn| Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>GetScript

DSC çıktısı kullanmayan `GetScript`. [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet'ini çalıştırır `GetScript` düğümün geçerli durumu alınamadı. Dönüş değeri, gelen gerekli değildir. `GetScript`. Dönüş değeri belirtirseniz, olması gereken bir `hashtable` içeren bir **sonucu** anahtar değeri olan bir `String`.

### <a name="testscript"></a>TestScript

`TestScript` Belirlemek için DSC tarafından yürütülen `SetScript` çalıştırılmalıdır. Varsa `TestScript` döndürür `$false`, DSC yürütür `SetScript` düğümü istenen duruma geri alma. Döndürmesi gereken bir `boolean` değeri. Sonucu `$true` düğümü uyumlu olduğunu gösterir ve `SetScript` çalıştırılmadı.

[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet'ini çalıştırır `TestScript` düğümleri uyumluluğu alınacak **betik** kaynakları. Ancak, bu durumda, `SetScript` , ne olursa olsun çalıştırmaz `TestScript` block döndürür.

> [!NOTE]
> Tüm çıktı, `TestScript` dönüş değeri bir parçasıdır. PowerShell anlamına unsuppressed çıkış olarak sıfır olmayan, yorumlar, `TestScript` döndüreceği `$true` bakılmaksızın, düğümün durumu.
> Bu beklenmeyen sonuç, hatalı pozitif sonuç verir ve sorun giderme sırasında zorluk neden olur.

### <a name="setscript"></a>SetScript

`SetScript` Enfore istenen durum düğüme değiştirir. Bu DSC tarafından çağrılır `TestScript` betik bloğu döndürür `$false`. `SetScript` Dönüş değeri olması gerekir.

## <a name="examples"></a>Örnekler

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Örnek 1: bir betik kaynak kullanarak örnek metin yazma

Bu örnekte varlığını test `C:\TempFolder\TestFile.txt` her düğümde. Yoksa, onu kullanarak oluşturur `SetScript`. `GetScript` İçeriğini dosya ve dönüş değeri kullanılmaz döndürür.

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Örnek 2: sürüm bilgilerini kullanarak bir komut dosyası kaynak karşılaştırın

Bu örnek alır *uyumlu* geliştirme bilgisayarında bir metin dosyasından sürüm bilgilerini ve depolar `$version` değişkeni. DSC düğümü MOF dosyası oluşturulurken değiştirir `$using:version` her komut dosyası değişkenleri block değeriyle `$version` değişkeni. Yürütme sırasında *uyumlu* sürümü bir metin dosyasındaki her bir düğümde depolanan ve karşılaştırma ve sonraki yürütmeleri üzerinde güncelleştirildi.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

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
}
```