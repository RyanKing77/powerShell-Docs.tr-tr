---
title: Açıklama tabanlı Yardım sözdizimi | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083221"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="7cfab-102">Yorum Tabanlı Yardım Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="7cfab-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="7cfab-103">Bu bölümde, açıklama tabanlı Yardım söz dizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7cfab-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="7cfab-104">Söz dizimi diyagramı</span><span class="sxs-lookup"><span data-stu-id="7cfab-104">Syntax Diagram</span></span>

 <span data-ttu-id="7cfab-105">Açıklama tabanlı Yardım için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7cfab-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="7cfab-106">Söz dizimi açıklaması</span><span class="sxs-lookup"><span data-stu-id="7cfab-106">Syntax Description</span></span>

 <span data-ttu-id="7cfab-107">Açıklama tabanlı Yardım açıklamaları dizisi olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="7cfab-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="7cfab-108">Açıklama simgesini (#) açıklamaları önce her bir satır yazın ya da kullanabilirsiniz "\<#" ve "#>" açıklama bloğu oluşturmak için semboller.</span><span class="sxs-lookup"><span data-stu-id="7cfab-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="7cfab-109">Açıklama bloğu içinde tüm satırları açıklamalar olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="7cfab-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="7cfab-110">Açıklama tabanlı Yardım her bölüm bir anahtar tarafından tanımlanır ve her anahtar sözcüğün bir nokta (.) tarafından öncesinde.</span><span class="sxs-lookup"><span data-stu-id="7cfab-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="7cfab-111">Anahtar sözcükler, herhangi bir sırada görünebilir.</span><span class="sxs-lookup"><span data-stu-id="7cfab-111">The keywords can appear in any order.</span></span> <span data-ttu-id="7cfab-112">Anahtar adları büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="7cfab-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="7cfab-113">Açıklama bloğu, en az bir Yardım anahtar sözcüğü içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cfab-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="7cfab-114">Bazı anahtar sözcükler gibi örnek, aynı açıklama bloğunda birden çok kez görünebilir.</span><span class="sxs-lookup"><span data-stu-id="7cfab-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="7cfab-115">Her anahtar sözcüğü için Yardım içeriği satırda anahtar sözcüğü sonra başlar ve birden fazla satırı kapsayabilir.</span><span class="sxs-lookup"><span data-stu-id="7cfab-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="7cfab-116">Tüm satırları açıklama tabanlı Yardım konusunun bitişik olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cfab-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="7cfab-117">Yardım konusunun bir parçası olmayan bir yorum açıklama tabanlı Yardım konusunun izleyen son Yardım olmayan yorum satırını açıklama tabanlı Yardım başlangıcı arasındaki en az bir boş satır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7cfab-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="7cfab-118">Örneğin, aşağıdaki açıklama tabanlı Yardım konusu içerir. Açıklama anahtar sözcüğü ve bir işlev veya betiği açıklamasını kendi değeri.</span><span class="sxs-lookup"><span data-stu-id="7cfab-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```