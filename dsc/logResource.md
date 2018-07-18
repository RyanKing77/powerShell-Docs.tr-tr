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
# <a name="dsc-log-resource"></a><span data-ttu-id="aa441-103">DSC Log kaynağı</span><span class="sxs-lookup"><span data-stu-id="aa441-103">DSC Log Resource</span></span>

> <span data-ttu-id="aa441-104">Uygulama hedefi: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aa441-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="aa441-105">__Günlük__ kaynak olarak Windows PowerShell Desired State Configuration (DSC), Microsoft Windows Desired State Configuration / analitik olay günlüğüne ileti yazmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa441-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="aa441-106">Varsayılan olarak, yalnızca işlem günlüklerinde DSC için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="aa441-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="aa441-107">Analitik günlüğü kullanılabilir veya görünür olacağını önce etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa441-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="aa441-108">Daha fazla bilgi için [DSC olay günlükleri nerede?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="aa441-108">For more information, see [Where are DSC Event Logs?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="aa441-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aa441-109">Properties</span></span>

|  <span data-ttu-id="aa441-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="aa441-110">Property</span></span>  |  <span data-ttu-id="aa441-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa441-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="aa441-112">İleti</span><span class="sxs-lookup"><span data-stu-id="aa441-112">Message</span></span>| <span data-ttu-id="aa441-113">Yapılandırma/analitik Microsoft-Windows-Desired durumu olay günlüğüne yazmak için istediğiniz iletiyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa441-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="aa441-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aa441-114">DependsOn</span></span> | <span data-ttu-id="aa441-115">Bu günlük iletisi yazılan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa441-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="aa441-116">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="aa441-116">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="aa441-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa441-117">Example</span></span>

<span data-ttu-id="aa441-118">Aşağıdaki örnek, Microsoft-Windows-Desired durumu yapılandırma/analitik olay günlüğüne bir ileti içerecek şekilde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aa441-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="aa441-119">Çalıştırırsanız [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) yapılandırılmış olan bu kaynak, her zaman döndüreceği **$false**.</span><span class="sxs-lookup"><span data-stu-id="aa441-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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