---
title: Varsayılan yöntemler için nesneleri tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068224"
---
# <a name="defining-default-methods-for-objects"></a>Nesneler için Varsayılan Yöntemleri Tanımlama

.NET Framework nesneleri genişlettiğinizde, kod ve betik yöntemleri nesneleri ekleyebilirsiniz. Bu yöntemleri tanımlamak için kullanılan XML aşağıdaki bölümlerde açıklanmıştır.

> [!NOTE]
> Aşağıdaki bölümlerde Windows PowerShell yükleme dizininde Types.ps1xml türleri dosyasından örnekler (`$pshome`).

## <a name="code-methods"></a>Kod yöntemleri

Bir kod yöntemi statik bir yöntem .NET Framework nesnesi başvuruyor.

Aşağıdaki örnekte, **ConvertLargeIntegerToInt64** yöntemi eklenir [System.Xml.Xmlnode? Displayproperty Fullname =](/dotnet/api/System.Xml.XmlNode) türü. [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) öğesi, kod yöntemi olarak genişletilmiş yöntemi tanımlar. [Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi genişletilmiş yöntemin adını belirtir. Ve [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) öğesi statik yöntemini belirtir. (Ayrıca ekleyebilirsiniz [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>Betik yöntemleri

Bir betik yöntemi, bir komut dosyası çıktısını değeri olan bir yöntem tanımlar. Aşağıdaki örnekte, **ConvertToDateTime** yöntemi eklenir [System.Management.Managementobject? Displayproperty Fullname =](/dotnet/api/System.Management.ManagementObject) türü. [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) öğe betik yöntemi olarak genişletilmiş yöntemi tanımlar. [Adı](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) öğesi genişletilmiş yöntemin adını belirtir. Ve [betik](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) öğesi yöntemi değer üreten betiği belirtir. (Ayrıca ekleyebilirsiniz [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) üyelerinin öğesine [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) öğesi.)

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)