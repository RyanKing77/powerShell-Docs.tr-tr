---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Yerleşik durum yapılandırma kaynakları Linux için istenen"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Yerleşik durum yapılandırma kaynakları Linux için istenen

Bir PowerShell istenen durum yapılandırması (DSC) komut dosyası yazmak için kullanabileceğiniz bir yapı taşları kaynaklardır. Linux için DSC kaynakları dosyaları ve klasörleri, paketler, ortam değişkenleri ve hizmetler ve işlemler gibi yapılandırma için yerleşik bir işlevi bir dizi birlikte gönderilir.

## <a name="built-in-resources"></a>Yerleşik kaynakları 

Aşağıdaki tabloda, bu kaynakları ve ayrıntılı olarak açıklayan konulara bağlantılar listesini sağlar.

* [nxArchive kaynak](lnxArchiveResource.md)--belirli bir yola Arşivi (.tar, .zip) dosyalarını açmak için bir mekanizma sağlar.
* [nxEnvironment kaynak](lnxEnvironmentResource.md)--hedef düğümleri ortam değişkenlerini yönetir. 
* [nxFile kaynak](lnxFileResource.md)--yönetir Linux dosyaları ve dizinleri. 
* [nxFileLine kaynak](lnxFileLineResource.md)--Linux dosyasına tek tek satır yönetir. 
* [nxGroup kaynak](lnxGroupResource.md)--yerel Linux grupları yönetir. 
* [nxPackage kaynak](lnxPackageResource.md)--Linux düğümleri paketleri yönetir.
* [nxScript kaynak](lnxScriptResource.md)--hedef düğümleri üzerinde komut dosyaları çalıştırır.
* [nxService kaynak](lnxServiceResource.md)--yönetir Linux Hizmetleri (Daemon).
* [nxSshAuthorizedKeys kaynak](lnxSshAuthorizedKeysResource.md)--ortak ssh anahtarları Linux kullanıcı için yönetir. 
* [nxUser kaynak](lnxUserResource.md)--yerel Linux kullanıcıları yönetir. 
  
