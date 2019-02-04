---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISE Nesne Modeli Hiyerarşisi
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683775"
---
# <a name="the-ise-object-model-hierarchy"></a>ISE Nesne Modeli Hiyerarşisi

Bu konu, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) kapsamındaki nesne hiyerarşisini gösterir.
Windows PowerShell 3.0 ve Windows PowerShell 4.0, Windows PowerShell ISE dahildir.
Bir nesne tanımlayan nesne sınıfı için başvuru belgeleri için almak için tıklayın.

## <a name="psise-object"></a>$psISE Object

**$PsISE** nesnedir [kök nesnesi](The-ObjectModelRoot-Object.md) Windows PowerShell ISE nesne hiyerarşisi.
En üst düzeyinde bulunan, aşağıdaki nesneler kullanılabilir komut dosyası için getirir:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

**$PsISE.CurrentFile** nesnedir örneği [Isefile](The-ISEFile-Object.md) sınıfı.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

**$PsISE.CurrentPowerShellTab** nesnedir örneği [PowerShellTab](The-PowerShellTab-Object.md) sınıfı.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

**$PsISE.CurrentVisibleHorizontalTool** nesnedir örneği [Iseaddontool](The-ISEAddOnTool-Object.md) sınıfı.
Windows PowerShell ISE penceresi üst kenarına şu anda sabitlenmiş yüklü eklenti aracını temsil eder.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

**$PsISE.CurrentVisibleHorizontalTool** nesnedir örneği [Iseaddontool](The-ISEAddOnTool-Object.md) sınıfı.
Windows PowerShell ISE penceresi sağ kenarına şu anda sabitlenmiş yüklü eklenti aracını temsil eder.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

**$PsISE.Options** nesnedir örneği [Iseoptions](The-ISEOptions-Object.md) sınıfı.
Iseoptions nesnesi, çeşitli Windows PowerShell ISE ayarlarını temsil eder.
Microsoft.PowerShell.Host.ISE.ISEOptions sınıfının bir örneğidir.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

**$PsISE.PowerShellTabs** nesnedir örneği [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) sınıfı.
Yerel bilgisayarda veya uzak bilgisayarlarda bağlı ortamlarda çalıştırmanızı kullanılabilir Windows PowerShell temsil eden tüm açık PowerShell sekmeleri koleksiyonudur.
Koleksiyonda her üye örneğidir [PowerShellTab](The-PowerShellTab-Object.md) sınıfı.

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE betik oluşturma nesne modelinin amacı](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE Nesne Modeli Hiyerarşisi](The-ISE-Object-Model-Hierarchy.md)