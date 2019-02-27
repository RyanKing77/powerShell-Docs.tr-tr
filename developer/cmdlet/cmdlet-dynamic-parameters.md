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
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845279"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="55e32-102">Cmdlet Dinamik Parametreler</span><span class="sxs-lookup"><span data-stu-id="55e32-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="55e32-103">Cmdlet'leri kullanıcının belirli bir değerin başka bir parametre bağımsız değişkeni olduğunda gibi özel koşullarda parametrelerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55e32-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="55e32-104">Bu parametreleri çalışma zamanında eklenir ve denir *dinamik parametreleri* çünkü yalnızca ihtiyacınız olduğunda eklenir.</span><span class="sxs-lookup"><span data-stu-id="55e32-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="55e32-105">Örneğin, yalnızca belirli anahtar parametresi belirtildiğinde, birkaç parametre ekleyen bir cmdlet tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55e32-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="55e32-106">Sağlayıcıları ve Windows PowerShell işlevleri dinamik parametreler de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55e32-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="55e32-107">Windows PowerShell cmdlet'lerinde dinamik parametreler</span><span class="sxs-lookup"><span data-stu-id="55e32-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="55e32-108">Windows PowerShell sağlayıcısı cmdlet'lerini bazılarını dinamik parametreler kullanır.</span><span class="sxs-lookup"><span data-stu-id="55e32-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="55e32-109">Örneğin, `Get-Item` ve `Get-ChildItem` cmdlet'leri eklendi bir `CodeSigningCert` zamanında parametre olduğunda `Path` cmdlet parametresi sertifika sağlayıcısı yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="55e32-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="55e32-110">Varsa `Path` cmdlet parametresi, farklı bir sağlayıcı için bir yol belirtir `CodeSigningCert` parametresi kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="55e32-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="55e32-111">Aşağıdaki örneklerde gösterildiği nasıl `CodeSigningCert` parametresi, çalışma zamanında eklenir, `Get-Item` cmdlet'ini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55e32-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="55e32-112">İlk örnekte, Windows PowerShell çalışma zamanı parametresi eklendi ve cmdlet başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="55e32-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="55e32-113">İkinci örnekte, bir dosya sistemi sürücü belirtilir ve bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="55e32-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="55e32-114">Hata iletisi gösterir `CodeSigningCert` parametresi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="55e32-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="55e32-115">Dinamik parametreleri için destek</span><span class="sxs-lookup"><span data-stu-id="55e32-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="55e32-116">Dinamik parametreleri desteklemek için cmdlet kod aşağıdaki öğeleri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="55e32-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="55e32-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) dinamik parametreleri alır, yöntem bu arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="55e32-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="55e32-118">Örnek:</span><span class="sxs-lookup"><span data-stu-id="55e32-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="55e32-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) bu yöntem dinamik parametre tanımları içeren nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="55e32-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="55e32-120">Örnek:</span><span class="sxs-lookup"><span data-stu-id="55e32-120">Example:</span></span>

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

<span data-ttu-id="55e32-121">Bu sınıf, dinamik parametre sınıfı eklenecek parametreleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55e32-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="55e32-122">Bu sınıf, her bir parametre ve cmdlet tarafından gerekli olan isteğe bağlı diğer ad ve doğrulama öznitelikleri için bir parametre özniteliği içermelidir.</span><span class="sxs-lookup"><span data-stu-id="55e32-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="55e32-123">Örnek:</span><span class="sxs-lookup"><span data-stu-id="55e32-123">Example:</span></span>

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

<span data-ttu-id="55e32-124">Dinamik parametreleri destekleyen bir cmdlet tam bir örnek için bkz: [nasıl dinamik parametreleri bildirmek için](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="55e32-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55e32-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="55e32-125">See Also</span></span>

[<span data-ttu-id="55e32-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="55e32-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="55e32-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="55e32-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="55e32-128">Dinamik parametreleri bildirmek nasıl</span><span class="sxs-lookup"><span data-stu-id="55e32-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="55e32-129">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="55e32-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
