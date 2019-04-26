---
title: HelpInfo XML Şeması | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082473"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="a2002-102">HelpInfo XML Şeması</span><span class="sxs-lookup"><span data-stu-id="a2002-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="a2002-103">Bu konu, güncelleştirilebilir Yardımı bilgi dosyaları, genellikle "HelpInfo XML dosyaları" bilinen için XML Şeması içerir.</span><span class="sxs-lookup"><span data-stu-id="a2002-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="a2002-104">HelpInfo XML Şeması</span><span class="sxs-lookup"><span data-stu-id="a2002-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="a2002-105">HelpInfo XML dosyaları, aşağıdaki XML şemasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="a2002-105">HelpInfo XML files are based on the following XML schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="a2002-106">HelpInfo XML öğeleri</span><span class="sxs-lookup"><span data-stu-id="a2002-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="a2002-107">HelpInfo XML dosyası aşağıdaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a2002-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="a2002-108">HelpContentURI CAB dosyaları modülü için Yardımı konumunu URI'sini içerir.</span><span class="sxs-lookup"><span data-stu-id="a2002-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="a2002-109">URI, "http" veya "https" ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2002-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="a2002-110">URI bir Internet konumu belirtmeniz gerekir, ancak CAB dosyası adı içermemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2002-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="a2002-111">**HelpContentURI** değeri aynı olabilir veya farklı **HelpInfoURI** değeri.</span><span class="sxs-lookup"><span data-stu-id="a2002-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="a2002-112">SupportedUICultures modülü Yardım dosyaları tüm UI kültürü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a2002-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="a2002-113">İçeren **UICulture** öğeleri, her biri bir dizi Yardım dosyası için belirtilen bir kullanıcı Arabirimi kültürünü modülünde temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a2002-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="a2002-114">UICulture temsil eden bir dizi Yardım dosyası içinde belirtilen bir kullanıcı Arabirimi kültürünü modülü için.</span><span class="sxs-lookup"><span data-stu-id="a2002-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="a2002-115">Ekleme bir **UICulture** Yardım dosyaları yazılır her UI kültürü için öğesi.</span><span class="sxs-lookup"><span data-stu-id="a2002-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="a2002-116">UICultureName Yardım dosyalarının yazıldığı UI kültürü için dil kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="a2002-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="a2002-117">UICultureVersion "N1., 4 bölümde sürüm numarası içerir. N2. N3. N4 "UI kültürü Yardım CAB dosyasındaki sürümünü temsil eden biçimi.</span><span class="sxs-lookup"><span data-stu-id="a2002-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="a2002-118">Bu sürüm numarası, yeni Yardım tarafından belirtilen kullanıcı Arabirimi kültürünü CAB dosyaları karşıya yüklediğiniz her artış **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="a2002-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="a2002-119">Bu değeri hakkında daha fazla bilgi için "Sürüm sınıfta (Sistem)" MSDN bakın.</span><span class="sxs-lookup"><span data-stu-id="a2002-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>