---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, Kur
title: Katalog cmdlet'leri
ms.openlocfilehash: f0869e8c174ab127996866775ad20d056f877345
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2017
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="f79df-103">Katalog cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="f79df-103">Catalog Cmdlets</span></span>  

<span data-ttu-id="f79df-104">İki yeni cmdlet'leri ekledik [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) oluşturmak ve windows katalog dosyaları doğrulamak için modülü.</span><span class="sxs-lookup"><span data-stu-id="f79df-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>  

## <a name="new-filecatalog"></a><span data-ttu-id="f79df-105">FileCatalog yeni</span><span class="sxs-lookup"><span data-stu-id="f79df-105">New-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="f79df-106">`New-FileCatalog`Dosya ve klasörleri kümesi için bir windows katalog dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f79df-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="f79df-107">Bir katalog dosyası belirtilen yolda tüm dosyalar için karmaları içerir.</span><span class="sxs-lookup"><span data-stu-id="f79df-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="f79df-108">Kullanıcılar bu klasörleri temsil eden katalog dosyası karşılık gelen birlikte klasörler kümesi dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f79df-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="f79df-109">Bir katalog dosyası içeriği alıcı tarafından katalog oluşturulduktan sonra klasörlere hiçbir değişiklik yapılmadan olup olmadığını doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f79df-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="f79df-110">Oluşturma katalog sürüm 1 ve 2 destekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="f79df-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="f79df-111">Sürüm 1 dosya karmaları ve sürüm 2 SHA256 kullanır oluşturmak için SHA1 karma algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f79df-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="f79df-112">Katalog sürüm 2 desteklenmiyor *Windows Server 2008 R2* ve *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="f79df-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="f79df-113">Katalog sürüm 2 platformları kullanıyorsanız kullanmak için önerilen *Windows 8*, *Windows Server 2012* ve üstü.</span><span class="sxs-lookup"><span data-stu-id="f79df-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>  

<span data-ttu-id="f79df-114">Var olan bir modül üzerinde bu komutu kullanmak için modül bildirimi konumunu eşleşecek şekilde CatalogFilePath ve yol değişkenleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="f79df-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="f79df-115">Aşağıdaki örnekte, C:\Program Files\Windows PowerShell\Modules\Pester modülü bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="f79df-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span> 

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="f79df-116">Bu, katalog dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f79df-116">This creates the catalog file.</span></span> 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

<span data-ttu-id="f79df-117">Bir katalog dosyası (exmaple yukarıda içinde Pester.cat) bütünlüğünü doğrulamak için bu kullanılarak imzalanmalıdır [kümesi AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="f79df-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>   


## <a name="test-filecatalog"></a><span data-ttu-id="f79df-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="f79df-118">Test-FileCatalog</span></span> 
--------------------------------

<span data-ttu-id="f79df-119">`Test-FileCatalog`klasörleri kümesini temsil eden katalog doğrular.</span><span class="sxs-lookup"><span data-stu-id="f79df-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span> 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="f79df-120">Bu cmdlet, tüm dosyaları ve bunların göreli yollar diske kaydedilmiş bulunanlarla katalog dosyasında bulunan karmaları karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="f79df-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="f79df-121">Herhangi dosya karmaları ve yolları arasında uyuşmazlık algılarsa durumunu döndürür `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="f79df-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span> <span data-ttu-id="f79df-122">Kullanıcılar, tüm bu bilgileri kullanarak alabilir `Detailed` geçin.</span><span class="sxs-lookup"><span data-stu-id="f79df-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="f79df-123">Kataloğun imzalama durumu görüntülenir `Signature` çağırmak kadar aynı alan [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) katalog dosyası cmdlet'ini.</span><span class="sxs-lookup"><span data-stu-id="f79df-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet on the catalog file.</span></span> <span data-ttu-id="f79df-124">Kullanıcılar ayrıca atlayabilirsiniz herhangi bir dosya doğrulama sırasında kullanarak `FilesToSkip` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f79df-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span> 

