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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068105"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="5d060-102">GetProc Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="5d060-102">GetProc Tutorial</span></span>

<span data-ttu-id="5d060-103">Bu bölüm, bunun için bir Get-Proc cmdlet oluşturma çok benzer bir öğretici sağlar [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) sağlanan tarafından Windows PowerShell cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="5d060-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="5d060-104">Bu öğretici, cmdlet'leri nasıl uygulandığını gösteren kod parçalarını ve kod bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d060-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="5d060-105">Bu öğreticide konuları</span><span class="sxs-lookup"><span data-stu-id="5d060-105">Topics in this Tutorial</span></span>

<span data-ttu-id="5d060-106">Bu öğreticide konular, önceki konu başlığında açıklanan üzerinde ne oluşturmaya her konu ile ardışık olarak okunacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5d060-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="5d060-107">[Parametresiz bir cmdlet'i oluşturma](./creating-a-cmdlet-without-parameters.md) Bu bölümde parametre kullanmadan bir yerel bilgisayardan bilgilerini alır ve sonra bilgi işlem hattına yazan bir cmdlet'i oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d060-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="5d060-108">[Bu işlem komut satırı giriş parametreleri ekleme](./adding-parameters-that-process-command-line-input.md) Bu bölümde, cmdlet cmdlet'e geçirilen açık nesneler göre giriş işleyebilmesi Get-Proc cmdlet'e parametre eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d060-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="5d060-109">Açıklanan uygulama burada kendi adına göre işlemler alır ve ardından işlem hattının bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="5d060-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="5d060-110">[Bu işlem ardışık giriş parametreleri ekleme](./adding-parameters-that-process-pipeline-input.md) Bu bölümde, cmdlet ardışık düzende geçirilen nesneleri işleyebilmesi Get-Proc cmdlet'e parametre eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d060-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="5d060-111">Açıklanan uygulama cmdlet burada işlemleri cmdlet'e geçirilen nesneleri temel alır ve ardından işlem hattının bilgi yazar.</span><span class="sxs-lookup"><span data-stu-id="5d060-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="5d060-112">[Bilgisayarınızı cmdlet'e ekleme olmak üzere Sonlandırmasız hata raporlama](./adding-non-terminating-error-reporting-to-your-cmdlet.md) Bu bölümde, bir cmdlet için olmak üzere sonlandırmasız rapor eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d060-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="5d060-113">Burada açıklanan uygulama girişi işlerken oluşur ve bir hata kaydı hatası akışa Yazar olmak üzere sonlandırmasız hatalar algılar.</span><span class="sxs-lookup"><span data-stu-id="5d060-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d060-114">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="5d060-114">See Also</span></span>

[<span data-ttu-id="5d060-115">Parametresiz bir cmdlet'i oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d060-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="5d060-116">Komut satırı giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="5d060-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="5d060-117">İşlem ardışık düzen giriş parametreleri ekleme</span><span class="sxs-lookup"><span data-stu-id="5d060-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="5d060-118">Cmdlet'inize için olmak üzere Sonlandırmasız rapor ekleme</span><span class="sxs-lookup"><span data-stu-id="5d060-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="5d060-119">Windows PowerShell SDK'sı</span><span class="sxs-lookup"><span data-stu-id="5d060-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
