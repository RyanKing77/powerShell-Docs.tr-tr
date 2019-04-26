---
title: Danışmanlık geliştirme yönergeleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 871a74a084da3c7ec36767b7195461e0e7290cb9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068802"
---
# <a name="advisory-development-guidelines"></a><span data-ttu-id="4696d-102">Tavsiye Niteliğinde Geliştirme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4696d-102">Advisory Development Guidelines</span></span>

<span data-ttu-id="4696d-103">Bu bölümde, iyi geliştirme ve kullanıcı deneyimleri sağlamak için dikkate almanız yönergeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4696d-103">This section describes guidelines that you should consider to ensure good development and user experiences.</span></span> <span data-ttu-id="4696d-104">Bazen uygulanabilir ve bazen olabilir değil.</span><span class="sxs-lookup"><span data-stu-id="4696d-104">Sometimes they might apply, and sometimes they might not.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="4696d-105">Tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4696d-105">Design Guidelines</span></span>

- [<span data-ttu-id="4696d-106">Bir Inputobject parametresi (AD01) desteği</span><span class="sxs-lookup"><span data-stu-id="4696d-106">Support an InputObject Parameter (AD01)</span></span>](./advisory-development-guidelines.md#AD01)

- [<span data-ttu-id="4696d-107">Force parametresini (AD02) desteği</span><span class="sxs-lookup"><span data-stu-id="4696d-107">Support the Force Parameter (AD02)</span></span>](./advisory-development-guidelines.md#AD02)

- [<span data-ttu-id="4696d-108">Windows PowerShell (AD03) üzerinden kimlik bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="4696d-108">Handle Credentials Through Windows PowerShell (AD03)</span></span>](./advisory-development-guidelines.md#AD03)

- [<span data-ttu-id="4696d-109">Kodlama parametreler (AD04) desteği</span><span class="sxs-lookup"><span data-stu-id="4696d-109">Support Encoding Parameters (AD04)</span></span>](./advisory-development-guidelines.md#AD04)

- [<span data-ttu-id="4696d-110">Sınama cmdlet'lerini bir Boole değeri (AD05) döndürmelidir</span><span class="sxs-lookup"><span data-stu-id="4696d-110">Test Cmdlets Should Return a Boolean (AD05)</span></span>](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a><span data-ttu-id="4696d-111">Kod kuralları</span><span class="sxs-lookup"><span data-stu-id="4696d-111">Code Guidelines</span></span>

- [<span data-ttu-id="4696d-112">Cmdlet'i sınıf adlandırma kuralları (AC01) izleyin</span><span class="sxs-lookup"><span data-stu-id="4696d-112">Follow Cmdlet Class Naming Conventions (AC01)</span></span>](./advisory-development-guidelines.md#AC01)

- [<span data-ttu-id="4696d-113">Herhangi bir işlem hattı giriş (AC02) BeginProcessing yöntemi geçersiz kılarsanız</span><span class="sxs-lookup"><span data-stu-id="4696d-113">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>](./advisory-development-guidelines.md#AC02)

- [<span data-ttu-id="4696d-114">Durdurma istekleri işlemek için (AC03) StopProcessing yöntemi geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="4696d-114">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>](./advisory-development-guidelines.md#AC03)

- [<span data-ttu-id="4696d-115">(AC04) IDisposable arayüzünü uygular</span><span class="sxs-lookup"><span data-stu-id="4696d-115">Implement the IDisposable Interface (AC04)</span></span>](./advisory-development-guidelines.md#AC04)

- [<span data-ttu-id="4696d-116">Serileştirme uyumlu parametre türleri (AC05) kullanın</span><span class="sxs-lookup"><span data-stu-id="4696d-116">Use Serialization-friendly Parameter Types (AC05)</span></span>](./advisory-development-guidelines.md#AC05)

- [<span data-ttu-id="4696d-117">Hassas verileri (AC06) SecureString kullanın</span><span class="sxs-lookup"><span data-stu-id="4696d-117">Use SecureString for Sensitive Data (AC06)</span></span>](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a><span data-ttu-id="4696d-118">Tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4696d-118">Design Guidelines</span></span>

<span data-ttu-id="4696d-119">Cmdlet'leri tasarlarken aşağıdaki yönergeleri dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4696d-119">The following guidelines should be considered when designing cmdlets.</span></span> <span data-ttu-id="4696d-120">Durumunuza bir tasarım kılavuzu bulduğunuzda, benzer yönergeleri için kod yönergelere bakmak emin olun.</span><span class="sxs-lookup"><span data-stu-id="4696d-120">When you find a Design guideline that applies to your situation, be sure to look at the Code guidelines for similar guidelines.</span></span>

### <a name="support-an-inputobject-parameter-ad01"></a><span data-ttu-id="4696d-121">Bir Inputobject parametresi (AD01) desteği</span><span class="sxs-lookup"><span data-stu-id="4696d-121">Support an InputObject Parameter (AD01)</span></span>

<span data-ttu-id="4696d-122">Windows PowerShell Microsoft .NET Framework nesneleri ile doğrudan çalıştığından, bir .NET Framework nesnesi genellikle tam olarak eşleşen kullanıcı türü gerekiyor belirli bir işlemi gerçekleştirip kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4696d-122">Because Windows PowerShell works directly with Microsoft .NET Framework objects, a .NET Framework object is often available that exactly matches the type the user needs to perform a particular operation.</span></span> <span data-ttu-id="4696d-123">`InputObject` Böyle bir nesnenin giriş olarak alan bir parametre için standart adıdır.</span><span class="sxs-lookup"><span data-stu-id="4696d-123">`InputObject` is the standard name for a parameter that takes such an object as input.</span></span> <span data-ttu-id="4696d-124">Örneğin, örnek **Stop-Proc** cmdlet'inde [StopProc öğretici](./stopproc-tutorial.md) tanımlayan bir `InputObject` ardışık düzendeki girişi destekleyen işlem türünde parametre.</span><span class="sxs-lookup"><span data-stu-id="4696d-124">For example, the sample **Stop-Proc** cmdlet in the [StopProc Tutorial](./stopproc-tutorial.md) defines an `InputObject` parameter of type Process that supports the input from the pipeline.</span></span> <span data-ttu-id="4696d-125">Kullanıcı işlem nesneleri kümesini almak, durdurmak için tam nesneleri seçmek için bunları yönetmek ve bunlara geçirmek **Stop-Proc** doğrudan cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="4696d-125">The user can get a set of process objects, manipulate them to select the exact objects to stop, and then pass them to the **Stop-Proc** cmdlet directly.</span></span>

### <a name="support-the-force-parameter-ad02"></a><span data-ttu-id="4696d-126">Force parametresini (AD02) desteği</span><span class="sxs-lookup"><span data-stu-id="4696d-126">Support the Force Parameter (AD02)</span></span>

<span data-ttu-id="4696d-127">Bazen, kullanıcının istenen işlemi gerçekleştirmemizi korumak bir cmdlet gerekir.</span><span class="sxs-lookup"><span data-stu-id="4696d-127">Occasionally, a cmdlet needs to protect the user from performing a requested operation.</span></span> <span data-ttu-id="4696d-128">Böyle bir cmdlet desteklemelidir bir `Force` kullanıcının işlemi gerçekleştirmek için izni olup olmadığını, korumayı geçersiz kılmak izin vermek için parametre.</span><span class="sxs-lookup"><span data-stu-id="4696d-128">Such a cmdlet should support a `Force` parameter to allow the user to override that protection if the user has permissions to perform the operation.</span></span>

<span data-ttu-id="4696d-129">Örneğin, [Kaldır öğesini](/powershell/module/microsoft.powershell.management/remove-item) cmdlet, salt okunur bir dosya normalde kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="4696d-129">For example, the [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet does not normally remove a read-only file.</span></span> <span data-ttu-id="4696d-130">Ancak, bu cmdlet destekleyen bir `Force` parametresi için bir kullanıcı bir salt okunur dosya kaldırılmasını zorlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4696d-130">However, this cmdlet supports a `Force` parameter so a user can force removal of a read-only file.</span></span> <span data-ttu-id="4696d-131">Kullanıcı salt okunur özniteliğini değiştirmek için izne zaten sahip ve kullanıcı dosyayı kaldırır, kullanım `Force` parametresi işlemi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="4696d-131">If the user already has permission to modify the read-only attribute, and the user removes the file, use of the `Force` parameter simplifies the operation.</span></span> <span data-ttu-id="4696d-132">Ancak, kullanıcının dosyayı silme iznine sahip değilse `Force` parametresi etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="4696d-132">However, if the user does not have permission to remove the file, the `Force` parameter has no effect.</span></span>

### <a name="handle-credentials-through-windows-powershell-ad03"></a><span data-ttu-id="4696d-133">Windows PowerShell (AD03) üzerinden kimlik bilgilerini işleme</span><span class="sxs-lookup"><span data-stu-id="4696d-133">Handle Credentials Through Windows PowerShell (AD03)</span></span>

<span data-ttu-id="4696d-134">Bir cmdlet tanımlamalıdır bir `Credential` kimlik bilgilerini temsil etmek için parametre.</span><span class="sxs-lookup"><span data-stu-id="4696d-134">A cmdlet should define a `Credential` parameter to represent credentials.</span></span> <span data-ttu-id="4696d-135">Bu parametre türü olmalıdır [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) ve bir kimlik bilgisi özniteliği bildirimi kullanılarak tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4696d-135">This parameter must be of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) and must be defined using a Credential attribute declaration.</span></span> <span data-ttu-id="4696d-136">Bu destek, otomatik olarak tam bir kimlik bilgisi doğrudan sağlanamadığında kullanıcının kullanıcı adı, parola veya her ikisi için de ister.</span><span class="sxs-lookup"><span data-stu-id="4696d-136">This support automatically prompts the user for the user name, for the password, or for both when a full credential is not supplied directly.</span></span> <span data-ttu-id="4696d-137">Kimlik bilgisi özniteliği hakkında daha fazla bilgi için bkz. [kimlik bilgisi öznitelik bildiriminin](./credential-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4696d-137">For more information about the Credential attribute, see [Credential Attribute Declaration](./credential-attribute-declaration.md).</span></span>

### <a name="support-encoding-parameters-ad04"></a><span data-ttu-id="4696d-138">Kodlama parametreler (AD04) desteği</span><span class="sxs-lookup"><span data-stu-id="4696d-138">Support Encoding Parameters (AD04)</span></span>

<span data-ttu-id="4696d-139">Cmdlet'inize okur ya da metin ya da bir dosya sistemi dosyasından okuma veya yazma gibi bir ikili biçimindeki Yazar cmdlet'inize nasıl metin ikili biçimde kodlandı belirten kodlama parametresi sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4696d-139">If your cmdlet reads or writes text to or from a binary form, such as writing to or reading from a file in a filesystem, then your cmdlet has to have Encoding parameter that specifies how the text is encoded in the binary form.</span></span>

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a><span data-ttu-id="4696d-140">Sınama cmdlet'lerini bir Boole değeri (AD05) döndürmelidir</span><span class="sxs-lookup"><span data-stu-id="4696d-140">Test Cmdlets Should Return a Boolean (AD05)</span></span>

<span data-ttu-id="4696d-141">Testleri kendi kaynaklara karşı gerçekleştirdiğiniz cmdlet'leri döndürmelidir bir [System.Boolean](/dotnet/api/System.Boolean) koşullu ifadelerde kullanılabilir olacak şekilde işlem hattının yazın.</span><span class="sxs-lookup"><span data-stu-id="4696d-141">Cmdlets that perform tests against their resources should return a [System.Boolean](/dotnet/api/System.Boolean) type to the pipeline so that they can be used in conditional expressions.</span></span>

## <a name="code-guidelines"></a><span data-ttu-id="4696d-142">Kod kuralları</span><span class="sxs-lookup"><span data-stu-id="4696d-142">Code Guidelines</span></span>

<span data-ttu-id="4696d-143">Cmdlet'i kodu yazarken aşağıdaki kılavuzları dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4696d-143">The following guidelines should be considered when writing cmdlet code.</span></span> <span data-ttu-id="4696d-144">Durumunuza bir kılavuz bulduğunuzda, benzer yönergeleri için tasarım kılavuzlarına bakın emin olun.</span><span class="sxs-lookup"><span data-stu-id="4696d-144">When you find a guideline that applies to your situation, be sure to look at the Design guidelines for similar guidelines.</span></span>

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a><span data-ttu-id="4696d-145">Cmdlet'i sınıf adlandırma kuralları (AC01) izleyin</span><span class="sxs-lookup"><span data-stu-id="4696d-145">Follow Cmdlet Class Naming Conventions (AC01)</span></span>

<span data-ttu-id="4696d-146">Aşağıdaki standart adlandırma kuralları cmdlet'lerinizi keşfedilmesini kolaylaştırın ve cmdlet'leri tam olarak ne anlama kullanıcı Yardımı.</span><span class="sxs-lookup"><span data-stu-id="4696d-146">By following standard naming conventions, you make your cmdlets more discoverable, and you help the user understand exactly what the cmdlets do.</span></span> <span data-ttu-id="4696d-147">Bu yöntem Windows PowerShell cmdlet'leri genel türleri olduğundan kullanarak diğer geliştiriciler için özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4696d-147">This practice is particularly important for other developers using Windows PowerShell because cmdlets are public types.</span></span>

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a><span data-ttu-id="4696d-148">Bir Cmdlet doğru Namespace tanımlayın</span><span class="sxs-lookup"><span data-stu-id="4696d-148">Define a Cmdlet in the Correct Namespace</span></span>

<span data-ttu-id="4696d-149">Ekler bir .NET Framework ad alanında normalde bir cmdlet için bir sınıf tanımlama ". Komutları"cmdlet'in çalıştığı bir ürünü temsil ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4696d-149">You normally define the class for a cmdlet in a .NET Framework namespace that appends ".Commands" to the namespace that represents the product in which the cmdlet runs.</span></span> <span data-ttu-id="4696d-150">Örneğin, Windows PowerShell ile dahil edilen cmdlet'ler içinde tanımlı `Microsoft.PowerShell.Commands` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4696d-150">For example, cmdlets that are included with Windows PowerShell are defined in the `Microsoft.PowerShell.Commands` namespace.</span></span>

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a><span data-ttu-id="4696d-151">Cmdlet adı ile eşleşmesi için bu cmdlet'i sınıfı adı</span><span class="sxs-lookup"><span data-stu-id="4696d-151">Name the Cmdlet Class to Match the Cmdlet Name</span></span>

<span data-ttu-id="4696d-152">Bir cmdlet uygulayan .NET Framework sınıf adı, sınıf adını "*\<fiil >**\<isim >**\<komut >*" değiştirinburada *\<Fiil >* ve  *\<isim >* fiil ve isim cmdlet adı için kullanılan, yer tutucular.</span><span class="sxs-lookup"><span data-stu-id="4696d-152">When you name the .NET Framework class that implements a cmdlet, name the class "*\<Verb>**\<Noun>**\<Command>*", where you replace the *\<Verb>* and *\<Noun>* placeholders with the verb and noun used for the cmdlet name.</span></span> <span data-ttu-id="4696d-153">Örneğin, [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet'i adlı bir sınıf tarafından uygulanan `GetProcessCommand`.</span><span class="sxs-lookup"><span data-stu-id="4696d-153">For example, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet is implemented by a class called `GetProcessCommand`.</span></span>

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a><span data-ttu-id="4696d-154">Herhangi bir işlem hattı giriş (AC02) BeginProcessing yöntemi geçersiz kılarsanız</span><span class="sxs-lookup"><span data-stu-id="4696d-154">If No Pipeline Input Override the BeginProcessing Method (AC02)</span></span>

<span data-ttu-id="4696d-155">İçinde cmdlet'inize ardışık düzendeki girişi kabul etmiyor, işleme uygulanmalıdır [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4696d-155">If your cmdlet does not accept input from the pipeline, processing should be implemented in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span> <span data-ttu-id="4696d-156">Bu yöntem cmdlet'leri sırayı da korumak Windows PowerShell kullanımına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4696d-156">Use of this method allows Windows PowerShell to maintain ordering between cmdlets.</span></span> <span data-ttu-id="4696d-157">İşlem hattının kalan cmdlet'leri, işleme başlamak için bir fırsat geçmeden önce işlem hattındaki ilk cmdlet her zaman nesnelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4696d-157">The first cmdlet in the pipeline always returns its objects before the remaining cmdlets in the pipeline get a chance to start their processing.</span></span>

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a><span data-ttu-id="4696d-158">Durdurma istekleri işlemek için (AC03) StopProcessing yöntemi geçersiz kılın</span><span class="sxs-lookup"><span data-stu-id="4696d-158">To Handle Stop Requests Override the StopProcessing Method (AC03)</span></span>

<span data-ttu-id="4696d-159">Geçersiz kılma [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) yöntemi cmdlet'inize durdurma sinyali işleyebilmeniz.</span><span class="sxs-lookup"><span data-stu-id="4696d-159">Override the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method so that your cmdlet can handle stop signal.</span></span> <span data-ttu-id="4696d-160">Bazı cmdlet'ler, işlemin tamamlanması uzun sürebilir ve cmdlet RPC çağrıları uzun süre çalışan iş parçacığında zaman engeller gibi Windows PowerShell çalışma zamanı yapılan çağrılar arasında geçirmek uzun sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="4696d-160">Some cmdlets take a long time to complete their operation, and they let a long time pass between calls to the Windows PowerShell runtime, such as when the cmdlet blocks the thread in long-running RPC calls.</span></span> <span data-ttu-id="4696d-161">Bu çağrı yapmak cmdlet'leri içerir [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) yöntemi, [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) yöntemi ve diğer geri bildirim Bu mekanizmalar tamamlanması uzun zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="4696d-161">This includes cmdlets that make calls to the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method, to the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, and to other feedback mechanisms that may take a long time to complete.</span></span> <span data-ttu-id="4696d-162">Bu durumda, kullanıcı için bu cmdlet'leri bir durdurma sinyali göndermek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4696d-162">For these cases the user might need to send a stop signal to these cmdlets.</span></span>

### <a name="implement-the-idisposable-interface-ac04"></a><span data-ttu-id="4696d-163">(AC04) IDisposable arayüzünü uygular</span><span class="sxs-lookup"><span data-stu-id="4696d-163">Implement the IDisposable Interface (AC04)</span></span>

<span data-ttu-id="4696d-164">Cmdlet'inize tarafından (işlem hattı için yazılmış) kaldırıldıklarından olmayan nesneler varsa [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi, ek bir nesneyi elden cmdlet'inize gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="4696d-164">If your cmdlet has objects that are not disposed of (written to the pipeline) by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, your cmdlet might require additional object disposal.</span></span> <span data-ttu-id="4696d-165">Örneğin, bir dosya tanıtıcısı cmdlet'inize açar, kendi [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi ve tutamacı açılmaya tarafından kullanılmak üzere tutar [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi, bu tutamacı sahip işlem sonunda kapatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4696d-165">For example, if your cmdlet opens a file handle in its [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, this handle has to be closed at the end of processing.</span></span>

<span data-ttu-id="4696d-166">Windows PowerShell çalışma zamanı her zaman arama [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4696d-166">The Windows PowerShell runtime does not always call the  [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="4696d-167">Örneğin, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi değil cmdlet midway bu işlemi iptal edilir ya da bir sonlandırma, herhangi bir bölümünü cmdlet'i hata meydana gelir, çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4696d-167">For example, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method might not be called if the cmdlet is canceled midway through its operation or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="4696d-168">Bu nedenle, nesne temizleme gerektiren bir cmdlet için .NET Framework sınıf tam uygulamalıdır [System.IDisposable](/dotnet/api/System.IDisposable) Sonlandırıcı dahil olmak üzere Windows PowerShell çalışma zamanı, her ikisi de çağırabilirsiniz arabirimi deseni [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ve [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) işleme sonunda yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="4696d-168">Therefore, the .NET Framework class for a cmdlet that requires object cleanup should implement the complete  [System.IDisposable](/dotnet/api/System.IDisposable) interface pattern, including the finalizer, so that the Windows PowerShell runtime can call both the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>

### <a name="use-serialization-friendly-parameter-types-ac05"></a><span data-ttu-id="4696d-169">Serileştirme uyumlu parametre türleri (AC05) kullanın</span><span class="sxs-lookup"><span data-stu-id="4696d-169">Use Serialization-friendly Parameter Types (AC05)</span></span>

<span data-ttu-id="4696d-170">Cmdlet'inize uzak bilgisayarlarda çalışmasını desteklemek için istemci bilgisayarda kolayca serileştirilmiş ve ardından sunucu bilgisayarda rehydrated türlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4696d-170">To support running your cmdlet on remote computers, use types that can be easily serialized on the client computer and then rehydrated on the server computer.</span></span> <span data-ttu-id="4696d-171">İzleme, serileştirme dostu türleridir.</span><span class="sxs-lookup"><span data-stu-id="4696d-171">The follow types are serialization-friendly.</span></span>

<span data-ttu-id="4696d-172">İlkel türler:</span><span class="sxs-lookup"><span data-stu-id="4696d-172">Primitive types:</span></span>

- <span data-ttu-id="4696d-173">Bayt, SByte, ondalık, tek, Double, Int16, Int32, Int64, UInt16, Uınt32 ve UInt64.</span><span class="sxs-lookup"><span data-stu-id="4696d-173">Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32, and UInt64.</span></span>

- <span data-ttu-id="4696d-174">Boolean, Guid, bayt [], TimeSpan, DateTime, URI ve sürüm.</span><span class="sxs-lookup"><span data-stu-id="4696d-174">Boolean, Guid, Byte[], TimeSpan, DateTime, Uri, and Version.</span></span>

- <span data-ttu-id="4696d-175">Char, String, XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="4696d-175">Char, String, XmlDocument.</span></span>

<span data-ttu-id="4696d-176">Yerleşik rehydratable türleri:</span><span class="sxs-lookup"><span data-stu-id="4696d-176">Built-in rehydratable types:</span></span>

- <span data-ttu-id="4696d-177">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="4696d-177">PSPrimitiveDictionary</span></span>

- <span data-ttu-id="4696d-178">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="4696d-178">SwitchParameter</span></span>

- <span data-ttu-id="4696d-179">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="4696d-179">PSListModifier</span></span>

- <span data-ttu-id="4696d-180">PSCredential</span><span class="sxs-lookup"><span data-stu-id="4696d-180">PSCredential</span></span>

- <span data-ttu-id="4696d-181">IP adresi, MailAddress</span><span class="sxs-lookup"><span data-stu-id="4696d-181">IPAddress, MailAddress</span></span>

- <span data-ttu-id="4696d-182">CultureInfo</span><span class="sxs-lookup"><span data-stu-id="4696d-182">CultureInfo</span></span>

- <span data-ttu-id="4696d-183">X509Certificate2, X500DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="4696d-183">X509Certificate2, X500DistinguishedName</span></span>

- <span data-ttu-id="4696d-184">DirectorySecurity, FileSecurity, RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="4696d-184">DirectorySecurity, FileSecurity, RegistrySecurity</span></span>

<span data-ttu-id="4696d-185">Diğer türleri:</span><span class="sxs-lookup"><span data-stu-id="4696d-185">Other types:</span></span>

- <span data-ttu-id="4696d-186">SecureString</span><span class="sxs-lookup"><span data-stu-id="4696d-186">SecureString</span></span>

- <span data-ttu-id="4696d-187">Kapsayıcılar (listeler ve yukarıdaki türü sözlükleri)</span><span class="sxs-lookup"><span data-stu-id="4696d-187">Containers (lists and dictionaries of the above type)</span></span>

### <a name="use-securestring-for-sensitive-data-ac06"></a><span data-ttu-id="4696d-188">Hassas verileri (AC06) SecureString kullanın</span><span class="sxs-lookup"><span data-stu-id="4696d-188">Use SecureString for Sensitive Data (AC06)</span></span>

<span data-ttu-id="4696d-189">Hassas verileri her zaman işlerken kullanmak [System.Security.Securestring](/dotnet/api/System.Security.SecureString) veri türü.</span><span class="sxs-lookup"><span data-stu-id="4696d-189">When handling sensitive data always use the [System.Security.Securestring](/dotnet/api/System.Security.SecureString) data type.</span></span> <span data-ttu-id="4696d-190">Bu işlem hattı giriş parametreleri yanı sıra işlem hattının hassas verileri döndüren içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4696d-190">This could include pipeline input to parameters, as well as returning sensitive data to the pipeline.</span></span>

## <a name="see-also"></a><span data-ttu-id="4696d-191">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4696d-191">See Also</span></span>

[<span data-ttu-id="4696d-192">Gerekli geliştirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4696d-192">Required Development Guidelines</span></span>](./required-development-guidelines.md)

[<span data-ttu-id="4696d-193">Önemle önerilir geliştirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4696d-193">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

[<span data-ttu-id="4696d-194">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="4696d-194">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
