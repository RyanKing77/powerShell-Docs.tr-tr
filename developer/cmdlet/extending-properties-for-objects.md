---
title: Özellikleri genişletme nesneleri için | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 496e363b041194563d46c09eee67a12055bb54b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068156"
---
# <a name="extending-properties-for-objects"></a>Nesnelerin Özelliklerini Genişletme

.NET Framework nesneleri genişlettiğinizde, nesnelere özellikler, kod özellikleri, Not özellikleri, betik özellikleri ve özellik kümeleri diğer adı ekleyebilirsiniz. Bu özellikleri tanımlamak için kullanılan XML aşağıdaki bölümlerde açıklanmıştır.

> [!NOTE]
> Aşağıdaki bölümlerde Windows PowerShell yükleme dizinindeki varsayılan Types.ps1xml türleri dosyasından örnekler (`$pshome`).

## <a name="alias-properties"></a>Diğer özellikler

Varolan bir özellik için yeni bir ad bir diğer ad özelliği tanımlar.

Aşağıdaki örnekte, `Count` özelliği eklenir [System.Array? Displayproperty Fullname =](/dotnet/api/System.Array) türü. [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) öğe genişletilmiş özellik bir diğer ad özelliği olarak tanımlar. [Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi yeni adı belirtir. Ve [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) öğesi diğer adının başvurduğu var olan özelliği belirtir. (Ayrıca ekleyebilirsiniz [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)

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

Kod bir özelliği, bir statik özellik bir .NET Framework nesnesi başvurur.

Aşağıdaki örnekte, `Node` özelliği eklenir [System.IO.Directoryinfo? Displayproperty Fullname =](/dotnet/api/System.IO.DirectoryInfo) türü. [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) öğe genişletilmiş özellik kod özelliği olarak tanımlar. [Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi, genişletilmiş özelliğin adını belirtir. Ve [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) öğe genişletilmiş özelliği tarafından başvurulan statik yöntemi tanımlar. (Ayrıca ekleyebilirsiniz [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)

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

## <a name="note-properties"></a>Not özellikleri

Bir not özelliğini statik bir değere sahip bir özelliği tanımlar.

Aşağıdaki örnekte, `Status` (değeri olan her zaman "Başarılı") özelliği eklenir [System.IO.Directoryinfo? Displayproperty Fullname =](/dotnet/api/System.IO.DirectoryInfo) türü. [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) öğe tanımlar genişletilmiş özellik Not özelliği olarak; [adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi genişletilmiş özelliğinin adını belirtir ve [değer](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) öğesi Genişletilmiş özellik statik değerini belirtir. ( [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) öğesi üyelerine de eklenebilir [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)

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

## <a name="script-properties"></a>Komut dosyası özellikleri

Bir komut dosyası özellik değeri olan bir komut dosyası çıktısını bir özelliği tanımlar.

Aşağıdaki örnekte, `VersionInfo` özelliği eklenir [System.IO.FileInfo? Displayproperty Fullname =](/dotnet/api/System.IO.FileInfo) türü. [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) öğe genişletilmiş özellik bir betik özelliği olarak tanımlar. [Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi, genişletilmiş özelliğin adını belirtir. Ve [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) öğesi özellik değerini üreten betiği belirtir. (Ayrıca ekleyebilirsiniz [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)

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

Bir özellik kümesi, bir küme adı tarafından başvurulan genişletilmiş özellikler grubunu tanımlar. Örneğin, `Property` parametresinin [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet'i, belirli bir özellik görüntülenecek kümesi belirtebilirsiniz. Bir özellik kümesi belirtildiğinde, kümeye ait özellikleri görüntülenir.

Bir nesne için tanımlanmış bir özellik kümeleri sayısına bir sınırlama yoktur. Ancak, bir nesnenin varsayılan görüntü özelliklerini tanımlamak için kullanılan özellik kümeleri PSStandardMembers üye kümesi içinde belirtilmelidir. Types.ps1xml türleri dosyasında DefaultDisplayProperty DefaultDisplayPropertySet ve DefaultKeyPropertySet varsayılan özellik kümesinin adlarını içerir. PSStandardMembers üye kümesine eklediğiniz herhangi bir ek özellik kümeleri göz ardı edilir.

Aşağıdaki örnekte, DefaultDisplayPropertySet özellik kümesi PSStandardMembers üye kümesine eklenen [System.Serviceprocess.Servicecontroller? Displayproperty Fullname =](/dotnet/api/System.ServiceProcess.ServiceController) türü. [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) öğe özellikler grubunu tanımlar. [Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi özellik kümesinin adını belirtir. Ve [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) öğesi kümesi özelliklerini belirtir. (Ayrıca ekleyebilirsiniz [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) üyelerinin öğesine [türü](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) öğesi.)

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

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
