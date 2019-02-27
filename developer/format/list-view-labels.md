---
title: Liste Görünümü (etiketler) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 2bb62ab3e4fa1db9b3af8c82eb9035aa4f3e31c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849703"
---
# <a name="list-view-labels"></a><span data-ttu-id="e5dc2-102">Liste Görünümü (Etiketler)</span><span class="sxs-lookup"><span data-stu-id="e5dc2-102">List View (Labels)</span></span>

<span data-ttu-id="e5dc2-103">Bu örnekte, listenin her satır için özel bir etiket gösteren bir liste görünümü uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="e5dc2-104">Bu liste görünümü özelliklerini görüntüler [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="e5dc2-105">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e5dc2-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="e5dc2-106">Bu örnekte, listenin her satır için özel bir etiket gösteren bir liste görünümü uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-106">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="e5dc2-107">Bu liste görünümü özelliklerini görüntüler [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="e5dc2-108">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e5dc2-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="e5dc2-109">Biçimlendirme bu dosyayı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="e5dc2-109">To load this formatting file</span></span>

1. <span data-ttu-id="e5dc2-110">XML, bu konunun Örnek bölümünde bir metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="e5dc2-111">Metin dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-111">Save the text file.</span></span> <span data-ttu-id="e5dc2-112">Eklediğinizden emin olun `format.ps1xml` biçimlendirme bir dosya olarak tanımlamak için dosya uzantısı.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="e5dc2-113">Windows PowerShell'i açın ve geçerli oturuma biçimlendirme dosya yüklemek için aşağıdaki komutu çalıştırın: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="e5dc2-114">Bu biçimlendirme dosyası zaten bir Windows PowerShell biçimlendirme dosyasında tanımlanan bir nesnenin görüntülenmesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="e5dc2-115">Kullanmalısınız `prependPath` cmdlet'i çalıştırın ve bu biçimlendirme yüklenemiyor parametre dosyası bir modül olarak.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e5dc2-116">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="e5dc2-116">Demonstrates</span></span>

<span data-ttu-id="e5dc2-117">Bu biçimlendirme dosyası aşağıdaki XML öğeleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="e5dc2-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="e5dc2-118">[Adı](./name-element-for-view-format.md) görünüm için öğesi.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="e5dc2-119">[ViewSelectedBy](./viewselectedby-element-format.md) görünüm tarafından görüntülenen hangi nesnelerin tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="e5dc2-120">[ListControl](./listcontrol-element-format.md) tanımlayan hangi özellik görünüm tarafından görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-120">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="e5dc2-121">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) tanımlayan bir liste görünümü satırda görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-121">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="e5dc2-122">[Etiket](./label-element-for-listitem-for-listcontrol-format.md) tanımlayan bir liste görünümü satırda görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-122">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="e5dc2-123">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) tanımlayan hangi özelliğinin görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="e5dc2-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5dc2-124">Example</span></span>

<span data-ttu-id="e5dc2-125">Her satırda bir özel etiket görüntüleyen bir liste görünümü aşağıdaki XML tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-125">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="e5dc2-126">Bu durumda, özellik adı büyük harfle her bir harf ile ve "özelliği" sözcüğü etiketi içerir.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-126">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="e5dc2-127">Her satırda özelliğin adı, özellik değeri tarafından izlenen görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-127">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
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
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="e5dc2-128">Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) Bu biçim dosyası yüklendikten sonra nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e5dc2-128">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="e5dc2-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e5dc2-129">See Also</span></span>

[<span data-ttu-id="e5dc2-130">Biçimlendirme dosyaları örnekleri</span><span class="sxs-lookup"><span data-stu-id="e5dc2-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="e5dc2-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="e5dc2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
