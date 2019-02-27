---
title: Nasıl HelpInfo XML dosya adı | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848093"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="d5202-102">HelpInfo XML Dosyasını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="d5202-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="d5202-103">Bu konu, genellikle HelpInfo XML dosyası olarak bilinen güncelleştirilebilir Yardımı bilgi dosyaları, gerekli ad biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d5202-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="d5202-104">HelpInfo XML Dosyasını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="d5202-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="d5202-105">HelpInfo XML dosyası aşağıdaki biçimde bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5202-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="d5202-106">Öğe adı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="d5202-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="d5202-107">ModuleName değeri, **adı** özelliği **ModuleInfo** nesnesinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5202-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="d5202-108">Değerini **adı** özelliği **ModuleInfo** nesnesinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5202-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="d5202-109">ModuleGUID değeri, **GUID** modül bildirimindeki anahtar.</span><span class="sxs-lookup"><span data-stu-id="d5202-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="d5202-110">Örneğin, modül adı "TestModule" ise ve ' % s'modülü GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 modülü için HelpInfo XML dosyasının adı olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d5202-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`