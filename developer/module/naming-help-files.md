---
title: Yardım dosyalarını adlandırma | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795360"
---
# <a name="naming-help-files"></a><span data-ttu-id="ea504-102">Yardım Dosyalarını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="ea504-102">Naming Help Files</span></span>

<span data-ttu-id="ea504-103">Bu konu başlığında, bir XML tabanlı Yardım dosyasını adlandırmak açıklanmaktadır böylece [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet'i, bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea504-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="ea504-104">Ad gereksinimleri, her komut türü için farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea504-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="ea504-105">Cmdlet Yardım dosyaları</span><span class="sxs-lookup"><span data-stu-id="ea504-105">Cmdlet Help Files</span></span>

<span data-ttu-id="ea504-106">İçin Yardım dosyasına bir C# cmdlet tanımlanır derleme için cmdlet adı.</span><span class="sxs-lookup"><span data-stu-id="ea504-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="ea504-107">Aşağıdaki dosya adı biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="ea504-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ea504-108">Derleme bir iç içe modül olsa bile, derleme adı biçimi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ea504-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ea504-109">Örneğin, [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet'i Microsoft.PowerShell.Diagnostics.dll derlemesinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ea504-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="ea504-110">`Get-Help` Cmdlet için Yardım konusunun arar `Get-WinEvent` cmdlet'i yalnızca modül dizinini Microsoft.PowerShell.Diagnostics.dll help.xml dosyasında.</span><span class="sxs-lookup"><span data-stu-id="ea504-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="ea504-111">Sağlayıcı Yardım dosyaları</span><span class="sxs-lookup"><span data-stu-id="ea504-111">Provider Help files</span></span>

<span data-ttu-id="ea504-112">Yardım dosyası bir Windows PowerShell sağlayıcısı için sağlayıcı tanımlandığı derleme için adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea504-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="ea504-113">Aşağıdaki dosya adı biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="ea504-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ea504-114">Derleme bir iç içe modül olsa bile, derleme adı biçimi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ea504-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ea504-115">Örneğin, sertifika sağlayıcısı Microsoft.PowerShell.Security.dll derlemede tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="ea504-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="ea504-116">`Get-Help` Cmdlet'i yalnızca modül dizinini Microsoft.PowerShell.Security.dll help.xml dosyasında sertifika sağlayıcısı için bir Yardım konusu arar.</span><span class="sxs-lookup"><span data-stu-id="ea504-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="ea504-117">Yardım dosyaları işlevi</span><span class="sxs-lookup"><span data-stu-id="ea504-117">Function Help Files</span></span>

<span data-ttu-id="ea504-118">İşlevleri kullanarak konusunda açıklanmaktadır [açıklama tabanlı Yardım](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) veya bir XML Yardım dosyasında belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ea504-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="ea504-119">İşlevi, bir XML dosyasında belirtildiği zaman, işlev olmalıdır bir `.ExternalHelp` işlevi olan XML dosyası ilişkilendirir anahtar sözcüğü açıklama satırı yapın.</span><span class="sxs-lookup"><span data-stu-id="ea504-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="ea504-120">Aksi takdirde, `Get-Help` cmdlet Yardım dosyasını bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="ea504-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="ea504-121">Bir işlev Yardım dosyasının adı için teknik gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ea504-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="ea504-122">Ancak, en iyi uygulama işlevi tanımlandığı betik modülü için Yardım dosyasına ad sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ea504-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="ea504-123">Örneğin, aşağıdaki işlev MyModule.psm1 dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ea504-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="ea504-124">CIM komut Yardım dosyaları</span><span class="sxs-lookup"><span data-stu-id="ea504-124">CIM Command Help Files</span></span>

<span data-ttu-id="ea504-125">CIM komut için Yardım dosyasına CIM komut tanımlandığı CDXML dosyayı adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea504-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="ea504-126">Aşağıdaki dosya adı biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="ea504-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="ea504-127">CIM komutları modülleri iç içe modül olarak yer alan CDXML dosyalarından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ea504-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="ea504-128">Windows PowerShell CIM komut işlevi olarak oturuma aktarıldığında ekler bir `.ExternalHelp` anahtar sözcüğü bir XML Yardım işlevi ilişkilendirir işlev tanımı için Dosya Açıklama CIM komut tanımlanır CDXML dosyayı adlı.</span><span class="sxs-lookup"><span data-stu-id="ea504-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="ea504-129">Betik iş akışı Yardım dosyaları</span><span class="sxs-lookup"><span data-stu-id="ea504-129">Script Workflow Help Files</span></span>

<span data-ttu-id="ea504-130">XML-tabanlı Yardım dosyaları belgelenmesi modüllerde yer alan komut dosyası iş akışları.</span><span class="sxs-lookup"><span data-stu-id="ea504-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="ea504-131">Yardım dosyasının adı için teknik gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ea504-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="ea504-132">Ancak, en iyi uygulama akışının tanımlandığı betik modülü için Yardım dosyasına ad sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ea504-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="ea504-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ea504-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="ea504-134">Diğer komut dosyalı komutlar, komut dosyası iş akışları gerektirmeyen bir `.ExternalHelp` anahtar sözcüğü, bir Yardım dosyası ile ilişkilendirilecek yorum.</span><span class="sxs-lookup"><span data-stu-id="ea504-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="ea504-135">Bunun yerine, Windows PowerShell modülü dizininin XML tabanlı Yardım dosyaları için kullanıcı Arabirimi kültüre özgü alt dizinleri arar ve Yardım iş akışı içindeki tüm dosyaları arar.</span><span class="sxs-lookup"><span data-stu-id="ea504-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="ea504-136">`.ExternalHelp` Açıklama anahtar sözcüğü göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="ea504-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="ea504-137">Çünkü `.ExternalHelp` açıklama anahtar sözcüğünü sayılır `Get-Help` cmdlet'i bulabilir Yardım iş akışları için Modüller yalnızca dahil olduğunda.</span><span class="sxs-lookup"><span data-stu-id="ea504-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>