---
title: Parametresi giriş doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6c700c8-0889-49a1-a990-8c6e9aaf4735
caps.latest.revision: 6
ms.openlocfilehash: 5166213f8247fa23d5e0b3fdfd2367062d595169
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067765"
---
# <a name="how-to-validate-parameter-input"></a><span data-ttu-id="de5fa-102">Parametre Girişini Doğrulama</span><span class="sxs-lookup"><span data-stu-id="de5fa-102">How to Validate Parameter Input</span></span>

<span data-ttu-id="de5fa-103">Bu bölüm, parametre girişi doğrulama kuralları uygulamak için çeşitli öznitelikleri kullanarak doğrulama işlemini gösteren örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="de5fa-103">This section contains examples that show how to validate parameter input by using various attributes to implement validation rules.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="de5fa-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="de5fa-104">In This Section</span></span>

<span data-ttu-id="de5fa-105">[Bir bağımsız değişken kümesi doğrulama](./how-to-validate-an-argument-set.md) ArgumentSet özniteliğini kullanarak bir bağımsız değişken doğrulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="de5fa-105">[How to Validate an Argument Set](./how-to-validate-an-argument-set.md) Describes how to validate an argument set by using the ArgumentSet attribute.</span></span>

<span data-ttu-id="de5fa-106">[Bir bağımsız değişkeni aralık doğrulama](./how-to-validate-an-argument-range.md) ArgumentRange özniteliğini kullanarak bir bağımsız değişkeni aralık doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="de5fa-106">[How to Validate an Argument Range](./how-to-validate-an-argument-range.md) Describes how to validate an argument range by using the ArgumentRange attribute.</span></span>

<span data-ttu-id="de5fa-107">[Bir bağımsız değişken desen doğrulama](./how-to-validate-an-argument-pattern.md) ArgumentPattern özniteliğini kullanarak bir bağımsız değişken desen doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="de5fa-107">[How to Validate an Argument Pattern](./how-to-validate-an-argument-pattern.md) Describes how to validate an argument pattern by using the ArgumentPattern attribute.</span></span>

<span data-ttu-id="de5fa-108">[Bağımsız değişken uzunluğu doğrulama](./how-to-validate-the-argument-length.md) ArgumentLength özniteliğini kullanarak bir bağımsız değişken uzunluğu doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="de5fa-108">[How to Validate the Argument Length](./how-to-validate-the-argument-length.md) Describes how to validate the length of an argument by using the ArgumentLength attribute.</span></span>

<span data-ttu-id="de5fa-109">[Bir bağımsız değişken sayısı doğrulama](./how-to-validate-an-argument-count.md) ArgumentCount özniteliğini kullanarak bir bağımsız değişken sayısı doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="de5fa-109">[How to Validate an Argument Count](./how-to-validate-an-argument-count.md) Describes how to validate an argument count by using the ArgumentCount attribute.</span></span>

<span data-ttu-id="de5fa-110">Bir parametre bildirilen biçimini doğrulama etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="de5fa-110">The way a parameter is declared can affect validation.</span></span> <span data-ttu-id="de5fa-111">Daha fazla bilgi için [Cmdlet parametreleri bildirmek için nasıl](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="de5fa-111">For more information, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

## <a name="reference"></a><span data-ttu-id="de5fa-112">Başvuru</span><span class="sxs-lookup"><span data-stu-id="de5fa-112">Reference</span></span>

## <a name="see-also"></a><span data-ttu-id="de5fa-113">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="de5fa-113">See Also</span></span>

[<span data-ttu-id="de5fa-114">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="de5fa-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
