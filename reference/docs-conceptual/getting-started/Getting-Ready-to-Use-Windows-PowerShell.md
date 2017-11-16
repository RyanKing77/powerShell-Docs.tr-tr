---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: "Windows PowerShell kullanmaya başlama"
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: de09c74e938f11a130864b1620d6c169006a27be
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2017
---
# <a name="getting-ready-to-use-windows-powershell"></a>Windows PowerShell kullanmaya başlama
Windows PowerShell yüklenmiş ve başlatılmış olduğundan, aşağıdaki kurulum seçenekleri göz önünde bulundurun. Herhangi bir zamanda bu görevleri gerçekleştirebilirsiniz.

- **Yardım dosyalarını yükleyin.** Windows PowerShell 3. 0 ' içerdiği cmdlet Yardım dosyalarıyla gelmeyen. Ancak, kullanabileceğiniz [Update-Help](/powershell/module/microsoft.powershell.core/update-help) bilgisayarınızda en yeni Yardım dosyalarını indirmek ve yüklemek için cmdlet'i. Dosyalar yüklendiğinde, kullanabileceğiniz [Get-Help](/powershell/module/microsoft.powershell.core/get-help) komut satırında sağa görüntülenecek cmdlet'i. Daha fazla bilgi için bkz: [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

    Yardım dosyalarını yüklememeye karar verirseniz, çevrimiçi Yardım konuları hala okuyabilir. Tüm cmdlet Yardım konusunun çevrimiçi sürümünü bulmak için şunu yazın: `Get-Help <CmdletName> -Online`. Windows PowerShell Yardım konularına bakın göz atmak için [PowerShell belgelerine](/powershell/scripting).

- **Komut dosyalarını çalıştırın.** Windows PowerShell güvenli tutmak için Windows PowerShell varsayılan yürütme ilkesi olan **kısıtlı**. Bu ilke cmdlet'leri ancak değil komut dosyaları çalıştırmanıza olanak tanır. Komut dosyaları çalıştırmak için kullandığınız [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) yürütme ilkesini değiştirmek için cmdlet **AllSigned** veya **RemoteSigned**. Yalnızca bilgisayarda Administrators grubunun üyeleri bu cmdlet'i çalıştırabilirsiniz. Daha fazla bilgi için bkz: [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Uzaktan iletişimini etkinleştirin.** Sistem, diğer bilgisayarlarda uzak komutları çalıştırmak zaten yapılandırıldı. Windows Server 2012 R2 ve Windows Server 2012 üzerinde sistem de yapılandırılmış uzak komutları, yani almak için yerel bilgisayarda Uzak komutları çalıştırmak üzere başka bilgisayarlar izin vermek için. Diğer uzak komutları almak için Windows sürümlerini çalıştıran bilgisayarları etkinleştirmek için çalıştırın [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) uzaktan yönetmek istediğiniz bilgisayarda cmdlet'i. Yalnızca bilgisayarda Administrators grubunun üyeleri bu cmdlet'i çalıştırabilirsiniz. Daha fazla bilgi için bkz: [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    Not: uzaktan Windows PowerShell 2.0 çalıştıran bir bilgisayarda etkinleştirilirse, Windows Management Framework 3.0 yüklendikten sonra remoting hala etkin. Ancak, Windows Server 2008'de (değil Windows Server 2008 R2), uzak Windows Management Framework 3.0 yüklendikten sonra yeniden etkinleştirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz:
- [Windows PowerShell'i yükleme](../setup/Installing-Windows-PowerShell.md)
- [Windows PowerShell'i başlatma](/powershell/scripting/setup/starting-windows-powershell)

