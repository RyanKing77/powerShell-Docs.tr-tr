---
title: Bir Windows PowerShell modülü yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082065"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="e4480-102">Windows PowerShell Modülü Yazma</span><span class="sxs-lookup"><span data-stu-id="e4480-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="e4480-103">Bu belge, Yöneticiler, betik geliştiriciler ve paketlemek ve kendi Windows PowerShell cmdlet'leri dağıtmak için gereken cmdlet'i geliştiriciler için yazılır.</span><span class="sxs-lookup"><span data-stu-id="e4480-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="e4480-104">Windows PowerShell modüllerini kullanarak, paketleyebilir ve Windows PowerShell çözümlerinizi olmadan derlenmiş bir dili kullanarak dağıtın.</span><span class="sxs-lookup"><span data-stu-id="e4480-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="e4480-105">Windows PowerShell modülleri bölüme etkinleştirmek, düzenlemek ve Windows PowerShell kodunuzu müstakil, yeniden kullanılabilir birimler halinde soyut.</span><span class="sxs-lookup"><span data-stu-id="e4480-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="e4480-106">Yeniden kullanılabilir bu birimleri ile kolayca modüllerinizi doğrudan diğer kişilerle paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4480-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="e4480-107">Betik geliştiriciyseniz de özel betik tabanlı uygulamalar oluşturmak amacıyla üçüncü taraf modülleriyle paketleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4480-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="e4480-108">Modüller, benzer modüllerine Perl ve Python gibi diğer komut dosyası dilleri içinde yeniden kullanılabilir, yeniden dağıtılabilir bileşenleri ile yeniden paketleyin ve birden çok bileşeni için soyut etkinleştirme avantajını kullanan üretime hazır betik çözümlerle özel çözümler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e4480-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="e4480-109">Konumunda, en temel, Windows PowerShell bir modül bir .psm1 dosyasında kaydedilen herhangi bir geçerli Windows PowerShell komut dosyası kodu kabul.</span><span class="sxs-lookup"><span data-stu-id="e4480-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="e4480-110">PowerShell, bir modül olarak herhangi bir ikili cmdlet'i derleme da otomatik olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="e4480-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="e4480-111">Ancak, bütün bir çözüm gruplamak için bir modül (veya daha açık belirtmek gerekirse bir modül bildirimi) da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4480-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="e4480-112">Windows PowerShell modülleri için genel kullanımlar aşağıdaki senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4480-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="e4480-113">Kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="e4480-113">Libraries</span></span>

<span data-ttu-id="e4480-114">Modüller, paket ve ortak görevleri gerçekleştirmek işlevlerin cohesive kitaplıkları dağıtmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4480-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="e4480-115">Genellikle, bu işlevlerin adlarını yansıtmak için kullanılan yaygın görev bir veya daha fazla isimleri paylaşın.</span><span class="sxs-lookup"><span data-stu-id="e4480-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="e4480-116">Genel ve özel üyelere sahip olabilir, bu işlevler de .NET Framework sınıfları benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4480-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="e4480-117">Örneğin, bir kitaplık, dosya aktarımları için bir işlevler kümesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e4480-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="e4480-118">Bu durumda, görevinin yansıtan isim "dosya" olabilir</span><span class="sxs-lookup"><span data-stu-id="e4480-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="e4480-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e4480-119">Configuration</span></span>

<span data-ttu-id="e4480-120">Modüller, bazı cmdlet'ler, sağlayıcıları, İşlevler ve değişkenler ekleyerek ortamınızı özelleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e4480-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="e4480-121">Derlenmiş kod geliştirme ve dağıtma</span><span class="sxs-lookup"><span data-stu-id="e4480-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="e4480-122">Cmdlet ve sağlayıcı geliştiriciler, test ve ek bileşenler oluşturmaya gerek kalmadan kendi derlenmiş kod dağıtmak için modülleri kullanabilir. Oluşturma ve ek bileşenler kaydetme gerek kalmadan bir modül (ikili Modülü) olarak derlenmiş kodunu içeren bütünleştirilmiş kodun aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4480-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4480-123">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e4480-123">See Also</span></span>

[<span data-ttu-id="e4480-124">Bir Windows PowerShell modülü anlama</span><span class="sxs-lookup"><span data-stu-id="e4480-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="e4480-125">Modul Skriptu Powershellu yazma</span><span class="sxs-lookup"><span data-stu-id="e4480-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="e4480-126">Bir ikili PowerShell modülü yazma</span><span class="sxs-lookup"><span data-stu-id="e4480-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="e4480-127">Bir PowerShell modül bildirimi yazma</span><span class="sxs-lookup"><span data-stu-id="e4480-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="e4480-128">PSModulePath yükleme yolunu değiştirme</span><span class="sxs-lookup"><span data-stu-id="e4480-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="e4480-129">Bir PowerShell modülü içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="e4480-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="e4480-130">Bir PowerShell modülü yükleniyor</span><span class="sxs-lookup"><span data-stu-id="e4480-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
