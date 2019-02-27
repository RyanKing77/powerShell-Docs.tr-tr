---
title: Windows PowerShell cmdlet'i kavramları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846665"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="4c6d1-102">Windows PowerShell Cmdlet Kavramları</span><span class="sxs-lookup"><span data-stu-id="4c6d1-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="4c6d1-103">Bu bölümde, cmdlet'leri nasıl çalıştığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4c6d1-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4c6d1-104">In This Section</span></span>

<span data-ttu-id="4c6d1-105">Bu bölüm aşağıdaki konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-105">This section includes the following topics.</span></span>

<span data-ttu-id="4c6d1-106">[Cmdlet geliştirme yönergeleri](./cmdlet-development-guidelines.md) bu konuda, doğru biçimlendirilmiş cmdlet'leri üretmek için kullanılan geliştirme yönergeleri sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="4c6d1-107">[Cmdlet'i sınıf bildirimi](./cmdlet-class-declaration.md) cmdlet'i sınıf bildiriminin bu konuda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="4c6d1-108">[Windows PowerShell komutları için fiiller onaylanan](./approved-verbs-for-windows-powershell-commands.md) Bu konu, bir cmdlet sınıfı bildirdiğinizde kullanabileceğiniz önceden tanımlanmış cmdlet fiilleri listeler.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="4c6d1-109">[Cmdlet giriş işleme yöntemlerini](./cmdlet-input-processing-methods.md) Bu konu ön işleme işlemleri, işlemleri giriş ve sonrası işlemleri bir cmdlet'in yürütülmesinin yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="4c6d1-110">[Cmdlet parametrelerini](./cmdlet-parameters.md) Bu bölümde cmdlet'lerinde ekleyebileceğiniz parametreleri farklı türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="4c6d1-111">[Cmdlet öznitelikleri](./cmdlet-attributes.md) Bu bölümde alanları cmdlet parametreleri olarak bildirmek için ve parametreler için giriş doğrulama kuralları bildirmek için .NET Framework sınıfları cmdlet'leri bildirmek için kullanılan öznitelikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="4c6d1-112">[Cmdlet diğer adlar](./cmdlet-aliases.md) cmdlet diğer adları bu konuda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="4c6d1-113">[Cmdlet çıkışı](./cmdlet-output.md) türüne cmdlet'leri döndürebilir çıkış nasıl tanımlanacağını ve cmdlet'ler tarafından döndürülen nesneleri görüntülemek ve bu bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="4c6d1-114">[Cmdlet'leri kaydetme](./modules-and-snap-ins.md) Bu bölümde, cmdlet modülleri ve ek bileşenler kullanarak kaydetmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="4c6d1-115">[Onay isteme](./requesting-confirmation-from-cmdlets.md) sistemde bir değişiklik yapmadan cmdlet bir kullanıcıdan onay nasıl istek bu bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="4c6d1-116">[Windows PowerShell, hata raporlama](./error-reporting-concepts.md) cmdlet'leri hataları sonlandıran ve sonlandırıcı olmayan hatalara nasıl rapor bu bölümde açıklanmaktadır ve hata kaydı yorumlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="4c6d1-117">[Arka plan işleri](./background-jobs.md) bu konuda cmdlet'leri geçerli oturumdaki yürütme komutlarla müdahale etmez arka plan işleri içinde işlerini nasıl gerçekleştirebileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="4c6d1-118">[Cmdlet'leri ve betikleri içinde bir Cmdlet yürütmesini](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) nasıl cmdlet'leri diğer cmdlet'leri ve betikleri içinden yöntemleri işleme kendi girişlerini çağırabilirsiniz bu konuda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="4c6d1-119">[Cmdlet'i ayarlar](./cmdlet-sets.md) cmdlet'leri kümesi oluşturmak için temel sınıfları kullanarak bu konuda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="4c6d1-120">[Windows PowerShell oturum durumu](./windows-powershell-session-state.md) Bu konu, Windows PowerShell oturum durumunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="4c6d1-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
