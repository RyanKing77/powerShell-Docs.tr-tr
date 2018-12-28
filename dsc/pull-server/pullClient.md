---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC çekme istemcisi ayarlama
ms.openlocfilehash: b7cd6dc0087eb8368c5467df4c3c7266ed704451
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405685"
---
# <a name="setting-up-a-dsc-pull-client"></a>DSC çekme istemcisi ayarlama

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Çekme sunucusu (Windows özelliği *DSC hizmet*) ancak desteklenen bir bileşen Windows Server'ın yeni özellikler veya yetenekler sunmak için herhangi bir plan vardır. Geçişi başlıyor önerilir yönetilen istemcilere [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (Windows Server çekme sunucusunda dışında özellikler dahildir) veya topluluk çözümlerden birini listelenen [burada](pullserver.md#community-solutions-for-pull-service).

Çekme modu kullanmak için bir uyarıyla ve URL veya dosya konumuna yapılandırmaları ve kaynakları almak için çekme sunucusu başvurabilir ve raporu verileri gönderip burada verilen her hedef düğümü vardır.

Aşağıdaki konular, çekme istemcilerini ayarlama açıklanmaktadır:

* [Yapılandırma adlarını kullanarak çekme istemcisi ayarlama](pullClientConfigNames.md)
* [Yapılandırma kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID.md)

> **Not**: Bu konular, PowerShell 5.0 için geçerlidir. PowerShell 4.0 çekme istemcisi ayarlama hakkında bilgi için bkz: [PowerShell 4. 0'yapılandırma Kimliğini kullanarak çekme istemcisi ayarlama](pullClientConfigID4.md).