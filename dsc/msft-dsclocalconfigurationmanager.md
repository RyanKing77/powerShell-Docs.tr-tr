---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: MSFT_DSCLocalConfigurationManager sınıfı
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892282"
---
# <a name="msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager sınıfı

Yapılandırma durumunu kontrol yerel Configuration Manager (LCM) dosyaları ve yapılandırmaları uygulamak için Yapılandırma Aracı'nı kullanır.

Aşağıdaki söz dizimini Yönetilen Nesne Biçimi (MOF) koddan Basitleştirilmiş ve tüm devralınan özellikler içerir.

## <a name="syntax"></a>Sözdizimi

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Üyeler

**MSFT_DSCLocalConfigurationManager** sınıfı aşağıdaki üyelere sahiptir:

- [Yöntemleri] []

### <a name="methods"></a>Yöntemler

**MSFT_DSCLocalConfigurationManager** sınıfı bu yöntemleri vardır.

|Yöntem |Açıklama |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Yapılandırma Aracı, bekleyen yapılandırmayı uygulamak için kullanır.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| DSC kaynak hata ayıklama devre dışı bırakır.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| DSC kaynak hata ayıklamasını etkinleştirir.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Yönetilen düğüme yapılandırma belgesi gönderir ve kullandığı **alma** yapılandırmayı uygulamak için yapılandırma aracısı yöntemi.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Belirli bir işle ilgili yapılandırma aracı çıkış alır.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Yapılandırma durumu geçmişi Al|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Yapılandırma Aracı denetlemek için kullanılan LCM ayarlarını alır.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Tutarlılık denetimi başlatır.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Yapılandırma dosyaları kaldırır.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Doğrudan çağıran **alma** DSC kaynağı yöntemi.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Doğrudan çağıran **ayarlamak** DSC kaynağı yöntemi.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Doğrudan çağıran **Test** DSC kaynağı yöntemi.|
| [Geri alma](msft-dsclocalconfigurationmanager-rollback.md)| Bir önceki yapılandırmaya geri dön dökümü yapar.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Yapılandırma belgelerini yönetilen düğüme gönderir ve bir bekleyen değişiklik olarak kaydeder.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Yapılandırma belgelerini yönetilen düğüme gönderir ve yapılandırmayı uygulamak için yapılandırma aracısı kullanır.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Yapılandırma belgelerini yönetilen düğüme gönderin ve yapılandırmayı uygulamak için Yapılandırma Aracı'nı kullanmaya başlayın. GetConfigurationResultOutput sonuç çıkış almak için kullanın.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Yapılandırma Aracı denetlemek için kullanılan LCM ayarlarını belirler.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Devam eden yapılandırma durdurur.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Yapılandırma belgelerini yönetilen düğüme gönderir ve belgeyi karşı geçerli yapılandırmasını doğrular.|

## <a name="requirements"></a>Gereksinimler

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration