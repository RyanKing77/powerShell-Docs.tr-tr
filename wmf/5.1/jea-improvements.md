---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: ryanpu
title: Yeterli yönetim (JEA) geliştirmeleri
ms.openlocfilehash: 66cbacb78f8a365e9c8556c7c56b3c3525de7395
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055641"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="0e707-103">Yeterli yönetim (JEA) geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="0e707-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="0e707-104">JEA uç öğesine/öğesinden kısıtlanmış dosya kopyalama</span><span class="sxs-lookup"><span data-stu-id="0e707-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="0e707-105">Artık dosyaları uzaktan kopyalayabilirsiniz/bağlanan kullanıcının yalnızca kopyalanamıyor bir JEA uç noktası ve rest garanti *herhangi* dosya sisteminize.</span><span class="sxs-lookup"><span data-stu-id="0e707-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="0e707-106">Kullanıcıları bağlamak için bir kullanıcı sürücü için PSSC dosyanızı yapılandırarak bu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0e707-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="0e707-107">Kullanıcı oturumu arasında kalıcıdır ve bağlanan her kullanıcı için benzersiz bir yeni PSDrive sürücüdür.</span><span class="sxs-lookup"><span data-stu-id="0e707-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="0e707-108">Zaman `Copy-Item` olduğu için veya bir JEA oturumdan dosyaları kopyalamak için kullanılan, onu yalnızca kullanıcı sürücüye erişime izin vermek için sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e707-108">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="0e707-109">Dosyaları kopyalamak için başka bir PSDrive girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0e707-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="0e707-110">Kullanıcı bir sürücünün JEA oturum yapılandırma dosyanızda ayarlamak için aşağıdaki yeni alanları kullanın:</span><span class="sxs-lookup"><span data-stu-id="0e707-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="0e707-111">Kullanıcı sürücünün yedekleme klasörü oluşturulur `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="0e707-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="0e707-112">Kullanıcı sürücü yazılımınız ve/kullanıcı sürücü kullanıma sunmak için yapılandırılmış bir JEA uç noktasından dosyaları kopyalamak için kullanın `-ToSession` ve `-FromSession` parametrelere `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="0e707-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="0e707-113">Ardından, kullanıcı sürücüde depolanan verileri işlemek ve kullanıcı rolü özelliği için kullanılabilir hale özel işlevler yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e707-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="0e707-114">Destek grubu için Yönetilen hizmet hesapları</span><span class="sxs-lookup"><span data-stu-id="0e707-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="0e707-115">Bazı durumlarda, bir kullanıcı bir JEA oturumda gerçekleştirmesi gereken bir görevi, yerel makine ötesindeki kaynaklara gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0e707-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="0e707-116">Bir JEA oturumu, sanal bir hesabı kullanacak şekilde yapılandırıldığında, yerel makinenin kimlik, olmayan sanal hesap veya bağlı durumda olan kullanıcı gelen gibi kaynaklarına ulaşmak için her türlü girişim görünecektir.</span><span class="sxs-lookup"><span data-stu-id="0e707-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="0e707-117">JEA bağlamında çalıştırma desteği etkinleştirdik TP5'te bir [Grup yönetilen hizmet hesabı](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), bir etki alanı kimliği'ni kullanarak ağ kaynaklarına erişmek çok daha kolay hale getirme.</span><span class="sxs-lookup"><span data-stu-id="0e707-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="0e707-118">Bir JEA oturumu gMSA hesabı altında çalışacak şekilde yapılandırmak için aşağıdaki yeni anahtarı PSSC dosyanızda kullanın:</span><span class="sxs-lookup"><span data-stu-id="0e707-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="0e707-119">Grup yönetilen hizmet hesapları yalıtım veya sanal hesaplar sınırlı kapsamı göze değil.</span><span class="sxs-lookup"><span data-stu-id="0e707-119">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="0e707-120">Bağlanan her kullanıcı izinlerinizi kuruluş genelinde aynı gMSA kimlik paylaşır.</span><span class="sxs-lookup"><span data-stu-id="0e707-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="0e707-121">Bir gmsa'yı kullanın ve her zaman mümkün olduğunda yerel makineye sınırlı olan sanal hesaplar tercih seçerken dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="0e707-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="0e707-122">Koşullu erişim ilkeleri</span><span class="sxs-lookup"><span data-stu-id="0e707-122">Conditional access policies</span></span>

<span data-ttu-id="0e707-123">JEA olduğunda bunlar, ne yapmalı yönetmek için bir sisteme ayrıca sınırlamak istiyorsanız bağlandıktan birinin neler yapabileceğinizi sınırlama en harika *olduğunda* birisi JEA kullanabilir miyim?</span><span class="sxs-lookup"><span data-stu-id="0e707-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="0e707-124">Güvenlik grupları bir kullanıcı bir JEA oturumu için ait olmalıdır belirtmenizi sağlar oturum yapılandırma dosyalarına (.pssc) yapılandırma seçeneği ekledik.</span><span class="sxs-lookup"><span data-stu-id="0e707-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="0e707-125">Ortamınızda yalnızca zamanında (JIT) sisteminiz ve kullanıcılarınızın üst düzeyde ayrıcalıklı bir JEA uç noktası erişmeden önce kendi ayrıcalıklarını yükseltme yapmak istiyorsanız bu özellikle yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e707-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="0e707-126">Yeni *RequiredGroups* PSSC dosyasında alan, bir kullanıcı için JEA bağlanabildiğini belirlemek için mantığı belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e707-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="0e707-127">Kullanır (isteğe bağlı olarak iç içe) bir hashtable belirtme oluşur 'Ve' ve 'Veya' anahtarlar kurallarınızı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0e707-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="0e707-128">Bu alan kullanmayı bazı örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0e707-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="0e707-129">Düzeltildi: Sanal hesaplar artık Windows Server 2008 R2 üzerinde desteklenir</span><span class="sxs-lookup"><span data-stu-id="0e707-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="0e707-130">WMF 5.1, artık Windows Server 2008 tutarlı yapılandırmalar ve özellik eşliği arasında Windows Server 2008 R2 - 2016 etkinleştirme R2 sanal hesaplar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e707-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="0e707-131">Jea'yı, Windows 7'de kullanırken sanal hesaplar desteklenmeyen kalır.</span><span class="sxs-lookup"><span data-stu-id="0e707-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>