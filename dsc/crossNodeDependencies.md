---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Geçici bir düğüm bağımlılıkları belirtme"
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a>Geçici bir düğüm bağımlılıkları belirtme

> İçin geçerlidir: Windows PowerShell 5.0

DSC özel kaynaklar sağlar **WaitForAll**, **WaitForAny**, ve **WaitForSome** kullanılabilecek yapılandırmalarında diğer yapılandırmaları bağımlılıklarını belirtmek için düğümleri. Bu kaynaklar davranışını aşağıdaki gibidir:

* **WaitForAll**: Belirtilen kaynak tanımlanan tüm hedef düğümleri üzerinde istenen durumda ise başarılı **NodeName** özelliği.
* **WaitForAny**: Belirtilen kaynak tanımlanan hedef düğümleri en az biri istenilen durumda ise başarılı **NodeName** özelliği.
* **WaitForSome**: belirten bir **NodeCount** özelliğine ek olarak bir **NodeName** özelliği. Kaynak istenen düğüm sayısı alt sınırı durumda ise kaynak başarılı (tarafından belirtilen **NodeCount**) tarafından tanımlanan **NodeName** özelliği. 

## <a name="using-waitforxxxx-resources"></a>WaitForXXXX kaynaklarını kullanma

Kullanılacak **WaitForXXXX** kaynakları, oluşturduğunuz bir kaynak blok bu kaynak türünün beklemek için düğümlerini ve DSC kaynağı belirtir. Daha sonra **DependsOn** herhangi bir kaynağa özelliğinde engeller belirtilen koşullar için beklenecek yapılandırmanızda **WaitForXXXX** başarılı olması için düğüm.

Örneğin, aşağıdaki yapılandırmasında, hedef düğüm bekliyor **xADDomain** bitmesi için kaynak **MyDC** en fazla 30 düğümle yeniden deneme sayısı, 15 saniye aralıklarla önce Hedef düğüm etki alanına katılmasını sağlayabilir.

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present' 
            Name = 'AD-Domain-Services' 
        }

        xADDomain NewDomain 
        { 
            DomainName = 'Contoso.com'            
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**Not:** WaitForXXX varsayılan kaynakları bir kez deneyin ve sonra başarısız. Gerekli olmamasına karşın, genellikle bir yeniden deneme aralığı ve sayısı belirtin istersiniz.

## <a name="see-also"></a>Ayrıca bkz:
* [DSC yapılandırmaları](configurations.md)
* [DSC kaynakları](resources.md)
* [Yerel Yapılandırma Yöneticisi'ni yapılandırma](metaConfig.md)

