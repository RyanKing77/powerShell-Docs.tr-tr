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
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082371"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="f2397-102">Güncelleştirilebilir Yardım CAB Dosyasını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="f2397-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="f2397-103">Bu konu, güncelleştirilebilir Yardımı dolap gerekli ad biçimini açıklar (. CAB) dosyası.</span><span class="sxs-lookup"><span data-stu-id="f2397-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="f2397-104">Güncelleştirilebilir Yardım CAB Dosyasını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="f2397-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="f2397-105">Güncelleştirilebilir bir dolap (. CAB) dosyası aşağıdaki biçimde bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2397-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="f2397-106">Öğe adı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="f2397-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="f2397-107">ModuleName değeri, **adı** özelliği **ModuleInfo** nesnesinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2397-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="f2397-108">ModuleGUID değeri, **GUID** modül bildirimindeki anahtar.</span><span class="sxs-lookup"><span data-stu-id="f2397-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="f2397-109">Yardım dosyaları CAB dosyasındaki UICulture UI kültür.</span><span class="sxs-lookup"><span data-stu-id="f2397-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="f2397-110">Bu değer bir değerle eşleşmelidir **UICulture** modülü için HelpInfo XML dosyasındaki öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f2397-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="f2397-111">Örneğin, modül adı "TestModule" ise, ' % s'modülü GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, ve UI kültürü "en-US" ise, CAB dosyasının adı olacaktır:</span><span class="sxs-lookup"><span data-stu-id="f2397-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`