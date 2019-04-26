---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Log kaynağı
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077237"
---
# <a name="dsc-log-resource"></a>DSC Log kaynağı

> _Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0_

__Günlük__ kaynak olarak Windows PowerShell Desired State Configuration (DSC), Microsoft Windows Desired State Configuration / analitik olay günlüğüne ileti yazmak için bir mekanizma sağlar.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> Varsayılan olarak, yalnızca işlem günlüklerinde DSC için etkinleştirilir. Analitik günlüğü kullanılabilir veya görünür olacağını önce etkinleştirilmesi gerekir. Daha fazla bilgi için [DSC olay günlükleri nerede?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).

## <a name="properties"></a>Özellikler

| Özellik | Açıklama |
| --- | --- |
| İleti| Yapılandırma/analitik Microsoft-Windows-Desired durumu olay günlüğüne yazmak için istediğiniz iletiyi gösterir.|
| dependsOn | Bu günlük iletisi yazılan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, Microsoft-Windows-Desired durumu yapılandırma/analitik olay günlüğüne bir ileti içerecek şekilde gösterilmektedir.

> [!NOTE]
> Çalıştırırsanız [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) yapılandırılmış olan bu kaynak, her zaman döndüreceği **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
