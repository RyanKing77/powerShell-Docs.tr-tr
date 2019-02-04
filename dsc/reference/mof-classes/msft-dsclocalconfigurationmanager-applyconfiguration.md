---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683915"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a4a62-103">MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4a62-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a4a62-104">Yapılandırma Aracı, bekleyen yapılandırmayı uygulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4a62-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="a4a62-105">Bekleyen herhangi bir yapılandırma varsa, bu yöntem geçerli yapılandırmasını yeniden uygular.</span><span class="sxs-lookup"><span data-stu-id="a4a62-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4a62-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4a62-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="a4a62-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4a62-107">Parameters</span></span>

<span data-ttu-id="a4a62-108">*zorla* \[içinde\] buysa **true**, bekleyen bir yapılandırma olsa bile geçerli yapılandırmasını yeniden uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a4a62-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="a4a62-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a4a62-109">Return value</span></span>

<span data-ttu-id="a4a62-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4a62-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a4a62-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4a62-111">Remarks</span></span>

<span data-ttu-id="a4a62-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="a4a62-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4a62-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4a62-113">Requirements</span></span>

<span data-ttu-id="a4a62-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a4a62-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a4a62-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a4a62-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a4a62-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4a62-116">See also</span></span>

[<span data-ttu-id="a4a62-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a4a62-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)