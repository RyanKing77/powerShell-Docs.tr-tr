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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066694"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="4b005-102">Özel Denetimler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4b005-102">Creating Custom Controls</span></span>

<span data-ttu-id="4b005-103">Özel denetimler biçimlendirme bir dosyanın en esnek bileşenlerdir.</span><span class="sxs-lookup"><span data-stu-id="4b005-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="4b005-104">Tablo, liste ve verileri içeren bir tablo gibi veri biçimsel bir yapı tanımla geniş görünümleri aksine özel denetimler tek bir veri parçasının nasıl görüntüleneceğini tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b005-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="4b005-105">Ortak bir dizi biçimlendirme dosyanın tüm görünümleri için kullanılabilen özel denetimler tanımlayabilirsiniz, belirli bir görünüm için kullanılabilen özel denetimler tanımlayabilirsiniz ve nesnelerin bir gruba kullanılabilir denetimleri kümesini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b005-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="4b005-106">Özel denetim örneği</span><span class="sxs-lookup"><span data-stu-id="4b005-106">Custom Control Example</span></span>

<span data-ttu-id="4b005-107">Aşağıdaki örnek Certificates.Format.ps1xml dosyasında tanımlanan özel bir denetimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b005-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="4b005-108">Bu özel denetimi ayırmak için kullanılan [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) Tablo görünümünde görüntülenen nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4b005-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4b005-109">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4b005-109">See Also</span></span>

[<span data-ttu-id="4b005-110">Dosya biçimlendirme bir PowerShell yazma</span><span class="sxs-lookup"><span data-stu-id="4b005-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
