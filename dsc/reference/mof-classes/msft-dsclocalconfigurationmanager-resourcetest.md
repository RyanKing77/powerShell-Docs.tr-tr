---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048704"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4b634-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b634-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4b634-104">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b634-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b634-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b634-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="4b634-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b634-106">Parameters</span></span>

<span data-ttu-id="4b634-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="4b634-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="4b634-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.</span><span class="sxs-lookup"><span data-stu-id="4b634-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="4b634-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b634-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="4b634-110">Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.</span><span class="sxs-lookup"><span data-stu-id="4b634-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="4b634-111">*InDesiredState* \[kullanıma\] getirisi, bu özellik kümesine **true** hedef düğüm istenen durumda ise.</span><span class="sxs-lookup"><span data-stu-id="4b634-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="4b634-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4b634-112">Return value</span></span>

<span data-ttu-id="4b634-113">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b634-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b634-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b634-114">Remarks</span></span>

<span data-ttu-id="4b634-115">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="4b634-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b634-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b634-116">Requirements</span></span>

<span data-ttu-id="4b634-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4b634-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4b634-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4b634-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4b634-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="4b634-119">See also</span></span>

[<span data-ttu-id="4b634-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4b634-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)