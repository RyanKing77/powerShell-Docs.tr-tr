---
title: ValidateCount özniteliği bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983907"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="71639-102">ValidateCount Özniteliği Bildirimi</span><span class="sxs-lookup"><span data-stu-id="71639-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="71639-103">ValidateCount öznitelik bağımsız değişkenleri bir cmdlet parametresi için izin verilen minimum ve maksimum sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="71639-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="71639-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71639-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="71639-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71639-105">Parameters</span></span>

<span data-ttu-id="71639-106">`MinLength` ([System.Int32][]) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71639-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="71639-107">En az sayıda bağımsız değişken belirtir.</span><span class="sxs-lookup"><span data-stu-id="71639-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="71639-108">`MaxLength`([System.Int32][]) gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71639-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="71639-109">En fazla sayıda bağımsız değişken belirtir.</span><span class="sxs-lookup"><span data-stu-id="71639-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="71639-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71639-110">Remarks</span></span>

- <span data-ttu-id="71639-111">Bu öznitelik bildirmek hakkında daha fazla bilgi için bkz. [bir bağımsız değişken sayısı doğrulama][].</span><span class="sxs-lookup"><span data-stu-id="71639-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="71639-112">Bu öznitelik değil çağrıldığında karşılık gelen bir cmdlet parametresi herhangi bir sayıda bağımsız değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="71639-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="71639-113">Windows PowerShell çalışma zamanı, aşağıdaki koşullarda bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="71639-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="71639-114">`MinLength` Ve `MaxLength` öznitelik parametreleri türünde olmayan [System.Int32][].</span><span class="sxs-lookup"><span data-stu-id="71639-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="71639-115">Değerini `MaxLength` öznitelik parametresi değerini azdır `MinLength` parametre özniteliği.</span><span class="sxs-lookup"><span data-stu-id="71639-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="71639-116">ValidateCount özniteliği tarafından tanımlanan [System.Management.Automation.ValidateCountAttribute][] sınıfı.</span><span class="sxs-lookup"><span data-stu-id="71639-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="71639-117">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="71639-117">See Also</span></span>

<span data-ttu-id="71639-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="71639-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="71639-119">[Bir bağımsız değişken sayısı doğrulama][]</span><span class="sxs-lookup"><span data-stu-id="71639-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="71639-120">[Bir Windows PowerShell cmdlet'i yazma][]</span><span class="sxs-lookup"><span data-stu-id="71639-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Bir bağımsız değişken sayısı doğrulama]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Bir Windows PowerShell cmdlet'i yazma]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
