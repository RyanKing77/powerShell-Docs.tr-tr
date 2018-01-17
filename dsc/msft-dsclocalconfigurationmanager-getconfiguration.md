---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi"
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="252b8-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="252b8-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="252b8-104">Yapılandırma belgesini yönetilen düğüme gönderir ve kullandığı **almak** yapılandırmayı uygulamak için yapılandırma Aracısı'nın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="252b8-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="252b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="252b8-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="252b8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="252b8-106">Parameters</span></span>
----------

<span data-ttu-id="252b8-107">*configurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="252b8-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="252b8-108">Göndermek için yapılandırma verilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="252b8-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="252b8-109">*yapılandırmaları* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="252b8-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="252b8-110">Getirisi, katıştırılmış yapılandırmaları örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="252b8-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="252b8-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="252b8-111">Return value</span></span>
------------

<span data-ttu-id="252b8-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="252b8-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="252b8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="252b8-113">Remarks</span></span>

<span data-ttu-id="252b8-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="252b8-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="252b8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="252b8-115">Requirements</span></span>
------------
><span data-ttu-id="252b8-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="252b8-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="252b8-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="252b8-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="252b8-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="252b8-118">See also</span></span>


[<span data-ttu-id="252b8-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="252b8-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



