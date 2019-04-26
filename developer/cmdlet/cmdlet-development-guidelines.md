---
title: Cmdlet geliştirme yönergeleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- development guidelines [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], development guidelines
ms.assetid: c30cc3c0-e958-4a8f-b81f-1e38de772f13
caps.latest.revision: 14
ms.openlocfilehash: 89c7682e87fa6f389349fc44275be0d2ffc83957
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068581"
---
# <a name="cmdlet-development-guidelines"></a><span data-ttu-id="e9910-102">Cmdlet Geliştirme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e9910-102">Cmdlet Development Guidelines</span></span>

<span data-ttu-id="e9910-103">Bu bölümdeki konular, iyi biçimlendirilmiş cmdlet'leri oluşturmak için kullanabileceğiniz geliştirme yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9910-103">The topics in this section provide development guidelines that you can use to produce well-formed cmdlets.</span></span> <span data-ttu-id="e9910-104">Bu yönergeleri izleyerek ve Windows PowerShell çalışma zamanı tarafından sağlanan ortak işlevselliği yararlanarak en az çaba ile güçlü cmdlet'leri geliştirebilir ve kullanıcı ile tutarlı bir deneyim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e9910-104">By leveraging the common functionality provided by the Windows PowerShell runtime and by following these guidelines, you can develop robust cmdlets with minimal effort and provide the user with a consistent experience.</span></span> <span data-ttu-id="e9910-105">Ayrıca, ortak işlevselliği çözülüp gerektirmediğinden test yükünü azaltır.</span><span class="sxs-lookup"><span data-stu-id="e9910-105">Additionally, you will reduce the test burden because common functionality does not require retesting.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e9910-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e9910-106">In This Section</span></span>

- [<span data-ttu-id="e9910-107">Gerekli geliştirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e9910-107">Required Development Guidelines</span></span>](./required-development-guidelines.md)

- [<span data-ttu-id="e9910-108">Önemle önerilir geliştirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e9910-108">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

- [<span data-ttu-id="e9910-109">Danışmanlık geliştirme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e9910-109">Advisory Development Guidelines</span></span>](./advisory-development-guidelines.md)

## <a name="see-also"></a><span data-ttu-id="e9910-110">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e9910-110">See Also</span></span>

[<span data-ttu-id="e9910-111">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="e9910-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="e9910-112">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="e9910-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
