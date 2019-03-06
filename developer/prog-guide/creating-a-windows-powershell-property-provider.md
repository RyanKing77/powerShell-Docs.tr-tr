---
title: Bir Windows PowerShell özelliği sağlayıcı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: 4ed15dabffa933dee9becf2f839887eb9108775d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430018"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Windows PowerShell Özellik Sağlayıcısı Oluşturma

Bu konuda, bir veri deposuna öğelerin özelliklerini değiştirmek kullanıcının sağlayan bir sağlayıcı oluşturmayı açıklar. Sonuç olarak, bu tür sağlayıcısı için Windows PowerShell özelliği sağlayıcısı olarak adlandırılır. Örneğin, kayıt defteri sağlayıcısı kayıt defteri anahtarı öğesi özelliklerini Windows PowerShell tanıtıcıları kayıt defteri anahtarı değerleri tarafından sağlanan. Bu tür sağlayıcısı eklemelisiniz [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) .NET sınıfın uygulaması için arabirim.

> [!NOTE]
> Windows PowerShell, Windows PowerShell sağlayıcısındaki geliştirmek için kullanabileceğiniz bir şablon dosyası sağlar. .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista üzerinde kullanılabilir TemplateProvider.cs dosyasıdır. Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen şablon kullanılabilir  **\<PowerShell örnekleri >** dizin. Bu dosyanın bir kopyasını alın ve gerekmeyen işlevleri kaldırma yeni bir Windows PowerShell sağlayıcısı oluşturmak için kopyalama kullanmalısınız.
>
> Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Özellik sağlayıcınız yöntemlerini kullanarak herhangi bir nesne yazmalısınız [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) yöntemi.

Aşağıdaki liste, bu konudaki bölümler içerir. Bir Windows PowerShell özelliği sağlayıcısı yazma ile alışkın değilseniz, bu bilgileri göründüğü sırayla okuyun. Ancak, bir Windows PowerShell özelliği sağlayıcısı yazma ile bilginiz varsa, lütfen gereksinim duyduğunuz bilgileri doğrudan gidin.

