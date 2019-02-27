---
title: Bir Windows PowerShell sürücüsünü sağlayıcı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846672"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Windows PowerShell Sürücü Sağlayıcısı Oluşturma

Bu konuda, bir Windows PowerShell sürücüsü bir veri deposuna erişmek için bir yol sağlayan bir Windows PowerShell sürücüsü sağlayıcısı oluşturmayı açıklar. Bu tür sağlayıcısı, aynı zamanda Windows PowerShell sürücüsü sağlayıcıları olarak da adlandırılır. Sağlayıcı tarafından kullanılan Windows PowerShell sürücülerini veri deposuna bağlanmak için bir yöntem sağlar.

Burada açıklanan Windows PowerShell sürücüsü sağlayıcısı, bir Microsoft Access veritabanına erişim sağlar. Bu sağlayıcı için Windows PowerShell sürücüsünü (mümkündür bir sürücü sağlayıcısı için herhangi bir sayıda sürücüler ekleme), veritabanı temsil eder. sürücünün en üst düzey kapsayıcıları veritabanındaki tabloları temsil eder ve satırlarda kapsayıcıları öğelerini temsil eder tablolar.

Bu konudaki bölümler listesi aşağıda verilmiştir. Bir Windows PowerShell sürücüsü sağlayıcısı yazma ile alışkın değilseniz, göründükleri sırayla bu bölümleri okuyun. Ancak, bir sürücü sağlayıcısı yazma ile bilginiz varsa, lütfen gereksinim duyduğunuz bilgileri doğrudan gidin.

