---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC WindowsOptionalFeatureSet kaynağı
ms.openlocfilehash: 7c5eb553b396776f54a36bec8971f71ec61f9354
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187666"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="47d78-103">DSC WindowsOptionalFeatureSet kaynağı</span><span class="sxs-lookup"><span data-stu-id="47d78-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="47d78-104">İçin geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="47d78-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="47d78-105">**WindowsOptionalFeatureSet** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), isteğe bağlı özellikler hedef düğümde etkin olduğundan emin olmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="47d78-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="47d78-106">Bu kaynak olmadığı bir [bileşik kaynak](authoringResourceComposite.md) çağrısı [WindowsOptionalFeature kaynak](windowsOptionalFeatureResource.md) belirtilen her bir özelliğin `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="47d78-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="47d78-107">Çok sayıda Windows isteğe bağlı özelliği aynı duruma yapılandırmak istediğinizde bu kaynağı kullanın.</span><span class="sxs-lookup"><span data-stu-id="47d78-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="47d78-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47d78-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="47d78-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="47d78-109">Properties</span></span>

|  <span data-ttu-id="47d78-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="47d78-110">Property</span></span>  |  <span data-ttu-id="47d78-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47d78-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="47d78-112">Ad</span><span class="sxs-lookup"><span data-stu-id="47d78-112">Name</span></span>| <span data-ttu-id="47d78-113">Sağlamak istediğiniz özellikleri adını etkin veya devre dışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="47d78-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="47d78-114">Emin olun</span><span class="sxs-lookup"><span data-stu-id="47d78-114">Ensure</span></span>| <span data-ttu-id="47d78-115">Özelliklerin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47d78-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="47d78-116">Özellikleri olduğundan emin olmak için etkinleştirilmişse, ayarlanmış "Etkinleştir" özellikleri devre dışı olduğunu, emin olmak için bu özelliği ayarlayın "Devre dışı bırak" özelliğine.</span><span class="sxs-lookup"><span data-stu-id="47d78-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="47d78-117">Kaynak</span><span class="sxs-lookup"><span data-stu-id="47d78-117">Source</span></span>| <span data-ttu-id="47d78-118">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="47d78-118">Not implemented.</span></span>|
| <span data-ttu-id="47d78-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="47d78-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="47d78-120">DISM Windows Update (WU) özelliklerini etkinleştirmek kaynak dosyalarını ararken kişiler olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="47d78-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="47d78-121">$True, DISM WU başvurun değil.</span><span class="sxs-lookup"><span data-stu-id="47d78-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="47d78-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="47d78-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="47d78-123">Kümesine **$true** bunlar devre dışı bırakıldığında özelliklerle ilişkili tüm dosyaları kaldırmak için (diğer bir deyişle, zaman **emin olun** ayarlanır "Yok" için).</span><span class="sxs-lookup"><span data-stu-id="47d78-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="47d78-124">GünlükDüzeyi</span><span class="sxs-lookup"><span data-stu-id="47d78-124">LogLevel</span></span>| <span data-ttu-id="47d78-125">Günlüklerde gösterilen maksimum çıktı düzeyini.</span><span class="sxs-lookup"><span data-stu-id="47d78-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="47d78-126">Kabul edilen değerler şunlardır: "(yalnızca hatalar kaydedilir) ErrorsOnly", "ErrorsAndWarning" (hatalar ve uyarılar günlüğe kaydedilir) ve "ErrorsAndWarningAndInformation" (hatalar, uyarılar ve hata ayıklama bilgileri kaydedilir).</span><span class="sxs-lookup"><span data-stu-id="47d78-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="47d78-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="47d78-127">LogPath</span></span>| <span data-ttu-id="47d78-128">Kaynak sağlayıcısı işlemi oturum istediğiniz bir günlük dosyası yolu.</span><span class="sxs-lookup"><span data-stu-id="47d78-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="47d78-129">dependsOn</span><span class="sxs-lookup"><span data-stu-id="47d78-129">DependsOn</span></span>| <span data-ttu-id="47d78-130">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="47d78-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="47d78-131">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise __ResourceName__ ve türünü __ResourceType__, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="47d78-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|