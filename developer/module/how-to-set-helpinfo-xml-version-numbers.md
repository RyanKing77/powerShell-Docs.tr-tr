---
title: HelpInfo XML sürüm numaraları ayarlama | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: 4929a5b1c9f73bb12b6df975e03fc529db3565ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851936"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="c7fee-102">HelpInfo XML Sürüm Numaralarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c7fee-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="c7fee-103">Bu konu başlığında, ayarlayın ve genellikle bir "HelpInfo XML dosyası." olarak bilinen bir güncelleştirilebilir bilgi dosyasında sürüm numaralarının artırmak açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="c7fee-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="c7fee-104">HelpInfo XML Sürüm Numaralarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c7fee-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="c7fee-105">Sürüm numaraları HelpInfo XML dosyasında, güncelleştirilebilir Yardımı çalışması için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7fee-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="c7fee-106">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet'leri, yalnızca uzak HelpInfo XML dosyasındaki bir UI kültürü için sürüm numarası bu UI kültürü için sürüm numarasından daha büyük olduğunda yeni Yardım dosyalarını indirme Yerel HelpInfo XML veya yerel HelpInfo XML dosyası yok.</span><span class="sxs-lookup"><span data-stu-id="c7fee-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>
<span data-ttu-id="c7fee-107">Sürüm numaraları HelpInfo XML dosyasında, güncelleştirilebilir Yardımı çalışması için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c7fee-107">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="c7fee-108">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet'leri, yalnızca uzak HelpInfo XML dosyasındaki bir UI kültürü için sürüm numarası bu UI kültürü için sürüm numarasından daha büyük olduğunda yeni Yardım dosyalarını indirme Yerel HelpInfo XML veya yerel HelpInfo XML dosyası yok.</span><span class="sxs-lookup"><span data-stu-id="c7fee-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="c7fee-109">Tanımlanan 4 bölümde sürüm numarasını HelpInfo XML dosyasını kullanan **System.Version** Microsoft .NET Framework sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7fee-109">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="c7fee-110">Biçim `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="c7fee-110">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="c7fee-111">Modül yazarları tarafından verilen düzeni numaralandırma herhangi bir sürümünü kullanabilir **System.Version** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c7fee-111">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="c7fee-112">Güncelleştirilebilir Yardımı gerektirir yalnızca sürüm numarası için kullanıcı Arabirimi kültürünü artışı CAB dosyası bu UI kültürü için yeni bir sürümü tarafından belirtilen konuma yüklendiğinde **HelpContentURI** HelpInfo XML dosyasında öğe.</span><span class="sxs-lookup"><span data-stu-id="c7fee-112">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="c7fee-113">Aşağıdaki örnek, Almanca (de-DE) UI kültür için sürüm 2.15.0.10 olduğunda HelpInfo XML dosyasının öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7fee-113">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="c7fee-114">UI kültürü için sürüm numarası, bu UI kültürü için CAB dosyası sürümü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="c7fee-114">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="c7fee-115">Sürüm numarası, tüm CAB dosyası için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c7fee-115">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="c7fee-116">CAB dosyası içinde farklı dosyalar farklı sürüm numaralarını ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="c7fee-116">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="c7fee-117">Her UI kültürü için sürüm numarası bağımsız olarak değerlendirilir ve modülün desteklediği diğer UI kültürü için sürüm numaraları için ilgili olmayan.</span><span class="sxs-lookup"><span data-stu-id="c7fee-117">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>