---
title: Bir Windows PowerShell öğe sağlayıcısı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055130"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Windows PowerShell Öğe Sağlayıcısı Oluşturma

Bu konuda, bir veri deposundaki verileri işlemek bir Windows PowerShell sağlayıcısı oluşturmayı açıklar. Bu konu başlığında, "" veri öğeleri depolamak için veri deposundaki öğeleri denir. Sonuç olarak deposundaki verileri işleyebileceğiniz bir sağlayıcı için bir Windows PowerShell öğe sağlayıcısı adlandırılır.

> [!NOTE]
> İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider03.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.
>
> Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).

Bu konuda açıklanan Windows PowerShell öğe sağlayıcısı, bir Access veritabanından veri öğelerini alır. Bu durumda, "öğe" Access veritabanındaki bir tablo ya da bir tablosunda bir satıra ' dir.

Aşağıdaki liste, bu konudaki bölümler içerir. Bir Windows PowerShell öğe sağlayıcısı yazma ile alışkın değilseniz, göründükleri sırayla bu bölümleri okuyun. Ancak, bir Windows PowerShell öğe sağlayıcısı yazma ile bilginiz varsa, gereksinim duyduğunuz bilgileri doğrudan gidin:

- [Windows PowerShell öğesi sağlayıcı sınıfı tanımlama](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Temel işlevlerini tanımlama](#Defining-Base-Functionality)

- [İçin yol geçerlilik denetimi](#Checking-for-Path-Validity)

- [Bir öğe var olup olmadığını belirleme](#Determining-if-an-Item-Exists)

- [Dinamik parametreleri ekleme `Test-Path` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Bir öğe alma](#Retrieving-an-Item)

- [Dinamik parametreleri ekleme `Get-Item` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Bir öğe ayarlama](#Setting-an-Item)

- [Dinamik parametreleri ekleme `Set-Item` cmdlet'i](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Bir öğe temizleme](#Clearing-an-Item)

- [Dinamik parametreler için Clear öğesi cmdlet'i ekleniyor](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Bir öğe için bir varsayılan eylem gerçekleştirme](#Performing-a-Default-Action-for-an-Item)

- [Dinamik parametreler için InvokeDefaultAction alınıyor](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Yardımcı yöntemler ve sınıfları uygulama](#Implementing-Helper-Methods-and-Classes)

- [Kod örneği](#Code-Sample)

- [Nesne türlerini tanımlama ve biçimlendirme](#Defining-Object-Types-and-Formatting)

- [Windows PowerShell sağlayıcısı oluşturma](#Building-the-Windows-PowerShell-provider)

- [Windows PowerShell sağlayıcıyı test etme](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Windows PowerShell öğesi sağlayıcı sınıfı tanımlama

Bir Windows PowerShell öğe sağlayıcısı, türetilen bir .NET sınıfı tanımlamanız gerekir [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) temel sınıfı. Bu bölümde açıklanan öğe sağlayıcısı için sınıf tanımının verilmiştir.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Bu tanım, sınıf unutmayın [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) iki parametre özniteliği içerir. İlk parametre, kullanıcı dostu bir Windows PowerShell uygulamaları tarafından kullanılan sağlayıcı adını belirtir. İkinci parametre, sağlayıcı için Windows PowerShell çalışma zamanı komut işleme sırasında ortaya koyan Windows PowerShell belirli özelliklerini belirtir. Bu sağlayıcı için hiçbir ek Windows PowerShell belirli özellikleri vardır.

## <a name="defining-base-functionality"></a>Temel işlevlerini tanımlama

Bölümünde anlatıldığı gibi [tasarım bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı farklı sağlanan çeşitli diğer sınıflarından türetilen Sağlayıcı işlevselliği. Bir Windows PowerShell öğe sağlayıcısı, bu nedenle, tüm bu sınıfları tarafından sağlanan işlevselliği tanımlamanız gerekir.

Özel oturum başlatma bilgileri ekleme ve sağlayıcı tarafından kullanılan kaynakları serbest bırakmak işlevselliğinin nasıl uygulandığını hakkında daha fazla bilgi için bkz. [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md). Ancak, çoğu sağlayıcıları, burada açıklanan sağlayıcısı dahil olmak üzere Windows PowerShell tarafından sağlanan bu işlevsellik varsayılan uygulamasını kullanabilirsiniz.

Windows PowerShell öğe sağlayıcısı depodaki öğe yönetebilirsiniz önce yöntemlerini uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) temel sınıfı veri deposuna erişmek için. Bu sınıf uygulama hakkında daha fazla bilgi için bkz. [sürücü bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>İçin yol geçerlilik denetimi

Veri öğesi için bakıldığında, Windows PowerShell çalışma zamanı sağlayıcısı, bir Windows PowerShell yolu "Pspath değeri kavramlar" bölümünde tanımlanan sağlar [nasıl Windows PowerShell çalışır](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Bir Windows PowerShell öğe sağlayıcısı uygulayarak geçirilen herhangi bir yola sözdizimsel ve semantik geçerliliğini doğrulamalısınız [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) yöntemi. Bu yöntem döndürür `true` yolu geçerliyse ve `false` Aksi takdirde. Bu yöntemin uygulanmasını yolu sözdizimi kurallarına göre olan öğe ancak yolda varlığını doğrulamanız değil kullanan ve anlamsal olarak doğru olması.

Uygulamasını işte [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) bu sağlayıcı için yöntemi. Unutmayın, bu uygulama Tekdüzen bir yoldaki tüm ayırıcı dönüştürülecek NormalizePath yardımcı yöntemini çağırır.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Bir öğe var olup olmadığını belirleme

Yolunu doğruladıktan sonra Windows PowerShell çalışma zamanı veri öğesi bu yolda olup olmadığını belirlemeniz gerekir. Bu tür bir sorgu desteklemek için Windows PowerShell öğe sağlayıcısı uygulayan [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) yöntemi. Bu yöntem döndürür `true` öğeyi belirtilen yolda bulunur ve `false` (Aksi takdirde varsayılan).

Uygulamasını işte [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) bu sağlayıcı için yöntemi. Bu yöntem PathIsDrive ChunkPath ve GetTable yardımcı yöntemlerini çağırır ve bir sağlayıcısı kullanıyor Not DatabaseTableInfo nesne tanımlı.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>ItemExists'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell öğe sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) yöntemi yönteme geçirilen yolu belirtilen özellik gereksinimleri karşıladığından emin gerekir. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Bu yöntemin uygulanmasını öğesi kullanıcıya görünür duruma sokan öğesine erişimi herhangi bir biçimde işlemelidir. Örneğin, bir kullanıcı (Windows PowerShell tarafından sağlanan) dosya sistemi sağlayıcısından ancak okuma erişimi aracılığıyla bir dosyaya yazma erişimi varsa, dosyanın hala var ve [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) döndürür `true`. Uygulamanızı bir üst öğesi alt öğesi listesinin oluşturulmasını görmek için denetimi gerektirebilir.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Test yolu cmdlet'e dinamik parametreleri ekleme

Bazen `Test-Path` çağıran cmdlet'i [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Öğe sağlayıcısı uygulanmalı Windows PowerShell Bu dinamik parametreleri sağlamak için [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Test-Path` cmdlet'i.

Bu Windows PowerShell öğe sağlayıcısı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Bir öğe alma

Bir öğe almak için Windows PowerShell öğe sağlayıcısı kılmalı [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) çağrılarından desteklemek için gereken yöntemini `Get-Item` cmdlet'i. Bu yöntemi kullanarak öğesi Yazar [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) yöntemi.

Uygulamasını işte [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) bu sağlayıcı için yöntemi. Bu yöntem, bir erişim veritabanındaki tabloları veya veri tablosundaki satırları olan öğeleri almak için GetTable ve GetRow yardımcı yöntemler kullandığına dikkat edin.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>GetItem'ı uygulama hakkında bunları unutmayın

Uygulaması için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell öğe sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) yönteme yolu bu gereksinimleri karşıladığından emin olmalısınız. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına kullanıcıdan sürece genellikle gizlenmiş nesneleri almalıdır değil [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Örneğin, [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) yöntemi dosya sistemi sağlayıcısı denetimlerinin [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) çağrılacak çalışmadan önce özellik [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) gizli ya da sistem dosyaları.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Get-Item cmdlet'e dinamik parametreleri ekleme

Bazen `Get-Item` cmdlet, çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Öğe sağlayıcısı uygulanmalı Windows PowerShell Bu dinamik parametreleri sağlamak için [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Get-Item` cmdlet'i.

Bu sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Bir öğe ayarlama

Bir öğe ayarlamak için Windows PowerShell öğe sağlayıcısı kılmalı [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) çağrılarından desteklemek için gereken yöntemini `Set-Item` cmdlet'i. Bu yöntem, belirtilen yolda öğenin değerini ayarlar.

Bu sağlayıcı için bir geçersiz kılma sağlamaz [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) yöntemi. Ancak, bu yöntem varsayılan uygulamasını verilmiştir.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>SetItem'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell öğe sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) yönteme yolu bu gereksinimleri karşıladığından emin olmalısınız. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına ayarlayın veya gerekir yazma sürece kullanıcıdan gizlenen nesneleri [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata gönderilmesi gereken [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) yolu gizli bir öğeyi temsil ediyorsa yöntemi ve [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

- Uygulamanıza [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değerini doğrulayın. Bu yöntem, dosyaları silme veri deposuna, örneğin, bir değişiklik yapıldığında, bir işlemin yürütülmesi doğrulamak için kullanılır. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) yöntemi gönderir kullanıcıya tüm komut satırı ayarlarını dikkate alarak Windows PowerShell çalışma zamanı ile değiştirilmesi kaynağın adını veya nelerin görüntüleneceğini belirlemede tercih değişkenleri.

  Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) yöntemi. Bu yöntem, işlem devam doğrulamak geri bildirim izin vermek için kullanıcıya bir ileti gönderir. Çağrı [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tehlikeli sistem değişiklikleri için ek bir denetim sağlar.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Dinamik parametreler için SetItem alınıyor

Bazen `Set-Item` cmdlet, çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Öğe sağlayıcısı uygulanmalı Windows PowerShell Bu dinamik parametreleri sağlamak için [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Set-Item` cmdlet'i.

Bu sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Bir öğe temizleme

Bir öğeyi silmek için Windows PowerShell öğe sağlayıcısı uygulayan [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) çağrılarından desteklemek için gereken yöntemini `Clear-Item` cmdlet'i. Bu yöntem, belirtilen yolda veri öğesini siler.

Bu sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>ClearItem'ı uygulama hakkında bunları unutmayın

Uygulaması için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell öğe sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) yönteme yolu bu gereksinimleri karşıladığından emin olmalısınız. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına ayarlayın veya gerekir yazma sürece kullanıcıdan gizlenen nesneleri [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata gönderilmesi gereken [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) kullanıcıdan gizlenen bir öğe yolu temsil ediyorsa yöntemi ve [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

- Uygulamanıza [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değerini doğrulayın. Bu yöntem, dosyaları silme veri deposuna, örneğin, bir değişiklik yapıldığında, bir işlemin yürütülmesi doğrulamak için kullanılır. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) yöntem, Windows PowerShell çalışma zamanı ile kullanıcı değişmesi ve herhangi bir komut satırı ayarlarını veya tercih işlemek için kaynağın adını gönderir nelerin görüntüleneceğini belirlemede değişkenler.

  Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) yöntemi. Bu yöntem, işlem devam doğrulamak geri bildirim izin vermek için kullanıcıya bir ileti gönderir. Çağrı [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tehlikeli sistem değişiklikleri için ek bir denetim sağlar.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Dinamik parametreler için clearItem alınamıyor

Bazen `Clear-Item` cmdlet, çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Öğe sağlayıcısı uygulanmalı Windows PowerShell Bu dinamik parametreleri sağlamak için [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı parametreleri eklemek için döndürülen nesne kullanır `Clear-Item` cmdlet'i.

Bu öğe sağlayıcısı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Bir öğe için bir varsayılan eylem gerçekleştirme

Windows PowerShell öğesi sağlayıcılarınızı uygulayabilirsiniz [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) çağrılarından desteklemek için gereken yöntemini `Invoke-Item` sağlayıcı sağlayan cmdlet için belirtilen yoldaki öğe için bir varsayılan eylem gerçekleştirin. Örneğin, dosya sistemi sağlayıcısı için belirli bir öğeyi ShellExecute çağırmak için bu yöntemi kullanabilirsiniz.

Bu sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>InvokeDefaultAction'ı uygulama hakkında bunları unutmayın

Uygulaması için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Sağlayıcı sınıf tanımlanırken, bir Windows PowerShell öğe sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) yönteme yolu bu gereksinimleri karşıladığından emin olmalısınız. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına ayarlayın veya gerekir yazma sürece kullanıcıdan gizlenen nesneleri [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata gönderilmesi gereken [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) kullanıcıdan gizlenen bir öğe yolu temsil ediyorsa yöntemi ve [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Dinamik parametreler için InvokeDefaultAction alınamıyor

Bazen `Invoke-Item` cmdlet, çalışma zamanında dinamik olarak belirtilen ek parametreler gerektirir. Öğe sağlayıcısı uygulanmalı Windows PowerShell Bu dinamik parametreleri sağlamak için [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı dinamik parametreleri eklemek için döndürülen nesne kullanır `Invoke-Item` cmdlet'i.

Bu öğe sağlayıcısı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Yardımcı yöntemler ve sınıfları uygulama

Bu öğe sağlayıcısı birkaç yardımcı yöntemin uygular ve genel tarafından kullanılan sınıflar, Windows PowerShell tarafından tanımlanan yöntemleri geçersiz kılın. Bu yardımcı yöntemler ve sınıflar için kod gösterilir [kod örneği](#Code-Sample) bölümü.

### <a name="normalizepath-method"></a>NormalizePath yöntemi

Bu öğe sağlayıcısı tutarlı bir biçimde olduğundan emin olmak için NormalizePath yardımcı yöntem uygular. Belirtilen biçimde bir ters eğik çizgi kullanır (\\) ayırıcı olarak.

### <a name="pathisdrive-method"></a>PathIsDrive yöntemi

Bu öğe sağlayıcısı belirtilen yol gerçekten sürücü adı olup olmadığını belirlemek için PathIsDrive yardımcı yöntemi uygular.

### <a name="chunkpath-method"></a>ChunkPath yöntemi

Bu öğe sağlayıcısı, böylece sağlayıcı tek tek öğelerini, belirtilen yolu keser ChunkPath yardımcı yöntemi uygular. Bir dizi yol öğelerinden oluşan döndürür.

### <a name="gettable-method"></a>GetTable yöntemi

Bu öğe sağlayıcısı çağrısında belirtilen tablonun ilgili bilgileri temsil eder bir DatabaseTableInfo nesnesi döndüren GetTables yardımcı yöntemi uygular.

### <a name="getrow-method"></a>GetRow metodu

[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) bu öğe sağlayıcısı yöntemi satır almak için yardımcı yöntemini çağırır. Bu yardımcı yöntem bilgileri tablosunda belirtilen satırı temsil eden bir DatabaseRowInfo nesnesini alır.

### <a name="databasetableinfo-class"></a>DatabaseTableInfo sınıfı

Bu öğe sağlayıcısı bilgileri veritabanında veri tablosunda bir koleksiyonunu temsil eder bir DatabaseTableInfo sınıfı tanımlar. Bu sınıf benzer [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) sınıfı.

Örnek öğe sağlayıcısı veritabanında tablolar tanımlama tablo bilgi nesnelerinin bir koleksiyonunu döndüren bir DatabaseTableInfo.GetTables yöntemi tanımlar. Bu yöntem herhangi bir veritabanı hatası bir satır olarak sıfır girişlerle hesaplamasındaki emin olmak için bir try/catch bloğu içerir.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo sınıfı

Bu öğe sağlayıcısı bir tablosunda bir satıra veritabanının temsil eden DatabaseRowInfo Yardımcısı sınıfı tanımlar. Bu sınıf benzer [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) sınıfı.

Örnek sağlayıcısında satır bilgileri nesneleri için belirtilen tablo koleksiyonu döndürülecek DatabaseRowInfo.GetRows yöntemi tanımlar. Bu yöntem, özel durumları yakalamak için try/catch bloğu içerir. Hiçbir satır bilgileri hataları neden olur.

## <a name="code-sample"></a>Kod örneği

Tam örnek kod için bkz: [AccessDbProviderSample03 kod örneği](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Nesne türlerini tanımlama ve biçimlendirme

Bir sağlayıcı yazarken, var olan nesnelerde üye eklemek veya yeni nesneleri tanımlamak gerekli olabilir. İşiniz bittiğinde, Windows PowerShell nesnesinin üyelerini tanımlamak için kullanabileceğiniz bir türleri dosyası ve nesne nasıl görüntüleneceğini tanımlayan bir biçim dosyası oluşturun. Hakkında daha fazla bilgi için bkz: [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcısı oluşturma

Bkz: [cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcıyı test etme

Windows PowerShell ile bu Windows PowerShell öğe sağlayıcısı kaydedildiğinde, yalnızca temel test edebilir ve sağlayıcı işlevselliğini sürücü. Öğeleri düzenlenmesini test etmek için de açıklanan kapsayıcı işlevselliği uygulamalıdır [kapsayıcısı Windows PowerShell sağlayıcısı uygulama](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell sağlayıcılar oluşturma](./how-to-create-a-windows-powershell-provider.md)

[Bilgisayarınızı bir Windows PowerShell sağlayıcısındaki tasarlama](./designing-your-windows-powershell-provider.md)

[Nesne türlerini genişletme ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell nasıl çalışır?](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Bir kapsayıcı Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md)

[Bir sürücü Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)