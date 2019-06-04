---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Kaynaklarıyla Kimlik Bilgilerini Kullanma
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470756"
---
# <a name="use-credentials-with-dsc-resources"></a>DSC Kaynaklarıyla Kimlik Bilgilerini Kullanma

> Şunun için geçerlidir: Windows PowerShell 5.0, 5.1 Windows PowerShell

Belirtilen kimlik bilgileri kümesi altında bir DSC kaynak otomatik kullanarak çalıştırabileceğiniz **PsDscRunAsCredential** yapılandırma özellik. Varsayılan olarak, DSC, her kaynak sistem hesabı olarak çalışır. Belirli bir kullanıcı bağlamında MSI paketleri yükleme, bir kullanıcının kayıt defteri anahtarlarını ayarlamak, bir kullanıcının belirli yerel dizine veya bir ağ erişim gibi gerekli bir kullanıcı olarak çalıştırmanın ne zaman paylaşmak zamanlar vardır. **SeInteractiveLogonRight** belirttiğiniz herhangi bir hesabı için hedef makine tarafından gerekli **PSDSCRunAsCredential**. Daha fazla bilgi için [hesabı haklarını sabitleri](/windows/desktop/secauthz/account-rights-constants).

Her DSC kaynağı bir **PsDscRunAsCredential** herhangi bir kullanıcı kimlik bilgisi için ayarlanabilir özelliği (bir [PSCredential](/dotnet/api/system.management.automation.pscredential) nesne). Kimlik bilgisi yapılandırma özelliğinin değeri olarak sabit kodlanmış olabilir ya da değer ayarlamak [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), hangi ister kullanıcı için bir kimlik bilgisi (hakkında bilgi için yapılandırma derlendiğinde yapılandırmaları derleme, bkz: [yapılandırmaları](configurations.md).

> [!NOTE]
> PowerShell 5.0, kullanarak **PsDscRunAsCredential** yapılandırmaları bileşik kaynakları arama özelliği desteklenmiyor. PowerShell 5.1 içinde **PsDscRunAsCredential** özelliği bileşik kaynakları arama yapılandırmada desteklenir. **PsDscRunAsCredential** PowerShell 4. 0'özelliği kullanılamaz.

Aşağıdaki örnekte, `Get-Credential` kullanıcıdan kimlik bilgileri istemek için kullanılır. **Kayıt defteri** kaynak Windows komut istemi penceresi arka plan rengini belirten kayıt defteri anahtarı değiştirmek için kullanılır.

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

> [!NOTE]
> Bu örnek, geçerli bir sertifikada sahibi olduğunuzu varsayar `C:\publicKeys\targetNode.cer`, ve bu sertifikanın parmak izini gösterilen değer olduğunu. DSC yapılandırma MOF dosyaları kimlik bilgilerini şifreleme hakkında daha fazla bilgi için bkz: [MOF dosyasının güvenliğini sağlama](../pull-server/secureMOF.md).
