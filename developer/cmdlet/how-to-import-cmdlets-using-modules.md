---
title: Modüller kullanılarak cmdlet 'Leri Içeri aktarma | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215268"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="2784c-102">Modül Kullanarak Cmdlet’i İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="2784c-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="2784c-103">Bu makalede, ikili bir modül kullanılarak cmdlet 'leri bir PowerShell oturumuna nasıl içeri aktarılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2784c-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="2784c-104">Modül üyeleri cmdlet 'leri, sağlayıcıları, işlevleri, değişkenleri, diğer adları ve çok daha fazlasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2784c-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="2784c-105">Ek bileşenler yalnızca cmdlet 'ler ve sağlayıcılar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2784c-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="2784c-106">Modül kullanarak cmdlet 'leri yükleme</span><span class="sxs-lookup"><span data-stu-id="2784c-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="2784c-107">Cmdlet 'lerinin uygulandığı derleme dosyasıyla aynı ada sahip bir modül klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2784c-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="2784c-108">Bu yordamda modül klasörü Windows `system32` klasöründe oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2784c-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="2784c-109">`PSModulePath` Ortam değişkeninin yeni modül klasörünüzün yolunu içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2784c-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="2784c-110">Varsayılan olarak, sistem klasörü `PSModulePath` ortam değişkenine zaten eklenir.</span><span class="sxs-lookup"><span data-stu-id="2784c-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="2784c-111">Görüntülemek `PSModulePath`için şunu yazın: `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="2784c-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="2784c-112">Cmdlet derlemesini modül klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2784c-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="2784c-113">Modülün kök klasörüne bir modül bildirim`.psd1`dosyası () ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2784c-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="2784c-114">PowerShell, modülünüzü içeri aktarmak için modül bildirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2784c-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="2784c-115">Daha fazla bilgi için bkz. [PowerShell modülü bildirimi yazma](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="2784c-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="2784c-116">Cmdlet 'leri oturuma eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2784c-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="2784c-117">Bu yordam, cmdlet 'lerinizi test etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2784c-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="2784c-118">Derlemedeki tüm cmdlet 'leri oturuma ekler.</span><span class="sxs-lookup"><span data-stu-id="2784c-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="2784c-119">Modüller hakkında daha fazla bilgi için bkz. [Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="2784c-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2784c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2784c-120">See also</span></span>

[<span data-ttu-id="2784c-121">PowerShell modülü bildirimi yazma</span><span class="sxs-lookup"><span data-stu-id="2784c-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="2784c-122">PowerShell modülünü içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="2784c-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="2784c-123">Import-Module</span><span class="sxs-lookup"><span data-stu-id="2784c-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="2784c-124">Modüller yükleniyor</span><span class="sxs-lookup"><span data-stu-id="2784c-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="2784c-125">PSModulePath yükleme yolunu değiştirme</span><span class="sxs-lookup"><span data-stu-id="2784c-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="2784c-126">Windows PowerShell cmdlet 'ı yazma</span><span class="sxs-lookup"><span data-stu-id="2784c-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
