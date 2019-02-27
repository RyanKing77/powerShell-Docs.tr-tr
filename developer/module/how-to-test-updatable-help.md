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
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845930"
---
# <a name="how-to-test-updatable-help"></a>Güncelleştirilebilir Yardımı Test Etme

Bu konuda, bir modül için güncelleştirilebilir Yardımı test yaklaşımları açıklanmaktadır.

## <a name="using-verbose-to-detect-errors"></a>Hataları algılamak için ayrıntılı kullanma

CAB dosyaları, modül için ve HelpInfo XML dosyasını karşıya yükledikten sonra dosyaları çalıştırarak test bir [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) komutunu **ayrıntılı** parametresi. **Ayrıntılı** parametresi yönlendirir `Update-Help` eylemlerini dosyasından okurken kritik adımları bildirmek için **HelpInfoUri** paketten çıkarılan CAB dosyasındaki dosya türleri doğrulama için modül bildirimindeki anahtar ve dile özgü modül dizindeki dosyaları yerleştirme.
CAB dosyaları, modül için ve HelpInfo XML dosyasını karşıya yükledikten sonra dosyaları çalıştırarak test bir [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) komutunu **ayrıntılı** parametresi. **Ayrıntılı** parametresi yönlendirir `Update-Help` eylemlerini dosyasından okurken kritik adımları bildirmek için **HelpInfoUri** paketten çıkarılan CAB dosyasındaki dosya türleri doğrulama için modül bildirimindeki anahtar ve dile özgü modül dizindeki dosyaları yerleştirme.

Tüm ayrıntılı iletiler çözümlendiğinde çalıştırma bir `Update-Help` komutunu **hata ayıklama** parametresi. Bu parametre, kalan problemleri güncelleştirilebilir Yardımı dosyalarla algılanmalıdır.