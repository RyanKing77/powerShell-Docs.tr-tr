---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC günlük kaynak
ms.openlocfilehash: c7e1957540da2fd85a30f739e0f69bdb6975a4d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-log-resource"></a>DSC günlük kaynak

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

__Günlük__ kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), Microsoft Windows istenen durum yapılandırması/analitik olay günlüğüne ileti yazmak için bir mekanizma sağlar.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

Not: yalnızca DSC için işlem günlüklerini varsayılan olarak etkindir.
Analitik günlük kullanılabilir veya görünür olacak önce etkinleştirilmesi gerekir.
Aşağıdaki makaleye bakın.

[DSC olay günlüklerini nerede?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Özellikler
|  Özellik  |  Açıklama   |
|---|---|
| İleti| Microsoft-Windows-Desired durumu yapılandırma/analitik olay günlüğüne yazmak için istediğiniz iletiyi belirtir.|
| dependsOn | Bu günlüğü iletisi yazılmış önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir ileti Microsoft-Windows-Desired durumu yapılandırma/analitik olay günlüğüne dahil etmek gösterilmiştir.

> **Not**: çalıştırırsanız [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) yapılandırılmış ile bu kaynak, her zaman döndürülecek **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```