---
title: HelpInfo XML örnek dosyası | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 11804db56ec47554e82f04fe6954920ad9577370
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082439"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="c6a56-102">HelpInfo XML Örnek Dosya</span><span class="sxs-lookup"><span data-stu-id="c6a56-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="c6a56-103">Bu konuda bir örnek genellikle "HelpInfo XML dosyası." olarak bilinen bir iyi biçimlendirilmiş güncelleştirilebilir bilgi dosyasının görüntüler</span><span class="sxs-lookup"><span data-stu-id="c6a56-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="c6a56-104">Bu örnek dosyasında UI kültürü öğeleri UI kültürü adına göre alfabetik sıraya göre düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="c6a56-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="c6a56-105">Alfabetik sıralama en iyi uygulamadır, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c6a56-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="c6a56-106">HelpInfo XML Örnek Dosya</span><span class="sxs-lookup"><span data-stu-id="c6a56-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>http://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```