---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSCAutomationHostEnabled kayıt defteri anahtarı
ms.openlocfilehash: 0cecbadc6802938cadb4ffb9745a23e6b98544be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221978"
---
><span data-ttu-id="f040a-103">Uygulandığı öğe: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f040a-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="f040a-104">DSCAutomationHostEnabled kayıt defteri anahtarı</span><span class="sxs-lookup"><span data-stu-id="f040a-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="f040a-105">DSC kullanır **DSCAutomationHostEnabled** kayıt defteri anahtarında **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Policies** ilk önyükleme yukarı yerindeki makinede yapılandırmasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="f040a-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="f040a-106">DSCAutomationHostEnabled üç modlarını destekler:</span><span class="sxs-lookup"><span data-stu-id="f040a-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="f040a-107">DSCAutomationHostEnabled değeri</span><span class="sxs-lookup"><span data-stu-id="f040a-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="f040a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f040a-108">Description</span></span>   |
|---|---|
<span data-ttu-id="f040a-109">0</span><span class="sxs-lookup"><span data-stu-id="f040a-109">0</span></span> | <span data-ttu-id="f040a-110">Makine önyükleme yukarı yapılandırma devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="f040a-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="f040a-111">1</span><span class="sxs-lookup"><span data-stu-id="f040a-111">1</span></span> | <span data-ttu-id="f040a-112">Makine önyükleme yukarı yapılandırma etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f040a-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="f040a-113">2</span><span class="sxs-lookup"><span data-stu-id="f040a-113">2</span></span> | <span data-ttu-id="f040a-114">Yalnızca DSC ise makine yapılandırma Etkinleştirme Beklemede veya geçerli durumu.</span><span class="sxs-lookup"><span data-stu-id="f040a-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="f040a-115">Bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="f040a-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f040a-116">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="f040a-116">See Also</span></span>

<span data-ttu-id="f040a-117">İlk önyükleme yukarı yapılandırmaları çalıştırmak için bu özelliği kullanmak nasıl bir örnek için bkz: [DSC kullanarak ilk önyükleme yukarı bir sanal makineleri yapılandırma](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="f040a-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>