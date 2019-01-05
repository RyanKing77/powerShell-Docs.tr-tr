---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048732"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c7ddc-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7ddc-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c7ddc-104">Yapılandırma durumu geçmişi Al</span><span class="sxs-lookup"><span data-stu-id="c7ddc-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7ddc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7ddc-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="c7ddc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7ddc-106">Parameters</span></span>

<span data-ttu-id="c7ddc-107">*Tüm* \[içinde\] **true** bu yöntem, yapılandırma makine üzerinde çalışan tüm hakkında bilgiler döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="c7ddc-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="c7ddc-108">*configurationStatus* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="c7ddc-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7ddc-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="c7ddc-109">Return value</span></span>

<span data-ttu-id="c7ddc-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7ddc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7ddc-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7ddc-111">Remarks</span></span>

<span data-ttu-id="c7ddc-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="c7ddc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7ddc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7ddc-113">Requirements</span></span>

<span data-ttu-id="c7ddc-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c7ddc-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c7ddc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c7ddc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c7ddc-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="c7ddc-116">See also</span></span>

[<span data-ttu-id="c7ddc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c7ddc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)