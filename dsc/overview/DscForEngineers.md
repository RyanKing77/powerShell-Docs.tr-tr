---
ms.date: 10/13/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Mühendisler için İstenen Durum Yapılandırmasına Genel Bakış
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079991"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="28ef3-103">Mühendisler için İstenen Durum Yapılandırmasına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="28ef3-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="28ef3-104">Bu belge, PowerShell Desired State Configuration (DSC) yararlarını Geliştirici ve işlem ekipleri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="28ef3-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="28ef3-105">DSC değeri daha yüksek düzey bir görünümünü sağlar için lütfen bkz [Desired State Configuration ' ne genel bakış karar alma](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="28ef3-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="28ef3-106">Desired State Configuration ' ın avantajları</span><span class="sxs-lookup"><span data-stu-id="28ef3-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="28ef3-107">DSC için bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="28ef3-107">DSC exists to:</span></span>

- <span data-ttu-id="28ef3-108">İçinde Windows scripting karmaşıklığını azaltın</span><span class="sxs-lookup"><span data-stu-id="28ef3-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="28ef3-109">Yineleme hızını artırın</span><span class="sxs-lookup"><span data-stu-id="28ef3-109">Increase the speed of iteration</span></span>

<span data-ttu-id="28ef3-110">"Sürekli dağıtım" kavramı daha önemli hale gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="28ef3-111">Sürekli dağıtım, birden çok kez günde sık, büyük olasılıkla dağıtma yeteneği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="28ef3-112">Bu dağıtımları amacı olan bir şeyi düzeltmemeyi ancak bir kolayca yayımlanan almak için.</span><span class="sxs-lookup"><span data-stu-id="28ef3-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="28ef3-113">Yeni özellikleri geliştirme işleminde göz önünde aracılığıyla sorunsuz ve mümkün olduğunca güvenilir bir şekilde alarak, saat değeri yeni iş mantığı azaltın.</span><span class="sxs-lookup"><span data-stu-id="28ef3-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="28ef3-114">Bulut bilgi işlemin son durumu ortam burada metin olarak bildirilmiş ve bir dağıtım altyapısı için yayımlanan bir "bildirim" Şablon modeli kullanan bir dağıtım çözümü gelir doğru taşıyın.</span><span class="sxs-lookup"><span data-stu-id="28ef3-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="28ef3-115">Herhangi bir zamanda dağıtımın bir bitiş durumuna güvence altına almak için tutarlı bir şekilde yinelenebilir çünkü bu dağıtım yöntemi, uygun ölçekte, hızlı bir değişiklik tehdit hatalarına karşı dayanıklılık ile olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="28ef3-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="28ef3-116">Araçlar ve bu işlemleri Otomasyon aracılığıyla stilini destekleyen hizmetleri oluşturmak, bu değişiklikleri yanıt olan.</span><span class="sxs-lookup"><span data-stu-id="28ef3-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="28ef3-117">DSC, bir bildirim temelli sağlayan bir platform ve etkili (tekrarlanabilir) dağıtım, yapılandırma ve uyumluluk içindir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="28ef3-118">DSC platform bileşenleri veri merkezinizin hataları önler ve pahalı dağıtım hatalarını önler doğru yapılandırma olmasını sağlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="28ef3-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="28ef3-119">DSC yapılandırmaları uygulama kodunun bir parçası olarak kabul ederek, DSC sürekli dağıtımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="28ef3-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="28ef3-120">DSC yapılandırması, uygulamayı dağıtmak için ihtiyacınız olan bilgileri her zaman güncel ve kullanılmaya hazır olduğundan emin olmanın uygulamanın bir parçası olarak güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="28ef3-121">"Ben PowerShell Desired State Configuration neden ihtiyacım var?"</span><span class="sxs-lookup"><span data-stu-id="28ef3-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="28ef3-122">DSC yapılandırmaları ayrı hedefi veya "ne yapmak istiyorum", yürütme veya "ne yapmak istiyorum."</span><span class="sxs-lookup"><span data-stu-id="28ef3-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="28ef3-123">Bu, yürütme mantığı içindeki kaynakların içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="28ef3-124">Kullanıcıların nasıl uygulamak veya bu özellik için bir DSC kaynağı kullanılabilir olduğunda, bir özellik dağıtmak bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="28ef3-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="28ef3-125">Bu, kullanıcının kendi dağıtım yapısı üzerinde odaklanmanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="28ef3-126">Örneğin, PowerShell betikleri gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="28ef3-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="28ef3-127">Bu, basit, anlaşılır ve basit betiğidir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="28ef3-128">Bununla birlikte, bu betiği üretime geçirmeden çalışırsanız, birkaç bir sorunla karşılaşırsanız çalışır.</span><span class="sxs-lookup"><span data-stu-id="28ef3-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="28ef3-129">Arka arkaya iki kez çalışan betik ne olacak?</span><span class="sxs-lookup"><span data-stu-id="28ef3-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="28ef3-130">Bob paylaşıma tam erişimi daha önce varsa ne olur?</span><span class="sxs-lookup"><span data-stu-id="28ef3-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="28ef3-131">Bu sorunlar için dengelemek için komut dosyasının "gerçek" bir sürümünü gibi bir şey daha yakından görünür:</span><span class="sxs-lookup"><span data-stu-id="28ef3-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
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

