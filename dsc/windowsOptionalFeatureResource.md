---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC WindowsOptionalFeature kaynağı
ms.openlocfilehash: 1866bc9cd2194a62de23eaabee8a9c5049a84946
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="8e6ad-103">DSC WindowsOptionalFeature kaynağı</span><span class="sxs-lookup"><span data-stu-id="8e6ad-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="8e6ad-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8e6ad-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8e6ad-105">**WindowsOptionalFeature** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), isteğe bağlı özellikler hedef düğümde etkin olduğundan emin olmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e6ad-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e6ad-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="8e6ad-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8e6ad-107">Properties</span></span>

|  <span data-ttu-id="8e6ad-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="8e6ad-108">Property</span></span>  |  <span data-ttu-id="8e6ad-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e6ad-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="8e6ad-110">Ad</span><span class="sxs-lookup"><span data-stu-id="8e6ad-110">Name</span></span>| <span data-ttu-id="8e6ad-111">Sağlamak istediğiniz özelliğin adını etkin veya devre dışı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="8e6ad-112">Emin olun</span><span class="sxs-lookup"><span data-stu-id="8e6ad-112">Ensure</span></span>| <span data-ttu-id="8e6ad-113">Özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="8e6ad-114">Özellik olduğundan emin olmak için etkinleştirilmişse, Ayarla "Etkinleştir" özelliğini devre dışı bırakıldığından, emin olmak için bu özelliği ayarlayın "Devre dışı bırak" özelliğine.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="8e6ad-115">Kaynak</span><span class="sxs-lookup"><span data-stu-id="8e6ad-115">Source</span></span>| <span data-ttu-id="8e6ad-116">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-116">Not implemented.</span></span>|
| <span data-ttu-id="8e6ad-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="8e6ad-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="8e6ad-118">DISM Windows Update (WU) bir özelliği etkinleştirmek kaynak dosyalarını ararken kişiler olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="8e6ad-119">$True, DISM WU başvurun değil.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="8e6ad-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="8e6ad-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="8e6ad-121">Kümesine **$true** devre dışı olduğunda özelliği ile ilişkilendirilen tüm dosyaları kaldırmak için (diğer bir deyişle, zaman **emin olun** ayarlanır "Yok" için).</span><span class="sxs-lookup"><span data-stu-id="8e6ad-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="8e6ad-122">GünlükDüzeyi</span><span class="sxs-lookup"><span data-stu-id="8e6ad-122">LogLevel</span></span>| <span data-ttu-id="8e6ad-123">Günlüklerde gösterilen maksimum çıktı düzeyini.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="8e6ad-124">Kabul edilen değerler şunlardır: "(yalnızca hatalar kaydedilir) ErrorsOnly", "ErrorsAndWarning" (hatalar ve uyarılar günlüğe kaydedilir) ve "ErrorsAndWarningAndInformation" (hatalar, uyarılar ve hata ayıklama bilgileri kaydedilir).</span><span class="sxs-lookup"><span data-stu-id="8e6ad-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="8e6ad-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="8e6ad-125">LogPath</span></span>| <span data-ttu-id="8e6ad-126">Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="8e6ad-127">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8e6ad-127">DependsOn</span></span>| <span data-ttu-id="8e6ad-128">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8e6ad-129">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|