---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "ISE nesne modeli hiyerarşisi"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>ISE nesne modeli hiyerarşisi
Bu konu, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) parçası olan nesne gösterir. Windows PowerShell ISE Windows PowerShell 3.0 ve Windows PowerShell 4.0 dahil edilir. Nesne tanımlayan sınıfının başvuru belgeleri için uygulamanız için bir nesne'ı tıklatın.

## <a name="psise-object"></a>$psISE nesnesi

**$PsISE** nesne [kök nesnesi](The-ObjectModelRoot-Object.md) Windows PowerShell ISE nesne hiyerarşisinin.
En üst düzeyinde bulunan, aşağıdaki nesneleri kullanılabilir komut dosyası için hale getirir:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

**$PsISE.CurrentFile** nesnesidir örneği [ISEFile](The-ISEFile-Object.md) sınıfı.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

**$PsISE.CurrentPowerShellTab** nesnesidir örneği [PowerShellTab](The-PowerShellTab-Object.md) sınıfı.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

**$PsISE.CurrentVisibleHorizontalTool** nesnesidir örneği [ISEAddOnTool](The-ISEAddOnTool-Object.md) sınıfı.
Şu anda yerleşik yüklü eklenti aracı Windows PowerShell ISE penceresi üst kenarına temsil eder.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

**$PsISE.CurrentVisibleHorizontalTool** nesnesidir örneği [ISEAddOnTool](The-ISEAddOnTool-Object.md) sınıfı.
Şu anda yerleşik yüklü eklenti aracı Windows PowerShell ISE penceresi sağ kenarı temsil eder.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

**$PsISE.Options** nesnesidir örneği [ISEOptions](The-ISEOptions-Object.md) sınıfı.
ISEOptions nesne çeşitli Windows PowerShell ISE ayarlarını temsil eder.
Microsoft.PowerShell.Host.ISE.ISEOptions sınıfının bir örneğidir.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

**$PsISE.PowerShellTabs** nesnesidir örneği [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) sınıfı.
Yerel bilgisayarda veya uzak bilgisayarlarda bağlı ortamları çalıştırmak kullanılabilir Windows PowerShell temsil eden tüm açık PowerShell sekmeleri koleksiyonudur. Koleksiyonda her üye bir örneğidir [PowerShellTab](The-PowerShellTab-Object.md) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell ISE nesne modeli komut dosyası oluşturma](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE nesne modeli başvurusu](Windows-PowerShell-ISE-Object-Model-Reference.md)
