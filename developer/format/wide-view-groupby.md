---
title: Geniş Görünüm (gruplandırma ölçütü) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083663"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="7f298-102">Geniş Görünüm (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="7f298-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="7f298-103">Bu örnek nasıl uygulanacağını grupları görüntüler geniş bir görünüm gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne `Get-Service` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="7f298-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="7f298-104">Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7f298-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="7f298-105">Biçimlendirme bu dosyayı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="7f298-105">To load this formatting file</span></span>

1. <span data-ttu-id="7f298-106">XML, bu konunun Örnek bölümünde bir metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7f298-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="7f298-107">Metin dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7f298-107">Save the text file.</span></span> <span data-ttu-id="7f298-108">Eklediğinizden emin olun `format.ps1xml` biçimlendirme bir dosya olarak tanımlamak için dosya uzantısı.</span><span class="sxs-lookup"><span data-stu-id="7f298-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="7f298-109">Windows PowerShell'i açın ve geçerli oturuma biçimlendirme dosya yüklemek için aşağıdaki komutu çalıştırın: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="7f298-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="7f298-110">Biçimlendirme bu dosya, görüntü dosyaları biçimlendirme bir Windows PowerShell tarafından zaten tanımlanmış bir nesnenin tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7f298-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="7f298-111">Kullanmalısınız `prependPath` cmdlet'i çalıştırın ve bu biçimlendirme yüklenemiyor parametre dosyası bir modül olarak.</span><span class="sxs-lookup"><span data-stu-id="7f298-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7f298-112">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="7f298-112">Demonstrates</span></span>

<span data-ttu-id="7f298-113">Bu biçimlendirme dosyası aşağıdaki XML öğeleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="7f298-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="7f298-114">[Adı](./name-element-for-view-format.md) görünüm için öğesi.</span><span class="sxs-lookup"><span data-stu-id="7f298-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="7f298-115">[ViewSelectedBy](./viewselectedby-element-format.md) görünüm tarafından görüntülenen hangi nesnelerin tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="7f298-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="7f298-116">[GroupBy](./groupby-element-for-view-format.md) tanımlayan yeni bir grup görüntülendiğinde öğe.</span><span class="sxs-lookup"><span data-stu-id="7f298-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="7f298-117">[WideItem](./wideitem-element-for-widecontrol-format.md) tanımlayan hangi özellik görünüm tarafından görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="7f298-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="7f298-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f298-118">Example</span></span>

<span data-ttu-id="7f298-119">Aşağıdaki XML nesne görüntüler geniş bir görünüm tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7f298-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="7f298-120">Her yeni Grup çalışmaya zaman değerini [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) özellik değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="7f298-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="7f298-121">Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) Bu biçim dosyası yüklendikten sonra nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7f298-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="7f298-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7f298-122">See Also</span></span>

[<span data-ttu-id="7f298-123">Biçimlendirme dosyaları örnekleri</span><span class="sxs-lookup"><span data-stu-id="7f298-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="7f298-124">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="7f298-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
