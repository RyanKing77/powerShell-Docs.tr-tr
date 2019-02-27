---
title: Tarih ve saat parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846714"
---
# <a name="date-and-time-parameters"></a><span data-ttu-id="a5035-102">Tarih ve Saat Parametreleri</span><span class="sxs-lookup"><span data-stu-id="a5035-102">Date and Time Parameters</span></span>

<span data-ttu-id="a5035-103">Aşağıdaki tabloda, önerilen ad ve tarih ve saat bilgilerini işleyen parametreleri için işlevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="a5035-103">The following table lists recommended names and functionality for parameters that handle date and time information.</span></span> <span data-ttu-id="a5035-104">Tarih ve saat parametreleri, genellikle bir sorun oluşturulduğunda veya erişilen kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5035-104">Date and time parameters are typically used to record when something is created or accessed.</span></span>

<span data-ttu-id="a5035-105">Erişilen veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="a5035-105">Accessed Data type: SwitchParameter</span></span>

<span data-ttu-id="a5035-106">Bu parametre, cmdlet, erişilen kaynaklar üzerinde çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama `Before` ve `After` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="a5035-106">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been accessed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="a5035-107">Bu parametre belirtilmezse, `Created` ve `Modified` parametreleri olmalıdır belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="a5035-107">If this parameter is specified, the `Created` and `Modified` parameters must be not be specified.</span></span>

<span data-ttu-id="a5035-108">Sonra veri türü: Tarih/saat</span><span class="sxs-lookup"><span data-stu-id="a5035-108">After Data type: DateTime</span></span>

<span data-ttu-id="a5035-109">Tarih ve saat sonra cmdlet kullanılan belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a5035-109">Implement this parameter to specify the date and time after which the cmdlet was used.</span></span> <span data-ttu-id="a5035-110">İçin `After` parametresi çalışmak için cmdlet ayrıca olmalıdır bir `Accessed`, `Created`, veya `Modified` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a5035-110">For the `After` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="a5035-111">Ve bu parametre ayarlanmalıdır `true` cmdlet zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a5035-111">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="a5035-112">Önce veri türü: Tarih/saat</span><span class="sxs-lookup"><span data-stu-id="a5035-112">Before Data type: DateTime</span></span>

<span data-ttu-id="a5035-113">Tarih ve saat önüne cmdlet kullanılan belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a5035-113">Implement this parameter to specify the date and time before which the cmdlet was used.</span></span> <span data-ttu-id="a5035-114">İçin `Before` parametresi çalışmak için cmdlet ayrıca olmalıdır bir `Accessed`, `Created`, veya `Modified` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a5035-114">For the `Before` parameter to work, the cmdlet must also have an `Accessed`, `Created`, or `Modified` parameter.</span></span> <span data-ttu-id="a5035-115">Ve bu parametre ayarlanmalıdır `true` cmdlet zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a5035-115">And, that parameter must be set to `true` when the cmdlet is called.</span></span>

<span data-ttu-id="a5035-116">Veri türü oluşturdu: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="a5035-116">Created Data type: SwitchParameter</span></span>

<span data-ttu-id="a5035-117">Bu parametre, cmdlet, oluşturulmuş olan kaynaklar üzerinde çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama `Before` ve `After` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="a5035-117">Implement this parameter so that when it is specified the cmdlet will operate on the resources that have been created based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="a5035-118">Bu parametre belirtilmezse, `Accessed` ve `Modified` parametreleri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a5035-118">If this parameter is specified, the `Accessed` and `Modified` parameters must not be specified.</span></span>

<span data-ttu-id="a5035-119">Tam veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="a5035-119">Exact Data type: SwitchParameter</span></span>

<span data-ttu-id="a5035-120">Bu parametre, böylece kaynak terimi, belirtilen kaynak adı tam olarak eşleşmelidir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a5035-120">Implement this parameter so that when it is specified the resource term must match the resource name exactly.</span></span> <span data-ttu-id="a5035-121">Parametre belirtilmediğinde adı ve kaynak terimi tam olarak eşleşmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a5035-121">When the parameter is not specified the resource term and name do not need to match exactly.</span></span>

<span data-ttu-id="a5035-122">Değiştirilen veri türü: Tarih/saat</span><span class="sxs-lookup"><span data-stu-id="a5035-122">Modified Data type: DateTime</span></span>

<span data-ttu-id="a5035-123">Bu parametre, cmdlet değişmiş olan kaynaklarda çalışır belirtildiğinde tarih ve saat tarafından belirlenen böylece temel uygulama `Before` ve `After` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="a5035-123">Implement this parameter so that when it is specified the cmdlet will operate on resources that have been changed based on the date and time specified by the `Before` and `After` parameters.</span></span>

<span data-ttu-id="a5035-124">Bu parametre belirtilmezse, `Accessed` ve `Created` parametreleri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a5035-124">If this parameter is specified, the `Accessed` and `Created` parameters must not be specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5035-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a5035-125">See Also</span></span>

[<span data-ttu-id="a5035-126">Cmdlet parametreleri</span><span class="sxs-lookup"><span data-stu-id="a5035-126">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="a5035-127">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="a5035-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="a5035-128">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="a5035-128">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
