---
title: Basit bir Cmdlet yazma | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 2fc1a3947ca6076387ea85d7f8ba9018ed7385a0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849535"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="602c0-102">Bir cmdlet yazma</span><span class="sxs-lookup"><span data-stu-id="602c0-102">How to write a cmdlet</span></span>

<span data-ttu-id="602c0-103">Bu makalede, bir cmdlet'in yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="602c0-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="602c0-104">**Gönderme Karşılama** cmdlet'i tek bir kullanıcı adı giriş olarak alır ve ardından o kullanıcıya bir karşılama yazar.</span><span class="sxs-lookup"><span data-stu-id="602c0-104">The **Send-Greeting** cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="602c0-105">Bu örnekte, cmdlet kadar iş yapmaz olsa da, bir cmdlet'in ana bölümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="602c0-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="602c0-106">Bir cmdlet yazma adımları</span><span class="sxs-lookup"><span data-stu-id="602c0-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="602c0-107">Sınıf bir cmdlet olarak bildirmek için kullanın **cmdlet'i** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="602c0-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="602c0-108">**Cmdlet'i** fiil ve isim için cmdlet adı özniteliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="602c0-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="602c0-109">Hakkında daha fazla bilgi için **cmdlet'i** özniteliği için bkz: [CmdletAttribute bildirimi](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="602c0-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="602c0-110">Sınıfın adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="602c0-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="602c0-111">Cmdlet aşağıdaki sınıflar birinden türetilen belirtin:</span><span class="sxs-lookup"><span data-stu-id="602c0-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="602c0-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="602c0-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="602c0-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="602c0-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="602c0-114">Cmdlet parametrelerini tanımlamak için **parametre** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="602c0-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="602c0-115">Bu durumda, yalnızca bir parametresi belirtilen gereklidir.</span><span class="sxs-lookup"><span data-stu-id="602c0-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="602c0-116">Hakkında daha fazla bilgi için **parametre** özniteliği için bkz: [ParameterAttribute bildirimi](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="602c0-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="602c0-117">Giriş işleme giriş işler yöntemi yok sayın.</span><span class="sxs-lookup"><span data-stu-id="602c0-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="602c0-118">Bu durumda, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi geçersiz kılınmıştır.</span><span class="sxs-lookup"><span data-stu-id="602c0-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="602c0-119">Karşılama yazılacak yöntemin kullanın [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="602c0-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="602c0-120">Karşılama şu biçimde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="602c0-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="602c0-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="602c0-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify and
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="602c0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="602c0-122">See also</span></span>

[<span data-ttu-id="602c0-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="602c0-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="602c0-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="602c0-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="602c0-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="602c0-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="602c0-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="602c0-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="602c0-127">CmdletAttribute bildirimi</span><span class="sxs-lookup"><span data-stu-id="602c0-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="602c0-128">ParameterAttribute bildirimi</span><span class="sxs-lookup"><span data-stu-id="602c0-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="602c0-129">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="602c0-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
