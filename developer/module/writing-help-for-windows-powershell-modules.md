---
title: Windows PowerShell modülleri için Yardım yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082048"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Windows PowerShell Modülleri için Yardım Dosyaları Yazma

Windows PowerShell modülleri ve cmdlet'leri, sağlayıcıları, İşlevler ve betikler gibi modülü üyeleri modülü hakkında Yardım konuları içerebilir. `Get-Help` Cmdlet diğer Windows PowerShell öğeleri için yardımı görüntüler ve kullanıcıların standart bu modülü Yardım konuları aynı biçimde görüntüler `Get-Help` Yardımı almak için komutları.

Bu belge, biçimi ve modül Yardımı doğru yerleşimi açıklar ve yönergeleri modülü Yardım içeriği önerir.

## <a name="types-of-module-help"></a>Tür modülü Yardımı

Bir modül Yardım aşağıdaki türleri içerebilir.

- **Cmdlet yardımına**. Bir modüldeki cmdlet'ler açıklayan Yardım konularının şema komutunu kullanın, XML dosyalarını yardımcı olan

- **Sağlayıcı Yardım**. Yardım sağlayıcıları bir modüle açıklayan Yardım şema sağlayıcısı XML dosyaları konulardır.

- **İşlev Yardım**. Modül içindeki işlevleri açıklayan Yardım konularının komutunu kullanın, XML dosyalarını şema veya açıklama tabanlı Yardım konuları işlev veya komut dosyası veya betik modülündeki yardımcı olabilir

- **Komut Yardımı**. Bir modül betiklerde açıklayan Yardım konuları, şema veya açıklama tabanlı Yardım konuları betik veya betik modülündeki ' komutunu kullanın, XML dosyalarını yardımcı olabilir.

- **("Hakkında") Yardım kavramsal**. ("") Yardım konu hakkında kavramsal modülü ve üyelerini açıklar ve nasıl üyeleri birlikte görevleri gerçekleştirmek için kullanılabilir açıklamak için kullanabilirsiniz. Kavramsal Yardım konuları, kodlama Unicode (UTF-8) ile metin dosyaları olan. Dosya adı kullanmalıdır `about_<name>.help.txt` about_MyModule.help.txt gibi biçimi. Varsayılan olarak, Windows PowerShell üzerinde 100 Bu kavramsal hakkında Yardım konuları içerir ve bunlar aşağıdaki gibi biçimlendirilir.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Yerleşimini modülü Yardımı

`Get-Help` Cmdlet'i modül dizinini, dile özgü alt modülü Yardım konusu dosyaları arar.

Örneğin, aşağıdaki dizin yapısını diyagram SampleModule modül için Yardım konularını konumunu gösterir.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> Örnekte,  *\<ModulePath >* yer tutucusu yollarında birini temsil eder `PSModulePath` $home\Documents\Modules, $pshome\Modules veya kullanıcının belirttiği özel bir yol gibi ortam değişkeni.

## <a name="getting-module-help"></a>Modül Yardım alma

Bir kullanıcı bir modülün oturuma aktardığında, bu modül için Yardım konularını oturumuna modülü ile birlikte içeri aktarılır. Modül bildirimindeki FileList anahtarının değerini Yardım konusu dosyaları listeleyebilirsiniz ancak Yardım konuları etkilenmez `Export-ModuleMember` cmdlet'i.

Farklı dillerde modülü Yardım konuları sağlayabilirsiniz. `Get-Help` Cmdlet'i otomatik olarak görüntüler modülü Yardım konuları için Denetim Masası'nda Bölge ve Dil Seçenekleri öğesi geçerli kullanıcının belirtilen dilde. Windows Vista ve sonraki sürümlerinde, Windows `Get-Help` Yardım konular, dile özgü alt modülü dizin için Windows dil geri dönüş standartlarla uygun olarak arar.

Çalışan Windows PowerShell 3.0 başlayan bir `Get-Help` komutu bir cmdlet veya işlevi için otomatik modül içeri tetikler. `Get-Help` Cmdlet modülünde hemen Yardım konularının içeriğini görüntüler.

