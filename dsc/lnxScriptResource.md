---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxScript kaynak için
ms.openlocfilehash: 7c8c3aa16af5b31c0a549972288c9466bb56609d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC Linux nxScript kaynak için

**NxScript** kaynağı içinde PowerShell istenen durum yapılandırması (DSC), bir Linux düğümünde Linux komut dosyalarını çalıştırmak için bir mekanizma sağlar.

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
| GetScript| Çağırdığınızda, çalıştırılan bir komut dosyası sağlar [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet'i. Komut dosyası # gibi bir shebang ile başlaması gerekir! / bin/bash.|
| SetScript| Bir komut dosyası sağlar. Ne zaman çağırmayı [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'ini **TestScript** ilk çalıştırır. Varsa **TestScript** bloğu döndüren bir çıkış kodu 0 dışında **SetScript** bloğu çalıştırır. Varsa **TestScript** bir çıkış kodu 0 döndürür **SetScript** çalışmaz. Komut dosyası gibi bir shebang ile başlamalıdır `#!/bin/bash`.|
| TestScript| Bir komut dosyası sağlar. Ne zaman çağırmayı [başlangıç DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i, bu komut dosyasını çalıştırır. 0 dışında bir çıkış kodu döndürürse, SetScript çalıştırın. 0, çıkış kodu döndürürse **SetScript** çalışmaz. **TestScript** çağırdığınızda, aynı zamanda çalıştırıyorsa [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet'i. Ancak, bu durumda, **SetScript** , hangi çıkış kodu öğesinden döndürülen olsun çalışmaz **TestScript**. **TestScript** geçerli istenen durum yapılandırması gerçek yapılandırmasıyla eşleşen ve bir çıkış kodu, diğer 0'dan, onu eşleşmiyorsa, 0 çıkış kodu döndürmesi gerekir. (Geçerli istenen durum yapılandırması, DSC kullanarak düğümde kamulaştırılmış son yapılandırmadır). Komut dosyası 1#!/bin/bash.1 gibi bir shebang ile başlamalıdır|
| Kullanıcı| Komut dosyası olarak çalıştırmak için kullanıcı.|
| Grup| Komut dosyası olarak çalıştırmak için Grup.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek kullanımını gösteren **nxScript** ek yapılandırma yönetimi gerçekleştirmek için kaynak.

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