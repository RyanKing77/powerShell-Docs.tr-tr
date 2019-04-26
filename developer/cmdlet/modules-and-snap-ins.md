---
title: Modüller ve ek bileşenler | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067629"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="72087-102">Modüller ve Ek Bileşenler</span><span class="sxs-lookup"><span data-stu-id="72087-102">Modules and Snap-ins</span></span>

<span data-ttu-id="72087-103">Cmdlet modülleri (Windows PowerShell 2.0 tarafından sunulan) veya ek bileşenleri'ni kullanarak bir oturuma eklenebilir. Cmdlet'i bir ana bilgisayar uygulaması veya etkileşimli olarak komut satırında programlı olarak çalıştırılabilir oturumu eklendikten sonra.</span><span class="sxs-lookup"><span data-stu-id="72087-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="72087-104">Aşağıdaki nedenlerle bir oturuma cmdlet'leri eklemek için teslim yöntemi olarak modülleri kullanmanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="72087-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="72087-105">Modülleri cmdlet tanımlandığı derleme yükleyerek cmdlet'leri eklemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="72087-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="72087-106">Ek bir sınıf uygulamak için gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="72087-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="72087-107">Modülleri değişkenler, İşlevler, komut dosyaları, türleri ve biçimlendirme dosyaları ve daha fazla gibi başka kaynaklar eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="72087-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="72087-108">Ek bileşenler, yalnızca cmdlet'lerini ve sağlayıcıları oturumuna eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72087-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="72087-109">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="72087-109">See Also</span></span>

[<span data-ttu-id="72087-110">Bir Windows PowerShell modülü yazma</span><span class="sxs-lookup"><span data-stu-id="72087-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="72087-111">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="72087-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
