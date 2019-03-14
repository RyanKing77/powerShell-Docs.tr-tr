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
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794833"
---
# <a name="list-view-labels"></a>Liste Görünümü (Etiketler)

Bu örnekte, listenin her satır için özel bir etiket gösteren bir liste görünümü uygulamak gösterilmektedir. Bu liste görünümü özelliklerini görüntüler [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet'i. Bir liste görünümü bileşenler hakkında daha fazla bilgi için bkz. [bir liste görünümü oluşturma](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Biçimlendirme bu dosyayı yüklemek için

1. XML, bu konunun Örnek bölümünde bir metin dosyasına kopyalayın.

2. Metin dosyasını kaydedin. Eklediğinizden emin olun `format.ps1xml` biçimlendirme bir dosya olarak tanımlamak için dosya uzantısı.

3. Windows PowerShell'i açın ve geçerli oturuma biçimlendirme dosya yüklemek için aşağıdaki komutu çalıştırın: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Bu biçimlendirme dosyası zaten bir Windows PowerShell biçimlendirme dosyasında tanımlanan bir nesnenin görüntülenmesini tanımlar. Kullanmalısınız `prependPath` cmdlet'i çalıştırın ve bu biçimlendirme yüklenemiyor parametre dosyası bir modül olarak.

## <a name="demonstrates"></a>Gösteriler

Bu biçimlendirme dosyası aşağıdaki XML öğeleri gösterir:

- [Adı](./name-element-for-view-format.md) görünüm için öğesi.

- [ViewSelectedBy](./viewselectedby-element-format.md) görünüm tarafından görüntülenen hangi nesnelerin tanımlayan öğe.

- [ListControl](./listcontrol-element-format.md) tanımlayan hangi özellik görünüm tarafından görüntülenen öğe.

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) tanımlayan bir liste görünümü satırda görüntülenen öğe.

- [Etiket](./label-element-for-listitem-for-listcontrol-format.md) tanımlayan bir liste görünümü satırda görüntülenen öğe.

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) tanımlayan hangi özelliğinin görüntülenen öğe.

## <a name="example"></a>Örnek

Her satırda bir özel etiket görüntüleyen bir liste görünümü aşağıdaki XML tanımlar. Bu durumda, özellik adı büyük harfle her bir harf ile ve "özelliği" sözcüğü etiketi içerir. Her satırda özelliğin adı, özellik değeri tarafından izlenen görüntülenir.

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

Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) Bu biçim dosyası yüklendikten sonra nesneleri.

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

## <a name="see-also"></a>Ayrıca bkz:

[Biçimlendirme dosyaları örnekleri](./examples-of-formatting-files.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