Modül, Yardım konuları içermiyor ve hiçbir kullanıcının bilgisayarında modüldeki komutlar için Yardım konularını varsa `Get-Help` otomatik olarak oluşturulan Yardımı görüntüler. Otomatik olarak oluşturulmuş Yardım komut söz dizimi, parametreleri ve girdi ve çıktı türleri içerir, ancak herhangi bir açıklamasını içermez. Otomatik olarak oluşturulmuş Yardım kullanmaya çalıştığınızda kullanıcının yönlendiren metin içeren `Update-Help` cmdlet'ini Internet veya Dosya Paylaşımı'ndan komut için Yardım'ı yükle. Ayrıca kullanmanızı önerir **çevrimiçi** parametresinin `Get-Help` Yardım konusunun çevrimiçi sürümünü almak için cmdlet.

## <a name="supporting-updatable-help"></a>Güncelleştirilebilir Yardımı destekleme

Kullanıcılar, Windows PowerShell 3.0 ve sonraki sürümlerinde Windows PowerShell, indirin ve Internet'ten veya bir yerel dosya paylaşımından bir modül için güncelleştirilmiş Yardım dosyalarını yükleyin. `Update-Help` Ve `Save-Help` cmdlet'leri kullanıcı yönetimi ayrıntıları gizle. Kullanıcıların çalıştırmasını `Update-Help` cmdlet'ini ve ardından `Get-Help` cmdlet Windows PowerShell komut isteminde modülü için en yeni Yardım dosyaları okumak için. Kullanıcılar, Windows veya Windows PowerShell yeniden başlatmanız gerekmez.

Güvenlik duvarları ve Internet erişimi olmayan kullanıcıların güncelleştirilebilir Yardımı de kullanabilirsiniz. Yöneticileri Internet erişimi kullanım `Save-Help` indirmek ve bir dosya paylaşımı için en yeni Yardım dosyaları yüklemek için cmdlet'i. Ardından, kullanıcıların kullanması **yolu** parametresinin `Update-Help` dosya paylaşımından en yeni Yardım dosyaları almak için cmdlet.

Modül yazarları, modüldeki Yardım dosyaları içerir ve Yardım dosyaları güncelleştirmek veya modülünden Yardım dosyaları çıkarın ve yüklemek ve bunları güncelleştirmek için güncelleştirilebilir Yardımı kullanın için güncelleştirilebilir Yardımı'ı kullanın.

Güncelleştirilebilir Yardımı hakkında daha fazla bilgi için bkz: [güncelleştirilebilir Yardımı destekleme](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Çevrimiçi Yardımı destekleme

Olamaz veya yükleme kullanıcıları Yardım dosyalarını bilgisayarlarında genellikle modülü Yardım konuları online sürümüne dayanan güncelleştirildi. **Çevrimiçi** parametresinin `Get-Help` cmdlet'i, bir cmdlet veya Gelişmiş işlevi kullanıcının Yardım konusunun çevrimiçi sürümünü kendi varsayılan Internet tarayıcısında açar.

`Get-Help` Cmdlet'ini kullanır değerini **HelpUri** cmdlet'ini veya işlevin Yardım konusunun çevrimiçi sürümünü bulmak için özellik.

Windows PowerShell 3. 0'den itibaren cmdlet ve işlev Yardım konuları'nın çevrimiçi sürümünü cmdlet'i sınıf üzerinde HelpUri özniteliğini tanımlayarak bulmalarına yardımcı olabilir veya **HelpUri** özelliği **CmdletBinding** özniteliği. Özniteliğin değerini değeridir **HelpUri** cmdlet'ini veya işlevin özelliği.

Daha fazla bilgi için [çevrimiçi Yardımı destekleme](./supporting-online-help.md).

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell modülü yazma](./writing-a-windows-powershell-module.md)

[Güncelleştirilebilir Yardımı destekleme](./supporting-updatable-help.md)

[Çevrimiçi Yardımı destekleme](./supporting-online-help.md)