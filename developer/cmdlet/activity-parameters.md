---
title: Etkinlik parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849094"
---
# <a name="activity-parameters"></a><span data-ttu-id="58c4c-102">Etkinlik Parametreleri</span><span class="sxs-lookup"><span data-stu-id="58c4c-102">Activity Parameters</span></span>

<span data-ttu-id="58c4c-103">Aşağıdaki tabloda, etkinlik parametreleri için işlevselliği ve önerilen adlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="58c4c-103">The following table lists the recommended names and functionality for activity parameters.</span></span>

<span data-ttu-id="58c4c-104">Veri türü ekleyin: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-104">Append Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-105">Parametresi belirtildiğinde kullanıcı içerik kaynak sonuna ekleyebilirsiniz, böylece bu parametre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-105">Implement this parameter so that the user can add content to the end of a resource when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-106">CaseSensitive veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-106">CaseSensitive Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-107">Parametresi belirtildiğinde kullanıcı büyük/küçük harfe duyarlılık gerektirebilir için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-107">Implement this parameter so the user can require case sensitivity when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-108">Komut veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="58c4c-108">Command Data type: String</span></span>

<span data-ttu-id="58c4c-109">Kullanıcı çalıştırılacak bir komut dizesi belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-109">Implement this parameter so the user can specify a command string to run.</span></span>

<span data-ttu-id="58c4c-110">CompatibleVersion veri türü: System.Version nesnesi</span><span class="sxs-lookup"><span data-stu-id="58c4c-110">CompatibleVersion Data type: System.Version object</span></span>

<span data-ttu-id="58c4c-111">Cmdlet'i önceki sürümleriyle uyumluluk için ile uyumlu olması gereken semantiği kullanıcı belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-111">Implement this parameter so the user can specify the semantics that the cmdlet must be compatible with for compatibility with previous versions.</span></span>

<span data-ttu-id="58c4c-112">Veri türü sıkıştırma: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-112">Compress Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-113">Parametresi belirtildiğinde veri sıkıştırma kullanılmasını sağlamak amacıyla, bu parametre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-113">Implement this parameter so that data compression is used when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-114">Veri türü sıkıştırma: Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="58c4c-114">Compress Data type: Keyword</span></span>

<span data-ttu-id="58c4c-115">Kullanıcı veri sıkıştırma için kullanılacak algoritmasını belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-115">Implement this parameter so that the user can specify the algorithm to use for data compression.</span></span>

<span data-ttu-id="58c4c-116">Sürekli veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-116">Continuous Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-117">Bu parametre, kullanıcının cmdlet kapsayıcınızın parametresi belirtildiğinde veriler işlenir böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-117">Implement this parameter so that data is processed until the user terminates the cmdlet when the parameter is specified.</span></span> <span data-ttu-id="58c4c-118">Parametre belirtilmezse, cmdlet önceden tanımlanmış bir miktarda veri işler ve sonra da işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="58c4c-118">If the parameter is not specified, the cmdlet processes a predefined amount of data and then terminates the operation.</span></span>

<span data-ttu-id="58c4c-119">Veri türü oluşturun: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-119">Create Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-120">Parametresi belirtildiğinde bir zaten mevcut değilse bir kaynak oluşturulduğunu belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-120">Implement this parameter to indicate that a resource is created if one does not already exist when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-121">Veri türü silin: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-121">Delete Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-122">Cmdlet parametresi belirtildiğinde kendi işlemi tamamlandığında, kaynaklar silinir, bu parametre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-122">Implement this parameter so that resources are deleted when the cmdlet has completed its operation when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-123">Veri türü Boşalt: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-123">Drain Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-124">Parametresi belirtildiğinde cmdlet yeni veri işlemeden önce bekleyen iş öğeleri işlenir belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-124">Implement this parameter to indicate that outstanding work items are processed before the cmdlet processes new data when the parameter is specified.</span></span> <span data-ttu-id="58c4c-125">Parametre belirtilmezse, iş öğelerinin hemen işlenir.</span><span class="sxs-lookup"><span data-stu-id="58c4c-125">If the parameter is not specified, the work items are processed immediately.</span></span>

<span data-ttu-id="58c4c-126">Veri türü sil: Int32</span><span class="sxs-lookup"><span data-stu-id="58c4c-126">Erase Data type: Int32</span></span>

<span data-ttu-id="58c4c-127">Bu parametre, kullanıcının kaç kez silinmeden önce bir kaynak silinir belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-127">Implement this parameter so that the user can specify the number of times a resource is erased before it is deleted.</span></span>

