---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="71486-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="71486-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="71486-104">Yapılandırma durumu geçmişi alın.</span><span class="sxs-lookup"><span data-stu-id="71486-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="71486-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71486-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="71486-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71486-106">Parameters</span></span>
----------

<span data-ttu-id="71486-107">*Tüm* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="71486-107">*All* \[in\]</span></span>  
<span data-ttu-id="71486-108">**doğru** bu yöntem tüm ilgili bilgileri yapılandırma çalıştıran makinede döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="71486-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="71486-109">*configurationStatus* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="71486-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="71486-110">Getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="71486-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="71486-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="71486-111">Return value</span></span>
------------

<span data-ttu-id="71486-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="71486-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="71486-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71486-113">Remarks</span></span>

<span data-ttu-id="71486-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="71486-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="71486-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71486-115">Requirements</span></span>
------------
><span data-ttu-id="71486-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="71486-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="71486-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="71486-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="71486-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="71486-118">See also</span></span>


[<span data-ttu-id="71486-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="71486-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



