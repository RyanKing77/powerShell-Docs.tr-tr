---
title: Cmdlet dinamik parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986245"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="f2585-102">Cmdlet dinamik parametreleri</span><span class="sxs-lookup"><span data-stu-id="f2585-102">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="f2585-103">Cmdlet 'leri, başka bir parametrenin bağımsız değişkeninin belirli bir değer olduğu durumlar gibi özel koşullar altında Kullanıcı tarafından kullanılabilen parametreleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f2585-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="f2585-104">Bu parametreler çalışma zamanına eklenir ve yalnızca gerektiğinde eklendiğinden dinamik parametreler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f2585-104">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="f2585-105">Örneğin, yalnızca belirli bir anahtar parametresi belirtildiğinde birkaç parametre ekleyen bir cmdlet tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2585-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="f2585-106">Sağlayıcılar ve PowerShell işlevleri, dinamik parametreleri de tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f2585-106">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="f2585-107">PowerShell cmdlet 'lerinde dinamik parametreler</span><span class="sxs-lookup"><span data-stu-id="f2585-107">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="f2585-108">PowerShell, çeşitli sağlayıcı cmdlet 'lerinde dinamik parametreler kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2585-108">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="f2585-109">Örneğin `Get-Item` , `Get-ChildItem` ve cmdlet 'leri, **yol** parametresi **sertifika** sağlayıcısı yolunu belirttiğinde çalışma zamanında bir **codesigningcert** parametresi ekler.</span><span class="sxs-lookup"><span data-stu-id="f2585-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="f2585-110">**Yol** parametresi farklı bir sağlayıcı için bir yol belirtirse, **codesigningcert** parametresi kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f2585-110">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="f2585-111">Aşağıdaki örneklerde, çalıştırıldığında **codesigningcert** parametresinin çalışma zamanında `Get-Item` nasıl eklendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f2585-111">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="f2585-112">Bu örnekte, PowerShell çalışma zamanı parametresini ekledi ve cmdlet başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="f2585-112">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="f2585-113">Bu örnekte bir **dosya sistemi** sürücüsü belirtilir ve bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f2585-113">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="f2585-114">Hata iletisi **Codesigningcert** parametresinin bulunamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2585-114">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="f2585-115">Dinamik parametreler için destek</span><span class="sxs-lookup"><span data-stu-id="f2585-115">Support for dynamic parameters</span></span>

<span data-ttu-id="f2585-116">Dinamik parametreleri desteklemek için aşağıdaki öğelerin cmdlet koduna eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2585-116">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="f2585-117">Arabirim</span><span class="sxs-lookup"><span data-stu-id="f2585-117">Interface</span></span>

<span data-ttu-id="f2585-118">[System. Management. Automation. ıdynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="f2585-118">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="f2585-119">Bu arabirim, dinamik parametreleri alan yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2585-119">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="f2585-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f2585-120">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="f2585-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f2585-121">Method</span></span>

<span data-ttu-id="f2585-122">[System. Management. Automation. ıdynamicparameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="f2585-122">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="f2585-123">Bu yöntem, dinamik parametre tanımlarını içeren nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="f2585-123">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="f2585-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f2585-124">For example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a><span data-ttu-id="f2585-125">Sınıf</span><span class="sxs-lookup"><span data-stu-id="f2585-125">Class</span></span>

<span data-ttu-id="f2585-126">Eklenecek dinamik parametreleri tanımlayan bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="f2585-126">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="f2585-127">Bu sınıf her bir parametre için bir **parametre** özniteliği ve cmdlet için gereken herhangi bir Isteğe bağlı **diğer ad** ve **doğrulama** özniteliği içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f2585-127">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="f2585-128">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f2585-128">For example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="f2585-129">Dinamik parametreleri destekleyen bir cmdlet 'inin tamamen bir örneği için bkz. [dinamik parametreleri bildirme](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f2585-129">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2585-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2585-130">See also</span></span>

[<span data-ttu-id="f2585-131">System. Management. Automation. ıdynamicparameters</span><span class="sxs-lookup"><span data-stu-id="f2585-131">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="f2585-132">System. Management. Automation. ıdynamicparameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="f2585-132">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="f2585-133">Dinamik parametreleri bildirme</span><span class="sxs-lookup"><span data-stu-id="f2585-133">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="f2585-134">Windows PowerShell cmdlet 'ı yazma</span><span class="sxs-lookup"><span data-stu-id="f2585-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
