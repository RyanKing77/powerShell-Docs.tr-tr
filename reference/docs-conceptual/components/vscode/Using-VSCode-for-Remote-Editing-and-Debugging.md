---
title: Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma
description: Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086688"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Uzaktan düzenleme ve hata ayıklama için Visual Studio Code’u kullanma

Bu işe ile ilgili bilgi sahibi olduğunuz, çalıştırabilir, hatırlayabilirsiniz `psedit file.ps1` dosyaları - yerel veya uzak - açmak için tümleşik konsoldan ISE'de sağ.

Bu özellik ayrıca ortaya çıkmıştır gibi PowerShell uzantısı VSCode için kullanıma sunulmuştur. Bu kılavuz, nasıl yapılacağı gösterilmektedir.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuz, olduğunu varsayar:

- Uzak Kaynak (örn: bir kapsayıcı bir VM) erişimi olmasını
- Bu ve ana makine üzerinde çalışan PowerShell
- VSCode ve VSCode için PowerShell uzantısı

Bu özellik, Windows PowerShell ve PowerShell Core üzerinde çalışır.

Bu özellik, uzak bir makinede WinRM, PowerShell Direct veya SSH üzerinden bağlanırken de çalışır. SSH kullanmak istediğiniz, ancak Windows kullanıyorsanız, kullanıma [SSH Win32 sürümünü](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Gidelim

Uzaktan düzenleme ve Azure'da çalışan bir Ubuntu VM my MacBook Pro, hata ayıklama aracılığıyla bu bölümde adım geçireceğiz. Ben Windows, kullanmıyor olabilir ancak **işlemi benzerdir**.

### <a name="local-file-editing-with-open-editorfile"></a>Yerel dosya açık EditorFile ile düzenleme

PowerShell uzantısıyla VSCode çalışmaya ve PowerShell tümleştirilmiş bir konsol açıldı, biz yazabilirsiniz `Open-EditorFile foo.ps1` veya `psedit foo.ps1` yerel foo.ps1 dosyanızı doğrudan düzenleyicide açın.

![Açık EditorFile foo.ps1 yerel olarak çalışır](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 önceden var olmalıdır.

Burada, şunları yapabiliriz:

cilt payını için kesme noktaları ekleyebilirsiniz ![kanalını için kesme noktası ekleme](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

ve PowerShell komut dosyası hata ayıklamak için F5'e basın.
![Yerel PowerShell betik hata ayıklama](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Hata ayıklarken hata ayıklama konsol ile etkileşemeyebilirsiniz, sol tarafta, hata ayıklama araçları diğer standart kapsam içinde değişkenlere göz atın.

### <a name="remote-file-editing-with-open-editorfile"></a>Uzak dosya açık EditorFile ile düzenleme

Şimdi düzenleme ve hata ayıklama uzak dosya geçelim. Adımlar neredeyse aynıdır, tek şey ihtiyacımız öncelikle-uzak sunucuya bizim PowerShell oturumu girin.

Bunu yapmak için bir cmdlet için yoktur. Çağrıldığı `Enter-PSSession`.

Cmdlet'ini aşağı watered açıklaması verilmiştir:

- `Enter-PSSession -ComputerName foo` WinRM aracılığıyla bir oturumu başlatır
- `Enter-PSSession -ContainerId foo` ve `Enter-PSSession -VmId foo` PowerShell Direct aracılığıyla bir oturumu başlatın
- `Enter-PSSession -HostName foo` SSH aracılığıyla bir oturumu başlatır

Daha fazla bilgi için `Enter-PSSession`, belgelere göz atın [burada](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Azure'da bir Ubuntu sanal makinesi için macOS göstereceğim bu yana miyim uzaktan iletişim için SSH kullanacaklardır.

İlk olarak, tümleşik konsolunda bizim Enter-PSSession çalıştıralım. Oturumda çünkü olduğunuz anlarsınız `[something]` isteminiz solunda gösterilir.

![Enter-PSSession çağrısı](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Biz bir yerel komut dosyası düzenleme yaptığınız gibi Burada, uygulanacak adımlar yapabiliriz.

1. Çalıştırma `Open-EditorFile test.ps1` veya `psedit test.ps1` uzak açmak için `test.ps1` dosya ![açık-EditorFile test.ps1 dosyası](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Dosya/set kesme noktaları Düzenle ![düzenleme, kesme noktaları ayarlama](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Uzak dosyanın (F5) hata ayıklamayı Başlat

![Uzak dosyanın hata ayıklama](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Tüm İşte bu kadar kolay! Bu kılavuz uzak hata ayıklama ve düzenleme VSCode içinde PowerShell hakkında sorular Temizle'kurmak Yardım umuyoruz.

Herhangi bir sorun varsa, sorunları açmak buraya dönebilirsiniz [GitHub deposunda](http://github.com/powershell/vscode-powershell).
