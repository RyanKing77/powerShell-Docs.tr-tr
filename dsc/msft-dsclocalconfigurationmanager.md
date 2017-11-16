---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "MSFT_DSCLocalConfigurationManager sınıfı"
ms.openlocfilehash: 35f732698fcc58f7bd43945edd10c143ffb79af9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfı

Yerel Yapılandırma Yöneticisi'ni (yapılandırma dosyalarını durumunu denetler ve yapılandırma aracısı yapılandırmaları uygulamak için kullandığı LCM'yi).

Aşağıdaki sözdizimini yönetilen Nesne Biçimi (MOF) koddan Basitleştirilmiş ve tüm devralınan özellikler içerir.

## <a name="syntax"></a>Sözdizimi
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Üyeler
-------

**MSFT_DSCLocalConfigurationManager** sınıfı aşağıdaki üyeleri sahiptir:

-   [Yöntemleri] []

### <a name="methods"></a>Yöntemler

**MSFT_DSCLocalConfigurationManager** sınıfı bu yöntemler vardır.

|Yöntem |Açıklama |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Bekleyen yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.| 
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| DSC kaynak hata ayıklama devre dışı bırakır.| 
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| DSC kaynak hata ayıklamasını etkinleştirir.| 
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Yapılandırma belgesini yönetilen düğüme gönderir ve kullandığı **almak** yapılandırmayı uygulamak için yapılandırma Aracısı'nın yöntemi.| 
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Belirli bir iş ile ilgili yapılandırma aracısı çıktısını alır.| 
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Yapılandırma durumu geçmişi alın.| 
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Yapılandırma aracısı denetlemek için kullanılan LCM'yi ayarlarını alır.| 
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Tutarlılık denetimi başlatır.| 
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Yapılandırma dosyalarını kaldırır.| 
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Doğrudan çağıran **almak** DSC kaynağı yöntemi.| 
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.| 
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Doğrudan çağıran **Test** DSC kaynağı yöntemi.| 
| [Geri alma](msft-dsclocalconfigurationmanager-rollback.md)| Dökümünü önceki yapılandırmaya geri dön.| 
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Yönetilen düğüme yapılandırma belgesini gönderir ve bekleyen bir değişiklik kaydeder.| 
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Yönetilen düğüme yapılandırma belgesini gönderir ve yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanır.| 
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Yönetilen düğüme yapılandırma belgesi göndermek ve yapılandırmayı uygulamak için yapılandırma Aracısı'nı kullanmaya başlayın. Sonuç çıkış almak için GetConfigurationResultOutput kullanın.| 
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Yapılandırma aracısı denetlemek için kullanılan LCM'yi ayarlarını belirler.| 
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Devam ediyor yapılandırma durdurur.| 
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Yönetilen düğüme yapılandırma belgesini gönderir ve geçerli yapılandırma belge karşı doğrular.| 



 

## <a name="requirements"></a>Gereksinimler
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration



 

 



