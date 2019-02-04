---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Kayıt Defteri Anahtarları ile Çalışma
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686953"
---
# <a name="working-with-registry-keys"></a>Kayıt Defteri Anahtarları ile Çalışma

Kayıt defteri anahtarlarını Windows PowerShell sürücülerini öğelerde olduğundan, bunlarla çalışmaya dosya ve klasörlerle çalışma çok benzer. Kritik farklardan biri bir kayıt defteri tabanlı Windows PowerShell sürücüsü her öğeyi bir klasöre bir dosya sistemi sürücüsünde olduğu gibi bir kapsayıcı olmasıdır. Ancak, kayıt defteri girdilerini ve ilişkili değerleri değil ayrı öğeleri öğelerin özelliklerini uygulanır.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Kayıt defteri anahtarını tüm alt anahtarlarını listeleme

Kullanarak, doğrudan bir kayıt defteri anahtarı içinde tüm öğeleri göstermek **Get-Childıtem**. İsteğe bağlı ekleme **zorla** gizli görüntülemek ya da sistem öğeleri için parametre. Örneğin, bu komut Windows PowerShell sürücüsünü HKCU doğrudan öğeleri görüntüler:, HKEY_CURRENT_USER defteri kovanına karşılık gelir:

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

Bunlar, üst düzey anahtarları HKEY_CURRENT_USER kayıt defteri Düzenleyicisi (Regedit.exe) altında görünür.

Ardından kayıt defteri sağlayıcısının adını belirterek bu kayıt defteri yolu belirtebilirsiniz "**::**". Kayıt defteri sağlayıcının tam adı **Microsoft.PowerShell.Core\\kayıt defteri**, ancak bu yalnızca kısalttık **kayıt defteri**. Aşağıdaki komutlardan herhangi birine içeriği doğrudan HKCU altında listelenir:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Bu komutları Cmd.exe's kullanma gibi doğrudan içerilen öğelerin yalnızca liste **DIR** komutu veya **ls** UNIX Kabuğu'nda. İçerilen öğelerin gösterilecek belirtmeniz gerekir **Recurse** parametresi. Tüm kayıt defteri anahtarlarını HKCU listelemek için (Bu işlem çok uzun zaman alabilir.) aşağıdaki komutu kullanın:

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-Childıtem** aracılığıyla karmaşık filtreleme yetenekleri gerçekleştirebilirsiniz, **yolu**, **filtre**, **INCLUDE**, ve **hariç**parametreleri, ancak bu parametreler yalnızca adına dayalı genellikle. Karmaşık filtreleme öğelerin diğer özelliklerini kullanarak gerçekleştirebileceğiniz **Where-Object** cmdlet'i. Aşağıdaki komutu kullanarak HKCU tüm anahtarların bulur:\\en fazla bir alt anahtarını ve tam olarak dört değer de sahip yazılım:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Anahtarları kopyalanıyor

Kopyalama ile yapılır **Copy-Item**. Aşağıdaki komut kopyalar HKLM:\\yazılım\\Microsoft\\Windows\\CurrentVersion ve tüm özelliklerini kullanarak HKCU için:\\, "CurrentVersion" adlı yeni bir anahtar oluşturuluyor:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Bu yeni bir anahtar kullanarak veya Kayıt Defteri Düzenleyicisi'nde inceleyin, **Get-Childıtem**, kapsanan alt kopyalarını yeni konumda olmadığını fark edeceksiniz. Tüm kapsayıcı içeriğini kopyalayın için belirtmeniz gerekir **Recurse** parametresi. Önceki kopyalama komutu özyinelemeli yapmak için şu komutu kullanırsınız:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Zaten dosya sistemi kopyaları oluşturmak kullanılabilir olan diğer araçları kullanmaya devam edebilirsiniz. Herhangi bir kayıt defteri düzenleme araçlarına — reg.exe regini.exe ve regedit.exe—and COM nesneleri (wscript.Shell nesnesinin ve WMI'ın StdRegProv sınıfı gibi) kayıt defteri düzenleme desteği dahil olmak üzere kullanılabilir gelen Windows PowerShell içinde.

### <a name="creating-keys"></a>Anahtarları oluşturma

Kayıt defterinde yeni anahtarları oluşturma, bir dosya sisteminde yeni bir öğe oluşturmaktan daha basittir. Tüm kayıt defteri anahtarlarını kapsayıcılar olduğundan, öğe türünü belirtmeniz gerekmez; yalnızca açık bir yol gibi sağlayın:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Sağlayıcı tabanlı bir yolu, bir anahtar belirtmek için de kullanabilirsiniz:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>Anahtarları silme

Öğeleri silme temelde tüm sağlayıcılar için aynıdır. Aşağıdaki komutları sessizce öğeler kaldırılır:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Belirli bir anahtarın altında tüm anahtarları kaldırılıyor

İçerilen öğelerin kullanarak kaldırabilirsiniz **Kaldır öğesini**, ancak başka bir öğe içeriyorsa, kaldırma işlemini onaylamanız istenir. Örneğin, HKCU silmeye çalışırsanız:\\CurrentVersion alt oluşturduk, bu görürüz:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

İçerilen öğelerin sormadan silmek için belirtin **-Recurse** parametresi:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

HKCU içindeki tüm öğeleri kaldırmak istiyorsanız:\\CurrentVersion ancak değil HKCU:\\CurrentVersion kendisi, bunun yerine kullanabilirsiniz:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```