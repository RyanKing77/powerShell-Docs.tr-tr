---
title: Cmdlet'i genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: f8a8c9300d1ac811c7fbbf7050dd24f78306db8f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068479"
---
# <a name="cmdlet-overview"></a>Cmdlet’e Genel Bakış

Bir cmdlet Windows PowerShell ortamında kullanılan basit bir komuttur. Windows PowerShell çalışma zamanı, bu cmdlet'ler komut satırında sağlanan Otomasyon betikleri bağlamında çağırır. Windows PowerShell çalışma zamanı Ayrıca bunları programlı olarak Windows PowerShell API'leri aracılığıyla çağırır.

## <a name="cmdlets"></a>Cmdlet’ler

Cmdlet'leri bir eylem gerçekleştirin ve genellikle ardışık düzende sonraki komuta bir Microsoft .NET Framework nesnesi döndürür. Bir cmdlet yazmak için iki özel cmdlet'i temel sınıflarının birinden türeyen bir cmdlet'i sınıf uygulamalıdır. Türetilmiş sınıf gerekir:

- Bir cmdlet olarak türetilmiş sınıf tanımlayan bir öznitelik bildirir.

- Cmdlet parametreleri genel özellikleri tanımlayan öznitelikleri ile donatılmış genel özelliklerini tanımlayın.

- Bir veya daha fazla işlem kayıtlarını yöntemlere işlem girişi geçersiz.

Kullanarak doğrudan sınıfı içeren derlemeyi yükleyebilir [Import-Module](/powershell/module/microsoft.powershell.core/import-module) veya cmdlet'ini kullanarak derlemeyi yükleyen bir ana bilgisayar uygulaması oluşturabilirsiniz [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Her iki yöntem işlevselliği cmdlet'inin programlı ve komut satırı erişim sağlar.

## <a name="cmdlet-terms"></a>Cmdlet koşulları

Aşağıdaki terimler Windows PowerShell cmdlet'i belgelerinde sık kullanılır:

- **Cmdlet özniteliği**: Bir cmdlet sınıfı bir cmdlet olarak bildirmek için kullanılan bir .NET Framework özniteliği. Windows PowerShell isteğe bağlı olarak birkaç öznitelik kullansa da, Cmdlet özniteliği gereklidir. Bu özniteliği hakkında daha fazla bilgi için bkz. [cmdlet'i özniteliği bildirimi](./cmdlet-attribute-declaration.md).

- **Cmdlet parametresi**: Kullanıcı veya uygulamaya cmdlet'ini çalıştırarak kullanılabilir parametreleri tanımlayan genel özellikleri. Cmdlet'leri gerekli, adlandırılmış, konumsal, ve *geçiş* parametreleri. Anahtar parametreleri yalnızca arama parametreleri belirtilmemişse değerlendirilir parametreleri tanımlamanızı sağlar. Farklı türde parametreler hakkında daha fazla bilgi için bkz: [Cmdlet parametreleri](./cmdlet-parameters.md).

- **Parametre kümesi**: Belirli bir eylemi gerçekleştirmek için aynı komutta kullanılan parametreler grubudur. Bir cmdlet birden fazla parametre kümesine sahip olabilir, ancak her parametre kümesi benzersiz olan en az bir parametreye sahip olmalıdır. İyi cmdlet'i tasarım kesin benzersiz parametresi gerekli bir parametre olmasını önerir. Parametre kümeleri hakkında daha fazla bilgi için bkz. [cmdlet'i parametre ayarlar](./cmdlet-parameter-sets.md).

- **Dinamik parametre**: Çalışma zamanında cmdlet'ine eklendi parametresi. Genellikle, başka bir parametre belirli bir değere ayarlandığında dinamik parametreler cmdlet'e eklenir. Dinamik parametreler hakkında daha fazla bilgi için bkz. [Cmdlet dinamik parametreleri](./cmdlet-dynamic-parameters.md).

