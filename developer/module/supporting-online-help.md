---
title: Çevrimiçi Yardımı destekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848156"
---
# <a name="supporting-online-help"></a>Çevrimiçi Yardımı Destekleme

Windows PowerShell 3. 0'den itibaren desteklemek için iki yolu vardır `Get-Help` Windows PowerShell komutları için çevrimiçi özelliği. Bu konuda, farklı komut türleri için bu özelliği uygulamanız açıklanmaktadır.

## <a name="about-online-help"></a>Çevrimiçi Yardım hakkında

Çevrimiçi Yardım her zaman Windows PowerShell sürecinin hayati bir parçası olmuştur. Ancak `Get-Help` cmdlet Yardım konuları komut isteminde görüntüler, birçok kullanıcı deneyimi çevrimiçi okuma, renk kodlaması, köprüler ve topluluk içeriği ve belgeleri wiki tabanlı paylaşım fikirler dahil olmak üzere tercih eder. En önemlisi de güncelleştirilebilir Yardımı gelişinden önce Yardım dosyaları en güncel sürümüne çevrimiçi Yardım sağlanır.

Güncelleştirilebilir Yardımı'ndaki Windows PowerShell 3.0 gelişinden ile çevrimiçi Yardım yine de önemli bir rol oynar. Esnek kullanıcı deneyiminin yanı sıra çevrimiçi Yardım olmayan veya Yardım konuları indirmek için güncelleştirilebilir Yardımı kullanamazsınız kullanıcıları için Yardım sağlar.

## <a name="how-get-help--online-works"></a>Nasıl Get-Help-Online çalışır

Komutlar için çevrimiçi Yardım konularını bulmalarına yardımcı olmak için `Get-Help` komutu bir komut için Yardım konusunun çevrimiçi sürümünü kullanıcının varsayılan Internet tarayıcısında açar. çevrimiçi bir parametresi vardır.

Örneğin, aşağıdaki komutu için çevrimiçi Yardım konusuna açılır `Invoke-Command` cmdlet'i.

```powershell
Get-Help Invoke-Command -Online
```

Uygulamak için `Get-Help` -çevrimiçi `Get-Help` cmdlet'i için bir Tekdüzen Kaynak Tanımlayıcısı (URI) çevrimiçi sürümünü Yardım konusunun aşağıdaki konumlarda arar.

- Komut için Yardım konusunun ilgili bağlantılar bölümündeki ilk bağlantıyı. Yardım konusu kullanıcının bilgisayarında yüklü olmalıdır. Bu özellik, Windows PowerShell 2.0 kullanılmaya başlandı.

- HelpUri özellik, herhangi bir komutu. HelpUri özellik bile komut için Yardım konusu kullanıcının bilgisayarında yüklü değilken erişilebilir. Bu özellik, Windows PowerShell 3. 0 ' sunulmuştur.

  `Get-Help` HelpUri özellik değerinin almadan önce bir URI ilgili bağlantılar bölümündeki ilk giriş arar. Özellik değeri yanlış veya değiştirildiyse, ilk ilgili bağlantıyı farklı bir değer girerek geçersiz kılabilirsiniz. Ancak, yalnızca Yardım konularının kullanıcının bilgisayarında yüklü olduğunda ilk ilgili bağlantıyı çalışır.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Komutun Yardım konusunun ilgili ilk bağlantı için bir URI ekleme

Destekleyebilirsiniz `Get-Help` -Online komutu için XML tabanlı Yardım konusunun ilgili bağlantılar bölümündeki ilk giriş geçerli bir URI ekleyerek herhangi bir komutu. Bu seçenek yalnızca XML tabanlı Yardım konularında geçerlidir ve yalnızca kullanıcının bilgisayarında Yardım konusuna yüklendiğinde çalışır. Yardım konusu URI doldurulur aldığında, bu değer önceliklidir **HelpUri** özelliği komutu. Komutları için XML tabanlı Yardım konuları hakkında daha fazla bilgi için bkz. [Writing XML-Based komutlar için Yardım konularını](../help/writing-xml-based-help-topics-for-commands.md).

Bu özelliği desteklemek için URI görünmelidir `maml:uri` altına ilk öğe `maml:relatedLinks/maml:navigationLink` öğesinde `maml:relatedLinks` öğesi.

Aşağıdaki XML URI'nin doğru yerleştirme gösterir. "Çevrimiçi sürüm:" metin `maml:linkText` öğesi en iyi bir uygulamadır, ancak gerekli değildir.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>HelpUri özellik için bir komut ekleme

Bu bölüm, farklı türlerdeki komutları HelpUri özelliğini eklemek gösterilmektedir.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Bir Cmdlet için HelpUri özellik ekleme

Yazılmış cmdlet'lerinin C#, ekleme bir **HelpUri** cmdlet'i sınıfı özniteliği. Özniteliğinin değeri "http" veya "https" ile başlayan bir URI olmalıdır.

Aşağıdaki kod HelpUri özniteliğini gösterir `Get-History` cmdlet'i sınıfı.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Gelişmiş bir işleve HelpUri özellik ekleme

Gelişmiş işlevler için ekleme bir **HelpUri** özelliğini **CmdletBinding** özniteliği. Özelliğinin değeri "http" veya "https" ile başlayan bir URI olmalıdır.

Aşağıdaki kod New-Takvim işlevinin HelpUri özniteliğini gösterir.

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>HelpUri özniteliğini CIM komut ekleme

CIM komutları için ekleme bir **HelpUri** özniteliğini **CmdletMetadata** CDXML dosyasındaki öğesi. Özniteliğinin değeri "http" veya "https" ile başlayan bir URI olmalıdır.

Aşağıdaki kod hata ayıklama başlangıç CIM komut HelpUri özniteliğini gösterir.

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>HelpUri özniteliğini bir iş akışına ekleme

Windows PowerShell dilinde yazılır, iş akışları için ekleme bir **. ExternalHelp** iş akışı kodu comment yönergesi. Yönerge değerini "http" veya "https" ile başlayan bir URI olmalıdır.

> [!NOTE]
> HelpUri özellik iş akışı XAML tabanlı Windows PowerShell için desteklenmiyor.

Aşağıdaki kod gösterir. Bir iş akışı dosyasındaki ExternalHelp yönergesi.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```