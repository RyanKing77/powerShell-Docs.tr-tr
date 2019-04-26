---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078665"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f3dec-103">MSFT_DSCLocalConfigurationManager sınıfının GetConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3dec-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f3dec-104">Yönetilen düğüme yapılandırma belgesi gönderir ve kullandığı **alma** yapılandırmayı uygulamak için yapılandırma aracısı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3dec-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3dec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3dec-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="f3dec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3dec-106">Parameters</span></span>

<span data-ttu-id="f3dec-107">*configurationData* \[içinde\] göndermek için yapılandırma verilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3dec-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="f3dec-108">*yapılandırmaları* \[kullanıma\] getirisi, yapılandırmaları katıştırılmış bir örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="f3dec-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="f3dec-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f3dec-109">Return value</span></span>

<span data-ttu-id="f3dec-110">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3dec-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3dec-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3dec-111">Remarks</span></span>

<span data-ttu-id="f3dec-112">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="f3dec-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f3dec-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3dec-113">Requirements</span></span>

<span data-ttu-id="f3dec-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f3dec-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f3dec-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f3dec-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f3dec-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3dec-116">See also</span></span>

[<span data-ttu-id="f3dec-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f3dec-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)