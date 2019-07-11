---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: PerformRequiredConfigurationChecks yöntemi
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734413"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="062c1-103">PerformRequiredConfigurationChecks yöntemi</span><span class="sxs-lookup"><span data-stu-id="062c1-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="062c1-104">Görev Zamanlayıcısı'nı kullanarak bir tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="062c1-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="062c1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="062c1-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="062c1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="062c1-106">Parameters</span></span>

<span data-ttu-id="062c1-107">*Bayrakları* \[içinde\] çalıştırmak için tutarlılık denetimi türünü belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="062c1-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="062c1-108">Aşağıdaki değerler geçerlidir ve bit düzeyinde kullanarak birleştirilebilir **veya** işlemi:</span><span class="sxs-lookup"><span data-stu-id="062c1-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="062c1-109">Değer</span><span class="sxs-lookup"><span data-stu-id="062c1-109">Value</span></span> |<span data-ttu-id="062c1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="062c1-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="062c1-111">**1**</span><span class="sxs-lookup"><span data-stu-id="062c1-111">**1**</span></span> | <span data-ttu-id="062c1-112">Normal bir tutarlılık denetimi.</span><span class="sxs-lookup"><span data-stu-id="062c1-112">A normal consistency check.</span></span> |
|<span data-ttu-id="062c1-113">**2**</span><span class="sxs-lookup"><span data-stu-id="062c1-113">**2**</span></span> | <span data-ttu-id="062c1-114">Bir tutarlılık denetimi bir yeniden başlatma işleminden sonra devam etmesi.</span><span class="sxs-lookup"><span data-stu-id="062c1-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="062c1-115">Bu değer, diğer değerlerle birleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="062c1-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="062c1-116">**4**</span><span class="sxs-lookup"><span data-stu-id="062c1-116">**4**</span></span> | <span data-ttu-id="062c1-117">Çekme sunucusundan metaconfiguration düğümü için belirtilen yapılandırma çekilmesi.</span><span class="sxs-lookup"><span data-stu-id="062c1-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="062c1-118">Bu değer her zaman ile birleştirilmelidir **1**, değeri için **5**.</span><span class="sxs-lookup"><span data-stu-id="062c1-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="062c1-119">**8**</span><span class="sxs-lookup"><span data-stu-id="062c1-119">**8**</span></span> | <span data-ttu-id="062c1-120">Durum rapor sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="062c1-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="062c1-121">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="062c1-121">Return value</span></span>

<span data-ttu-id="062c1-122">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="062c1-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="062c1-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="062c1-123">Remarks</span></span>

<span data-ttu-id="062c1-124">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="062c1-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="062c1-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="062c1-125">Requirements</span></span>

<span data-ttu-id="062c1-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="062c1-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="062c1-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="062c1-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="062c1-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="062c1-128">See also</span></span>

[<span data-ttu-id="062c1-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="062c1-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
