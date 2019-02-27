---
title: Yardım dosyalarını nasıl güncelleştireceğinizi | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846483"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="78d2f-102">Yardım Dosyalarını Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="78d2f-102">How to Update Help Files</span></span>

<span data-ttu-id="78d2f-103">Bu konu, güncelleştirilebilir Yardımı'nı destekleyen bir modül için Yardım dosyalarını nasıl güncelleştireceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="78d2f-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="78d2f-104">Yardım dosyaları güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="78d2f-104">Updating Help Files</span></span>

<span data-ttu-id="78d2f-105">Yardım dosyaları, hataları düzeltme, bir kavramı açıklığa kavuşturan, sık sorulan soru yanıtlama, yeni dosyaları ekleme veya yeni ve daha iyi örnekleri ekleme gibi güncelleştirmek için birçok neden vardır.</span><span class="sxs-lookup"><span data-stu-id="78d2f-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="78d2f-106">Yardım dosyasını güncelleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="78d2f-106">To update a help file:</span></span>

1. <span data-ttu-id="78d2f-107">Dosyaları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="78d2f-107">Change the files.</span></span>

2. <span data-ttu-id="78d2f-108">Dosyalar diğer UI kültürü çevir.</span><span class="sxs-lookup"><span data-stu-id="78d2f-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="78d2f-109">Tüm Yardım dosyaları (yeni, değiştirilmiş ve değişmeden) için her UI kültürü modülünde toplayın.</span><span class="sxs-lookup"><span data-stu-id="78d2f-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="78d2f-110">Dosyaları XML şemasına karşı doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="78d2f-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="78d2f-111">CAB dosyaları her UI kültürü için yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78d2f-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="78d2f-112">HelpInfo XML dosyasında sürüm numaralarının her UI kültürü için CAB dosyasının artırın.</span><span class="sxs-lookup"><span data-stu-id="78d2f-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="78d2f-113">Değeri tarafından belirtilen konuma yeni CAB dosyaları karşıya yükleme **HelpContentUri** HelpInfo XML dosyasında öğe.</span><span class="sxs-lookup"><span data-stu-id="78d2f-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="78d2f-114">Eski CAB dosyaları, CAB dosyaları yeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="78d2f-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="78d2f-115">Tarafından belirtilen konuma güncelleştirilmiş HelpInfo XML dosyasını karşıya yükleme **HelpInfoUri** modül bildirimindeki anahtar.</span><span class="sxs-lookup"><span data-stu-id="78d2f-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="78d2f-116">Eski HelpInfo XML dosyası yeni dosya ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="78d2f-116">Replace the older HelpInfo XML file with the new file.</span></span>