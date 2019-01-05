---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Registry kaynağı
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048724"
---
# <a name="dsc-registry-resource"></a>DSC Registry kaynağı

_Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0_

**Kayıt defteri** kaynak olarak Windows PowerShell Desired State Configuration (DSC), kayıt defteri anahtarlarını ve değerlerini bir hedef düğümde yönetmek için bir mekanizma sağlar.

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

| Özellik | Açıklama |
| --- | --- |
| üzerine gelin| Belirli bir durumu sağlamak istediğiniz kayıt defteri anahtarının yolunu gösterir. Bu yol, hive içermelidir.|
| değer adı| Kayıt defteri değerinin adını belirtir. Bir kayıt defteri anahtarı ekleyip için ValueType veya ValueData belirtmeden bu özellik boş bir dize belirtin. Bir kayıt defteri anahtarının varsayılan değeri kaldırın ya da değiştirmek için ValueType veya ValueData belirtirken de bu özellik boş bir dize belirtin.|
| Emin olun| Anahtar ve değer olup olmadığını gösterir. "Var" Bu özelliği ayarlamak emin olmak için. Nesneler yok emin olmak için "Yok" özelliğini ayarlayın. "Var" varsayılan değerdir.|
| Force| Belirtilen kayıt defteri anahtarı varsa **zorla** yeni değeri ile değiştirir. Alt anahtarlar içeren bir kayıt defteri anahtarının silinmesi, bu olması gereken **$true** |
| Onaltılık| Onaltılık biçimde belirtilecektir verileri gösterir. Belirtilmişse DWORD/QWORD değer verisini onaltılık biçimde sunulur. Diğer türleri için geçerli değil. Varsayılan değer **$false**.|
| DependsOn| Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Kayıt defteri değeri için veriler.|
| ValueType| Değer türünü belirtir. Desteklenen türler şunlardır: Dize (REG_SZ), ikili dosya (ikili REG), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), çok dizeli (REG_MULTI_SZ), Genişletilebilir dize (REG_EXPAND_SZ) |

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

> [!NOTE]
> Bir kayıt defteri ayarı değiştirerek `HKEY\CURRENT\USER` hive gerektirir yapılandırma sistemi olarak değil, kullanıcı kimlik bilgileriyle çalışır. Kullanabileceğiniz **PsDscRunAsCredential** özelliği yapılandırması için kullanıcı kimlik bilgilerini belirtin. Bir örnek için bkz. [DSC çalıştıran kullanıcı kimlik bilgileriyle](../../../configurations/runAsUser.md).
