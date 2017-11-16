---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi"
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="369ba-103">MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="369ba-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="369ba-104">Yönetilen düğüme yapılandırma belgesini gönderir ve geçerli yapılandırma belge karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="369ba-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="369ba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="369ba-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="369ba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="369ba-106">Parameters</span></span>
----------

<span data-ttu-id="369ba-107">*configurationData* \[içinde\]</span><span class="sxs-lookup"><span data-stu-id="369ba-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="369ba-108">Ortam verilerini confuguration için.</span><span class="sxs-lookup"><span data-stu-id="369ba-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="369ba-109">*InDesiredState* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="369ba-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="369ba-110">Getirisi, yönetilen düğüm yapılandırması belgesi tarafından belirtilen durumda olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="369ba-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="369ba-111">*ResourcesInDesiredState* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="369ba-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="369ba-112">Getirisi, katıştırılmış örneğini içeren **MSFT_ResourceInDesiredState** istenilen durumda olan kaynakların belirten sınıf.</span><span class="sxs-lookup"><span data-stu-id="369ba-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="369ba-113">*ResourcesNotInDesiredState* \[çıkışı\]</span><span class="sxs-lookup"><span data-stu-id="369ba-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="369ba-114">Getirisi, katıştırılmış örneğini içeren **MSFT_ResourceNotInDesiredState** istenilen durumda olmayan kaynakları belirleyen sınıf.</span><span class="sxs-lookup"><span data-stu-id="369ba-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="369ba-115">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="369ba-115">Return value</span></span>
------------

<span data-ttu-id="369ba-116">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="369ba-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="369ba-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="369ba-117">Remarks</span></span>

<span data-ttu-id="369ba-118">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="369ba-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="369ba-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="369ba-119">Requirements</span></span>
------------
><span data-ttu-id="369ba-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="369ba-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="369ba-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="369ba-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="369ba-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="369ba-122">See also</span></span>


[<span data-ttu-id="369ba-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="369ba-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



