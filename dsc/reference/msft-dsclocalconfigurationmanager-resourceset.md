---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405842"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6f64a-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f64a-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6f64a-104">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6f64a-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f64a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f64a-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="6f64a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f64a-106">Parameters</span></span>

<span data-ttu-id="6f64a-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="6f64a-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="6f64a-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.</span><span class="sxs-lookup"><span data-stu-id="6f64a-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="6f64a-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f64a-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="6f64a-110">Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.</span><span class="sxs-lookup"><span data-stu-id="6f64a-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="6f64a-111">*RebootRequired* \[kullanıma\] getirisi, bu özellik kümesine **true** hedef düğüm yeniden başlatılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="6f64a-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="6f64a-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="6f64a-112">Return value</span></span>

<span data-ttu-id="6f64a-113">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f64a-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f64a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f64a-114">Remarks</span></span>

<span data-ttu-id="6f64a-115">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="6f64a-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6f64a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f64a-116">Requirements</span></span>

<span data-ttu-id="6f64a-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6f64a-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6f64a-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6f64a-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6f64a-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6f64a-119">See also</span></span>

[<span data-ttu-id="6f64a-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6f64a-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)