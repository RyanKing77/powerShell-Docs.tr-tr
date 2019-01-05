---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yerleşik kaynaklar için Linux Desired State Configuration
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048715"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Yerleşik kaynaklar için Linux Desired State Configuration

PowerShell Desired State Configuration (DSC) komut dosyası yazmak için kullanabileceğiniz bir yapı taşlarını kaynaklardır. Linux için DSC, yapılandırma dosyaları ve klasörleri, paketler, ortam değişkenleri ve hizmetler ve işlemler gibi kaynaklar için yerleşik bir işlevi bir dizi ile birlikte gelir.

## <a name="built-in-resources"></a>Yerleşik kaynaklar

Aşağıdaki tabloda, bu kaynakları ve bunların ayrıntılı olarak açıklayan konulara bağlantılar listesini sağlar.

* [nxArchive kaynağı](lnxArchiveResource.md)--belirli bir yola Arşivi (.tar, .zip) dosyaları açmak için bir mekanizma sağlar.
* [nxEnvironment kaynağı](lnxEnvironmentResource.md)--hedef düğümleri üzerindeki ortam değişkenlerini yönetir.
* [nxFile kaynağı](lnxFileResource.md)--yönetir Linux dosyalar ve dizinler.
* [nxFileLine kaynağı](lnxFileLineResource.md)--Linux dosyası ayrı satırlarda yönetir.
* [nxGroup kaynağı](lnxGroupResource.md)--yerel Linux yönetir.
* [nxPackage kaynağı](lnxPackageResource.md)--Linux düğümleri paketleri yönetir.
* [Kaynak nxScript](lnxScriptResource.md)--hedef düğümler üzerinde komut dosyalarını çalıştırır.
* [nxService kaynağı](lnxServiceResource.md)--yönetir Linux Hizmetleri (Daemon'ları).
* [nxSshAuthorizedKeys kaynağı](lnxSshAuthorizedKeysResource.md)--genel ssh anahtarları için Linux kullanıcı yönetir.
* [nxUser kaynağı](lnxUserResource.md)--yerel Linux kullanıcıları yönetir.