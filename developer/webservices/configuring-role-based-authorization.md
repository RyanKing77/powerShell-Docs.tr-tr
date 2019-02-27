---
title: Rol tabanlı yetkilendirme yapılandırma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849332"
---
# <a name="configuring-role-based-authorization"></a>Rol Tabanlı Yetkilendirmeyi Yapılandırma

Bu konu, örnek uygulaması için rol tabanlı yetkilendirme ilkesini yapılandırma işlemi gösterilmektedir [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) arabirimi açıklanan [özel uygulama Management OData IIS uzantısı için yetkilendirme](./implementing-custom-authorization-for-a-management-odata-web-service.md).

Bu örnekte, örnek Yönetimi OData uygulama tarafından yetkilendirme ilkesini tanımlamak için kullanılan bir XML dosyası yapılandıracaksınız. İki rol oluşturacak ve bu rolleri ile iş akışlarını içeren farklı Windows PowerShell modülleri ilişkilendirin. XML dosyasını tanımlayan şemayı adresinde listelenmiş [rol tabanlı yetkilendirme yapılandırma şeması](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>RBacConfiguration.xml dosyasını değiştirme

Bu dosya, uygulama için yetkilendirme ilkesini tanımlar. Rolleri kullanarak tanımlanmış `Group` düğümleri. A `Group` düğümü bu gruba atanmış kullanıcıların Windows PowerShell komutlarını tanımlar. Kullanıcıları, grupları kullanarak atanır `User` düğümleri.

Bu örneklerde, bir modül yöneticinin ekleyeceksiniz `Group` düğümünü ve her gruba bir kullanıcı ekleyin.

#### <a name="adding-a-module-to-a-group-node"></a>Bir modül için bir grup düğüm ekleme

1. Adlı bir dosya oluşturun **RBacConfiguration.xml** bir metin düzenleyicisinde. Bu dosya, web hizmetiniz için ana uygulama dizinine kaydedilmelidir. Aşağıdaki metni dosyaya ekleyin.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. İki dosyayı içeren `Group` düğümleri. Bunlar bu örnekte kullanılan iki rolleri temsil `NonAdminGroup` ve `AdminGroup` rolleri.

   Kapatma sonrasında doğrudan `Cmdlets` ilk etiket `Group` düğümü, aşağıdaki XML'i ekleyin:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Bir grup düğümüne bir kullanıcı ekleme

1. Açık **RBacConfiguration.xml** dosyasını bir metin düzenleyicisinde. Bu dosya C: klasöründe bulunan\\yüklemeden önce uç nokta adı değiştirmediyseniz \inetpub\wwwroot\Modata.

2. İçinde kapanış etiketinin hemen sonra `Users` düğümü, aşağıdaki XML'i ekleyin:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Önceki adımda XML eklendikten sonra doğrudan aşağıdaki XML'i ekleyin:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```