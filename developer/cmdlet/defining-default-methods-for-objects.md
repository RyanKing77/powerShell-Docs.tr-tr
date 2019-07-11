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
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733985"
---
# <a name="defining-default-methods-for-objects"></a>Nesneler için Varsayılan Yöntemleri Tanımlama

.NET Framework nesneleri genişlettiğinizde, kod ve betik yöntemleri nesneleri ekleyebilirsiniz. Bu yöntemleri tanımlamak için kullanılan XML aşağıdaki bölümlerde açıklanmıştır.

> [!NOTE]
> Aşağıdaki bölümlerde Windows PowerShell yükleme dizininde Types.ps1xml türleri dosyasından örnekler (`$pshome`).

## <a name="code-methods"></a>Kod yöntemleri

Bir kod yöntemi statik bir yöntem .NET Framework nesnesi başvuruyor.

Aşağıdaki örnekte, **ConvertLargeIntegerToInt64** yöntemi eklenir [System.Xml.Xmlnode? Displayproperty Fullname =](/dotnet/api/System.Xml.XmlNode) türü. [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) öğesi, kod yöntemi olarak genişletilmiş yöntemi tanımlar. [Adı](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) öğesi genişletilmiş yöntemin adını belirtir. Ve [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) öğesi statik yöntemini belirtir. (Ayrıca ekleyebilirsiniz [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) üyelerinin öğesine [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) öğesi.)

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

Bir betik yöntemi, bir komut dosyası çıktısını değeri olan bir yöntem tanımlar. Aşağıdaki örnekte, **ConvertToDateTime** yöntemi eklenir [System.Management.Managementobject? Displayproperty Fullname =](/dotnet/api/System.Management.ManagementObject) türü. [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) öğe betik yöntemi olarak genişletilmiş yöntemi tanımlar. [Adı](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) öğesi genişletilmiş yöntemin adını belirtir. Ve [betik](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) öğesi yöntemi değer üreten betiği belirtir. (Ayrıca ekleyebilirsiniz [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) üyelerinin öğesine [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) öğesi.)

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
