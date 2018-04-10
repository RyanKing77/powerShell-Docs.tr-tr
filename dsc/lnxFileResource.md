---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, yapılandırma, Kur
title: DSC Linux nxFile kaynak için
ms.openlocfilehash: 41b5ebde299c47b38d7a6e7f71607332b24ca0e4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC Linux nxFile kaynak için

**NxFile** kaynak olarak PowerShell istenen durum yapılandırması (DSC) dosyaları ve dizinleri Linux düğümde yönetmek üzere bir mekanizma sağlar.

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
| HedefYolu| Bir dosya veya dizin durumu sağlamak istediğiniz konumu belirtir.|
| Kaynak yolu| Dosya veya klasör kaynak kopyalanacak yolunu belirtir. Bu yol, yerel bir yol olabilir veya bir `http/https/ftp` URL. Uzak `http/https/ftp` URL'leri, yalnızca zaman desteklenen değerini **türü** özelliği dosyasıdır.|
| Emin olun| Dosyanın var olup olmadığını denetlemek belirler. Bu özelliği dosyanın var olduğundan emin olmak için "var" olarak ayarlayın. "Mevcut için" dosya yok emin olmak için ayarlayın. "Var" varsayılan değerdir.|
| Tür| Yapılandırılmakta kaynak bir dizin veya bir dosya olup olmadığını belirtir. Bu özelliği kaynak bir dizin olduğunu belirtmek için "dizin" olarak ayarlayın. Kaynak dosya olduğunu belirtmek için "dosyası için" olarak ayarlayın. "Dosya" varsayılan değer:|
| İçerikler| Belirli bir dize gibi bir dosyanın içeriğini belirtir.|
| Sağlama| İki dosya aynı olup olmadığını belirlerken kullanılacak türünü tanımlar. Varsa **sağlama toplamı** belirtilmezse, yalnızca dosya veya dizin adı karşılaştırma için kullanılır. Değerler: "ctime", "mtime" veya "md5".|
| Recurse| Alt dizinleri dahil olup olmadığını gösterir. Bu özelliği ayarlamak **$true** dahil edilmesi için alt dizinler istediğinizi belirtmek için. Varsayılan değer **$false**. **Not:** bu özellik yalnızca geçerlidir **türü** özelliği dizinine ayarlanır.|
| Force| Belirli dosya işlemleri (örneğin, bir dosyanın üzerine veya boş olmayan bir dizin silme) bir hatayla sonuçlanır. Kullanarak **zorla** özelliği gibi hataları geçersiz kılar. Varsayılan değer **$false**.|
| Bağlantılar| Sembolik bağlantılar için istenen davranış belirtir. "Sembolik bağlantılar izleyin ve bağlantıları hedefe (örneğin, hareket izlemek için" Bu özelliği ayarlayın bağlantı yerine dosya Kopyala). "Bağlantısına (örneğin, davranacak şekilde yönetmek için" Bu özelliği ayarlayın Bağlantıyı Kopyala). "Sembolik bağlantılar yoksaymak için yoksay'a için" Bu özelliği ayarlayın.|
| Grup| Adını **grup** dosya veya dizin sahibi.|
| Mod| Kaynak için istenen izinleri sekizli veya sembolik gösterimde belirtir. (örneğin, 777 veya rwxrwxrwx). Simgesel gösterimini kullanarak, dizin veya dosya gösteren ilk karakter sağlamaz.|
| dependsOn | Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir. Örneğin, varsa **kimliği** çalıştırmak istediğiniz yapılandırma betik bloğu ilk kaynaktır **ResourceName** ve türünü **ResourceType**, bunu kullanarak söz dizimi özellik `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Ek Bilgi


Linux ve Windows kullanın farklı satır sonu karakterleri metin dosyalarında varsayılan olarak, ve bu bazı dosyaları ile Linux bilgisayarda yapılandırılırken beklenmeyen sonuçlara neden olabilir __nxFile__. Beklenmeyen satır sonu karakterleri tarafından nedeniyle oluşan sorunları kaçınarak Linux dosyasının içeriği yönetmek için birden çok yolu vardır:

1. adım: dosyayı bir uzak kaynaktan (http, https veya ftp) kopyalayın: İstenen içeriği ile Linux üzerinde bir dosya oluşturun ve bir web veya ftp sunucusunda erişilebilir yapılandıracağınız düğümlerini hazırlama. Tanımlamak __KaynakYolu__ özelliğinde __nxFile__ kaynak dosyasının web veya ftp URL'si ile.

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


2. adım: PowerShell Betiği ile dosya içeriğini okuma [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) ayarlanmasından sonra __$OFS__ Linux satır sonu karakteri kullanmak için özelliği.


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


3. adım: Windows satır sonları ile Linux satır sonu karakterleri değiştirmek için bir PowerShell işlevini kullanın.

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

Aşağıdaki örnek dizini sağlar `/opt/mydir` var olduğundan ve belirtilen içeriği dosyasıyla bu dizin mevcut.

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