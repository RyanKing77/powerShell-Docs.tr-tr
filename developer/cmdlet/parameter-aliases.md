---
title: Parametre diğer adlarına | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067595"
---
# <a name="parameter-aliases"></a><span data-ttu-id="098c6-102">Parametre Diğer Adları</span><span class="sxs-lookup"><span data-stu-id="098c6-102">Parameter Aliases</span></span>

<span data-ttu-id="098c6-103">Cmdlet parametreleri, diğer adlar da olabilir.</span><span class="sxs-lookup"><span data-stu-id="098c6-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="098c6-104">Diğer adları yerine parametre adları, yazın veya bir komut parametresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="098c6-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="098c6-105">Diğer ad kullanmanın avantajları</span><span class="sxs-lookup"><span data-stu-id="098c6-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="098c6-106">Diğer adlar parametreleri ekleyerek, aşağıdaki avantajları sağlar.</span><span class="sxs-lookup"><span data-stu-id="098c6-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="098c6-107">Böylece kullanıcı, cmdlet çağrıldığında tam parametre adı kullanmak zorunda değil, bir kısayol sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="098c6-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="098c6-108">Örneğin, "Bilgisayaradı" parametre adı yerine "CN =" diğer ad kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="098c6-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="098c6-109">Aynı parametre için farklı adlar sağlamak istiyorsanız, birden fazla diğer ad tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="098c6-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="098c6-110">Farklı yollarla aynı veriye başvurmaktadır birden çok kullanıcı gruplarıyla çalışma varsa birden çok diğer adlarını tanımlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="098c6-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="098c6-111">Bir parametrenin adı değişirse, var olan betikler için geriye dönük uyumluluk sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="098c6-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="098c6-112">Diğer ad özniteliği ValueFromPipelineByName özniteliği ile birlikte kullanarak, farklı nesne türlerine bağlanacak cmdlet'inize izin veren bir parametre tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="098c6-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="098c6-113">Örneğin, iki farklı türde nesneler vardı ve yazıcı özelliği ilk nesneniz ve bir düzenleyici özelliğini ikinci nesneniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="098c6-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="098c6-114">Cmdlet'inize sahip bir parametreye sahipse, yazıcı ve düzenleyici diğer adlar ve cmdlet ardışık giriş özellik adları göre kabul, cmdlet'inize iki parametre diğer adlarına kullanarak her iki nesnelere bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="098c6-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="098c6-115">Belirli parametreleri ile kullanılabilecek diğer adları hakkında daha fazla bilgi için bkz. [genel parametre adları](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="098c6-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="098c6-116">Parametre diğer adlarına tanımlama</span><span class="sxs-lookup"><span data-stu-id="098c6-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="098c6-117">Bir parametre için bir diğer ad tanımlamak için aşağıdaki parametreyi bildirimde gösterildiği gibi diğer ad özniteliği bildirin.</span><span class="sxs-lookup"><span data-stu-id="098c6-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="098c6-118">Bu örnekte, birden çok diğer adı için aynı parametre olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="098c6-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="098c6-119">(Daha fazla bilgi için[Cmdlet parametreleri bildirmek için nasıl](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="098c6-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="098c6-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="098c6-120">See Also</span></span>

[<span data-ttu-id="098c6-121">Genel parametre adları</span><span class="sxs-lookup"><span data-stu-id="098c6-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="098c6-122">Cmdlet parametreleri bildirmek nasıl</span><span class="sxs-lookup"><span data-stu-id="098c6-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="098c6-123">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="098c6-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
