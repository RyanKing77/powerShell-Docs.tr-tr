---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405727"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="08fd9-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfigurationStatus yöntemi</span><span class="sxs-lookup"><span data-stu-id="08fd9-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="08fd9-104">Yapılandırma durumu geçmişi Al</span><span class="sxs-lookup"><span data-stu-id="08fd9-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="08fd9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08fd9-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="08fd9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08fd9-106">Parameters</span></span>

<span data-ttu-id="08fd9-107">*Tüm* \[içinde\] **true** bu yöntem, yapılandırma makine üzerinde çalışan tüm hakkında bilgiler döndürmelidir, yapılandırma uygulama ve tutarlılık denetimi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="08fd9-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="08fd9-108">*configurationStatus* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCConfigurationStatus** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="08fd9-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="08fd9-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="08fd9-109">Return value</span></span>

<span data-ttu-id="08fd9-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="08fd9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="08fd9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08fd9-111">Remarks</span></span>

<span data-ttu-id="08fd9-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="08fd9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="08fd9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08fd9-113">Requirements</span></span>

<span data-ttu-id="08fd9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="08fd9-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="08fd9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="08fd9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="08fd9-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="08fd9-116">See also</span></span>

[<span data-ttu-id="08fd9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="08fd9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)