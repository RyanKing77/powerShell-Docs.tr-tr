---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Kaynaklarıyla Kimlik Bilgilerini Kullanma
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080059"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="3b153-103">DSC Kaynaklarıyla Kimlik Bilgilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="3b153-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="3b153-104">Uygulama hedefi: Windows PowerShell 5.0, 5.1 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b153-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="3b153-105">Belirtilen kimlik bilgileri kümesi altında bir DSC kaynak otomatik kullanarak çalıştırabileceğiniz **PsDscRunAsCredential** yapılandırma özellik.</span><span class="sxs-lookup"><span data-stu-id="3b153-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="3b153-106">Varsayılan olarak, DSC, her kaynak sistem hesabı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="3b153-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="3b153-107">Belirli bir kullanıcı bağlamında MSI paketleri yükleme, bir kullanıcının kayıt defteri anahtarlarını ayarlamak, bir kullanıcının belirli yerel dizine veya bir ağ erişim gibi gerekli bir kullanıcı olarak çalıştırmanın ne zaman paylaşmak zamanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="3b153-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="3b153-108">Her DSC kaynağı bir **PsDscRunAsCredential** herhangi bir kullanıcı kimlik bilgisi için ayarlanabilir özelliği (bir [PSCredential](/dotnet/api/system.management.automation.pscredential) nesne).</span><span class="sxs-lookup"><span data-stu-id="3b153-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span>
<span data-ttu-id="3b153-109">Kimlik bilgisi yapılandırma özelliğinin değeri olarak sabit kodlanmış olabilir ya da değer ayarlamak [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), hangi ister kullanıcı için bir kimlik bilgisi (hakkında bilgi için yapılandırma derlendiğinde yapılandırmaları derleme, bkz: [yapılandırmaları](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="3b153-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3b153-110">PowerShell 5.0, kullanarak **PsDscRunAsCredential** yapılandırmaları bileşik kaynakları arama özelliği desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3b153-110">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
> <span data-ttu-id="3b153-111">PowerShell 5.1 içinde **PsDscRunAsCredential** özelliği bileşik kaynakları arama yapılandırmada desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3b153-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>
> <span data-ttu-id="3b153-112">**PsDscRunAsCredential** PowerShell 4. 0'özelliği kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3b153-112">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="3b153-113">Aşağıdaki örnekte, `Get-Credential` kullanıcıdan kimlik bilgileri istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b153-113">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span>
<span data-ttu-id="3b153-114">**Kayıt defteri** kaynak Windows komut istemi penceresi arka plan rengini belirten kayıt defteri anahtarı değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b153-114">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
> <span data-ttu-id="3b153-115">Bu örnek, geçerli bir sertifikada sahibi olduğunuzu varsayar `C:\publicKeys\targetNode.cer`, ve bu sertifikanın parmak izini gösterilen değer olduğunu.</span><span class="sxs-lookup"><span data-stu-id="3b153-115">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
> <span data-ttu-id="3b153-116">DSC yapılandırma MOF dosyaları kimlik bilgilerini şifreleme hakkında daha fazla bilgi için bkz: [MOF dosyasının güvenliğini sağlama](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="3b153-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
