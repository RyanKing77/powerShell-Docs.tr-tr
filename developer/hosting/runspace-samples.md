---
title: Çalışma örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082745"
---
# <a name="runspace-samples"></a>Çalışma Alanı Örnekleri

Bu bölüm, zaman uyumlu ve zaman uyumsuz olarak komutlarını çalıştırmak için çalışma alanları farklı türde kullanmayı gösteren örnek kodu içerir. Microsoft Visual Studio, bir konsol uygulaması oluşturun ve ardından kodu bu bölümdeki konular ana uygulamanıza kopyalamak için kullanabilirsiniz.

## <a name="in-this-section"></a>Bu Bölümde

> [!NOTE]
> Özel ana bilgisayar arabirimler uygulamalarını barındırmak için bkz [özel konak örnekleri](./custom-host-samples.md).

 [Runspace01 örnek](./runspace01-sample.md) Bu örnek nasıl kullanılacağını gösterir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) çalıştırılacak sınıfı [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet'i zaman uyumlu olarak ve çıktısını bir konsolda görüntüleme pencere.

 [Runspace02 örnek](./runspace02-sample.md) Bu örnek nasıl kullanılacağını gösterir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) çalıştırılacak sınıfı [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) ve [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet'leri zaman uyumlu olarak. Sonuçları aşağıdaki komutlardan birini kullanarak görüntülenen bir [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) denetimi.

 [Runspace03 örnek](./runspace03-sample.md) Bu örnek nasıl kullanılacağını gösterir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) zaman uyumlu olarak bir betik çalıştırmak için sınıf ve sonlandırıcı olmayan hatalara nasıl ele alınacağını. Betik işlem adları listesini alır ve ardından bu işlemleri alır. Komut dosyası çalıştırılırken oluşturulan sonlandırmayan hatalar dahil olmak üzere betik sonuçlarını konsol penceresinde görüntülenir.

 [Runspace04 örnek](./runspace04-sample.md) Bu örnek nasıl kullanılacağını gösterir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) komutlarını çalıştırmak için sınıf ve komutlarını çalıştırırken oluşturulan catch Sonlandırıcı hataları. İki komutu çalıştırın ve son komut, geçerli olmayan bir parametre bağımsız değişkeni olarak geçirilir. Sonuç olarak hiçbir nesne döndürülür ve bir sonlandırma hatası oluşturulur.

 [Runspace05 örnek](./runspace05-sample.md) Bu örnek, bir ek bileşenine ekleme işlemi açıklanır bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) böylece çalışma açıldığında, ek cmdlet kullanılabilir nesne. Ek bir Get-Proc cmdlet sağlar (tarafından tanımlanan [GetProcessSample01 örnek](../cmdlet/getprocesssample01-sample.md)) kullanarak zaman uyumlu olarak çalıştırılan bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.

 [Runspace06 örnek](./runspace06-sample.md) Bu örnek, bir modüle ekleneceği gösterilmiştir bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) modülü bir çalışma açıldığında yüklenmesi nesne. Get-Proc cmdlet modülü sağlar (tarafından tanımlanan [GetProcessSample02 örnek](../cmdlet/getprocesssample02-sample.md)) kullanarak zaman uyumlu olarak çalıştırılan bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.

 [Runspace07 örnek](./runspace07-sample.md) Bu örnek, bir çalışma alanı oluşturun ve ardından bu çalışma alanı iki cmdlet kullanarak zaman uyumlu olarak çalışacak şekilde nasıl gösterir. bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.

 [Runspace08 örnek](./runspace08-sample.md) Bu örnek, komut ve bağımsız değişkenler için işlem hattı ekleneceği gösterilmiştir bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne ve zaman uyumlu olarak komutları çalıştırmayı öğrenin.

 [Runspace09 örnek](./runspace09-sample.md) nasıl işlem hattı için bir komut dosyası eklemek Bu örnek gösterir bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne ve komut zaman uyumsuz olarak çalıştırmayı öğrenin. Olaylar, komut çıktısı işlemek için kullanılır.

 [Runspace10 örnek](./runspace10-sample.md) Bu örnek, bir varsayılan ilk oturum durumu oluşturma işlemi gösterilmektedir bir cmdlet'e ekleme [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), kullanan bir çalışma alanı oluşturma ilk oturum durumu ve komutu çalıştırmak amacıyla kullanmak üzere nasıl bir [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) nesne.

 [Runspace11 örnek](./runspace11-sample.md) bu nasıl kullanılacağını gösterir [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) var olan bir cmdlet'i çağırır, ancak kullanılabilir parametreleri kümesini sınırlayan bir ara sunucu komutu oluşturmak için sınıf. Ara sunucu komutunu kısıtlı bir çalışma alanı oluşturmak için kullanılan bir ilk oturum durumunu daha sonra eklenir. Bu, kullanıcının yalnızca ara sunucu komutu cmdlet işlevselliğini erişebileceği anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz:
