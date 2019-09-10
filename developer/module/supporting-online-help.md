---
title: Çevrimiçi yardımı destekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848082"
---
# <a name="supporting-online-help"></a>Çevrimiçi Yardımı Destekleme

Windows PowerShell 3,0 ' den başlayarak, Windows PowerShell komutlarının `Get-Help` çevrimiçi özelliğini desteklemeye yönelik iki yol vardır. Bu konu, farklı komut türleri için bu özelliğin nasıl uygulanacağını açıklar.

## <a name="about-online-help"></a>Çevrimiçi Yardım hakkında

Çevrimiçi yardım her zaman Windows PowerShell 'in önemli bir parçasıdır. `Get-Help` Cmdlet 'i komut isteminde Yardım konularını görüntülüyor olsa da birçok kullanıcı, topluluk içerikleriyle ve wiki tabanlı belgelerde renk kodlama, köprüler ve paylaşma fikirleri dahil olmak üzere çevrimiçi okuma deneyimini tercih eder. En önemlisi, güncelleştirilebilir yardım 'dan önce, yardım dosyalarının en güncel sürümünü sağlamadan önce çevrimiçi yardım.

Windows PowerShell 3,0 ' de güncelleştirilebilir yardım ile ilgili, çevrimiçi yardım hala önemli bir rol oynar. Esnek kullanıcı deneyiminin yanı sıra, çevrimiçi yardım, yardım konularını indirmek için güncelleştirilebilir yardımı kullanmayan veya kullanmayan kullanıcılara yardım sağlar.

## <a name="how-get-help--online-works"></a>Get-Help-online nasıl Işe yarar?

Kullanıcıların, komutlara yönelik çevrimiçi Yardım konularını bulmasına yardımcı olmak için, `Get-Help` kullanıcının varsayılan Internet tarayıcısında bir komutla ilgili Yardım konusunun çevrimiçi sürümünü açan bir çevrimiçi parametresi vardır.

Örneğin, aşağıdaki komut, `Invoke-Command` cmdlet 'i için çevrimiçi Yardım konusunu açar.

```powershell
Get-Help Invoke-Command -Online
```

-Online `Get-Help` `Get-Help` 'ı uygulamak için, cmdlet aşağıdaki konumlarda yer alarak çevrimiçi sürüm yardım konusu için bir Tekdüzen Kaynak tanımlayıcısı (URI) arar.

- Komutun Yardım konusunun Ilgili bağlantılar bölümündeki ilk bağlantı. Yardım konusunun kullanıcının bilgisayarında yüklü olması gerekir. Bu özellik Windows PowerShell 2,0 ' de tanıtılmıştır.

- Herhangi bir komutun HelpUri özelliği. HelpUri özelliği, komutun yardım konusu Kullanıcı bilgisayarında yüklü olmadığında bile erişilebilir. Bu özellik Windows PowerShell 3,0 ' de tanıtılmıştır.

  `Get-Help`HelpUri özellik değerini almadan önce Ilgili bağlantılar bölümündeki ilk girişte bir URI arar. Özellik değeri yanlışsa veya değiştiyse, ilk Ilgili bağlantıya farklı bir değer girerek onu geçersiz kılabilirsiniz. Ancak, ilk Ilişkili bağlantı yalnızca kullanıcının bilgisayarına yardım konuları yüklendiğinde işe yarar.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Komut Yardım konusunun ilk ilgili bağlantısına URI ekleme

Komutu için XML `Get-Help` tabanlı Yardım konusunun ilgili bağlantılar bölümündeki ilk girişe geçerli bir URI ekleyerek, herhangi bir komut için-online 'ı destekleyebilirsiniz. Bu seçenek yalnızca, XML tabanlı yardım konularında geçerlidir ve yalnızca kullanıcının bilgisayarında yardım konusu yüklendiğinde kullanılır. Yardım konusu yüklendiğinde ve URI doldurulduğu zaman, bu değer komutun **HelpUri** özelliğinden önceliklidir.

Bu özelliği desteklemek için URI 'nin `maml:uri` `maml:relatedLinks` öğedeki ilk `maml:relatedLinks/maml:navigationLink` öğe altındaki öğesinde görünmesi gerekir.

Aşağıdaki XML URI 'nin doğru yerleşimini gösterir. `maml:linkText` Öğedeki "Çevrimiçi sürüm:" metni en iyi uygulamadır, ancak gerekli değildir.

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

## <a name="adding-the-helpuri-property-to-a-command"></a>Bir komuta HelpUri özelliğini ekleme

Bu bölümde, HelpUri özelliğinin farklı türlerin komutlarına nasıl ekleneceği gösterilmektedir.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Bir cmdlet 'e HelpUri özelliği ekleme

İçinde C#yazılan cmdlet 'ler Için, cmdlet sınıfına bir **helpurı** özniteliği ekleyin. Özniteliğin değeri "http" veya "https" ile başlayan bir URI olmalıdır.

Aşağıdaki kod, `Get-History` cmdlet sınıfının HelpUri özniteliğini gösterir.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Gelişmiş Işleve HelpUri özelliği ekleme

Gelişmiş işlevler için, **CmdletBinding** özniteliğine bir **HelpUri** özelliği ekleyin. Özelliğin değeri, "http" veya "https" ile başlayan bir URI olmalıdır.

Aşağıdaki kod, New-Calendar işlevinin HelpUri özniteliğini gösterir

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>CıM komutuna Helpurı özniteliği ekleme

CıM komutları için CDXML dosyasındaki **Cmdletmetadata** öğesine bir **helpurı** özniteliği ekleyin. Özniteliğin değeri "http" veya "https" ile başlayan bir URI olmalıdır.

Aşağıdaki kod, Start-Debug CıM komutunun HelpUri özniteliğini gösterir

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Bir Iş akışına Helpurı özniteliği ekleme

Windows PowerShell dilinde yazılmış iş akışları için bir ekleyin **.** İş akışı koduna ExternalHelp açıklama yönergesi. Yönergesinin değeri, "http" veya "https" ile başlayan bir URI olmalıdır.

> [!NOTE]
> HelpUri özelliği, Windows PowerShell 'de XAML tabanlı iş akışları için desteklenmez.

Aşağıdaki kod, gösterir. Bir iş akışı dosyasında ExternalHelp yönergesi.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```