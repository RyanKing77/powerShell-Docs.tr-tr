---
title: Windows PowerShell sağlayıcınız tasarlama | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081827"
---
# <a name="designing-your-windows-powershell-provider"></a>Windows PowerShell Sağlayıcınızı Tasarlama

Ürün veya yapılandırma depolanmış veriler, kullanıcının gidin veya betiğe gitmek için istediğiniz bir veritabanı gibi bir dizi sunarsa bir Windows PowerShell sağlayıcısı uygulamalıdır. Çok düzeyli bir kapsayıcı olmasa bile bir kapsayıcı ürününüzü sağlar, ayrıca, bir Windows PowerShell sağlayıcısı için uygulanacak mantıklıdır. Örneğin, cmdlet fiili kopyalama, taşıma, yeniden adlandırma, yeni veya kaldırma ürün veya yapılandırma verileriniz üzerinde bir işlem olarak algılama yaparsa bir Windows PowerShell kapsayıcısı sağlayıcısı uygulamak isteyebilirsiniz.

## <a name="windows-powershell-paths-identify-your-provider"></a>Sağlayıcınız Windows PowerShell yolları belirle

Windows PowerShell çalışma zamanı, uygun Windows PowerShell Sağlayıcısı'na erişmek için Windows PowerShell yollarını kullanır. Bir cmdlet bu yollardan belirttiğinde, çalışma zamanı ilişkili veri deposuna erişmek için hangi sağlayıcı bilir. Bu yolları sürücü nitelenmiş yollar, sağlayıcı nitelenmiş yollar, sağlayıcı doğrudan yolları ve sağlayıcı iç yolları içerir. Her bir Windows PowerShell sağlayıcısı, bir veya daha fazla Bu yolları desteklemesi gerekir.

Windows PowerShell yolları hakkında daha fazla bilgi için bkz. nasıl Windows PowerShell çalışır.

### <a name="defining-a-drive-qualified-path"></a>Sürücü nitelenmiş bir yolu tanımlama

Bir fiziksel sürücü bulunan verilere erişmesine izin vermek için Windows PowerShell sağlayıcısındaki sürücü nitelenmiş bir yol desteklemesi gerekir. Bu yol, bir üste (:), örneğin mydrive:\abc\bar sürücü adı ile başlar.

### <a name="defining-a-provider-qualified-path"></a>Sağlayıcı nitelenmiş bir yolu tanımlama

Başlatıp uninitialize sağlayıcısı Windows PowerShell çalışma zamanı izin vermek için Windows PowerShell sağlayıcısındaki sağlayıcısı nitelenmiş bir yol desteklemesi gerekir. Örneğin, dosya sistemi::\\\uncshare\abc\bar olan Windows PowerShell tarafından vermek amacıyla sağlanmış dosya sistemi sağlayıcısı için sağlayıcı nitelenmiş yolu.

### <a name="defining-a-provider-direct-path"></a>Bir sağlayıcı doğrudan yolu tanımlama

Windows PowerShell sağlayıcınız uzaktan erişime izin vermek için doğrudan Windows PowerShell sağlayıcısı için geçerli konumun geçirmek için bir sağlayıcı doğrudan yolu desteklemelidir. Örneğin, kayıt defteri Windows PowerShell sağlayıcısını kullanabilirsiniz \\\server\regkeypath sağlayıcısı doğrudan yol.

### <a name="defining-a-provider-internal-path"></a>Sağlayıcı İç bir yolu tanımlama

Sağlayıcı cmdlet'ini kullanarak Windows PowerShell uygulama programlama arabirimleri (API) veri erişim izin vermek için Windows PowerShell sağlayıcısındaki sağlayıcısı iç yolu desteklemelidir. Bu yolu sonra gösterilen "::" Sağlayıcı nitelikli yolda. Örneğin, dosya sistemi Windows PowerShell sağlayıcısı için sağlayıcı iç yolu olan \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Depolanan verileri değiştirme

