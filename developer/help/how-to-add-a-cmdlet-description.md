---
title: Bir Cmdlet açıklama ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851432"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="c09f3-102">Cmdlet Açıklaması Ekleme</span><span class="sxs-lookup"><span data-stu-id="c09f3-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="c09f3-103">Bu bölümde, cmdlet Yardım Açıklama bölümünde görüntülenen içerik eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c09f3-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="c09f3-104">Yardım dosyasında, bu içerik, her cmdlet için komut düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="c09f3-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c09f3-105">Dll Help.xml dosyalardan biri Windows PowerShell yükleme dizininde bulunan bir Yardım dosyasını açın tam görünümü için.</span><span class="sxs-lookup"><span data-stu-id="c09f3-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="c09f3-106">Örneğin, Microsoft.PowerShell.Commands.Management.dll Help.xml dosya içeriği birçok Windows PowerShell cmdlet'lerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c09f3-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="c09f3-107">Bir açıklama eklemek için</span><span class="sxs-lookup"><span data-stu-id="c09f3-107">To Add a Description</span></span>

- <span data-ttu-id="c09f3-108">Daha ayrıntılı cmdlet temel özelliklerini açıklayarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="c09f3-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="c09f3-109">Çoğu durumda, cmdlet adı kullanılan terimler açıklanmaktadır ve bir örnek ile bilinmeyen kavramları göstermek.</span><span class="sxs-lookup"><span data-stu-id="c09f3-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="c09f3-110">Cmdlet'i bir dosyaya veri ekler, örneğin, bu veri, varolan bir dosyanın sonuna ekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c09f3-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="c09f3-111">Tüm cmdlet özelliklerini bulmak için parametre listesini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="c09f3-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="c09f3-112">Birincil işlevi cmdlet'inin açıklayan ve sonra diğer işlevleri ve özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c09f3-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="c09f3-113">Örneğin, bir özelliği değiştirmek için cmdlet main işlevi olduğu, ancak cmdlet tüm özelliklerini değiştirebilirsiniz, bunu ayrıntılı bir açıklama varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c09f3-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="c09f3-114">Cmdlet parametrelerini bilgi farklı şekillerde irtibat kullanıcılara izin vermek istiyorsanız, onu açıklayın.</span><span class="sxs-lookup"><span data-stu-id="c09f3-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="c09f3-115">Kullanıcılar belirgin kullandığı ek cmdlet kullanabileceğiniz yollar hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c09f3-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="c09f3-116">Örneğin, nesne kullanabilirsiniz, `Get-Host` Windows PowerShell komut penceresinde metnin rengini değiştirmek için cmdlet'i alır.</span><span class="sxs-lookup"><span data-stu-id="c09f3-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="c09f3-117">Örnek:  " `Get-Acl` Cmdlet'i, bir dosyanın veya kaynağın güvenlik tanımlayıcısı temsil eden nesneleri alır.</span><span class="sxs-lookup"><span data-stu-id="c09f3-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="c09f3-118">Kaynak erişim denetim listelerini (ACL'ler) güvenlik tanımlayıcısını içerir.</span><span class="sxs-lookup"><span data-stu-id="c09f3-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="c09f3-119">ACL kaynağa erişmek için kullanıcıların ve kullanıcı gruplarının sahip izinleri belirtir."</span><span class="sxs-lookup"><span data-stu-id="c09f3-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="c09f3-120">Ayrıntılı bir açıklama cmdlet açıklaması gerekir, ancak cmdlet'ini kullanır kavramları açıklamak değildir.</span><span class="sxs-lookup"><span data-stu-id="c09f3-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="c09f3-121">Kavram tanımları içinde ek notlar yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c09f3-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="c09f3-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c09f3-122">See Also</span></span>

[<span data-ttu-id="c09f3-123">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="c09f3-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
