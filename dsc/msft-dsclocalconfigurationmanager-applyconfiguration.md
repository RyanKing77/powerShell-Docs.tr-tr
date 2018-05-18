---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2f827-103">MSFT_DSCLocalConfigurationManager sınıfının ApplyConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f827-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2f827-104">Bekleyen yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f827-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="2f827-105">Bekleyen yapılandırma yoksa, bu yöntem geçerli yapılandırmasını yeniden uygular.</span><span class="sxs-lookup"><span data-stu-id="2f827-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="2f827-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f827-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="2f827-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f827-107">Parameters</span></span>
----------

<span data-ttu-id="2f827-108">*zorla* \[içinde\] bu ise **doğru**, bekleyen bir yapılandırma olsa bile geçerli yapılandırmasını yeniden.</span><span class="sxs-lookup"><span data-stu-id="2f827-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="2f827-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2f827-109">Return value</span></span>
------------

<span data-ttu-id="2f827-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2f827-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f827-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f827-111">Remarks</span></span>

<span data-ttu-id="2f827-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="2f827-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f827-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f827-113">Requirements</span></span>
------------
><span data-ttu-id="2f827-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2f827-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2f827-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f827-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2f827-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2f827-116">See also</span></span>


[<span data-ttu-id="2f827-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2f827-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)