Temel alınan veri deposunu değiştirme yöntemleri geçersiz kılarken, her zaman çağrı [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) öğesinin en güncel sürümüyle yöntemi tarafından değiştirildi yöntem. Sağlayıcı altyapı öğesi nesnesi zaman - PassThru parametresini kullanıcının belirttiği gibi işlem hattına geçirilmesi gerekip gerekmediğini belirler. En güncel öğesi alınırken pahalı bir işlem (performance-wise) ise, gerçekten elde edilen öğeyi yazma gerekip gerekmediğini belirlemek için Context.PassThru özelliğini test edebilirsiniz.

## <a name="choose-a-base-class-for-your-provider"></a>Sağlayıcınız için bir temel sınıf seçin

Windows PowerShell bir dizi, kendi Windows PowerShell sağlayıcısını uygulamak için kullanabileceğiniz temel sınıflar sağlar. Bir sağlayıcı tasarlarken, gereksinimlerinize en uygun Bu bölümde açıklanan temel sınıf seçin.

Her Windows PowerShell sağlayıcısı temel sınıfı bir dizi cmdlet kullanılabilir hale getirir. Bu bölümde, cmdlet'ler açıklanmaktadır, ancak kendi parametrelerini açıklamaz.

Oturum durumu kullanarak, Windows PowerShell çalışma zamanı birkaç konumu cmdlet'lerin belirli Windows PowerShell sağlayıcılarına gibi kullanılabilmesini `Get-Location`, `Set-Location`, `Pop-Location`, ve `Push-Location` cmdlet'leri. Kullanabileceğiniz `Get-Help` bu konuma cmdlet'ler hakkında bilgi almak için cmdlet'i.

### <a name="cmdletprovider-base-class"></a>CmdletProvider temel sınıfı

[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) sınıfı, temel bir Windows PowerShell sağlayıcısını tanımlar. Bu sınıf, sağlayıcı bildirimi destekler ve özellikler ve tüm Windows PowerShell sağlayıcıları için kullanılabilir olan yöntemler sunar. Sınıfı tarafından çağrılan `Get-PSProvider` cmdlet'ini oturum açmak için tüm kullanılabilir sağlayıcılar listesi. Bu cmdlet uygulamasının oturum durumu tarafından verilmiştir.

> [!NOTE]
> Windows PowerShell sağlayıcıları tüm Windows PowerShell dil kapsamlar için kullanılabilir.

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider temel sınıfı

[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) yeni sürücüler ekleyerek, var olan sürücüleri kaldırma ve varsayılan sürücüleri başlatma işlemleri destekleyen bir Windows PowerShell sürücüsü sağlayıcısına sınıfı tanımlar. Örneğin, sürücüleri, sabit disk sürücüleri ve CD/DVD cihaz sürücüleri gibi bağlı tüm birimler için Windows PowerShell tarafından sağlanan dosya sistemi sağlayıcıyı başlatır.

Bu sınıfın türetildiği [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) temel sınıfı. Aşağıdaki tabloda, bu sınıf tarafından kullanıma sunulan cmdlet'leri listelenmektedir. Listelenenlere, `Get-PSDrive` (oturum durumu tarafından gösterilen) kullanılabilir sürücüler almak için kullanılan bir ilgili cmdlet cmdlet'tir.

|Cmdlet|Açıklama|
|------------|----------------|
|`New-PSDrive`|Yeni bir sürücü için bir oturum oluşturur ve sürücü bilgileri akışa sunar.|
|`Remove-PSDrive`|Bir sürücü oturumdan kaldırır.|

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider temel sınıfı

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) sınıfı, veri deposunun bireysel öğeleri üzerinde işlemler gerçekleştiren bir Windows PowerShell öğe sağlayıcısı tanımlar ve tüm kapsayıcı varsaymaz veya Gezinti özellikleri. Bu sınıfın türetildiği [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) temel sınıfı. Aşağıdaki tabloda, bu sınıf tarafından kullanıma sunulan cmdlet'leri listelenmektedir.

