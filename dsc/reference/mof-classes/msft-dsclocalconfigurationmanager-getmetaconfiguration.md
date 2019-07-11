---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: GetMetaConfiguration yöntemi
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734434"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="9e555-103">GetMetaConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e555-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="9e555-104">Yapılandırma Aracı denetlemek için kullanılan yerel Configuration Manager ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="9e555-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e555-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e555-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="9e555-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e555-106">Parameters</span></span>

<span data-ttu-id="9e555-107">*MetaConfiguration* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCMetaConfiguration** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="9e555-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e555-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9e555-108">Return value</span></span>

<span data-ttu-id="9e555-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9e555-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e555-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e555-110">Remarks</span></span>

<span data-ttu-id="9e555-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="9e555-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e555-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e555-112">Requirements</span></span>

<span data-ttu-id="9e555-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9e555-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9e555-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9e555-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9e555-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e555-115">See also</span></span>

[<span data-ttu-id="9e555-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9e555-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
