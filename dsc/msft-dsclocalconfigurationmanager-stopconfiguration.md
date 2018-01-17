---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi"
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="17b07-103">MSFT_DSCLocalConfigurationManager sınıfının StopConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="17b07-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="17b07-104">Devam ediyor yapılandırma değişikliği durdurur.</span><span class="sxs-lookup"><span data-stu-id="17b07-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="17b07-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17b07-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="17b07-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17b07-106">Parameters</span></span>
----------

<span data-ttu-id="17b07-107">*zorla* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="17b07-107">*force* \[in\]</span></span>  
<span data-ttu-id="17b07-108">**doğru** durdurmak için yapılandırmayı zorla uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="17b07-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="17b07-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="17b07-109">Return value</span></span>
------------

<span data-ttu-id="17b07-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="17b07-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="17b07-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17b07-111">Remarks</span></span>

<span data-ttu-id="17b07-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="17b07-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="17b07-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17b07-113">Requirements</span></span>
------------
><span data-ttu-id="17b07-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="17b07-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="17b07-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="17b07-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="17b07-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="17b07-116">See also</span></span>


[<span data-ttu-id="17b07-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="17b07-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



