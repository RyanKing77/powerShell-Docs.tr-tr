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
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082405"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="47a82-102">HelpInfo XML Dosyasını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="47a82-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="47a82-103">Bu konu, genellikle HelpInfo XML dosyası olarak bilinen güncelleştirilebilir Yardımı bilgi dosyaları, gerekli ad biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="47a82-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="47a82-104">HelpInfo XML Dosyasını Adlandırma</span><span class="sxs-lookup"><span data-stu-id="47a82-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="47a82-105">HelpInfo XML dosyası aşağıdaki biçimde bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="47a82-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="47a82-106">Öğe adı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="47a82-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="47a82-107">ModuleName değeri, **adı** özelliği **ModuleInfo** nesnesinin [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet döndürür.</span><span class="sxs-lookup"><span data-stu-id="47a82-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="47a82-108">ModuleGUID değeri, **GUID** modül bildirimindeki anahtar.</span><span class="sxs-lookup"><span data-stu-id="47a82-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="47a82-109">Örneğin, modül adı "TestModule" ise ve ' % s'modülü GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 modülü için HelpInfo XML dosyasının adı olacaktır:</span><span class="sxs-lookup"><span data-stu-id="47a82-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`