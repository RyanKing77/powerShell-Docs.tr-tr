---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: Yerleşik durum yapılandırma kaynakları Linux için istenen
ms.openlocfilehash: 77617b72584f39c46fc4b9eb67235378bbfc19aa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Yerleşik durum yapılandırma kaynakları Linux için istenen

Bir PowerShell istenen durum yapılandırması (DSC) komut dosyası yazmak için kullanabileceğiniz bir yapı taşları kaynaklardır. Linux için DSC kaynakları dosyaları ve klasörleri, paketler, ortam değişkenleri ve hizmetler ve işlemler gibi yapılandırma için yerleşik bir işlevi bir dizi birlikte gönderilir.

## <a name="built-in-resources"></a>Yerleşik kaynaklar

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