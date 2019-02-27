---
title: Liste Görünümü (Temel) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 1c683693c331ccfaf7355a0dd51801ed6fd39b3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844929"
---
# <a name="list-view-basic"></a><span data-ttu-id="6a71e-102">Liste Görünümü (Temel)</span><span class="sxs-lookup"><span data-stu-id="6a71e-102">List View (Basic)</span></span>

<span data-ttu-id="6a71e-103">Bu örnek nasıl uygulayacağınızı gösteren bir temel liste görünümü gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="6a71e-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="6a71e-104">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6a71e-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="6a71e-105">Bu örnek nasıl uygulayacağınızı gösteren bir temel liste görünümü gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="6a71e-105">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="6a71e-106">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6a71e-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="6a71e-107">Biçimlendirme bu dosyayı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="6a71e-107">To load this formatting file</span></span>

1. <span data-ttu-id="6a71e-108">XML, bu konunun Örnek bölümünde bir metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6a71e-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="6a71e-109">Metin dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6a71e-109">Save the text file.</span></span> <span data-ttu-id="6a71e-110">Eklediğinizden emin olun `format.ps1xml` biçimlendirme bir dosya olarak tanımlamak için dosya uzantısı.</span><span class="sxs-lookup"><span data-stu-id="6a71e-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="6a71e-111">Windows PowerShell'i açın ve geçerli oturuma biçimlendirme dosya yüklemek için aşağıdaki komutu çalıştırın: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="6a71e-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="6a71e-112">Bu biçimlendirme dosyası zaten bir Windows PowerShell biçimlendirme dosyasında tanımlanan bir nesnenin görüntülenmesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a71e-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="6a71e-113">Kullanmalısınız `prependPath` cmdlet'i çalıştırın ve bu biçimlendirme yüklenemiyor parametre dosyası bir modül olarak.</span><span class="sxs-lookup"><span data-stu-id="6a71e-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6a71e-114">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="6a71e-114">Demonstrates</span></span>

<span data-ttu-id="6a71e-115">Bu biçimlendirme dosyası aşağıdaki XML öğeleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="6a71e-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="6a71e-116">[Adı](./name-element-for-view-format.md) görünüm için öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a71e-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="6a71e-117">[ViewSelectedBy](./viewselectedby-element-format.md) görünüm tarafından görüntülenen hangi nesnelerin tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="6a71e-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="6a71e-118">[ListControl](./listcontrol-element-format.md) tanımlayan hangi özellik görünüm tarafından görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="6a71e-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="6a71e-119">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) tanımlayan bir liste görünümü satırda görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="6a71e-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="6a71e-120">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) tanımlayan hangi özelliğinin görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="6a71e-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="6a71e-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a71e-121">Example</span></span>

<span data-ttu-id="6a71e-122">Dört özelliklerini gösteren bir liste görünümü aşağıdaki XML tanımlar [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) nesne.</span><span class="sxs-lookup"><span data-stu-id="6a71e-122">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="6a71e-123">Her satırda özelliğin adı, özellik değeri tarafından izlenen görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6a71e-123">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <View>
    <Name>System.ServiceProcess.ServiceController</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <ListControl>
      <ListEntries>
        <ListEntry>
          <ListItems>
            <ListItem>
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="6a71e-124">Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) Bu biçim dosyası yüklendikten sonra nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6a71e-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="6a71e-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6a71e-125">See Also</span></span>

[<span data-ttu-id="6a71e-126">Biçimlendirme dosyaları örnekleri</span><span class="sxs-lookup"><span data-stu-id="6a71e-126">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="6a71e-127">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="6a71e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
