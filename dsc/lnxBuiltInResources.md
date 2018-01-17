---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Yerleşik durum yapılandırma kaynakları Linux için istenen"
ms.openlocfilehash: e268cb2ee8a246f18216b34e5e2a6d512f15e18c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
  
