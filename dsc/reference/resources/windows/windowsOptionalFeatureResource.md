---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC WindowsOptionalFeature kaynağı
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048696"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="320b5-103">DSC WindowsOptionalFeature kaynağı</span><span class="sxs-lookup"><span data-stu-id="320b5-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="320b5-104">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="320b5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="320b5-105">**WindowsOptionalFeature** kaynak olarak Windows PowerShell Desired State Configuration (DSC), isteğe bağlı özellikler hedef düğümde etkinleştirildiğinden emin olmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="320b5-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="320b5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="320b5-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="320b5-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="320b5-107">Properties</span></span>

|  <span data-ttu-id="320b5-108">Özellik</span><span class="sxs-lookup"><span data-stu-id="320b5-108">Property</span></span>  |  <span data-ttu-id="320b5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="320b5-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="320b5-110">Ad</span><span class="sxs-lookup"><span data-stu-id="320b5-110">Name</span></span>| <span data-ttu-id="320b5-111">Sağlamak istediğiniz özelliğin adını etkin veya devre dışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="320b5-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="320b5-112">Emin olun</span><span class="sxs-lookup"><span data-stu-id="320b5-112">Ensure</span></span>| <span data-ttu-id="320b5-113">Özelliğin etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="320b5-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="320b5-114">Özelliği olduğundan emin olmak için etkin olarak ayarlayın "Etkinleştir" özellik devre dışıdır emin olmak için bu özelliği ayarlayın "Devre dışı bırak" özelliğini.</span><span class="sxs-lookup"><span data-stu-id="320b5-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="320b5-115">Kaynak</span><span class="sxs-lookup"><span data-stu-id="320b5-115">Source</span></span>| <span data-ttu-id="320b5-116">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="320b5-116">Not implemented.</span></span>|
| <span data-ttu-id="320b5-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="320b5-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="320b5-118">DISM'nin Windows Update (WU) bir özelliği etkinleştirmek kaynak dosyalarının aranacağı kişiler olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="320b5-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="320b5-119">$True, DISM WU sizinle iletişime değil.</span><span class="sxs-lookup"><span data-stu-id="320b5-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="320b5-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="320b5-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="320b5-121">Kümesine **$true** devre dışı olduğunda özellikle ilişkilendirilen tüm dosyaları kaldırmak için (diğer bir deyişle, zaman **emin olun** ayarlanır için "Yok").</span><span class="sxs-lookup"><span data-stu-id="320b5-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="320b5-122">GünlükDüzeyi</span><span class="sxs-lookup"><span data-stu-id="320b5-122">LogLevel</span></span>| <span data-ttu-id="320b5-123">Günlüklerde gösterilen maksimum çıktı düzeyini.</span><span class="sxs-lookup"><span data-stu-id="320b5-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="320b5-124">Kabul edilen değerler şunlardır: "(Yalnızca hatalar kaydedilir) ErrorsOnly", "ErrorsAndWarning" (hatalar ve uyarılar günlüğe kaydedilir) ve "ErrorsAndWarningAndInformation" (hataları, uyarıları ve hata ayıklama bilgileri kaydedilir).</span><span class="sxs-lookup"><span data-stu-id="320b5-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="320b5-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="320b5-125">LogPath</span></span>| <span data-ttu-id="320b5-126">Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="320b5-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="320b5-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="320b5-127">DependsOn</span></span>| <span data-ttu-id="320b5-128">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="320b5-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="320b5-129">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise __ResourceName__ ve kendi türünün __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="320b5-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|