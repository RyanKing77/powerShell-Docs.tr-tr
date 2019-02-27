---
title: Biçimlendirme parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 4f24af9b32f785695d156bfb4784aa03c97e8987
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849423"
---
# <a name="format-parameters"></a><span data-ttu-id="baf15-102">Biçim Parametreleri</span><span class="sxs-lookup"><span data-stu-id="baf15-102">Format Parameters</span></span>

<span data-ttu-id="baf15-103">Aşağıdaki tabloda, önerilen adları ve biçimlendirmek için veya verileri oluşturmak için kullanılan parametreler için işlevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="baf15-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

<span data-ttu-id="baf15-104">Veri türü: Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="baf15-104">As Data type: Keyword</span></span>

<span data-ttu-id="baf15-105">Cmdlet çıktı biçimini belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="baf15-105">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="baf15-106">Örneğin, olası değerleri metin veya komut dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="baf15-106">For example, possible values could be Text or Script.</span></span>

<span data-ttu-id="baf15-107">İkili veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="baf15-107">Binary Data type: SwitchParameter</span></span>

<span data-ttu-id="baf15-108">Cmdlet ikili değerler işlediğini göstermek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="baf15-108">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>

<span data-ttu-id="baf15-109">Kodlama veri türü: Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="baf15-109">Encoding Data type: Keyword</span></span>

<span data-ttu-id="baf15-110">Desteklenen kodlama türünü belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="baf15-110">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="baf15-111">Örneğin, ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, bayt ve dize olası değerler olabilir.</span><span class="sxs-lookup"><span data-stu-id="baf15-111">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>

<span data-ttu-id="baf15-112">Yeni satır veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="baf15-112">NewLine Data type: SwitchParameter</span></span>

<span data-ttu-id="baf15-113">Bu parametre, böylece parametresi belirtildiğinde yeni satır karakterleri desteklenir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="baf15-113">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>

<span data-ttu-id="baf15-114">ShortName veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="baf15-114">ShortName Data type: SwitchParameter</span></span>

<span data-ttu-id="baf15-115">Bu parametre, böylece parametresi belirtildiğinde kısa adları desteklenen uygulayın.</span><span class="sxs-lookup"><span data-stu-id="baf15-115">Implement this parameter so that short names are supported when the parameter is specified.</span></span>

<span data-ttu-id="baf15-116">Genişlik veri türü: Int32</span><span class="sxs-lookup"><span data-stu-id="baf15-116">Width Data type: Int32</span></span>

<span data-ttu-id="baf15-117">Bu parametre, kullanıcının çıktı cihazına genişliğini belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="baf15-117">Implement this parameter so that the user can specify the width of the output device.</span></span>

<span data-ttu-id="baf15-118">Veri türü kaydır: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="baf15-118">Wrap Data type: SwitchParameter</span></span>

<span data-ttu-id="baf15-119">Bu parametre, böylece parametresi belirtildiğinde metin kaydırmayı desteklenir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="baf15-119">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="baf15-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="baf15-120">See Also</span></span>

[<span data-ttu-id="baf15-121">Cmdlet parametreleri</span><span class="sxs-lookup"><span data-stu-id="baf15-121">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="baf15-122">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="baf15-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="baf15-123">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="baf15-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
