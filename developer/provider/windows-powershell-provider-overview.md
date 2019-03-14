---
title: Windows PowerShell sağlayıcısındaki genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 0d4addc0a064873701ae15c204dbd335f3374ab7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795632"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell Sağlayıcısına Genel Bakış

Bir Windows PowerShell sağlayıcısı herhangi bir veri deposu bağlı sürücü gibi bir dosya sistemi gibi gösterilmesine izin verir. Örneğin, yerleşik kayıt defteri sağlayıcısı kayıt defterine gidin gibi gitmenizi sağlar `c` bilgisayarınızın sürücü. Sağlayıcı geçersiz de kılabilirsiniz `Item` cmdlet'leri (örneğin, `Get-Item`, `Set-Item`, vs.), veri deposundaki dosyaları gibi ele alınabilir ve bir dosya sistemi gezinirken dizinleri kabul edilir. Sağlayıcılar ve sürücüleri ve Windows PowerShell'de yerleşik sağlayıcılar hakkında daha fazla bilgi için bkz. [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Sağlayıcılar ve sürücüler

Erişim, gidin ve bir sürücüye sağlayıcı tarafından tanımlanan türde bir özel giriş noktası bir veri deposu (veya bir veri deposu bölümü) belirtirken bir veri deposu düzenlemek için kullanılan mantıksal bir sağlayıcı tanımlar. Örneğin, kayıt defteri sağlayıcısı yığınlarını ve bir kayıt defteri anahtarları erişmenize olanak sağlar ve kayıt defteri içinde karşılık gelen yığınlarını HKLM ve HKCU sürücüleri belirtin. HKLM ve HKCU sürücüleri, kayıt defteri sağlayıcısını kullanın.

Bir sağlayıcı yazdığınızda, varsayılan sürücüleri-sağlayıcısı kullanılabilir olduğunda otomatik olarak oluşturulan sürücüsü belirtebilirsiniz. Ayrıca, bu sağlayıcısı kullanan yeni sürücüleri oluşturmak için bir yöntem de tanımlayın.

## <a name="type-of-providers"></a>Tür sağlayıcıları

Sağlayıcıların her biri farklı düzeyde işlevsellik sağlayan birkaç türü vardır. Alt öğeleri birinden türetilen bir sınıf olarak uygulanan bir sağlayıcı [System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider) sınıfı. Sağlayıcıların farklı türleri hakkında daha fazla bilgi için bkz: [sağlayıcısı türleri](./provider-types.md).

## <a name="provider-cmdlets"></a>Sağlayıcı cmdlet’leri

Sağlayıcıları bu sağlayıcı için bir sürücü kullanıldığında bu cmdlet için özel davranışlar oluşturma cmdlet'leri için karşılık gelen yöntemleri uygulayabilirsiniz. Sağlayıcı türüne bağlı olarak farklı bir cmdlet kümesi kullanılabilir. Özelleştirme sağlayıcıları için kullanılabilir cmdlet'lerin tam listesi için bkz. [sağlayıcısı cmdlet'leri](./provider-cmdlets.md).

## <a name="provider-paths"></a>Sağlayıcı yolları

Kullanıcılar, dosya sistemleri gibi sağlayıcısı sürücüleri gidin. Bu nedenle, dosya sistemi gezintisi içinde kullanılan yollara karşılık gelen yollar söz dizimi beklerler. Bir kullanıcı bir sağlayıcı cmdlet çalıştırdığında, bunlar erişilecek öğesi için bir yol belirtin. Belirtilen yolun birkaç şekilde yorumlanabilir. Bir sağlayıcı, bir veya daha fazla yol türlerinden birini desteklemelidir.

### <a name="drive-qualified-paths"></a>Sürücü nitelenmiş yollar

Sürücü nitelenmiş bir yolu, öğe adı, kapsayıcı ve öğenin bulunduğu alt kapsayıcılar ve öğesi erişilen Windows PowerShell sürücüsünü birleşimidir. (Sürücü veri deposuna erişmek için kullanılan sağlayıcı tarafından tanımlanır. Bu yol, izleyen iki nokta (:) sürücü adı ile başlar. Örneğin: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Sağlayıcı nitelenmiş yollar

Windows PowerShell altyapısı başlatıp sağlayıcınız kapatması izin vermek için sağlayıcı sağlayıcısı nitelenmiş bir yol desteklemesi gerekir. Örneğin, kullanıcı başlatın ve aşağıdaki sağlayıcısı tam yolunu tanımlar çünkü dosya sistemi sağlayıcısı geri alınıyor: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Sağlayıcı doğrudan yolları

Windows PowerShell sağlayıcınız uzaktan erişime izin vermek için doğrudan Windows PowerShell sağlayıcısı için geçerli konumun geçirmek için bir sağlayıcı doğrudan yolu desteklemelidir. Örneğin, kayıt defteri Windows PowerShell sağlayıcısını kullanabilirsiniz `\\server\regkeypath` sağlayıcısı doğrudan yol.

### <a name="provider-internal-paths"></a>Sağlayıcı İç yolları

Sağlayıcı cmdlet'ini kullanarak Windows PowerShell uygulama programlama arabirimleri (API) veri erişim izin vermek için Windows PowerShell sağlayıcısındaki sağlayıcısı iç yolu desteklemelidir. Bu yolu sonra gösterilen "::" Sağlayıcı nitelikli yolda. Örneğin, dosya sistemi Windows PowerShell sağlayıcısı için sağlayıcı iç yolu olan `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Cmdlet parametrelerini geçersiz kılma

Bazı sağlayıcıya özgü cmdlet'lerin davranışını bir sağlayıcı tarafından geçersiz kılınabilir. Geçersiz kılınabilir parametreler ve bunları sağlayıcısı sınıfınızda geçersiz kılma için bkz. [sağlayıcısı cmdlet parametreleri](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Dinamik parametreler

Sağlayıcıları cmdlet'inin statik parametrelerden biri için belirli bir değer kullanıcının belirttiği alındığında, bir sağlayıcı cmdlet'e eklenen dinamik parametreleri tanımlayabilirsiniz. Bir veya daha fazla dinamik parametre yöntemleri uygulayarak bir sağlayıcı bunu yapar. Dinamik parametre ve bunları uygulamak için kullanılan yöntemler eklemek için kullanılan cmdlet parametreleri listesi için bkz. [sağlayıcısı cmdlet dinamik parametreleri](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Sağlayıcı özellikleri

[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) numaralandırma birkaç sağlayıcıları destekleyebilir özelliği tanımlar. Bunlar, joker karakterleri kullan, öğeleri filtrelemek ve Destek işlemleri özelliği içerir. Özellikleri için bir sağlayıcı belirtmek için değerleri listesi ekleme [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) numaralandırma, bir mantıksal ile birleştirilmiş `OR` işlemi olarak [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) özelliğini (özniteliğinin ikinci parametresi) [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) sağlayıcısı sınıfınız için özniteliği. Örneğin, aşağıdaki öznitelik sağlayıcının desteklediği belirtir [System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess) ve [ System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions) özellikleri.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Sağlayıcı cmdlet Yardımı

Bir sağlayıcı yazarken, kendi Yardım için destek sağlayıcısı cmdlet'leri uygulayabilirsiniz. Bu, tek bir Yardım konusu her sağlayıcısı cmdlet'i veya bir Yardım konusu burada sağlayıcısı cmdlet davranır durumlarda farklı dinamik parametre kullanım dayanarak birden çok sürümünü içerir. Sağlayıcı cmdlet'e özel Yardım desteklemek için sağlayıcınıza uygulamalıdır [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) arabirimi.

Windows PowerShell altyapısının çağrıları [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) , sağlayıcısı cmdlet'leri için Yardım konusuna görüntülemek için yöntemi. Kullanıcı çalıştırılırken belirtilen cmdlet adı altyapısı sağlar `Get-Help` cmdlet'i ve kullanıcının geçerli yolu. Sağlayıcınız aynı sağlayıcı cmdlet'i farklı sürücüleri için farklı sürümlerini uyguluyorsa geçerli yolu gereklidir. Yöntemi, cmdlet Yardım için XML içeren bir dize döndürmelidir.

Yardım dosyası içeriğini PSMAML XML kullanarak yazılır. Tek başına cmdlet'leri için Yardım içeriği yazmak için kullanılan aynı XML şema budur. Özel cmdlet'inize sağlayıcınız için Yardım dosyasına Yardım içeriğini Ekle altında `CmdletHelpPaths` öğesi. Aşağıdaki örnekte gösterildiği `command` öğesi için bir sağlayıcı cmdlet ve gösterir sağlayıcısı cmdlet'in adını nasıl belirttiğiniz, sağlayıcınız. Destekler

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sağlayıcısındaki işlevselliği](./provider-types.md)

[Sağlayıcısı cmdlet'leri](./provider-cmdlets.md)

[Bir Windows PowerShell sağlayıcısı yazma](./writing-a-windows-powershell-provider.md)