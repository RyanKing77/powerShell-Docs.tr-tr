---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC için Linux nxFile kaynağı
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225718"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC için Linux nxFile kaynağı

**NxFile** içinde PowerShell Desired State Configuration (DSC) kaynak dosyalar ve dizinler Linux düğümde yönetmek için bir mekanizma sağlar.

## <a name="syntax"></a>Sözdizimi

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Özellikler

|  Özellik |  Açıklama |
|---|---|
| DestinationPath| Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.|
| Kaynak yolu| Dosya veya klasör kaynak kopyalanacak yolunu belirtir. Bu yol, yerel bir yol olabilir veya bir `http/https/ftp` URL'si. Uzak `http/https/ftp` URL'leri, yalnızca desteklenen zaman değerini **türü** özelliği dosyasıdır.|
| Emin olun| Dosyanın mevcut olup olmadığını denetleyin belirler. "Var" dosyası var. olmak için bu özelliği ayarlayın. Kümesi "Yok" dosya sağlamak için mevcut değil. "Var" varsayılan değerdir.|
| Tür| Yapılandırılan kaynak bir dizin veya bir dosya olup olmadığını belirtir. Bu özelliği kaynak dizin olduğunu belirtmek için "dizin" olarak ayarlayın. "Kaynak bir dosya olduğunu belirtmek için dosya için" olarak ayarlayın. "Dosya" varsayılan değer:|
| İçerikler| Belirli bir dize gibi bir dosyanın içeriğini belirtir.|
| Sağlama| İki dosya aynı olup olmadığını belirlerken kullanılacak türünü tanımlar. Varsa **sağlama toplamı** belirtilmezse, yalnızca dosya veya dizin adı, karşılaştırma için kullanılır. Değerler: "ctime", "mtime" veya "md5".|
| Recurse| Alt dizinleri dahil olup olmadığını gösterir. Bu özellik kümesine **$true** dahil edilmesi için alt dizinler istediğinizi belirtmek için. Varsayılan değer **$false**. **Not:** bu özellik yalnızca geçerlidir **türü** özelliği dizinine ayarlanır.|
| Force| Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizini silme) bir hataya neden olur. Kullanarak **zorla** özelliği, bu tür hatalar'ı geçersiz kılar. Varsayılan değer **$false**.|
| Bağlantılar| Sembolik bağlantılar için istenen davranışı belirtir. "Sembolik bağlantıları izleyin ve bağlantı hedef (örn. işlem yapma izlemek için" Bu özelliği ayarlayın bağlantı yerine dosya kopyalama). "Bağlantıya (ör. davranacak şekilde yönetmek için" Bu özelliği ayarlayın bağlantıya Kopyala). "Simgesel bağlantılar yoksaymak için yoksay'a için" Bu özelliği ayarlayın.|
| Grup| Adını **grubu** dosya veya dizin sahibi.|
| Mod| Sekizlik veya sembolik gösterimde, kaynak için izinleri belirtir. (örneğin, 777 veya rwxrwxrwx). Sembolik gösterimini kullanarak, dizin veya dosya gösteren ilk karakteri sağlamaz.|
| DependsOn | Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir. Örneğin, varsa **kimliği** kaynağın çalıştırmak istediğiniz yapılandırma komut dosyası bloğu ilk. **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Ek Bilgi


Linux ve Windows farklı satır sonu karakterleri metin dosyalarında varsayılan olarak ve bunun bazı dosyaları bir Linux bilgisayarda yapılandırılırken beklenmeyen sonuçlara neden olabilir __nxFile__. Beklenmeyen satır sonu karakterleri tarafından neden olduğu sorunları kaçınarak Linux dosyası içeriğini yönetmek için birden çok yolu vardır:

1. adım: bir uzak kaynaktan (http, https veya ftp) dosya kopyala: İstenen içeriği ile Linux üzerinde bir dosya oluşturun ve yapılandıracağınız düğümde bir web veya ftp sunucusunda erişilebilir hazırlayın. Tanımlama __SourcePath__ özelliğinde __nxFile__ kaynak dosyanın web veya ftp URL'si ile.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


2. adım: PowerShell betiğiyle dosyanın içeriğini okumak [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) ayarlanmasından sonra __$OFS__ Linux satır sonu karakteri kullanmak için özelliği.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


3. adım: Windows satır sonları ile Linux satır sonu karakterleri değiştirmek için bir PowerShell işlevi kullanın.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a>Örnek

Aşağıdaki örnek dizinin sağlar `/opt/mydir` var ve bir dosyanın belirtilen içeriğiyle bu dizinin var olduğunu.

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```