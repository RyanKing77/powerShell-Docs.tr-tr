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
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082286"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="8d654-102">HelpInfo XML Sürüm Numaralarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="8d654-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="8d654-103">Bu konu başlığında, ayarlayın ve genellikle bir "HelpInfo XML dosyası." olarak bilinen bir güncelleştirilebilir bilgi dosyasında sürüm numaralarının artırmak açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="8d654-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="8d654-104">HelpInfo XML Sürüm Numaralarını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="8d654-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="8d654-105">Sürüm numaraları HelpInfo XML dosyasında, güncelleştirilebilir Yardımı çalışması için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8d654-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="8d654-106">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet'leri, yalnızca uzak HelpInfo XML dosyasındaki bir UI kültürü için sürüm numarası bu UI kültürü için sürüm numarasından daha büyük olduğunda yeni Yardım dosyalarını indirme Yerel HelpInfo XML veya yerel HelpInfo XML dosyası yok.</span><span class="sxs-lookup"><span data-stu-id="8d654-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="8d654-107">Tanımlanan 4 bölümde sürüm numarasını HelpInfo XML dosyasını kullanan **System.Version** Microsoft .NET Framework sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8d654-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="8d654-108">Biçim `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="8d654-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="8d654-109">Modül yazarları tarafından verilen düzeni numaralandırma herhangi bir sürümünü kullanabilir **System.Version** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8d654-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="8d654-110">Güncelleştirilebilir Yardımı gerektirir yalnızca sürüm numarası için kullanıcı Arabirimi kültürünü artışı CAB dosyası bu UI kültürü için yeni bir sürümü tarafından belirtilen konuma yüklendiğinde **HelpContentURI** HelpInfo XML dosyasında öğe.</span><span class="sxs-lookup"><span data-stu-id="8d654-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="8d654-111">Aşağıdaki örnek, Almanca (de-DE) UI kültür için sürüm 2.15.0.10 olduğunda HelpInfo XML dosyasının öğeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d654-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="8d654-112">UI kültürü için sürüm numarası, bu UI kültürü için CAB dosyası sürümü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="8d654-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="8d654-113">Sürüm numarası, tüm CAB dosyası için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8d654-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="8d654-114">CAB dosyası içinde farklı dosyalar farklı sürüm numaralarını ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="8d654-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="8d654-115">Her UI kültürü için sürüm numarası bağımsız olarak değerlendirilir ve modülün desteklediği diğer UI kültürü için sürüm numaraları için ilgili olmayan.</span><span class="sxs-lookup"><span data-stu-id="8d654-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>