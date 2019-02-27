---
title: Dinamik parametreler için sağlayıcı Yardım konusunun ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849528"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Sağlayıcı Yardım Konusuna Dinamik Parametreler Ekleme

Bu bölümde doldurmak açıklanmaktadır **dinamik parametreleri** sağlayıcısı Yardım konusunun bölümü.

*Dinamik parametreleri* bir cmdlet parametreleri veya yalnızca şuranın altında kullanılabilir işlev belirtilen koşullar.

Bir sağlayıcı Yardım konusunda belgelenen dinamik parametreleri cmdlet'ini veya işlev sağlayıcısı sürücüde kullanıldığında, cmdlet veya işlevi için sağlayıcı ekler dinamik parametreleridir.

Sağlayıcı için özel cmdlet Yardımı'nda dinamik parametreler de belgelenen. Sağlayıcısı için sağlayıcı Yardım hem özel cmdlet yardımına yazarken, hem belgelerde dinamik parametre belgeleri içerir. Özel cmdlet Yardım hakkında daha fazla bilgi için bkz: [yazma Windows PowerShell özel Cmdlet için Yardım sağlayıcıları](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Bir sağlayıcı, herhangi bir dinamik parametre uygulamaz, boş bir sağlayıcı Yardım konusuna içeren `DynamicParameters` öğesi.

### <a name="to-add-dynamic-parameters"></a>Dinamik parametreleri eklemek için

1. İçinde *AssemblyName*içinde help.xml .dll dosyası `providerHelp` öğe, Ekle bir `DynamicParameters` öğesi. `DynamicParameters` Öğesi sonra görüntülenmelidir `Tasks` öğesi ve önce `RelatedLinks` öğesi.

   Örneğin:

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   Sağlayıcı, herhangi bir dinamik parametre uygulamıyorsa `DynamicParameters` öğesi boş olabilir.

2. İçinde `DynamicParameters` her dinamik bir parametre için bir öğe ekleme bir `DynamicParameter` öğesi.

   Örneğin:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Her `DynamicParameter` öğe, Ekle bir `Name` ve `CmdletSupported` öğesi.

   |Öğe Adı|Açıklama|
   |------------------|-----------------|
   |Adı|Parametre adını belirtir.|
   |CmdletSupported|Parametrenin geçerli olduğundan cmdlet'leri belirtir. Cmdlet adları virgülle ayrılmış bir listesini yazın.|

   Örneğin, aşağıdaki XML belgeleri `Encoding` Windows PowerShell dosya sistemi sağlayıcısı ekler dinamik parametre `Add-Content`, `Get-Content`, `Set-Content` cmdlet'leri.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Her `DynamicParameter` öğe, Ekle bir `Type` öğesi. `Type` Öğesi için bir kapsayıcıdır `Name` dinamik parametre değerini .NET türünü içeren öğe.

   Örneğin, .NET türünü gösteren aşağıdaki XML `Encoding` dinamik parametredir [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) sabit listesi.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. Ekleme `Description` dinamik parametre kısa bir açıklamasını içeren öğe. Açıklama oluştururken de tüm cmdlet parametreleri için belirlenen yönergeleri kullanın [parametre bilgilerini ekleme](./how-to-add-parameter-information.md).

   Örneğin, aşağıdaki XML açıklamasını içerir `Encoding` dinamik parametre.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. Ekleme `PossibleValues` öğesi ve onun alt öğeleri. Birlikte, bu öğeleri dinamik parametre değerleri açıklar. Bu öğe Enum değerleri için tasarlanmıştır. Dinamik parametre bir değer almaz, anahtar parametresi gibi olduğu ve değerleri numaralandırılamıyor, boş bir ekleme `PossibleValues` öğesi.

   Aşağıdaki tabloda listelenmekte ve açıklanmaktadır `PossibleValues` öğesi ve onun alt öğeleri.

   |Öğe Adı|Açıklama|
   |------------------|-----------------|
   |PossibleValues|Bu öğe bir kapsayıcıdır. Alt öğeleri, aşağıda açıklanmıştır. Eklemesini `PossibleValues` her sağlayıcısı Yardım konusu öğesi. Öğe boş olabilir.|
   |PossibleValue|Bu öğe bir kapsayıcıdır. Alt öğeleri, aşağıda açıklanmıştır. Eklemesini `PossibleValue` her dinamik parametresinin değeri için öğesi.|
   |Değer|Değer adı belirtir.|
   |Açıklama|Bu öğeyi içeren bir `Para` öğesi. Metinde `Para` açıklar adlı değer `Value` öğesi.|

   Örneğin, aşağıdaki XML bir gösterir `PossibleValue` öğesinin `Encoding` dinamik parametre.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>Örnek

Aşağıdaki örnekte gösterildiği `DynamicParameters` öğesinin `Encoding` dinamik parametre.

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```