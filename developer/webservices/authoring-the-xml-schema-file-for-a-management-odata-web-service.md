---
title: Management OData web hizmeti için XML şema dosyası yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848198"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="15653-102">Yönetim OData web hizmeti için XML şema dosyası yazma</span><span class="sxs-lookup"><span data-stu-id="15653-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="15653-103">Kaynakları tanımladıktan sonra web hizmetiniz açığa çıkarır (bkz [yönetim OData web hizmeti için MOF şema dosyası yazma](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), desteklenen uygulayan temel alınan Windows PowerShell cmdlet'leri için bu kaynakları eşleme işlemleri uyan bir XML dosyası oluşturarak her bir kaynak için [kaynak eşleme şeması](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="15653-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="15653-104">XML dosyası, istemci tarafından kaynaklara erişmek için kullanılan URL'leri de belirtir.</span><span class="sxs-lookup"><span data-stu-id="15653-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="15653-105">URL'lere Mappng kaynakları</span><span class="sxs-lookup"><span data-stu-id="15653-105">Mappng resources to URLs</span></span>

<span data-ttu-id="15653-106">XML dosyasının ilk bölümü bunlara erişmek için kullanılan URL'leri MOF şema dosyasında tanımlanan kaynakları eşler.</span><span class="sxs-lookup"><span data-stu-id="15653-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="15653-107">Aşağıdaki örnek, bu eşlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="15653-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="15653-108">Eşleme cmdlet'lerinde CRUD işlemleri</span><span class="sxs-lookup"><span data-stu-id="15653-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="15653-109">Ardından CRUD için karşılık gelen cmdlet'leri belirtin (oluşturma, okuma, güncelleştirme ve silme) Destek kaynakları operations.</span><span class="sxs-lookup"><span data-stu-id="15653-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="15653-110">Yönetim odata'da [kaynak eşleme şeması](./resource-mapping-schema.md), CRUD işlemleri şu şekilde eşlenir.</span><span class="sxs-lookup"><span data-stu-id="15653-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="15653-111">CRUD komutu</span><span class="sxs-lookup"><span data-stu-id="15653-111">CRUD command</span></span>|<span data-ttu-id="15653-112">XML öğesi</span><span class="sxs-lookup"><span data-stu-id="15653-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="15653-113">Oluşturma</span><span class="sxs-lookup"><span data-stu-id="15653-113">Create</span></span>|<span data-ttu-id="15653-114">Oluşturma</span><span class="sxs-lookup"><span data-stu-id="15653-114">Create</span></span>|
|<span data-ttu-id="15653-115">Okuma</span><span class="sxs-lookup"><span data-stu-id="15653-115">Read</span></span>|<span data-ttu-id="15653-116">Sorgu</span><span class="sxs-lookup"><span data-stu-id="15653-116">Query</span></span>|
|<span data-ttu-id="15653-117">Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="15653-117">Update</span></span>|<span data-ttu-id="15653-118">Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="15653-118">Update</span></span>|
|<span data-ttu-id="15653-119">Sil</span><span class="sxs-lookup"><span data-stu-id="15653-119">Delete</span></span>|<span data-ttu-id="15653-120">Sil</span><span class="sxs-lookup"><span data-stu-id="15653-120">Delete</span></span>|

<span data-ttu-id="15653-121">Aşağıdaki örnek, üzerinde oluşturma, okuma ve güncelleştirme işlemleri için eşlemeleri gösterir. `Service` kaynak.</span><span class="sxs-lookup"><span data-stu-id="15653-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="15653-122">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="15653-122">See Also</span></span>

[<span data-ttu-id="15653-123">Management OData web hizmeti için MOF şema dosyası yazma</span><span class="sxs-lookup"><span data-stu-id="15653-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="15653-124">Kaynak Eşleme Şeması</span><span class="sxs-lookup"><span data-stu-id="15653-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="15653-125">Management OData Web hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="15653-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)