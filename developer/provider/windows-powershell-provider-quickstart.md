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
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="5da57-102">Windows PowerShell Sağlayıcısı Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="5da57-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="5da57-103">Bu konu, yeni bir sürücüye oluşturmanın temel işlevlerini içeren bir Windows PowerShell sağlayıcısı oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="5da57-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="5da57-104">Sağlayıcılar hakkında genel bilgi için bkz. [Windows PowerShell sağlayıcısı genel bakış](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5da57-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="5da57-105">Daha kapsamlı işlevsellik sağlayıcılarıyla örnekleri için bkz. [sağlayıcısı örnekleri](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5da57-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="5da57-106">Temel sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="5da57-106">Writing a basic provider</span></span>

<span data-ttu-id="5da57-107">En temel bir Windows PowerShell sağlayıcısının oluşturmak ve sürücüleri kaldırmak için bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="5da57-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="5da57-108">Biz bu örnekte, uygulama [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) ve [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemlerinin [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5da57-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="5da57-109">Ayrıca, bir sağlayıcı sınıfı bildirmeyi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="5da57-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="5da57-110">Bir sağlayıcı yazdığınızda, varsayılan sürücüleri-sağlayıcısı kullanılabilir olduğunda otomatik olarak oluşturulan sürücüsü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5da57-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="5da57-111">Ayrıca, bu sağlayıcısı kullanan yeni sürücüleri oluşturmak için bir yöntem de tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5da57-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="5da57-112">Bu konudaki sağladığınız örnekleri temel alan [AccessDBProviderSample02](./accessdbprovidersample02.md) örnek, bir Access veritabanı bir Windows PowerShell sürücüsü olarak temsil eden daha büyük bir örnek bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="5da57-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="5da57-113">Projeyi ayarlama</span><span class="sxs-lookup"><span data-stu-id="5da57-113">Setting up the project</span></span>

<span data-ttu-id="5da57-114">Visual Studio'da AccessDBProviderSample adlı bir sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5da57-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="5da57-115">Derleme ve projenizi başlatın, Windows PowerShell başlar ve sağlayıcı oturuma yüklenir, projenizi yapılandırmak için aşağıdaki adımları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="5da57-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="5da57-116">Sağlayıcı projesini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5da57-116">Configure the provider project</span></span>

1. <span data-ttu-id="5da57-117">Projenize bir başvuru olarak System.Management.Automation derlemesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5da57-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="5da57-118">Tıklayın **Proje > AccessDBProviderSample özellikleri > hata ayıklama**.</span><span class="sxs-lookup"><span data-stu-id="5da57-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="5da57-119">İçinde **başlangıç projesi**, tıklayın **harici program Başlat**ve Windows PowerShell yürütülebilir dosyaya gidin (genellikle c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="5da57-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="5da57-120">Altında **Başlat seçenekleri**, aşağıdakileri girin **komut satırı bağımsız değişkenleri** kutusunda: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="5da57-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="5da57-121">Sağlayıcı Sınıf Bildirme</span><span class="sxs-lookup"><span data-stu-id="5da57-121">Declaring the provider class</span></span>

<span data-ttu-id="5da57-122">Bizim sağlayıcısı türetildiği [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5da57-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="5da57-123">(Erişmek ve öğeleri işleme, veri deposu gezinme ve alma ve öğelerinin içeriğini ayarlama) gerçek işlevleri sağlayan çoğu sağlayıcıları türetilmesi [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5da57-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="5da57-124">Öğesinden türetilen sınıf belirtme yanı sıra [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), kendisiyle süslemek [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5da57-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="5da57-125">NewDrive uygulama</span><span class="sxs-lookup"><span data-stu-id="5da57-125">Implementing NewDrive</span></span>

<span data-ttu-id="5da57-126">[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) yöntemi, Windows PowerShell altyapısı tarafından çağrıldığında, bir kullanıcı çağırdığında [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)sağlayıcınızın adı belirterek cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="5da57-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="5da57-127">PSDriveInfo parametresi Windows PowerShell altyapısı tarafından geçirilir ve yöntem yeni bir sürücüye Windows PowerShell altyapısı için döndürür.</span><span class="sxs-lookup"><span data-stu-id="5da57-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="5da57-128">Bu yöntem, yukarıda oluşturulan sınıf içinde bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5da57-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="5da57-129">Yöntemi, hem sürücü nesnesi ve geçirilen sürücünün kök var, iade emin olmak için ilk denetler `null` , aşağıdakilerden birini yapın.</span><span class="sxs-lookup"><span data-stu-id="5da57-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="5da57-130">Yeni bir sürücüye oluşturmak için bir iç sınıf AccessDBPSDriveInfo Oluşturucusu kullanır ve sürücü Access veritabanı bağlantısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5da57-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="5da57-131">Aşağıda, yeni bir sürücüye oluşturmak için kullanılan Oluşturucu içerir ve sürücü için durum bilgisi içeren AccessDBPSDriveInfo iç sınıftır.</span><span class="sxs-lookup"><span data-stu-id="5da57-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="5da57-132">RemoveDrive uygulama</span><span class="sxs-lookup"><span data-stu-id="5da57-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="5da57-133">[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) yöntemi, Windows PowerShell altyapısı tarafından çağrıldığında, bir kullanıcı çağırdığında [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="5da57-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="5da57-134">Bu sağlayıcı yöntemi veritabanına bağlantıyı kapatır.</span><span class="sxs-lookup"><span data-stu-id="5da57-134">The method in this provider closes the connection to the Access database.</span></span>

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