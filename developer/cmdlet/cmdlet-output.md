---
title: Cmdlet çıkışı | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1362f4cd-4e05-4ace-ade6-7128da8ad86c
caps.latest.revision: 10
ms.openlocfilehash: 4c6aacd49b0a87bca6806ba5f08a1b4d48a90959
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068564"
---
# <a name="cmdlet-output"></a><span data-ttu-id="d3a3c-102">Cmdlet Çıkışı</span><span class="sxs-lookup"><span data-stu-id="d3a3c-102">Cmdlet Output</span></span>

<span data-ttu-id="d3a3c-103">Bu bölümde, cmdlet çıktı ve cmdlet çıktı gibi hata iletileri ve nesneler oluşturmak için çağırabileceğiniz yöntemler türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3a3c-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="d3a3c-104">Bu bölümde Ayrıca, cmdlet tarafından döndürülen .NET Framework türleri tanımlama ve bu nesnelerin nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3a3c-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d3a3c-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d3a3c-105">In This Section</span></span>

<span data-ttu-id="d3a3c-106">[Cmdlet çıktı türleri](./types-of-cmdlet-output.md) türlerini ve cmdlet'leri oluşturabilen çıkış ve cmdlet çıktı üretmek için çağıran yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3a3c-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="d3a3c-107">[Cmdlet'i hata raporlama](./cmdlet-error-reporting.md) cmdlet'i hata raporlama, cmdlet çıkışı kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3a3c-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="d3a3c-108">[Çıkış nesnelerini genişleterek](./extending-output-objects.md) cmdlet'ler, İşlevler ve betikleri tarafından döndürülen .NET Framework nesneleri genişletmek için türler dosyaları (.ps1xml) kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3a3c-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="d3a3c-109">[PowerShell biçimlendirme dosyaları](../format/powershell-formatting-files.md) biçimlendirme dosyaları açıklar (. format.ps1xml) varsayılan tanımlama dosyaları görüntülemek için Windows PowerShell, .NET Framework nesneleri belirli bir dizi.</span><span class="sxs-lookup"><span data-stu-id="d3a3c-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="d3a3c-110">[Özel biçimlendirme dosyaları](./custom-formatting-files.md) nasıl kendi özel biçimlendirme oluşturmak için varsayılan üzerine yazmak için dosyaları, biçimleri görüntülemek veya kendi komutları tarafından döndürülen nesnelerin görünümünü tanımlamak için açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d3a3c-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3a3c-111">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d3a3c-111">See Also</span></span>

[<span data-ttu-id="d3a3c-112">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="d3a3c-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
