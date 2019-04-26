---
title: Geniş bir görünüm oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066728"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="d90cd-102">Geniş Görünüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d90cd-102">Creating a Wide View</span></span>

<span data-ttu-id="d90cd-103">Geniş bir görünüm, görüntülenen her nesne için tek bir değer görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d90cd-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="d90cd-104">Görüntülenen değer, bir .NET nesnesini özelliğinin değerini veya bir komut dosyası değerini olabilir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="d90cd-105">Varsayılan olarak, bu görünüm için üst bilgi veya etiket yoktur.</span><span class="sxs-lookup"><span data-stu-id="d90cd-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="d90cd-106">Geniş görünüm görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d90cd-106">A Wide View Display</span></span>

<span data-ttu-id="d90cd-107">Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) tarafından döndürülen nesne [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) çıktısını cmdlet'iyle yönetilir, cmdlet [ Biçim genelinde](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="d90cd-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="d90cd-108">(Varsayılan olarak, [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet'i bir tablo görünümü verir.) Bu örnekte, iki sütunlu, döndürülen her nesne için işlemin adını görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="d90cd-109">Nesnenin özellik adını gösterilmiyorsa, yalnızca özelliğinin değeri.</span><span class="sxs-lookup"><span data-stu-id="d90cd-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="d90cd-110">Geniş bir görünüm tanımlama</span><span class="sxs-lookup"><span data-stu-id="d90cd-110">Defining the Wide View</span></span>

<span data-ttu-id="d90cd-111">Aşağıdaki XML geniş view schema gösterir [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) nesne.</span><span class="sxs-lookup"><span data-stu-id="d90cd-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="d90cd-112">Aşağıdaki XML öğeleri, geniş bir görünüm tanımlamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="d90cd-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="d90cd-113">[Görünümü](./view-element-format.md) geniş görünüm üst öğesinin bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="d90cd-114">(Bu tablo, liste ve özel denetim görünümleri için aynı üst öğe,.)</span><span class="sxs-lookup"><span data-stu-id="d90cd-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="d90cd-115">[Adı](./name-element-for-view-format.md) öğesi, görünümün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="d90cd-116">Bu öğe tüm görünümleri için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-116">This element is required for all views.</span></span>

- <span data-ttu-id="d90cd-117">[ViewSelectedBy](./viewselectedby-element-format.md) öğe görünümünü kullanın nesneleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="d90cd-118">Bu öğe gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-118">This element is required.</span></span>

- <span data-ttu-id="d90cd-119">[GroupBy](./groupby-element-for-view-format.md) öğe yeni bir grup nesne görüntülendiğinde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="d90cd-120">Bir özel özellik veya betik değeri değiştiğinde yeni bir grup başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="d90cd-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d90cd-121">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-121">This element is optional.</span></span>

