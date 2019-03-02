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
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251192"
---
# <a name="format-parameters"></a><span data-ttu-id="a23bf-102">Biçim Parametreleri</span><span class="sxs-lookup"><span data-stu-id="a23bf-102">Format Parameters</span></span>

<span data-ttu-id="a23bf-103">Aşağıdaki tabloda, önerilen adları ve biçimlendirmek için veya verileri oluşturmak için kullanılan parametreler için işlevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="a23bf-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="a23bf-104">Parametre</span><span class="sxs-lookup"><span data-stu-id="a23bf-104">Parameter</span></span>|<span data-ttu-id="a23bf-105">İşlevsellik</span><span class="sxs-lookup"><span data-stu-id="a23bf-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="a23bf-106">**olarak**</span><span class="sxs-lookup"><span data-stu-id="a23bf-106">**As**</span></span><br><span data-ttu-id="a23bf-107">Veri türü: Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a23bf-107">Data type: Keyword</span></span>|<span data-ttu-id="a23bf-108">Cmdlet çıktı biçimini belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a23bf-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="a23bf-109">Örneğin, olası değerleri metin veya komut dosyası olabilir.</span><span class="sxs-lookup"><span data-stu-id="a23bf-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="a23bf-110">**İkili**</span><span class="sxs-lookup"><span data-stu-id="a23bf-110">**Binary**</span></span><br><span data-ttu-id="a23bf-111">Veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="a23bf-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="a23bf-112">Cmdlet ikili değerler işlediğini göstermek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a23bf-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="a23bf-113">**Kodlama**</span><span class="sxs-lookup"><span data-stu-id="a23bf-113">**Encoding**</span></span><br><span data-ttu-id="a23bf-114">Veri türü: Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a23bf-114">Data type: Keyword</span></span>|<span data-ttu-id="a23bf-115">Desteklenen kodlama türünü belirtmek için bu parametreyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a23bf-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="a23bf-116">Örneğin, ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, bayt ve dize olası değerler olabilir.</span><span class="sxs-lookup"><span data-stu-id="a23bf-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="a23bf-117">**Yeni satır**</span><span class="sxs-lookup"><span data-stu-id="a23bf-117">**NewLine**</span></span><br><span data-ttu-id="a23bf-118">Veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="a23bf-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="a23bf-119">Bu parametre, böylece parametresi belirtildiğinde yeni satır karakterleri desteklenir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a23bf-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="a23bf-120">**Hosts**</span><span class="sxs-lookup"><span data-stu-id="a23bf-120">**ShortName**</span></span><br><span data-ttu-id="a23bf-121">Veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="a23bf-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="a23bf-122">Bu parametre, böylece parametresi belirtildiğinde kısa adları desteklenen uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a23bf-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="a23bf-123">**Genişlik**</span><span class="sxs-lookup"><span data-stu-id="a23bf-123">**Width**</span></span><br><span data-ttu-id="a23bf-124">Veri türü: Int32</span><span class="sxs-lookup"><span data-stu-id="a23bf-124">Data type: Int32</span></span>|<span data-ttu-id="a23bf-125">Bu parametre, kullanıcının çıktı cihazına genişliğini belirtebilirsiniz böylece uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a23bf-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="a23bf-126">**Kaydırma**</span><span class="sxs-lookup"><span data-stu-id="a23bf-126">**Wrap**</span></span><br><span data-ttu-id="a23bf-127">Veri türü: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="a23bf-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="a23bf-128">Bu parametre, böylece parametresi belirtildiğinde metin kaydırmayı desteklenir uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a23bf-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="a23bf-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a23bf-129">See Also</span></span>

[<span data-ttu-id="a23bf-130">Cmdlet parametreleri</span><span class="sxs-lookup"><span data-stu-id="a23bf-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="a23bf-131">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="a23bf-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="a23bf-132">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="a23bf-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
