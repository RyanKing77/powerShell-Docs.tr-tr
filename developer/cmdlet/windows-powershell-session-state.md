---
title: Windows PowerShell oturum durumu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: 5d4effb508c9f2544832dad557671520cb0a7ac7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851705"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="13ee1-102">Windows PowerShell Oturum Durumu</span><span class="sxs-lookup"><span data-stu-id="13ee1-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="13ee1-103">Oturum durumu için Windows PowerShell oturumunda veya modül geçerli yapılandırmasını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="13ee1-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="13ee1-104">Bir Windows PowerShell oturumu etkileşimli komut satırı kullanıcı veya program aracılığıyla bir ana bilgisayar uygulaması tarafından kullanılan işlem ortamıdır.</span><span class="sxs-lookup"><span data-stu-id="13ee1-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="13ee1-105">Oturum durumu bir oturum için genel oturum durumuna adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="13ee1-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="13ee1-106">Geliştirici açısından bakıldığında, bir Windows PowerShell oturumu ana bilgisayar uygulamasına bir Windows PowerShell çalışma açıldığında ve çalışma kapattığı zaman arasındaki süreyi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="13ee1-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="13ee1-107">Başka bir şekilde baktığı, çalışma alanı bulunduğu sürece, çağrılan Windows PowerShell altyapısı örneği ömrünü oturumdur.</span><span class="sxs-lookup"><span data-stu-id="13ee1-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="13ee1-108">Modül oturum durumu</span><span class="sxs-lookup"><span data-stu-id="13ee1-108">Module Session State</span></span>

<span data-ttu-id="13ee1-109">Modül veya iç içe geçmiş kendi modüllerinin bir oturuma aktarılır her modül oturum durumları oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="13ee1-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="13ee1-110">Cmdlet'i, işlev veya betik gibi bir öğenin bir modül dışa aktardığında, oturumun genel oturum durumuna bu öğeye bir başvuru eklenir.</span><span class="sxs-lookup"><span data-stu-id="13ee1-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="13ee1-111">Ancak, öğe çalıştırdığınızda, oturum durumu modülü içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="13ee1-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="13ee1-112">Oturum durumu verileri</span><span class="sxs-lookup"><span data-stu-id="13ee1-112">Session-State Data</span></span>

<span data-ttu-id="13ee1-113">Oturum durumu verilerini, genel veya özel olabilir.</span><span class="sxs-lookup"><span data-stu-id="13ee1-113">Session state data can be public or private.</span></span> <span data-ttu-id="13ee1-114">Özel veriler yalnızca oturum durumu içinden kullanılabilir olduğu sürece genel veri oturum durumu dışından çağrılar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13ee1-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="13ee1-115">Örneğin, bir modül yalnızca modül veya yalnızca dahili olarak adlandırılan özel bir işlevi olabilir aktarılmış olan bir genel öğe.</span><span class="sxs-lookup"><span data-stu-id="13ee1-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="13ee1-116">Bu bir .NET Framework türü özel ve genel üyeleri benzer.</span><span class="sxs-lookup"><span data-stu-id="13ee1-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="13ee1-117">Oturum durumu verilerini, yürütme altyapısı geçerli Windows PowerShell oturumu bağlamında geçerli örneği tarafından depolanır.</span><span class="sxs-lookup"><span data-stu-id="13ee1-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="13ee1-118">Oturum durumu verileri şu öğelerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="13ee1-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="13ee1-119">Yol bilgileri</span><span class="sxs-lookup"><span data-stu-id="13ee1-119">Path information</span></span>

- <span data-ttu-id="13ee1-120">Sürücü bilgileri</span><span class="sxs-lookup"><span data-stu-id="13ee1-120">Drive information</span></span>

- <span data-ttu-id="13ee1-121">Windows PowerShell sağlayıcısı bilgileri</span><span class="sxs-lookup"><span data-stu-id="13ee1-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="13ee1-122">İçeri aktarılan modülleri ve modül tarafından dışarı aktarılan modül öğelere (örneğin, cmdlet'ler, İşlevler ve betikler) başvurular hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="13ee1-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="13ee1-123">Bu bilgiler ve bu başvuruları yalnızca genel oturum durumu için var.</span><span class="sxs-lookup"><span data-stu-id="13ee1-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="13ee1-124">Oturum durumu değişken bilgileri</span><span class="sxs-lookup"><span data-stu-id="13ee1-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="13ee1-125">Cmdlet'ler içinde oturum durumu verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="13ee1-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="13ee1-126">Cmdlet'leri erişebilir oturum durumu verilerini ya da dolaylı olarak ile [System.Management.Automation.Pscmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) özelliğini cmdlet'i sınıf veya doğrudan aracılığıyla [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="13ee1-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.Pscmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="13ee1-127">[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) sınıfı, farklı türde oturum durumu verileri araştırmak için kullanılan özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="13ee1-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="13ee1-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="13ee1-128">See Also</span></span>

[<span data-ttu-id="13ee1-129">System.Management.Automation.Pscmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="13ee1-129">System.Management.Automation.Pscmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="13ee1-130">System.Management.Automation.Sessionstate? Displayproperty tam adı =</span><span class="sxs-lookup"><span data-stu-id="13ee1-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="13ee1-131">Windows PowerShell cmdlet'leri</span><span class="sxs-lookup"><span data-stu-id="13ee1-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="13ee1-132">Bir Windows PowerShell cmdlet'i yazma</span><span class="sxs-lookup"><span data-stu-id="13ee1-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="13ee1-133">Windows PowerShell Kabuk SDK'sı</span><span class="sxs-lookup"><span data-stu-id="13ee1-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
