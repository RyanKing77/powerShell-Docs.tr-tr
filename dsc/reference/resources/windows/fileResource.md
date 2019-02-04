---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC dosya kaynağı
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688430"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="ca121-103">DSC dosya kaynağı</span><span class="sxs-lookup"><span data-stu-id="ca121-103">DSC File Resource</span></span>

> <span data-ttu-id="ca121-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ca121-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ca121-105">Dosya kaynağı, Windows PowerShell Desired State Configuration (DSC) hedef düğüm üzerindeki dosya ve klasörleri yönetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca121-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="ca121-106">**HedefYolu** ve **SourcePath** hem de hedef düğüm tarafından erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca121-106">The **DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca121-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca121-107">Syntax</span></span>

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="ca121-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ca121-108">Properties</span></span>

|<span data-ttu-id="ca121-109">Özellik</span><span class="sxs-lookup"><span data-stu-id="ca121-109">Property</span></span>       |<span data-ttu-id="ca121-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca121-110">Description</span></span>                                                                   |<span data-ttu-id="ca121-111">Gerekli</span><span class="sxs-lookup"><span data-stu-id="ca121-111">Required</span></span>|<span data-ttu-id="ca121-112">Varsayılan</span><span class="sxs-lookup"><span data-stu-id="ca121-112">Default</span></span>|
|---------------|------------------------------------------------------------------------------|--------|-------|
|<span data-ttu-id="ca121-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="ca121-113">DestinationPath</span></span>|<span data-ttu-id="ca121-114">Sağlamak istediğiniz hedef düğümde konumu olan `Present` veya `Absent`.</span><span class="sxs-lookup"><span data-stu-id="ca121-114">The location, on the target node, you want to ensure is `Present` or `Absent`.</span></span>|<span data-ttu-id="ca121-115">Evet</span><span class="sxs-lookup"><span data-stu-id="ca121-115">Yes</span></span>|<span data-ttu-id="ca121-116">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-116">No</span></span>|
|<span data-ttu-id="ca121-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ca121-117">Attributes</span></span>     |<span data-ttu-id="ca121-118">Hedef dosya veya dizin özniteliklerini istenen durum.</span><span class="sxs-lookup"><span data-stu-id="ca121-118">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="ca121-119">Geçerli değerler **arşiv**, **gizli**, **salt okunur**, ve **sistem**.</span><span class="sxs-lookup"><span data-stu-id="ca121-119">Valid values are **Archive**, **Hidden**, **ReadOnly**, and **System**.</span></span>|<span data-ttu-id="ca121-120">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-120">No</span></span>|<span data-ttu-id="ca121-121">Yok</span><span class="sxs-lookup"><span data-stu-id="ca121-121">None</span></span>|
|<span data-ttu-id="ca121-122">Sağlama</span><span class="sxs-lookup"><span data-stu-id="ca121-122">Checksum</span></span>      |<span data-ttu-id="ca121-123">İki dosya aynı olup olmadığını belirlerken kullanılacak sağlama türü.</span><span class="sxs-lookup"><span data-stu-id="ca121-123">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="ca121-124">Geçerli değerler şunlardır: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="ca121-124">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|<span data-ttu-id="ca121-125">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-125">No</span></span>|<span data-ttu-id="ca121-126">Yalnızca dosya veya dizin adı karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="ca121-126">Only the file or directory name is compared.</span></span>|
|<span data-ttu-id="ca121-127">İçerikler</span><span class="sxs-lookup"><span data-stu-id="ca121-127">Contents</span></span>       |<span data-ttu-id="ca121-128">İle kullanıldığında geçerli `File` türü.</span><span class="sxs-lookup"><span data-stu-id="ca121-128">Only valid when used with `File` type.</span></span> <span data-ttu-id="ca121-129">Olun içeriğini gösterir `Present` veya `Absent` hedeflenen dosyasından.</span><span class="sxs-lookup"><span data-stu-id="ca121-129">Indicates the contents to Ensure are `Present` or `Absent` from the targeted file.</span></span> |<span data-ttu-id="ca121-130">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-130">No</span></span>|<span data-ttu-id="ca121-131">Yok</span><span class="sxs-lookup"><span data-stu-id="ca121-131">None</span></span>|
|<span data-ttu-id="ca121-132">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="ca121-132">Credential</span></span>     |<span data-ttu-id="ca121-133">Kaynak dosyaları gibi kaynaklarına erişmek için gerekli olan kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="ca121-133">The credentials that are required to access resources, such as source files.</span></span>|<span data-ttu-id="ca121-134">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-134">No</span></span>|<span data-ttu-id="ca121-135">Hedef düğümün bilgisayar hesabı.</span><span class="sxs-lookup"><span data-stu-id="ca121-135">The target node's Computer Account.</span></span> <span data-ttu-id="ca121-136">(*bkz. Not*)</span><span class="sxs-lookup"><span data-stu-id="ca121-136">(*see note*)</span></span>|
|<span data-ttu-id="ca121-137">Emin olun</span><span class="sxs-lookup"><span data-stu-id="ca121-137">Ensure</span></span>         |<span data-ttu-id="ca121-138">Hedef dosya veya dizin istenen durumu.</span><span class="sxs-lookup"><span data-stu-id="ca121-138">The desired state of the target file or directory.</span></span> |<span data-ttu-id="ca121-139">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-139">No</span></span>|<span data-ttu-id="ca121-140">**Mevcut**</span><span class="sxs-lookup"><span data-stu-id="ca121-140">**Present**</span></span>|
|<span data-ttu-id="ca121-141">Force</span><span class="sxs-lookup"><span data-stu-id="ca121-141">Force</span></span>          |<span data-ttu-id="ca121-142">(Örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hata ile sonuçlandı erişim işlemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ca121-142">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span>|<span data-ttu-id="ca121-143">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-143">No</span></span>|`$false`|
|<span data-ttu-id="ca121-144">Recurse</span><span class="sxs-lookup"><span data-stu-id="ca121-144">Recurse</span></span>        |<span data-ttu-id="ca121-145">İle kullanıldığında geçerli `Directory` türü.</span><span class="sxs-lookup"><span data-stu-id="ca121-145">Only valid when used with `Directory` type.</span></span> <span data-ttu-id="ca121-146">Durum işlem yinelemeli olarak tüm alt dizinler için gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ca121-146">Performs the state operation recursively to all subdirectories.</span></span>|<span data-ttu-id="ca121-147">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-147">No</span></span>|`$false`|
|<span data-ttu-id="ca121-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ca121-148">DependsOn</span></span>      |<span data-ttu-id="ca121-149">Belirtilen kaynaklar üzerinde bir bağımlılık ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ca121-149">Sets a dependency on specified resource(s).</span></span> <span data-ttu-id="ca121-150">Bu kaynak, yalnızca tüm bağımlı kaynakları başarılı yürütme sonrasında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ca121-150">This resource will only execute after successful execution of any dependent resources.</span></span> <span data-ttu-id="ca121-151">Bağımlı kaynaklar söz dizimini kullanarak belirttiğiniz `"[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ca121-151">You can specify dependent resources using the syntax `"[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="ca121-152">Bkz: [about_DependsOn](../../../configurations/resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="ca121-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span></span>|<span data-ttu-id="ca121-153">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-153">No</span></span>|<span data-ttu-id="ca121-154">Yok</span><span class="sxs-lookup"><span data-stu-id="ca121-154">None</span></span>|
|<span data-ttu-id="ca121-155">Kaynak yolu</span><span class="sxs-lookup"><span data-stu-id="ca121-155">SourcePath</span></span>     |<span data-ttu-id="ca121-156">Dosya veya klasör kaynak kopyalama kaynağı yolu.</span><span class="sxs-lookup"><span data-stu-id="ca121-156">The path from which to copy the file or folder resource.</span></span>|<span data-ttu-id="ca121-157">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-157">No</span></span>|<span data-ttu-id="ca121-158">Yok</span><span class="sxs-lookup"><span data-stu-id="ca121-158">None</span></span>|
|<span data-ttu-id="ca121-159">Tür</span><span class="sxs-lookup"><span data-stu-id="ca121-159">Type</span></span>           |<span data-ttu-id="ca121-160">Yapılandırılan kaynak türü.</span><span class="sxs-lookup"><span data-stu-id="ca121-160">The type of resource being configured.</span></span> <span data-ttu-id="ca121-161">Geçerli değerler `Directory` ve `File`.</span><span class="sxs-lookup"><span data-stu-id="ca121-161">Valid values are `Directory` and `File`.</span></span>|<span data-ttu-id="ca121-162">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-162">No</span></span>|`File`|
|<span data-ttu-id="ca121-163">MatchSource</span><span class="sxs-lookup"><span data-stu-id="ca121-163">MatchSource</span></span>    |<span data-ttu-id="ca121-164">Kaynak ilk kopyayı sonra kaynak dizine eklenen yeni dosyalar için izlemeniz gerekir, belirler.</span><span class="sxs-lookup"><span data-stu-id="ca121-164">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="ca121-165">Değerini `$true` ilk kopyalamadan sonra yeni kaynak dosyalarını hedefe kopyalanması gereken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca121-165">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="ca121-166">Varsa kümesine `$False`, kaynağın kaynak dizinin içeriğini önbelleğe alır ve ilk kopyalamadan sonra eklenen tüm dosyaları yok sayar.</span><span class="sxs-lookup"><span data-stu-id="ca121-166">If set to `$False`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span>|<span data-ttu-id="ca121-167">Hayır</span><span class="sxs-lookup"><span data-stu-id="ca121-167">No</span></span>|`$false`|

> [!WARNING]
> <span data-ttu-id="ca121-168">İçin bir değer belirtmezseniz `Credential` veya `PSRunAsCredential` (PS V.5), kaynak bilgisayar hesabını hedef düğüme erişmek için kullanacağı `SourcePath`.</span><span class="sxs-lookup"><span data-stu-id="ca121-168">If you do not specify a value for `Credential` or `PSRunAsCredential` (PS V.5), the resource will use the computer account of the target node to access the `SourcePath`.</span></span>  <span data-ttu-id="ca121-169">Zaman `SourcePath` olduğu bir UNC paylaşımı, bu bir "Erişim reddedildi" hata neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca121-169">When the `SourcePath` is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="ca121-170">Lütfen izinlerinizi buna uygun olarak ayarlayın ya da kullanmak olun `Credential` veya `PSRunAsCredential` özellikler kullanılması gereken hesabı belirtin.</span><span class="sxs-lookup"><span data-stu-id="ca121-170">Please ensure your permissions are set accordingly, or use the `Credential` or `PSRunAsCredential` properties to specify the account that should be used.</span></span>

## <a name="present-vs-absent"></a><span data-ttu-id="ca121-171">Mevcut vs. Yok</span><span class="sxs-lookup"><span data-stu-id="ca121-171">Present vs. Absent</span></span>

<span data-ttu-id="ca121-172">Her DSC kaynak için belirttiğiniz değere göre farklı işlemler gerçekleştiren `Ensure` özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca121-172">Each DSC resource performs different operations based on the value you specify for the `Ensure` property.</span></span> <span data-ttu-id="ca121-173">Yukarıdaki özelliklerini belirler durumu işlemi için belirttiğiniz değerleri gerçekleştirdi.</span><span class="sxs-lookup"><span data-stu-id="ca121-173">The values you specify for the above properties determines the state operation performed.</span></span>

### <a name="existence"></a><span data-ttu-id="ca121-174">Varlığı</span><span class="sxs-lookup"><span data-stu-id="ca121-174">Existence</span></span>

<span data-ttu-id="ca121-175">Yalnızca belirttiğinizde bir `DestinationPath`, yolun var olduğundan kaynak sağlar (`Present`) veya yok (`Absent`).</span><span class="sxs-lookup"><span data-stu-id="ca121-175">When you only specify a `DestinationPath`, the resource ensures that the path exists (`Present`) or does not exist (`Absent`).</span></span>

### <a name="copy-operations"></a><span data-ttu-id="ca121-176">Kopyalama işlemleri</span><span class="sxs-lookup"><span data-stu-id="ca121-176">Copy Operations</span></span>

<span data-ttu-id="ca121-177">Belirttiğinizde bir `SourcePath` ve `DestinationPath` ile bir `Type` değerini **dizin**, hedef yol için kaynak kopya kaynak dizini.</span><span class="sxs-lookup"><span data-stu-id="ca121-177">When you specify a `SourcePath` and a `DestinationPath` with a `Type` value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="ca121-178">Özellikleri `Recurse`, `Force`, ve `MatchSource` kopyalama işlemi türünü değiştirme gerçekleştirilirse, while `Credential` kaynak dizinine erişmek için kullanacağınız hesabı belirler.</span><span class="sxs-lookup"><span data-stu-id="ca121-178">The properties `Recurse`, `Force`, and `MatchSource` change the type of copy operation performed, while `Credential` determines which account to use to access the source directory.</span></span>

### <a name="limitations"></a><span data-ttu-id="ca121-179">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="ca121-179">Limitations</span></span>

<span data-ttu-id="ca121-180">Değeri belirtilmişse `ReadOnly` için `Attributes` özelliğinin yanı sıra bir `DestinationPath`, `Ensure = "Present"` belirtilen yol oluşturacak sırada `Contents` dosyasının içeriğini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca121-180">If you specified a value of `ReadOnly` for the `Attributes` property alongside a `DestinationPath`, `Ensure = "Present"` would create the path specified, while `Contents` would set the contents of the file.</span></span>  <span data-ttu-id="ca121-181">Bir `Absent` durumu işlemi yoksayacaktır `Attributes` özelliği tamamen ve belirtilen yoldaki tüm dosyayı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ca121-181">An `Absent` state operation would ignore the `Attributes` property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="ca121-182">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca121-182">Example</span></span>

<span data-ttu-id="ca121-183">Aşağıdaki örnek bir dizin ve alt dizinlerinde çekme sunucusundan dosya kaynağı kullanan bir hedef düğüme kopyalar.</span><span class="sxs-lookup"><span data-stu-id="ca121-183">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="ca121-184">İşlem başarılı olursa, Log kaynağı bir onay iletisi olay günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="ca121-184">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="ca121-185">Kaynak dizini UNC yoludur (`\\PullServer\DemoSource`) çekme sunucusundan paylaşılan.</span><span class="sxs-lookup"><span data-stu-id="ca121-185">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="ca121-186">`Recurse` Özelliği sağlar tüm alt dizinler de kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="ca121-186">The `Recurse` property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca121-187">LCM hedef düğüm varsayılan olarak yerel sistem hesabı bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="ca121-187">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="ca121-188">Erişim izni vermek için **SourcePath**, hedef düğümün bilgisayar hesabının uygun izinleri verin.</span><span class="sxs-lookup"><span data-stu-id="ca121-188">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="ca121-189">**Kimlik bilgisi** ve **PSDSCRunAsCredential** (v5) hem de erişmek için kullandığı bağlam LCM değiştirme **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="ca121-189">The **Credential** and **PSDSCRunAsCredential** (v5) both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="ca121-190">Kullanılacak hesap erişim vermek yine erişimi **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="ca121-190">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="ca121-191">Daha fazla üzerinde kullanma **kimlik bilgilerini** DSC görüyor [kullanıcı olarak çalıştır](../../../configurations/runAsUser.md) veya [yapılandırma veri kimlik bilgileri](../../../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="ca121-191">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
