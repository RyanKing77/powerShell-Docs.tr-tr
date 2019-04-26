---
title: Güncelleştirilebilir Yardımı Test etme | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082337"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="00a92-102">Güncelleştirilebilir Yardımı Test Etme</span><span class="sxs-lookup"><span data-stu-id="00a92-102">How to Test Updatable Help</span></span>

<span data-ttu-id="00a92-103">Bu konuda, bir modül için güncelleştirilebilir Yardımı test yaklaşımları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00a92-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="00a92-104">Hataları algılamak için ayrıntılı kullanma</span><span class="sxs-lookup"><span data-stu-id="00a92-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="00a92-105">CAB dosyaları, modül için ve HelpInfo XML dosyasını karşıya yükledikten sonra dosyaları çalıştırarak test bir [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) komutunu **ayrıntılı** parametresi.</span><span class="sxs-lookup"><span data-stu-id="00a92-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="00a92-106">**Ayrıntılı** parametresi yönlendirir `Update-Help` eylemlerini dosyasından okurken kritik adımları bildirmek için **HelpInfoUri** paketten çıkarılan CAB dosyasındaki dosya türleri doğrulama için modül bildirimindeki anahtar ve dile özgü modül dizindeki dosyaları yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="00a92-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="00a92-107">Tüm ayrıntılı iletiler çözümlendiğinde çalıştırma bir `Update-Help` komutunu **hata ayıklama** parametresi.</span><span class="sxs-lookup"><span data-stu-id="00a92-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="00a92-108">Bu parametre, kalan problemleri güncelleştirilebilir Yardımı dosyalarla algılanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00a92-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>