# <a name="using-visual-studio-code-for-powershell-development"></a>PowerShell geliştirme için Visual Studio Code'u kullanma

Ek olarak [PowerShell ISE][ise], PowerShell Visual Studio Code'da iyi desteklenen de.
Visual Studio Code için PowerShell Core (Windows, macOS ve Linux) tüm platformlarda desteklenir ancak Ayrıca, işe PowerShell Core ile desteklenmiyor

Visual Studio Code Windows PowerShell sürüm 5 ile Windows 10 veya yükleyerek kullanabileceğinizi [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) için alt düzey Windows OSs (örneğin Windows 8.1, vb.).

Başlamadan önce lütfen PowerShell sisteminizde mevcut olduğundan emin olun.
Windows, macOS ve Linux'ta modern iş yükleri için bkz:

- [Linux'ta PowerShell Core yükleme][install-pscore-linux]
- [Macos'ta PowerShell Core yükleme][install-pscore-macos]
- [Üzerinde Windows PowerShell Core yükleme][install-pscore-windows]

Geleneksel Windows PowerShell iş yükleri için bkz: [Windows PowerShell'i yükleme][install-winps].

## <a name="editing-with-visual-studio-code"></a>Visual Studio kodu ile düzenleme

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Visual Studio Code yükleme](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: yükleme yönergelerini izleyin [Linux üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/linux) sayfası

- **macOS**: yükleme yönergelerini izleyin [macOS üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/mac) sayfası

  > [!IMPORTANT]
  > MacOS üzerinde doğru çalışması için PowerShell uzantısı için OpenSSL yüklemeniz gerekir.
  > Bunu yapmanın en kolay yolu yüklemektir [Homebrew](http://brew.sh/) ve ardından çalıştırın `brew install openssl`.
  > VS Code şimdi yükleyebilir PowerShell uzantı başarıyla.

- **Windows**: yükleme yönergelerini izleyin [Windows üzerinde çalışan VS Code](https://code.visualstudio.com/docs/setup/windows) sayfası

### <a name="2-installing-powershell-extension"></a>2. PowerShell uzantısı yükleniyor

- Visual Studio Code tarafından uygulama başlatma:
  - **Windows**: yazarak `code` PowerShell oturumunuzda
  - **Linux**: yazarak `code` , Terminal
  - **macOS**: yazarak `code` , Terminal

- Başlatma **Quick Open** tuşuna basarak **Ctrl + P** (**Cmd + P** Mac üzerinde).
- Hızlı Aç yazın `ext install powershell` ve isabet **Enter**.
- **Uzantıları** taraftaki çubukta görünümü açılır. Microsoft PowerShell uzantıyı seçin.
  Bir şey görmeniz gerekir aşağıdaki gibi:

  ![VSCode](../../images/vscode.png)

- Tıklayın **yükleme** Microsoft gelen PowerShell uzantısında düğmesi.
- Yüklemeyi tamamladıktan sonra gördüğünüz **yükleme** düğmesi dönüşür **yeniden**.
  Tıklayarak **yeniden**.
- Visual Studio Code yeniden sahip olduktan sonra düzenleme için hazır olursunuz.

Örneğin, yeni bir dosya oluşturmak için tıklayın **Dosya -> Yeni**.
Bunu kaydetmek için tıklatın **Dosya -> Kaydet** ve ardından bir dosya adı, şimdi deyin sağlayın `HelloWorld.ps1`.
Dosyayı kapatmak için dosya adının yanındaki "x" tıklayın.
Visual Studio Code, çıkmak için **Dosya -> çıkış**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Belirli yüklü PowerShell sürümü kullanıyor

Visual Studio Code ile belirli bir PowerShell yüklemesi kullanmak istiyorsanız, yeni bir değişken, kullanıcı ayarları dosyanıza ekleme gerekir.

1. Tıklayın **dosya Tercihler -> Ayarlar ->**
1. İki Düzenleyici bölme görünür.
   En sağdaki bölmede (`settings.json`), aşağıdaki ayar Ekle iki süslü ayraçlar arasında bir yerde, işletim sistemi için uygun (`{` ve `}`) ve yerine **\<sürüm\>** yüklü PowerShell sürümü ile:

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. Yürütülebilir istenen PowerShell yoluyla ayarını değiştirin
1. Ayarlar dosyasını kaydedin ve Visual Studio Code'u yeniden başlatın

#### <a name="configuration-settings-for-visual-studio-code"></a>Visual Studio Code için yapılandırma ayarları

Önceki paragrafta adımları kullanarak, yapılandırma ayarlarında ekleyebilirsiniz `settings.json`.

Visual Studio Code için aşağıdaki yapılandırma ayarları öneririz:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Visual Studio kodu ile hata ayıklama

### <a name="no-workspace-debugging"></a>Hayır-çalışma hata ayıklama

Visual Studio Code sürümü 1.9 itibarıyla PowerShell komut dosyasını içeren klasörü açmak zorunda kalmadan PowerShell betikleri hata ayıklaması yapabilirsiniz.
PowerShell komut dosyasıyla açmanız yeterlidir **Dosya -> Dosya Aç...** satırında (F9 tuşuna basın) bir kesme noktası ayarlayın ve ardından hata ayıklamayı başlatmak için F5 tuşuna basın.
Hata ayıklayıcı, adım, sürdürme ve hata ayıklamayı durdurmak sonu sağlayan görünen hata ayıklama Eylemler bölmesinde görmeniz gerekir.

### <a name="workspace-debugging"></a>Çalışma hata ayıklama

Çalışma hata ayıklama başvuruyor Visual Studio Code kullanarak açılan bir klasörü bağlamında hata ayıklama için **Klasör Aç...**  gelen **dosya** menüsü.
Açtığınız genellikle PowerShell proje klasörünüze ve/veya Git deponuzun kök klasördür.

Bu modda da F5'e basarak o anda seçili PowerShell betik hata ayıklama başlayabilirsiniz.
Ancak, çalışma hata ayıklama, şu anda açık dosya yalnızca hata ayıklama dışında birden çok hata ayıklama yapılandırmaları tanımlamanızı sağlar.
Örneğin, bir yapılandırmalarına ekleyebilirsiniz:

- Hata ayıklayıcı Pester testlerinde başlatın
- Belirli bir dosya hata ayıklayıcı bağımsız değişkenleriyle Başlat
- Hata ayıklayıcı etkileşimli bir oturum başlatın
- Bir PowerShell ana bilgisayar işlemi için hata ayıklayıcının

  Hata ayıklama yapılandırma dosyanızı oluşturmak için aşağıdaki adımları izleyin:

  1. Açık **hata ayıklama** tuşuna basarak görünümü **Ctrl + SHIFT + D** (**Cmd + SHIFT + D** Mac üzerinde).
  2. Tuşuna **yapılandırma** araç çubuğundaki dişli simgesi.
  3. Visual Studio Code ister **ortamı seçin**.
  Seçin **PowerShell**.

  Bunu yaptığınızda, Visual Studio Code kullanarak çalışma klasörünüzde kök dizininde bir dizin ve dosya ".vscode\launch.json" oluşturur.
  Bu, hata ayıklama yapılandırması depolandığı yerdir. Dosyalarınızı Git deposunda ise genellikle launch.json dosyası işleme istersiniz.
  Launch.json dosyasının içeriğini şunlardır:

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

  Bu, hata ayıklama senaryoları temsil eder.
  Ancak, bu dosya Düzenleyicisi'nde açtığınızda, gördüğünüz bir **Yapılandırması Ekle...**  düğmesi.
  Daha fazla PowerShell hata ayıklama yapılandırmaları eklemek için bu düğmeyi basabilirsiniz. Eklemek için kullanışlı bir yapılandırma **PowerShell: başlatma betiği**.
  Bu yapılandırma ile hangi dosya düzenleyicide şu anda etkin olursa olsun F5 tuşuna basarak her başlatılacak isteğe bağlı bağımsız değişkenler ile belirli bir dosyayı belirtebilirsiniz.

  Hata ayıklama yapılandırması kurulduktan sonra hata ayıklama oturumu sırasında bir hata ayıklama yapılandırması açılan listesinde seçerek kullanmak istediğiniz yapılandırmayı seçebilirsiniz **hata ayıklama** görünümünün araç çubuğu.

  Visual Studio Code için PowerShell uzantısını kullanarak başlamanıza yardımcı olmak yardımcı olabilecek birkaç blogları vardır.

Visual Studio kodu:

- [PowerShell uzantısı][ps-extension]
- [Yazma ve PowerShell betikleri Visual Studio code'da Hata Ayıkla][debug]
- [Hata ayıklama Visual Studio kod Kılavuzu][vscode-guide]
- [Visual Studio code'da hata ayıklama PowerShell][ps-vscode]
- [Visual Studio code'da PowerShell geliştirme ile çalışmaya başlama][getting-started]
- [Düzenleme özellikleri PowerShell geliştirme – bölüm 1 için Visual Studio Code][editing-part1]
- [Visual Studio kod düzenleme özellikleri PowerShell geliştirme – bölüm 2][editing-part2]
- [Visual Studio Code – bölüm 1 PowerShell betik hata ayıklama][debugging-part1]
- [Visual Studio Code – bölüm 2 PowerShell betik hata ayıklama][debugging-part2]

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>Visual Studio Code için PowerShell uzantısı

PowerShell uzantının kaynak kodu bulunabilir [GitHub](https://github.com/PowerShell/vscode-powershell).