---
title: Liste Görünümü (gruplandırma ölçütü) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849717"
---
# <a name="list-view-groupby"></a><span data-ttu-id="08e74-102">Liste Görünümü (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="08e74-102">List View (GroupBy)</span></span>

<span data-ttu-id="08e74-103">Bu örnek nasıl uygulanacağını listesi satırlarını gruplar halinde ayıran bir liste görünümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="08e74-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="08e74-104">Bu liste görünümü özelliklerini görüntüler [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="08e74-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="08e74-105">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="08e74-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="08e74-106">Bu örnek nasıl uygulanacağını listesi satırlarını gruplar halinde ayıran bir liste görünümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="08e74-106">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="08e74-107">Bu liste görünümü özelliklerini görüntüler [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="08e74-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="08e74-108">Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="08e74-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="08e74-109">Biçimlendirme bu dosyayı yüklemek için</span><span class="sxs-lookup"><span data-stu-id="08e74-109">To load this formatting file</span></span>

1. <span data-ttu-id="08e74-110">XML, bu konunun Örnek bölümünde bir metin dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="08e74-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="08e74-111">Metin dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="08e74-111">Save the text file.</span></span> <span data-ttu-id="08e74-112">Eklediğinizden emin olun `format.ps1xml` biçimlendirme bir dosya olarak tanımlamak için dosya uzantısı.</span><span class="sxs-lookup"><span data-stu-id="08e74-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="08e74-113">Windows PowerShell'i açın ve geçerli oturuma biçimlendirme dosya yüklemek için aşağıdaki komutu çalıştırın: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="08e74-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="08e74-114">Bu biçimlendirme dosyası zaten bir Windows PowerShell biçimlendirme dosyasında tanımlanan bir nesnenin görüntülenmesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08e74-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="08e74-115">Kullanmalısınız `prependPath` cmdlet'i çalıştırın ve bu biçimlendirme yüklenemiyor parametre dosyası bir modül olarak.</span><span class="sxs-lookup"><span data-stu-id="08e74-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="08e74-116">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="08e74-116">Demonstrates</span></span>

<span data-ttu-id="08e74-117">Bu biçimlendirme dosyası aşağıdaki XML öğeleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="08e74-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="08e74-118">[Adı](./name-element-for-view-format.md) görünüm için öğesi.</span><span class="sxs-lookup"><span data-stu-id="08e74-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="08e74-119">[ViewSelectedBy](./viewselectedby-element-format.md) görünüm tarafından görüntülenen hangi nesnelerin tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="08e74-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="08e74-120">[GroupBy](./viewselectedby-element-format.md) yeni bir grup nesnelerin nasıl görüntüleneceğini tanımlayan öğe.</span><span class="sxs-lookup"><span data-stu-id="08e74-120">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="08e74-121">[ListControl](./listcontrol-element-format.md) tanımlayan hangi özellik görünüm tarafından görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="08e74-121">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="08e74-122">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) tanımlayan bir liste görünümü satırda görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="08e74-122">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="08e74-123">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) tanımlayan hangi özelliğinin görüntülenen öğe.</span><span class="sxs-lookup"><span data-stu-id="08e74-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="08e74-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="08e74-124">Example</span></span>

<span data-ttu-id="08e74-125">Yeni başlayan bir liste görünümü aşağıdaki XML tanımlar her grup değerini [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) özellik değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="08e74-125">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="08e74-126">Her Grup başlatıldığında özelliğinin yeni değeri içeren özel bir etiket görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="08e74-126">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
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

<span data-ttu-id="08e74-127">Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) Bu biçim dosyası yüklendikten sonra nesneleri.</span><span class="sxs-lookup"><span data-stu-id="08e74-127">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="08e74-128">Önce ve sonra Grup etiketi eklenen boş satırlar, Windows PowerShell tarafından otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="08e74-128">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="08e74-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="08e74-129">See Also</span></span>

[<span data-ttu-id="08e74-130">Biçimlendirme dosyaları örnekleri</span><span class="sxs-lookup"><span data-stu-id="08e74-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="08e74-131">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="08e74-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
