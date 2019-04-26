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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080688"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="c6449-102">Rol Tabanlı Yetkilendirmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c6449-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="c6449-103">Bu konu, örnek uygulaması için rol tabanlı yetkilendirme ilkesini yapılandırma işlemi gösterilmektedir [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) arabirimi açıklanan [özel uygulama Management OData IIS uzantısı için yetkilendirme](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="c6449-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="c6449-104">Bu örnekte, örnek Yönetimi OData uygulama tarafından yetkilendirme ilkesini tanımlamak için kullanılan bir XML dosyası yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="c6449-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="c6449-105">İki rol oluşturacak ve bu rolleri ile iş akışlarını içeren farklı Windows PowerShell modülleri ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="c6449-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="c6449-106">XML dosyasını tanımlayan şemayı adresinde listelenmiş [rol tabanlı yetkilendirme yapılandırma şeması](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="c6449-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="c6449-107">RBacConfiguration.xml dosyasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="c6449-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="c6449-108">Bu dosya, uygulama için yetkilendirme ilkesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c6449-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="c6449-109">Rolleri kullanarak tanımlanmış `Group` düğümleri.</span><span class="sxs-lookup"><span data-stu-id="c6449-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="c6449-110">A `Group` düğümü bu gruba atanmış kullanıcıların Windows PowerShell komutlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c6449-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="c6449-111">Kullanıcıları, grupları kullanarak atanır `User` düğümleri.</span><span class="sxs-lookup"><span data-stu-id="c6449-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="c6449-112">Bu örneklerde, bir modül yöneticinin ekleyeceksiniz `Group` düğümünü ve her gruba bir kullanıcı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6449-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="c6449-113">Bir modül için bir grup düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="c6449-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="c6449-114">Adlı bir dosya oluşturun **RBacConfiguration.xml** bir metin düzenleyicisinde.</span><span class="sxs-lookup"><span data-stu-id="c6449-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="c6449-115">Bu dosya, web hizmetiniz için ana uygulama dizinine kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c6449-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="c6449-116">Aşağıdaki metni dosyaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6449-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="c6449-117">İki dosyayı içeren `Group` düğümleri.</span><span class="sxs-lookup"><span data-stu-id="c6449-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="c6449-118">Bunlar bu örnekte kullanılan iki rolleri temsil `NonAdminGroup` ve `AdminGroup` rolleri.</span><span class="sxs-lookup"><span data-stu-id="c6449-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="c6449-119">Kapatma sonrasında doğrudan `Cmdlets` ilk etiket `Group` düğümü, aşağıdaki XML'i ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6449-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="c6449-120">Bir grup düğümüne bir kullanıcı ekleme</span><span class="sxs-lookup"><span data-stu-id="c6449-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="c6449-121">Açık **RBacConfiguration.xml** dosyasını bir metin düzenleyicisinde.</span><span class="sxs-lookup"><span data-stu-id="c6449-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="c6449-122">Bu dosya C: klasöründe bulunan\\yüklemeden önce uç nokta adı değiştirmediyseniz \inetpub\wwwroot\Modata.</span><span class="sxs-lookup"><span data-stu-id="c6449-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="c6449-123">İçinde kapanış etiketinin hemen sonra `Users` düğümü, aşağıdaki XML'i ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6449-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="c6449-124">Önceki adımda XML eklendikten sonra doğrudan aşağıdaki XML'i ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6449-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```