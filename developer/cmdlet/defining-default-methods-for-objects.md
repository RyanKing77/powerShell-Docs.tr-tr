---
title: Nesneler için varsayılan yöntemleri tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215279"
---
# <a name="defining-default-methods-for-objects"></a>Nesneler için Varsayılan Yöntemleri Tanımlama

Nesneleri .NET Framework genişlettiğinizde, nesnelere kod yöntemleri ve betik yöntemleri ekleyebilirsiniz.
Bu yöntemleri tanımlamak için kullanılan XML aşağıdaki bölümlerde açıklanmıştır.

> [!NOTE]
> Aşağıdaki bölümlerdeki `Types.ps1xml` örnekler, Windows PowerShell yükleme dizinindeki (`$PSHOME`) türler dosyasıdır. Daha fazla bilgi için bkz [. Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="code-methods"></a>Kod yöntemleri

Kod yöntemi bir .NET Framework nesnesinin statik yöntemine başvurur.

Aşağıdaki örnekte, **ToString** yöntemi [System. xml. XMLNode](/dotnet/api/System.Xml.XmlNode) türüne eklenir. [Pscodemethod](/dotnet/api/system.management.automation.pscodemethod) öğesi, genişletilmiş yöntemi bir kod yöntemi olarak tanımlar. [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) öğesi, genişletilmiş yöntemin adını belirtir. [Cobaşvuru](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) öğesi de statik yöntemi belirtir. [Pscodemethod](/dotnet/api/system.management.automation.pscodemethod) öğesini de [psmembersets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) öğesinin üyelerine ekleyebilirsiniz.

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a>Betik metotları

Betik yöntemi, bir betiğin çıkışı olan bir yöntemi tanımlar. Aşağıdaki örnekte, **Converttodatetime** yöntemi [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) türüne eklenir. [Psscriptmethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) öğesi, genişletilmiş yöntemi bir betik yöntemi olarak tanımlar. [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) öğesi, genişletilmiş yöntemin adını belirtir. Ve [komut dosyası](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) öğesi, yöntem değerini üreten betiği belirtir. [Psscriptmethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) öğesini de [psmembersets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) öğesinin üyelerine ekleyebilirsiniz.

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

## <a name="see-also"></a>Ayrıca bkz.

[Windows PowerShell cmdlet 'ı yazma](./writing-a-windows-powershell-cmdlet.md)
