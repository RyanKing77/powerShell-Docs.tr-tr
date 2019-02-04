---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de bir PowerShell Sekmesi Oluşturma
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 080fe89bf1443f51460589b445431913fa20b4b8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688136"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="e7251-103">Windows PowerShell ISE’de bir PowerShell Sekmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7251-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="e7251-104">Sekmeler, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) aynı anda oluşturmak ve aynı uygulama içinde birden çok yürütme ortamları kullanma olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7251-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="e7251-105">Her bir PowerShell sekmesi, bir ayrı yürütme ortamı veya oturumu karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e7251-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="e7251-106">Değişkenler, İşlevler ve bir sekmede oluşturma diğer adları diğerine taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="e7251-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="e7251-107">Farklı Windows PowerShell oturumları değildirler.</span><span class="sxs-lookup"><span data-stu-id="e7251-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="e7251-108">Windows PowerShell'de bir sekmesini kapatın veya aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7251-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="e7251-109">Bir sekme yeniden adlandırmak için ayarlanmış [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) özelliği Windows PowerShell sekme betik oluşturma nesne.</span><span class="sxs-lookup"><span data-stu-id="e7251-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="e7251-110">Yeni bir PowerShell sekmesi oluşturma ve</span><span class="sxs-lookup"><span data-stu-id="e7251-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="e7251-111">Üzerinde **dosya** menüsünü tıklatın **yeni bir PowerShell sekmesi**. Yeni bir PowerShell sekmesi, her zaman etkin pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="e7251-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="e7251-112">PowerShell sekme, bunlar açık olan dosyalardaki sırayla artımlı olarak numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="e7251-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="e7251-113">Her sekme, kendi Windows PowerShell konsol penceresi ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="e7251-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="e7251-114">32 adede kadar PowerShell sekmelerle kendi oturumu açma (8, Windows PowerShell ISE 2.0 üzerinde sınırlı budur.) bir zaman olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7251-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="e7251-115">Sonuçlandığını unutmayın **yeni** veya **açık** araç çubuğundaki simgeler ayrı bir oturum ile yeni bir sekme oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="e7251-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="e7251-116">Bunun yerine, bu düğmeler şu anda etkin sekmede bir yeni veya mevcut bir komut dosyası ile bir oturumu açın.</span><span class="sxs-lookup"><span data-stu-id="e7251-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="e7251-117">Birden çok betik dosyaları her bir sekme ve oturum açma olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7251-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="e7251-118">İlişkili oturum etkin olduğunda bir oturum için betik sekmeleri yalnızca oturumu sekmeleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e7251-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="e7251-119">Bir PowerShell sekmesi etkin hale getirmek için sekmesinde tıklayın. Açık olan tüm PowerShell sekmeler aralarından seçim yapabileceğiniz **görünümü** menüsünde, kullanmak istediğiniz PowerShell sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e7251-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="e7251-120">Oluşturma ve yeni bir uzak PowerShell sekme kullanma</span><span class="sxs-lookup"><span data-stu-id="e7251-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="e7251-121">Üzerinde **dosya** menüsünde tıklatın **yeni uzak PowerShell sekme** uzak bir bilgisayarda oturum oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e7251-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="e7251-122">Bir iletişim kutusu görünür ve uzak bağlantı kurmak için gerekli ayrıntıları girmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="e7251-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="e7251-123">Uzak sekmesinin işlevleri yalnızca yerel bir PowerShell sekmesi gibi ancak uzak bilgisayarda komutlar ve komut dosyaları çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e7251-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="e7251-124">Bir PowerShell sekmesi kapatmak için</span><span class="sxs-lookup"><span data-stu-id="e7251-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="e7251-125">Bir sekme kapatmak için aşağıdaki tekniklerden birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e7251-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="e7251-126">Kapatmak istediğiniz sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e7251-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="e7251-127">Üzerinde **dosya** menüsünde tıklatın **PowerShell sekmeyi Kapat**, ya da Kapat düğmesine tıklayın (**X**) etkin sekmede sekmesini kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="e7251-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="e7251-128">Kaydedilmemiş değişiklikleriniz var, dosyaları PowerShell sekmede aç kapatmak, kaydetmek veya atmak istenir.</span><span class="sxs-lookup"><span data-stu-id="e7251-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="e7251-129">Bir komut dosyası kaydetme hakkında daha fazla bilgi için bkz. [kaydetmek bir komut dosyasına nasıl](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="e7251-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7251-130">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e7251-130">See Also</span></span>

- [<span data-ttu-id="e7251-131">Windows PowerShell ISE Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="e7251-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="e7251-132">Windows PowerShell ISE'de konsol bölmesini kullanma</span><span class="sxs-lookup"><span data-stu-id="e7251-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)