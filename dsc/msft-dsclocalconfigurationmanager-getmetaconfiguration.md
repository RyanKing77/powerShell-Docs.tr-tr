---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının GetMetaConfiguration yöntemi
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="df4b5-103">MSFT_DSCLocalConfigurationManager sınıfının GetMetaConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="df4b5-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="df4b5-104">Yapılandırma aracısı denetlemek için kullanılan yerel Configuration Manager ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="df4b5-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="df4b5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df4b5-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="df4b5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df4b5-106">Parameters</span></span>
----------

<span data-ttu-id="df4b5-107">*Meta yapılandırmasını* \[çıkışı\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCMetaConfiguration** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="df4b5-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="df4b5-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="df4b5-108">Return value</span></span>
------------

<span data-ttu-id="df4b5-109">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="df4b5-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="df4b5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df4b5-110">Remarks</span></span>

<span data-ttu-id="df4b5-111">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="df4b5-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="df4b5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df4b5-112">Requirements</span></span>
------------
><span data-ttu-id="df4b5-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="df4b5-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="df4b5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="df4b5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="df4b5-115">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="df4b5-115">See also</span></span>


[<span data-ttu-id="df4b5-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="df4b5-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)