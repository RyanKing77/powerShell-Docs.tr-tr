---
title: Bir Windows PowerShell Gezinti sağlayıcı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081861"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Windows PowerShell Gezinti Sağlayıcısı Oluşturma

Bu konuda, veri deposu gidebilirsiniz bir Windows PowerShell Gezinti sağlayıcısı oluşturmayı açıklar. Bu tür sağlayıcısı özyinelemeli komutları, iç içe geçmiş kapsayıcılar ve göreli yolları destekler.

> [!NOTE]
> İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider05.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.
>
> Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).

Kullanıcı veritabanında veri tablolarına gidebilmeniz burada açıklanan sağlayıcının kullanıcı tanıtıcı bir Access veritabanının bir sürücü olarak sağlar. Kendi gezinme sağlayıcısı oluşturulurken gezinme için gerekli sürücü nitelenmiş yollar yapmak, göreli yollar Normalleştir, öğeleri alt adları almak, bir öğenin üst yolu ve test yöntemleri yanı sıra veri depolama, taşıma yöntemleri uygulayabilirsiniz. bir öğeyi tanımlamak için bir kapsayıcıdır.

> [!CAUTION]
> Bu tasarım bir alan adı Kimliğine sahip olan bir veritabanının varsayar ve alan türünü LongInteger olduğunu unutmayın.

Aşağıdaki listede, bu konudaki bölümler içerir. Bir Windows PowerShell Gezinti sağlayıcısı yazma ile alışkın değilseniz, bu bilgileri göründüğü sırayla okuyun. Ancak, bir Windows PowerShell Gezinti sağlayıcısı yazma ile bilginiz varsa, lütfen gereksinim duyduğunuz bilgileri doğrudan gidin.

