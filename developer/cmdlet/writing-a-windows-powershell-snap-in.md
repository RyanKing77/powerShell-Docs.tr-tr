---
title: Bir Windows PowerShell ek bileşenini yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: d4f57c062fee09e85c290445082be745ab229985
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795044"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="3e694-102">Windows PowerShell Ek Bileşeni Yazma</span><span class="sxs-lookup"><span data-stu-id="3e694-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="3e694-103">Bu örnek, bir derlemede tüm cmdlet'leri ve Windows PowerShell sağlayıcıları kaydetmek için kullanılan bir Windows PowerShell ek bileşenini yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e694-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="3e694-104">Bu tür ek bileşeninin hangi cmdlet'lerini ve sağlayıcıları kaydetmek istediğiniz seçmeyin.</span><span class="sxs-lookup"><span data-stu-id="3e694-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="3e694-105">Ne kayıtlı seçmenizi sağlayan bir ek bileşenini yazmak için bkz: [bir özel Windows PowerShell ek bileşenini yazma](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="3e694-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="3e694-106">Windows PowerShell Ek Bileşeni Yazma</span><span class="sxs-lookup"><span data-stu-id="3e694-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="3e694-107">RunInstallerAttribute özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e694-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="3e694-108">Türetilen bir ortak sınıf oluşturun [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3e694-108">Create a public class that derives from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="3e694-109">Bu örnekte, "GetProcPSSnapIn01" sınıf adıdır.</span><span class="sxs-lookup"><span data-stu-id="3e694-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="3e694-110">(Gerekli) ek bileşenini adı için bir ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e694-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="3e694-111">Ek bileşenler adlandırırken şu karakterlerin hiçbirini kullanmayın: #.</span><span class="sxs-lookup"><span data-stu-id="3e694-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="3e694-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="3e694-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="3e694-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="3e694-113">@ \` \*</span></span>

    <span data-ttu-id="3e694-114">Bu örnekte ek bileşenini "GetProcPSSnapIn01" adıdır.</span><span class="sxs-lookup"><span data-stu-id="3e694-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="3e694-115">(Gerekli) ek bileşenini, satıcı için ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e694-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="3e694-116">Bu örnekte, satıcı "Microsoft" ise.</span><span class="sxs-lookup"><span data-stu-id="3e694-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="3e694-117">Satıcı kaynak ek bileşeninin (isteğe bağlı) için bir ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e694-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="3e694-118">Bu örnekte, "GetProcPSSnapIn01, Microsoft" Satıcı kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="3e694-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="3e694-119">(Gerekli) ek bileşenini açıklaması için bir ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e694-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="3e694-120">Bu örnekte, "Get-proc cmdlet kaydeder bir Windows PowerShell ek bileşenini budur" açıklamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3e694-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="3e694-121">Açıklama kaynağı ek bileşeninin (isteğe bağlı) için bir ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e694-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="3e694-122">Bu örnekte, "GetProcPSSnapIn01, bu cmdlet get-proc kaydeder bir Windows PowerShell ek bileşenini bir" Satıcı kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="3e694-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="3e694-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e694-123">Example</span></span>

<span data-ttu-id="3e694-124">Bu örnekte, Get-Proc cmdlet Windows PowerShell shell'de kaydetmek için kullanılan bir Windows PowerShell ek bileşenini yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e694-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="3e694-125">Bu örnekte, tam derleme yalnızca GetProcPSSnapIn01 eklentisini sınıfı ve Get-Proc cmdlet'i sınıfı içerecektir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3e694-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="3e694-126">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3e694-126">See Also</span></span>

[<span data-ttu-id="3e694-127">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="3e694-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3e694-128">Windows PowerShell Kabuk SDK'sı</span><span class="sxs-lookup"><span data-stu-id="3e694-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
