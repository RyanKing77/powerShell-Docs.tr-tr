---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi"
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2e1e1-103">MSFT_DSCLocalConfigurationManager sınıfının SendConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e1e1-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2e1e1-104">Yönetilen düğüme yapılandırma belgesini gönderir ve bekleyen bir değişiklik kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2e1e1-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="2e1e1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e1e1-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="2e1e1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e1e1-106">Parameters</span></span>
----------

<span data-ttu-id="2e1e1-107">*ConfigurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="2e1e1-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="2e1e1-108">Ortam verilerini yapılandırması için.</span><span class="sxs-lookup"><span data-stu-id="2e1e1-108">The environment data for the configuration.</span></span>

<span data-ttu-id="2e1e1-109">*zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="2e1e1-109">*force* \[in\]</span></span>  
<span data-ttu-id="2e1e1-110">**doğru** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="2e1e1-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2e1e1-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2e1e1-111">Return value</span></span>
------------

<span data-ttu-id="2e1e1-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e1e1-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e1e1-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e1e1-113">Remarks</span></span>

<span data-ttu-id="2e1e1-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="2e1e1-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2e1e1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e1e1-115">Requirements</span></span>
------------
><span data-ttu-id="2e1e1-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2e1e1-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2e1e1-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2e1e1-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2e1e1-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="2e1e1-118">See also</span></span>


[<span data-ttu-id="2e1e1-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2e1e1-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



