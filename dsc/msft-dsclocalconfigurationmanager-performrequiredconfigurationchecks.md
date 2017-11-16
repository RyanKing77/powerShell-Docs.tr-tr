---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e9288-103">MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9288-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e9288-104">Görev Zamanlayıcısı'nı kullanarak bir tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="e9288-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="e9288-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9288-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="e9288-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9288-106">Parameters</span></span>
----------

<span data-ttu-id="e9288-107">*Bayrakları* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="e9288-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="e9288-108">Tutarlılık denetimi Çalıştır türünü belirtir. bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="e9288-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="e9288-109">Aşağıdaki değerler geçerlidir ve bit kullanılarak birleştirilebilir **veya** işlemi:</span><span class="sxs-lookup"><span data-stu-id="e9288-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="e9288-110">Değer</span><span class="sxs-lookup"><span data-stu-id="e9288-110">Value</span></span> |<span data-ttu-id="e9288-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9288-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="e9288-112">**1**</span><span class="sxs-lookup"><span data-stu-id="e9288-112">**1**</span></span> | <span data-ttu-id="e9288-113">Normal tutarlılık denetimi.</span><span class="sxs-lookup"><span data-stu-id="e9288-113">A normal consistency check.</span></span> |
|<span data-ttu-id="e9288-114">**2**</span><span class="sxs-lookup"><span data-stu-id="e9288-114">**2**</span></span> | <span data-ttu-id="e9288-115">Tutarlılık denetimi devamlılık bir yeniden başlatma işleminden sonra.</span><span class="sxs-lookup"><span data-stu-id="e9288-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="e9288-116">Bu değer diğer değerlerle birleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="e9288-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="e9288-117">**4**</span><span class="sxs-lookup"><span data-stu-id="e9288-117">**4**</span></span> | <span data-ttu-id="e9288-118">Yapılandırma meta yapılandırmasını düğümü için belirtilen çekme sunucusundan çekilen.</span><span class="sxs-lookup"><span data-stu-id="e9288-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="e9288-119">Bu değer her zaman ile birleştirilmelidir **1**, değeri için **5**.</span><span class="sxs-lookup"><span data-stu-id="e9288-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="e9288-120">**8**</span><span class="sxs-lookup"><span data-stu-id="e9288-120">**8**</span></span> | <span data-ttu-id="e9288-121">Durum rapor sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="e9288-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e9288-122">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e9288-122">Return value</span></span>
------------

<span data-ttu-id="e9288-123">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9288-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9288-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9288-124">Remarks</span></span>

<span data-ttu-id="e9288-125">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="e9288-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e9288-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9288-126">Requirements</span></span>
------------
><span data-ttu-id="e9288-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e9288-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e9288-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9288-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e9288-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e9288-129">See also</span></span>


[<span data-ttu-id="e9288-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e9288-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



