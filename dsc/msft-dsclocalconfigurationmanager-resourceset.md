---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892109"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f8e3f-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8e3f-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f8e3f-104">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f8e3f-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8e3f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8e3f-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="f8e3f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f8e3f-106">Parameters</span></span>

<span data-ttu-id="f8e3f-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="f8e3f-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="f8e3f-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.</span><span class="sxs-lookup"><span data-stu-id="f8e3f-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f8e3f-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8e3f-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f8e3f-110">Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.</span><span class="sxs-lookup"><span data-stu-id="f8e3f-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f8e3f-111">*RebootRequired* \[kullanıma\] getirisi, bu özellik kümesine **true** hedef düğüm yeniden başlatılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="f8e3f-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="f8e3f-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f8e3f-112">Return value</span></span>

<span data-ttu-id="f8e3f-113">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f8e3f-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8e3f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8e3f-114">Remarks</span></span>

<span data-ttu-id="f8e3f-115">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="f8e3f-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8e3f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8e3f-116">Requirements</span></span>

<span data-ttu-id="f8e3f-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f8e3f-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f8e3f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8e3f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f8e3f-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f8e3f-119">See also</span></span>

[<span data-ttu-id="f8e3f-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f8e3f-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)