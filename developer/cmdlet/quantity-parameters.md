---
title: Miktar parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251379"
---
# <a name="quantity-parameters"></a><span data-ttu-id="50faf-102">Miktar Parametreleri</span><span class="sxs-lookup"><span data-stu-id="50faf-102">Quantity Parameters</span></span>

<span data-ttu-id="50faf-103">Önerilen adlarını ve işlevsellik miktarı parametreler için aşağıdaki tabloda listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="50faf-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="50faf-104">Parametre</span><span class="sxs-lookup"><span data-stu-id="50faf-104">Parameter</span></span>|<span data-ttu-id="50faf-105">İşlevsellik</span><span class="sxs-lookup"><span data-stu-id="50faf-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="50faf-106">**Tümü**</span><span class="sxs-lookup"><span data-stu-id="50faf-106">**All**</span></span><br><span data-ttu-id="50faf-107">Veri türü: Boolean</span><span class="sxs-lookup"><span data-stu-id="50faf-107">Data type: Boolean</span></span>|<span data-ttu-id="50faf-108">Bu parametre uygulamak için `true` tüm kaynakları yerine varsayılan alt kümesini işlem yapılması olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="50faf-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="50faf-109">Bu parametre uygulamak için `false` kaynakların alt kümesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="50faf-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="50faf-110">**ayırma**</span><span class="sxs-lookup"><span data-stu-id="50faf-110">**Allocation**</span></span><br><span data-ttu-id="50faf-111">Veri türü: Int32</span><span class="sxs-lookup"><span data-stu-id="50faf-111">Data type: Int32</span></span>|<span data-ttu-id="50faf-112">Kullanıcı ayrılacak öğe sayısını belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50faf-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="50faf-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="50faf-113">**BlockCount**</span></span><br><span data-ttu-id="50faf-114">Veri türü: Int64</span><span class="sxs-lookup"><span data-stu-id="50faf-114">Data type: Int64</span></span>|<span data-ttu-id="50faf-115">Bu parametre, kullanıcının blok sayısı belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50faf-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="50faf-116">**Sayısı**</span><span class="sxs-lookup"><span data-stu-id="50faf-116">**Count**</span></span><br><span data-ttu-id="50faf-117">Veri türü: Int64</span><span class="sxs-lookup"><span data-stu-id="50faf-117">Data type: Int64</span></span>|<span data-ttu-id="50faf-118">Bu parametre, kullanıcı sayısı belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50faf-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="50faf-119">**Kapsam**</span><span class="sxs-lookup"><span data-stu-id="50faf-119">**Scope**</span></span><br><span data-ttu-id="50faf-120">Veri türü: Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="50faf-120">Data type: Keyword</span></span>|<span data-ttu-id="50faf-121">Bu parametre, kullanıcının üzerinde çalışacağı kapsam belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="50faf-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="50faf-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="50faf-122">See Also</span></span>

[<span data-ttu-id="50faf-123">Cmdlet parametreleri</span><span class="sxs-lookup"><span data-stu-id="50faf-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="50faf-124">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="50faf-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="50faf-125">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="50faf-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
