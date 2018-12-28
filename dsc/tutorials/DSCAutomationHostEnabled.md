---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSCAutomationHostEnabled kayıt defteri anahtarı
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405691"
---
><span data-ttu-id="9611c-103">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9611c-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="9611c-104">DSCAutomationHostEnabled kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="9611c-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="9611c-105">DSC kullandığı **DSCAutomationHostEnabled** kayıt defteri anahtarı altında **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies** ilk önyükleme yukarı makinenin yapılandırmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="9611c-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="9611c-106">DSCAutomationHostEnabled üç modunu destekler:</span><span class="sxs-lookup"><span data-stu-id="9611c-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="9611c-107">DSCAutomationHostEnabled değeri</span><span class="sxs-lookup"><span data-stu-id="9611c-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="9611c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9611c-108">Description</span></span>   |
|---|---|
<span data-ttu-id="9611c-109">0</span><span class="sxs-lookup"><span data-stu-id="9611c-109">0</span></span> | <span data-ttu-id="9611c-110">Makine önyüklemede yapılandırma devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="9611c-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="9611c-111">1</span><span class="sxs-lookup"><span data-stu-id="9611c-111">1</span></span> | <span data-ttu-id="9611c-112">Makine önyüklemede yapılandırma etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9611c-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="9611c-113">2</span><span class="sxs-lookup"><span data-stu-id="9611c-113">2</span></span> | <span data-ttu-id="9611c-114">Yalnızca DSC ise, makine yapılandırma Etkinleştirme Beklemede veya geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="9611c-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="9611c-115">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9611c-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9611c-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="9611c-116">See Also</span></span>

<span data-ttu-id="9611c-117">İlk önyüklemede yapılandırma çalıştırmak için bu özelliği kullanmak nasıl bir örnek için bkz [DSC kullanarak ilk önyüklemede bir sanal makine yapılandırma](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="9611c-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>