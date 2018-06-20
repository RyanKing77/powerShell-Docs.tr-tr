---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi
ms.openlocfilehash: 30cbaa907d4dc3a921c9e5fe61ffddc5d61c2347
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187876"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2fd9c-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceGet yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fd9c-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2fd9c-104">Doğrudan çağıran **almak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2fd9c-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="2fd9c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fd9c-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="2fd9c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2fd9c-106">Parameters</span></span>
----------

<span data-ttu-id="2fd9c-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="2fd9c-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="2fd9c-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="2fd9c-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="2fd9c-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="2fd9c-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="2fd9c-110">Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2fd9c-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="2fd9c-111">*yapılandırmaları* \[çıkışı\] getirisi, katıştırılmış yapılandırmaları örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="2fd9c-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="2fd9c-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2fd9c-112">Return value</span></span>
------------

<span data-ttu-id="2fd9c-113">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fd9c-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fd9c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fd9c-114">Remarks</span></span>

<span data-ttu-id="2fd9c-115">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="2fd9c-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2fd9c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fd9c-116">Requirements</span></span>
------------
><span data-ttu-id="2fd9c-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2fd9c-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2fd9c-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2fd9c-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2fd9c-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2fd9c-119">See also</span></span>


[<span data-ttu-id="2fd9c-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2fd9c-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)