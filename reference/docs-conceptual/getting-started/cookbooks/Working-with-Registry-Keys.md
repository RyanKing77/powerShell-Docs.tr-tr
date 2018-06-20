---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Kayıt Defteri Anahtarları ile Çalışma
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951707"
---
# <a name="working-with-registry-keys"></a>Kayıt Defteri Anahtarları ile Çalışma

Kayıt defteri anahtarları öğeler Windows PowerShell sürücülerde olduğundan, bunlarla çalışmaya dosyalar ve klasörlerle çalışmaya çok benzer. Bir kritik fark her öğe bir kayıt defteri tabanlı Windows PowerShell sürücüsünde bir dosya sistemi sürücüsündeki bir klasörde bulunan gibi bir kapsayıcı olmasıdır. Ancak, kayıt defteri girdileri ve ilişkili değerleri değil ayrı öğeleri öğeleri özellikleridir.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Tüm alt anahtarlarının kayıt defteri anahtarının listeleme

Kullanarak doğrudan bir kayıt defteri anahtarı içinde tüm öğeleri gösterebilir **Get-Childıtem**. İsteğe bağlı eklemek **zorla** görüntüleme gizli veya sistem öğelere parametresi. Örneğin, bu komut öğeleri doğrudan Windows PowerShell sürücüsü HKCU görüntüler:, HKEY_CURRENT_USER kayıt defteri kovanı karşılık gelir:

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

Kayıt Defteri Düzenleyicisi (Regedit.exe) HKEY_CURRENT_USER altında görünür üst düzey anahtarları şunlardır.

Ardından kayıt defteri sağlayıcının adı belirterek bu kayıt defteri yolu da belirtebilirsiniz "**::**". Kayıt defteri sağlayıcının tam ad **Microsoft.PowerShell.Core\\kayıt defteri**, ancak bu yalnızca için kısaltılmış **kayıt defteri**. Aşağıdaki komutlardan herhangi birini içeriği doğrudan HKCU altında listelenir:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Bu komutları liste Cmd.exe's kullanarak benzer doğrudan içerilen öğelerin yalnızca **DIR** komut veya **ls** UNIX Kabuğu'nda. Kapsanan öğeleri gösterecek şekilde belirtmeniz gerekir **Recurse** parametresi. HKCU tüm kayıt defteri anahtarlarında listelemek için (Bu işlem çok uzun bir süre devam edebilir.) aşağıdaki komutu kullanın:

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-Childıtem** aracılığıyla karmaşık filtreleme yetenekleri gerçekleştirebilirsiniz kendi **yolu**, **filtre**, **INCLUDE**, ve **hariç**parametreleri, ancak bu parametreler yalnızca adına bağlı genellikle. Karmaşık öğelerinin diğer özellikleri kullanarak göre filtreleme gerçekleştirebilirsiniz **Where-Object** cmdlet'i. Tüm anahtarları HKCU içinde aşağıdaki komutu bulur:\\Hayır birden fazla alt anahtar ve ayrıca tam olarak dört değerlere sahip olan yazılım:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Anahtarları kopyalama

Kopyalama ile yapılır **Copy-Item**. Aşağıdaki komut kopyalar HKLM:\\yazılım\\Microsoft\\Windows\\CurrentVersion ve tüm özelliklerini HKCU:\\, "CurrentVersion" adlı yeni bir anahtar oluşturma:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Bu yeni bir anahtar kullanarak veya Kayıt Defteri Düzenleyicisi'nde inceleyin, **Get-Childıtem**, içerdiği alt anahtarlarını kopyalarını yeni konuma sahip olmadığını göreceksiniz. Tüm kapsayıcı içeriğini kopyalamak için belirtmeniz gerekir **Recurse** parametresi. Önceki kopyalama komut özyinelemeli yapmak için bu komutu kullanırsınız:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Zaten sahip olduğunuz kullanılabilir dosya sistemi kopyaları gerçekleştirmek üzere diğer araçlarını kullanmaya devam edebilirsiniz. Hiçbir kayıt defteri düzenleme araçları — (wscript.Shell nesnesinin ve WMI'ın StdRegProv sınıfı gibi) kayıt defteri düzenlemesini destekleyecek reg.exe, regini.exe ve regedit.exe—and COM nesneleri dahil olmak üzere kullanılabilir gelen Windows PowerShell içinde.

### <a name="creating-keys"></a>Anahtarları oluşturma

Kayıt defterinde yeni anahtarları oluşturma, bir dosya sisteminde yeni bir öğe oluşturmaktan daha basittir. Tüm kayıt defteri anahtarları kapsayıcıları olduğundan, öğe türü belirtmeniz gerekmez; yalnızca açık bir yolu gibi sağladığınız:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Sağlayıcı tabanlı bir yolu, bir anahtarı belirtmek üzere de kullanabilirsiniz:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>Anahtarları silme

Öğeleri silme temelde tüm sağlayıcılar için aynıdır. Aşağıdaki komutları sessizce öğeleri kaldıracak:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Belirli bir anahtarın altında tüm anahtarları kaldırılıyor

İçerilen öğelerin kullanarak kaldırabilirsiniz **Kaldır öğesini**, ancak başka bir şey öğe içeriyorsa, kaldırma işlemini onaylamanız istenir. Örneğin, HKCU silmeye çalışırsanız:\\CurrentVersion alt anahtarının oluşturduğumuz, biz bunu bakın:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Sormadan içerilen öğelerin silmek için belirtmek **-Recurse** parametre:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

HKCU içindeki tüm öğeleri kaldırmak istiyorsanız:\\CurrentVersion ancak değil HKCU:\\CurrentVersion kendisi, bunun yerine kullanabileceğiniz:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```