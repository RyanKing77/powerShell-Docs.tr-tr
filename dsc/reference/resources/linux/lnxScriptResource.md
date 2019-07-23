---
ms.date: 06/12/2017
keywords: DSC, PowerShell, yapılandırma, kurulum
title: Linux nxScript kaynağı için DSC
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372156"
---
# <a name="dsc-for-linux-nxscript-resource"></a>Linux nxScript kaynağı için DSC

PowerShell Istenen durum yapılandırması (DSC) içindeki **Nxscript** kaynağı bir Linux düğümünde Linux betikleri çalıştırmak için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama |
|---|---|
| GetScript| Makinenin geçerli durumunu döndürmek için bir betik sağlar.  Bu betik, [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) betiğini çağırdığınızda çalışır. Betiğin #!/bin/Bash. gibi bir shebang ile başlaması gerekir|
| SetScript| Makineyi doğru duruma koyan bir betik sağlar. [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) betiğini çağırdığınızda **TestScript** önce çalışır. **TestScript** bloğu 0 dışında bir çıkış kodu döndürürse, **setscript** bloğu çalışır. **Testscrıpt** 0 çıkış kodu döndürürse, **setscript** çalıştırılmaz. Betiğin gibi bir shebang `#!/bin/bash`ile başlaması gerekir.|
| TestScript| Düğümün Şu anda doğru durumda olup olmadığını değerlendiren bir betik sağlar. [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) betiğini çağırdığınızda, bu betik çalışır. 0 dışında bir çıkış kodu döndürürse, SetScript çalışır. 0 çıkış kodu döndürürse, **Setscript** çalıştırılmaz. **TestScript** , [testdscconfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) betiğini çağırdığınızda de çalışır. Ancak, bu durumda, **TestScript**'ten çıkış kodu Döndürülmeksizin, **setscript** çalıştırılmaz. **Test betiği** içerik içermeli ve gerçek yapılandırma geçerli durum yapılandırmasıyla eşleşiyorsa 0 çıkış kodu ve eşleşmezse 0 dışında bir çıkış kodu döndürmelidir. (Geçerli istenen durum yapılandırması, DSC kullanan düğümde kullanılan son yapılandırmadır). Betiğin, 1 #!/bin/Bash.1 gibi bir shebang ile başlaması gerekir|
| Kullanıcı| Betiği çalıştıran kullanıcı.|
| Grup| Betiği çalıştırmak için Grup.|
| DependsOn | Bu kaynak yapılandırıldıktan önce başka bir kaynağın yapılandırmasının çalıştırılması gerektiğini gösterir. Örneğin, önce çalıştırmak istediğiniz kaynak yapılandırma betiği bloğunun **kimliği** **resourceName** ise ve türü **ResourceType**ise, bu özelliği kullanmak için sözdizimi olur `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, ek yapılandırma yönetimi gerçekleştirmek için **Nxscript** kaynağının kullanımını gösterir.

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```
