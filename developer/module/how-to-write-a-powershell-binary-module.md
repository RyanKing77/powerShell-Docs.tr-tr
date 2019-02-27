---
title: Bir ikili PowerShell modülü yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847155"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="7de5d-102">PowerShell İkili Modülü Yazma</span><span class="sxs-lookup"><span data-stu-id="7de5d-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="7de5d-103">İkili bir modül, cmdlet sınıfları içeren herhangi bir derleme (.dll) olabilir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="7de5d-104">İkili modül içeri aktarıldığında varsayılan olarak derleme içindeki tüm cmdlet'ler içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="7de5d-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="7de5d-105">Ancak, kök derleme modülüdür bir modül bildirimi oluşturarak içeri aktarılan cmdlet'ler kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7de5d-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="7de5d-106">(Örneğin, bildirimin CmdletsToExport anahtarı gerekli cmdlet'leri dışarı aktarmak için kullanılabilir.) Ayrıca, bir ikili modül ek dosyalar, bir dizin yapısına ve diğer yararlı yönetim bilgilerine tek bir cmdlet yükleyemediği parçalarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="7de5d-107">Aşağıdaki yordam, oluşturma ve ikili bir PowerShell modülü yükleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="7de5d-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="7de5d-108">Oluşturma ve PowerShell ikili modülünü yükleme</span><span class="sxs-lookup"><span data-stu-id="7de5d-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="7de5d-109">İkili bir PowerShell çözümü oluşturun (yazılan bir cmdlet gibi C#), özellikleriyle gerekir ve düzgün çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="7de5d-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="7de5d-110">Kod açısından bakıldığında, ikili bir modülün çekirdek sadece bir cmdlet derlemesidir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="7de5d-111">Aslında, PowerShell cmdlet'i tek bir bütünleştirilmiş kod yükleme ve kaldırma ile Geliştirici tarafında ek çaba açısından bir modül olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="7de5d-112">Bir cmdlet yazma hakkında daha fazla bilgi için bkz. [yazma bir Windows PowerShell cmdlet'i](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="7de5d-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="7de5d-113">Gerekirse, çözümünüzün rest oluşturun: (ek cmdlet'leri, XML dosyaları vb.) ve bunları bir modül bildirimi ile açıklar.</span><span class="sxs-lookup"><span data-stu-id="7de5d-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="7de5d-114">Çözümünüzü cmdlet'i derlemelerde açıklayan ek olarak, bir modül bildirimi dışarı ve içeri aktarılan modülünüzde istediğiniz, hangi cmdlet'leri sunulur ve ek dosyaları ne modüle geçer tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7de5d-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span> <span data-ttu-id="7de5d-115">Ancak daha önce belirtildiği gibi PowerShell gibi ek çaba sahip bir modül ikili bir cmdlet davranabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7de5d-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span> <span data-ttu-id="7de5d-116">Bu nedenle, bir modül bildirimi çoğunlukla birden çok dosyayı tek bir paket birleştirmek için veya belirli bir derleme için yayın açıkça denetlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7de5d-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span> <span data-ttu-id="7de5d-117">Daha fazla bilgi için [bildirim PowerShell modülü yazma](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span><span class="sxs-lookup"><span data-stu-id="7de5d-117">For more information, see [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

   <span data-ttu-id="7de5d-118">Aşağıdaki kod bir son derece basittir C# aynı dosyada bir modül olarak kullanılabilecek üç cmdlet'leri içeren bir kod bloğu.</span><span class="sxs-lookup"><span data-stu-id="7de5d-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="7de5d-119">Çözümünüzü paketini ve paket için bir yere kaydedin PowerShell modülü yolda.</span><span class="sxs-lookup"><span data-stu-id="7de5d-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="7de5d-120">`PSModulePath` Genel ortam değişkeni PowerShell modülünüzde bulmak için kullanacağı varsayılan yollarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7de5d-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="7de5d-121">Örneğin, bir sistemde bir modüle kaydetmek için yaygın bir yolu olabilir `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="7de5d-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="7de5d-122">Varsayılan yolları kullanmıyorsanız, modülünüzün konumu yükleme sırasında açıkça durum gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="7de5d-123">Birden çok derlemeleri ve çözümünüz için dosyaları depolamak için klasör gerekebilir, modülünüzde kaydedileceği klasörü oluşturmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="7de5d-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="7de5d-124">Teknik olarak, modülünüzün herhangi bir yere yüklemek ihtiyacınız yoktur, Not `PSModulePath` -yalnızca PowerShell modülünüzde için görüneceğini varsayılan konumları olanlardır.</span><span class="sxs-lookup"><span data-stu-id="7de5d-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="7de5d-125">Ancak, modülünüzde başka bir yerde depolanması için geçerli bir nedeniniz yoksa, bunu yapmak için en iyi kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="7de5d-126">Daha fazla bilgi için [PowerShell modülünü yükleme](./installing-a-powershell-module.md) ve [PowerShell modülü yükleme yolunu değiştirmek](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="7de5d-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="7de5d-127">Bir çağrı ile PowerShell içinde modülü içeri [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="7de5d-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="7de5d-128">İçin çağırma [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) modülünüzde etkin belleğe yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="7de5d-129">PowerShell 3.0 kullanıyorsanız ve daha sonra kodda çağrısı yaparak modülünüzün adını da alma işlemi Daha fazla bilgi için [PowerShell modülünü içeri aktararak](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="7de5d-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="7de5d-130">Ek derlemeler modül içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="7de5d-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="7de5d-131">Cmdlet'leri ve ek bileşenini derlemeleri yok sağlayıcıları, ikili modülleri olarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="7de5d-132">Ek derlemeler ikili modülleri yüklü olduğunda, cmdlet'leri ve sağlayıcıları ek bileşeninde kullanıcıya kullanılabilir ancak ek bileşenini derlemede sınıfı, göz ardı edilir ve ek bileşenini kayıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="7de5d-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="7de5d-133">Sonuç olarak, cmdlet'leri ve sağlayıcıları oturuma kullanılabilir olsa bile ek bileşenini Windows PowerShell tarafından sağlanan ek bileşenini cmdlet'leri algılayamaz.</span><span class="sxs-lookup"><span data-stu-id="7de5d-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="7de5d-134">Ayrıca, eklenti tarafından başvurulan türleri biçimlendirme veya dosyaları ikili bir modülün bir parçası olarak içeri aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="7de5d-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span> <span data-ttu-id="7de5d-135">Biçimlendirme ve türleri dosyalarını içeri aktarmak için bir modül bildirimi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7de5d-135">To import the formatting and types files you must create a module manifest.</span></span> <span data-ttu-id="7de5d-136">Bkz, [nasıl yazılacağını bir PowerShell modülü bildirim](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span><span class="sxs-lookup"><span data-stu-id="7de5d-136">See, [How to Write a PowerShell Module Manifest](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).</span></span>

## <a name="see-also"></a><span data-ttu-id="7de5d-137">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7de5d-137">See Also</span></span>

[<span data-ttu-id="7de5d-138">Bir Windows PowerShell modülü yazma</span><span class="sxs-lookup"><span data-stu-id="7de5d-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
