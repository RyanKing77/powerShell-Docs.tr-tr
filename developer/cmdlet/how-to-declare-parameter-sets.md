---
title: Parametre kümeleri nasıl | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067901"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="c634e-102">Parametre Kümelerini Bildirme</span><span class="sxs-lookup"><span data-stu-id="c634e-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="c634e-103">Bu örnek, bir cmdlet parametreleri bildirdiğinizde, iki parametre kümeleri tanımlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c634e-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="c634e-104">Her parametre kümesi benzersiz bir parametre hem de her iki parametre kümeleri tarafından kullanılan paylaşılan bir parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="c634e-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="c634e-105">Varsayılan parametre kümesi belirleme de dahil olmak üzere, parametre kümeleri hakkında daha fazla bilgi için bkz. [cmdlet'i parametre ayarlar](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c634e-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c634e-106">Mümkün olduğunda, gerekli bir parametre bir parametrenin benzersiz parametre tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c634e-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="c634e-107">Ancak, herhangi bir parametre belirtmeden çalıştırılacak cmdlet'inize istiyorsanız benzersiz parametresi isteğe bağlı bir parametre olabilir.</span><span class="sxs-lookup"><span data-stu-id="c634e-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="c634e-108">Örneğin, benzersiz parametresinin `Get-Command` cmdlet'i, isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c634e-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="c634e-109">İki parametre kümesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="c634e-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="c634e-110">Ekleme `ParameterSet` benzersiz parametresi ilk parametre kümesi için parametre özniteliği için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c634e-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="c634e-111">Ekleme `ParameterSet` ikinci parametre kümesi benzersiz parametresi için parametre özniteliği için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c634e-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="c634e-112">Her iki parametre kümelerine ait parametresi için her parametre kümesi için bir parametre özniteliği ekleyin ve sonra ekleyin `ParameterSet` anahtar sözcüğü her kümesi.</span><span class="sxs-lookup"><span data-stu-id="c634e-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="c634e-113">Her parametre özniteliği, bu parametrenin nasıl tanımlandığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c634e-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="c634e-114">Bir parametre, isteğe bağlı bir kümede bulunan ve başka bir zorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="c634e-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="c634e-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c634e-115">See Also</span></span>

[<span data-ttu-id="c634e-116">Cmdlet parametre kümeleri</span><span class="sxs-lookup"><span data-stu-id="c634e-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="c634e-117">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="c634e-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
