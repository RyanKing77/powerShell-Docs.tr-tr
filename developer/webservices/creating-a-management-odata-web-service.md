---
title: Management OData Web hizmeti oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847253"
---
# <a name="creating-a-management-odata-web-service"></a>Yönetim OData Web Hizmeti Oluşturma

Management ODATA IIS uzantısı, bir ASP.NET web hizmeti uç Windows PowerShell cmdlet'leri ve betikleri, OData Web hizmetini varlıklar olarak aracılığıyla erişilebilen yönetim verilerinizi gösteren noktası oluşturmak için kullanılan bir altyapıdır. Bunu, OData istekleri işleme ve bunları bir Windows PowerShell çağırma dönüştürme yapar. Ürün takımlar belirli yönetim veri kümelerini kullanıma uç noktalar oluşturmak için bu altyapısı üzerine oluşturabilirsiniz.

İndirme ve yükleme [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) örnek. Web hizmetini dağıtmak için yönergeleri izleyin. Bu web hizmeti oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemleri aracılığıyla hizmet ve işlem sunar. Web hizmetine yapılan CRUD istekleri istenen işlemleri gerçekleştirmek Windows PowerShell komutları çağırır. Temel alınan Windows PowerShell komutları ile CRUD işlemleri arasında bir eşleme, iki şema dosyaları, schema.mof ve schema.xml tarafından uygulanır. Schema.mof dosyasını kullanan [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) Yönetilen Nesne (MOF) standart. Schema.xml dosya açıklanan bir XML şeması kullanır [kaynak eşleme şeması](./resource-mapping-schema.md).

> [!IMPORTANT]
> Aşağıdaki özellikler, önce Windows Server 2008 R2 SP1 Management ODATA IIS uzantısı etkinleştirilirken etkinleştirilmelidir.
>
> 1.  IIS WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Management OData web hizmeti oluşturma adımları

Aşağıdaki konular, yönetim OData web hizmeti oluşturma ve dağıtma açıklanır.

- [Bir yönetim OData Web hizmeti için kaynak ekleme](./adding-resources-to-a-management-odata-web-service.md)

- [Management OData web hizmeti için özel yetkilendirme uygulama](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Management OData web hizmeti uzantısı SessionConfiguration uygulama](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Management OData web hizmeti için MOF şema dosyası yazma](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Management OData web hizmeti için XML şema dosyası yazma](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Management OData web hizmeti için Web.config dosyası yazma](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Management OData web hizmetini dağıtma](./deploying-a-management-odata-web-service.md)

- [Management OData varlıkları ilişkilendirme](./associating-management-odata-entities.md)

## <a name="see-also"></a>Ayrıca bkz:

[Management ODATA IIS uzantısı şema dosyaları](./management-odata-iis-extension-schema-files.md)
