---
ms.date: 2017-10-13
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Durum yapılandırmasına genel bakış karar alıcılar için istenen"
ms.openlocfilehash: ae545ead0718def44d5a17708d254b872691e1d3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="de974-103">Durum yapılandırmasına genel bakış mühendisleri için istenen</span><span class="sxs-lookup"><span data-stu-id="de974-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="de974-104">Bu belge, PowerShell istenen durum yapılandırması (DSC) avantajlarını öğrenmeniz Geliştirici ve işlemleri ekipleri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="de974-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="de974-105">DSC değeri yüksek düzey bir görünümünü sağlar için lütfen bkz [istenen durum yapılandırması için genel bakış karar alıcılar](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="de974-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="de974-106">İstenen durum yapılandırması yararları</span><span class="sxs-lookup"><span data-stu-id="de974-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="de974-107">DSC var için:</span><span class="sxs-lookup"><span data-stu-id="de974-107">DSC exists to:</span></span>

- <span data-ttu-id="de974-108">Windows komut dosyası karmaşıklığını azaltmak</span><span class="sxs-lookup"><span data-stu-id="de974-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="de974-109">Yineleme hızını artırmak</span><span class="sxs-lookup"><span data-stu-id="de974-109">Increase the speed of iteration</span></span>

<span data-ttu-id="de974-110">"Sürekli dağıtımı" kavramı daha önemli hale gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="de974-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="de974-111">Sürekli dağıtım sık, potansiyel olarak birçok kez günde dağıtma yeteneği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="de974-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="de974-112">Bu dağıtımlar amacı olan bir şey düzeltme değil ancak hızlı bir şekilde yayımlanan bir şey almak için.</span><span class="sxs-lookup"><span data-stu-id="de974-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="de974-113">Yeni özellikler işlemde geliştirme aracılığıyla sorunsuz ve mümkün olduğunca güvenilir bir şekilde alarak, saat değerini yeni iş mantığı azaltın.</span><span class="sxs-lookup"><span data-stu-id="de974-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="de974-114">Burada bir bitiş durumu ortam metin olarak bildirilen ve dağıtım altyapısına yayımlanan bir "bildirim temelli" şablonu modeli kullanan bir dağıtım çözümü gelir bulut doğru taşıyın.</span><span class="sxs-lookup"><span data-stu-id="de974-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="de974-115">Herhangi bir zamanda dağıtım son durum güvence altına almak için tutarlı bir şekilde yinelenebilir olduğundan bu dağıtım yöntemi, ölçekte hızlı değişiklik hatanın tehdide karşı esnekliği ile sağlar.</span><span class="sxs-lookup"><span data-stu-id="de974-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="de974-116">Araçlar ve işlem Otomasyonu boyunca bu stili destekleyen hizmetlerin oluşturulmasını bu değişikliklere yanıt olan.</span><span class="sxs-lookup"><span data-stu-id="de974-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="de974-117">DSC bir bildirim temelli sağlar platform ve ıdempotent (yinelenebilir) dağıtımı, yapılandırma ve uyumluluk içindir.</span><span class="sxs-lookup"><span data-stu-id="de974-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="de974-118">DSC platformu, veri merkezinizdeki bileşenlerinin hatalarını önler ve pahalı dağıtım hatalarını önler doğru yapılandırmasına sahip olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="de974-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="de974-119">DSC yapılandırmaları uygulama kodunun bir parçası olarak kabul ederek, DSC sürekli dağıtımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="de974-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="de974-120">DSC yapılandırması uygulamayı dağıtmak için gereken bilgi her zaman güncel ve kullanılacak hazır olduğundan emin olmanın uygulama, bir parçası olarak güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="de974-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="de974-121">"I PowerShell istenen durum yapılandırması neden ihtiyacım var?"</span><span class="sxs-lookup"><span data-stu-id="de974-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="de974-122">DSC yapılandırmaları ayrı amacını veya "ne yapmak istiyorum", yürütme veya "nasıl yapılacağını istiyorum."</span><span class="sxs-lookup"><span data-stu-id="de974-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="de974-123">Bu, yürütme mantığını içindeki kaynaklara içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="de974-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="de974-124">Kullanıcıların nasıl uygulanacağını veya bu özellik için bir DSC kaynağı kullanılabilir olduğunda bir özellik dağıtmak bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="de974-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="de974-125">Bu, kullanıcının kendi dağıtım yapısı üzerinde odaklanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="de974-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="de974-126">Örnek olarak, PowerShell komut aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="de974-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="de974-127">Bu komut, basit, anlaşılabilir ve kolay dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="de974-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="de974-128">Bununla birlikte, bu komut dosyası üretime geçirmeden çalışırsanız, çeşitli sorunlar çalışır.</span><span class="sxs-lookup"><span data-stu-id="de974-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="de974-129">Ne betik arka arkaya iki kez çalışan olur?</span><span class="sxs-lookup"><span data-stu-id="de974-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="de974-130">Bob paylaşıma tam erişimi daha önce varsa ne olur?</span><span class="sxs-lookup"><span data-stu-id="de974-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="de974-131">Bu sorunlar için dengelemek için komut dosyası "gerçek" sürümü gibi bir daha yakın görünür:</span><span class="sxs-lookup"><span data-stu-id="de974-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="de974-132">Bu komut, daha karmaşık, Eskinin mantık ve hata işleme ile dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="de974-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="de974-133">Yanıtlar, istediğiniz artık belirten olduğundan komut dosyası daha karmaşıktır, ancak *nasıl yapılacağını*.</span><span class="sxs-lookup"><span data-stu-id="de974-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="de974-134">Temel mantığını hemen soyutlanır ve DSC yapılmasını istediğinizi düşünelim sağlar.</span><span class="sxs-lookup"><span data-stu-id="de974-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="de974-135">Bu komut, düzgün bir şekilde biçimlendirilmiş ve okumak basit dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="de974-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="de974-136">Hata işleme ve mantık yollarını içinde hala mevcut [kaynak](resources.md) uygulama ancak betik Yazar görünmez.</span><span class="sxs-lookup"><span data-stu-id="de974-136">The logic paths and error handling are still present in the [resource](resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="de974-137">Yapı ortamından ayırma</span><span class="sxs-lookup"><span data-stu-id="de974-137">Separating Environment from Structure</span></span>

<span data-ttu-id="de974-138">DevOps ortak desende dağıtımı için birden çok ortamları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de974-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="de974-139">Örneğin, hızlı bir şekilde prototip yeni kod kullanılan "geliştirme" ortam olabilir.</span><span class="sxs-lookup"><span data-stu-id="de974-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="de974-140">"Geliştirme" ortamından kod burada diğer kişilerin yeni işlevselliği doğrulayın "test" ortamına gider.</span><span class="sxs-lookup"><span data-stu-id="de974-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="de974-141">Son olarak, kod "prod" ya da Canlı site üretim ortamına gider.</span><span class="sxs-lookup"><span data-stu-id="de974-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="de974-142">DSC yapılandırmaları uyum bu geliştirme test üretim ardışık düzen kullanılarak [yapılandırma verilerini](configData.md).</span><span class="sxs-lookup"><span data-stu-id="de974-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](configData.md).</span></span>
<span data-ttu-id="de974-143">Bu, daha fazla yönetilen düğümler yapılandırmasından yapısını arasındaki farkı soyutlar.</span><span class="sxs-lookup"><span data-stu-id="de974-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="de974-144">Örneğin, bir SQL server, IIS sunucusu ve bir orta katman server gerektiren bir yapılandırma tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de974-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="de974-145">Bu yapılandırma farklı parçalarının hangi düğümleri Al bağımsız olarak, bu üç öğe her zaman mevcut olacaktır.</span><span class="sxs-lookup"><span data-stu-id="de974-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="de974-146">Üç tüm öğeleri aynı makine üç öğeleri ayrı bir test ortamı için üç farklı makinelere geliştirme ortamınız için doğru işaret edecek şekilde yapılandırma verilerini kullanabilirsiniz ve son olarak üretim ortamı için tüm üretim sunucularında doğru.</span><span class="sxs-lookup"><span data-stu-id="de974-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="de974-147">Farklı ortamlar için dağıtmak için çağırabilirsiniz **başlangıç DscConfiguration** hedeflemek istediğiniz ortam için doğru yapılandırma verileri.</span><span class="sxs-lookup"><span data-stu-id="de974-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="de974-148">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="de974-148">See Also</span></span>

[<span data-ttu-id="de974-149">Yapılandırmalar</span><span class="sxs-lookup"><span data-stu-id="de974-149">Configurations</span></span>](configurations.md)

[<span data-ttu-id="de974-150">Yapılandırma verileri</span><span class="sxs-lookup"><span data-stu-id="de974-150">Configuration Data</span></span>](configData.md)

[<span data-ttu-id="de974-151">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="de974-151">Resources</span></span>](resources.md)
