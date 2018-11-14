---
ms.date: 11/06/2018
contributor: JKeithB
keywords: Galeri, powershell, cmdlet, psgallery, psget
title: Yerel PSRepositories ile çalışma
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619266"
---
# <a name="working-with-local-powershellget-repositories"></a>Yerel PowerShellGet depoları ile çalışma

PowerShellGet modülü desteği, PowerShell Galerisi dışındaki depolar.
Bu cmdlet'ler aşağıdaki senaryolara olanak tanır:

- Ortamınızda PowerShell modülleri güvenilir, önceden doğrulanmış kümesi desteği
- PowerShell modülleri veya betikleri bir CI/CD işlem hattı test etme
- PowerShell betikleri ve modülleri Internet'e sistemlerine sunun

Bu makalede, yerel bir PowerShell deposu ayarlama açıklar. Makaleyi de kapsayan [OfflinePowerShellGetDeploy][] PowerShell Galerisi'nden modül. Bu modül, yerel deponuzu PowerShellGet en son sürümünü yüklemek için cmdlet'leri içerir.

## <a name="local-repository-types"></a>Yerel depo türleri

Yerel PSRepository oluşturmanın iki yolu vardır: NuGet sunucusu veya dosya paylaşımı. Her tür avantajları ve dezavantajları vardır:

NuGet sunucusu

| Olumlu yönleri| Olumsuz yönleri |
| --- | --- |
| PowerShellGallery işlevselliği yakından taklit eder | Çok katmanlı bir uygulama, operasyon ve Destek gerektirir |
| NuGet, Visual Studio, diğer araçlar ile tümleşir | Kimlik doğrulama modeli ve gerekli NuGet hesap yönetimi |
| NuGet destekleyen, meta verilerde `.Nupkg` paketleri | Yayınlama API anahtarı yönetim ve bakım gerektirir |
| Arama, paket yönetimi sağlar. | |

Dosya Paylaşımı

| Olumlu yönleri| Olumsuz yönleri |
| --- | --- |
| Kolay ayarlama, yedeklemek ve korumak | PowerShellGet tarafından kullanılan meta verileri kullanılamıyor |
| Basit bir güvenlik modeli - paylaşım kullanıcı izinleri | Temel dosya paylaşımı ötesinde kullanıcı Arabirimi |
| Varolan öğelerini değiştirme gibi hiçbir kısıtlama | Sınırlı bir güvenlik ve kimin hangi güncelleştirmelerin, hiçbir kayıt |

PowerShellGet, türü ve destekleyen sürümler ve bağımlılık yükleme bulma ile çalışır.
Ancak, temel NuGet sunucularını veya dosya paylaşımları için PowerShell Galerisi için çalışan bazı özellikler kullanılamaz.

- Her şeyi bir - betikleri, modüller, DSC kaynakları veya rol işlevleri hiçbir ayrım paketidir.
- Paket meta etiketleri dahil olmak üzere, dosya paylaşımı sunucuları göremez.

## <a name="creating-a-local-repository"></a>Yerel bir depo oluşturma

Aşağıdaki makalede kendi NuGet sunucusu kurma adımları listelenir.

- [NuGet.Server][]

