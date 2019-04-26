---
title: Cmdlet'leri ve komut dosyalarını içinde bir Cmdlet yürütmesini | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067680"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="908ce-102">Bir Cmdlet’te Cmdlet ve Betikleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="908ce-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="908ce-103">Bir cmdlet diğer cmdlet'ler ve işleme yöntemi cmdlet'inin girdideki betiklerin çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="908ce-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="908ce-104">Bu, yeniden kod yazmak zorunda kalmadan, cmdlet'e mevcut cmdlet'leri ve betikleri işlevselliğini eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="908ce-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="908ce-105">Invoke yöntemi</span><span class="sxs-lookup"><span data-stu-id="908ce-105">The Invoke Method</span></span>

<span data-ttu-id="908ce-106">Var olan bir cmdlet'i çağırarak tüm cmdlet'ler çağırabilirsiniz [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) yönteminden yöntemi gibi işleme giriş içinde [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), diğer bir deyişle cmdlet'i tarafından geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="908ce-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="908ce-107">Ancak, doğrudan öğesinden türetilen cmdlet'leri çağırabilirsiniz [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="908ce-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="908ce-108">Türetilen bir cmdlet çağrılamıyor [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="908ce-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="908ce-109">[System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) yöntemi aşağıdaki çeşitler sahiptir.</span><span class="sxs-lookup"><span data-stu-id="908ce-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="908ce-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Bu cmdlet nesnesini başlatır ve "T" türü nesnelerinin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="908ce-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="908ce-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Bu cmdlet nesnesini başlatır ve kesin türü belirtilmiş emumerator döndürür.</span><span class="sxs-lookup"><span data-stu-id="908ce-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="908ce-112">Bu değişken, nesneleri koleksiyonda özel işlemler gerçekleştirmek için kullanılacak kullanıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="908ce-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="908ce-113">Örnekler</span><span class="sxs-lookup"><span data-stu-id="908ce-113">Examples</span></span>

|<span data-ttu-id="908ce-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="908ce-114">Example</span></span>|<span data-ttu-id="908ce-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="908ce-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="908ce-116">Bir Cmdlet cmdlet'lerin çağırma</span><span class="sxs-lookup"><span data-stu-id="908ce-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="908ce-117">Bu örnekte, başka bir cmdlet içinde cmdlet'inden çağrılacak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="908ce-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="908ce-118">Bir Cmdlet içinde betikleri çağırma</span><span class="sxs-lookup"><span data-stu-id="908ce-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="908ce-119">Bu örnek cmdlet'in içinde başka bir cmdlet için sağlanan bir betik çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="908ce-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="908ce-120">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="908ce-120">See Also</span></span>

[<span data-ttu-id="908ce-121">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="908ce-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
