---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi"
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="07152-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="07152-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="07152-104">Yönetilen düğüme yapılandırma belgesini gönderir ve bekleyen bir değişiklik kaydeder.</span><span class="sxs-lookup"><span data-stu-id="07152-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="07152-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07152-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="07152-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07152-106">Parameters</span></span>
----------

<span data-ttu-id="07152-107">*ConfigurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="07152-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="07152-108">Ortam verilerini yapılandırması için.</span><span class="sxs-lookup"><span data-stu-id="07152-108">The environment data for the configuration.</span></span>

<span data-ttu-id="07152-109">*zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="07152-109">*force* \[in\]</span></span>  
<span data-ttu-id="07152-110">**doğru** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="07152-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="07152-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="07152-111">Return value</span></span>
------------

<span data-ttu-id="07152-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="07152-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="07152-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07152-113">Remarks</span></span>

<span data-ttu-id="07152-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="07152-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="07152-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07152-115">Requirements</span></span>
------------
><span data-ttu-id="07152-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="07152-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="07152-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="07152-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="07152-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="07152-118">See also</span></span>


[<span data-ttu-id="07152-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="07152-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



