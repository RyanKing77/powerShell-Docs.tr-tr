---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi"
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="23389-103">MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi</span><span class="sxs-lookup"><span data-stu-id="23389-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="23389-104">Görev Zamanlayıcısı'nı kullanarak bir tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="23389-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="23389-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23389-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="23389-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23389-106">Parameters</span></span>
----------

<span data-ttu-id="23389-107">*Bayrakları* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="23389-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="23389-108">Tutarlılık denetimi Çalıştır türünü belirtir. bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="23389-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="23389-109">Aşağıdaki değerler geçerlidir ve bit kullanılarak birleştirilebilir **veya** işlemi:</span><span class="sxs-lookup"><span data-stu-id="23389-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="23389-110">Değer</span><span class="sxs-lookup"><span data-stu-id="23389-110">Value</span></span> |<span data-ttu-id="23389-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23389-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="23389-112">**1**</span><span class="sxs-lookup"><span data-stu-id="23389-112">**1**</span></span> | <span data-ttu-id="23389-113">Normal tutarlılık denetimi.</span><span class="sxs-lookup"><span data-stu-id="23389-113">A normal consistency check.</span></span> |
|<span data-ttu-id="23389-114">**2**</span><span class="sxs-lookup"><span data-stu-id="23389-114">**2**</span></span> | <span data-ttu-id="23389-115">Tutarlılık denetimi devamlılık bir yeniden başlatma işleminden sonra.</span><span class="sxs-lookup"><span data-stu-id="23389-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="23389-116">Bu değer diğer değerlerle birleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="23389-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="23389-117">**4**</span><span class="sxs-lookup"><span data-stu-id="23389-117">**4**</span></span> | <span data-ttu-id="23389-118">Yapılandırma meta yapılandırmasını düğümü için belirtilen çekme sunucusundan çekilen.</span><span class="sxs-lookup"><span data-stu-id="23389-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="23389-119">Bu değer her zaman ile birleştirilmelidir **1**, değeri için **5**.</span><span class="sxs-lookup"><span data-stu-id="23389-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="23389-120">**8**</span><span class="sxs-lookup"><span data-stu-id="23389-120">**8**</span></span> | <span data-ttu-id="23389-121">Durum rapor sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="23389-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="23389-122">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="23389-122">Return value</span></span>
------------

<span data-ttu-id="23389-123">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="23389-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="23389-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23389-124">Remarks</span></span>

<span data-ttu-id="23389-125">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="23389-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="23389-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23389-126">Requirements</span></span>
------------
><span data-ttu-id="23389-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="23389-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="23389-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="23389-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="23389-129">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="23389-129">See also</span></span>


[<span data-ttu-id="23389-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="23389-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



