---
title: Windows PowerShell sağlayıcısındaki hızlı başlangıç | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054926"
---
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell Sağlayıcısı Hızlı Başlangıç

Bu konu, yeni bir sürücüye oluşturmanın temel işlevlerini içeren bir Windows PowerShell sağlayıcısı oluşturma işlemini açıklar. Sağlayıcılar hakkında genel bilgi için bkz. [Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md). Daha kapsamlı işlevsellik sağlayıcılarıyla örnekleri için bkz. [sağlayıcısı örnekleri](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Temel sağlayıcısı yazma

En temel bir Windows PowerShell sağlayıcısının oluşturmak ve sürücüleri kaldırmak için bir işlevdir. Biz bu örnekte, uygulama [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) ve [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemlerinin [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı. Ayrıca, bir sağlayıcı sınıfı bildirmeyi görürsünüz.

Bir sağlayıcı yazdığınızda, varsayılan sürücüleri-sağlayıcısı kullanılabilir olduğunda otomatik olarak oluşturulan sürücüsü belirtebilirsiniz. Ayrıca, bu sağlayıcısı kullanan yeni sürücüleri oluşturmak için bir yöntem de tanımlayın.

Bu konudaki sağladığınız örnekleri temel alan [AccessDBProviderSample02](./accessdbprovidersample02.md) örnek, bir Access veritabanı bir Windows PowerShell sürücüsü olarak temsil eden daha büyük bir örnek bir parçasıdır.

### <a name="setting-up-the-project"></a>Projeyi ayarlama

Visual Studio'da AccessDBProviderSample adlı bir sınıf kitaplığı projesi oluşturun. Derleme ve projenizi başlatın, Windows PowerShell başlar ve sağlayıcı oturuma yüklenir, projenizi yapılandırmak için aşağıdaki adımları tamamlayın.

##### <a name="configure-the-provider-project"></a>Sağlayıcı projesini yapılandırma

1. Projenize bir başvuru olarak System.Management.Automation derlemesini ekleyin.

2. Tıklayın **Proje > AccessDBProviderSample özellikleri > hata ayıklama**. İçinde **başlangıç projesi**, tıklayın **harici program Başlat**ve Windows PowerShell yürütülebilir dosyaya gidin (genellikle c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. Altında **Başlat seçenekleri**, aşağıdakileri girin **komut satırı bağımsız değişkenleri** kutusunda: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Sağlayıcı Sınıf Bildirme

Bizim sağlayıcısı türetildiği [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı. (Erişmek ve öğeleri işleme, veri deposu gezinme ve alma ve öğelerinin içeriğini ayarlama) gerçek işlevleri sağlayan çoğu sağlayıcıları türetilmesi [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.

Öğesinden türetilen sınıf belirtme yanı sıra [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), kendisiyle süslemek [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) örnekte gösterildiği gibi.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>NewDrive uygulama

[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) yöntemi, Windows PowerShell altyapısı tarafından çağrıldığında, bir kullanıcı çağırdığında [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)sağlayıcınızın adı belirterek cmdlet'i. PSDriveInfo parametresi Windows PowerShell altyapısı tarafından geçirilir ve yöntem yeni bir sürücüye Windows PowerShell altyapısı için döndürür. Bu yöntem, yukarıda oluşturulan sınıf içinde bildirilmesi gerekir.

Yöntemi, hem sürücü nesnesi ve geçirilen sürücünün kök var, iade emin olmak için ilk denetler `null` , aşağıdakilerden birini yapın. Yeni bir sürücüye oluşturmak için bir iç sınıf AccessDBPSDriveInfo Oluşturucusu kullanır ve sürücü Access veritabanı bağlantısını temsil eder.

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

Aşağıda, yeni bir sürücüye oluşturmak için kullanılan Oluşturucu içerir ve sürücü için durum bilgisi içeren AccessDBPSDriveInfo iç sınıftır.

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a>RemoveDrive uygulama

[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi, Windows PowerShell altyapısı tarafından çağrıldığında, bir kullanıcı çağırdığında [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet'i. Bu sağlayıcı yöntemi veritabanına bağlantıyı kapatır.

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```