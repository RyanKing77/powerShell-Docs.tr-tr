---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynağı yöntemlerini doğrudan çağırma
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405705"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="5ba9a-103">DSC kaynağı yöntemlerini doğrudan çağırma</span><span class="sxs-lookup"><span data-stu-id="5ba9a-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="5ba9a-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5ba9a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5ba9a-105">Kullanabileceğiniz [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) işlevleri veya DSC kaynak yöntemlerine doğrudan çağırmak için cmdlet ( **Get-TargetResource**, **kümesi TargetResource**ve  **Test-TargetResource** MOF temelli kaynak işlevleri veya **alma**, **ayarlayın**, ve **Test** sınıf tabanlı bir kaynak yöntemleri).</span><span class="sxs-lookup"><span data-stu-id="5ba9a-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="5ba9a-106">Bu DSC kaynakları kullanmak istediğiniz Üçüncü taraflardan ya da faydalı bir araç kaynakları geliştirirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ba9a-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="5ba9a-107">Bu cmdlet genellikle metaconfiguration özelliğiyle birlikte `refreshMode = 'Disabled'`, ancak bunu ne olursa olsun kullanılabilir **refreshMode** ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5ba9a-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="5ba9a-108">Çağrılırken **Invoke-DscResource** cmdlet'i, belirttiğiniz hangi yöntemi veya kullanılarak çağrılacak işlev **yöntemi** parametresi.</span><span class="sxs-lookup"><span data-stu-id="5ba9a-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="5ba9a-109">Bir karma tablo değeri olarak geçirerek kaynak özelliklerini belirtin **özelliği** parametresi.</span><span class="sxs-lookup"><span data-stu-id="5ba9a-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="5ba9a-110">Kaynak yöntemlerine doğrudan çağırma örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5ba9a-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="5ba9a-111">Bir dosya mevcut olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="5ba9a-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="5ba9a-112">Bir dosyanın var olup olmadığını test</span><span class="sxs-lookup"><span data-stu-id="5ba9a-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="5ba9a-113">Dosya içeriğini Al</span><span class="sxs-lookup"><span data-stu-id="5ba9a-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="5ba9a-114">**Not:** Bileşik kaynak yöntemlerine doğrudan çağırma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5ba9a-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="5ba9a-115">Bunun yerine, temel alınan kaynakların bileşik kaynağı olun yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="5ba9a-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ba9a-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5ba9a-116">See Also</span></span>
- [<span data-ttu-id="5ba9a-117">MOF ile özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="5ba9a-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="5ba9a-118">PowerShell sınıfları ile özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="5ba9a-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="5ba9a-119">DSC kaynaklarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5ba9a-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)