---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSCAutomationHostEnabled kayıt defteri anahtarı
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076505"
---
><span data-ttu-id="d4f21-103">Şunun için geçerlidir: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d4f21-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="d4f21-104">DSCAutomationHostEnabled kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="d4f21-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="d4f21-105">DSC kullandığı **DSCAutomationHostEnabled** kayıt defteri anahtarı altında **hkey_local_machıne\software\microsoft\windows\currentversion\policies\system** makinenin başlangıç yapılandırmasını etkinleştirmek için önyükleme artırma.</span><span class="sxs-lookup"><span data-stu-id="d4f21-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="d4f21-106">**DSCAutomationHostEnabled** üç modunu destekler:</span><span class="sxs-lookup"><span data-stu-id="d4f21-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="d4f21-107">DSCAutomationHostEnabled değeri</span><span class="sxs-lookup"><span data-stu-id="d4f21-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="d4f21-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4f21-108">Description</span></span>   |
|---|---|
<span data-ttu-id="d4f21-109">0</span><span class="sxs-lookup"><span data-stu-id="d4f21-109">0</span></span> | <span data-ttu-id="d4f21-110">Makine önyüklemede yapılandırma devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="d4f21-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="d4f21-111">1</span><span class="sxs-lookup"><span data-stu-id="d4f21-111">1</span></span> | <span data-ttu-id="d4f21-112">Makine önyüklemede yapılandırma etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d4f21-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="d4f21-113">2</span><span class="sxs-lookup"><span data-stu-id="d4f21-113">2</span></span> | <span data-ttu-id="d4f21-114">Yalnızca DSC ise, makine yapılandırma Etkinleştirme Beklemede veya geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="d4f21-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="d4f21-115">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="d4f21-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="d4f21-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="d4f21-116">See Also</span></span>

<span data-ttu-id="d4f21-117">İlk önyüklemede yapılandırma çalıştırmak için bu özelliği kullanmak nasıl bir örnek için bkz [DSC kullanarak ilk önyüklemede bir sanal makine yapılandırma](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="d4f21-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
