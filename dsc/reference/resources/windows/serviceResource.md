---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Hizmet kaynağı
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048632"
---
# <a name="dsc-service-resource"></a>DSC Hizmet kaynağı

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0


**Hizmet** kaynak olarak Windows PowerShell Desired State Configuration (DSC), hedef düğümdeki hizmetleri yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| Ad| Hizmet adını belirtir. Bazen bu görünen addan farklı olduğunu unutmayın. Hizmetler ve Get-Service cmdlet'i ile bunların geçerli durumunu listesini alabilirsiniz.|
| BuiltInAccount| Hizmet için kullanılacak oturum açma hesabı gösterir. Bu özellik için izin verilen değerler şunlardır: **Yerelhizmet**, **LocalSystem**, ve **NetworkService**.|
| Kimlik bilgisi| Hizmet, altında çalışacağı hesabın kimlik bilgilerini belirtir. Bu özellik ve __BuiltinAccount__ özelliği birlikte kullanılamaz.|
| DependsOn| Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|
| Başlangıç türü| Hizmet başlangıç türünü gösterir. Bu özellik için izin verilen değerler şunlardır: **Otomatik**, **devre dışı bırakılmış**, ve **el ile**|
| Durum| Hizmet için sağlamak istediğiniz durumu gösterir.|
| Açıklama | Hedef hizmet açıklamasını gösterir.|
| Görünen Ad | Hedef hizmet görünen adını belirtir.|
| Emin olun | Hedef hizmet sistemde var olup olmadığını gösterir. Bu özellik kümesine **devamsızlık** hedef hizmet yok emin olmak için. Bu ayarın **mevcut** hedef hizmetinin var olduğunu (varsayılan değer) sağlar.|
| Yol | Yeni bir hizmet için ikili dosya yolunu gösterir.|

## <a name="example"></a>Örnek

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```