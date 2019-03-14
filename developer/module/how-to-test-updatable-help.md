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
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794272"
---
# <a name="how-to-test-updatable-help"></a>Güncelleştirilebilir Yardımı Test Etme

Bu konuda, bir modül için güncelleştirilebilir Yardımı test yaklaşımları açıklanmaktadır.

## <a name="using-verbose-to-detect-errors"></a>Hataları algılamak için ayrıntılı kullanma

CAB dosyaları, modül için ve HelpInfo XML dosyasını karşıya yükledikten sonra dosyaları çalıştırarak test bir [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) komutunu **ayrıntılı** parametresi. **Ayrıntılı** parametresi yönlendirir `Update-Help` eylemlerini dosyasından okurken kritik adımları bildirmek için **HelpInfoUri** paketten çıkarılan CAB dosyasındaki dosya türleri doğrulama için modül bildirimindeki anahtar ve dile özgü modül dizindeki dosyaları yerleştirme.

Tüm ayrıntılı iletiler çözümlendiğinde çalıştırma bir `Update-Help` komutunu **hata ayıklama** parametresi. Bu parametre, kalan problemleri güncelleştirilebilir Yardımı dosyalarla algılanmalıdır.