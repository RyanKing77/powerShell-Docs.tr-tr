---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: Yerleşik durum yapılandırma kaynakları Linux için istenen
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="851f3-103">Yerleşik durum yapılandırma kaynakları Linux için istenen</span><span class="sxs-lookup"><span data-stu-id="851f3-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="851f3-104">Bir PowerShell istenen durum yapılandırması (DSC) komut dosyası yazmak için kullanabileceğiniz bir yapı taşları kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="851f3-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="851f3-105">Linux için DSC kaynakları dosyaları ve klasörleri, paketler, ortam değişkenleri ve hizmetler ve işlemler gibi yapılandırma için yerleşik bir işlevi bir dizi birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="851f3-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="851f3-106">Yerleşik kaynaklar</span><span class="sxs-lookup"><span data-stu-id="851f3-106">Built-in resources</span></span>

<span data-ttu-id="851f3-107">Aşağıdaki tabloda, bu kaynakları ve ayrıntılı olarak açıklayan konulara bağlantılar listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="851f3-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="851f3-108">[nxArchive kaynak](lnxArchiveResource.md)--belirli bir yola Arşivi (.tar, .zip) dosyalarını açmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="851f3-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="851f3-109">[nxEnvironment kaynak](lnxEnvironmentResource.md)--hedef düğümleri ortam değişkenlerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="851f3-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="851f3-110">[nxFile kaynak](lnxFileResource.md)--yönetir Linux dosyaları ve dizinleri.</span><span class="sxs-lookup"><span data-stu-id="851f3-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="851f3-111">[nxFileLine kaynak](lnxFileLineResource.md)--Linux dosyasına tek tek satır yönetir.</span><span class="sxs-lookup"><span data-stu-id="851f3-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="851f3-112">[nxGroup kaynak](lnxGroupResource.md)--yerel Linux grupları yönetir.</span><span class="sxs-lookup"><span data-stu-id="851f3-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="851f3-113">[nxPackage kaynak](lnxPackageResource.md)--Linux düğümleri paketleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="851f3-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="851f3-114">[nxScript kaynak](lnxScriptResource.md)--hedef düğümleri üzerinde komut dosyaları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="851f3-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="851f3-115">[nxService kaynak](lnxServiceResource.md)--yönetir Linux Hizmetleri (Daemon).</span><span class="sxs-lookup"><span data-stu-id="851f3-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="851f3-116">[nxSshAuthorizedKeys kaynak](lnxSshAuthorizedKeysResource.md)--ortak ssh anahtarları Linux kullanıcı için yönetir.</span><span class="sxs-lookup"><span data-stu-id="851f3-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="851f3-117">[nxUser kaynak](lnxUserResource.md)--yerel Linux kullanıcıları yönetir.</span><span class="sxs-lookup"><span data-stu-id="851f3-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>