- <span data-ttu-id="d90cd-122">[Denetimleri](./controls-element-for-view-format.md) öğeleri geniş görünüm tarafından tanımlanan özel denetimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="d90cd-123">Denetimler, daha fazla verinin nasıl görüntüleneceğini belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="d90cd-124">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-124">This element is optional.</span></span> <span data-ttu-id="d90cd-125">Bir görünüm kendi özel denetimler tanımlayabilirsiniz veya biçimlendirme dosyasında herhangi bir görünüm tarafından kullanılabilen ortak denetimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="d90cd-126">Özel denetimler hakkında daha fazla bilgi için bkz: [özel denetimler oluşturma](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d90cd-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="d90cd-127">[WideControl](./widecontrol-element-format.md) öğesi ve onun alt öğeleri tanımlayan ne Görünümü'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="d90cd-128">Önceki örnekte, görünümün görüntülemek üzere tasarlanmış [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) özelliği.</span><span class="sxs-lookup"><span data-stu-id="d90cd-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="d90cd-129">Basit bir geniş görünüm tanımlayan bir tam biçimlendirme dosyası örneği için bkz. [geniş Görünüm (Temel)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d90cd-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="d90cd-130">Geniş görünümünüz için tanımları sağlama</span><span class="sxs-lookup"><span data-stu-id="d90cd-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="d90cd-131">Geniş görünümler, alt öğelerini kullanarak bir veya daha fazla tanımları sağlayabilir [WideControl](./widecontrol-element-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d90cd-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="d90cd-132">Genellikle, bir görünümü sadece bir tanım sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="d90cd-133">Aşağıdaki örnekte, değerini görüntüler tek bir tanım görünümü sağlar [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) özelliği.</span><span class="sxs-lookup"><span data-stu-id="d90cd-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="d90cd-134">Geniş bir görünüm, bir özelliğin değerini veya bir betik (örnekte gösterilmiştir değil) değerini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="d90cd-135">Aşağıdaki XML öğeleri, geniş bir görünüm tanımlarında sağlamak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d90cd-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="d90cd-136">[WideControl](./widecontrol-element-format.md) öğesi ve onun alt öğeleri tanımlayan ne Görünümü'nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="d90cd-137">[AutoSize](./autosize-element-for-widecontrol-format.md) öğesi sütun boyutu ve sütun sayısı verilerin boyutuna bağlı olarak ayarlanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="d90cd-138">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-138">This element is optional.</span></span>

- <span data-ttu-id="d90cd-139">[ColumnNumber](./columnnumber-element-for-widecontrol-format.md) öğesi geniş görüntülenmesini sütun sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="d90cd-140">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-140">This element is optional.</span></span>

- <span data-ttu-id="d90cd-141">[WideEntries](./wideentries-element-for-widecontrol-format.md) öğesi, görünümün tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="d90cd-142">Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="d90cd-143">Bu öğe gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-143">This element is required.</span></span>

- <span data-ttu-id="d90cd-144">[WideEntry](./wideentry-element-for-widecontrol-format.md) öğesi, görünümün tanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="d90cd-145">En az bir [WideEntry](./wideentry-element-for-widecontrol-format.md) gereklidir; ancak, hiçbir ekleyebileceğiniz öğe sayısı üst sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="d90cd-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="d90cd-146">Çoğu durumda, yalnızca bir tanımı bir görünüm olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="d90cd-147">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) öğesi, belirli bir tanımı tarafından görüntülenen nesneleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="d90cd-148">Bu öğe isteğe bağlıdır ve yalnızca birden çok tanımlarken gerekli [WideEntry](./wideentry-element-for-widecontrol-format.md) görüntüleme farklı nesneleri öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d90cd-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="d90cd-149">[WideItem](./wideitem-element-for-widecontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="d90cd-150">Diğer görünüm türleri aksine, geniş bir denetim, yalnızca bir öğe görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="d90cd-151">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) öğesi değeri görünüm tarafından görüntülenen özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="d90cd-152">Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d90cd-153">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="d90cd-154">Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="d90cd-155">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) verileri görüntülemek için kullanılan bir model öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="d90cd-156">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-156">This element is optional.</span></span>

