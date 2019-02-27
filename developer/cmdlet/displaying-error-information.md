---
title: Hata bilgileri görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848408"
---
# <a name="displaying-error-information"></a><span data-ttu-id="544f6-102">Hata Bilgilerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="544f6-102">Displaying Error Information</span></span>

<span data-ttu-id="544f6-103">Bu konuda, kullanıcılar hata bilgilerini görüntüleyebilir yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="544f6-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="544f6-104">Hata bilgilerini sunumunu cmdlet'inize hatayla karşılaştığında, varsayılan olarak, aşağıdaki hata çıktıya benzer olacak.</span><span class="sxs-lookup"><span data-stu-id="544f6-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="544f6-105">Ancak, kullanıcıların hataları kategoriye göre ayarlayarak görüntüleyebileceği `$ErrorView` değişkenini `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="544f6-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="544f6-106">Kategori Görünümü Serbest metin açıklamasını hata yerine hata kaydı belirli bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="544f6-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="544f6-107">Bu görünüm, tarama hataların uzun bir listeniz varsa yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="544f6-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="544f6-108">Kategori görünümünde, aşağıdaki gibi önceki hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="544f6-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="544f6-109">Hata kategorileri hakkında daha fazla bilgi için bkz. [Windows PowerShell hata kaydı](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="544f6-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="544f6-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="544f6-110">See Also</span></span>

[<span data-ttu-id="544f6-111">Windows PowerShell hata kaydı</span><span class="sxs-lookup"><span data-stu-id="544f6-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="544f6-112">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="544f6-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
