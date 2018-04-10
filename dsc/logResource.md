---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC günlük kaynak
ms.openlocfilehash: f1a528767508d4a0e7f0ea2e58fd27a6a4d7ec75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-log-resource"></a><span data-ttu-id="1373b-103">DSC günlük kaynak</span><span class="sxs-lookup"><span data-stu-id="1373b-103">DSC Log Resource</span></span>

> <span data-ttu-id="1373b-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1373b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1373b-105">__Günlük__ kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), Microsoft Windows istenen durum yapılandırması/analitik olay günlüğüne ileti yazmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1373b-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="1373b-106">Not: yalnızca DSC için işlem günlüklerini varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="1373b-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="1373b-107">Analitik günlük kullanılabilir veya görünür olacak önce etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1373b-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="1373b-108">Aşağıdaki makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="1373b-108">See the following article.</span></span>

[<span data-ttu-id="1373b-109">DSC olay günlüklerini nerede?</span><span class="sxs-lookup"><span data-stu-id="1373b-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="1373b-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1373b-110">Properties</span></span>
|  <span data-ttu-id="1373b-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="1373b-111">Property</span></span>  |  <span data-ttu-id="1373b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1373b-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="1373b-113">İleti</span><span class="sxs-lookup"><span data-stu-id="1373b-113">Message</span></span>| <span data-ttu-id="1373b-114">Microsoft-Windows-Desired durumu yapılandırma/analitik olay günlüğüne yazmak için istediğiniz iletiyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="1373b-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="1373b-115">dependsOn</span><span class="sxs-lookup"><span data-stu-id="1373b-115">DependsOn</span></span> | <span data-ttu-id="1373b-116">Bu günlüğü iletisi yazılmış önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="1373b-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="1373b-117">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1373b-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="1373b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="1373b-118">Example</span></span>

<span data-ttu-id="1373b-119">Aşağıdaki örnek, bir ileti Microsoft-Windows-Desired durumu yapılandırma/analitik olay günlüğüne dahil etmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1373b-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="1373b-120">**Not**: çalıştırırsanız [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) yapılandırılmış ile bu kaynak, her zaman döndürülecek **$false**.</span><span class="sxs-lookup"><span data-stu-id="1373b-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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