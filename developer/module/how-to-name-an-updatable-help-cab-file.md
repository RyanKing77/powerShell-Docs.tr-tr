---
title: Nasıl bir güncelleştirilebilir Yardımı CAB dosyası adı | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 23303489372cfe7e036fdea842ae75f7e47503c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850515"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="a4963-102">Güncelleştirilebilir Yardım CAB Dosyasını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="a4963-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="a4963-103">Bu konu, güncelleştirilebilir Yardımı dolap gerekli ad biçimini açıklar (. CAB) dosyası.</span><span class="sxs-lookup"><span data-stu-id="a4963-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="a4963-104">Güncelleştirilebilir Yardım CAB Dosyasını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="a4963-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="a4963-105">Güncelleştirilebilir bir dolap (. CAB) dosyası aşağıdaki biçimde bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4963-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="a4963-106">Öğe adı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="a4963-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="a4963-107">ModuleName değeri, **adı** özelliği **ModuleInfo** nesnesinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4963-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="a4963-108">Değerini **adı** özelliği **ModuleInfo** nesnesinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4963-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="a4963-109">ModuleGUID değeri, **GUID** modül bildirimindeki anahtar.</span><span class="sxs-lookup"><span data-stu-id="a4963-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="a4963-110">Yardım dosyaları CAB dosyasındaki UICulture UI kültür.</span><span class="sxs-lookup"><span data-stu-id="a4963-110">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="a4963-111">Bu değer bir değerle eşleşmelidir **UICulture** modülü için HelpInfo XML dosyasındaki öğeleri.</span><span class="sxs-lookup"><span data-stu-id="a4963-111">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="a4963-112">Örneğin, modül adı "TestModule" ise, ' % s'modülü GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, ve UI kültürü "en-US" ise, CAB dosyasının adı olacaktır:</span><span class="sxs-lookup"><span data-stu-id="a4963-112">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`