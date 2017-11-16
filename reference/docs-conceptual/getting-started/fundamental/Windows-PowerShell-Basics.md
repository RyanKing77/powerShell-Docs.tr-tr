---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell temel kavramları"
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: 7b5cdfce876aa7d5559fe772379829011b275a02
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-basics"></a><span data-ttu-id="fef81-103">Windows PowerShell temel kavramları</span><span class="sxs-lookup"><span data-stu-id="fef81-103">Windows PowerShell Basics</span></span>
<span data-ttu-id="fef81-104">Grafik kullanıcı arabirimleri çoğu bilgisayar kullanıcıları için bilinen bazı temel kavramları kullanın.</span><span class="sxs-lookup"><span data-stu-id="fef81-104">Graphical user interfaces use some basic concepts that are well known to most computer users.</span></span> <span data-ttu-id="fef81-105">Kullanıcıların görevleri gerçekleştirmek için bu arabirimleri benzerlik üzerinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="fef81-105">Users rely on the familiarity of those interfaces to accomplish tasks.</span></span> <span data-ttu-id="fef81-106">İşletim sistemleri, genellikle bağlam özgü işlevsellik erişmek için belirli işlevleri ve bağlam menülerini erişmek için aşağı açılır menüler ile gözatılabilir öğeleri grafik gösterimi ile kullanıcılar sunar.</span><span class="sxs-lookup"><span data-stu-id="fef81-106">Operating systems present users with a graphical representation of items that can be browsed, usually with drop-down menus for accessing specific functionality and context menus for accessing context-specific functionality.</span></span>

<span data-ttu-id="fef81-107">Menüleri veya kullanıcının yardımcı olmak için grafik sistemleri olmadığı için Windows PowerShell gibi komut satırı arabirimi (CLI) bilgilerini ifşa farklı bir yaklaşım kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fef81-107">A command-line interface (CLI), such as Windows PowerShell, must use a different approach to expose information, because it does not have menus or graphical systems to help the user.</span></span> <span data-ttu-id="fef81-108">Kullanabilmek için önce komut adlarını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fef81-108">You need to know command names before you can use them.</span></span> <span data-ttu-id="fef81-109">GUI ortamında özellikleri eşdeğer karmaşık komutları yazabilirsiniz rağmen sık kullanılan komutlar ve komut parametreleri ile aşina olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="fef81-109">Although you can type complex commands that are equivalent to the features in a GUI environment, you must become familiar with commonly-used commands and command parameters.</span></span>

<span data-ttu-id="fef81-110">Çoğu CLIs kullanıcı arabirimi öğrenmek için yardımcı olabilecek düzenlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="fef81-110">Most CLIs do not have patterns that can help the user to learn the interface.</span></span> <span data-ttu-id="fef81-111">İlk işletim sistemi Kabukları CLIs olması nedeniyle birçok komut ve parametre adlarını rasgele seçilmedi.</span><span class="sxs-lookup"><span data-stu-id="fef81-111">Because CLIs were the first operating system shells, many command names and parameter names were selected arbitrarily.</span></span> <span data-ttu-id="fef81-112">Kısa komut adlarının Temizle olanları genellikle seçilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fef81-112">Terse command names were generally chosen over clear ones.</span></span> <span data-ttu-id="fef81-113">Ancak yardım sistemleri ve komut tasarım standartları çoğu CLIs tümleştirilmiştir, komut kümesi hala on yılları önce kararlara tarafından şeklinde böylece bunlar genellikle en erken komutları ile uyumluluk için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fef81-113">Although help systems and command design standards are integrated into most CLIs, they have been generally designed for compatibility with the earliest commands, so the command set is still shaped by decisions made decades ago.</span></span>

<span data-ttu-id="fef81-114">Windows PowerShell Geçmiş bilgisi CLIs kullanıcının yararlanmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fef81-114">Windows PowerShell was designed to take advantage of a user's historic knowledge of CLIs.</span></span> <span data-ttu-id="fef81-115">Bu bölümde, biz bazı temel Araçlar ve Windows PowerShell hızla bilgi edinmek için kullanabileceğiniz kavramları hakkında konuşur.</span><span class="sxs-lookup"><span data-stu-id="fef81-115">In this chapter, we will talk about some basic tools and concepts that you can use to learn Windows PowerShell quickly.</span></span> <span data-ttu-id="fef81-116">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="fef81-116">They include:</span></span>

- <span data-ttu-id="fef81-117">Get-Command kullanma</span><span class="sxs-lookup"><span data-stu-id="fef81-117">Using Get-Command</span></span>

- <span data-ttu-id="fef81-118">Cmd.exe ve UNIX komutları kullanarak</span><span class="sxs-lookup"><span data-stu-id="fef81-118">Using Cmd.exe and UNIX commands</span></span>

- <span data-ttu-id="fef81-119">Dış komutları kullanarak</span><span class="sxs-lookup"><span data-stu-id="fef81-119">Using External Commands</span></span>

- <span data-ttu-id="fef81-120">Sekme tamamlama kullanma</span><span class="sxs-lookup"><span data-stu-id="fef81-120">Using Tab-Completion</span></span>

- <span data-ttu-id="fef81-121">Get-Help kullanma</span><span class="sxs-lookup"><span data-stu-id="fef81-121">Using Get-Help</span></span>

