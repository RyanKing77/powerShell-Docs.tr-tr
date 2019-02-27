---
title: StopProc Eğitmeni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 6e1c8a4709988adfa59bda14eb3af52b0a79f1df
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847064"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="6eb78-102">StopProc Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="6eb78-102">StopProc Tutorial</span></span>

<span data-ttu-id="6eb78-103">Bu bölümde çok benzer Stop-Proc cmdlet oluşturmaya yönelik bir öğretici [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) sağlanan tarafından Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="6eb78-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="6eb78-104">Bu öğretici, cmdlet'leri nasıl uygulandığını gösteren kod parçalarını ve kod bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="6eb78-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>
<span data-ttu-id="6eb78-105">Bu bölümde çok benzer Stop-Proc cmdlet oluşturmaya yönelik bir öğretici [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) sağlanan tarafından Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="6eb78-105">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="6eb78-106">Bu öğretici, cmdlet'leri nasıl uygulandığını gösteren kod parçalarını ve kod bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="6eb78-106">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="6eb78-107">Bu öğreticide konuları</span><span class="sxs-lookup"><span data-stu-id="6eb78-107">Topics in this Tutorial</span></span>

<span data-ttu-id="6eb78-108">Bu öğreticide konular, önceki konu başlığında açıklanan üzerinde ne oluşturmaya her konu ile ardışık olarak okunacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6eb78-108">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="6eb78-109">[Bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md) Bu bölümde bilgisayar üzerinde çalışan bir işlemin durdurulması gibi sistem değişiklikleri, destekleyen bir cmdlet oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6eb78-109">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="6eb78-110">[Kullanıcı iletileri Your cmdlet'e ekleme](./adding-user-messages-to-your-cmdlet.md) Bu bölüm, kullanıcı iletileri, hata ayıklama iletileri, uyarı iletilerini ve ilerleme durumu bilgileri için cmdlet yazma olanağı eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="6eb78-110">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="6eb78-111">[Diğer adları, joker karakter genişletmesi, ekleme ve Yardım için Cmdlet parametreleri](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) Bu bölümde parametre diğer adlarına, Yardım ve joker karakter genişletmesi destekleyen bir cmdlet oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6eb78-111">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="6eb78-112">[Parametre ayarlar Cmdlet'lerinde ekleme](./adding-parameter-sets-to-a-cmdlet.md) Bu bölümde, bir cmdlet'e parametre ayarlar eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="6eb78-112">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="6eb78-113">Parametre kümeleri çalışması için cmdlet'i farklı kullanıcı tarafından hangi parametrelerin belirtilen imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="6eb78-113">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="6eb78-114">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6eb78-114">See Also</span></span>

[<span data-ttu-id="6eb78-115">Bir Cmdlet oluşturma sistemi değiştirir</span><span class="sxs-lookup"><span data-stu-id="6eb78-115">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="6eb78-116">Kullanıcı iletileri, cmdlet'e ekleme</span><span class="sxs-lookup"><span data-stu-id="6eb78-116">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="6eb78-117">Diğer adları, joker karakter genişletmesi, ekleme ve Cmdlet parametreleri için Yardım</span><span class="sxs-lookup"><span data-stu-id="6eb78-117">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="6eb78-118">Cmdlet'leri için ayarlar parametresi eklendi</span><span class="sxs-lookup"><span data-stu-id="6eb78-118">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="6eb78-119">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="6eb78-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
