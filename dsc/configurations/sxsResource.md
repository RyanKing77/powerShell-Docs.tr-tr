---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yüklü bir kaynağın belirli bir sürümünü içeri aktarma
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683887"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Yüklü bir kaynağın belirli bir sürümünü içeri aktarma

> Şunun için geçerlidir: Windows PowerShell 5.0

PowerShell 5. 0'da, DSC kaynakları ayrı sürümleri bir bilgisayarda yan yana yüklenebilir. Kaynak modülü sürüm klasörleri adlı ayrı bir kaynak sürümleri depolayabilirsiniz.

## <a name="installing-separate-resource-versions-side-by-side"></a>Ayrı kaynak sürümlerini yan yana yükleme

Kullanabileceğiniz **MinimumVersion**, **MaximumVersion**, ve **RequiredVersion** parametrelerinin [Install-Module](/powershell/module/PowershellGet/Install-Module) belirtmek için cmdlet hangi sürümü yüklemek için bir modülün. Çağırma **Install-Module** belirtmeden bir sürümü, en son sürümünü yükler.

Örneğin, birden çok sürümü vardır **xFailOverCluster** modülü, her birinde bir **xCluster** kaynak. Çağırma **Install-Module** sürümü belirtmeden numarası modülünün en son sürümünü yükler.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Bir modülün belirli bir sürümünü yüklemek için belirtin bir **RequiredVersion** 1.1.0.0 biri. Bu, belirtilen sürümü yüklü olan sürümü ile yan yana yüklenir.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Her ikisi de artık bkz modülünün sürümünü kullandığınızda listelenen `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Bir yapılandırmada bir kaynak sürümünü belirtme

Bir bilgisayarda yüklü ayrı kaynak sürümleri varsa, bu kaynağın sürümünü bir yapılandırmada kullandığınızda belirtmeniz gerekir. Belirterek bunu **ModuleVersion** parametresinin **Import-DscResource** anahtar sözcüğü. Bir kaynak modülü birden fazla sürümü yüklü olan bir kaynağın sürümünü belirtmek başarısız olursa, yapılandırma, bir hata oluşturur.

Aşağıdaki yapılandırmayı çağırmak için kaynağın sürümünü belirteceğiniz gösterilmektedir:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>Not: Import-DscResource ModuleVersion parametresini PowerShell 4. 0'kullanılamaz. PowerShell 4. 0'da, Import-DscResource ModuleName parametresi için bir modül belirtimi nesnesi geçirerek bir modül sürümü belirtebilirsiniz. Modülü belirtimi nesnesi ModuleName ve RequiredVersion anahtarları içeren bir karma tablodur. Örneğin:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

Bu PowerShell 5. 0'da çalışır, ancak kullanmanızı tavsiye edilir **ModuleVersion** parametresi.

## <a name="see-also"></a>Ayrıca bkz.

- [DSC yapılandırmaları](configurations.md)
- [DSC kaynakları](../resources/resources.md)
