---
title: Visual Studio code'da ISE deneyimi çoğaltma
description: Visual Studio code'da ISE deneyimi çoğaltma
ms.date: 08/06/2018
ms.openlocfilehash: 0ac38985a842a0dfc6118d0ae7116d12e1579daf
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655538"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Visual Studio code'da ISE deneyimi çoğaltma

VSCode için PowerShell uzantısı tam özellik eşliği PowerShell ISE ile arama değildir, ancak özellikler mevcuttur VSCode deneyimi ISE kullanıcılar için daha doğal hale getirmek için bir yerde.

Bu belge, kullanıcı deneyimini ISE'ye kıyasla biraz daha tanıdık yapmak için VSCode yapılandırabileceğiniz listesi ayarları dener.

## <a name="key-bindings"></a>Tuş bağlamaları

| İşlev                              | ISE bağlama                  | VSCode bağlama                              |
| ----------------                      | -----------                  | --------------                              |
| Kesme ve hata ayıklayıcı kesme          | <kbd>CTRL</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Geçerli satır ve vurgulanan metin yürütün | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Kullanılabilir kod parçacıkları listesi               | <kbd>CTRL</kbd>+<kbd>J</kbd> | <kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Özel anahtar bağlamaları

Yapabilecekleriniz [kendi tuş bağlamaları yapılandırma](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) de VSCode içinde.

## <a name="tab-completion"></a>Sekme tamamlama

Daha fazla ISE benzeri sekme tamamlamayı etkinleştirmek için bu ayarı ekleyin:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Bu ayar, doğrudan VSCode (yerine uzantısında) eklendi. Davranışını VSCode tarafından doğrudan belirlenir ve uzantısı tarafından değiştirilemez.

## <a name="no-focus-on-console-when-executing"></a>Hiçbir yürütülürken konsol odaklanır

İle yürütürken odağı düzenleyiciye tutmak <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Varsayılan değer `true` erişilebilmesi için.

## <a name="dont-start-integrated-console-on-startup"></a>Tümleşik bir konsol başlangıçta başlatma

Başlatma sırasında tümleşik bir konsol durdurmak için aşağıdakileri ayarlayın:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Arka plan PowerShell işlem hala sağlayan bu yana IntelliSense, kod analizi, sembol gezintisini vb. başlar. Ancak, konsolda gösterilmez.

## <a name="assume-files-are-powershell-by-default"></a>Dosyalar varsayılan olarak PowerShell olduğu varsayılır

Yeni/adsız dosyaları hale getirmek için varsayılan PowerShell kaydedin:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Renk şeması

ISE Temalar sayısı ISE gibi çok daha düzenleyiciniz VSCode için kullanılabilir.

İçinde [komut paleti] türü `theme` almak için `Preferences: Color Theme` basın <kbd>Enter</kbd>.
Aşağı açılan listesinde seçin `PowerShell ISE`.

Bu tema ayarlarla ayarlayabilirsiniz:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>PowerShell komut Gezgini

Çalışması sayesinde [ @corbob ](https://github.com/corbob), kendi komut explorer'ın beginnings PowerShell uzantısına sahiptir.

İçinde [komut paleti], girin `PowerShell Command Explorer` basın <kbd>Enter</kbd>.

## <a name="open-in-the-ise"></a>ISE Aç

Yine de ISE'de bir dosyayı açmaya isteyen gerekmesi halinde kullanabileceğiniz <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Diğer kaynaklar

- 4sysops sahip [harika bir makale](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) VSCode ISE gibi daha fazla olacak şekilde yapılandırma.
- Mike F Robbins sahip [harika bir gönderi](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) VSCode ayarlama.
- PowerShell sahip öğrenin [yukarı mükemmel bir yazma](https://www.learnpwsh.com/setup-vs-code-for-powershell/) VSCode Forms'dan kurulumu için PowerShell.

## <a name="more-settings"></a>Daha fazla ayar

ISE kullanıcılar için daha tanıdık gelmeli VSCode yapmak için daha fazla şekilde biliyorsanız, bu belge için katkıda bulunur. Aradığınız bir uyumluluk yapılandırma yoktur ancak bunu etkinleştirmek için herhangi bir şekilde bulunamıyor [bir sorun açın](https://github.com/PowerShell/vscode-powershell/issues/new/choose) hemen isteyin!

Her zaman çekme istekleri ve Katkıları da kabul olmaktan mutluluk duyarız!

## <a name="vscode-tips"></a>VSCode ipuçları

### <a name="command-palette"></a>Komut paleti

<kbd>F1</kbd> veya <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Kaydırma</kbd>+<kbd>P</kbd> macOS üzerinde)

VSCode içinde komut yürütmenin kurmanızı sağlar.
Daha fazla bilgi için [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Komut paleti]: #command-palette
