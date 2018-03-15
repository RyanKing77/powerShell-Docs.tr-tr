---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Kaynaklar birden çok sürümü ile kullanma"
ms.openlocfilehash: 5ca4eadfe23a4675e1b81b86d4274d7f113228fe
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="using-resources-with-multiple-versions"></a>Kaynaklar birden çok sürümü ile kullanma

> İçin geçerlidir: Windows PowerShell 5.0

PowerShell 5. 0'da, DSC kaynakları birden çok sürümü olabilir ve bir bilgisayar yan yana üzerinde sürümleri yüklenebilir. Bu, aynı modülü klasörde yer alan birden çok kaynak Modül sürümü sağlayarak uygulanır.

## <a name="installing-multiple-resource-versions-side-by-side"></a>Birden çok kaynak sürümlerini yan yana yükleme

Kullanabileceğiniz **MinimumVersion**, **MaximumVersion**, ve **RequiredVersion** parametrelerinin [yükleme-Module](https://technet.microsoft.com/library/dn807162.aspx) belirtmek için cmdlet yüklemek için bir modül hangi sürümü. Çağırma **yükleme-Module** belirtmeden bir sürüm en son sürümü yükler.

Örneğin, birden çok sürümü vardır **xFailOverCluster** modülü, her biri içeren bir **xCluster** kaynağa. Arama sonucu **yükleme-Module** sürüm belirtmeden numarası aşağıdaki gibidir:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Şimdi çağırırsanız, **yükleme-Module** yeniden, ancak belirtin bir **RequiredVersion** 1.1.0.0 bunu aşağıdaki sonuçları:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Bir kaynak sürümü bir yapılandırmada belirtme

Bir bilgisayarda yüklü birden fazla kaynaklarınız varsa, bir yapılandırmada kullandığınızda, bu kaynak sürümü belirtmeniz gerekir. Belirterek bunu **ModuleVersion** parametresinin **alma DscResource** anahtar sözcüğü. Yapılandırma birden çok sürüm yüklü olan bir kaynağın kaynak modülünün sürümünü belirtmek başarısız olursa bir hata oluşturur.

Aşağıdaki yapılandırma çağırmak için kaynak sürümünü belirtin gösterilmektedir:

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

>Not: Alma DscResource ModuleVersion parametresinin PowerShell 4. 0 ' kullanılabilir değil. PowerShell 4. 0'da, bir modül sürümü alma DscResource ModuleName parametresi için bir modül belirtimi nesnesi geçirerek belirtebilirsiniz. Bir modül belirtimi ModuleName ve RequiredVersion anahtarları içeren bir karma tablosu nesnesidir. Örneğin:

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

Bu PowerShell 5. 0'da çalışır, ancak kullanmanız önerilir **ModuleVersion** parametresi.

## <a name="see-also"></a>Ayrıca bkz:
* [DSC yapılandırmaları](configurations.md)
* [DSC kaynakları](resources.md)

