---
title: GetProc Eğitmeni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851334"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="c7f36-102">GetProc Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="c7f36-102">GetProc Tutorial</span></span>

<span data-ttu-id="c7f36-103">Bu bölüm, bunun için bir Get-Proc cmdlet oluşturma çok benzer bir öğretici sağlar [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) sağlanan tarafından Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="c7f36-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="c7f36-104">Bu öğretici, cmdlet'leri nasıl uygulandığını gösteren kod parçalarını ve kod bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7f36-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="c7f36-105">Bu öğreticide konuları</span><span class="sxs-lookup"><span data-stu-id="c7f36-105">Topics in this Tutorial</span></span>

<span data-ttu-id="c7f36-106">Bu öğreticide konular, önceki konu başlığında açıklanan üzerinde ne oluşturmaya her konu ile ardışık olarak okunacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7f36-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="c7f36-107">[Parametresiz bir cmdlet'i oluşturma](./creating-a-cmdlet-without-parameters.md) Bu bölümde parametre kullanmadan bir yerel bilgisayardan bilgilerini alır ve sonra bilgi işlem hattına yazan bir cmdlet'i oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7f36-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="c7f36-108">[Bu işlem komut satırı giriş parametreleri ekleme](./adding-parameters-that-process-command-line-input.md) Bu bölümde, cmdlet cmdlet'e geçirilen açık nesneler göre giriş işleyebilmesi Get-Proc cmdlet'e parametre eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7f36-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="c7f36-109">Açıklanan uygulama burada kendi adına göre işlemler alır ve ardından işlem hattının bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="c7f36-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="c7f36-110">[Bu işlem ardışık giriş parametreleri ekleme](./adding-parameters-that-process-pipeline-input.md) Bu bölümde, cmdlet ardışık düzende geçirilen nesneleri işleyebilmesi Get-Proc cmdlet'e parametre eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7f36-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="c7f36-111">Açıklanan uygulama cmdlet burada işlemleri cmdlet'e geçirilen nesneleri temel alır ve ardından işlem hattının bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="c7f36-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="c7f36-112">[Bilgisayarınızı cmdlet'e ekleme olmak üzere Sonlandırmasız hata raporlama](./adding-non-terminating-error-reporting-to-your-cmdlet.md) Bu bölümde, bir cmdlet için olmak üzere sonlandırmasız rapor eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7f36-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="c7f36-113">Burada açıklanan uygulama girişi işlerken oluşur ve bir hata kaydı hatası akışa Yazar olmak üzere sonlandırmasız hatalar algılar.</span><span class="sxs-lookup"><span data-stu-id="c7f36-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7f36-114">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c7f36-114">See Also</span></span>

[<span data-ttu-id="c7f36-115">Parametresiz bir cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7f36-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="c7f36-116">Komut satırı giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="c7f36-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c7f36-117">İşlem ardışık düzen giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="c7f36-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="c7f36-118">Cmdlet'inize için olmak üzere Sonlandırmasız rapor ekleme</span><span class="sxs-lookup"><span data-stu-id="c7f36-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="c7f36-119">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="c7f36-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
