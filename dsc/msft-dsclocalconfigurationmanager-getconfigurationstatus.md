---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi
ms.openlocfilehash: dde4ac003b346018561481e05ca7374475f9ff1d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d91e8-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="d91e8-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d91e8-104">Yapılandırma durumu geçmişi alın.</span><span class="sxs-lookup"><span data-stu-id="d91e8-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="d91e8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d91e8-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="d91e8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d91e8-106">Parameters</span></span>
----------

<span data-ttu-id="d91e8-107">*Tüm* \[içinde\] **true** bu yöntem tüm ilgili bilgileri yapılandırma çalıştıran makinede döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="d91e8-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="d91e8-108">*configurationStatus* \[çıkışı\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="d91e8-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d91e8-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d91e8-109">Return value</span></span>
------------

<span data-ttu-id="d91e8-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d91e8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d91e8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d91e8-111">Remarks</span></span>

<span data-ttu-id="d91e8-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="d91e8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d91e8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d91e8-113">Requirements</span></span>
------------
><span data-ttu-id="d91e8-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d91e8-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d91e8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d91e8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d91e8-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d91e8-116">See also</span></span>


[<span data-ttu-id="d91e8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d91e8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)