Paketleri ekleme noktaya kadar adımları izleyin. Adımları [bir paket yayımlama](#publishing-to-a-local-repository) bu makalenin sonraki bölümlerinde ele alınmaktadır.

Bir dosya paylaşımı tabanlı deposu için kullanıcılarınızın dosya paylaşımına erişmek için izinlere sahip olduğunuzdan emin olun.

## <a name="registering-a-local-repository"></a>Yerel bir depoya kaydetme

Bir depo kullanılabilmesi için önce onu kullanarak kaydedilmelidir `Register-PSRepository` komutu.
Aşağıdaki örneklerde **InstallationPolicy** ayarlanır *güvenilen*, kendi deponuzu güven varsayımına üzerinde.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

İki komut nasıl işleneceğini arasındaki farkı Not **ScriptSourceLocation**. Dosya Paylaşımı tabanlı depoları **SourceLocation** ve **ScriptSourceLocation** eşleşmelidir. Web tabanlı bir depo için farklı olmalıdır bunu Bu örnekte bir sondaki "/" eklenir **SourceLocation**.

Yeni oluşturulan PSRepository varsayılan depoyu olmasını istiyorsanız, diğer tüm PSRepositories kaydını silmeniz gerekir. Örneğin:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> Depo adı 'PSGallery' PowerShell Galerisi tarafından kullanılmak üzere ayrılmış. PSGallery kaydını kaldırabilirsiniz, ancak farklı bir depoda PSGallery adı yeniden kullanamazsınız.

PSGallery geri yüklemeniz gerekirse, aşağıdaki komutu çalıştırın:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Yerel bir depo yayımlama

Yerel PSRepository kaydettikten sonra yerel PSRepository için yayımlayabilirsiniz. Yayımlama iki ana senaryo vardır: kendi modül yayımlama ve PSGallery modülünden yayımlama.

### <a name="publishing-a-module-you-authored"></a>Bir modül, yazılan yayımlama

Kullanım `Publish-Module` ve `Publish-Script` modülünüzde, yerel PSRepository için PowerShell Galerisi için bunu aynı şekilde yayımlamak için.

- Kodunuz için konumu belirtin
- Bir API anahtarı sağlayın
- Depo adını belirtin. Örneğin, `-PSRepository LocalPSRepo`

> [!NOTE]
> NuGet sunucusu bir hesap oluşturma ardından oluşturmak ve API anahtarını kaydetmek oturum açın.
> Bir dosya paylaşımı için herhangi bir boş olmayan dize NuGetApiKey değeri kullanın.

Örnekler:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Güvenliğini sağlamak için API anahtarları betiklerde sabit kodlanmış olmamalıdır. Güvenli anahtar yönetimi sistemi kullanın.

### <a name="publishing-a-module-from-the-psgallery"></a>Bir modülden PSGallery yayımlama

Bir modülden PSGallery için yerel PSRepository yayımlamak için 'Kaydet-Package' cmdlet'ini kullanabilirsiniz.

- Paket adını belirtin
- 'NuGet' sağlayıcısı olarak belirtin.
- Kaynak (PSGallery konumu belirtin https://www.powershellgallery.com/api/v2)
- Yerel deponuzu yolunu belirtin

Örnek:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Web tabanlı, yerel PSRepository ise nuget.exe yayımlamak için kullandığı ek bir adım gerektirir.

Kullanmaya yönelik belgeler bkz [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Bağlantısı kesilmiş bir sisteme PowerShellGet yükleme

PowerShellGet dağıtma, internet'ten kesilecek sistemleri gerektiren ortamlarda zordur. PowerShellGet ilk kez kullanıldığı en son sürümü yükleyen bir önyükleme işlemi var. PowerShell Galerisi OfflinePowerShellGetDeploy modülünde bu önyükleme işlemini destekleyecek cmdlet'leri sağlar.

Çevrimdışı bir dağıtım bootstrap için için gerekir:

- OfflinePowerShellGetDeploy, İnternet'e bağlı sistem ve bağlantısı kesilmiş sistemlerinizi indirip yükleyin
- PowerShellGet ve kullanarak İnternet'e bağlı sistem bağımlılıklarını karşıdan `Save-PowerShellGetForOffline` cmdlet'i
- PowerShellGet ve bağımlılıklarını İnternet'e bağlı sistemden, bağlantısı kesilmiş sunucuya kopyalayın.
- Kullanım `Install-PowerShellGetOffline` PowerShellGet ve bağımlılıklarının doğru klasörler halinde yerleştirmek için bağlantısı kesik sistemdeki

Aşağıdaki komutları kullanın `Save-PowerShellGetForOffline` tüm bileşenlerin bir klasöre koymak için `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Bu noktada, içeriğini yapmalısınız `F:\OfflinePowerShellGet` bağlantısı kesilmiş sistemleriniz için kullanılabilir. Çalıştırma `Install-PowerShellGetOffline` cmdlet'ini PowerShellGet bağlantısı kesilmiş sisteme yükleyin.

> [!NOTE]
> Bir PowerShell oturumunda aşağıdaki komutları çalıştırmadan önce PowerShellGet çalıştırmayın önemlidir. PowerShellGet oturuma yüklendikten sonra bileşenlerin güncelleştirilemiyor. PowerShellGet yanlışlıkla başlatırsanız, çıkmak ve PowerShell yeniden başlatın.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Bu komutları çalıştırdıktan sonra yerel deponuzu PowerShellGet yayımlamak hazır olursunuz.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Güvenliğini sağlamak için API anahtarları betiklerde sabit kodlanmış olmamalıdır. Güvenli anahtar yönetimi sistemi kullanın.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
