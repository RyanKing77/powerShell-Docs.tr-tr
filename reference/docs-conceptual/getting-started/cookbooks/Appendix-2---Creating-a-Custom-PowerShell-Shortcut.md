---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Ek özel PowerShell kısayol oluşturma 2"
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: d5e554f6f062fc5bf1beddd2aca1acf0b93d2133
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="a4091-103">Ek 2 - özel PowerShell kısayol oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4091-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>
<span data-ttu-id="a4091-104">Aşağıdaki yordamda, özelleştirilmiş birkaç uygun seçenek olan Windows PowerShell için kısayol oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4091-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="a4091-105">Powershell.exe işaret eden bir kısayol oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4091-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="a4091-106">Kısayoluna sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="a4091-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="a4091-107">Tıklatın **seçenekleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="a4091-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="a4091-108">İçinde **seçeneklerini Düzenle** bölümünde, select **Düzen** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="a4091-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="a4091-109">Bu ayar, sol fare düğmesini sürükleyerek Windows PowerShell konsol penceresinde metni seçme sağlar ve ENTER tuşuna basarak veya fareyi sağ tıklanarak metni panoya kopyala olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a4091-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="a4091-110">İçinde **seçeneklerini Düzenle** bölümünde, select **Ekle modu** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="a4091-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="a4091-111">Bu ayarı otomatik olarak Panodaki metni yapıştırmak için konsol penceresinde sağ olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4091-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="a4091-112">İçinde **komut geçmişini** bölümünde yazın veya 1 ile 999 içinde arasında bir sayı seçin **arabellek boyutu** kutusu.</span><span class="sxs-lookup"><span data-stu-id="a4091-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="a4091-113">Bu konsol arabellekte tutulacak yazılı komutları sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a4091-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="a4091-114">İçinde **komut geçmişini** bölümünde, select **eski kopyaları at** konsol arabellek yinelenen komutları ortadan kaldırmak üzere onay kutusunu.</span><span class="sxs-lookup"><span data-stu-id="a4091-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="a4091-115">Tıklatın **düzeni** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="a4091-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="a4091-116">İçinde **ekran arabelleğinde** bölümünde, 1 ile 9999 içinde arasında bir sayı yazın **yükseklik** kutusu.</span><span class="sxs-lookup"><span data-stu-id="a4091-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="a4091-117">Yükseklik çıktısını arabelleğe alınmış satır sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4091-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="a4091-118">Maksimum konsol penceresinde kaydırma yapılırken görüntülemek için korunur satır sayısı budur.</span><span class="sxs-lookup"><span data-stu-id="a4091-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="a4091-119">Bu sayı gösterilen yükseklik daha düşük olup olmadığını **pencere boyutu** bölümünde, pencere boyutu yüksekliği otomatik olarak aynı değeri azalır.</span><span class="sxs-lookup"><span data-stu-id="a4091-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="a4091-120">İçinde **pencere boyutu** bölümünde, 1 ile 9999 genişliği için arasında bir sayı yazın.</span><span class="sxs-lookup"><span data-stu-id="a4091-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="a4091-121">Bu konsol penceresi görüntülenen karakter sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4091-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="a4091-122">Varsayılan genişliğini 80'dir ve Windows PowerShell'in çıktı biçimlendirmesi bu genişliği için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4091-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="a4091-123">Masaüstünde belirli bir noktada, Temizle açıldığında konsol yerleştirmek istiyorsanız **izin pencere konumunu sistem** onay kutusuna **pencere konumunu** bölümünde ve ardından değerlerindedeğişiklik **Sol** ve **üst** kutularındaki **pencere konumunu** bölümü.</span><span class="sxs-lookup"><span data-stu-id="a4091-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="a4091-124">**Tamam**’a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a4091-124">Click **OK**.</span></span>

