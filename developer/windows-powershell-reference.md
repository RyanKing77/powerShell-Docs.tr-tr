---
title: Windows PowerShell başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: 48b2b2b9ab2a39cf185ed54bcfa99d46562e13b6
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733743"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell Başvurusu

Windows PowerShell yönetici otomasyonu için tasarlanan Microsoft .NET Framework bağlı ortamıdır. Windows PowerShell komutları oluşturma çözümleri oluşturma ve grafik kullanıcı arabirimi tabanlı yönetim araçları oluşturmak için yeni bir yaklaşım sağlar.

Windows PowerShell komutların yürütülmesini sistem kaynaklarının yönetimini otomatikleştirmek bir Sistem Yöneticisi sağlar doğrudan ya da betikler aracılığıyla.

## <a name="developer-audience"></a>Geliştirici hedef kitle

Windows PowerShell Yazılım Geliştirme Seti (SDK), Windows PowerShell tarafından sağlanan API'leri hakkında başvuru bilgisi gerektiren komut geliştiriciler için yazılır. Komut geliştiriciler Windows PowerShell komutları hem de Windows PowerShell tarafından gerçekleştirilen görevleri genişleten sağlayıcıları oluşturmak için kullanın.

## <a name="windows-powershell-resources"></a>Windows PowerShell kaynakları

Windows PowerShell SDK ek olarak, aşağıdaki kaynakları daha fazla bilgi sağlar.

[Windows PowerShell ile çalışmaya başlama](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Windows PowerShell tanıtır: dil, cmdlet'ler, sağlayıcıları ve nesnelerin kullanın.

[Bir Windows PowerShell modülü yazma](./module/writing-a-windows-powershell-module.md) bilgi ve örnekler Yöneticiler, betik geliştiriciler ve paketini ve Windows PowerShell modüllerini kullanarak Windows PowerShell çözümlerini dağıtmak için gereken cmdlet'i geliştiriciler için sağlar.

[Bir Windows PowerShell cmdlet'i yazma](./cmdlet/writing-a-windows-powershell-cmdlet.md) cmdlet'leri tasarlama program yöneticileri ve cmdlet kod uygulama geliştiriciler için bilgi ve kod örnekleri sağlar.

[Windows PowerShell ekibi blogu](https://blogs.msdn.microsoft.com/PowerShell/) öğrenmek ve diğer Windows PowerShell kullanıcıları ile çalışmak için en iyi bir kaynaktır. Windows PowerShell ekibi blogu okuyun ve ardından Windows PowerShell kullanıcı forumu (microsoft.public.windows.powershell) katılın. Diğer Windows PowerShell blogları ve kaynakları bulmak için Windows Live Search kullanın. Uzmanlığınızı geliştirirken, serbestçe fikirlerinizi katkıda bulunur.

[PowerShell Modül Tarayıcısı](/powershell/module/) komut satırı Yardım konuları en son sürümlerini sağlar.

## <a name="class-libraries"></a>Sınıf kitaplıkları

[System.Management.Automation](/dotnet/api/System.Management.Automation) kök ad alanı Windows PowerShell için bu ad alanıdır. Bu sınıflar, numaralandırmalar ve özel cmdlet'leri uygulamak için gereken arabirimler içerir. Özellikle, [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) hangi tüm cmdlet'inden gerekir türetilmiş sınıflar temel sınıfı. Cmdlet'ler hakkında daha fazla bilgi için bkz.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) bu ad alanı, sınıflar, numaralandırmalar ve bir Windows PowerShell sağlayıcısını uygulamak için gereken arabirimler içerir. Özellikle, [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) hangi tüm Windows Powershell'den sağlayıcısı gerekir türetilmiş sınıflar temel sınıfı.

[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) bu ad alanı cmdlet'lerini ve Windows PowerShell tarafından uygulanan sağlayıcıları için sınıflar içerir. Benzer şekilde, oluşturmanız önerilir bir *adınız*. Uygulamanız bu cmdlet'leri için ad alanı komutları.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) bu ad alanı, sınıflar, numaralandırmalar ve Windows PowerShell ve kullanıcı arasındaki etkileşimi tanımlamak için cmdlet'i kullanan arabirimleri içerir.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) bu ad alanı diğer ad alanı sınıfları tarafından kullanılan temel sınıflar içerir. Örneğin, [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) için temel sınıfı [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) sınıfı.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) bu ad alanı, sınıflar, numaralandırmalar ve bir Windows PowerShell çalışma alanı oluşturmak için kullandığınız arabirimlerini içerir. Bu bağlamda, bir Windows PowerShell çalışma, bir veya daha fazla işlem hattı Windows PowerShell cmdlet'leri çağırma bağlamdır. Diğer bir deyişle, cmdlet'ler, bir Windows PowerShell çalışma bağlamında çalışır. Daha fazla bilgi aboutWindows için PowerShell çalışma alanları, bkz: [Windows PowerShell çalışma alanları](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
