---
title: Geniş Görünüm (Temel) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849689"
---
# <a name="wide-view-basic"></a><span data-ttu-id="a0697-102">Geniş Görünüm (Temel)</span><span class="sxs-lookup"><span data-stu-id="a0697-102">Wide View (Basic)</span></span>

<span data-ttu-id="a0697-103">Bu örnek nasıl uygulayacağınızı gösteren temel bir geniş görünüm gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne `Get-Service` cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="a0697-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="a0697-104">Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a0697-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="a0697-105">Biçimlendirme bu dosyayı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="a0697-105">To load this formatting file</span></span>

1. <span data-ttu-id="a0697-106">XML, bu konunun Örnek bölümünde bir metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a0697-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="a0697-107">Metin dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a0697-107">Save the text file.</span></span> <span data-ttu-id="a0697-108">Eklediğinizden emin olun `format.ps1xml` biçimlendirme bir dosya olarak tanımlamak için dosya uzantısı.</span><span class="sxs-lookup"><span data-stu-id="a0697-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="a0697-109">Windows PowerShell'i açın ve geçerli oturuma biçimlendirme dosya yüklemek için aşağıdaki komutu çalıştırın: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="a0697-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="a0697-110">Bu biçimlendirme dosyası zaten bir Windows PowerShell biçimlendirme dosyasında tanımlanan bir nesnenin görüntülenmesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a0697-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="a0697-111">Kullanmalısınız `prependPath` cmdlet'i çalıştırın ve bu biçimlendirme yüklenemiyor parametre dosyası bir modül olarak.</span><span class="sxs-lookup"><span data-stu-id="a0697-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a0697-112">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="a0697-112">Demonstrates</span></span>

<span data-ttu-id="a0697-113">Bu biçimlendirme dosyası aşağıdaki XML öğeleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="a0697-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="a0697-114">[Adı](./name-element-for-view-format.md) görünüm için öğesi.</span><span class="sxs-lookup"><span data-stu-id="a0697-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="a0697-115">[ViewSelectedBy](./viewselectedby-element-format.md) görünüm tarafından görüntülenen hangi nesnelerin tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="a0697-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="a0697-116">[WideItem](./wideitem-element-for-widecontrol-format.md) tanımlayan hangi özellik görünüm tarafından görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="a0697-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="a0697-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0697-117">Example</span></span>

<span data-ttu-id="a0697-118">Aşağıdaki XML değerini görüntüler geniş bir görünüm tanımlar [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) özelliği.</span><span class="sxs-lookup"><span data-stu-id="a0697-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="a0697-119">Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) Bu biçim dosyası yüklendikten sonra nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a0697-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="a0697-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a0697-120">See Also</span></span>

[<span data-ttu-id="a0697-121">Biçimlendirme dosyaları örnekleri</span><span class="sxs-lookup"><span data-stu-id="a0697-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="a0697-122">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="a0697-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
