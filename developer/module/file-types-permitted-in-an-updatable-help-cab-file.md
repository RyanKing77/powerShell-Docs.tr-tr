---
title: Güncelleştirilebilir bir izin verilen dosya türleri Yardım CAB dosyası | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082456"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Güncelleştirilebilir CAB Dosyasında İzin Verilen Dosya Türleri

Bu konular, listeler ve içerik için güncelleştirilebilir Yardımı CAB dosyaları gereksinimlerini açıklar.

## <a name="updatable-help-cab-file-requirements"></a>Güncelleştirilebilir Yardımı CAB dosyası gereksinimleri

Sıkıştırılmamış CAB dosya içeriği varsayılan olarak 1 GB ile sınırlıdır. Bu sınırı atlamak için kullanılacak kullanıcınız **zorla** parametresinin [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet'leri.

Internet'ten indirilen Yardım dosyaları güvenliğini sağlamak için güncelleştirilebilir Yardımı CAB dosyası yalnızca aşağıda listelenen dosya türlerini içerebilir. [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet Yardım konusu şemaları karşı tüm dosyaları doğrular. Varsa `Update-Help` cmdlet'i geçersiz veya izin verilen bir tür değil bir dosyayı karşılaştığında, geçersiz dosya yüklemez ve kullanıcının bilgisayarında CAB dosyaları yükleme durdurur.

- Cmdlet'leri için XML tabanlı Yardım konuları.

- Betik ve işlevlerde için XML tabanlı Yardım konuları.

- Windows PowerShell sağlayıcıları için XML tabanlı Yardım konuları.

- Metin tabanlı Yardım konuları, gibi ilgili konular.

[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) CAB ayıklar CAB içeriği doğrular. Varsa `Update-Help` bulur uyumlu olmayan dosya türlerini bir güncelleştirilebilir Yardımı CAB dosyası, bir sonlandırma hatası oluşturur ve işlemi durdurur. Yardım dosyaları CAB, bile bu uyumlu bir dosya türlerinin yüklemez.