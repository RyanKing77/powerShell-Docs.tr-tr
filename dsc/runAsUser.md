---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC kullanıcı kimlik bilgileriyle çalıştırma"
ms.openlocfilehash: 7b57732679e4fb29112a3ca7fe64cba2bda67207
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="7e3ea-103">DSC kullanıcı kimlik bilgileriyle çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7e3ea-103">Running DSC with user credentials</span></span> 

> <span data-ttu-id="7e3ea-104">İçin geçerlidir: Windows PowerShell 5.0, 5.1 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e3ea-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="7e3ea-105">Belirtilen kimlik bilgileri kümesi altında bir DSC kaynak otomatik kullanarak çalıştırabilirsiniz **PsDscRunAsCredential** özelliğini yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="7e3ea-106">Varsayılan olarak, DSC her bir kaynağın sistem hesabı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="7e3ea-107">Bir kullanıcı belirli bir kullanıcı bağlamında bir MSI paketleri yükleme, bir kullanıcının kayıt defteri anahtarlarını ayarlamak, bir kullanıcının belirli yerel dizinine erişmesini veya bir ağa erişen gibi gerekli olduğu gibi çalışan zaman paylaşmak zamanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="7e3ea-108">Her DSC kaynağı olan bir **PsDscRunAsCredential** tüm kullanıcı kimlik bilgilerinin ayarlanabilir özelliği (bir [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) nesnesi).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="7e3ea-109">Kimlik bilgileri Yapılandırma özelliğinin değeri olarak sabit kodlanmış olabilir ya da değeri ayarlamak [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), hangi ister kullanıcı için bir kimlik bilgisi (hakkında bilgi için yapılandırma derlendiğinde yapılandırmaları derleme, bkz: [yapılandırmaları](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="7e3ea-110">**Not:** PowerShell'de kullanarak 5.0, **PsDscRunAsCredential** bileşik kaynakları çağırma yapılandırmaları özelliğinde desteklenmiyordu.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> 
><span data-ttu-id="7e3ea-111">PowerShell 5.1 içinde **PsDscRunAsCredential** özelliği bileşik kaynakları çağırma yapılandırmalarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="7e3ea-112">**Not:** **PsDscRunAsCredential** özelliği PowerShell 4. 0 ' kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="7e3ea-113">Aşağıdaki örnekte, **Get-Credential** kullanıcıdan kimlik bilgileri istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span> <span data-ttu-id="7e3ea-114">[Kayıt defteri](registryResource.md) kaynak Windows komut istemi penceresi arka plan rengini belirtir kayıt defteri anahtarı değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
><span data-ttu-id="7e3ea-115">**Not:** Bu örnek, geçerli bir sertifika olduğunu varsayar `C:\publicKeys\targetNode.cer`, ve bu sertifikanın parmak izini gösterilen değer olduğunu.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="7e3ea-116">DSC yapılandırma MOF dosyaları kimlik bilgileri şifreleme hakkında daha fazla bilgi için bkz: [MOF dosyası güvenli hale getirme](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>

