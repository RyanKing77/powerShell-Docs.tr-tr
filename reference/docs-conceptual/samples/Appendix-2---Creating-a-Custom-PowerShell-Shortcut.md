---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Ek 2 Özel bir PowerShell Kısayolu Oluşturma
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057869"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="3a665-103">Ek 2 - özel bir PowerShell kısayolu oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a665-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="3a665-104">Aşağıdaki yordam özelleştirilmiş birkaç uygun seçenekleri olan bir Windows PowerShell kısayolu oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a665-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="3a665-105">Powershell.exe işaret eden bir kısayol oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a665-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="3a665-106">Kısayoluna sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3a665-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="3a665-107">Tıklayın **seçenekleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="3a665-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="3a665-108">İçinde **düzenleme seçenekleri** bölümünden **Düzen** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="3a665-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="3a665-109">Bu ayar farenin sol düğmesine sürükleyerek Windows PowerShell konsol penceresine metin seçmenize olanak verir ve ENTER tuşuna basarak veya sağ fare metni panoya kopyalamak olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3a665-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="3a665-110">İçinde **düzenleme seçenekleri** bölümünden **ekleme modu** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="3a665-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="3a665-111">Bu ayarı otomatik olarak Panodaki metni yapıştırmak için konsol penceresinde sağ olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a665-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="3a665-112">İçinde **komut geçmişi** bölümüne yazın veya 1 ile 999 içinde arasında bir sayı seçin **arabellek boyutu** kutusu.</span><span class="sxs-lookup"><span data-stu-id="3a665-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="3a665-113">Bu konsol arabellekteki tutulacak yazılı komutları sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3a665-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="3a665-114">İçinde **komut geçmişi** bölümünden **eski kopyaları at** konsol arabellekteki yinelenen komutları ortadan kaldırmak için onay kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="3a665-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="3a665-115">Tıklayın **Düzen** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="3a665-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="3a665-116">İçinde **ekran arabelleğinin** bölümünde, 1 ile 9999 içinde arasında bir sayı yazın **yükseklik** kutusu.</span><span class="sxs-lookup"><span data-stu-id="3a665-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="3a665-117">Yükseklik ara belleğe alınır çıkış satırlarını sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3a665-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="3a665-118">Bu satırları korunur konsol penceresinden kaydırdığınızda görüntülemek için en büyük sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="3a665-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="3a665-119">Bu sayı gösterilen daha düşük olup olmadığını **pencere boyutunu** bölümünde pencere boyutu yüksekliği için aynı değeri otomatik olarak azaltılır.</span><span class="sxs-lookup"><span data-stu-id="3a665-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="3a665-120">İçinde **pencere boyutunu** bölümünde, 1 ile 9999 genişliği arasında bir sayı yazın.</span><span class="sxs-lookup"><span data-stu-id="3a665-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="3a665-121">Bu konsol penceresi görüntülenen bir karakter sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3a665-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="3a665-122">Varsayılan genişliğini 80'dir ve Windows PowerShell'in çıktı biçimlendirme bu genişliği için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3a665-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="3a665-123">Bunu Temizle açıldığında, masaüstünde, belirli bir noktada konsol yerleştirmek istiyorsanız **izin pencere konumunu sistem** onay kutusuna **pencere konumu** bölümüne ve ardından değerlerideğiştirin **Sol** ve **üst** kutularındaki **pencere konumu** bölümü.</span><span class="sxs-lookup"><span data-stu-id="3a665-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="3a665-124">**Tamam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3a665-124">Click **OK**.</span></span>