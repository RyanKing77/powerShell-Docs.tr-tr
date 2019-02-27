---
title: Özel denetimler oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844852"
---
# <a name="creating-custom-controls"></a>Özel Denetimler Oluşturma

Özel denetimler biçimlendirme bir dosyanın en esnek bileşenlerdir. Tablo, liste ve verileri içeren bir tablo gibi veri biçimsel bir yapı tanımla geniş görünümleri aksine özel denetimler tek bir veri parçasının nasıl görüntüleneceğini tanımlamanızı sağlar. Ortak bir dizi biçimlendirme dosyanın tüm görünümleri için kullanılabilen özel denetimler tanımlayabilirsiniz, belirli bir görünüm için kullanılabilen özel denetimler tanımlayabilirsiniz ve nesnelerin bir gruba kullanılabilir denetimleri kümesini tanımlayabilirsiniz.

## <a name="custom-control-example"></a>Özel denetim örneği

Aşağıdaki örnek Certificates.Format.ps1xml dosyasında tanımlanan özel bir denetimi gösterir. Bu özel denetimi ayırmak için kullanılan [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) Tablo görünümünde görüntülenen nesneleri.

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a>Ayrıca bkz:

[Dosya biçimlendirme bir PowerShell yazma](./writing-a-powershell-formatting-file.md)
