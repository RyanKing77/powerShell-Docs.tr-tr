---
title: Cmdlet modüllerini kullanarak içeri aktarma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067986"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="569e7-102">Modül Kullanarak Cmdlet’i İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="569e7-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="569e7-103">Bu konuda, ikili modül kullanarak bir Windows PowerShell oturumuna cmdlet'leri içe aktarmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="569e7-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="569e7-104">Üyeleri modülleri, cmdlet'leri, sağlayıcıları, İşlevler, değişkenler, diğer adlar ve çok daha fazlasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="569e7-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="569e7-105">Ek bileşenler, yalnızca cmdlet'lerini ve sağlayıcıları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="569e7-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="569e7-106">Bir modül kullanarak cmdlet'leri yükleme</span><span class="sxs-lookup"><span data-stu-id="569e7-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="569e7-107">Cmdlet'ler uygulanan derleme dosyası aynı ada sahip bir modül klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="569e7-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="569e7-108">Bu yordamda, modül klasöründe oluşturulan `system32` klasör.</span><span class="sxs-lookup"><span data-stu-id="569e7-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="569e7-109">Emin olun `PSModulePath` ortam değişkeni, yeni modül klasörün yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="569e7-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="569e7-110">Varsayılan olarak, sistem klasörü zaten eklenir `PSModulePath` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="569e7-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="569e7-111">Cmdlet derleme modülü klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="569e7-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="569e7-112">Cmdlet'lerini oturumuna eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="569e7-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="569e7-113">Bu yordam, cmdlet'lerinizi test etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="569e7-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="569e7-114">Oturuma derlemedeki tüm cmdlet'ler ekler.</span><span class="sxs-lookup"><span data-stu-id="569e7-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="569e7-115">Modüller hakkında daha fazla bilgi için farklı türlerdeki modüllerin, modüller ve verilen, bir modül öğelerini kısıtlamak nasıl yük farklı yollarını görmek [bir Windows PowerShell modülü yazma](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="569e7-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="569e7-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="569e7-116">See Also</span></span>

[<span data-ttu-id="569e7-117">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="569e7-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="569e7-118">Modülleri yükleme</span><span class="sxs-lookup"><span data-stu-id="569e7-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)