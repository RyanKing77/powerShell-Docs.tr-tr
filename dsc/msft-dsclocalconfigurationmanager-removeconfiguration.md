---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892693"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="979a0-103">MSFT_DSCLocalConfigurationManager sınıfının RemoveConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="979a0-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="979a0-104">Yapılandırma dosyaları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="979a0-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="979a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="979a0-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="979a0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="979a0-106">Parameters</span></span>

<span data-ttu-id="979a0-107">*Aşama* \[içinde\] kaldırmak için hangi yapılandırma belgesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="979a0-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="979a0-108">Aşağıdaki değerler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="979a0-108">The following values are valid:</span></span>

|<span data-ttu-id="979a0-109">Değer</span><span class="sxs-lookup"><span data-stu-id="979a0-109">Value</span></span> |<span data-ttu-id="979a0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="979a0-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="979a0-111">**1**</span><span class="sxs-lookup"><span data-stu-id="979a0-111">**1**</span></span> | <span data-ttu-id="979a0-112">**Geçerli** yapılandırma belgesi (current.mof).</span><span class="sxs-lookup"><span data-stu-id="979a0-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="979a0-113">**2**</span><span class="sxs-lookup"><span data-stu-id="979a0-113">**2**</span></span> | <span data-ttu-id="979a0-114">**Bekleyen** yapılandırma belgesi (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="979a0-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="979a0-115">**4**</span><span class="sxs-lookup"><span data-stu-id="979a0-115">**4**</span></span> | <span data-ttu-id="979a0-116">**Önceki** yapılandırma belgesi (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="979a0-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="979a0-117">*Zorla* \[içinde\] **true** yapılandırma kaldırılmasını zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="979a0-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="979a0-118">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="979a0-118">Return value</span></span>

<span data-ttu-id="979a0-119">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="979a0-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="979a0-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="979a0-120">Remarks</span></span>

<span data-ttu-id="979a0-121">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="979a0-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="979a0-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="979a0-122">Requirements</span></span>

<span data-ttu-id="979a0-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="979a0-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="979a0-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="979a0-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="979a0-125">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="979a0-125">See also</span></span>

[<span data-ttu-id="979a0-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="979a0-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)