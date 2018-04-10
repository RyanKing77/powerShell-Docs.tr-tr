---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi
ms.openlocfilehash: 3fd7ae54eb3ae782156dc4619ee0b6905dfb1212
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4a707-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a707-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4a707-104">Doğrudan çağıran **almak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4a707-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="4a707-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a707-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="4a707-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a707-106">Parameters</span></span>
----------

<span data-ttu-id="4a707-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="4a707-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="4a707-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="4a707-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="4a707-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a707-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="4a707-110">Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4a707-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="4a707-111">*yapılandırmaları* \[çıkışı\] getirisi, katıştırılmış yapılandırmaları örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="4a707-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="4a707-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4a707-112">Return value</span></span>
------------

<span data-ttu-id="4a707-113">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a707-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a707-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a707-114">Remarks</span></span>

<span data-ttu-id="4a707-115">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4a707-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a707-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a707-116">Requirements</span></span>
------------
><span data-ttu-id="4a707-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4a707-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4a707-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a707-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4a707-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4a707-119">See also</span></span>


[<span data-ttu-id="4a707-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4a707-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)