|Cmdlet|Açıklama|
|------------|----------------|
|`Clear-Item`|Öğelerinin belirtilen konumda geçerli bir içeriği temizler ve sağlayıcı tarafından belirtilen "clear" değeri ile değiştirir. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|
|`Get-Item`|Belirtilen konumdan öğeleri alır ve sonuç nesneleri akışları.|
|`Invoke-Item`|Belirtilen yoldaki öğesi için varsayılan eylem çağırır.|
|`Set-Item`|Belirtilen konumda belirtilen değere sahip bir öğe ayarlar. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|
|`Resolve-Path`|Bir Windows PowerShell yolu ve akışları yol bilgisi için joker karakterler çözümler.|
|`Test-Path`|Belirtilen yol için test eder ve döndürür `true` varsa ve `false` Aksi takdirde. Bu cmdlet desteklemek için uygulanan `IsContainer` parametresi için [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) yöntemi.|

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider temel sınıfı

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) sınıfı, kullanıcı için veri deposu öğeleri için bir kapsayıcı gösterir bir Windows PowerShell kapsayıcısı sağlayıcısı tanımlar. Yalnızca bir kapsayıcı (iç içe geçmiş kapsayıcılar yok) içindeki öğeler olduğunda bir Windows PowerShell kapsayıcısı sağlayıcısı kullanılabileceğini unutmayın. İç içe geçmiş kapsayıcılar varsa, Windows PowerShell Gezinti sağlayıcıyı uygulama gerekir.

Bu sınıfın türetildiği [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) temel sınıfı. Aşağıdaki tabloda, bu sınıf tarafından uygulanan cmdlet'leri tanımlar.

|Cmdlet|Açıklama|
|------------|----------------|
|`Copy-Item`|Öğeleri kopyalar bir konumdan diğerine. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|
|`Get-Childitem`|Belirtilen konumdaki alt öğelerini alır ve bunları nesneler olarak akışları.|
|`New-Item`|Belirtilen konumda yeni bir öğe oluşturur ve akışları sonuç nesnesi.|
|`Remove-Item`|Öğeleri belirtilen konumdan kaldırır.|
|`Rename-Item`|Belirtilen konumda bir öğeyi yeniden adlandırır. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider temel sınıfı

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfını kullanan birden fazla kapsayıcı öğeleri için işlemler gerçekleştiren bir Windows PowerShell Gezinti sağlayıcı tanımlar. Bu sınıfın türetildiği [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) temel sınıfı. Aşağıdaki tabloda, bu sınıf tarafından kullanıma cmdlet öğelerini listeler.

|Cmdlet|Açıklama|
|------------|----------------|
|Birleştir-yolu|İki yolu yolları arasında bir sağlayıcıya özgü sınırlayıcıyı kullanarak tek bir yol birleştirir. Bu cmdlet, dizeleri akışları.|
|`Move-Item`|Öğe belirtilen konuma taşır. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|

İlgili cmdlet, Windows PowerShell tarafından vermek amacıyla sağlanmış temel ayrıştırma yolu cmdlet'tir. Bu cmdlet bir Windows PowerShell desteği yolu ayrıştırmak için kullanılan `Parent` parametresi. Bu, üst yol dizesi akışları.

## <a name="select-provider-interfaces-to-support"></a>Destek Sağlayıcısı arayüzleri seçin

Windows PowerShell temel sınıflarının birinden türettikten ek olarak, Windows PowerShell sağlayıcısı bir veya daha fazla aşağıdaki sağlayıcısı arayüzleri öğesinden türetme tarafından diğer işlevleri destekleyebilir. Bu bölümde, bu arabirimleri ve her tarafından desteklenen cmdlet'leri tanımlar. Arabirim tarafından desteklenen cmdlet'leri için parametreleri açıklamaz. Cmdlet'i parametre bilgileri kullanarak çevrimiçi kullanılabilir `Get-Command` ve `Get-Help` cmdlet'leri.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) arabirimi bir veri öğesinin içeriği işlemleri gerçekleştiren bir içerik sağlayıcı tanımlar. Aşağıdaki tabloda, bu arabirim tarafından kullanıma sunulan cmdlet'leri listelenmektedir.

