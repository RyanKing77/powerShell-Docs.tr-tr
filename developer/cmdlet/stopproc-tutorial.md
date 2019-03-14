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
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794408"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="795b5-102">StopProc Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="795b5-102">StopProc Tutorial</span></span>

<span data-ttu-id="795b5-103">Bu bölümde çok benzer Stop-Proc cmdlet oluşturmaya yönelik bir öğretici [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) sağlanan tarafından Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="795b5-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="795b5-104">Bu öğretici, cmdlet'leri nasıl uygulandığını gösteren kod parçalarını ve kod bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="795b5-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="795b5-105">Bu öğreticide konuları</span><span class="sxs-lookup"><span data-stu-id="795b5-105">Topics in this Tutorial</span></span>

<span data-ttu-id="795b5-106">Bu öğreticide konular, önceki konu başlığında açıklanan üzerinde ne oluşturmaya her konu ile ardışık olarak okunacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="795b5-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="795b5-107">[Bir Cmdlet oluşturma sistemi değiştirir](./creating-a-cmdlet-that-modifies-the-system.md) Bu bölümde bilgisayar üzerinde çalışan bir işlemin durdurulması gibi sistem değişiklikleri, destekleyen bir cmdlet oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="795b5-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="795b5-108">[Kullanıcı iletileri Your cmdlet'e ekleme](./adding-user-messages-to-your-cmdlet.md) Bu bölüm, kullanıcı iletileri, hata ayıklama iletileri, uyarı iletilerini ve ilerleme durumu bilgileri için cmdlet yazma olanağı eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="795b5-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="795b5-109">[Diğer adları, joker karakter genişletmesi, ekleme ve Yardım için Cmdlet parametreleri](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) Bu bölümde parametre diğer adlarına, Yardım ve joker karakter genişletmesi destekleyen bir cmdlet oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="795b5-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="795b5-110">[Parametre ayarlar Cmdlet'lerinde ekleme](./adding-parameter-sets-to-a-cmdlet.md) Bu bölümde, bir cmdlet'e parametre ayarlar eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="795b5-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="795b5-111">Parametre kümeleri çalışması için cmdlet'i farklı kullanıcı tarafından hangi parametrelerin belirtilen imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="795b5-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="795b5-112">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="795b5-112">See Also</span></span>

[<span data-ttu-id="795b5-113">Bir Cmdlet oluşturma sistemi değiştirir</span><span class="sxs-lookup"><span data-stu-id="795b5-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="795b5-114">Kullanıcı iletileri, cmdlet'e ekleme</span><span class="sxs-lookup"><span data-stu-id="795b5-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="795b5-115">Diğer adları, joker karakter genişletmesi, ekleme ve Cmdlet parametreleri için Yardım</span><span class="sxs-lookup"><span data-stu-id="795b5-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="795b5-116">Cmdlet'leri için ayarlar parametresi eklendi</span><span class="sxs-lookup"><span data-stu-id="795b5-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="795b5-117">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="795b5-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
