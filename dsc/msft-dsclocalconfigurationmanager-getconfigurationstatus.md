---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi"
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="41987-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="41987-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="41987-104">Yapılandırma durumu geçmişi alın.</span><span class="sxs-lookup"><span data-stu-id="41987-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="41987-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41987-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="41987-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41987-106">Parameters</span></span>
----------

<span data-ttu-id="41987-107">*Tüm* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="41987-107">*All* \[in\]</span></span>  
<span data-ttu-id="41987-108">**doğru** bu yöntem tüm ilgili bilgileri yapılandırma çalıştıran makinede döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="41987-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="41987-109">*configurationStatus* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="41987-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="41987-110">Getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="41987-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="41987-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="41987-111">Return value</span></span>
------------

<span data-ttu-id="41987-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="41987-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="41987-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41987-113">Remarks</span></span>

<span data-ttu-id="41987-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="41987-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="41987-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41987-115">Requirements</span></span>
------------
><span data-ttu-id="41987-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="41987-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="41987-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="41987-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="41987-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="41987-118">See also</span></span>


[<span data-ttu-id="41987-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="41987-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



