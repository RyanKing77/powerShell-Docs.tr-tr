---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: ryanpu
title: Tam yetecek kadar Yönetim (JEA) geliştirmeleri
ms.openlocfilehash: 47a58a6fae9f3a41ec527ec1f77ac1c196336669
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222426"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Tam yetecek kadar Yönetim (JEA) geliştirmeleri

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>JEA uç noktalar/gruptan kısıtlanmış dosya kopyalama

Şimdi dosyalarına uzaktan kopyalayabilirsiniz/bağlanan kullanıcının yalnızca kopyalanamıyor JEA uç noktası ve rest garanti *herhangi* sisteminizdeki dosyası.
Kullanıcıların bağlanmak için bir kullanıcı sürücü için PSSC dosyasını yapılandırarak bu mümkündür.
Kullanıcı, bağlanan her kullanıcı için benzersiz olan ve oturumlarında devam ederse yeni bir PSDrive sürücüdür.
Öğeyi Kopyala veya JEA oturumdan dosyaları kopyalamak için kullanıldığında, yalnızca kullanıcı sürücü erişmesine izin vermek için sınırlı değildir.
Dosyaları kopyalamak için başka bir PSDrive girişimleri başarısız olur.

Kullanıcı bir sürücünün JEA oturum yapılandırma dosyanızda ayarlamak için aşağıdaki yeni alanları kullanın:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

Kullanıcı sürücüsünde yedekleme klasörü oluşturulur `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Kullanıcı sürücü kullanmak ve/kullanıcı sürücü kullanıma sunmak için yapılandırılmış bir JEA uç noktasından dosyaları kopyalamak için kullanın `-ToSession` ve `-FromSession` Copy-Item parametreleri.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

Ardından, kullanıcı sürücüde depolanan verileri işlemek ve bu kullanıcılara Rol Yetenek dosyanızdaki kullanılabilir yapmak için özel işlevler de yazabilirsiniz.

## <a name="support-for-group-managed-service-accounts"></a>Destek grubu için Yönetilen hizmet hesapları

Bazı durumlarda, yerel makine ötesindeki kaynaklara erişmek bir kullanıcı bir JEA oturumda gerçekleştirmek için gereken bir görev gerekebilir.
JEA oturum sanal bir hesabı kullanacak şekilde yapılandırıldığında, her türlü girişim gibi kaynaklara ulaşmak için yerel makinenin kimliğini, değil sanal hesap veya bağlı olan kullanıcı gelen görünecektir.
TP5 içinde biz JEA bağlamı altında çalışırken desteğini etkinleştirdiyseniz [grup yönetilen hizmet hesabı](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx) , bir etki alanı kimliği kullanarak ağ kaynaklarına erişmek çok daha kolay.

JEA oturum gMSA hesabı altında çalışacak şekilde yapılandırmak için aşağıdaki yeni anahtarı PSSC dosyanızda kullanın:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> **Not:** Grup yönetilen hizmet hesapları yalıtım veya sanal hesaplar sınırlı kapsamını göze değil.
> Bağlanan her kullanıcının kuruluş genelinde izniniz olmayabilir aynı gMSA kimlik paylaşır.
> Bir gmsa'yı kullanın ve her zaman mümkün olduğunda yerel makineye sınırlı sanal hesapları tercih seçerken dikkatli olun.

## <a name="conditional-access-policies"></a>Koşullu erişim ilkeleri

JEA, ne yapmalı yönetmek için bir sistem, ayrıca sınırlamak istiyorsanız bağlı zaman birisi neler yapabileceğinizi sınırlama en büyük *zaman* birisi JEA kullanabilirsiniz?
Güvenlik grupları bir kullanıcı bir JEA oturumu için ait olmalıdır belirtmenize izin vermek için yapılandırma seçenekleri oturum yapılandırma dosyalarına (.pssc) ekledik.
Ortamınızda yalnızca içinde anında (JIT) sistem varsa ve kullanıcılarınızın kendi ayrıcalıklarını bir yüksek ayrıcalıklı JEA uç noktası erişmeden önce yükseltme yapmak istediğiniz bu özellikle yararlı olabilir.

Yeni *RequiredGroups* PSSC dosyasında alan bir kullanıcı için JEA bağlanabildiğinizi belirlemek için mantığı belirtmenize olanak verir.
Kullanır (isteğe bağlı olarak iç içe) bir hashtable belirtme oluşur 'Ve' ve 'Veya' anahtarları kurallarınızı oluşturmak için.
Bu alan yararlanmak nasıl bazı örnekleri şunlardır:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Sabit: Sanal hesapları artık Windows Server 2008 R2'de desteklenir
WMF 5.1, Windows Server 2008 tutarlı yapılandırmalar ve özellik eşliği Windows Server 2008 R2 - 2016 etkinleştirme R2 sanal hesaplar kullanabilmek için sunulmuştur.
Sanal hesaplar JEA Windows 7'de kullanırken desteklenmeyen kalır.
