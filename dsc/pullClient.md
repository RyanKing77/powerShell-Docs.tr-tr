---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC çekme istemci ayarlama
ms.openlocfilehash: 4c56671313b93cc12ce9460ce41e1710e0d6a526
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a>DSC çekme istemci ayarlama

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusuna (Windows özelliği *DSC hizmet*) vardır ancak desteklenen bir bileşen Windows Server'ın yeni özellikleri veya yetenekleri sunmak için herhangi bir plan vardır. Geçiş başlamak için önerilen yönetilen istemcilere [Azure Otomasyonu DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda ötesinde özellikler içerir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Çekme modunu kullanacak şekilde söylediyse ve URL veya dosya konumuna yapılandırmaları ve kaynakları almak için çekme sunucunun başvurabilirsiniz ve rapor verilerini göndermelisiniz burada verilen her hedef düğüme sahiptir.

Aşağıdaki konularda, çekme istemcilerini ayarlama açıklanmaktadır:

* [Yapılandırma adlarını kullanarak çekme istemcisi ayarlama](pullClientConfigNames.md)
* [Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md)

> **Not**: Bu konular PowerShell 5.0 için geçerlidir. Çekme istemci PowerShell 4. 0 olarak ayarlamak için bkz: [PowerShell 4. 0 ' yapılandırması kimliği kullanan bir çekme istemci ayarlama](pullClientConfigID4.md).