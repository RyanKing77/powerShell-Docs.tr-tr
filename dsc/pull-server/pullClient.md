---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC çekme istemcisi ayarlama
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054263"
---
# <a name="setting-up-a-dsc-pull-client"></a>DSC çekme istemcisi ayarlama

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır. Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Çekme modu kullanmak için bir uyarıyla ve URL veya dosya konumuna yapılandırmaları ve kaynakları almak için çekme sunucusu başvurabilir ve raporu verileri gönderip burada verilen her hedef düğümü vardır.

Aşağıdaki konular, çekme istemcilerini ayarlama açıklanmaktadır:

* [Yapılandırma adlarını kullanarak çekme istemcisi ayarlama](pullClientConfigNames.md)
* [Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md)

> [!NOTE]
> Bu konular, PowerShell 5.0 için geçerlidir. PowerShell 4.0 çekme istemcisi ayarlama hakkında bilgi için bkz: [PowerShell 4. 0'yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID4.md).