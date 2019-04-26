---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynak Linux nxScript için
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077832"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC kaynak Linux nxScript için

**NxScript** kaynak içinde PowerShell Desired State Configuration (DSC), bir Linux düğümde Linux betiklerini çalıştırmak için bir mekanizma sağlar.

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
| GetScript| Çağırdığınızda, çalışan bir komut dosyası sağlar [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet'i. Betik # gibi bir shebang'i başlamalıdır! / bin/bash.|
| SetScript| Bir komut dosyası sağlar. Çağırdığınızda [Başlat-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'ini **TestScript** ilk çalıştırır. Varsa **TestScript** bloğu döndüren bir çıkış kodu 0 dışındaki **SetScript** bloğu çalışır. Varsa **TestScript** 0 çıkış kodu döndürür **SetScript** çalışmaz. Betik gibi bir shebang'i ile başlamalıdır `#!/bin/bash`.|
| TestScript| Bir komut dosyası sağlar. Çağırdığınızda [Başlat-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet'i, bu betiği çalıştırır. 0 dışında bir çıkış kodu döndürürse, SetScript çalıştırılır. 0 çıkış kodu döndürürse **SetScript** çalışmaz. **TestScript** çağırdığınızda, aynı zamanda çalıştırıyorsa [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet'i. Ancak, bu durumda, **SetScript** , hangi çıkış kodu öğesinden döndürülen ne olursa olsun çalışmaz **TestScript**. **TestScript** gerçek yapılandırmasını geçerli istenen durum yapılandırması ile eşleşen ve bir çıkış kodu, diğer 0'dan, eşleşmiyorsa, 0 çıkış kodu döndürmesi gerekir. (Geçerli istenen durum yapılandırması, DSC kullanarak bir düğümde yapılandırmalara uygun koşullarda çalışıldığından son yapılandırmadır). Betik 1#!/bin/bash.1 gibi bir shebang'i ile başlamalıdır|
| Kullanıcı| Betik olarak çalıştırmak için kullanıcı.|
| Grup| Betik olarak çalıştırmak için Grup.|
| dependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, kullanımını gösterir **nxScript** ek yapılandırma yönetimi gerçekleştirmek için kaynak.

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