---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının GetMetaConfiguration yöntemi"
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="18e6e-103">MSFT_DSCLocalConfigurationManager sınıfının GetMetaConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="18e6e-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="18e6e-104">Yapılandırma aracısı denetlemek için kullanılan yerel Configuration Manager ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="18e6e-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="18e6e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18e6e-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="18e6e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18e6e-106">Parameters</span></span>
----------

<span data-ttu-id="18e6e-107">*Meta yapılandırmasını* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="18e6e-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="18e6e-108">Getirisi, katıştırılmış örneğini içeren **MSFT_DSCMetaConfiguration** ayarları tanımlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="18e6e-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="18e6e-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="18e6e-109">Return value</span></span>
------------

<span data-ttu-id="18e6e-110">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="18e6e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="18e6e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18e6e-111">Remarks</span></span>

<span data-ttu-id="18e6e-112">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="18e6e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="18e6e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18e6e-113">Requirements</span></span>
------------
><span data-ttu-id="18e6e-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="18e6e-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="18e6e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="18e6e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="18e6e-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="18e6e-116">See also</span></span>


[<span data-ttu-id="18e6e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="18e6e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



