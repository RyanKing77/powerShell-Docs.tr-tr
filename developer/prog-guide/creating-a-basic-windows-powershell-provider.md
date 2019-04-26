---
title: Temel Windows PowerShell sağlayıcısı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082082"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Temel bir Windows PowerShell Sağlayıcısı Oluşturma

Bu konuda, bir Windows PowerShell sağlayıcısı oluşturmayı öğrenmek için başlangıç noktasıdır. Burada açıklanan temel sağlayıcısı ve sağlayıcı durdurmaktan yöntemler sağlar ve bu sağlayıcı veri deposuna erişmek için alın veya veri deposuna veri kümesi için bir yol sağlamaz ancak tarafından gerekli olan temel işlevleri sağlar Tüm sağlayıcıları.

Daha önce açıklanan temel sağlayıcısı belirtildiği gibi burada başlatma ve durdurma sağlayıcı yöntemlerini uygular. Windows PowerShell çalışma zamanı başlatıp sağlayıcı kapatması için bu yöntemleri çağırır.

> [!NOTE]
> Bu sağlayıcı örneği, Windows PowerShell tarafından sağlanan AccessDBSampleProvider01.cs dosyasında bulabilirsiniz.

Bu konudaki bölümler şunları içerir:

- [Windows PowerShell sağlayıcısındaki sınıfı tanımlama](#Defining-the-Windows-PowerShell-Provider-Class)

- [Sağlayıcıya özel durum bilgilerini tanımlama](#Defining-Provider-Specific-State-Information)

- [Sağlayıcıyı başlatırken](#Initializing-the-Provider)

- [Dinamik parametreleri Başlat](#Start-Dynamic-Parameters)

- [Sağlayıcı başlatmayı kaldırma](#Uninitializing-the-Provider)

- [Kod örneği](#Code-Sample)

- [Windows PowerShell sağlayıcıyı test etme](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Windows PowerShell sağlayıcısındaki sınıfı tanımlama

Bir Windows PowerShell sağlayıcısı oluşturmanın ilk adımı, .NET sınıf tanımlamaktır. Bu temel sağlayıcı adlı bir sınıf tanımlar `AccessDBProvider` türetilen [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) temel sınıfı.

Sağlayıcı sınıflarınızdaki yerleştirmeniz önerilir bir `Providers` API ad alanınızın, örneğin, xxx ad alanı. PowerShell.Providers. Bu sağlayıcıyı kullanan `Microsoft.Samples.PowerShell.Provider` ad alanı, tüm Windows PowerShell sağlayıcısı örnekleri çalıştırıldığı.

> [!NOTE]
> Sınıf bir Windows PowerShell sağlayıcısı için genel olarak açıkça işaretlenmelidir. Genel olarak işaretlenmemiş sınıflar için iç varsayılan ve Windows PowerShell çalışma zamanı tarafından bulunmaz.

Bu temel sağlayıcı için bir sınıf tanımı aşağıda verilmiştir:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Şu sınıf tanımından önce bildirmelisiniz [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) sözdizimi [CmdletProvider()] özniteliğiyle.

Daha fazla gerekirse sınıf tanımlamak için öznitelik anahtar sözcükleri ayarlayabilirsiniz. Dikkat [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) öznitelik burada bildirildi, iki parametre içerir. İlk öznitelik parametresi sağlayıcının kullanıcı daha sonra değiştirebileceğiniz varsayılan dostu adını belirtir. İkinci parametre, sağlayıcı Windows PowerShell çalışma zamanının komut işleme sırasında ortaya koyan Windows PowerShell tarafından tanımlanan özelliklerini belirtir. Sağlayıcı özellikleri için olası değerler tarafından tanımlanan [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu temel sağlayıcısı olduğundan, hiçbir özellikleri destekler.

> [!NOTE]
> Windows PowerShell sağlayıcısını tam olarak nitelenmiş adını derleme adı ve sağlayıcı kaydı sırasında Windows PowerShell tarafından belirlenen diğer özniteliklerini içerir.

## <a name="defining-provider-specific-state-information"></a>Sağlayıcıya özel durum bilgilerini tanımlama

[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) temel sınıf ve tüm türetilen sınıflarının değerlendirilir durum bilgisi olmayan Windows PowerShell çalışma zamanı sağlayıcısı örnekleri yalnızca gerektiği oluşturduğundan. Bu nedenle, sağlayıcınız sağlayıcıya özgü veriler için tam denetim ve durumu Bakımı gerektiriyorsa, bunu bir sınıftan türetilmelidir [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) sınıfı. Windows PowerShell çalışma zamanı çağırdığında, sağlayıcıya özgü verileri erişilebilir olacak şekilde durumunu korumak üzere gerekli üyeler türetilmiş sınıfınızın tanımlamalıdır [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Sağlayıcısı'nı başlatmak için yöntemi.

Bir Windows PowerShell sağlayıcısı, ayrıca bağlantı tabanlı durumu koruyabilir. Bağlantı durumu bakımı hakkında daha fazla bilgi için bkz. [sürücü bir PowerShell sağlayıcı oluşturma](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Sağlayıcıyı başlatırken

Windows PowerShell çalışma zamanı çağrıları sağlayıcıyı başlatmak için [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Windows PowerShell başlatıldığında yöntemi. Sağlayıcınız bu yöntemin, sadece döndürür varsayılan uygulama çoğunlukla, kullanabilirsiniz [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) sağlayıcınız tanımlayan nesne. Ancak, ek başlatma bilgileri eklemek istediğiniz durumlarda, kendi uygulamalıdır [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) değiştirilmişbirsürümünüdöndürüryöntemi[ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) sağlayıcınıza geçirilen nesne. Genel olarak, bu yöntem sağlanan döndürmelidir [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) nesnesi veya bir değişiklik için geçirilen [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) nesnesinin diğer başlatma bilgileri içerir.

Bu temel sağlayıcısı bu yöntemi geçersiz kılmaz. Ancak, aşağıdaki kod, bu yöntem varsayılan uygulanışı gösterilmektedir:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Sağlayıcı açıklandığı sağlayıcıya özgü bilgileri durumunu koruyabilir [tanımlama sağlayıcıya özgü veri durumu](#Defining-Provider-Specific-State-Information). Bu durumda, uygulamanızı kılmalı [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) türetilmiş sınıfın bir örneğine geri dönmek için yöntemi.

## <a name="start-dynamic-parameters"></a>Dinamik parametreleri Başlat

Sağlayıcı uygulamanıza [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) yöntemine ek parametreler gerekebilir. Bu durumda, sağlayıcı geçersiz kılmalıdır [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) yöntem ve özellikleri ve alanları ayrıştırma ile sahip bir nesne öznitelikleri benzeyen dönüş bir cmdlet'i sınıf veya [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne.

Bu temel sağlayıcısı bu yöntemi geçersiz kılmaz. Ancak, aşağıdaki kod, bu yöntem varsayılan uygulanışı gösterilmektedir:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Sağlayıcı başlatmayı kaldırma

Windows PowerShell sağlayıcısını kullanan kaynakları serbest bırakacak sağlayıcınız kendi uygulamalıdır [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) yöntemi. Bu yöntem, oturum kapatma sağlayıcısında kapatmak için Windows PowerShell çalışma zamanı tarafından çağrılır.

Bu temel sağlayıcısı bu yöntemi geçersiz kılmaz. Ancak, aşağıdaki kod, bu yöntem varsayılan uygulanışı gösterilmektedir:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Kod örneği

Tam örnek kod için bkz: [AccessDbProviderSample01 kod örneği](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell sağlayıcıyı test etme

Windows PowerShell ile Windows PowerShell sağlayıcısı kaydedildikten komut satırında desteklenen cmdlet'lerini çalıştırarak test edebilirsiniz. Bu temel sağlayıcı için yeni kabuğunu çalıştırın ve `Get-PSProvider` cmdlet'ini sağlayıcılarının listesini almak ve AccessDb sağlayıcısı mevcut olduğundan emin olun.

```powershell
Get-PSProvider
```

Şu çıktı görünür:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sağlayıcılar oluşturma](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell sağlayıcınız tasarlama](./designing-your-windows-powershell-provider.md)