<span data-ttu-id="28ef3-132">Bu betik, karmaşık olsun, Eskinin mantık ve hata işleme ile.</span><span class="sxs-lookup"><span data-stu-id="28ef3-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="28ef3-133">Bitti, istediğiniz artık belirten çünkü kod daha karmaşıktır ama *nasıl yapılacağını*.</span><span class="sxs-lookup"><span data-stu-id="28ef3-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="28ef3-134">Temel mantığını hemen soyutlanır ve DSC bitti istediğinizi varsayalım sağlar.</span><span class="sxs-lookup"><span data-stu-id="28ef3-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

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
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="28ef3-135">Bu, düzgün bir şekilde biçimlendirilmiş ve okunamıyor basit betiğidir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="28ef3-136">Hata işleme ve mantık yollarını hâlâ bulunan [kaynak](../resources/resources.md) uygulaması, ancak komut dosyası yazma için görünmez.</span><span class="sxs-lookup"><span data-stu-id="28ef3-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="28ef3-137">Yapı ortamından ayırma</span><span class="sxs-lookup"><span data-stu-id="28ef3-137">Separating Environment from Structure</span></span>

<span data-ttu-id="28ef3-138">DevOps, yaygın bir düzen dağıtımı için birden çok ortamı sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="28ef3-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="28ef3-139">Örneğin, hızlı bir şekilde prototip yeni kod için kullanılan bir "dev" ortam olabilir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="28ef3-140">"Dev" ortam koddan bir "test" ortamına burada diğer kişilerin yeni işlevselliğini doğrulamak gider.</span><span class="sxs-lookup"><span data-stu-id="28ef3-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="28ef3-141">Son olarak, kodu "prod" veya canlı site üretim ortamına gider.</span><span class="sxs-lookup"><span data-stu-id="28ef3-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="28ef3-142">DSC yapılandırmaları barındırmak bu geliştirme-test-prod işlem hattı kullanımının [yapılandırma verilerini](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="28ef3-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="28ef3-143">Bu, daha fazla yönetilen düğümlere yapılandırmasından yapısını arasındaki farkı soyutlar.</span><span class="sxs-lookup"><span data-stu-id="28ef3-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="28ef3-144">Örneğin, bir SQL server, IIS sunucusu ve bir orta katman sunucusu gerektiren bir yapılandırmasını tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="28ef3-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="28ef3-145">Hangi düğümleri Bu yapılandırmanın farklı parçaları Al bağımsız olarak, bu üç öğe her zaman mevcut olacak.</span><span class="sxs-lookup"><span data-stu-id="28ef3-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="28ef3-146">Üç tüm öğeler aynı makine için bir geliştirme ortamı, üç öğeleri ayrı bir test ortamı için üç farklı makinelere işaret edecek şekilde yapılandırma verilerini kullanabilirsiniz ve son olarak, tüm üretim sunucuları üretim ortamı için doğru.</span><span class="sxs-lookup"><span data-stu-id="28ef3-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="28ef3-147">Farklı ortamlara dağıtmak üzere, çağırabilirsiniz **Başlat-DscConfiguration** hedeflemek istediğiniz ortam için doğru yapılandırma verileri.</span><span class="sxs-lookup"><span data-stu-id="28ef3-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="28ef3-148">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="28ef3-148">See Also</span></span>

[<span data-ttu-id="28ef3-149">Yapılandırmalar</span><span class="sxs-lookup"><span data-stu-id="28ef3-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="28ef3-150">Yapılandırma verileri</span><span class="sxs-lookup"><span data-stu-id="28ef3-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="28ef3-151">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="28ef3-151">Resources</span></span>](../resources/resources.md)