<span data-ttu-id="58c4c-128">ErrorLevel veri türü: Int32</span><span class="sxs-lookup"><span data-stu-id="58c4c-128">ErrorLevel Data type: Int32</span></span>

<span data-ttu-id="58c4c-129">Kullanıcı raporuna hatalarının düzeyini belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-129">Implement this parameter so that the user can specify the level of errors to report.</span></span>

<span data-ttu-id="58c4c-130">Veri türü hariç tut: String[]</span><span class="sxs-lookup"><span data-stu-id="58c4c-130">Exclude Data type: String[]</span></span>

<span data-ttu-id="58c4c-131">Bu parametre, böylece kullanıcı etkinliği bir şey hariç tutabilirsiniz uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-131">Implement this parameter so that the user can exclude something from an activity.</span></span> <span data-ttu-id="58c4c-132">Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="58c4c-132">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="58c4c-133">Filtre veri türü: Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="58c4c-133">Filter Data type: Keyword</span></span>

<span data-ttu-id="58c4c-134">Bu parametre, kullanıcının cmdlet'i eylemi gerçekleştirmek bağlı kaynaklar seçen bir filtre belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-134">Implement this parameter so that the user can specify a filter that selects the resources upon which to perform the cmdlet action.</span></span> <span data-ttu-id="58c4c-135">Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="58c4c-135">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="58c4c-136">Veri türü izleyin: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-136">Follow Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-137">Bu parametre, böylece parametresi belirtildiğinde ilerleme izlenir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-137">Implement this parameter so that progress is tracked when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-138">Zorlama veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-138">Force Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-139">Parametresi belirtildiğinde kısıtlamaları karşılaşılan olsa bile bir eylem kullanıcının gerçekleştirebileceği belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-139">Implement this parameter to indicate that the user can perform an action even if restrictions are encountered when the parameter is specified.</span></span> <span data-ttu-id="58c4c-140">Parametresi, güvenliği tehlikeye izin vermez.</span><span class="sxs-lookup"><span data-stu-id="58c4c-140">The parameter does not allow security to be compromised.</span></span> <span data-ttu-id="58c4c-141">Örneğin, bu parametre, salt okunur dosyanın üzerine bir kullanıcı olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="58c4c-141">For example, this parameter lets a user overwrite a read-only file.</span></span>

<span data-ttu-id="58c4c-142">Veri türü şunlardır: String[]</span><span class="sxs-lookup"><span data-stu-id="58c4c-142">Include Data type: String[]</span></span>

<span data-ttu-id="58c4c-143">Bu parametre, böylece kullanıcı bir şey bir etkinlik içerebilir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-143">Implement this parameter so that the user can include something in an activity.</span></span> <span data-ttu-id="58c4c-144">Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="58c4c-144">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="58c4c-145">Artımlı veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-145">Incremental Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-146">Parametresi belirtildiğinde işleme artımlı olarak gerçekleştirildiğini belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-146">Implement this parameter to indicate that processing is performed incrementally when the parameter is specified.</span></span> <span data-ttu-id="58c4c-147">Örneğin, bu parametre yalnızca son yedeklemeden bu yana dosyaları yedekleme artımlı yedeklemeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="58c4c-147">For example, this parameter lets a user perform incremental backups that back up files only since the last backup.</span></span>

<span data-ttu-id="58c4c-148">Inputobject veri türü: Nesne</span><span class="sxs-lookup"><span data-stu-id="58c4c-148">InputObject Data type: Object</span></span>

<span data-ttu-id="58c4c-149">Bu parametre, cmdlet diğer cmdlet'lerinden giriş aldığı durumlarda uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-149">Implement this parameter when the cmdlet takes input from other cmdlets.</span></span> <span data-ttu-id="58c4c-150">Tanımladığınızda bir `InputObject` parametresi her zaman belirtin `ValueFromPipeline` bildirdiğinizde, anahtar sözcüğü **parametre** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="58c4c-150">When you define an `InputObject` parameter, always specify the `ValueFromPipeline` keyword when you declare the **Parameter** attribute.</span></span> <span data-ttu-id="58c4c-151">Giriş filtrelerini kullanma hakkında daha fazla bilgi için bkz. [filtre parametrelerini](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="58c4c-151">For more information about using input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="58c4c-152">Veri türü ekleyin: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-152">Insert Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-153">Parametresi belirtildiğinde cmdlet, bir öğe ekler. Bu parametre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-153">Implement this parameter so that the cmdlet inserts an item when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-154">Etkileşimli veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-154">Interactive Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-155">Parametresi belirtildiğinde kullanıcıyla cmdlet'i etkileşimli olarak çalışır. böylece, bu parametre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-155">Implement this parameter so that the cmdlet works interactively with the user when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-156">Aralık veri türü: HashTable</span><span class="sxs-lookup"><span data-stu-id="58c4c-156">Interval Data type: HashTable</span></span>

