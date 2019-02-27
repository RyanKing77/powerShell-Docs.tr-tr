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
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="7e62d-102">Yönetim OData Web Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e62d-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="7e62d-103">Management ODATA IIS uzantısı, bir ASP.NET web hizmeti uç Windows PowerShell cmdlet'leri ve betikleri, OData Web hizmetini varlıklar olarak aracılığıyla erişilebilen yönetim verilerinizi gösteren noktası oluşturmak için kullanılan bir altyapıdır.</span><span class="sxs-lookup"><span data-stu-id="7e62d-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="7e62d-104">Bunu, OData istekleri işleme ve bunları bir Windows PowerShell çağırma dönüştürme yapar.</span><span class="sxs-lookup"><span data-stu-id="7e62d-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="7e62d-105">Ürün takımlar belirli yönetim veri kümelerini kullanıma uç noktalar oluşturmak için bu altyapısı üzerine oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e62d-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="7e62d-106">İndirme ve yükleme [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) örnek.</span><span class="sxs-lookup"><span data-stu-id="7e62d-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="7e62d-107">Web hizmetini dağıtmak için yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7e62d-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="7e62d-108">Bu web hizmeti oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemleri aracılığıyla hizmet ve işlem sunar.</span><span class="sxs-lookup"><span data-stu-id="7e62d-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="7e62d-109">Web hizmetine yapılan CRUD istekleri istenen işlemleri gerçekleştirmek Windows PowerShell komutları çağırır.</span><span class="sxs-lookup"><span data-stu-id="7e62d-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="7e62d-110">Temel alınan Windows PowerShell komutları ile CRUD işlemleri arasında bir eşleme, iki şema dosyaları, schema.mof ve schema.xml tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7e62d-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="7e62d-111">Schema.mof dosyasını kullanan [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) Yönetilen Nesne (MOF) standart.</span><span class="sxs-lookup"><span data-stu-id="7e62d-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="7e62d-112">Schema.xml dosya açıklanan bir XML şeması kullanır [kaynak eşleme şeması](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="7e62d-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e62d-113">Aşağıdaki özellikler, önce Windows Server 2008 R2 SP1 Management ODATA IIS uzantısı etkinleştirilirken etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7e62d-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="7e62d-114">IIS WebServerRole</span><span class="sxs-lookup"><span data-stu-id="7e62d-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="7e62d-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="7e62d-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="7e62d-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="7e62d-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="7e62d-117">IIS ManagementOData</span><span class="sxs-lookup"><span data-stu-id="7e62d-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="7e62d-118">Management OData web hizmeti oluşturma adımları</span><span class="sxs-lookup"><span data-stu-id="7e62d-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="7e62d-119">Aşağıdaki konular, yönetim OData web hizmeti oluşturma ve dağıtma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="7e62d-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="7e62d-120">Bir yönetim OData Web hizmeti için kaynak ekleme</span><span class="sxs-lookup"><span data-stu-id="7e62d-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="7e62d-121">Management OData web hizmeti için özel yetkilendirme uygulama</span><span class="sxs-lookup"><span data-stu-id="7e62d-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="7e62d-122">Management OData web hizmeti uzantısı SessionConfiguration uygulama</span><span class="sxs-lookup"><span data-stu-id="7e62d-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="7e62d-123">Management OData web hizmeti için MOF şema dosyası yazma</span><span class="sxs-lookup"><span data-stu-id="7e62d-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="7e62d-124">Management OData web hizmeti için XML şema dosyası yazma</span><span class="sxs-lookup"><span data-stu-id="7e62d-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="7e62d-125">Management OData web hizmeti için Web.config dosyası yazma</span><span class="sxs-lookup"><span data-stu-id="7e62d-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="7e62d-126">Management OData web hizmetini dağıtma</span><span class="sxs-lookup"><span data-stu-id="7e62d-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="7e62d-127">Management OData varlıkları ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="7e62d-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="7e62d-128">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="7e62d-128">See Also</span></span>

[<span data-ttu-id="7e62d-129">Management ODATA IIS uzantısı şema dosyaları</span><span class="sxs-lookup"><span data-stu-id="7e62d-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
