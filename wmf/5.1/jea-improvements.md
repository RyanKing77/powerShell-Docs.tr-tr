---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: ryanpu
title: Yeterli yönetim (JEA) geliştirmeleri
ms.openlocfilehash: a9a8a0fd2b726ded33aa07c205292efd7148f3f0
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093628"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Yeterli yönetim (JEA) geliştirmeleri

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>JEA uç öğesine/öğesinden kısıtlanmış dosya kopyalama

Artık dosyaları uzaktan kopyalayabilirsiniz/bağlanan kullanıcının yalnızca kopyalanamıyor bir JEA uç noktası ve rest garanti *herhangi* dosya sisteminize.
Kullanıcıları bağlamak için bir kullanıcı sürücü için PSSC dosyanızı yapılandırarak bu mümkündür.
Kullanıcı oturumu arasında kalıcıdır ve bağlanan her kullanıcı için benzersiz bir yeni PSDrive sürücüdür.
Zaman `Copy-Item` olduğu için veya bir JEA oturumdan dosyaları kopyalamak için kullanılan, onu yalnızca kullanıcı sürücüye erişime izin vermek için sınırlıdır.
Dosyaları kopyalamak için başka bir PSDrive girişimleri başarısız olur.

Kullanıcı bir sürücünün JEA oturum yapılandırma dosyanızda ayarlamak için aşağıdaki yeni alanları kullanın:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Kullanıcı sürücünün yedekleme klasörü oluşturulur `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Kullanıcı sürücü yazılımınız ve/kullanıcı sürücü kullanıma sunmak için yapılandırılmış bir JEA uç noktasından dosyaları kopyalamak için kullanın `-ToSession` ve `-FromSession` parametrelere `Copy-Item`.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Ardından, kullanıcı sürücüde depolanan verileri işlemek ve kullanıcı rolü özelliği için kullanılabilir hale özel işlevler yazabilirsiniz.

## <a name="support-for-group-managed-service-accounts"></a>Destek grubu için Yönetilen hizmet hesapları

Bazı durumlarda, bir kullanıcı bir JEA oturumda gerçekleştirmesi gereken bir görevi, yerel makine ötesindeki kaynaklara gerekebilir.
Bir JEA oturumu, sanal bir hesabı kullanacak şekilde yapılandırıldığında, yerel makinenin kimlik, olmayan sanal hesap veya bağlı durumda olan kullanıcı gelen gibi kaynaklarına ulaşmak için her türlü girişim görünecektir.
JEA bağlamında çalıştırma desteği etkinleştirdik TP5'te bir [Grup yönetilen hizmet hesabı](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), bir etki alanı kimliği'ni kullanarak ağ kaynaklarına erişmek çok daha kolay hale getirme.

Bir JEA oturumu gMSA hesabı altında çalışacak şekilde yapılandırmak için aşağıdaki yeni anahtarı PSSC dosyanızda kullanın:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Grup yönetilen hizmet hesapları yalıtım veya sanal hesaplar sınırlı kapsamı göze değil.
> Bağlanan her kullanıcı izinlerinizi kuruluş genelinde aynı gMSA kimlik paylaşır.
> Bir gmsa'yı kullanın ve her zaman mümkün olduğunda yerel makineye sınırlı olan sanal hesaplar tercih seçerken dikkatli olun.

## <a name="conditional-access-policies"></a>Koşullu erişim ilkeleri

JEA olduğunda bunlar, ne yapmalı yönetmek için bir sisteme ayrıca sınırlamak istiyorsanız bağlandıktan birinin neler yapabileceğinizi sınırlama en harika *olduğunda* birisi JEA kullanabilir miyim?
Güvenlik grupları bir kullanıcı bir JEA oturumu için ait olmalıdır belirtmenizi sağlar oturum yapılandırma dosyalarına (.pssc) yapılandırma seçeneği ekledik.
Ortamınızda yalnızca zamanında (JIT) sisteminiz ve kullanıcılarınızın üst düzeyde ayrıcalıklı bir JEA uç noktası erişmeden önce kendi ayrıcalıklarını yükseltme yapmak istiyorsanız bu özellikle yararlı olabilir.

Yeni *RequiredGroups* PSSC dosyasında alan, bir kullanıcı için JEA bağlanabildiğini belirlemek için mantığı belirtmenize olanak sağlar.
Kullanır (isteğe bağlı olarak iç içe) bir hashtable belirtme oluşur 'Ve' ve 'Veya' anahtarlar kurallarınızı oluşturmak için.
Bu alan kullanmayı bazı örnekleri aşağıda verilmiştir:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Düzeltildi: Sanal hesaplar artık Windows Server 2008 R2 üzerinde desteklenir

WMF 5.1, artık Windows Server 2008 tutarlı yapılandırmalar ve özellik eşliği arasında Windows Server 2008 R2 - 2016 etkinleştirme R2 sanal hesaplar kullanabilirsiniz.
Jea'yı, Windows 7'de kullanırken sanal hesaplar desteklenmeyen kalır.