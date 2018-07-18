---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Log kaynağı
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093485"
---
# <a name="dsc-log-resource"></a>DSC Log kaynağı

> Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0

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
> Varsayılan olarak, yalnızca işlem günlüklerinde DSC için etkinleştirilir. Analitik günlüğü kullanılabilir veya görünür olacağını önce etkinleştirilmesi gerekir. Daha fazla bilgi için [DSC olay günlükleri nerede?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).

## <a name="properties"></a>Özellikler

|  Özellik  |  Açıklama   |
|---|---|
| İleti| Yapılandırma/analitik Microsoft-Windows-Desired durumu olay günlüğüne yazmak için istediğiniz iletiyi gösterir.|
| DependsOn | Bu günlük iletisi yazılan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = '[ResourceType]ResourceName'`.|

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