- [Windows PowerShell sağlayıcısını tanımlama](#Defining-the-Windows-PowerShell-provider)

- [Temel işlevlerini tanımlama](#Defining-Base-Functionality)

- [Özellikleri alınıyor](#Retrieving-Properties)

- [Dinamik parametreleri ekleme `Get-ItemProperty` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Özellikleri ayarlama](#Setting-Properties)

- [Dinamik parametreleri ekleme `Set-ItemProperty` cmdlet'i](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [Bir özelliği temizleniyor](#Clearing-Properties)

- [Dinamik parametreleri ekleme `Clear-ItemProperty` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Windows PowerShell sağlayıcısı oluşturma](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcısını tanımlama

Bir özellik sağlayıcısı, destekleyen bir .NET sınıfı oluşturmalısınız [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) arabirimi. Aşağıda, Windows PowerShell tarafından sağlanan TemplateProvider.cs dosyasından varsayılan sınıf bildirimi verilmiştir.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Temel işlevlerini tanımlama

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) arabirimi eklenebilir herhangi bir sağlayıcı temel sınıfı, dışında [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı. Kullanmakta olduğunuz taban sınıfı tarafından gerekli olan temel işlevleri ekleyin. Temel sınıflar hakkında daha fazla bilgi için bkz: [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Özellikleri alınıyor

Sağlayıcı özelliklerini almak için uygulamalıdır [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) çağrılarından desteklemek için gereken yöntemini `Get-ItemProperty` cmdlet'i. Bu yöntem, belirtilen sağlayıcı iç (tam) yoldaki öğesinin özelliklerini alır.

`providerSpecificPickList` Parametresi almak için özellikleri gösterir. Bu parametre `null` veya boşsa, yöntemin tüm özelliklerini almanız gerekir. Ayrıca, [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) örneğini Yazar bir [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) temsil eden bir nesne bir alınan özelliklerin özellik paketi. Yöntemi, hiçbir şey döndürmelidir.

Önerilir yürütmesinin [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) özellik adlarının her öğe için joker karakter genişletmesi seçim listesinde destekler. Bunu yapmak için [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) joker karakter deseni eşleştirme işlemi yapmak için sınıf.

Varsayılan uygulaması işte [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) Windows PowerShell tarafından sağlanan TemplateProvider.cs dosyasından.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>GetProperty'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell özellik sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) yöntemi gereken yönteme yolu belirtilen gereksinimleri karşıladığından emin olmak özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına sürece kullanıcıdan gizlenen nesneleri için bir okuyucu almalıdır değil [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata yolu kullanıcıdan gizlenen bir öğeyi temsil edip etmediğini yazılması gerektiğini ve [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Get-Itemproperty cmdlet'e dinamik parametreleri ekleme

`Get-ItemProperty` Cmdlet'i, çalışma zamanında dinamik olarak belirtilen ek parametreler gerekebilir. Bu dinamik parametreleri sağlamak için Windows PowerShell özellik sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) yöntemi. `path` Parametresi bir tam sağlayıcısı iç yolu gösterir ancak `providerSpecificPickList` parametresi, komut satırına girilen sağlayıcıya özgü özelliklerini belirtir. Bu parametre olabilir `null` veya özellikleri cmdlet'e yöneltilen, boş. Bu durumda, bu yöntem, özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı, döndürülen nesneyi cmdlet'e parametre eklemek için kullanır.

Varsayılan uygulaması işte [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) Windows PowerShell tarafından sağlanan TemplateProvider.cs dosyasından.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Özellikleri ayarlama

Özellikleri ayarlamak için Windows PowerShell özellik sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) çağrılarından desteklemek için gereken yöntemini `Set-ItemProperty` cmdlet'i. Bu yöntem, belirtilen yolda bir veya daha fazla öğenin özelliklerini ayarlar ve gerekli olarak sağlanan özelliklerini üzerine yazar. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) de bir örneğini Yazar bir [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) güncelleştirilmiş bir özellik paketi temsil eden nesne özellikleri.

Varsayılan uygulaması işte [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) Windows PowerShell tarafından sağlanan TemplateProvider.cs dosyasından.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Set-Itemproperty'ı uygulama hakkında bunları unutmayın

Uygulaması için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell özellik sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) yöntemi yönteme geçirilen yolu belirtilen gereksinimleri karşıladığından emin gerekir özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına sürece kullanıcıdan gizlenen nesneleri için bir okuyucu almalıdır değil [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata yolu kullanıcıdan gizlenen bir öğeyi temsil edip etmediğini yazılması gerektiğini ve [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

- Uygulamanıza [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değerini doğrulayın. Bu yöntem, bir sistem durumu, örneğin, dosyaları yeniden adlandırma değişiklik yapıldığında, bir işlemin yürütülmesi doğrulamak için kullanılır. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) Windows PowerShell çalışma zamanı ve herhangi bir komut satırı ayarlarını veya tercih değişkenleri işlenmesi ile kullanıcı değiştirilecek şekilde kaynağın adını gönderir nelerin görüntüleneceğini belirleyin.

  Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, potansiyel olarak tehlikeli olabilecek bir sistem değişiklikler yapıldığında, [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) yöntemi. Bu yöntem, işlem devam olduğunu belirtmek ek geri bildirim izin vermek için kullanıcıya bir onay iletisi gönderir.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Set-Itemproperty cmdlet'i için dinamik parametreler ekleme

`Set-ItemProperty` Cmdlet'i, çalışma zamanında dinamik olarak belirtilen ek parametreler gerekebilir. Bu dinamik parametreleri sağlamak için Windows PowerShell özellik sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) yöntemi. Bu yöntem, özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. `null` Değeri döndürülecek eklenecek hiçbir dinamik parametre değildir.

Varsayılan uygulaması işte [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) Windows PowerShell tarafından sağlanan TemplateProvider.cs dosyasından.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Temizleme özellikleri

Windows PowerShell özellik sağlayıcısı özellikleri temizlemek için uygulamalıdır [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) çağrılarından desteklemek için gereken yöntemini `Clear-ItemProperty` cmdlet'i. Bu yöntem, belirtilen yolda bulunan öğe için bir veya daha fazla özelliklerini ayarlar.

Varsayılan uygulaması işte [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) Windows PowerShell tarafından sağlanan TemplateProvider.cs dosyasından.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Bir şey ClearProperty'ı uygulama hakkında unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell özellik sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) yöntemi gereken yönteme yolu belirtilen gereksinimleri karşıladığından emin olmak özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına sürece kullanıcıdan gizlenen nesneleri için bir okuyucu almalıdır değil [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata yolu kullanıcıdan gizlenen bir öğeyi temsil edip etmediğini yazılması gerektiğini ve [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

- Uygulamanıza [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değerini doğrulayın. Bu yöntem, bir işlemin yürütülmesi için içerik temizleme gibi sistem durumu, bir değişiklik yapılmadan önce doğrulamak için kullanılır. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) kullanıcı için herhangi bir komut satırı ayarlarını veya tercih değişkenleri dikkate alarak, çalışma zamanı Windows PowerShell ile değiştirilmesi kaynağın adını gönderir nelerin görüntüleneceğini belirleyin.

  Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, potansiyel olarak tehlikeli olabilecek bir sistem değişiklikler yapıldığında, [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) yöntemi. Bu yöntem, potansiyel olarak tehlikeli olabilecek işlemi devam olduğunu belirtmek ek geri bildirim izin vermek için kullanıcıya bir onay iletisi gönderir.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Clear-Itemproperty cmdlet'e dinamik parametreleri ekleme

`Clear-ItemProperty` Cmdlet'i, çalışma zamanında dinamik olarak belirtilen ek parametreler gerekebilir. Bu dinamik parametreleri sağlamak için Windows PowerShell özellik sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) yöntemi. Bu yöntem, özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. `null` Değeri döndürülecek eklenecek hiçbir dinamik parametre değildir.

Varsayılan uygulaması işte [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) Windows PowerShell tarafından sağlanan TemplateProvider.cs dosyasından.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcısı oluşturma

Bkz: [cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sağlayıcısı](./designing-your-windows-powershell-provider.md)

[Tasarım bilgisayarınızı Windows PowerShell sağlayıcısı](./designing-your-windows-powershell-provider.md)

[Nesne türlerini genişletme ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)