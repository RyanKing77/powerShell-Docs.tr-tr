---
title: Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma
description: Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263956"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma

Bu, işe ile ilgili bilgi sahibi olduğunuz, çalıştırabilir, hatırlayabilirsiniz `psedit file.ps1` dosyaları - yerel veya uzak - açmak için tümleşik konsoldan ISE'de sağ.

Bu özellik, VSCode için PowerShell uzantısı'nda da kullanılabilir. Bu kılavuz nasıl yapılacağını gösterir.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuz, olduğunu varsayar:

- Uzak Kaynak (örn: bir kapsayıcı bir VM) erişimi olmasını
- Bu ve ana makine üzerinde çalışan PowerShell
- VSCode ve VSCode için PowerShell uzantısı

Bu özellik, Windows PowerShell ve PowerShell Core üzerinde çalışır.

Bu özellik, uzak bir makinede WinRM, PowerShell Direct veya SSH üzerinden bağlanırken de çalışır. SSH kullanmak istediğiniz, ancak Windows kullanıyorsanız, kullanıma [SSH Win32 sürümünü](https://github.com/PowerShell/Win32-OpenSSH)!

> [!IMPORTANT]
> `Open-EditorFile` Ve `psedit` komutları yalnızca iş **PowerShell tümleştirilmiş bir konsol** VSCode için PowerShell uzantısı tarafından oluşturuldu.

## <a name="usage-examples"></a>Kullanım örnekleri

Bu örnekler, Azure'da çalışan düzenleme ve bir MacBook Pro Ubuntu sanal makinesi için hata ayıklama uzak gösterir. Windows üzerinde işlem aynıdır.

### <a name="local-file-editing-with-open-editorfile"></a>Yerel dosya açık EditorFile ile düzenleme

PowerShell uzantısıyla VSCode çalışmaya ve PowerShell tümleştirilmiş bir konsol açıldı, biz yazabilirsiniz `Open-EditorFile foo.ps1` veya `psedit foo.ps1` yerel foo.ps1 dosyanızı doğrudan düzenleyicide açın.

![Açık EditorFile foo.ps1 yerel olarak çalışır](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> Dosya `foo.ps1` zaten mevcut olmalıdır.

Burada, şunları yapabiliriz:

- Kesme noktası cilt payını için ekleyin

  ![kanalını için kesme noktası ekleme](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- PowerShell komut dosyası hata ayıklamak için F5'e basın.

  ![Yerel PowerShell betik hata ayıklama](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Hata ayıklarken hata ayıklama konsol ile etkileşemeyebilirsiniz, sol tarafta, hata ayıklama araçları diğer standart kapsam içinde değişkenlere göz atın.

### <a name="remote-file-editing-with-open-editorfile"></a>Uzak dosya açık EditorFile ile düzenleme

Şimdi düzenleme ve hata ayıklama uzak dosya geçelim. Adımlar neredeyse aynıdır, tek şey ihtiyacımız öncelikle-uzak sunucuya bizim PowerShell oturumu girin.

Bunu yapmak için bir cmdlet için yoktur. Çağrıldığı `Enter-PSSession`.

Cmdlet'ini aşağı watered açıklaması verilmiştir:

- `Enter-PSSession -ComputerName foo` WinRM aracılığıyla bir oturumu başlatır
- `Enter-PSSession -ContainerId foo` ve `Enter-PSSession -VmId foo` PowerShell Direct aracılığıyla bir oturumu başlatın
- `Enter-PSSession -HostName foo` SSH aracılığıyla bir oturumu başlatır

Daha fazla bilgi için belgelerine bakın [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

MacOS azure'daki bir Ubuntu sanal kullanacağız olduğundan, uzaktan iletişim için SSH kullanıyoruz.

İlk olarak, tümleşik konsolda Çalıştır `Enter-PSSession`. Uzak oturuma bağlı olduğunuz zaman `[<hostname>]` isteminiz soluna kadar gösterir.

![Enter-PSSession çağrısı](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Şimdi, biz bir yerel komut dosyasını düzenliyorsanız gibi aynı adımları yapabiliriz.

1. Çalıştırma `Open-EditorFile test.ps1` veya `psedit test.ps1` uzak açmak için `test.ps1` dosyası

  ![Açık-EditorFile test.ps1 dosyası](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Dosya/set kesme noktaları Düzenle

   ![düzenleme, kesme noktaları ayarlama](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Uzak dosyanın (F5) hata ayıklamayı Başlat

   ![Uzak dosyanın hata ayıklama](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Herhangi bir sorun varsa, sorunları açabileceğiniz [GitHub deposunu](https://github.com/powershell/vscode-powershell).
