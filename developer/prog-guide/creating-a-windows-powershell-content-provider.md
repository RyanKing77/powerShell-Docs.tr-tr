---
title: Bir Windows PowerShell içeriği sağlayıcısı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: d7e237514b4db4bce3366836d3b6e0cd340bf107
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855016"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Windows PowerShell İçerik Sağlayıcısı Oluşturma

Bu konuda, kullanıcı bir veri deposundaki öğeleri içeriğini işlemek etkinleştiren bir Windows PowerShell sağlayıcısı oluşturmayı açıklar. Sonuç olarak, öğeleri içeriğini işlemek bir sağlayıcı için bir Windows PowerShell içerik sağlayıcısı olarak adlandırılır.

> [!NOTE]
> İndirebileceğiniz C# .NET Framework 3.0 çalışma zamanı bileşenleri ve Microsoft Windows Yazılım Geliştirme Seti için Windows Vista'yı kullanarak bu sağlayıcı için kaynak dosyası (AccessDBSampleProvider06.cs). Yükleme yönergeleri için bkz: [Windows PowerShell yükleme ve indirme Windows PowerShell SDK'sı](/powershell/developer/installing-the-windows-powershell-sdk).
>
> İndirilen kaynak dosyaları kullanılabilir  **\<PowerShell örnekleri >** dizin.
>
> Diğer Windows PowerShell sağlayıcısı uygulamaları hakkında daha fazla bilgi için bkz. [tasarlama bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md).

## <a name="define-the-windows-powershell-content-provider-class"></a>Windows PowerShell içerik sağlayıcı sınıfı tanımlayın

