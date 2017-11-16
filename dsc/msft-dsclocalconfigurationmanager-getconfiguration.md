---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi"
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ba3d0-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba3d0-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ba3d0-104">Yapılandırma belgesini yönetilen düğüme gönderir ve kullandığı **almak** yapılandırmayı uygulamak için yapılandırma Aracısı'nın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba3d0-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="ba3d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba3d0-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="ba3d0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba3d0-106">Parameters</span></span>
----------

<span data-ttu-id="ba3d0-107">*configurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="ba3d0-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="ba3d0-108">Göndermek için yapılandırma verilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba3d0-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="ba3d0-109">*yapılandırmaları* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="ba3d0-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="ba3d0-110">Getirisi, katıştırılmış yapılandırmaları örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="ba3d0-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="ba3d0-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="ba3d0-111">Return value</span></span>
------------

<span data-ttu-id="ba3d0-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba3d0-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba3d0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba3d0-113">Remarks</span></span>

<span data-ttu-id="ba3d0-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="ba3d0-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba3d0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba3d0-115">Requirements</span></span>
------------
><span data-ttu-id="ba3d0-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ba3d0-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ba3d0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba3d0-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ba3d0-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="ba3d0-118">See also</span></span>


[<span data-ttu-id="ba3d0-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ba3d0-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



