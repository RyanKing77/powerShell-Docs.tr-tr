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
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="0f933-103">Yerleşik kaynaklar için Linux Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="0f933-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="0f933-104">PowerShell Desired State Configuration (DSC) komut dosyası yazmak için kullanabileceğiniz bir yapı taşlarını kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="0f933-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="0f933-105">Linux için DSC, yapılandırma dosyaları ve klasörleri, paketler, ortam değişkenleri ve hizmetler ve işlemler gibi kaynaklar için yerleşik bir işlevi bir dizi ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="0f933-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="0f933-106">Yerleşik kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0f933-106">Built-in resources</span></span>

<span data-ttu-id="0f933-107">Aşağıdaki tabloda, bu kaynakları ve bunların ayrıntılı olarak açıklayan konulara bağlantılar listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f933-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="0f933-108">[nxArchive kaynağı](lnxArchiveResource.md)--belirli bir yola Arşivi (.tar, .zip) dosyaları açmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f933-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="0f933-109">[nxEnvironment kaynağı](lnxEnvironmentResource.md)--hedef düğümleri üzerindeki ortam değişkenlerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="0f933-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="0f933-110">[nxFile kaynağı](lnxFileResource.md)--yönetir Linux dosyalar ve dizinler.</span><span class="sxs-lookup"><span data-stu-id="0f933-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="0f933-111">[nxFileLine kaynağı](lnxFileLineResource.md)--Linux dosyası ayrı satırlarda yönetir.</span><span class="sxs-lookup"><span data-stu-id="0f933-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="0f933-112">[nxGroup kaynağı](lnxGroupResource.md)--yerel Linux yönetir.</span><span class="sxs-lookup"><span data-stu-id="0f933-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="0f933-113">[nxPackage kaynağı](lnxPackageResource.md)--Linux düğümleri paketleri yönetir.</span><span class="sxs-lookup"><span data-stu-id="0f933-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="0f933-114">[Kaynak nxScript](lnxScriptResource.md)--hedef düğümler üzerinde komut dosyalarını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0f933-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="0f933-115">[nxService kaynağı](lnxServiceResource.md)--yönetir Linux Hizmetleri (Daemon'ları).</span><span class="sxs-lookup"><span data-stu-id="0f933-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="0f933-116">[nxSshAuthorizedKeys kaynağı](lnxSshAuthorizedKeysResource.md)--genel ssh anahtarları için Linux kullanıcı yönetir.</span><span class="sxs-lookup"><span data-stu-id="0f933-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="0f933-117">[nxUser kaynağı](lnxUserResource.md)--yerel Linux kullanıcıları yönetir.</span><span class="sxs-lookup"><span data-stu-id="0f933-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>