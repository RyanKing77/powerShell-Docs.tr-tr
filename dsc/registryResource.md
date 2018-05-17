---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kayıt kaynağı
ms.openlocfilehash: 8819b3704fa1a61d2be5ce11c974542f48177e09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-registry-resource"></a>DSC kayıt kaynağı

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

**Kayıt defteri** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), kayıt defteri anahtarları ve değerleri bir hedef düğümdeki yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Özellikler
|  Özellik  |  Açıklama   |
|---|---|
| üzerine gelin| Belirli bir durumu sağlamak istediğiniz kayıt defteri anahtarının yolunu gösterir. Bu yol hive içermelidir.|
| Değer adı| Kayıt defteri değerinin adını belirtir. Eklemek veya bir kayıt defteri anahtarı kaldırmak için ValueType veya ValueData belirtmeden bu özellik olarak boş bir dize belirtin. Değiştirmek veya bir kayıt defteri anahtarının varsayılan değeri kaldırmak için ValueType veya ValueData de belirtildiğinde bu özellik olarak boş bir dize belirtin.|
| Emin olun| Anahtar ve değer var olup olmadığını gösterir. "Var" Bu özelliği ayarlayın emin olmak için. Mevcut olduğundan emin olmak için "Yok" özelliğini ayarlayın. "Var" varsayılan değerdir.|
| Force| Belirtilen kayıt defteri anahtarı varsa, __zorla__ yeni değerle üzerine yazar. Alt anahtarlar içeren bir kayıt defteri anahtarının silinmesi, bu olması gerekir __$true__|
| Onaltılık| Onaltılık biçimde belirtilecektir veri gösterir. Belirtilmişse, onaltılık biçimde DWORD/QWORD değer verisi sunulur. Diğer türleri için geçerli değil. Varsayılan değer __$false__.|
| dependsOn| Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Kayıt defteri değeri verileri.|
| ValueType| Değerin türünü belirtir. Desteklenen türler şunlardır:
<ul><li>Dize (REG_SZ)</li>


<li>İkili (ikili REG)</li>


<li>DWORD 32-bit (REG_DWORD)</li>


<li>QWORD 64-bit (REG_QWORD)</li>


<li>Çoklu dize (REG_MULTI_SZ)</li>


<li>Genişletilebilir dize (REG_EXPAND_SZ)</li></ul>

## <a name="example"></a>Örnek
Bu örnekte "ExampleKey" adlı bir anahtar mevcut olmasını sağlar **HKEY\_yerel\_makine** hive.
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

>**Not:** bir kayıt defteri ayarını değiştirerek **HKEY\_geçerli\_kullanıcı** hive gerektirir yapılandırma sistemi olarak değil, kullanıcı kimlik bilgileriyle çalışır.
>Kullanabileceğiniz **PsDscRunAsCredential** özelliği yapılandırma için kullanıcı kimlik bilgilerini belirtin. Bir örnek için bkz: [çalıştıran DSC kullanıcı kimlik bilgileri](runAsUser.md)
