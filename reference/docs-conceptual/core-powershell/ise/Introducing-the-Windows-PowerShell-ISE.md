---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell ISE Tanıtımı"
ms.openlocfilehash: 75242c20548e2e83397867214417a48806c897ec
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="864c0-103">Windows PowerShell ISE Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="864c0-103">Introducing the Windows PowerShell ISE</span></span>
<span data-ttu-id="864c0-104">Windows PowerShell Tümleşik komut dosyası ortamı (ISE), Windows PowerShell için bir ana bilgisayar uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="864c0-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="864c0-105">Windows PowerShell ISE'de da çalıştırma komutları ve yazma, test ve tek bir Windows tabanlı grafik kullanıcı arabirimi çok satırlı düzenleme, sekme tamamlama, sözdizimi renklendirmesi, seçmeli yürütme, bağlama duyarlı Yardım ve Destek ile betiklerde hata ayıklama Sağdan sola yazılan diller.</span><span class="sxs-lookup"><span data-stu-id="864c0-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span>
<span data-ttu-id="864c0-106">Windows PowerShell konsolunda gerçekleştirecek gerçekleştirdiğiniz görevlerin çoğunu gerçekleştirmek için menü öğeleri ve klavye kısayollarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="864c0-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span>  <span data-ttu-id="864c0-107">Örneğin, Windows PowerShell ISE kodda hata ayıklama işlemi yaparken, bir komut dosyasında bir satır kesme noktası ayarlamak için kod satırı sağ tıklayın ve ardından **kesme**.</span><span class="sxs-lookup"><span data-stu-id="864c0-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="864c0-108">Windows PowerShell ISE bu özelliklerin deneyin.</span><span class="sxs-lookup"><span data-stu-id="864c0-108">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="864c0-109">Çok satırlı düzenleme: komut Bölmesi'nde geçerli satır altında boş bir satır eklemek için SHIFT + ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="864c0-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>

- <span data-ttu-id="864c0-110">Seçmeli yürütme: bir komut dosyasının parçası çalıştırmak için çalıştırın ve ardından istediğiniz metni seçin **komut dosyasını Çalıştır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="864c0-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="864c0-111">Ya da F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="864c0-111">Or, press F5.</span></span>

- <span data-ttu-id="864c0-112">Bağlama duyarlı Yardım: türü **Invoke-Item**, ve F1 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="864c0-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="864c0-113">Yardım dosyası için Yardım konusu için açılır **Invoke-Item** cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="864c0-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="864c0-114">Windows PowerShell ISE görünümünü bazı yönlerini özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="864c0-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="864c0-115">Ayrıca, Windows PowerShell ISE burada işlevleri, diğer adlar, değişkenler ve kullandığınız komutları depolayabilir kendi Windows PowerShell profiliniz da vardır.</span><span class="sxs-lookup"><span data-stu-id="864c0-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="864c0-116">Windows PowerShell ISE başlatmak için</span><span class="sxs-lookup"><span data-stu-id="864c0-116">To start the Windows PowerShell ISE</span></span>

1. <span data-ttu-id="864c0-117">Aşağıdakilerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="864c0-117">Do one of the following:</span></span>

    -   <span data-ttu-id="864c0-118">Tıklatın **Başlat**, işaret **tüm programlar**, işaret **Windows PowerShell V2**ve ardından **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="864c0-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>

    -   <span data-ttu-id="864c0-119">Windows PowerShell Konsolu Cmd.exe veya Çalıştır kutusuna yazın, **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="864c0-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="864c0-120">Windows PowerShell ISE Yardım almak için</span><span class="sxs-lookup"><span data-stu-id="864c0-120">To get Help in the Windows PowerShell ISE</span></span>

- <span data-ttu-id="864c0-121">Üzerinde **yardımcı** menüsünde tıklatın **Windows PowerShell Yardımı**.</span><span class="sxs-lookup"><span data-stu-id="864c0-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="864c0-122">Veya F1 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="864c0-122">Or, press F1.</span></span> <span data-ttu-id="864c0-123">Windows PowerShell ISE ve tüm Get-Help cmdlet'ten kullanılabilir Yardım'ın da dahil olmak üzere Windows PowerShell açar dosya açıklar.</span><span class="sxs-lookup"><span data-stu-id="864c0-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>

