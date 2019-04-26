---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: Yapılandırmalarda koşullu deyimler ve döngüler
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080144"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Yapılandırmalarda koşullu deyimler ve döngüler

Yapabileceğiniz, [yapılandırmaları](configurations.md) daha dinamik PowerShell akış denetimi anahtar sözcüklerini kullanarak. Bu makalede, yapılandırmalarınızı daha dinamik hale getireceğinizi koşullu ifadeleri ve döngüler nasıl kullanabileceğinizi gösterir. Birleştirme koşullu ve döngüler ile [parametreleri](add-parameters-to-a-configuration.md) ve [yapılandırma verilerini](configData.md) yapılandırmalarınızı derleme sırasında daha fazla esneklik ve denetim sağlar.

Bir işlev veya bir betik bloğu yalnızca gibi yapılandırması içindeki herhangi bir PowerShell dil kullanabilirsiniz. ".Mof" dosyasını derlemek için yapılandırmayı çağırdığınızda kullandığınız deyimleri yalnızca değerlendirilir. Aşağıdaki örnekler kavramları göstermek için basit bir senaryo gösterir. Koşullular döngüler parametreler ve yapılandırma verileri ile daha sık kullanılan ' dir.

Bu basit örnekte, **hizmet** kaynak blok geçerli durumunu koruyan bir ".mof" dosyası oluşturmak için derleme zamanında bir hizmetinin geçerli durumunu alır.

> [!NOTE]
> Dinamik kaynak bloklarını kullanarak, IntelliSense verimliliğini etkisiz hale. PowerShell ayrıştırıcı yapılandırmasını derlenmiş kadar belirtilen değerleri kabul edilebilir olup olmadığını belirleyemiyor.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

Ayrıca, aşağıdakileri oluşturabilirsiniz bir **hizmet** block geçerli makine üzerinde her hizmet için kaynak kullanarak bir `foreach` döngü.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

Ayrıca yalnızca basit bir kullanarak çevrimiçi olan makineler için yapılandırmaları oluşturabilirsiniz `if` deyimi.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> Dinamik kaynak Yukarıdaki örneklerde başvurusu geçerli makine engeller. Geliştirmekte yapılandırma üzerinde makine olabilir, bu örnekte, hedef değil düğümü.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Özet

Özet olarak, bir yapılandırması içindeki herhangi bir PowerShell dil kullanabilirsiniz.

Bu gibi şeyleri içerir:

- Özel nesneler
- Hashtable'da
- Dize düzenlemesi
- Uzaktan iletişim
- WMI ve CIM
- Active Directory nesneleri
- ve daha fazlası...

Bir yapılandırmada tanımlanmış herhangi bir PowerShell kod, derleme zamanında değerlendirilir, ancak kod yapılandırmanızı içeren betik yerleştirebilirsiniz. Yapılandırma içeri aktardığınızda yapılandırma bloğu dışında herhangi bir kod yürütülür.

## <a name="see-also"></a>Ayrıca bkz.

- [İçin yapılandırma parametreleri Ekle](add-parameters-to-a-configuration.md)
- [Yapılandırmaları yapılandırma verilerinden ayrı](configData.md)