- [Windows PowerShell sağlayıcısındaki sınıfı tanımlama](#Defining-the-Windows-PowerShell-Provider-Class)

- [Temel işlevlerini tanımlama](#Defining-Base-Functionality)

- [Sürücü durumu bilgilerini oluşturma](#Creating-Drive-State-Information)

- [Bir sürücü oluşturma](#Creating-a-Drive)

- [Dinamik parametreler için NewDrive ekleme](#Attaching-Dynamic-Parameters-to-NewDrive)

- [Bir sürücü kaldırılıyor](#Removing-a-Drive)

- [Varsayılan başlatma sürücüleri](#Initializing-Default-Drives)

- [Kod örneği](#Code-Sample)

- [Windows PowerShell sürücüsünü sağlayıcıyı test etme](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Windows PowerShell sağlayıcısındaki sınıfı tanımlama

Sürücü sağlayıcınız, türetilen bir .NET sınıfı tanımlamanız gerekir [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) temel sınıfı. Bu sürücü sağlayıcısı için sınıf tanımı aşağıda verilmiştir:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Bu örnekte, dikkat [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) sağlayıcı ve Windows PowerShell belirli bir özellik için bir kolay ad özniteliğini belirtir, sağlayıcı Windows PowerShell çalışma zamanına komut işleme sırasında ortaya çıkarır. Sağlayıcı özellikleri için olası değerler tarafından tanımlanan [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) sabit listesi. Bu sürücü sağlayıcısı bu özellikleri desteklemez.

## <a name="defining-base-functionality"></a>Temel işlevlerini tanımlama

Bölümünde anlatıldığı gibi [tasarım bilgisayarınızı Windows PowerShell sağlayıcısındaki](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıf türetilir [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) temel sınıf başlatma ve başlatmayı kaldırma sağlayıcı için gereken yöntemleri tanımlar. Özel oturum başlatma bilgileri ekleme ve sağlayıcı tarafından kullanılan kaynakları serbest bırakmak için işlevselliği uygulamak için bkz: [temel bir Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md). Ancak, çoğu sağlayıcıları (burada açıklanan sağlayıcısı dahil), Windows PowerShell tarafından sağlanan bu işlevsellik varsayılan uygulamasını kullanabilirsiniz.

## <a name="creating-drive-state-information"></a>Sürücü durumu bilgilerini oluşturma

Tüm Windows PowerShell sağlayıcıları sürücü sağlayıcınız sağlayıcınız çağırdığında, Windows PowerShell çalışma zamanı tarafından gereken herhangi bir durum bilgisini oluşturmak için gerek duyduğu anlamına gelir durum bilgisi olarak kabul edilir.

Bu sürücü sağlayıcısı için kitaplığın sürücü bilgilerinin bir parçası olarak tutulur veritabanına bağlantı durumu bilgilerini içerir. Bu bilgileri nasıl depolandığını gösteren kod işte [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) sürücü açıklayan nesnesi:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Bir sürücü oluşturma

Bir sürücü oluşturmak Windows PowerShell çalışma zamanı izin vermek için sürücü sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) yöntemi. Aşağıdaki kod uygulamasını gösterir [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) yöntemi bu sürücü sağlayıcısı için:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

Bu yöntemi geçersiz kılma aşağıdakileri yapmanız gerekir:

- Doğrulayın [System.Management.Automation.Psdriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) üyesi var ve veri deposuna bağlantı yapılabilir.

- Bir sürücü oluşturmak ve support, bağlantı üye doldurmak `New-PSDrive` cmdlet'i.

- Doğrulama [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) önerilen sürücü için nesne.

- Değiştirme [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) sürücü gerekli performans veya güvenilirlik bilgileri açıklayan nesne ya da bu sürücüyü kullanıp arayanlar için ek verileri sağlar.

- Kullanarak hatalarını [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) yöntemi ve ardından return `null`.

  Bu yöntem, yöntem veya bir sağlayıcıya özgü sürümü geçilen ya da sürücü bilgileri döndürür.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Dinamik parametreler için NewDrive ekleme

`New-PSDrive` Cmdlet'i sürücü sağlayıcınız tarafından desteklenen ek parametreler gerekebilir. Bu dinamik parametreler cmdlet'e iliştirmek için sağlayıcı uygulayan [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) yöntemi. Bu yöntem, özellikler ve alanları cmdlet'i sınıfına benzer öznitelikleri ayrıştırma ile sahip bir nesne döndürür veya bir [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) nesne.

Bu sürücü sağlayıcısı bu yöntemi geçersiz kılmaz. Ancak, aşağıdaki kod, bu yöntem varsayılan uygulanışı gösterilmektedir:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Bir sürücü kaldırılıyor

Veritabanı bağlantısını kapatmak için sürücü sağlayıcısı uygulamalıdır [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi. Bu yöntem, bir sağlayıcıya özgü bilgileri temizleniyor sonra sürücü bağlantıyı kapatır.

Aşağıdaki kod uygulamasını gösterir [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi bu sürücü sağlayıcısı için:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Sürücü kaldırılabilir, yöntem yöntemine geçirilen bilgileri döndürmelidir `drive` parametresi. Sürücü kaldırılamazsa yöntemi bir özel durum yazma ve ardından dönün `null`. Sağlayıcınız bu yöntemi yok sayın değil, bu yöntem varsayılan uygulaması yalnızca giriş olarak geçirilen sürücü bilgileri döndürür.

## <a name="initializing-default-drives"></a>Varsayılan başlatma sürücüleri

Sürücü sağlayıcısı uygular [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) sürücüleri bağlamak için yöntemi. Örneğin, Active Directory Sağlayıcısı varsayılan olarak bilgisayarın bir etki alanına katılmışsa adlandırma bağlamı için bir sürücü bağlama.

Bu yöntem, başlatılmış sürücüleriyle ilgili sürücü bilgileri koleksiyonunu ya da boş bir koleksiyon döndürür. Windows PowerShell çalışma zamanı çağrıları sonra bu yönteme bir çağrı yapılır [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Sağlayıcısı'nı başlatmak için yöntemi.

Bu sürücü sağlayıcısı geçersiz [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) yöntemi. Ancak, aşağıdaki kod, bir sürücü boş koleksiyonu döndürür. varsayılan uygulama gösterir:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>InitializeDefaultDrives'ı uygulama hakkında bunları unutmayın

Tüm sürücü sağlayıcıları kullanıcının bulunabilirliği yardımcı olmak için bir kök sürücü bağlamak. Kök sürücü bağlı diğer sürücülerin kökleri görevi gören konumları listeleyebilir. Örneğin, Active Directory sağlayıcısı bulunan adlandırma bağlamlarının listeleyen bir sürücü oluşturabilirsiniz `namingContext` Dağıtılmış Sistem ortamı (DSE) kök öznitelikleri. Bu, bağlama noktaları diğer sürücüleri için keşfetmek kullanıcılara yardımcı olur.

## <a name="code-sample"></a>Kod örneği

Tam örnek kod için bkz: [AccessDbProviderSample02 kod örneği](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Windows PowerShell sürücüsünü sağlayıcıyı test etme

Windows PowerShell ile Windows PowerShell sağlayıcısı kayıtlı olduğunda türetme tarafından kullanıma sunulan tüm cmdlet'leri dahil olmak üzere komut satırında desteklenen cmdlet'lerini çalıştırarak test edebilirsiniz. Şimdi örnek sürücü sağlayıcısı test edin.

1. Çalıştırma `Get-PSProvider` AccessDB sürücü sağlayıcısı mevcut olduğundan emin olmak için sağlayıcıları listesini almak için cmdlet:

   **PS> `Get-PSProvider`**

   Şu çıktı görünür:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Bir veritabanı sunucu adı (DSN) erişerek veritabanı için mevcut olduğundan emin olun **veri kaynakları** kısmı **Yönetimsel Araçlar** işletim sistemi için. İçinde **Kullanıcı DSN** tablo, çift **MS Access veritabanı** C:\ps\northwind.mdb sürücü yolu ekleyin.

3. Örnek sürücü Sağlayıcısı'nı kullanarak yeni bir sürücüye oluşturun:

   **PS > psdrive yeni-adı mydb-c:\ps\northwind.mdb - psprovider AccessDb kök**

   Şu çıktı görünür:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Bağlantıyı doğrulama. Bağlantı sürücü üyesi olarak tanımlı olduğundan, Get-PDDrive cmdlet'ini kullanarak denetleyebilirsiniz.

   > [!NOTE]
   > Sağlayıcı, bu etkileşim için kapsayıcı işlevi gereksinimleriniz değiştikçe kullanıcı henüz bir sürücü olarak sağlayıcısı ile etkileşime giremezler. Daha fazla bilgi için [bir Windows PowerShell kapsayıcısı sağlayıcısı oluşturma](./creating-a-windows-powershell-container-provider.md).

   **PS > (get-psdrive mydb) .connection**

   Şu çıktı görünür:

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Sürücü kaldırın ve kabuktan çıkış yapma:

   **PS > remove-psdrive mydb**

   **PS > Çık**

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell sağlayıcılar oluşturma](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell sağlayıcınız tasarlama](./designing-your-windows-powershell-provider.md)

[Temel Windows PowerShell sağlayıcısı oluşturma](./creating-a-basic-windows-powershell-provider.md)