- [PS Gezinti sağlayıcı sınıfı tanımlama](#Define-the-Windows-PowerShell-provider)

- [Temel işlevlerini tanımlama](#Defining-Base-Functionality)

- [PS yol oluşturma](#Creating-a-Windows-PowerShell-Path)

- [Üst yolu alınıyor](#Retrieving-the-Parent-Path)

- [Alt yol adı alınıyor](#Retrieve-the-Child-Path-Name)

- [Bir öğenin bir kapsayıcı olup olmadığını belirleme](#Determining-if-an-Item-is-a-Container)

- [Bir öğe taşıma](#Moving-an-Item)

- [Dinamik parametreleri ekleme `Move-Item` cmdlet'i](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [Göreli bir yol Normalleştiriliyor](#Normalizing-a-Relative-Path)

- [Kod örneği](#Code-Sample)

- [Nesne türlerini tanımlama ve biçimlendirme](#Defining-Object-Types-and-Formatting)

- [Windows PowerShell sağlayıcısı oluşturma](#Building-the-Windows-PowerShell-provider)

- [Windows PowerShell sağlayıcıyı test etme](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcısını tanımlayın

Bir Windows PowerShell Gezinti sağlayıcısı, türetilen bir .NET sınıfı oluşturmalısınız [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) temel sınıfı. Bu bölümde açıklanan Gezinti sağlayıcısı için sınıf tanımı aşağıda verilmiştir.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Bu sağlayıcıda unutmayın [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) iki parametre özniteliği içerir. İlk parametre, kullanıcı dostu bir Windows PowerShell uygulamaları tarafından kullanılan sağlayıcı adını belirtir. İkinci parametre, sağlayıcı için Windows PowerShell çalışma zamanı komut işleme sırasında ortaya koyan Windows PowerShell belirli özelliklerini belirtir. Bu sağlayıcı için eklenen hiçbir Windows PowerShell belirli özellikleri vardır.

## <a name="defining-base-functionality"></a>Temel işlevlerini tanımlama

Bölümünde anlatıldığı gibi [tasarım sağlayıcınız PS](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) temel sınıf farklı bir sağlayıcı sağlanan çeşitli diğer sınıflarından türetilen işlevselliği. Bir Windows PowerShell Gezinti sağlayıcısı, bu nedenle, tüm bu sınıfları tarafından sağlanan işlevselliği tanımlamanız gerekir.

Özel oturum başlatma bilgileri ekleme ve sağlayıcı tarafından kullanılan kaynakları serbest bırakmak için işlevselliği uygulamak için bkz: [temel bir PS sağlayıcı oluşturma](./creating-a-basic-windows-powershell-provider.md). Ancak, çoğu sağlayıcıları (burada açıklanan sağlayıcısı dahil), Windows PowerShell tarafından sağlanan bu işlevsellik varsayılan uygulamasını kullanabilirsiniz.

Bir Windows PowerShell sürücüsü veri deposuna erişmek için yöntemlerini uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) temel sınıfı. Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [sürücü bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md).

Bir veri deposu, alma, ayarlama ve temizleme öğeleri gibi öğeleri işlemek için sağlayıcı tarafından sağlanan yöntemleri uygulamalıdır [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) temel sınıfı. Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [bir Windows PowerShell öğe sağlayıcısı oluşturma](./creating-a-windows-powershell-item-provider.md).

Alt öğeler veya oluşturma, kopyalama, yeniden adlandırmak ve öğeleri kaldırmak yöntemleri yanı sıra veri deposu, adlarını almak için tarafından sağlanan yöntemleri uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)temel sınıfı. Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Bir Windows PowerShell yol oluşturma

Windows PowerShell Gezinti sağlayıcısı veri deposunun öğeleri gitmek için bir sağlayıcı iç Windows PowerShell yol kullanın. Sağlayıcı bir sağlayıcı iç yolu oluşturmak için uygulaması [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) destekleyen bir yönteme birleştirme yolu cmdlet'inden çağırır. Bu yöntem bir sağlayıcıya özgü yol ayırıcı arasındaki üst ve alt yolları kullanarak sağlayıcısı iç yolu, üst ve alt yolu birleştirir.

Varsayılan uygulama alan yolları ile "/" veya "\\"yol ayırıcı olarak yolu ayırıcısı normalleştirir"\\", üst ve alt yol bölümleri arasındaki ayırıcı ile birleştirir ve ardından içeren bir dize döndürür. Birleşik yolları.

Bu gezinti sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod varsayılan uygulamasıdır [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>MakePath'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) yöntemi doğrulamamanız yolu yasal tam yol sağlayıcı ad alanı olarak. Her parametre yalnızca yolun bir bölümünü temsil edebilir ve birleştirilmiş parçaları bir tam yol oluşturabilen değil unutmayın. Örneğin, [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) dosya sistemi sağlayıcısı yöntemi alma "windows\system32" `parent` parametresi ve "abc.dll"`child` parametresi. Yöntemi bu değerleri ile birleştiren "\\" ayırıcı ve "bir tam dosya sistemi yolu olmayan döndürür windows\system32\abc.dll",.

  > [!IMPORTANT]
  > Çağrısında sağlanan yol bölümleri [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) sağlayıcı ad alanı içinde izin verilmeyen karakterleri içerebilir. Bu karakterler için joker karakter genişletmesi büyük olasılıkla kullanılır ve bu yöntemin uygulanmasını bunları kaldırmamalısınız.

## <a name="retrieving-the-parent-path"></a>Üst yolu alınıyor

Windows PowerShell Gezinti sağlayıcıları uygulamak [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) üst kısmını belirtilen tam veya kısmi alınacak yöntemi sağlayıcıya özgü yolu. Yöntem yolunun alt parçası kaldırır ve üst yol bölümü döndürür. `root` Parametresi bir sürücünün kökünü tam yolunu belirtir. Bu parametre null ya da bir sürücünün alma işlemi için kullanımda değilse boş olabilir. Bir kök belirtilmezse, kök olarak aynı ağacında bir kapsayıcıya yöntemi bir yol döndürmesi gerekir.

Örnek gezinme sağlayıcısı bu yöntemi yok sayın değil, ancak varsayılan uygulama kullanır. İkisi de yolları kabul ettiği "/" ve "\\" yol ayırıcıları olarak. Önce yalnızca yolu normalleştirir "\\" Ayırıcılar, ardından üst yolu kapalı son böler "\\" ve üst yolu döndürür.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>GetParentPath'ı uygulama hakkında unutmayın

Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) yöntemi sağlayıcı ad alanı için yol ayırıcı yolunda sözcüksel olarak Böl. Örneğin, dosya sistemi sağlayıcısı için son aramak için bu yöntemi kullanır "\\" ve her şeyi ayırıcının solunda döndürür.

## <a name="retrieve-the-child-path-name"></a>Alt yol adını alma

Gezinti sağlayıcı uygular, [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) yönteminin öğesinin alt (yaprak öğe) adını almak için belirtilen tam bulunan veya Kısmi sağlayıcıya özgü yolu.

Örnek gezinme sağlayıcının bu yöntemi geçersiz kılmaz. Varsayılan uygulama, aşağıda gösterilmiştir. İkisi de yolları kabul ettiği "/" ve "\\" yol ayırıcıları olarak. Önce yalnızca yolu normalleştirir "\\" Ayırıcılar, ardından üst yolu kapalı son böler "\\" ve yol bölümü alt adını döndürür.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>GetChildName'ı uygulama hakkında bunları unutmayın

Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) yöntemi yol ayırıcısı yolunda sözcüksel olarak Böl. Sağlanan yol hiçbir yol ayırıcıları içeriyorsa, yöntem üzerinde değişiklik yapılmadan yolu döndürmelidir.

> [!IMPORTANT]
> Bu yöntem çağrısında sağlanan yol sağlayıcı ad alanı içinde geçersiz karakterler içeriyor olabilir. Joker karakter genişletmesi veya normal ifadenin eşleştirilmesi için kullanılan bu karakterler büyük olasılıkla ve bu yöntemin uygulanmasını bunları kaldırmamalısınız.

## <a name="determining-if-an-item-is-a-container"></a>Bir öğenin bir kapsayıcı olup olmadığını belirleme

Gezinti sağlayıcılarınızı uygulayabilirsiniz [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) yöntemi belirtilen yol bir kapsayıcı sağlayacağını belirleyin. Aksi takdirde bir kapsayıcı ve yanlış yolu temsil ediyorsa true değerini döndürür. Kullanabilmek için bu yöntemi kullanıcının erişmesi `Test-Path` cmdlet için sağlanan yol.

Aşağıdaki kodda gösterildiği [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) bizim örnek Gezinti sağlayıcısı uygulaması. Yöntemi, belirtilen yolun doğru olduğundan ve tablosunun var olduğunu ve bir kapsayıcı yolunu belirtir, true değerini döndürür, doğrular.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>IsItemContainer'ı uygulama hakkında bunları unutmayın

Öğesinden gezinme sağlayıcınız .NET sınıf sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu durumda, uygulanması [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) geçirilen yolu gereksinimlerini karşıladığından emin olmak gerekir. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) özelliği.

## <a name="moving-an-item"></a>Bir öğe taşıma

Support, `Move-Item` Gezinti sağlayıcınız cmdlet'ini uygulayan [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemi. Bu yöntem tarafından belirtilen öğe taşır `path` parametresi sağlanan yolda kapsayıcıya `destination` parametresi.

Örnek gezinme sağlayıcı geçersiz [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemi. Aşağıdaki varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>MoveItem'ı uygulama hakkında bunları unutmayın

Öğesinden gezinme sağlayıcınız .NET sınıf sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu durumda, uygulanması [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) geçirilen yolu gereksinimleri karşıladığından emin olmalısınız. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, **CmdletProvider.Exclude** özelliği.

Varsayılan olarak, bu yöntem geçersiz kılmalarına nesneleri var olan nesnelerin üzerine sürece taşımamalısınız [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Örneğin, dosya sistemi sağlayıcısı c:\temp\abc.txt varolan c:\bar.txt dosyasını sürece kopyalamaz [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Yolunu belirtilmişse `destination` parametresi var ve bir kapsayıcı [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özellik gerekli değildir. Bu durumda, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) tarafından belirtilen öğe taşımalısınız `path` kapsayıcıya parametresi tarafından belirtilen `destination` parametre olarak bir alt.

Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değeri denetleyin. Bu yöntem, bir sistem durumu, örneğin, dosyaları silme değişiklik yapıldığında, bir işlemin yürütülmesi doğrulamak için kullanılır. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) kullanıcı için herhangi bir komut satırı ayarlarını veya tercih değişkenleri dikkate alarak, çalışma zamanı Windows PowerShell ile değiştirilmesi kaynağın adını gönderir kullanıcıya görüntülenen belirleme.

Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) yöntemi. Bu yöntem, geri bildirim işlemi devam söylemek izin vermek için kullanıcıya bir ileti gönderir. Sağlayıcınız çağırmalıdır [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) olarak tehlikeli olabilecek bir sistem değişiklikleri için ek bir denetim.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Öğe taşıma cmdlet'e dinamik parametreleri ekleme

Bazen `Move-Item` cmdlet, çalışma zamanında dinamik olarak sağlanan ek parametreler gerektirir. Bu dinamik parametreleri sağlamak için Gezinti sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) gerekli parametre değerlerini almak için yöntemi Belirtilen yol ve dönüş öğesi özelliklerini ve alanları ayrıştırma ile sahip bir nesne cmdlet'i sınıfla benzer öznitelikleri veya bir [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne.

Bu gezinti sağlayıcı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod varsayılan uygulamasıdır [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Göreli bir yol Normalleştiriliyor

Gezinti sağlayıcı uygular, [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) tam yol'leri normalleştirmek için yöntemi gösterilir `path` parametresi tarafından belirtilen göreli olarak `basePath` parametresi. Yöntemi, normalleştirilmiş yol dize gösterimini döndürür. Bu bir hata ortaya çıkarsa Yazar `path` parametresi, varolmayan bir yol belirtir.

Örnek gezinme sağlayıcının bu yöntemi geçersiz kılmaz. Aşağıdaki varsayılan uygulamasıdır.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>NormalizeRelativePath'ı uygulama hakkında bunları unutmayın

Uygulamanıza [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) çözümlenmelidir `path` parametresi, ancak sahip değil söz dizimi tamamen Ayrıştırmada kullanılacak. Büyük/küçük harf veri deposundaki yol bilgileri aramak ve oluşturan bir yol yolu kullanmak için bu yöntem eşleşen tasarım için önerilir ve yolu sözdizimi standart.

## <a name="code-sample"></a>Kod örneği

Tam örnek kod için bkz: [AccessDbProviderSample05 kod örneği](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Nesne türlerini tanımlama ve biçimlendirme

Varolan nesnelere üyelerini ekleyebilir veya yeni nesneleri tanımlamak için bir sağlayıcı için mümkündür. Daha fazla bilgi için[genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcısı oluşturma

Daha fazla bilgi için [kaydetme cmdlet'leri ve sağlayıcıları uygulamalarını barındırmak için nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcıyı test etme

Windows PowerShell ile Windows PowerShell sağlayıcısı kayıtlı olduğunda göre türetme kullanıma cmdlet de dahil olmak üzere komut satırında desteklenen cmdlet'lerini çalıştırarak test edebilirsiniz. Bu örnekte, örnek Gezinti sağlayıcısı test eder.

1. Yeni kabuğunuz çalıştırın ve `Set-Location` erişim veritabanını belirtmek için bir yol ayarlamak için cmdlet'i.

   ```powershell
   Set-Location mydb:
   ```

2. Şimdi Çalıştır `Get-Childitem` kullanılabilir veritabanı tablolar veritabanı öğelerinin bir listesini almak için cmdlet'i. Her tablo için bu cmdlet ayrıca tablo satır sayısını alır.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Kullanım `Set-Location` cmdlet'ini yeniden çalışanlar veri tablosunun konumunu ayarlayın.

   ```powershell
   Set-Location Employees
   ```

4. Şimdi kullanalım `Get-Location` Employees tablosunu yolunu almak için cmdlet'i.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Artık `Get-Childitem` cmdlet'i yöneltilen için `Format-Table` cmdlet'i. Bu cmdlet kümesini, çalışanların veri tablosu için tablo satırları olan öğeleri alır. Biçimlendirilmiş belirtildiği gibi `Format-Table` cmdlet'i.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Şimdi Çalıştır `Get-Item` çalışanlar veri tablonun satırında 0 olan öğeleri almak için cmdlet'i.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Kullanım `Get-Item` yeniden satır 0 öğeler için çalışan verilerini almak için cmdlet'i.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sağlayıcılar oluşturma](./how-to-create-a-windows-powershell-provider.md)

[Tasarım bilgisayarınızı Windows PowerShell sağlayıcısı](./designing-your-windows-powershell-provider.md)

[Nesne türlerini genişletme ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Kapsayıcı Windows PowerShell sağlayıcıyı uygulama](./creating-a-windows-powershell-container-provider.md)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)