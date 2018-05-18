---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi
ms.openlocfilehash: 2df04d317bd5e7a5c2a713d92be57c5c9a9f5e8c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="be703-103">MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="be703-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="be703-104">Yönetilen düğüme yapılandırma belgesini gönderir ve geçerli yapılandırma belge karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="be703-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="be703-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be703-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="be703-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be703-106">Parameters</span></span>
----------

<span data-ttu-id="be703-107">*configurationData* \[içinde\] confuguration için ortam verileri.</span><span class="sxs-lookup"><span data-stu-id="be703-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="be703-108">*InDesiredState* \[çıkışı\] getirisi, yönetilen düğüm yapılandırması belgesi tarafından belirtilen durumda olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be703-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="be703-109">*ResourcesInDesiredState* \[çıkışı\] getirisi, katıştırılmış örneğini içeren **MSFT_ResourceInDesiredState** istenilen durumda olan kaynakların belirten sınıf.</span><span class="sxs-lookup"><span data-stu-id="be703-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="be703-110">*ResourcesNotInDesiredState* \[çıkışı\] getirisi, katıştırılmış örneğini içeren **MSFT_ResourceNotInDesiredState** istenilen durumda olmayan kaynakları belirleyen sınıf.</span><span class="sxs-lookup"><span data-stu-id="be703-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="be703-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="be703-111">Return value</span></span>
------------

<span data-ttu-id="be703-112">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="be703-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="be703-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be703-113">Remarks</span></span>

<span data-ttu-id="be703-114">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="be703-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="be703-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be703-115">Requirements</span></span>
------------
><span data-ttu-id="be703-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="be703-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="be703-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="be703-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="be703-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="be703-118">See also</span></span>


[<span data-ttu-id="be703-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="be703-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)