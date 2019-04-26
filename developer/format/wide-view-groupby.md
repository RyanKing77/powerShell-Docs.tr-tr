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
# <a name="wide-view-groupby"></a>Geniş Görünüm (GroupBy)

Bu örnek nasıl uygulanacağını grupları görüntüler geniş bir görünüm gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) tarafından döndürülen nesne `Get-Service` cmdlet'i. Geniş bir görünüm bileşenleri hakkında daha fazla bilgi için bkz. [geniş bir görünüm oluşturma](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Biçimlendirme bu dosyayı yüklemek için

1. XML, bu konunun Örnek bölümünde bir metin dosyasına kopyalayın.

2. Metin dosyasını kaydedin. Eklediğinizden emin olun `format.ps1xml` biçimlendirme bir dosya olarak tanımlamak için dosya uzantısı.

3. Windows PowerShell'i açın ve geçerli oturuma biçimlendirme dosya yüklemek için aşağıdaki komutu çalıştırın: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Biçimlendirme bu dosya, görüntü dosyaları biçimlendirme bir Windows PowerShell tarafından zaten tanımlanmış bir nesnenin tanımlar. Kullanmalısınız `prependPath` cmdlet'i çalıştırın ve bu biçimlendirme yüklenemiyor parametre dosyası bir modül olarak.

## <a name="demonstrates"></a>Gösteriler

Bu biçimlendirme dosyası aşağıdaki XML öğeleri gösterir:

- [Adı](./name-element-for-view-format.md) görünüm için öğesi.

- [ViewSelectedBy](./viewselectedby-element-format.md) görünüm tarafından görüntülenen hangi nesnelerin tanımlayan öğe.

- [GroupBy](./groupby-element-for-view-format.md) tanımlayan yeni bir grup görüntülendiğinde öğe.

- [WideItem](./wideitem-element-for-widecontrol-format.md) tanımlayan hangi özellik görünüm tarafından görüntülenen öğe.

## <a name="example"></a>Örnek

Aşağıdaki XML nesne görüntüler geniş bir görünüm tanımlar. Her yeni Grup çalışmaya zaman değerini [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) özellik değişiklikleri.

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

Aşağıdaki örnek Windows PowerShell biçimini gösterir [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) Bu biçim dosyası yüklendikten sonra nesneleri.

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

## <a name="see-also"></a>Ayrıca bkz:

[Biçimlendirme dosyaları örnekleri](./examples-of-formatting-files.md)

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
