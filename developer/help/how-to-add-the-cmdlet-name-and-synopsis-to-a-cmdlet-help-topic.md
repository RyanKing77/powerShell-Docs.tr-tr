---
title: Cmdlet adı ve özeti için Cmdlet Yardım konusunun ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850893"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="ee339-102">Cmdlet Yardım Konularına Cmdlet Adı ve Özet Ekleme</span><span class="sxs-lookup"><span data-stu-id="ee339-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="ee339-103">Bu bölümde, cmdlet yardımına adı ve özeti bölümlerinde gösterilen içeriği eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee339-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="ee339-104">Yardım dosyasında, bu içerik, her cmdlet için komut düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="ee339-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="ee339-105">Dll Help.xml dosyalardan biri Windows PowerShell yükleme dizininde bulunan bir Yardım dosyasını açın tam görünümü için.</span><span class="sxs-lookup"><span data-stu-id="ee339-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="ee339-106">Örneğin, Microsoft.PowerShell.Commands.Management.dll Help.xml dosya içeriği birçok Windows PowerShell cmdlet'lerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ee339-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="ee339-107">Cmdlet adı ve doğrulanır eklemek için</span><span class="sxs-lookup"><span data-stu-id="ee339-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="ee339-108">Cmdlet Yardım cmdlet'i için iki açıklama görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee339-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="ee339-109">İlk özeti denir kısa bir açıklama açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ee339-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="ee339-110">İçinde açıklanan daha ayrıntılı bir açıklama ikinci açıklamasıdır [ayrıntılı bir açıklaması için Cmdlet Yardım konusunun ekleme](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="ee339-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="ee339-111">Hem bu açıklamalar, tek bir paragraf olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee339-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="ee339-112">Cmdlet adı özeti tekrarlamayın.</span><span class="sxs-lookup"><span data-stu-id="ee339-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="ee339-113">Cmdlet Get-Server'ın bir sunucu alır kullanıcı bildiren kısa, ancak değil bilgilendirici değildir.</span><span class="sxs-lookup"><span data-stu-id="ee339-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="ee339-114">Bunun yerine, eş anlamlı sözcükler kullanın ve Ayrıntılar için bir açıklama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee339-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="ee339-115">Örnek: "Yerel veya uzak bir bilgisayarı temsil eden bir nesne alır."</span><span class="sxs-lookup"><span data-stu-id="ee339-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="ee339-116">"Get", "oluşturma" ve "içinde doğrulanır Değiştir" gibi basit fiilleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee339-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="ee339-117">"Set", belirsiz olduğundan ve başvurmaktan sözcükler gibi "değiştirin." kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="ee339-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="ee339-118">Örnek: "Bir dosyada Authenticode imzası hakkındaki bilgileri alır."</span><span class="sxs-lookup"><span data-stu-id="ee339-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="ee339-119">İçinde etkin ses yazın.</span><span class="sxs-lookup"><span data-stu-id="ee339-119">Write in active voice.</span></span> <span data-ttu-id="ee339-120">Örneğin, "TimeSpan nesne kullan …" "TimeSpan nesne için kullanılabilecek olandan..." çok nettir</span><span class="sxs-lookup"><span data-stu-id="ee339-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="ee339-121">Nesneleri Al cmdlet'leri anlatırken "display" fiili kaçının.</span><span class="sxs-lookup"><span data-stu-id="ee339-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="ee339-122">Windows PowerShell cmdlet'i verileri görüntüler ancak kullanıcılar cmdlet verisini görüntülenmeyebilir .NET Framework nesneleri döndüren kavramı tanıtmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ee339-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="ee339-123">Görüntü vurgulamak, kullanıcı cmdlet diğer birçok yararlı özellik ve görüntülenmez yöntemleri döndürmüş, farkına varmazsınız.</span><span class="sxs-lookup"><span data-stu-id="ee339-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee339-124">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ee339-124">See Also</span></span>

 [<span data-ttu-id="ee339-125">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="ee339-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)