---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893085"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="735db-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceTest yöntemi</span><span class="sxs-lookup"><span data-stu-id="735db-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="735db-104">Doğrudan çağıran **Test** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="735db-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="735db-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="735db-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="735db-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="735db-106">Parameters</span></span>

<span data-ttu-id="735db-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="735db-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="735db-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modül adı.</span><span class="sxs-lookup"><span data-stu-id="735db-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="735db-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="735db-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="735db-110">Kullanım [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet'ini kaynak özelliklerini ve bunların türlerini keşfedin.</span><span class="sxs-lookup"><span data-stu-id="735db-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="735db-111">*InDesiredState* \[kullanıma\] getirisi, bu özellik kümesine **true** hedef düğüm istenen durumda ise.</span><span class="sxs-lookup"><span data-stu-id="735db-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="735db-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="735db-112">Return value</span></span>

<span data-ttu-id="735db-113">Başarılıysa sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="735db-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="735db-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="735db-114">Remarks</span></span>

<span data-ttu-id="735db-115">Statik bir yöntem budur.</span><span class="sxs-lookup"><span data-stu-id="735db-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="735db-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="735db-116">Requirements</span></span>

<span data-ttu-id="735db-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="735db-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="735db-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="735db-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="735db-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="735db-119">See also</span></span>

[<span data-ttu-id="735db-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="735db-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)