<span data-ttu-id="58c4c-157">Bu parametre değerleri içeren bir karma tablo anahtar sözcüklerin kullanıcı belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-157">Implement this parameter so that the user can specify a hash table of keywords that contains the values.</span></span> <span data-ttu-id="58c4c-158">Örnek değerler için aşağıdaki örnekte `Interval` parametresi: `-interval @{ResumeScan=15; Retry=3}`.</span><span class="sxs-lookup"><span data-stu-id="58c4c-158">The following example shows sample values for the `Interval` parameter: `-interval @{ResumeScan=15; Retry=3}`.</span></span>

<span data-ttu-id="58c4c-159">Günlük veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-159">Log Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-160">Parametresi belirtildiğinde bu parametre denetimi cmdlet'inin eylemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-160">Implement this parameter audit the actions of the cmdlet when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-161">NoClobber veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-161">NoClobber Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-162">Bu parametre, böylece parametresi belirtildiğinde kaynağın üzerine yazılmaz uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-162">Implement this parameter so that the resource will not be overwritten when the parameter is specified.</span></span> <span data-ttu-id="58c4c-163">Bu parametre, genellikle yeni nesneler oluşturabilir ve böylece aynı ada sahip mevcut nesnelerin üzerine yazılmasını engellenebilir cmdlet'leri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="58c4c-163">This parameter generally applies to cmdlets that create new objects so that they can be prevented from overwriting existing objects with the same name.</span></span>

<span data-ttu-id="58c4c-164">Veri türü bildirmek: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-164">Notify Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-165">Bu parametre, böylece kullanıcı parametresi belirtildiğinde etkinlik tamamlandıktan bildirilir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-165">Implement this parameter so that the user will be notified that the activity is complete when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-166">NotifyAddress veri türü: E-posta adresi</span><span class="sxs-lookup"><span data-stu-id="58c4c-166">NotifyAddress Data type: E-mail address</span></span>

<span data-ttu-id="58c4c-167">Kullanıcı bildirim göndermek için kullanılacak e-posta adresini belirtmek için bu parametreyi uygulamak, `Notify` parametre belirtildi.</span><span class="sxs-lookup"><span data-stu-id="58c4c-167">Implement this parameter so that the user can specify the e-mail address to use to send a notification when the `Notify` parameter is specified.</span></span>

<span data-ttu-id="58c4c-168">Veri türü üzerine yaz: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-168">Overwrite Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-169">Bu parametre, böylece parametresi belirtildiğinde cmdlet tüm mevcut verilerin üzerine yazar uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-169">Implement this parameter so that the cmdlet overwrites any existing data when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-170">Komut istemi veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="58c4c-170">Prompt Data type: String</span></span>

<span data-ttu-id="58c4c-171">Bu parametre, kullanıcının cmdlet için bir istem belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-171">Implement this parameter so that the user can specify a prompt for the cmdlet.</span></span>

<span data-ttu-id="58c4c-172">Sessiz veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-172">Quiet Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-173">Cmdlet parametresi belirtildiğinde kullanıcı geri bildirim sırasında eylemlerini engeller. Bu parametre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-173">Implement this parameter so that the cmdlet suppresses user feedback during its actions when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-174">Veri türü recurse: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-174">Recurse Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-175">Parametresi belirtildiğinde cmdlet yinelemeli olarak eylemlerini kaynaklardaki gerçekleştirir. böylece, bu parametre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-175">Implement this parameter so that the cmdlet recursively performs its actions on resources when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-176">Onarım veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-176">Repair Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-177">Bu parametre, böylece cmdlet parametresi belirtildiğinde bir şey bozuk durumdan düzeltmek dener uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-177">Implement this parameter so that the cmdlet will attempt to correct something from a broken state when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-178">RepairString veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="58c4c-178">RepairString Data type: String</span></span>

<span data-ttu-id="58c4c-179">Kullanıcı bir dize ne zaman kullanılacağını belirtmek için bu parametreyi uygulamak `Repair` parametre belirtildi.</span><span class="sxs-lookup"><span data-stu-id="58c4c-179">Implement this parameter so that the user can specify a string to use when the `Repair` parameter is specified.</span></span>