<span data-ttu-id="d90cd-157">Geniş görünüm tanımı tanımlayan bir tam biçimlendirme dosyası örneği için bkz: [geniş Görünüm (Temel)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d90cd-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="d90cd-158">Geniş görünüm kullanan nesneler tanımlama</span><span class="sxs-lookup"><span data-stu-id="d90cd-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="d90cd-159">Hangi .NET nesneleri kullanan geniş görünüm tanımlamak için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="d90cd-160">Kullanabileceğiniz [ViewSelectedBy](./viewselectedby-element-format.md) görünümü veya tüm tanımları tarafından görüntülenebilen nesneler tanımlamak için kullanabileceğiniz [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) hangi nesnelerin tarafından görüntülenen tanımlamak için bir Belirli görünüm tanımı.</span><span class="sxs-lookup"><span data-stu-id="d90cd-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="d90cd-161">Çoğu durumda, nesneler genellikle tarafından tanımlanan şekilde bir görünümü sadece bir tanım vardır. [ViewSelectedBy](./viewselectedby-element-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d90cd-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="d90cd-162">Aşağıdaki örnek, geniş görünüm kullanarak görüntülenen nesneleri tanımlamak gösterilmektedir [ViewSelectedBy](./viewselectedby-element-format.md) ve [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d90cd-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d90cd-163">Sınırsız sayıda [TypeName](./typename-element-for-viewselectedby-format.md) öğeleri belirtebilirsiniz ve bunların sırası önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="d90cd-164">Aşağıdaki XML öğeleri, geniş bir görünüm tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d90cd-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="d90cd-165">[ViewSelectedBy](./viewselectedby-element-format.md) öğesi, hangi nesnelerin geniş görünüm tarafından görüntülenen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="d90cd-166">[TypeName](./typename-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen .NET belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="d90cd-167">Tam .NET türü adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="d90cd-168">En az bir türü veya görünümü için seçim belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="d90cd-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d90cd-169">Eksiksiz bir biçimlendirme dosyası örneği için bkz. [geniş Görünüm (Temel)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d90cd-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="d90cd-170">Aşağıdaki örnekte [ViewSelectedBy](./viewselectedby-element-format.md) ve [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d90cd-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="d90cd-171">Geniş bir görünüm ve aynı nesneleri için bir tablo görünümü tanımladığınızda gibi birden çok görünüm, görüntülenen nesnelerin ilgili kümesi sahip olduğu kullanma seçimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="d90cd-172">Seçimi kümesi oluşturma hakkında daha fazla bilgi için bkz. [tanımlama seçimi ayarlar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d90cd-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="d90cd-173">Aşağıdaki XML öğeleri, geniş bir görünüm tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d90cd-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="d90cd-174">[ViewSelectedBy](./viewselectedby-element-format.md) öğesi, hangi nesnelerin geniş görünüm tarafından görüntülenen tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="d90cd-175">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) öğesi görünüm tarafından görüntülenen bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="d90cd-176">En az bir seçimi kümesi veya görünüm türünü belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="d90cd-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="d90cd-177">Aşağıdaki örnek, geniş görünüm kullanarak belirli bir tanımı tarafından görüntülenecek nesneleri tanımlamak gösterilmektedir [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d90cd-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="d90cd-178">Bu öğe kullanarak, nesne, Nesne Seçimi kümesi veya tanımı kullanıldığında belirten bir seçim koşulu .NET türü adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="d90cd-179">Seçim koşullar oluşturma hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d90cd-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="d90cd-180">Aşağıdaki XML öğeleri, belirli bir geniş görünüm tanımı tarafından kullanılan nesneleri belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d90cd-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="d90cd-181">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) öğe tanımlar hangi nesnelerin tanımına göre görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="d90cd-182">[TypeName](./typename-element-for-viewselectedby-format.md) öğe tanımına göre görüntülenen .NET belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="d90cd-183">Bu öğe kullanırken tam .NET türü adı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="d90cd-184">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="d90cd-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d90cd-185">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) (gösterilmemiştir) öğesi bu tanımı tarafından görüntülenebilen bir nesne belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="d90cd-186">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="d90cd-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="d90cd-187">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (gösterilmemiştir) öğesi kullanılmak üzere bu tanım için bulunması gereken bir koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="d90cd-188">En az bir türü, seçim kümesi veya tanımı için seçim koşulu belirtmeniz gerekir, ancak belirtilebilir öğelerinin hiçbir üst limiti yoktur.</span><span class="sxs-lookup"><span data-stu-id="d90cd-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="d90cd-189">Seçimi koşulları tanımlama hakkında daha fazla bilgi için bkz. [görüntüleyen veri koşulları tanımlama](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d90cd-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="d90cd-190">Geniş bir görünüm nesnelerin gruplarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d90cd-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="d90cd-191">Gruplar halinde geniş görünüm tarafından görüntülenen nesneleri ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="d90cd-192">Yalnızca belirli bir özellik veya betik değeri değiştiğinde Windows PowerShell'in yeni bir grup başlatır. Bu bir grubu tanımlayan gelmez.</span><span class="sxs-lookup"><span data-stu-id="d90cd-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="d90cd-193">Aşağıdaki örnekte, yeni bir grup başlatıldığında her değeri [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) özellik değişiklikleri.</span><span class="sxs-lookup"><span data-stu-id="d90cd-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="d90cd-194">Aşağıdaki XML öğeleri bir grup başlatıldığında tanımlamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="d90cd-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="d90cd-195">[GroupBy](./groupby-element-for-view-format.md) öğesi, özellik veya yeni Grup başlar ve Grup nasıl görüntüleneceğini tanımlar betiği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="d90cd-196">[PropertyName](./propertyname-element-for-groupby-format.md) değeri değiştiğinde yeni bir grup başlatan özellik öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="d90cd-197">Bir özellik veya grubu başlatmak için komut dosyasını belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="d90cd-198">[ScriptBlock](./scriptblock-element-for-groupby-format.md) öğesi değeri değiştiğinde yeni bir grup başlatan komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="d90cd-199">Bir betiği veya grup başlatmak için özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="d90cd-200">[Etiket](./label-element-for-groupby-format.md) her grubu başında görüntülenen etiket öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="d90cd-201">Bu öğe tarafından belirtilen metin ek olarak, Windows PowerShell öncesi ve sonrası etiketi boş bir satır ekler ve yeni Grup tetiklenen değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d90cd-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="d90cd-202">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-202">This element is optional.</span></span>

- <span data-ttu-id="d90cd-203">[Özel denetim](./customcontrol-element-for-groupby-format.md) öğe verileri görüntülemek için kullanılan bir denetimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d90cd-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="d90cd-204">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-204">This element is optional.</span></span>

- <span data-ttu-id="d90cd-205">[CustomControlName](./customcontrolname-element-for-groupby-format.md) öğeyi belirten bir ortak veya verileri görüntülemek için kullanılan denetim görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d90cd-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="d90cd-206">Bu öğe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-206">This element is optional.</span></span>

<span data-ttu-id="d90cd-207">Grupları tanımlayan bir tam biçimlendirme dosyası örneği için bkz. [geniş Görünüm (gruplandırma ölçütü)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="d90cd-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="d90cd-208">Biçim dizeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="d90cd-208">Using Format Strings</span></span>

<span data-ttu-id="d90cd-209">Daha fazla verinin nasıl görüntüleneceğini tanımlamak için geniş bir görünüm için biçimlendirme dizeleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="d90cd-210">Aşağıdaki örnek, bir biçimlendirme dizesi değerini tanımlamak gösterilmektedir `StartTime` özelliği.</span><span class="sxs-lookup"><span data-stu-id="d90cd-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="d90cd-211">Aşağıdaki XML öğeleri, bir biçim deseni belirtmek için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d90cd-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="d90cd-212">[WideItem](./wideitem-element-for-widecontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="d90cd-213">[PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) öğesi değeri görünüm tarafından görüntülenen özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="d90cd-214">Bir özellik ya da bir komut dosyası belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="d90cd-215">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) öğesi Görünümü'nde özellik veya betik değerin nasıl görüntüleneceğini tanımlayan bir biçim deseni belirtir</span><span class="sxs-lookup"><span data-stu-id="d90cd-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="d90cd-216">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (gösterilmemiştir) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="d90cd-217">Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="d90cd-218">Aşağıdaki örnekte, `ToString` yöntemi betik değerini biçimlendirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d90cd-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="d90cd-219">Komut, bir nesnenin herhangi bir yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="d90cd-220">Bu nedenle, bir nesne gibi bir yöntem varsa `ToString`biçimlendirme parametreleri olan, betik komut çıktı değerini biçimlendirmek için bu yöntem çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="d90cd-221">Aşağıdaki XML öğesi için arama kullanılabilir `ToString` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d90cd-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="d90cd-222">[WideItem](./wideitem-element-for-widecontrol-format.md) öğesi görünüm tarafından görüntülenen verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="d90cd-223">[ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (gösterilmemiştir) öğesi değeri görünüm tarafından görüntülenen komut dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d90cd-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="d90cd-224">Bir betik ya da bir özellik belirtmeniz gerekir, ancak ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d90cd-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d90cd-225">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d90cd-225">See Also</span></span>

[<span data-ttu-id="d90cd-226">Geniş Görünüm (Temel)</span><span class="sxs-lookup"><span data-stu-id="d90cd-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="d90cd-227">Geniş Görünüm (gruplandırma ölçütü)</span><span class="sxs-lookup"><span data-stu-id="d90cd-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="d90cd-228">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="d90cd-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
