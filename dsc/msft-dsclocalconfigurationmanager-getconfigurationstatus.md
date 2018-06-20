---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221774"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3aa95-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="3aa95-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3aa95-104">Yapılandırma durumu geçmişi alın.</span><span class="sxs-lookup"><span data-stu-id="3aa95-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="3aa95-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3aa95-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="3aa95-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3aa95-106">Parameters</span></span>
----------

<span data-ttu-id="3aa95-107">*Tüm* \[içinde\] **true** bu yöntem tüm ilgili bilgileri yapılandırma çalıştıran makinede döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="3aa95-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="3aa95-108">*configurationStatus* \[çıkışı\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="3aa95-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="3aa95-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3aa95-109">Return value</span></span>
------------

<span data-ttu-id="3aa95-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3aa95-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3aa95-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aa95-111">Remarks</span></span>

<span data-ttu-id="3aa95-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="3aa95-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3aa95-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3aa95-113">Requirements</span></span>
------------
><span data-ttu-id="3aa95-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3aa95-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3aa95-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3aa95-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3aa95-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="3aa95-116">See also</span></span>


[<span data-ttu-id="3aa95-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3aa95-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)