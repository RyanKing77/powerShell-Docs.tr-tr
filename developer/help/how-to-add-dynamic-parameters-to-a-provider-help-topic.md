---
title: Sağlayıcıya dinamik parametreler ekleme Yardım konusu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737594"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Sağlayıcı Yardım Konusuna Dinamik Parametreler Ekleme

Bu bölümde, bir sağlayıcı Yardım konusunun **dınamık parametreler** bölümünün nasıl doldurulacağı açıklanmaktadır.

*Dinamik parametreler* yalnızca belirtilen koşullarda kullanılabilen bir cmdlet veya işlevin parametreleridir.

Sağlayıcı yardım konusunda belgelenen dinamik parametreler, sağlayıcının cmdlet 'i veya işlevi sağlayıcı sürücüsünde kullanıldığında cmdlet veya işleve eklediği dinamik parametrelerdir.

Dinamik parametreler, bir sağlayıcı için özel cmdlet yardımı 'nda da açıklanmalıdır. Sağlayıcı için hem sağlayıcı yardımını hem de özel cmdlet yardımını yazarken, dinamik parametre belgelerini her iki belgeye de ekleyin. Özel cmdlet yardımı hakkında daha fazla bilgi için bkz. [sağlayıcılar Için Windows PowerShell özel cmdlet yardımı yazma](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Bir sağlayıcı herhangi bir dinamik parametre uygulamadıysanız, sağlayıcı yardım konusu boş `DynamicParameters` bir öğesi içerir.

### <a name="to-add-dynamic-parameters"></a>Dinamik parametreler eklemek için

1. *AssemblyName*. dll-Help. xml dosyasında, `providerHelp` öğesi içinde, bir `DynamicParameters` öğesi ekleyin. Öğe, `Tasks` öğesinden sonra ve öğesinden önce `RelatedLinks` görünmelidir. `DynamicParameters`

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

   Sağlayıcı herhangi bir dinamik parametre uygulamadıysanız, `DynamicParameters` öğe boş olabilir.

2. Öğesi içinde, her dinamik parametre için bir `DynamicParameter` öğesi ekleyin. `DynamicParameters`

   Örneğin:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Her `DynamicParameter` öğesinde bir `Name` ve `CmdletSupported` öğesi ekleyin.

   |Öğe Adı|Açıklama|
   |------------------|-----------------|
   |Adı|Parametrenin adını belirtir.|
   |CmdletSupported|Parametresinin geçerli olduğu cmdlet 'leri belirtir. Cmdlet adlarının virgülle ayrılmış bir listesini yazın.|

   Örneğin, aşağıdaki XML, Windows PowerShell FileSystem `Encoding` sağlayıcısının `Add-Content`, `Get-Content` `Set-Content` , cmdlet 'lerine eklediği dinamik parametreyi belgeler.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Her `DynamicParameter` öğesinde bir `Type` öğesi ekleyin. Öğesi, dinamik parametre değerinin .NET türünü `Name` içeren öğesi için bir kapsayıcıdır. `Type`

   Örneğin, aşağıdaki XML, `Encoding` dinamik parametrenin .NET türünün [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) numaralandırması olduğunu gösterir.

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

5. Dinamik parametrenin kısa bir açıklamasını içeren öğesiniekleyin.`Description` Açıklamayı oluştururken [parametre bilgilerini ekleme](./how-to-add-parameter-information.md)içindeki tüm cmdlet parametreleri için önceden belirlenmiş olan yönergeleri kullanın.

   Örneğin, aşağıdaki XML `Encoding` dinamik parametrenin açıklamasını içerir.

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

6. `PossibleValues` Öğesi ve alt öğelerini ekleyin. Birlikte, bu öğeler dinamik parametrenin değerlerini anlatmaktadır. Bu öğe, numaralandırılmış değerler için tasarlanmıştır. Dinamik parametre bir değer almaz (örneğin, bir switch parametresi ile birlikte) veya değerler numaralandırılamıyor, boş `PossibleValues` bir öğe ekleyin.

   Aşağıdaki tabloda `PossibleValues` öğesi ve alt öğeleri listelenmektedir ve açıklanmaktadır.

   |Öğe Adı|Açıklama|
   |------------------|-----------------|
   |PossibleValues|Bu öğe bir kapsayıcıdır. Alt öğeleri aşağıda açıklanmıştır. Her sağlayıcı `PossibleValues` yardım konusuna bir öğe ekleyin. Öğe boş olabilir.|
   |PossibleValue|Bu öğe bir kapsayıcıdır. Alt öğeleri aşağıda açıklanmıştır. Dinamik parametrenin `PossibleValue` her bir değeri için bir öğe ekleyin.|
   |Değer|Değer adını belirtir.|
   |Açıklama|Bu öğe bir `Para` öğesi içerir. `Para` Öğesindeki metin, `Value` öğesinde adı geçen değeri açıklar.|

   Örneğin, aşağıdaki XML `PossibleValue` `Encoding` dinamik parametrenin bir öğesini gösterir.

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

Aşağıdaki örnek, `Encoding` dinamik parametrenin `DynamicParameters` öğesini gösterir.

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