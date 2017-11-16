---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell ISE PowerShell sekme oluşturma"
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 3cfeb18babe6b63f0e02da8cf0fd460950f1afce
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="62f8c-103">Windows PowerShell ISE PowerShell sekme oluşturma</span><span class="sxs-lookup"><span data-stu-id="62f8c-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>
<span data-ttu-id="62f8c-104">Sekmeleri içinde Windows PowerShell Tümleşik komut dosyası ortamı (ISE), aynı anda oluşturmak ve aynı uygulama içinde birden fazla yürütme ortamlarında kullanmak izin verir.</span><span class="sxs-lookup"><span data-stu-id="62f8c-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="62f8c-105">Her PowerShell sekmesinde ayrı yürütme ortamı ya da oturum karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="62f8c-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="62f8c-106">**NOT**:</span><span class="sxs-lookup"><span data-stu-id="62f8c-106">**NOTE**:</span></span>
>
> <span data-ttu-id="62f8c-107">Değişkenler, İşlevler ve bir sekmede oluşturduğunuz diğer adlar diğerine taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="62f8c-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="62f8c-108">Farklı Windows PowerShell oturumlarınızı oldukları.</span><span class="sxs-lookup"><span data-stu-id="62f8c-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="62f8c-109">Açmak veya Windows PowerShell'de sekmesini kapatmak için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="62f8c-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="62f8c-110">Sekme yeniden adlandırmak için ayarlanmış [DisplayName](The-PowerShellTab-Object.md#displayname) Windows PowerShell sekme komut dosyası nesnesinde özelliği.</span><span class="sxs-lookup"><span data-stu-id="62f8c-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="62f8c-111">Oluşturma ve yeni bir PowerShell sekmesi kullanma</span><span class="sxs-lookup"><span data-stu-id="62f8c-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="62f8c-112">Üzerinde **dosya** menüsünde tıklatın **yeni PowerShell sekme**. Yeni bir PowerShell sekmesi her zaman etkin pencereyi açar.</span><span class="sxs-lookup"><span data-stu-id="62f8c-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="62f8c-113">PowerShell sekmeleri artımlı olarak açılmış sırayla numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="62f8c-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="62f8c-114">Her sekme kendi Windows PowerShell konsol penceresi ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="62f8c-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="62f8c-115">Kendi oturumu açma (Bu Windows PowerShell ISE 2.0 üzerinde 8 sınırlıdır.) bir seferde en fazla 32 PowerShell sekmelerle olabilir</span><span class="sxs-lookup"><span data-stu-id="62f8c-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="62f8c-116">Bu tıklatarak Not **yeni** veya **açık** araç çubuğundaki simgelerin yeni bir sekme ayrı bir oturumla oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="62f8c-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="62f8c-117">Bunun yerine, bu düğmeleri yeni veya var olan komut dosyası şu anda etkin sekmede ile oturum açın.</span><span class="sxs-lookup"><span data-stu-id="62f8c-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="62f8c-118">Birden çok komut dosyalarını her sekmesi ve oturum açma olabilir.</span><span class="sxs-lookup"><span data-stu-id="62f8c-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="62f8c-119">İlişkili oturum etkin olduğunda, bir oturum için komut dosyası sekmeleri yalnızca oturum sekmeler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="62f8c-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="62f8c-120">Bir PowerShell sekmesi etkin hale getirmek için sekmesini tıklatın. Açık olan tüm PowerShell sekmeleri aralarından seçim yapabileceğiniz **Görünüm** menüsünde, kullanmak istediğiniz PowerShell sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="62f8c-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="62f8c-121">Oluşturma ve yeni bir uzaktan PowerShell sekmesi kullanma</span><span class="sxs-lookup"><span data-stu-id="62f8c-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="62f8c-122">Üzerinde **dosya** menüsünde tıklatın **yeni uzak PowerShell sekme** uzak bir bilgisayarda oturum oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="62f8c-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="62f8c-123">Bir iletişim kutusu görünür ve uzak bağlantı kurmak için gerekli ayrıntıları girmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="62f8c-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="62f8c-124">Uzak sekmesinin işlevleri yerel bir PowerShell sekmesi olduğu gibi ancak uzak bilgisayarda komutları ve komut dosyaları çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="62f8c-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="62f8c-125">PowerShell sekmesini kapatmak için</span><span class="sxs-lookup"><span data-stu-id="62f8c-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="62f8c-126">Bir sekmeyi kapatmak için aşağıdaki tekniklerden herhangi birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="62f8c-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="62f8c-127">Kapatmak istediğiniz sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="62f8c-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="62f8c-128">Üzerinde **dosya** menüsünde tıklatın **PowerShell sekmeyi Kapat**, veya Kapat düğmesini tıklatın (**X**) etkin bir sekmede sekmesini kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="62f8c-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="62f8c-129">Kaydedilmemiş değişiklikleriniz varsa PowerShell sekmesindeki açık dosyalar kapatmak, kaydedin veya bunları atmanız istenir.</span><span class="sxs-lookup"><span data-stu-id="62f8c-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="62f8c-130">Bir komut dosyasını kaydetme hakkında daha fazla bilgi için bkz: [bir komut dosyası kaydetmek için nasıl](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="62f8c-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="62f8c-131">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="62f8c-131">See Also</span></span>

- [<span data-ttu-id="62f8c-132">Windows PowerShell ISE kullanma</span><span class="sxs-lookup"><span data-stu-id="62f8c-132">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="62f8c-133">Konsol bölmesinde Windows PowerShell ISE kullanma</span><span class="sxs-lookup"><span data-stu-id="62f8c-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)