- **Giriş işleme yöntemi**: Bir cmdlet kayıtlarını işlemek için kullanabileceğiniz bir yöntem girdi olarak alır. Giriş işleme yöntemlerden [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi ve [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) yöntemi. Bir cmdlet uygularken en az biri kılmalı [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)ve [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemleri. Genellikle, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemidir cmdlet tarafından işlenen her kayıt için çağrıldığından, geçersiz kılma yöntemi. Buna karşılık, [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) yöntemi ve [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) yöntemi bir kez gerçekleştirmek için çağrılır ön işleme veya kayıtlarını son işlemi. Bu yöntemler hakkında daha fazla bilgi için bkz. [giriş işleme yöntemlerini](./cmdlet-input-processing-methods.md).

- **ShouldProcess özellik**: Windows PowerShell cmdlet, sistemde bir değişiklik yaparsa önce geri bildirim kullanıcıdan cmdlet'leri oluşturmanıza olanak sağlar. Bu özelliği kullanmak için cmdlet, Cmdlet öznitelik bildirmek ve cmdlet çağırmalıdır ShouldProcess özelliği desteklediğini bildirmeniz gerekir [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ve [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) içinde işleme yöntemi giriş yöntemleri. ShouldProcess işlevselliği desteklemek nasıl hakkında daha fazla bilgi için bkz. [onay isteme](./requesting-confirmation-from-cmdlets.md).

- **İşlem**: Tek bir görev kabul edilir komutları mantıksal grubudur. Görev grubundaki herhangi bir komut başarısız ve kullanıcının seçimi kabul etme veya reddetme işlem içinde gerçekleştirilen eylemler varsa otomatik olarak başarısız. Bir işlemde katılmak için cmdlet cmdlet'i öznitelik bildirildiğinde bu işlemleri destekler bildirmeniz gerekir. Katmanı, Windows PowerShell 2.0 sürümünde kullanıma sunulmuştur. İşlemler hakkında daha fazla bilgi için bkz. [Windows PowerShell işlemleri](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710).

## <a name="how-cmdlets-differ-from-commands"></a>Cmdlet'leri komutları farkı

Cmdlet'leri diğer komut kabuğu ortamlarda komutlarından şu bakımlardan ayrılır:

- .NET Framework sınıfları cmdlet'leridir; tek başına yürütülebilir dosyaları değiller.

- Cmdlet'leri bir düzine kod satırlarını olarak oluşturulabilir.

- Genel kullanıma cmdlet kendi ayrıştırma hatası sunu veya çıktı biçimlendirme yapmayın. Ayrıştırma hatası sunu ve çıktı biçimlendirme Windows PowerShell çalışma zamanı tarafından işlenir.

- Ardışık Düzen yerine metnin akışlarından nesneleri cmdlet'leri işlem giriş ve cmdlet'leri nesneleri genellikle işlem hattına çıktı olarak sunun.

- Bir kerede tek bir nesneyi işlemek için kayıt odaklı cmdlet'leri.

## <a name="cmdlet-base-classes"></a>Cmdlet'i temel sınıflar

Windows PowerShell cmdlet'lerini aşağıdaki iki temel sınıflarından türetilen destekler.

- Öğesinden türetilen bir .NET Framework sınıf çoğu cmdlet dayalı [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) temel sınıfı. Bu sınıftan türetme, Windows PowerShell çalışma zamanında en düşük bağımlılıklar kümesini kullanmak bir cmdlet'i sağlar. Bunun iki avantajı vardır. İlk cmdlet nesneleri daha küçüktür ve Windows PowerShell çalışma zamanı değişiklikleri tarafından etkilenmiş olma olasılığını azaltacak avantajdır. İkinci gerekiyorsa, doğrudan cmdlet'i nesnesi örneğini oluşturabilir ve bunu Windows PowerShell çalışma zamanı doğrudan çağırmak yerine çağırmak, avantajdır.

- Öğesinden türetilen .NET Framework sınıfları daha karmaşık cmdlet'leri dayalı [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) temel sınıfı. Bu sınıftan türetme için Windows PowerShell çalışma zamanı çok daha fazla erişim sağlar. Bu erişim sağlayıcıları erişmek ve geçerli bir oturum durumu erişmek için betiklerin çağırmak, cmdlet'i sağlar. (Geçerli oturum durumu erişmek için alma ve oturum değişkenleri ve tercihlerinizi ayarlayın.) Ancak, bu sınıftan türetme cmdlet'i nesnenin boyutunu artırır ve cmdlet'inize, geçerli Windows PowerShell çalışma zamanı sürümüne daha sıkı şekilde bağlı anlamına gelir.

Genişletilmiş Windows PowerShell çalışma zamanı erişmeniz sürece genel olarak, size türetilmesi [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı. Ancak, Windows PowerShell çalışma zamanı cmdlet'leri yürütülmesi için kapsamlı günlüğe kaydetme özellikleri vardır. Bu günlük denetim modelinizi bağımlı olması durumunda, türeterek içinde başka bir cmdlet cmdlet'inize yürütülmesini engelleyebilirsiniz [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) sınıfı.

## <a name="input-processing-methods"></a>Giriş yöntemleri işleme

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) sınıfı kayıtlarını işlemek için kullanılan aşağıdaki sanal yöntemler sağlar. Tüm türetilmiş cmdlet'i sınıflar, bir veya daha önce üç yöntemi geçersiz kılmanız gerekir:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Cmdlet'i için isteğe bağlı bir kerelik, ön işleme işlevleri sağlamak için kullanılır.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Cmdlet'i için kayıt kayıt işleme işlevleri sağlamak için kullanılır. [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) yöntemi herhangi bir sayı sayısı veya hiç, giriş cmdlet'inin bağlı olarak çağrılabilir.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Cmdlet'i için tek seferlik işlem sonrası isteğe bağlı işlevselliği sağlamak için kullanılır.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Kullanıcı (örneğin, CTRL + C tuşlarına basarak) cmdlet zaman uyumsuz olarak durduğunda. durdurmak için kullanılır.

Bu yöntemler hakkında daha fazla bilgi için bkz. [cmdlet'i giriş işleme yöntemlerini](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Cmdlet Öznitelikleri

Windows PowerShell cmdlet'leri yönetmek ve Windows PowerShell tarafından sağlanan ve, cmdlet tarafından gerekli olabilecek ortak işlevselliği belirtmek için kullanılan birkaç .NET Framework öznitelikleri tanımlar. Örneğin, öznitelikler, bir sınıf cmdlet parametreleri belirtin ve böylece cmdlet'i geliştiriciler cmdlet'i kodlarını söz konusu işlevselliği uygulamak izniniz yok, giriş doğrulama istemek için bir cmdlet olarak belirlemek için kullanılır. Öznitelikler hakkında daha fazla bilgi için bkz. [Windows PowerShell öznitelikleri](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Cmdlet adları

Windows PowerShell bir fiil-isim adı çifti adı cmdlet'leri kullanır. Örneğin, `Get-Command` dahil Windows PowerShell'de bir cmdlet komut kabuğu'nda kayıtlı olan tüm cmdlet'ler almak için kullanılır. Cmdlet gerçekleştiren Eylem fiili tanımlar ve isim cmdlet eylemi gerçekleştiren kaynak belirler.

.NET Framework sınıf cmdlet'ini olarak bildirildiğinde bu adlar belirtilir. Bir cmdlet olarak bir .NET Framework sınıf bildirme hakkında daha fazla bilgi için bkz: [cmdlet'i özniteliği bildirimi](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Cmdlet kod yazma

Bu belge cmdlet kod nasıl yazılır bulmak için iki yol sunar. Kodu olmadan kadar bir açıklama görmek isterseniz, bkz. [Cmdlet kod örnekleri](./examples-of-cmdlet-code.md). Kod hakkında daha fazla açıklama tercih ediyorsanız, bkz [GetProc öğretici](./getproc-tutorial.md), [StopProc öğretici](./stopproc-tutorial.md), veya [SelectStr öğretici](./selectstr-tutorial.md) konuları.

Yazma cmdlet'leri için yönergeleri hakkında daha fazla bilgi için bkz. [cmdlet'i geliştirme yönergeleri](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell cmdlet'i kavramları](./windows-powershell-cmdlet-concepts.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
