---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405704"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cad1b-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi</span><span class="sxs-lookup"><span data-stu-id="cad1b-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cad1b-104">Doğrudan çağıran **alma** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cad1b-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="cad1b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cad1b-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="cad1b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cad1b-106">Parameters</span></span>

<span data-ttu-id="cad1b-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="cad1b-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="cad1b-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.</span><span class="sxs-lookup"><span data-stu-id="cad1b-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="cad1b-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="cad1b-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="cad1b-110">Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.</span><span class="sxs-lookup"><span data-stu-id="cad1b-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="cad1b-111">*yapılandırmaları* \[kullanıma\] getirisi, yapılandırmaları katıştırılmış bir örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="cad1b-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="cad1b-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="cad1b-112">Return value</span></span>

<span data-ttu-id="cad1b-113">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="cad1b-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cad1b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cad1b-114">Remarks</span></span>

<span data-ttu-id="cad1b-115">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="cad1b-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cad1b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cad1b-116">Requirements</span></span>

<span data-ttu-id="cad1b-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cad1b-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cad1b-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cad1b-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cad1b-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="cad1b-119">See also</span></span>

[<span data-ttu-id="cad1b-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cad1b-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)