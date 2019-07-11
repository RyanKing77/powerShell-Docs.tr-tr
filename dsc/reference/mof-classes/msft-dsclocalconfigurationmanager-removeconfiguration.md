---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: RemoveConfiguration yöntemi
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734393"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="4131c-103">RemoveConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="4131c-103">RemoveConfiguration method</span></span>

<span data-ttu-id="4131c-104">Yapılandırma dosyaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4131c-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="4131c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4131c-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="4131c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4131c-106">Parameters</span></span>

<span data-ttu-id="4131c-107">*Aşama* \[içinde\] kaldırmak için hangi yapılandırma belgesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4131c-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="4131c-108">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="4131c-108">The following values are valid:</span></span>

|<span data-ttu-id="4131c-109">Değer</span><span class="sxs-lookup"><span data-stu-id="4131c-109">Value</span></span> |<span data-ttu-id="4131c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4131c-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="4131c-111">**1**</span><span class="sxs-lookup"><span data-stu-id="4131c-111">**1**</span></span> | <span data-ttu-id="4131c-112">**Geçerli** yapılandırma belgesi (current.mof).</span><span class="sxs-lookup"><span data-stu-id="4131c-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="4131c-113">**2**</span><span class="sxs-lookup"><span data-stu-id="4131c-113">**2**</span></span> | <span data-ttu-id="4131c-114">**Bekleyen** yapılandırma belgesi (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="4131c-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="4131c-115">**4**</span><span class="sxs-lookup"><span data-stu-id="4131c-115">**4**</span></span> | <span data-ttu-id="4131c-116">**Önceki** yapılandırma belgesi (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="4131c-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="4131c-117">*Zorla* \[içinde\] **true** yapılandırma kaldırılmasını zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="4131c-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4131c-118">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4131c-118">Return value</span></span>

<span data-ttu-id="4131c-119">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4131c-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4131c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4131c-120">Remarks</span></span>

<span data-ttu-id="4131c-121">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="4131c-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4131c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4131c-122">Requirements</span></span>

<span data-ttu-id="4131c-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4131c-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4131c-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4131c-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4131c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4131c-125">See also</span></span>

[<span data-ttu-id="4131c-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4131c-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
