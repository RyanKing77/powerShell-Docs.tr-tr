---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078780"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7e597-103">MSFT_DSCLocalConfigurationManager sınıfının EnableDebugConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e597-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7e597-104">DSC kaynak hata ayıklamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7e597-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e597-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e597-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="7e597-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e597-106">Parameters</span></span>

<span data-ttu-id="7e597-107">*BreakAll* \[içinde\] kaynak betiği her satırında bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7e597-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="7e597-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="7e597-108">Return value</span></span>

<span data-ttu-id="7e597-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e597-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e597-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e597-110">Remarks</span></span>

<span data-ttu-id="7e597-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="7e597-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e597-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e597-112">Requirements</span></span>

<span data-ttu-id="7e597-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7e597-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7e597-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7e597-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7e597-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e597-115">See also</span></span>

[<span data-ttu-id="7e597-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7e597-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)