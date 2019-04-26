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
# <a name="helpinfo-xml-schema"></a>HelpInfo XML Şeması

Bu konu, güncelleştirilebilir Yardımı bilgi dosyaları, genellikle "HelpInfo XML dosyaları" bilinen için XML Şeması içerir.

## <a name="helpinfo-xml-schema"></a>HelpInfo XML Şeması

HelpInfo XML dosyaları, aşağıdaki XML şemasını temel alır.

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

## <a name="helpinfo-xml-elements"></a>HelpInfo XML öğeleri

HelpInfo XML dosyası aşağıdaki öğeleri içerir.

HelpContentURI CAB dosyaları modülü için Yardımı konumunu URI'sini içerir. URI, "http" veya "https" ile başlamalıdır. URI bir Internet konumu belirtmeniz gerekir, ancak CAB dosyası adı içermemesi gerekir. **HelpContentURI** değeri aynı olabilir veya farklı **HelpInfoURI** değeri.

SupportedUICultures modülü Yardım dosyaları tüm UI kültürü temsil eder. İçeren **UICulture** öğeleri, her biri bir dizi Yardım dosyası için belirtilen bir kullanıcı Arabirimi kültürünü modülünde temsil eder.

UICulture temsil eden bir dizi Yardım dosyası içinde belirtilen bir kullanıcı Arabirimi kültürünü modülü için. Ekleme bir **UICulture** Yardım dosyaları yazılır her UI kültürü için öğesi.

UICultureName Yardım dosyalarının yazıldığı UI kültürü için dil kodu içerir.

UICultureVersion "N1., 4 bölümde sürüm numarası içerir. N2. N3. N4 "UI kültürü Yardım CAB dosyasındaki sürümünü temsil eden biçimi. Bu sürüm numarası, yeni Yardım tarafından belirtilen kullanıcı Arabirimi kültürünü CAB dosyaları karşıya yüklediğiniz her artış **UICultureName**. Bu değeri hakkında daha fazla bilgi için "Sürüm sınıfta (Sistem)" MSDN bakın.