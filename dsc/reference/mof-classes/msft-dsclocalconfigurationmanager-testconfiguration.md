---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048652"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="eabcb-103">MSFT_DSCLocalConfigurationManager sınıfının TestConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="eabcb-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="eabcb-104">Yapılandırma belgelerini yönetilen düğüme gönderir ve belgeyi karşı geçerli yapılandırmasını doğrular.</span><span class="sxs-lookup"><span data-stu-id="eabcb-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="eabcb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eabcb-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="eabcb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eabcb-106">Parameters</span></span>

<span data-ttu-id="eabcb-107">*configurationData* \[içinde\] confuguration ortam verileri.</span><span class="sxs-lookup"><span data-stu-id="eabcb-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="eabcb-108">*InDesiredState* \[kullanıma\] getirisi, yönetilen düğüme yapılandırma belgesi tarafından belirtilen durumda olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="eabcb-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="eabcb-109">*ResourcesInDesiredState* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_ResourceInDesiredState** istenen durumda olan kaynakların belirten sınıf.</span><span class="sxs-lookup"><span data-stu-id="eabcb-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="eabcb-110">*ResourcesNotInDesiredState* \[kullanıma\] getirisi, katıştırılmış örneğini içeren **MSFT_ResourceNotInDesiredState** istenen durumda olmayan kaynaklar belirten sınıf.</span><span class="sxs-lookup"><span data-stu-id="eabcb-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="eabcb-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="eabcb-111">Return value</span></span>

<span data-ttu-id="eabcb-112">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="eabcb-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="eabcb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eabcb-113">Remarks</span></span>

<span data-ttu-id="eabcb-114">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="eabcb-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="eabcb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eabcb-115">Requirements</span></span>

<span data-ttu-id="eabcb-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="eabcb-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="eabcb-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="eabcb-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="eabcb-118">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="eabcb-118">See also</span></span>

[<span data-ttu-id="eabcb-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="eabcb-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)