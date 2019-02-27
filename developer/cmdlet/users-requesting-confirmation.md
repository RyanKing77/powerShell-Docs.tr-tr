---
title: Onay isteyen kullanıcıların | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846980"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="4d7b7-102">Onay İsteyen Kullanıcılar</span><span class="sxs-lookup"><span data-stu-id="4d7b7-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="4d7b7-103">Değerini belirttiğinizde `true` için `SupportsShouldProcess` cmdlet'i özniteliği bildirimi parametresi, kullanıcıların belirtebilirsiniz `Confirm` parametresi komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="4d7b7-104">Varsayılan ortamda kullanıcılar belirtebilir `Confirm` parametresi veya `"-Confirm:$true` onay istenmeden, zaman [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="4d7b7-105">Bu atlar [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bile yüksek etkili işlemleri için onay istekleri.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-105">This bypasses [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="4d7b7-106">Varsa `Confirm` belirtilmezse, [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrı varsa onay istekleri `$ConfirmPreference` tercih değişkeni eşit veya ondan `ConfirmImpact` ayarıyla cmdlet'ini veya sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="4d7b7-107">Varsayılan ayar `$ConfirmPreference` yüksek.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="4d7b7-108">Bu nedenle, varsayılan ortamda yalnızca cmdlet'leri ve etkili bir eylemi belirtin sağlayıcıları onay isteyin.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="4d7b7-109">Varsa `Confirm` yanlış veya `"-Confirm:$false` belirtilen [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) çağrı, kullanıcıdan onayı ister ve `$ConfirmPreference` Kabuk değişkeni yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d7b7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d7b7-110">Remarks</span></span>

- <span data-ttu-id="4d7b7-111">Cmdlet'leri ve belirttiğiniz sağlayıcılarına `SupportsShouldProcess`, ama `ConfirmImpact`, bu eylemlerin "Orta etkisi" eylem olarak işlenir ve varsayılan olarak istemez.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="4d7b7-112">Kendi etki düzeyi varsayılan ayar'dan küçük `$ConfirmPreference` tercih değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="4d7b7-113">Kullanıcı belirtiyorsa `Verbose` parametresi onaylamanız istenmez bile çalışmasını bildirilir.</span><span class="sxs-lookup"><span data-stu-id="4d7b7-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d7b7-114">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4d7b7-114">See Also</span></span>

[<span data-ttu-id="4d7b7-115">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="4d7b7-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
