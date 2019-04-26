---
title: Dosya biçimlendirme bir PowerShell yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083585"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="eaf04-102">PowerShell Biçimlendirme Dosyası Yazma</span><span class="sxs-lookup"><span data-stu-id="eaf04-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="eaf04-103">"Biçimlendirme bir PowerShell dosyasını yazma" cmdlet'leri veya komut satırı nesnelere çıkış işlevleri yazma komut geliştiriciler içindir.</span><span class="sxs-lookup"><span data-stu-id="eaf04-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="eaf04-104">Biçimlendirme dosyaları, PowerShell komut satırında bu nesnelerin biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eaf04-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="eaf04-105">Bu belge dosyaları, biçimlendirme genel bir açıklama bu dosyaların, bu dosyalar ve başvuru bölümünde, XML öğeleri için kullanılan XML örnekleri yazılırken anlamanız gereken kavramlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaf04-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="eaf04-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="eaf04-106">In This Section</span></span>

<span data-ttu-id="eaf04-107">[Dosya genel bakış biçimlendirme](./formatting-file-overview.md) Describes bir biçim dosyası ve .NET nesneleri için tanımlanan biçimi görünüm farklı türlerini dosyasında tanımlanan ortak özellikleri dahil olmak üzere bir biçimlendirme dosyasının genel bileşenleri ve Basitleştirilmiş bir tablo görünümü tanımlamak için kullanılan XML örneği.</span><span class="sxs-lookup"><span data-stu-id="eaf04-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="eaf04-108">[Dosya kavramları biçimlendirme](./formatting-file-concepts.md) zaman kendi biçimlendirme, tanımlayabileceğiniz görünüm farklı türlerini ve özel bileşenlerinin bu görünümleri gibi dosyaları oluşturma bilmek ihtiyacınız olabilecek bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="eaf04-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="eaf04-109">[Biçimlendirme dosya örnekleri](./examples-of-formatting-files.md) Tablo görünümü, bir liste görünümü ve geniş bir görünüm örneklerini yanı sıra, seçim kümeleri, seçim koşulları gibi özellikleri tanımlamak nasıl gösteren örnekler de dahil olmak üzere bazı biçimlendirme dosyaları sağlayan XML örnekleri ve Ortak Denetimler.</span><span class="sxs-lookup"><span data-stu-id="eaf04-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="eaf04-110">[Biçimlendirme XML başvurusu](./format-schema-xml-reference.md) biçimlendirme dosyasında kullanılan XML öğeleri için başvuru konularını içerir.</span><span class="sxs-lookup"><span data-stu-id="eaf04-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
