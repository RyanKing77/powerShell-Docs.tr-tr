---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının GetMetaConfiguration yöntemi
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686001"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="929ca-103">MSFT_DSCLocalConfigurationManager sınıfının GetMetaConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="929ca-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="929ca-104">Yapılandırma Aracı denetlemek için kullanılan yerel Configuration Manager ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="929ca-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="929ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="929ca-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="929ca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="929ca-106">Parameters</span></span>

<span data-ttu-id="929ca-107">*MetaConfiguration* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_DSCMetaConfiguration** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="929ca-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="929ca-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="929ca-108">Return value</span></span>

<span data-ttu-id="929ca-109">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="929ca-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="929ca-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="929ca-110">Remarks</span></span>

<span data-ttu-id="929ca-111">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="929ca-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="929ca-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="929ca-112">Requirements</span></span>

<span data-ttu-id="929ca-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="929ca-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="929ca-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="929ca-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="929ca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="929ca-115">See also</span></span>

[<span data-ttu-id="929ca-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="929ca-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)