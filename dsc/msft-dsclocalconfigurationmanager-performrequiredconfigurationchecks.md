---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186703"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4007a-103">MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi</span><span class="sxs-lookup"><span data-stu-id="4007a-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4007a-104">Görev Zamanlayıcısı'nı kullanarak bir tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="4007a-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="4007a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4007a-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="4007a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4007a-106">Parameters</span></span>
----------

<span data-ttu-id="4007a-107">*Bayrakları* \[içinde\] çalıştırmak için tutarlılık denetimi türünü belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="4007a-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="4007a-108">Aşağıdaki değerler geçerlidir ve bit kullanılarak birleştirilebilir **veya** işlemi:</span><span class="sxs-lookup"><span data-stu-id="4007a-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="4007a-109">Değer</span><span class="sxs-lookup"><span data-stu-id="4007a-109">Value</span></span> |<span data-ttu-id="4007a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4007a-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="4007a-111">**1**</span><span class="sxs-lookup"><span data-stu-id="4007a-111">**1**</span></span> | <span data-ttu-id="4007a-112">Normal tutarlılık denetimi.</span><span class="sxs-lookup"><span data-stu-id="4007a-112">A normal consistency check.</span></span> |
|<span data-ttu-id="4007a-113">**2**</span><span class="sxs-lookup"><span data-stu-id="4007a-113">**2**</span></span> | <span data-ttu-id="4007a-114">Tutarlılık denetimi devamlılık bir yeniden başlatma işleminden sonra.</span><span class="sxs-lookup"><span data-stu-id="4007a-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="4007a-115">Bu değer diğer değerlerle birleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="4007a-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="4007a-116">**4**</span><span class="sxs-lookup"><span data-stu-id="4007a-116">**4**</span></span> | <span data-ttu-id="4007a-117">Yapılandırma meta yapılandırmasını düğümü için belirtilen çekme sunucusundan çekilen.</span><span class="sxs-lookup"><span data-stu-id="4007a-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="4007a-118">Bu değer her zaman ile birleştirilmelidir **1**, değeri için **5**.</span><span class="sxs-lookup"><span data-stu-id="4007a-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="4007a-119">**8**</span><span class="sxs-lookup"><span data-stu-id="4007a-119">**8**</span></span> | <span data-ttu-id="4007a-120">Durum rapor sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="4007a-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="4007a-121">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4007a-121">Return value</span></span>
------------

<span data-ttu-id="4007a-122">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4007a-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4007a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4007a-123">Remarks</span></span>

<span data-ttu-id="4007a-124">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4007a-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4007a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4007a-125">Requirements</span></span>
------------
><span data-ttu-id="4007a-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4007a-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4007a-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4007a-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4007a-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4007a-128">See also</span></span>


[<span data-ttu-id="4007a-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4007a-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)