---
title: Nesneler için özellikleri genişletme | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986480"
---
# <a name="extending-properties-for-objects"></a>Nesnelerin Özelliklerini Genişletme

Nesneleri .NET Framework genişlettiğinizde, nesnelere diğer ad özellikleri, kod özellikleri, Note özellikleri, betik özellikleri ve özellik kümeleri ekleyebilirsiniz. Bu özellikleri tanımlayan XML aşağıdaki bölümlerde açıklanmıştır.

> [!NOTE]
> Aşağıdaki bölümlerdeki örnekler, PowerShell yükleme dizinindeki ( `Types.ps1xml` `$PSHOME`) varsayılan türler dosyasıdır. Daha fazla bilgi için bkz [. Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="alias-properties"></a>Diğer ad özellikleri

Bir Alias özelliği, var olan bir özellik için yeni bir ad tanımlar.

Aşağıdaki örnekte, **Count** özelliği [System. Array](/dotnet/api/System.Array) türüne eklenir. [Alias özelliği](/dotnet/api/system.management.automation.psaliasproperty) öğesi genişletilmiş özelliği bir diğer ad özelliği olarak tanımlar. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi yeni adı belirtir. Ve [Referencedmembername](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) öğesi, diğer ad tarafından başvurulan var olan özelliği belirtir. Ayrıca, `AliasProperty` öğesini [membersets](/dotnet/api/system.management.automation.psmemberset) öğesinin üyelerine de ekleyebilirsiniz.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a>Kod özellikleri

Bir kod özelliği bir .NET Framework nesnesinin statik özelliğine başvurur.

Aşağıdaki örnekte, **Mode** özelliği [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) türüne eklenir. [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) öğesi, Genişletilmiş özelliği bir kod özelliği olarak tanımlar. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi, genişletilmiş özelliğin adını belirtir. Ve, [Getcobaşvuru](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) öğesi, genişletilmiş özellik tarafından başvurulan statik yöntemi tanımlar. Ayrıca, `CodeProperty` öğesini [membersets](/dotnet/api/system.management.automation.psmemberset) öğesinin üyelerine de ekleyebilirsiniz.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a>Notun özellikleri

Note özelliği statik değere sahip bir özelliği tanımlar.

Aşağıdaki örnekte, değeri her zaman **başarılı**olan **Status** özelliği [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) türüne eklenir. [Noteproperty](/dotnet/api/system.management.automation.psnoteproperty) öğesi genişletilmiş özelliği Not özelliği olarak tanımlar. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi, genişletilmiş özelliğin adını belirtir. [Value](/dotnet/api/system.management.automation.psnoteproperty.value) öğesi, genişletilmiş özelliğin statik değerini belirtir. Öğesi membersets öğesinin üyelerine de eklenebilir. [](/dotnet/api/system.management.automation.psmemberset) `NoteProperty`

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a>Betik özellikleri

Betik özelliği, değeri bir betiğin çıkışı olan bir özelliği tanımlar.

Aşağıdaki örnekte, **VersionInfo** özelliği [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) türüne eklenir. [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) öğesi, Genişletilmiş özelliği bir betik özelliği olarak tanımlar. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi, genişletilmiş özelliğin adını belirtir. Ve [Getscriptblock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) öğesi, özellik değerini üreten betiği belirtir. Ayrıca, `ScriptProperty` öğesini [membersets](/dotnet/api/system.management.automation.psmemberset) öğesinin üyelerine de ekleyebilirsiniz.

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a>Özellik kümeleri

Bir özellik kümesi, küme adı tarafından başvurulabilen genişletilmiş özellikler grubunu tanımlar.
Örneğin, [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**özelliği** parametresi, görüntülenmek üzere belirli bir özellik kümesi belirtebilir. Bir özellik kümesi belirtildiğinde, yalnızca kümesine ait özellikler görüntülenir.

Bir nesne için tanımlanabilir özellik kümesi sayısında kısıtlama yoktur. Ancak, bir nesnenin varsayılan görüntüleme özelliklerini tanımlamak için kullanılan özellik kümelerinin **Psstandardmembers** üye kümesi içinde belirtilmesi gerekir. Türler dosyasında, varsayılan özellik kümesi adları **defaultdisplayproperty**, **defaultdisplaypropertyset**ve **defaultkeypropertyset**' i içerir. `Types.ps1xml` **Psstandardmembers** üye kümesine eklediğiniz herhangi bir ek özellik kümesi yok sayılır.

Aşağıdaki örnekte, **Defaultdisplaypropertyset** özelliği kümesi, [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) türünün **psstandardmembers** üye kümesine eklenir. [PropertySet](/dotnet/api/system.management.automation.pspropertyset) öğesi Özellik grubunu tanımlar. [Name](/dotnet/api/system.management.automation.psmemberinfo.name) öğesi özellik kümesi adını belirtir. Ve [Referencedproperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) öğesi, küme özelliklerini belirtir. Ayrıca, `PropertySet` öğesini [Type](/dotnet/api/system.management.automation.pstypename) öğesinin üyelerine de ekleyebilirsiniz.

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a>Ayrıca bkz.

[Türler. ps1xml hakkında](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Windows PowerShell cmdlet 'ı yazma](./writing-a-windows-powershell-cmdlet.md)
