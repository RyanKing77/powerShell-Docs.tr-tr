---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC WindowsOptionalFeatureSet kaynağı"
ms.openlocfilehash: 3bf6a993d0ec9ce71c1e9222ddaa3bb429accb15
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="993f5-103">DSC WindowsOptionalFeatureSet kaynağı</span><span class="sxs-lookup"><span data-stu-id="993f5-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="993f5-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="993f5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="993f5-105">**WindowsOptionalFeatureSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), isteğe bağlı özellikler hedef düğümde etkin olduğundan emin olmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="993f5-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="993f5-106">Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [WindowsOptionalFeature kaynak](windowsOptionalFeatureResource.md) belirtilen her bir özelliğin `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="993f5-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="993f5-107">Çok sayıda Windows isteğe bağlı özelliği aynı duruma yapılandırmak istediğinizde bu kaynağı kullanın.</span><span class="sxs-lookup"><span data-stu-id="993f5-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="993f5-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="993f5-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="993f5-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="993f5-109">Properties</span></span>

|  <span data-ttu-id="993f5-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="993f5-110">Property</span></span>  |  <span data-ttu-id="993f5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="993f5-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="993f5-112">Ad</span><span class="sxs-lookup"><span data-stu-id="993f5-112">Name</span></span>| <span data-ttu-id="993f5-113">Sağlamak istediğiniz özellikleri adını etkin veya devre dışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="993f5-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>| 
| <span data-ttu-id="993f5-114">Emin olun</span><span class="sxs-lookup"><span data-stu-id="993f5-114">Ensure</span></span>| <span data-ttu-id="993f5-115">Özelliklerin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="993f5-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="993f5-116">Özellikleri olduğundan emin olmak için etkinleştirilmişse, ayarlanmış "Etkinleştir" özellikleri devre dışı olduğunu, emin olmak için bu özelliği ayarlayın "Devre dışı bırak" özelliğine.</span><span class="sxs-lookup"><span data-stu-id="993f5-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="993f5-117">Kaynak</span><span class="sxs-lookup"><span data-stu-id="993f5-117">Source</span></span>| <span data-ttu-id="993f5-118">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="993f5-118">Not implemented.</span></span>|
| <span data-ttu-id="993f5-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="993f5-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="993f5-120">DISM Windows Update (WU) özelliklerini etkinleştirmek kaynak dosyalarını ararken kişiler olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="993f5-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="993f5-121">$True, DISM WU başvurun değil.</span><span class="sxs-lookup"><span data-stu-id="993f5-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="993f5-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="993f5-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="993f5-123">Kümesine **$true** bunlar devre dışı bırakıldığında özelliklerle ilişkili tüm dosyaları kaldırmak için (diğer bir deyişle, zaman **emin olun** ayarlanır "Yok" için).</span><span class="sxs-lookup"><span data-stu-id="993f5-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="993f5-124">GünlükDüzeyi</span><span class="sxs-lookup"><span data-stu-id="993f5-124">LogLevel</span></span>| <span data-ttu-id="993f5-125">Günlüklerde gösterilen maksimum çıktı düzeyini.</span><span class="sxs-lookup"><span data-stu-id="993f5-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="993f5-126">Kabul edilen değerler şunlardır: "(yalnızca hatalar kaydedilir) ErrorsOnly", "ErrorsAndWarning" (hatalar ve uyarılar günlüğe kaydedilir) ve "ErrorsAndWarningAndInformation" (hatalar, uyarılar ve hata ayıklama bilgileri kaydedilir).</span><span class="sxs-lookup"><span data-stu-id="993f5-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="993f5-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="993f5-127">LogPath</span></span>| <span data-ttu-id="993f5-128">Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="993f5-128">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="993f5-129">dependsOn</span><span class="sxs-lookup"><span data-stu-id="993f5-129">DependsOn</span></span>| <span data-ttu-id="993f5-130">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="993f5-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="993f5-131">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="993f5-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



