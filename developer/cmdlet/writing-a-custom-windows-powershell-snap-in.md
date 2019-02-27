---
title: Bir özel Windows PowerShell ek bileşenini yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 20b7fdce1d31e3dee4598a7595962fca1c99d80a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851957"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="62a6b-102">Özel Windows PowerShell Ek Bileşeni Yazma</span><span class="sxs-lookup"><span data-stu-id="62a6b-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="62a6b-103">Bu örnek, bazı cmdlet'ler kaydeder bir Windows PowerShell ek bileşenini yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="62a6b-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="62a6b-104">Bu tür ek bileşeninin hangi cmdlet'leri, sağlayıcıları, türleri veya biçimleri kaydetmek için belirtin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="62a6b-105">Bir derlemede tüm cmdlet'leri ve sağlayıcıları kaydettirir bir ek bileşenini yazma hakkında daha fazla bilgi için bkz. [yazma bir Windows PowerShell ek bileşenini](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="62a6b-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="62a6b-106">Bir Windows PowerShell ek bileşenini yazmak için bazı cmdlet'ler kaydeder.</span><span class="sxs-lookup"><span data-stu-id="62a6b-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="62a6b-107">RunInstallerAttribute özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="62a6b-108">Türetilen bir ortak sınıf oluşturun [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="62a6b-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="62a6b-109">Bu örnekte, "CustomPSSnapinTest" sınıf adıdır.</span><span class="sxs-lookup"><span data-stu-id="62a6b-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="62a6b-110">(Gerekli) ek bileşenini adı için bir ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="62a6b-111">Ek bileşenler adlandırırken şu karakterlerin hiçbirini kullanmayın: #.</span><span class="sxs-lookup"><span data-stu-id="62a6b-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="62a6b-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="62a6b-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="62a6b-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="62a6b-113">@ \` \*</span></span>

   <span data-ttu-id="62a6b-114">Bu örnekte ek bileşenini "CustomPSSnapInTest" adıdır.</span><span class="sxs-lookup"><span data-stu-id="62a6b-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="62a6b-115">(Gerekli) ek bileşenini, satıcı için ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="62a6b-116">Bu örnekte, satıcı "Microsoft" ise.</span><span class="sxs-lookup"><span data-stu-id="62a6b-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="62a6b-117">Satıcı kaynak ek bileşeninin (isteğe bağlı) için bir ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="62a6b-118">Bu örnekte, "CustomPSSnapInTest, Microsoft" Satıcı kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="62a6b-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="62a6b-119">(Gerekli) ek bileşenini açıklaması için bir ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="62a6b-120">Bu örnekte, bir açıklaması verilmiştir: "Bu bir özel Windows PowerShell ek-Test-HelloWorld ve Test CustomSnapinTest cmdlet'leri içeren bileşenidir".</span><span class="sxs-lookup"><span data-stu-id="62a6b-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="62a6b-121">Açıklama kaynağı ek bileşeninin (isteğe bağlı) için bir ortak özelliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="62a6b-122">Bu örnekte, "CustomPSSnapInTest, bir özel Windows PowerShell Test-HelloWorld ve Test CustomSnapinTest cmdlet'leri içeren eklentisini budur" Satıcı kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="62a6b-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="62a6b-123">Özel ek bileşenini (isteğe bağlı) kullanarak ait cmdlet'lerin belirtin [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="62a6b-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="62a6b-124">Buraya eklenen bilgilerin (cmdlet Yardım dosya adının biçimi name.dll help.xml olmalıdır) cmdlet Yardım dosyası adı cmdlet ve .NET türü adını içerir.</span><span class="sxs-lookup"><span data-stu-id="62a6b-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="62a6b-125">Bu örnek, Test-HelloWorld ve TestCustomSnapinTest cmdlet'leri ekler.</span><span class="sxs-lookup"><span data-stu-id="62a6b-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="62a6b-126">Özel ek bileşenini (isteğe bağlı) ait sağlayıcılarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="62a6b-127">Bu örnek, bir sağlayıcısı belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="62a6b-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="62a6b-128">Özel ek bileşenini (isteğe bağlı) ait türlerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="62a6b-129">Bu örnek, herhangi bir tür belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="62a6b-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="62a6b-130">Özel ek bileşenini (isteğe bağlı) ait biçimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="62a6b-131">Bu örnek, diğer biçimleri belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="62a6b-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="62a6b-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="62a6b-132">Example</span></span>

<span data-ttu-id="62a6b-133">Bu örnekte, Test-HelloWorld ve Test CustomSnapinTest cmdlet'lerini kaydetmek için kullanılan bir özel Windows PowerShell ek bileşenini yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="62a6b-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="62a6b-134">Bu örnekte, tam derleme diğer cmdlet'leri ve bu eklenti tarafından kayıtlı değil sağlayıcılarını içerebilir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="62a6b-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="62a6b-135">Eklentileri kaydetme hakkında daha fazla bilgi için bkz. [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) içinde [Windows PowerShell Programcı Kılavuzu](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="62a6b-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62a6b-136">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="62a6b-136">See Also</span></span>

[<span data-ttu-id="62a6b-137">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="62a6b-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="62a6b-138">Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl</span><span class="sxs-lookup"><span data-stu-id="62a6b-138">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="62a6b-139">Windows PowerShell Kabuk SDK'sı</span><span class="sxs-lookup"><span data-stu-id="62a6b-139">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
