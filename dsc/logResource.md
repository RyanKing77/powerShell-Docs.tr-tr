---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC günlük kaynak"
ms.openlocfilehash: 72c9c5a9b8e2a4ed4ce43cfd792572ce95b502b3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-log-resource"></a><span data-ttu-id="feab3-103">DSC günlük kaynak</span><span class="sxs-lookup"><span data-stu-id="feab3-103">DSC Log Resource</span></span> 

> <span data-ttu-id="feab3-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="feab3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="feab3-105">__Günlük__ kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), Microsoft Windows istenen durum yapılandırması/analitik olay günlüğüne ileti yazmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="feab3-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="feab3-106">Not: yalnızca DSC için işlem günlüklerini varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="feab3-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="feab3-107">Analitik günlük kullanılabilir veya görünür olacak önce etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="feab3-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="feab3-108">Aşağıdaki makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="feab3-108">See the following article.</span></span>

[<span data-ttu-id="feab3-109">DSC olay günlüklerini nerede?</span><span class="sxs-lookup"><span data-stu-id="feab3-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="feab3-110">Özellikler</span><span class="sxs-lookup"><span data-stu-id="feab3-110">Properties</span></span>
|  <span data-ttu-id="feab3-111">Özellik</span><span class="sxs-lookup"><span data-stu-id="feab3-111">Property</span></span>  |  <span data-ttu-id="feab3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feab3-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="feab3-113">İleti</span><span class="sxs-lookup"><span data-stu-id="feab3-113">Message</span></span>| <span data-ttu-id="feab3-114">Microsoft-Windows-Desired durumu yapılandırma/analitik olay günlüğüne yazmak için istediğiniz iletiyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="feab3-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>| 
| <span data-ttu-id="feab3-115">dependsOn</span><span class="sxs-lookup"><span data-stu-id="feab3-115">DependsOn</span></span> | <span data-ttu-id="feab3-116">Bu günlüğü iletisi yazılmış önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="feab3-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="feab3-117">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="feab3-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="feab3-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="feab3-118">Example</span></span>

<span data-ttu-id="feab3-119">Aşağıdaki örnek, bir ileti Microsoft-Windows-Desired durumu yapılandırma/analitik olay günlüğüne dahil etmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="feab3-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="feab3-120">**Not**: çalıştırırsanız [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) yapılandırılmış ile bu kaynak, her zaman döndürülecek **$false**.</span><span class="sxs-lookup"><span data-stu-id="feab3-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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