<span data-ttu-id="58c4c-180">Veri türü yeniden deneme: Int32</span><span class="sxs-lookup"><span data-stu-id="58c4c-180">Retry Data type: Int32</span></span>

<span data-ttu-id="58c4c-181">Kullanıcı bir eylem cmdlet çalışacağı deneme sayısını belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-181">Implement this parameter so the user can specify the number of times the cmdlet will attempt an action.</span></span>

<span data-ttu-id="58c4c-182">Veri türünü seçin: Anahtar sözcük dizisi</span><span class="sxs-lookup"><span data-stu-id="58c4c-182">Select Data type: Keyword array</span></span>

<span data-ttu-id="58c4c-183">Kullanıcının bir dizi öğelerinin türlerini belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-183">Implement this parameter so that the user can specify an array of the types of items.</span></span>

<span data-ttu-id="58c4c-184">Stream veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-184">Stream Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-185">Bu parametre, parametre belirtildiğinde birden çok çıkış nesnelerini ardışık düzeninden kullanıcı akışını şekilde uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-185">Implement this parameter so the user can stream multiple output objects through the pipeline when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-186">Katı veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-186">Strict Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-187">Bu parametre, böylece parametresi belirtildiğinde tüm hataları sonlandıran hatalar olarak işlenmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-187">Implement this parameter so that all errors are handled as terminating errors when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-188">TempLocation veri türü: Dize</span><span class="sxs-lookup"><span data-stu-id="58c4c-188">TempLocation Data type: String</span></span>

<span data-ttu-id="58c4c-189">Kullanıcı cmdlet'inin işlemi sırasında kullanılan geçici veri konumunu belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-189">Implement this parameter so the user can specify the location of temporary data that is used during the operation of the cmdlet.</span></span>

<span data-ttu-id="58c4c-190">Zaman aşımı veri türü: Int32</span><span class="sxs-lookup"><span data-stu-id="58c4c-190">Timeout Data type: Int32</span></span>

<span data-ttu-id="58c4c-191">Bu parametre, kullanıcının zaman aşımı aralığı (milisaniye cinsinden) belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-191">Implement this parameter so that the user can specify the timeout interval (in milliseconds).</span></span>

<span data-ttu-id="58c4c-192">Veri türü kesin: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-192">Truncate Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-193">Bu parametre, böylece parametresi belirtildiğinde cmdlet eylemlerini kısaltabilir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-193">Implement this parameter so that the cmdlet will truncate its actions when the parameter is specified.</span></span> <span data-ttu-id="58c4c-194">Bu parametre belirtilmemişse cmdlet başka bir eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="58c4c-194">If the parameter is not specified, the cmdlet performs another action.</span></span>

<span data-ttu-id="58c4c-195">Veri türünü doğrulayın: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-195">Verify Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-196">Cmdlet parametresi belirtildiğinde bir eylem oluşup oluşmadığını belirlemek için test edecek, bu parametre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-196">Implement this parameter so that the cmdlet will test to determine whether an action has occurred when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-197">Veri türü bekleyin: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="58c4c-197">Wait Data type: SwitchParameter</span></span>

<span data-ttu-id="58c4c-198">Bu parametre, cmdlet parametresi belirtildiğinde devam etmeden önce kullanıcı girişi beklemesi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="58c4c-198">Implement this parameter so that the cmdlet will wait for user input before continuing when the parameter is specified.</span></span>

<span data-ttu-id="58c4c-199">WaitTime veri türü: Int32</span><span class="sxs-lookup"><span data-stu-id="58c4c-199">WaitTime Data type: Int32</span></span>

<span data-ttu-id="58c4c-200">Kullanıcı Süresi (saniye cinsinden) belirtmek için bu parametreyi uygulamak cmdlet için kullanıcı bekler, giriş ne zaman `Wait` parametre belirtildi.</span><span class="sxs-lookup"><span data-stu-id="58c4c-200">Implement this parameter so that the user can specify the duration (in seconds) that the cmdlet will wait for user input when the `Wait` parameter is specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="58c4c-201">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="58c4c-201">See Also</span></span>

[<span data-ttu-id="58c4c-202">Cmdlet parametreleri</span><span class="sxs-lookup"><span data-stu-id="58c4c-202">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="58c4c-203">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="58c4c-203">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="58c4c-204">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="58c4c-204">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
