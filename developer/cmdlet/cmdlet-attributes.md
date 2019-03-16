---
title: Cmdlet öznitelikleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055181"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="c914b-102">Cmdlet Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="c914b-102">Cmdlet Attributes</span></span>

<span data-ttu-id="c914b-103">Windows PowerShell içinde kendi kodunuzu işlevselliği uygulamadan cmdlet'lerinizi için ortak işlevselliği eklemek için kullanabileceğiniz çeşitli özniteliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c914b-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="c914b-104">Bu cmdlet, ortak özellikler cmdlet'ini olarak tanımlayan parametre özniteliği tarafından döndürülen .NET Framework türlerini belirtir OutputType özniteliğini cmdlet'i bir sınıf olarak bir Microsoft .NET Framework sınıfı tanımlayan cmdlet'i özniteliği içerir Parametreler ve daha fazlası.</span><span class="sxs-lookup"><span data-stu-id="c914b-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c914b-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c914b-105">In This Section</span></span>

<span data-ttu-id="c914b-106">[Cmdlet kod öznitelikleri](./attributes-in-cmdlet-code.md) cmdlet'i kodda özniteliklerini kullanmanın avantajı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c914b-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="c914b-107">[Öznitelik türlerini](./attribute-types.md) cmdlet'i sınıf donatmak farklı öznitelikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c914b-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="c914b-108">[Diğer ad özniteliği bildirimi](./alias-attribute-declaration.md) bir cmdlet parametresi adı için diğer adlar tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="c914b-109">[Cmdlet özniteliği bildirimi](./cmdlet-attribute-declaration.md) bir .NET Framework sınıfı bir cmdlet tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="c914b-110">[Kimlik bilgisi özniteliği bildirimi](./credential-attribute-declaration.md) giriş dize dönüştürme için destek eklemeyi açıklar bir [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) nesne.</span><span class="sxs-lookup"><span data-stu-id="c914b-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="c914b-111">[OutputType özniteliğini bildirimi](./outputtype-attribute-declaration.md) cmdlet'i tarafından döndürülen .NET Framework türlerini belirtmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="c914b-112">[Parametre özniteliği bildirimi](./parameter-attribute-declaration.md) bir cmdlet parametreleri tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="c914b-113">[ValidateCount özniteliği bildirimi](./validatecount-attribute-declaration.md) kaç tane bağımsız değişken için bir parametre izin tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="c914b-114">[ValidateLength özniteliği bildirimi](./validatelength-attribute-declaration.md) parametre bağımsız değişken uzunluğu (karakter cinsinden) tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="c914b-115">[ValidatePattern özniteliği bildirimi](./validatepattern-attribute-declaration.md) parametre bağımsız değişkeni için geçerli desenleri tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="c914b-116">[ValidateRange özniteliği bildirimi](./validaterange-attribute-declaration.md) parametre bağımsız değişkeni için geçerli aralık tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="c914b-117">[ValidateSet özniteliği bildirimi](./validateset-attribute-declaration.md) parametre bağımsız değişkeni için olası değerler tanımlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c914b-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="c914b-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c914b-118">Reference</span></span>

[<span data-ttu-id="c914b-119">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="c914b-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
