---
title: Parametre olarak özellikleri bildirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850578"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="73496-102">Özellikleri Parametre Olarak Bildirme</span><span class="sxs-lookup"><span data-stu-id="73496-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="73496-103">Bu konu, bir cmdlet parametreleri bildirmek önce anlamanız gereken temel bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="73496-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="73496-104">Cmdlet Sınıfınız içinde bir cmdlet parametreleri bildirmek için her parametreyi temsil eden genel özelliklerini tanımlamak ve ardından her bir özellik için bir veya daha fazla parametre öznitelikleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="73496-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="73496-105">Windows PowerShell çalışma zamanı parametre öznitelikleri özelliği bir cmdlet parametresi olarak tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="73496-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="73496-106">Parametre özniteliği bildirmek için temel söz dizimi `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="73496-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="73496-107">Gerekli parametre olarak tanımlanmış bir özellik bir örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="73496-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="73496-108">Parametreleri hakkında hatırlamak işlemlerden bazıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="73496-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="73496-109">Bir parametre açıkça genel olarak işaretlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="73496-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="73496-110">İç ortak varsayılan olarak işaretlenmez ve Windows PowerShell çalışma zamanı tarafından bulunmaz parametreler.</span><span class="sxs-lookup"><span data-stu-id="73496-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="73496-111">Parametreleri daha iyi parametre doğrulaması sağlamak için Microsoft .NET Framework türleri'olarak tanımlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="73496-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="73496-112">Örneğin, bir değerler kümesi dışında bir değer sınırlı parametreleri bir numaralandırma türü tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73496-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="73496-113">Bir Tekdüzen Kaynak Tanımlayıcısı (URI) değeri parametre türünden olmalıdır [System.Uri](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="73496-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="73496-114">Temel dize parametreleri tüm serbest biçimli metin özellikleri kaçının.</span><span class="sxs-lookup"><span data-stu-id="73496-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="73496-115">Bir parametre, parametre kümeleri herhangi bir sayıda ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73496-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="73496-116">Parametre kümeleri hakkında daha fazla bilgi için bkz. [cmdlet'i parametre ayarlar](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="73496-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="73496-117">Windows PowerShell, ayrıca her cmdlet için otomatik olarak kullanılabilen ortak parametreler kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="73496-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="73496-118">Bu parametreler ve bunların diğer adları hakkında daha fazla bilgi için bkz. [Cmdlet genel parametreleri](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="73496-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73496-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="73496-119">See Also</span></span>

[<span data-ttu-id="73496-120">Cmdlet ortak parametreleri</span><span class="sxs-lookup"><span data-stu-id="73496-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="73496-121">Cmdlet parametresi türü</span><span class="sxs-lookup"><span data-stu-id="73496-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="73496-122">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="73496-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