Windows PowerShell içerik sağlayıcısı destekleyen bir .NET sınıfı oluşturmalısınız [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi. Bu bölümde açıklanan öğe sağlayıcısı için sınıf tanımı aşağıda verilmiştir.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Bu tanım, sınıf unutmayın [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) iki parametre özniteliği içerir. İlk parametre, kullanıcı dostu bir Windows PowerShell uygulamaları tarafından kullanılan sağlayıcı adını belirtir. İkinci parametre, sağlayıcı için Windows PowerShell çalışma zamanı komut işleme sırasında ortaya koyan Windows PowerShell belirli özelliklerini belirtir. Bu sağlayıcı için hiçbir ek Windows PowerShell belirli özellikleri vardır.

## <a name="define-functionality-of-base-class"></a>Temel sınıf işlevselliğinin tanımlayın

Bölümünde anlatıldığı gibi [tasarım bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı sağlanan çeşitli diğer sınıflarından türetilen farklı bir sağlayıcı işlevselliği. Bir Windows PowerShell içerik sağlayıcı, bu nedenle, genellikle tüm bu sınıfları tarafından sağlanan işlevleri tanımlar.

Özel oturum başlatma bilgileri ekleme ve sağlayıcı tarafından kullanılan kaynakları serbest bırakmak işlevselliğinin nasıl uygulandığını hakkında daha fazla bilgi için bkz. [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md). Ancak, çoğu sağlayıcıları, burada açıklanan sağlayıcısı dahil olmak üzere Windows PowerShell tarafından sağlanan bu işlevsellik varsayılan uygulamasını kullanabilirsiniz.

Veri deposuna erişmek için sağlayıcı yöntemlerini uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) temel sınıfı. Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [sürücü bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-windows-powershell-drive-provider.md).

Bir veri deposu, alma, ayarlama ve temizleme öğeleri gibi öğeleri işlemek için sağlayıcı tarafından sağlanan yöntemleri uygulamalıdır [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) temel sınıfı. Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [bir Windows PowerShell öğe sağlayıcısı oluşturma](./creating-a-windows-powershell-item-provider.md).

Çok katmanlı veri depolarına üzerinde çalışmak için sağlayıcı tarafından sağlanan yöntemleri uygulamalıdır [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) temel sınıfı. Bu yöntemleri kullanma hakkında daha fazla bilgi için bkz. [bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md).

Özyinelemeli komutları, iç içe geçmiş kapsayıcılar ve göreli yolları desteklemek için sağlayıcı uygulamalıdır [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) temel sınıfı. Ayrıca, bu Windows PowerShell içerik sağlayıcısı için ekler [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimini [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) temel sınıfı ve bu nedenle bu sınıfı tarafından sağlanan yöntemleri uygulamalıdır. Bu yöntemleri uygulamaya daha fazla bilgi için bkz: [Gezinti Windows PowerShell sağlayıcıyı uygulama](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Bir içerik okuyucu uygulama

Bir öğe içeriği okumasına izin sağlayıcı gerekir, türetilen bir içerik okuyucu sınıfını uyguluyor [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). İçerik okuyucu bu sağlayıcı için bir veri tablosunda bir satıra içeriğini erişim sağlar. İçerik okuyucu sınıfı tanımlayan bir **okuma** yönteminin belirtilen satırdaki verileri alır ve bu verileri temsil eden bir liste döndürür bir **arama** içerik okuyucu taşır yöntemi bir  **Kapat** içerik okuyucu kapatır yöntemi ve bir **Dispose** yöntemi.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>İçerik yazan uygulama

Bir öğe için içerik yazma için sağlayıcıyı içerik uygulama yazıcı sınıf türetilir [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). İçerik yazıcı sınıfını tanımlar bir **yazma** belirtilen satır içeriği yazan yöntemi bir **arama** içerik yazıcı taşır yöntemi bir **Kapat** kapatır yöntemi İçerik yazıcı ve **Dispose** yöntemi.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>İçerik okuyucu alınıyor

Bir öğe içerik almak için sağlayıcı uygulamalıdır [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) desteklemek için `Get-Content` cmdlet'i. Bu yöntem, belirtilen yoldaki öğesi için içerik okuyucu döndürür. Okuyucu nesnesi, içeriğini okumak için ardından açılabilir.

Uygulamasını işte [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) bu sağlayıcı için bu yöntem için.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>GetContentReader'ı uygulama hakkında bunları unutmayın

Uygulaması için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Sağlayıcı sınıf tanımlanırken, Windows PowerShell içerik sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) yöntemi yönteme geçirilen yolu belirtilen gereksinimleri karşıladığından emin gerekir özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına sürece kullanıcıdan gizlenen nesneleri için bir okuyucu almalıdır değil [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata yolu kullanıcıdan gizlenen bir öğeyi temsil edip etmediğini yazılması gerektiğini ve [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Get-Content cmdlet'e dinamik parametreleri ekleme

`Get-Content` Cmdlet'i, çalışma zamanında dinamik olarak belirtilen ek parametreler gerekebilir. Bu dinamik parametreleri sağlamak için Windows PowerShell içerik sağlayıcısına uygulamalıdır [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) yöntemi. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı, döndürülen nesneyi cmdlet'e parametre eklemek için kullanır.

Bu Windows PowerShell kapsayıcısı sağlayıcısı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>İçerik yazıcı alınıyor

Bir öğe için içerik yazmak için sağlayıcı uygulamalıdır [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) desteklemek için `Set-Content` ve `Add-Content` cmdlet'leri. Bu yöntem, belirtilen yoldaki öğesi için içerik yazıcı döndürür.

Uygulamasını işte [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) bu yöntem için.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>GetContentWriter'ı uygulama hakkında bunları unutmayın

Uygulamanız için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Sağlayıcı sınıf tanımlanırken, Windows PowerShell içerik sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) yöntemi yönteme geçirilen yolu belirtilen gereksinimleri karşıladığından emin gerekir özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına sürece kullanıcıdan gizlenen nesneleri için bir yazıcı almalıdır değil [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata yolu kullanıcıdan gizlenen bir öğeyi temsil edip etmediğini yazılması gerektiğini ve [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>İçerik Ekle ve Set-içerik Cmdlet'lerinde dinamik parametreleri ekleme

`Add-Content` Ve `Set-Content` cmdlet'ler, bir çalışma zamanı eklenen ek dinamik parametreler gerekebilir. Bu dinamik parametreleri sağlamak için Windows PowerShell içerik sağlayıcısına uygulamalıdır [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) bu işlemeye yöntemi Parametreler. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı döndürülen nesne cmdlet'lerinde parametreleri eklemek için kullanır.

Bu Windows PowerShell kapsayıcısı sağlayıcısı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>İçerik temizleme

İçerik sağlayıcı uygular [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) yöntemi support, `Clear-Content` cmdlet'i. Bu yöntem, belirtilen yolda bir öğenin içeriğini kaldırır, ancak öğe dokunmaz.

Uygulamasını işte [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) bu sağlayıcı için yöntemi.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>ClearContent'ı uygulama hakkında bunları unutmayın

Uygulaması için aşağıdaki koşullar geçerli [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Sağlayıcı sınıf tanımlanırken, Windows PowerShell içerik sağlayıcısı sağlayıcısı yeteneklerini ExpandWildcards, filtre, INCLUDE veya Exclude, gelen bildirmek [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)sabit listesi. Bu gibi durumlarda, uygulanması [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) yöntemi yönteme geçirilen yolu belirtilen gereksinimleri karşıladığından emin gerekir özellikleri. Bunu yapmak için yöntemin uygun özellik örneğin erişmeli, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) ve [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) özellikleri.

- Varsayılan olarak, bu yöntem geçersiz kılmalarına sürece kullanıcıdan gizlenen nesnelerin içeriğini temizlemelisiniz değil [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) özelliği `true`. Bir hata yolu kullanıcıdan gizlenen bir öğeyi temsil edip etmediğini yazılması gerektiğini ve [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ayarlanır `false`.

- Uygulamanıza [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ve veri deposuna herhangi bir değişiklik yapmadan önce dönüş değerini doğrulayın. Bu yöntem, içerik temizleme gibi veri deposuna bir değişiklik yapıldığında, bir işlemin yürütülmesi doğrulamak için kullanılır. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) yöntem, kullanıcı için herhangi bir komut satırı ayarlarını veya tercih işleme Windows PowerShell çalışma zamanı ile değiştirilmesi kaynağın adını gönderir nelerin görüntüleneceğini belirlemede değişkenler.

  Çağrısından sonra [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) döndürür `true`, [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) yöntemini çağırma [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) yöntemi. Bu yöntem, işlem devam doğrulamak geri bildirim izin vermek için kullanıcıya bir ileti gönderir. Çağrı [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tehlikeli sistem değişiklikleri için ek bir denetim sağlar.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Clear-Content cmdlet'e dinamik parametreleri ekleme

`Clear-Content` Cmdlet'i, çalışma zamanında eklenen ek dinamik parametreler gerekebilir. Bu dinamik parametreleri sağlamak için Windows PowerShell içerik sağlayıcısına uygulamalıdır [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) bu işlemeye yöntemi Parametreler. Bu yöntem, öğeyi belirtilen yolda parametrelerini alır. Bu yöntem, belirtilen yolda öğesi için dinamik parametrelerini alır ve özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne. Windows PowerShell çalışma zamanı, döndürülen nesneyi cmdlet'e parametre eklemek için kullanır.

Bu Windows PowerShell kapsayıcısı sağlayıcısı, bu yöntem uygulamıyor. Ancak, aşağıdaki kod bu yöntem varsayılan uygulamasıdır.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Kod örneği

Tam örnek kod için bkz: [AccessDbProviderSample06 kod örneği](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Nesne türlerini tanımlama ve biçimlendirme

Bir sağlayıcı yazarken, var olan nesnelerde üye eklemek veya yeni nesneleri tanımlamak gerekli olabilir. Bu yapıldığında, Windows PowerShell nesnesinin üyelerini tanımlamak için kullanabileceğiniz bir türleri dosyası ve nesne nasıl görüntüleneceğini tanımlayan bir biçim dosyası oluşturmanız gerekir. Daha fazla bilgi için [genişletme nesne türleri ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcısı oluşturma

Bkz: [cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcıyı test etme

Windows PowerShell ile Windows PowerShell sağlayıcısı kayıtlı, komut satırında desteklenen cmdlet'lerini çalıştırarak test edebilirsiniz. Örneğin, örnek içerik sağlayıcısına test edin.

Kullanım `Get-Content` veritabanı tablosundaki tarafından belirtilen yolda belirtilen öğenin içeriğini almak için cmdlet `Path` parametresi. `ReadCount` Parametresi (varsayılan 1) okumak tanımlı içerik okuyucu öğe sayısını belirtir. Aşağıdaki komut girdiyle cmdlet iki satır (öğeleri) tablosundan alır ve bunların içeriğini görüntüler. Aşağıdaki örnek çıktıda, kurgusal bir Access veritabanı kullandığına dikkat edin.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sağlayıcılar oluşturma](./how-to-create-a-windows-powershell-provider.md)

[Tasarım bilgisayarınızı Windows PowerShell sağlayıcısı](./designing-your-windows-powershell-provider.md)

[Nesne türlerini genişletme ve biçimlendirme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Gezinti Windows PowerShell sağlayıcıyı uygulama](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlet, sağlayıcılar kaydetmek ve uygulamaları barındırmak nasıl](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)

[Windows PowerShell Programcı Kılavuzu](./windows-powershell-programmer-s-guide.md)