|Cmdlet|Açıklama|
|------------|----------------|
|`Add-Content`|Belirtilen değer uzunlukları içeriğini belirtilen öğeyi ekler. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|
|`Clear-Content`|Belirtilen öğenin içeriğini "clear" değerine ayarlar. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|
|`Get-Content`|Belirtilen öğelerin içeriklerini alır ve sonuçta elde edilen nesnelerin akışları.|
|`Set-Content`|Belirtilen öğeler için var olan içeriğin değiştirir. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) veri deposunda öğelerin özelliklerini işlemleri gerçekleştiren bir özelliği Windows PowerShell sağlayıcısı arabirimi tanımlar. Aşağıdaki tabloda, bu arabirim tarafından kullanıma sunulan cmdlet'leri listelenmektedir.

> [!NOTE]
> `Path` Bu cmdlet'ler parametresi yerine bir özelliği tanımlayan bir öğe için bir yol gösterir.

|Cmdlet|Açıklama|
|------------|----------------|
|`Clear-ItemProperty`|Belirtilen öğelerin özelliklerini "clear" değerine ayarlar. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|
|`Get-ItemProperty`|Belirtilen öğelerden özellikleri alır ve sonuçta elde edilen nesnelerin akışları.|
|`Set-ItemProperty`|Belirtilen değerlerle belirtilen öğelerin özelliklerini ayarlar. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

[System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) arabirimi, türetilen [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), tanımlayan bir sağlayıcısı için desteklenen cmdlet'lerini dinamik parametreleri belirtir. Bu tür sağlayıcısı, çalışma zamanında, örneğin, yeni bir özellik işlemi özellikleri tanımlanabilir işlemleri gerçekleştirir. Bu işlemler, Özellikler statik olarak tanımlanan öğelerde mümkün değildir. Aşağıdaki tabloda, bu arabirim tarafından kullanıma sunulan cmdlet'leri listelenmektedir.

|Cmdlet|Açıklama|
|------------|----------------|
|`Copy-ItemProperty`|Bir özellik için başka bir öğe belirtilen öğeyi kopyalar. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|
|`Move-ItemProperty`|Bir özelliği belirtilen öğeyi başka bir öğeye hareket ettirir. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|
|`New-ItemProperty`|Belirtilen öğe üzerinde bir özellik oluşturur ve sonuç nesneleri akışları.|
|`Remove-ItemProperty`|Bir özelliği için belirtilen öğeleri kaldırır.|
|`Rename-ItemProperty`|Bir özelliği belirtilen öğelerin yeniden adlandırır. Bu cmdlet bir çıkış nesnesi ardışık düzeninden sürece geçmez, `PassThru` parametre belirtildi.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

[System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) arabirimi sağlayıcı için güvenlik tanımlayıcısı işlevi ekler. Bu arabirim, almak ve veri deposunda öğenin güvenlik tanımlayıcısı bilgilerini ayarlamak kullanıcı sağlar. Aşağıdaki tabloda, bu arabirim tarafından kullanıma sunulan cmdlet'leri listelenmektedir.

|Cmdlet|Açıklama|
|------------|----------------|
|`Get-Acl`|Örneğin, işletim sistemi kaynaklarını korumak için kullanılan bir güvenlik tanımlayıcısı, bir dosya veya bir nesne bir parçası olan bir erişim denetimi listede (ACL) yer alan bilgileri alır.|
|`Set-Acl`|Bir ACL bilgilerini ayarlar. Örneği hatalardan biri [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) belirtilen yol için belirtilen öğeleri üzerinde. Bu cmdlet Windows PowerShell sağlayıcısını güvenlik bilgileri ayarını destekliyorsa, dosyalar, anahtarları ve alt anahtarları hakkında bilgi kayıt defteri veya diğer sağlayıcısı öğeyi ayarlayabilirsiniz.|

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sağlayıcılar oluşturma](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell nasıl çalışır?](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)