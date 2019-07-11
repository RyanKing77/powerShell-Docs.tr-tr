---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: ResourceTest yöntemi
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727080"
---
# <a name="resourcetest-method"></a><span data-ttu-id="f9fe1-103">ResourceTest yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9fe1-103">ResourceTest method</span></span>

<span data-ttu-id="f9fe1-104">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9fe1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9fe1-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="f9fe1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9fe1-106">Parameters</span></span>

<span data-ttu-id="f9fe1-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="f9fe1-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f9fe1-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f9fe1-110">Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f9fe1-111">*InDesiredState* \[kullanıma\] getirisi, bu özellik kümesine **true** hedef düğüm istenen durumda ise.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="f9fe1-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f9fe1-112">Return value</span></span>

<span data-ttu-id="f9fe1-113">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9fe1-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9fe1-114">Remarks</span></span>

<span data-ttu-id="f9fe1-115">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9fe1-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9fe1-116">Requirements</span></span>

<span data-ttu-id="f9fe1-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f9fe1-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f9fe1-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f9fe1-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f9fe1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9fe1-119">See also</span></span>

[<span data-ttu-id="f9fe1-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f9fe1-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
