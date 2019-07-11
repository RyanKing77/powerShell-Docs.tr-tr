---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: GetConfigurationStatus yöntemi
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734503"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="0d83d-103">GetConfigurationStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d83d-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="0d83d-104">Yapılandırma durumu geçmişi Al</span><span class="sxs-lookup"><span data-stu-id="0d83d-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d83d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d83d-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="0d83d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d83d-106">Parameters</span></span>

<span data-ttu-id="0d83d-107">*Tüm* \[içinde\] **true** bu yöntem, yapılandırma makine üzerinde çalışan tüm hakkında bilgiler döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="0d83d-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="0d83d-108">*configurationStatus* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="0d83d-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d83d-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="0d83d-109">Return value</span></span>

<span data-ttu-id="0d83d-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d83d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d83d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d83d-111">Remarks</span></span>

<span data-ttu-id="0d83d-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="0d83d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d83d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d83d-113">Requirements</span></span>

<span data-ttu-id="0d83d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0d83d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0d83d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d83d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0d83d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d83d-116">See also</span></span>

[<span data-ttu-id="0d83d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0d83d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
