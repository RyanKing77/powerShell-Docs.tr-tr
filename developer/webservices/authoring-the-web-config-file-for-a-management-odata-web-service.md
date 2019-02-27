---
title: Management OData web hizmeti Web.config dosyasını yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847316"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Yönetim OData web hizmeti için Web.config dosyası yazma

Management OData web hizmetini dağıtmadan önce web.config dosyasının, XML şema dosyalarını ve uygulayan DLL'leri işaret edecek şekilde yapılandırmanız gerekir [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) ve [ System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) arabirimleri.

## <a name="sample-config-file"></a>Örnek yapılandırma dosyası

Web hizmetiniz için web.config dosyasının benzer bir örnek verilmiştir.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a>Ayrıca bkz:

[Management OData web hizmeti için özel yetkilendirme uygulama](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[Management OData web hizmeti uzantısı SessionConfiguration uygulama](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Management OData web hizmeti için MOF şema dosyası yazma](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Management OData web hizmeti için XML şema dosyası yazma](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Management OData Web hizmeti oluşturma](./creating-a-management-odata-web-service.md)