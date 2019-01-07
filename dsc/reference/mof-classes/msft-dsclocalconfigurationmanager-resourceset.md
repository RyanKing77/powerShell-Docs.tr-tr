---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048695"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b98be-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi</span><span class="sxs-lookup"><span data-stu-id="b98be-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b98be-104">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b98be-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="b98be-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b98be-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="b98be-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b98be-106">Parameters</span></span>

<span data-ttu-id="b98be-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="b98be-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="b98be-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.</span><span class="sxs-lookup"><span data-stu-id="b98be-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b98be-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="b98be-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b98be-110">Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.</span><span class="sxs-lookup"><span data-stu-id="b98be-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b98be-111">*RebootRequired* \[kullanıma\] getirisi, bu özellik kümesine **true** hedef düğüm yeniden başlatılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="b98be-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="b98be-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b98be-112">Return value</span></span>

<span data-ttu-id="b98be-113">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b98be-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b98be-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b98be-114">Remarks</span></span>

<span data-ttu-id="b98be-115">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="b98be-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b98be-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b98be-116">Requirements</span></span>

<span data-ttu-id="b98be-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b98be-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b98be-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b98be-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b98be-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="b98be-119">See also</span></span>

[<span data-ttu-id="b98be-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b98be-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)