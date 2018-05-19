---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi
ms.openlocfilehash: 0c9c1d33117067d76d61036d5839f0b676eb4a97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6792a-103">MSFT_DSCLocalConfigurationManager sınıfının ResourceSet yöntemi</span><span class="sxs-lookup"><span data-stu-id="6792a-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6792a-104">Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6792a-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="6792a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6792a-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="6792a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6792a-106">Parameters</span></span>
----------

<span data-ttu-id="6792a-107">*ResourceType* \[içinde\] çağırmak için kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="6792a-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="6792a-108">*ModuleName* \[içinde\] çağırmak için kaynak içeren modülü adı.</span><span class="sxs-lookup"><span data-stu-id="6792a-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="6792a-109">*resourceProperty* \[içinde\] kaynak özellik adını ve değerini bir karma tablosunda anahtar ve değer sırasıyla belirtir.</span><span class="sxs-lookup"><span data-stu-id="6792a-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="6792a-110">Kullanım [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kaynak özelliklerini ve bunların türlerini bulmak için cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6792a-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="6792a-111">*RebootRequired* \[çıkışı\] getirisi, bu özelliği ayarlamak **true** hedef düğümün yeniden başlatılması gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="6792a-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="6792a-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="6792a-112">Return value</span></span>
------------

<span data-ttu-id="6792a-113">Başarı sıfır döndürür; Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6792a-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6792a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6792a-114">Remarks</span></span>

<span data-ttu-id="6792a-115">Bu statik bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="6792a-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6792a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6792a-116">Requirements</span></span>
------------
><span data-ttu-id="6792a-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6792a-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6792a-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6792a-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6792a-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6792a-119">See also</span></span>


[<span data-ttu-id="6792a-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6792a-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)