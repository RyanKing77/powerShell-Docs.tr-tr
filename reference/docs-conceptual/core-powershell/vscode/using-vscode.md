# <a name="using-visual-studio-code-for-powershell-development"></a>PowerShell geliştirme için Visual Studio Code kullanma

Ek olarak [PowerShell ISE][ise], PowerShell Visual Studio kodda iyi desteklenen de.
Visual Studio Code PowerShell çekirdek için tüm platformlarda (Windows, macOS ve Linux) destekleniyorsa Ayrıca, işe PowerShell çekirdek ile desteklenmiyor

Visual Studio Code Windows PowerShell sürüm 5 ile Windows 10 veya yükleyerek kullanabilirsiniz [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) için alt düzey Windows OSs (örneğin Windows 8.1, vb.).

Başlamadan önce lütfen PowerShell sisteminizde bulunduğundan emin olun.
Windows, macOS ve Linux modern iş yükleri için bkz:

- [PowerShell çekirdek Linux'ta yükleme][install-pscore-linux]
- [PowerShell çekirdeği üzerinde macOS yükleme][install-pscore-macos]
- [Windows PowerShell çekirdek yükleniyor][install-pscore-windows]

Geleneksel Windows PowerShell iş yükleri için bkz: [Windows PowerShell'i yükleme][install-winps].

## <a name="editing-with-visual-studio-code"></a>Visual Studio Code ile düzenleme

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Visual Studio Code yükleme](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: yükleme yönergelerini izleyin [Linux üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/linux) sayfası

- **macOS**: yükleme yönergelerini izleyin [macOS üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/mac) sayfası

> [!IMPORTANT]
> MacOS üzerinde düzgün çalışması için OpenSSL PowerShell uzantısı yüklemeniz gerekir.
> Bunu yapmanın en kolay yolu yüklemektir [Homebrew](http://brew.sh/) ve ardından çalıştırın `brew install openssl`.
> VS Code şimdi yükleyebilirsiniz PowerShell uzantısı başarıyla.

- **Windows**: yükleme yönergelerini izleyin [Windows üzerinde çalışan VS kodu](https://code.visualstudio.com/docs/setup/windows) sayfası

### <a name="2-installing-powershell-extension"></a>2. PowerShell uzantısı yükleme

- Visual Studio Code uygulama tarafından başlatma:
    - **Windows**: yazarak `code` PowerShell oturumunuzda
    - **Linux**: yazarak `code` terminalinizde
    - **macOS**: yazarak `code` terminalinizde

- Başlatma **hızlı açık** basarak **Ctrl + P** (**Cmd + P** Mac üzerinde).
- Hızlı Aç yazın `ext install powershell` ve isabet **Enter**.
- **Uzantıları** yan çubuğunda görünümünü açar. PowerShell uzantısı Microsoft'tan seçin.
  Bir şey görmeniz gerekir aşağıdaki gibi:

  ![VSCode](../../images/vscode.png)

- Tıklatın **yükleme** Microsoft PowerShell uzantısından düğmesinde.
- Yüklemeyi tamamladıktan sonra gördüğünüz **yüklemek** düğmesini döndüğüne **yeniden**.
  Tıklayın **yeniden**.
- Visual Studio Code yeniden sahip olduktan sonra düzenleme için hazır olursunuz.

Örneğin, yeni bir dosya oluşturmak için tıklatın **Dosya -> Yeni**.
Dosyayı kaydetmek için tıklatın **Dosya -> Kaydet** ve ardından, bir dosya adı şimdi deyin sağlayın `HelloWorld.ps1`.
Dosyayı kapatın, dosya adının yanındaki "x"'a tıklayın.
Visual Studio Code, çıkmak için **Dosya -> çıkış**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Belirli bir yüklü sürümünü PowerShell kullanma

Visual Studio Code ile belirli bir PowerShell yüklemesini kullanmak istiyorsanız, kullanıcı ayarları dosyanız için yeni bir değişken eklemeniz gerekir.

1. Tıklatın **dosya Tercihler -> Ayarlar ->**
1. İki Düzenleyicisi bölmeleri görünür.
   En sağdaki bölmede (`settings.json`), aşağıdaki ayar Ekle iki süslü ayraçlar arasında bir yerde, işletim sistemi için uygun (`{` ve `}`) ve değiştirme *<version>* yüklü ile PowerShell sürümü:

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. Yürütülebilir istenen PowerShell yoluyla ayarını değiştirin
1. Ayarlar dosyasını kaydedin ve Visual Studio Code yeniden başlatın

#### <a name="configuration-settings-for-visual-studio-code"></a>Visual Studio Code için yapılandırma ayarları

Önceki paragrafta adımları kullanarak yapılandırma ayarlarında ekleyebilirsiniz `settings.json`.

Visual Studio Code aşağıdaki yapılandırma ayarları öneririz:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Visual Studio Code ile hata ayıklama

### <a name="no-workspace-debugging"></a>Hayır-çalışma hata ayıklama

Visual Studio Code sürüm 1.9 itibariyle PowerShell komut dosyasını içeren klasörü açmak zorunda kalmadan PowerShell komut dosyaları ayıklayabilirsiniz.
PowerShell komut dosyası ile açmanız yeterlidir **Dosya -> Dosya Aç...** , bir satırı (F9 tuşuna basın) bir kesme noktası ayarlayın ve ardından hata ayıklamayı başlatmak için F5'e basın.
Hata ayıklayıcı, adım, devam ettirme ve durdurma hata ayıklama bölün sağlayan görünür ve hata ayıklama Eylemler bölmesinde görmeniz gerekir.

### <a name="workspace-debugging"></a>Çalışma hata ayıklama

Hata ayıklama çalışma başvuruyor Visual Studio Code kullanarak açtığınız bir klasör bağlamında hata ayıklama için **Klasör Aç...**  gelen **dosya** menüsü.
Açtığınız genellikle PowerShell proje klasörünüzdeki ve/veya Git deponuzu kökündeki klasörüdür.

Bu modda bile F5'e basarak şu anda seçili PowerShell komut dosyası hata ayıklama başlatabilirsiniz.
Ancak, çalışma hata ayıklama yalnızca şu anda açık olan dosyayla hata ayıklama dışında birden çok hata ayıklama yapılandırmaları tanımlamanızı sağlar.
Örneğin, bir yapılandırmaları ekleyebilirsiniz:

- Hata ayıklayıcı Pester testlerinde başlatma
- Hata ayıklayıcı bağımsız değişkenlerle belirli bir dosya başlatma
- Hata ayıklayıcı etkileşimli oturum başlatma
- PowerShell ana bilgisayar işlemi için hata ayıklayıcıyı Ekle

Hata ayıklama yapılandırma dosyası oluşturmak için aşağıdaki adımları izleyin:

1. Açık **hata ayıklama** basarak Görünüm **Ctrl + Shift + D** (**Cmd + SHIFT + D** Mac üzerinde).
1. Tuşuna **yapılandırma** araç çubuğunda dişli simgesi.
1. Visual Studio Code ister **seçin ortamı**.
   Seçin **PowerShell**.

   Bunu yaparken, Visual Studio Code çalışma klasörünüze kök dizininde bir dizin ve dosya ".vscode\launch.json" oluşturur.
   Bu, hata ayıklama yapılandırmasını depolandığı yerdir. Dosyalarınızı Git deposunda varsa, genellikle Launch.json'u dosyasını kaydetmek istediğiniz.
   Launch.json'u dosyasının içeriğini şunlardır:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
}
```

Bu hata ayıklama senaryoları temsil eder.
Ancak, bu dosyayı düzenleyicide açtığınızda gördüğünüz bir **Yapılandırması Ekle...**  düğmesi.
Daha fazla PowerShell hata ayıklama yapılandırmaları eklemek için bu düğmeyi basabilirsiniz. Eklemek için kullanışlı bir yapılandırma **PowerShell: başlatma komut dosyası**.
Bu yapılandırma ile hangi dosya Düzenleyicisi'nde şu anda etkin olan geçtiğinden bağımsız F5'e basın her başlatılması gereken isteğe bağlı bağımsız değişkenler ile belirli bir dosya belirtebilirsiniz.

Hata ayıklama yapılandırmasını kurulduktan sonra bir hata ayıklama oturumu sırasında bir hata ayıklama yapılandırmasını açılan listesinde seçerek kullanmak istediğiniz yapılandırma seçebilirsiniz **hata ayıklama** görünümünün araç.

Visual Studio Code için PowerShell uzantısını kullanarak başlamanıza yardımcı olmak kullanışlı olabilecek birkaç bloglar vardır

- Visual Studio Code: [PowerShell uzantısı][ps-extension]
- [Yazma ve PowerShell betikleri Visual Studio kodda hata ayıklama][debug]
- [Visual Studio kod Kılavuzu hata ayıklama][vscode-guide]
- [PowerShell Visual Studio kodda hata ayıklama][ps-vscode]
- [Visual Studio Code PowerShell geliştirme kullanmaya başlama][getting-started]
- [Visual Studio Code PowerShell geliştirme – 1. bölüm özelliklerini düzenleme][editing-part1]
- [Visual Studio Code PowerShell geliştirme – Kısım 2 özelliklerini düzenleme][editing-part2]
- [Visual Studio Code – Kısım 1 PowerShell komut dosyası hata ayıklaması][debugging-part1]
- [Visual Studio Code – Kısım 2 PowerShell komut dosyası hata ayıklaması][debugging-part2]

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>Visual Studio Code için PowerShell uzantısı

PowerShell uzantının kaynak kodu bulunabilir [GitHub](https://github.com/PowerShell/vscode-powershell).
