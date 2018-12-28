---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405683"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e22cb-103">MSFT_DSCLocalConfigurationManager sınıfının PerformRequiredConfigurationChecks yöntemi</span><span class="sxs-lookup"><span data-stu-id="e22cb-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e22cb-104">Görev Zamanlayıcısı'nı kullanarak bir tutarlılık denetimi başlatır.</span><span class="sxs-lookup"><span data-stu-id="e22cb-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="e22cb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e22cb-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="e22cb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e22cb-106">Parameters</span></span>

<span data-ttu-id="e22cb-107">*Bayrakları* \[içinde\] çalıştırmak için tutarlılık denetimi türünü belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="e22cb-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="e22cb-108">Aşağıdaki değerler geçerlidir ve bit düzeyinde kullanarak birleştirilebilir **veya** işlemi:</span><span class="sxs-lookup"><span data-stu-id="e22cb-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="e22cb-109">Değer</span><span class="sxs-lookup"><span data-stu-id="e22cb-109">Value</span></span> |<span data-ttu-id="e22cb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e22cb-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="e22cb-111">**1**</span><span class="sxs-lookup"><span data-stu-id="e22cb-111">**1**</span></span> | <span data-ttu-id="e22cb-112">Normal bir tutarlılık denetimi.</span><span class="sxs-lookup"><span data-stu-id="e22cb-112">A normal consistency check.</span></span> |
|<span data-ttu-id="e22cb-113">**2**</span><span class="sxs-lookup"><span data-stu-id="e22cb-113">**2**</span></span> | <span data-ttu-id="e22cb-114">Bir tutarlılık denetimi bir yeniden başlatma işleminden sonra devam etmesi.</span><span class="sxs-lookup"><span data-stu-id="e22cb-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="e22cb-115">Bu değer, diğer değerlerle birleştirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="e22cb-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="e22cb-116">**4**</span><span class="sxs-lookup"><span data-stu-id="e22cb-116">**4**</span></span> | <span data-ttu-id="e22cb-117">Çekme sunucusundan metaconfiguration düğümü için belirtilen yapılandırma çekilmesi.</span><span class="sxs-lookup"><span data-stu-id="e22cb-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="e22cb-118">Bu değer her zaman ile birleştirilmelidir **1**, değeri için **5**.</span><span class="sxs-lookup"><span data-stu-id="e22cb-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="e22cb-119">**8**</span><span class="sxs-lookup"><span data-stu-id="e22cb-119">**8**</span></span> | <span data-ttu-id="e22cb-120">Durum rapor sunucusuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="e22cb-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e22cb-121">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e22cb-121">Return value</span></span>

<span data-ttu-id="e22cb-122">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e22cb-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e22cb-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e22cb-123">Remarks</span></span>

<span data-ttu-id="e22cb-124">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="e22cb-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e22cb-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e22cb-125">Requirements</span></span>

<span data-ttu-id="e22cb-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e22cb-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e22cb-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e22cb-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e22cb-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="e22cb-128">See also</span></span>

[<span data-ttu-id="e22cb-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e22cb-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)