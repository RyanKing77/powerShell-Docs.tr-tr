---
title: Bir Windows PowerShell ek bileşenini oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849444"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="a91ec-102">Windows PowerShell Ek Bileşeni Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a91ec-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="a91ec-103">Bir Windows PowerShell ek bileşenini böylece Kabuk işlevselliğini genişletme Kabuk ile cmdlet'leri ve başka bir Windows PowerShell sağlayıcısını kaydetmek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a91ec-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="a91ec-104">Bir Windows PowerShell ek bileşenini tüm cmdlet'leri ve sağlayıcıları tek bir derleme kaydedebilirsiniz veya belirli bir liste cmdlet'leri ve sağlayıcıları kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a91ec-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="a91ec-105">Yalnızca diğer işletim sistemlerinde olduğu gibi korumalı bir dizinde ek derlemeler yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a91ec-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="a91ec-106">Aksi takdirde, kötü amaçlı kullanıcıların bir bütünleştirilmiş kod güvenli olmayan kod ile değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a91ec-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="a91ec-107">Windows PowerShell ek bileşeni sınıfları</span><span class="sxs-lookup"><span data-stu-id="a91ec-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="a91ec-108">Tüm Windows PowerShell ek bileşenini sınıflar türetilen [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) veya [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) sınıfları.</span><span class="sxs-lookup"><span data-stu-id="a91ec-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="a91ec-109">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a91ec-109">Examples</span></span>

<span data-ttu-id="a91ec-110">[Bir Windows PowerShell ek bileşenini yazma](./writing-a-windows-powershell-snap-in.md): Bu örnek, bir derlemede tüm cmdlet'leri ve sağlayıcıları kaydetmek için kullanılan bir ek bileşenini oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a91ec-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="a91ec-111">[Bir özel Windows PowerShell ek bileşenini yazma](./writing-a-custom-windows-powershell-snap-in.md): Bu örnek, bir özel cmdlet'lerini ve sağlayıcıları var olmayabilir veya belirli bir dizi tek bir derleme kaydetmek için kullanılan eklentisini oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a91ec-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="a91ec-112">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="a91ec-112">See Also</span></span>

[<span data-ttu-id="a91ec-113">System.Management.Automation.Pssnapin</span><span class="sxs-lookup"><span data-stu-id="a91ec-113">System.Management.Automation.Pssnapin</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="a91ec-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="a91ec-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="a91ec-115">Cmdlet'leri kaydetme</span><span class="sxs-lookup"><span data-stu-id="a91ec-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="a91ec-116">Windows PowerShell Kabuk SDK'sı</span><span class="sxs-lookup"><span data-stu-id="a91ec-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
