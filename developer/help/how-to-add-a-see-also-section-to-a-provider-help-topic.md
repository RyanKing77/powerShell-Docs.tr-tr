---
title: Nasıl bir bakın bölümü için sağlayıcı Yardım konusunun da ekleyin. | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848457"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="c8ea8-102">Sağlayıcı Yardım Konusuna Ayrıca Bakın Bölümü Ekleme</span><span class="sxs-lookup"><span data-stu-id="c8ea8-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="c8ea8-103">Bu bölümde doldurmak açıklanmaktadır **ayrıca** sağlayıcısı Yardım konusunun bölümü.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="c8ea8-104">**Ayrıca** bölüm sağlayıcısıyla ilgili ya da daha iyi anlamanıza ve sağlayıcıyı kullanacak kullanıcı yardımcı olabilecek konuların listesini oluşur.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="c8ea8-105">Konu listesi cmdlet yardımını, sağlayıcı içerebilir ve kavramsal ("hakkında") Windows PowerShell Yardım konuları.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="c8ea8-106">Ayrıca, kitaplar, inceleme ve geçerli sağlayıcı Yardım konusunun çevrimiçi sürümünü de dahil olmak üzere çevrimiçi konuları başvuruları de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="c8ea8-107">Çevrimiçi konulara bakın URI veya bir arama terimi düz metin biçiminde belirtin.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="c8ea8-108">`Get-Help` Cmdlet'i bağlantı etmez veya yeniden yönlendirmek için konularına listesinde.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="c8ea8-109">Ayrıca, `Online` parametresinin `Get-Help` cmdlet'i sağlayıcı yardımıyla çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="c8ea8-110">Ayrıca bkz. bölümünde oluşturulur `RelatedLinks` öğesi ve içerdiği etiketler.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="c8ea8-111">Aşağıdaki XML etiket ekleme işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="c8ea8-112">"Ayrıca bkz:" konuları eklemek için</span><span class="sxs-lookup"><span data-stu-id="c8ea8-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="c8ea8-113">İçinde *AssemblyName*içinde help.xml .dll dosyası `providerHelp` öğe, Ekle bir `RelatedLinks` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="c8ea8-114">`RelatedLinks` Öğesi içindeki son öğeden olmalıdır `providerHelp` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="c8ea8-115">Yalnızca bir `RelatedLinks` öğesi her sağlayıcısı Yardım konusunda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="c8ea8-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c8ea8-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="c8ea8-117">Her bir konuda için **ayrıca** bölümünde, içinde `RelatedLinks` öğesi ekleme bir `navigationLink` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="c8ea8-118">Ardından, her `navigationLink` öğesi, bir tane ekleyin `linkText` öğesi ve bir `uri` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="c8ea8-119">Kullanmıyorsanız, `uri` öğesi ekleyebilirsiniz, boş bir öğe olarak (\<URI / >).</span><span class="sxs-lookup"><span data-stu-id="c8ea8-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="c8ea8-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c8ea8-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="c8ea8-121">Konu adı arasında `linkText` etiketler.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="c8ea8-122">Bir URI sağlıyorsanız arasında yazın `uri` etiketler.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="c8ea8-123">Geçerli sağlayıcı Yardım konusunun çevrimiçi sürümünü arasında belirtmek için `linkText` etiketler, tür "çevrimiçi sürüm:" yerine konu adı.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="c8ea8-124">Genellikle, "çevrimiçi sürüm:" ilk konu ayrıca konu listesindeki bir bağlantıdır.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="c8ea8-125">Aşağıdaki örnek, üç ayrıca konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="c8ea8-126">İlk geçerli konuyu çevrimiçi sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="c8ea8-127">İkinci bir Windows PowerShell cmdlet Yardım konusunun için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="c8ea8-128">Üçüncü için başka bir çevrimiçi konusuna ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c8ea8-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```