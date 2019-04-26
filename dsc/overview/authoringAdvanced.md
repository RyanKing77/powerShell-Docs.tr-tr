---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: CI/CD işlem hattında DSC'ın rolünü anlama
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079854"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="383b4-103">CI/CD işlem hattında DSC'ın rolünü anlama</span><span class="sxs-lookup"><span data-stu-id="383b4-103">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="383b4-104">Bu makalede, yapılandırmaları ve kaynakları birleştirmek için kullanılabilen yaklaşımlardan türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="383b4-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="383b4-105">Her senaryo için hedef, birden fazla yapılandırması, bir sunucu dağıtımı bitiş durumuna ulaşmak için tercih edilen zaman karmaşıklığını azaltmak için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="383b4-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="383b4-106">Buna örnek olarak bir uygulama sahibi uygulama durumunu ve güvenlik temellerini değişiklikleri serbest merkezi bir ekip bakımını yapma gibi bir sunucu dağıtımı sonucunu merkezine katkı sağlayan birden çok takımı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="383b4-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="383b4-107">Her yaklaşımın avantajları ve risklerinin dahil olmak üzere küçük farklar aşağıda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="383b4-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![İşlem hattı](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="383b4-109">İşbirliğine dayalı geliştirme teknikleri türleri</span><span class="sxs-lookup"><span data-stu-id="383b4-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="383b4-110">Bu kavramı etkinleştirmek için yerel Configuration Manager için yerleşik iki çözümü vardır:</span><span class="sxs-lookup"><span data-stu-id="383b4-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="383b4-111">Kavram</span><span class="sxs-lookup"><span data-stu-id="383b4-111">Concept</span></span> | <span data-ttu-id="383b4-112">Ayrıntılı bilgi</span><span class="sxs-lookup"><span data-stu-id="383b4-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="383b4-113">Kısmi Yapılandırmalar</span><span class="sxs-lookup"><span data-stu-id="383b4-113">Partial Configurations</span></span> | [<span data-ttu-id="383b4-114">Belgeleri</span><span class="sxs-lookup"><span data-stu-id="383b4-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="383b4-115">Bileşik kaynaklar</span><span class="sxs-lookup"><span data-stu-id="383b4-115">Composite Resources</span></span> | [<span data-ttu-id="383b4-116">Belgeleri</span><span class="sxs-lookup"><span data-stu-id="383b4-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="383b4-117">Her bir yaklaşıma etkisini anlama</span><span class="sxs-lookup"><span data-stu-id="383b4-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="383b4-118">Bu çözümlerden birini, bir sunucu dağıtımı sonucunu yönetmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="383b4-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="383b4-119">Ancak, her bir yaklaşım kullanarak etkisini önemli fark yoktur.</span><span class="sxs-lookup"><span data-stu-id="383b4-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="383b4-120">Kısmi Yapılandırmalar</span><span class="sxs-lookup"><span data-stu-id="383b4-120">Partial Configurations</span></span>

<span data-ttu-id="383b4-121">Kısmi yapılandırmalar kullanırken, yerel Configuration Manager birden fazla yapılandırması bağımsız olarak yönetmek üzere yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="383b4-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="383b4-122">Yapılandırmaları bağımsız olarak derlenir ve ardından düğüme atanır.</span><span class="sxs-lookup"><span data-stu-id="383b4-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="383b4-123">Bu, her bir yapılandırma adı ile önceden yapılandırılmış olması için LCM'yi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="383b4-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="383b4-125">İki kısmi yapılandırmaları sağlamak ya da daha, takımlar üzerinde sık iletişim veya işbirliği avantajı olmadan bir sunucunun yapılandırmasını tam denetim.</span><span class="sxs-lookup"><span data-stu-id="383b4-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="383b4-126">Müşteriler bu kaynak çakışmaları, yanlışlıkla geçersiz kılmalar ve varlığın true yapılandırma denetim kaybı sonuçta açabilir geri bildirim sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="383b4-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="383b4-127">Ayrıca, müşteriler bu model kullanılırken, her denetimi takımlar yapılandırma değişikliklerini tam olarak bir yayın ardışık düzeni test olasılığının düşük olduğu bir geri bildirim üretimde beklenmeyen sonuçlar için önde gelen sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="383b4-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="383b4-128">**Tek bir işlem hattını sunucularına tüm değişiklikleri yayın değerlendirmek için kullanılması önemlidir.**</span><span class="sxs-lookup"><span data-stu-id="383b4-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="383b4-129">Aşağıdaki çizimde, B takımı takım A. takım bir kısmi yapılandırmalarını serbest bırakır ardından kendi çalıştırdığında uygulanan hem yapılandırmaları olan bir sunucuda yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="383b4-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="383b4-130">Bu modelde, yalnızca bir yetkili üretim ortamında değişiklik yapma iznine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="383b4-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="383b4-132">Değişiklikleri Team B'den gerekli olduğunda, bir çekme isteği takım A'ın kaynak denetimi ortamı karşı gönderin.</span><span class="sxs-lookup"><span data-stu-id="383b4-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="383b4-133">Bir takım test otomasyonu kullanarak değişiklikleri gözden geçirin ve değişiklikler uygulamaların veya sunucu tarafından barındırılan hizmetleri hataları açmayacağını güvenle olduğunda üretime sürüm.</span><span class="sxs-lookup"><span data-stu-id="383b4-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="383b4-134">Bileşik kaynaklar</span><span class="sxs-lookup"><span data-stu-id="383b4-134">Composite Resources</span></span>

<span data-ttu-id="383b4-135">Yalnızca bir kaynak olarak paketlenmiş DSC yapılandırma bir bileşik kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="383b4-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="383b4-136">Bileşik kaynakları kabul edecek şekilde LCM yapılandırma için özel gereksinimler yoktur.</span><span class="sxs-lookup"><span data-stu-id="383b4-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="383b4-137">Kaynaklar içinde yeni bir yapılandırma kullanılır ve tek bir derleme bir MOF dosyasında sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="383b4-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="383b4-139">Bileşik kaynaklar için iki yaygın senaryo vardır.</span><span class="sxs-lookup"><span data-stu-id="383b4-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="383b4-140">İlk karmaşıklığı ve soyut benzersiz kavramları azaltmaktır.</span><span class="sxs-lookup"><span data-stu-id="383b4-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="383b4-141">İkincisi, paketlenmiş bir uygulama ekipleri tüm testleri geçtikten sonra güvenli bir şekilde üretime, yayın ardışık düzeni üzerinden dağıtmak taban çizgileri izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="383b4-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="383b4-142">Bileşik kaynaklar hem oluşturma hem de işletimsel olgunluk oluşturulurken bir işlem hattı kullanarak işbirliği Yükselt</span><span class="sxs-lookup"><span data-stu-id="383b4-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="383b4-143">Zaten bileşik kaynakları fark etmeden kullanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="383b4-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="383b4-144">Bir örnek **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="383b4-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="383b4-145">Bu kaynak ayrı ayrı listelemek olmadan birden çok Windows hizmetlerinin durumunu yönetir.</span><span class="sxs-lookup"><span data-stu-id="383b4-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="383b4-146">Name özelliği, her hizmetin adını sağlamak için bir dize dizisi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="383b4-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="383b4-147">Yapılandırma derlendiğinde MOF ServiceSet için geçirilen adlarının her biri için benzersiz bir hizmet bölümü içerecektir.</span><span class="sxs-lookup"><span data-stu-id="383b4-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="383b4-148">Kuruluşların "Aracısı" veya "her sunucuya yüklenmesi ara yazılımı" olabilir.</span><span class="sxs-lookup"><span data-stu-id="383b4-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="383b4-149">Bağımlılıklar, Kurulum ve bu araçlar ve yardımcı programlar yapılandırmasını yönetmek için en iyi cevabı buna bileşik bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="383b4-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="383b4-150">Kişi veya birden çok sunucu uzanan çözümler için sorumlu ekip gereksinimlerine içeren bir yapılandırma yazar.</span><span class="sxs-lookup"><span data-stu-id="383b4-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="383b4-151">Ardından, yapılandırmayı bileşik kaynak belgelerde sağlanan yönergeleri kullanarak bir bileşik kaynak paketlenmesi.</span><span class="sxs-lookup"><span data-stu-id="383b4-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="383b4-152">Son olarak, bir dosya paylaşımı gibi bir konuma yeni bileşik kaynak yayımlanan veya burada uygulama ekipleri akışı NuGet yapılandırmalarında kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="383b4-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="383b4-153">Yeni bir sürüm takım sürümleri her zaman kendi bileşik kaynak için modül bildirimindeki sürüm numarasını artırmanız.</span><span class="sxs-lookup"><span data-stu-id="383b4-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="383b4-154">Uygulama ekipleri, uygulama bağımlılıkları yönetmek için yazar yapılandırmasında bileşik kaynak içerir.</span><span class="sxs-lookup"><span data-stu-id="383b4-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="383b4-155">İşlem/güvenlik takımlar yeni bir sürümü, kaynak serbest bıraktığınızda, bunlar yeni bir değişiklik uygulama ekipleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="383b4-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="383b4-156">Uygulama ekipleri, burada taban çizgisine göre tek değişiklik, üretim sürümü tetikleyebilir.</span><span class="sxs-lookup"><span data-stu-id="383b4-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="383b4-157">Ancak, bu uygulamaları bir hizmet kesintisi riskini önce etkisini değerlendirmek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="383b4-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="383b4-158">Not - bileşik kaynaklar kullanımına ilişkin geri bildirim, değişiklik yapmadan derleme ve yeni bir MOF serbest gerektirdiğini eleştirilere eklemiştir.</span><span class="sxs-lookup"><span data-stu-id="383b4-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="383b4-159">Bu tasarım gereğidir.</span><span class="sxs-lookup"><span data-stu-id="383b4-159">This is by design.</span></span>
<span data-ttu-id="383b4-160">Her yeni yapılandırma sürüm, her bir kaynağın belirli bir sürümünü statik bir başvuru içermelidir ve üretim sunucusu düğümleri ulaşmadan önce testler tarafından doğrulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="383b4-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="383b4-161">Test ve kaynak denetiminden değişiklikleri serbest bırakma işlemi, değişiklik küçük ancak sık toplu serbest bırakmak için güvenli bir ortam oluşturur.</span><span class="sxs-lookup"><span data-stu-id="383b4-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="383b4-162">Teknik incelemeyi yayın işlem hatları, çekirdek altyapıyı yönetmek için kullanma hakkında daha fazla bilgi için bkz: [Yayın işlem hattı modelini](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="383b4-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
