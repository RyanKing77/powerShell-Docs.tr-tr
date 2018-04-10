---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC’yi kullanıcı kimlik bilgileri ile çalıştırma
ms.openlocfilehash: 37e6ff64c9c6d3960653d417e22a6c93c653230c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="running-dsc-with-user-credentials"></a>DSC’yi kullanıcı kimlik bilgileri ile çalıştırma

> İçin geçerlidir: Windows PowerShell 5.0, 5.1 Windows PowerShell

Belirtilen kimlik bilgileri kümesi altında bir DSC kaynak otomatik kullanarak çalıştırabilirsiniz **PsDscRunAsCredential** özelliğini yapılandırma.
Varsayılan olarak, DSC her bir kaynağın sistem hesabı olarak çalışır.
Bir kullanıcı belirli bir kullanıcı bağlamında bir MSI paketleri yükleme, bir kullanıcının kayıt defteri anahtarlarını ayarlamak, bir kullanıcının belirli yerel dizinine erişmesini veya bir ağa erişen gibi gerekli olduğu gibi çalışan zaman paylaşmak zamanlar vardır.

Her DSC kaynağı olan bir **PsDscRunAsCredential** tüm kullanıcı kimlik bilgilerinin ayarlanabilir özelliği (bir [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) nesnesi).
Kimlik bilgileri Yapılandırma özelliğinin değeri olarak sabit kodlanmış olabilir ya da değeri ayarlamak [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), hangi ister kullanıcı için bir kimlik bilgisi (hakkında bilgi için yapılandırma derlendiğinde yapılandırmaları derleme, bkz: [yapılandırmaları](configurations.md).

>**Not:** PowerShell'de kullanarak 5.0, **PsDscRunAsCredential** bileşik kaynakları çağırma yapılandırmaları özelliğinde desteklenmiyordu.
>PowerShell 5.1 içinde **PsDscRunAsCredential** özelliği bileşik kaynakları çağırma yapılandırmalarında desteklenir.

>**Not:** **PsDscRunAsCredential** özelliği PowerShell 4. 0 ' kullanılabilir değil.

Aşağıdaki örnekte, **Get-Credential** kullanıcıdan kimlik bilgileri istemek için kullanılır.
[Kayıt defteri](registryResource.md) kaynak Windows komut istemi penceresi arka plan rengini belirtir kayıt defteri anahtarı değiştirmek için kullanılır.

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
>**Not:** Bu örnek, geçerli bir sertifika olduğunu varsayar `C:\publicKeys\targetNode.cer`, ve bu sertifikanın parmak izini gösterilen değer olduğunu.
>DSC yapılandırma MOF dosyaları kimlik bilgileri şifreleme hakkında daha fazla bilgi için bkz: [MOF dosyası güvenli hale getirme](secureMOF.md).