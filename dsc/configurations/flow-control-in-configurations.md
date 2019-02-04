---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırmalarda koşullu deyimler ve döngüler
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55689053"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="479ad-103">Yapılandırmalarda koşullu deyimler ve döngüler</span><span class="sxs-lookup"><span data-stu-id="479ad-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="479ad-104">Yapabileceğiniz, [yapılandırmaları](configurations.md) daha dinamik PowerShell akış denetimi anahtar sözcüklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="479ad-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="479ad-105">Bu makalede, yapılandırmalarınızı daha dinamik hale getireceğinizi koşullu ifadeleri ve döngüler nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="479ad-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="479ad-106">Birleştirme koşullu ve döngüler ile [parametreleri](add-parameters-to-a-configuration.md) ve [yapılandırma verilerini](configData.md) yapılandırmalarınızı derleme sırasında daha fazla esneklik ve denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="479ad-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="479ad-107">Bir işlev veya bir betik bloğu yalnızca gibi yapılandırması içindeki herhangi bir PowerShell dil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479ad-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="479ad-108">".Mof" dosyasını derlemek için yapılandırmayı çağırdığınızda kullandığınız deyimleri yalnızca değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="479ad-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="479ad-109">Aşağıdaki örnekler kavramları göstermek için basit bir senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="479ad-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="479ad-110">Koşullular döngüler parametreler ve yapılandırma verileri ile daha sık kullanılan ' dir.</span><span class="sxs-lookup"><span data-stu-id="479ad-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="479ad-111">Bu basit örnekte, **hizmet** kaynak blok geçerli durumunu koruyan bir ".mof" dosyası oluşturmak için derleme zamanında bir hizmetinin geçerli durumunu alır.</span><span class="sxs-lookup"><span data-stu-id="479ad-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="479ad-112">Dinamik kaynak bloklarını kullanarak, IntelliSense verimliliğini etkisiz hale.</span><span class="sxs-lookup"><span data-stu-id="479ad-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="479ad-113">PowerShell ayrıştırıcı yapılandırmasını derlenmiş kadar belirtilen değerleri kabul edilebilir olup olmadığını belirleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="479ad-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="479ad-114">Ayrıca, aşağıdakileri oluşturabilirsiniz bir **hizmet** block geçerli makine üzerinde her hizmet için kaynak kullanarak bir `foreach` döngü.</span><span class="sxs-lookup"><span data-stu-id="479ad-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="479ad-115">Ayrıca yalnızca basit bir kullanarak çevrimiçi olan makineler için yapılandırmaları oluşturabilirsiniz `if` deyimi.</span><span class="sxs-lookup"><span data-stu-id="479ad-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="479ad-116">Dinamik kaynak Yukarıdaki örneklerde başvurusu geçerli makine engeller.</span><span class="sxs-lookup"><span data-stu-id="479ad-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="479ad-117">Geliştirmekte yapılandırma üzerinde makine olabilir, bu örnekte, hedef değil düğümü.</span><span class="sxs-lookup"><span data-stu-id="479ad-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="479ad-118">Özet</span><span class="sxs-lookup"><span data-stu-id="479ad-118">Summary</span></span>

<span data-ttu-id="479ad-119">Özet olarak, bir yapılandırması içindeki herhangi bir PowerShell dil kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479ad-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="479ad-120">Bu gibi şeyleri içerir:</span><span class="sxs-lookup"><span data-stu-id="479ad-120">This includes things like:</span></span>

- <span data-ttu-id="479ad-121">Özel nesneler</span><span class="sxs-lookup"><span data-stu-id="479ad-121">Custom Objects</span></span>
- <span data-ttu-id="479ad-122">Hashtable'da</span><span class="sxs-lookup"><span data-stu-id="479ad-122">Hashtables</span></span>
- <span data-ttu-id="479ad-123">Dize düzenlemesi</span><span class="sxs-lookup"><span data-stu-id="479ad-123">String manipulation</span></span>
- <span data-ttu-id="479ad-124">Uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="479ad-124">Remoting</span></span>
- <span data-ttu-id="479ad-125">WMI ve CIM</span><span class="sxs-lookup"><span data-stu-id="479ad-125">WMI and CIM</span></span>
- <span data-ttu-id="479ad-126">Active Directory nesneleri</span><span class="sxs-lookup"><span data-stu-id="479ad-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="479ad-127">ve daha fazlası...</span><span class="sxs-lookup"><span data-stu-id="479ad-127">and more...</span></span>

<span data-ttu-id="479ad-128">Bir yapılandırmada tanımlanmış herhangi bir PowerShell kod, derleme zamanında değerlendirilir, ancak kod yapılandırmanızı içeren betik yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="479ad-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="479ad-129">Yapılandırma içeri aktardığınızda yapılandırma bloğu dışında herhangi bir kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="479ad-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="479ad-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="479ad-130">See also</span></span>

- [<span data-ttu-id="479ad-131">İçin yapılandırma parametreleri Ekle</span><span class="sxs-lookup"><span data-stu-id="479ad-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="479ad-132">Yapılandırmaları yapılandırma verilerinden ayrı</span><span class="sxs-lookup"><span data-stu-id="479ad-132">Separate Configuration data from Configurations</span></span>](configData.md)
