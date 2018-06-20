---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC komut dosyası kaynağı
ms.openlocfilehash: 1163d454972d8ee519d1c55b77bb85979faf3536
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189457"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="24c21-103">DSC komut dosyası kaynağı</span><span class="sxs-lookup"><span data-stu-id="24c21-103">DSC Script Resource</span></span>


> <span data-ttu-id="24c21-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="24c21-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="24c21-105">**Betik** kaynağı içinde Windows PowerShell istenen durum yapılandırması (DSC), Windows PowerShell komut dosyası blokları hedef düğümlerinde çalıştırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="24c21-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="24c21-106">`Script` Kaynak `GetScript`, `SetScript`, ve `TestScript` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="24c21-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="24c21-107">Bu özelliklerin her hedef düğümde çalışacak komut dosyası blokları ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="24c21-107">These properties should be set to script blocks that will run on each target node.</span></span>

<span data-ttu-id="24c21-108">`GetScript` Betik bloğu geçerli düğüm durumunu temsil eden bir hashtable döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="24c21-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="24c21-109">Hashtable yalnızca bir anahtar içermelidir `Result` ve değer türü olmalıdır `String`.</span><span class="sxs-lookup"><span data-stu-id="24c21-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="24c21-110">Herhangi bir şeyi geri dönmek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="24c21-110">It is not required to return anything.</span></span> <span data-ttu-id="24c21-111">DSC çıkış bu betik bloğunun herhangi bir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="24c21-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="24c21-112">`TestScript` Betik bloğu geçerli düğüm değiştirilmesi gerekip gerekmediğini belirlemek.</span><span class="sxs-lookup"><span data-stu-id="24c21-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="24c21-113">Döndürme zorunluluğu `$true` düğümü güncel ise.</span><span class="sxs-lookup"><span data-stu-id="24c21-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="24c21-114">Döndürme zorunluluğu `$false` düğümün yapılandırma güncel değil ve tarafından güncelleştirilmesi `SetScript` betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="24c21-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="24c21-115">`TestScript` Betik bloğu DSC tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="24c21-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="24c21-116">`SetScript` Betik bloğu düğüm değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="24c21-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="24c21-117">Buna göre DSC denir `TestScript` engelleme return `$false`.</span><span class="sxs-lookup"><span data-stu-id="24c21-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="24c21-118">Yapılandırma komut dosyanıza değişkenlerinden kullanmanız gerekip gerekmediğini `GetScript`, `TestScript`, veya `SetScript` komut dosyası blokları, kullanın `$using:` kapsam (bir örnek için aşağıya bakın).</span><span class="sxs-lookup"><span data-stu-id="24c21-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="24c21-119">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24c21-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="24c21-120">Özellikler</span><span class="sxs-lookup"><span data-stu-id="24c21-120">Properties</span></span>

|  <span data-ttu-id="24c21-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="24c21-121">Property</span></span>  |  <span data-ttu-id="24c21-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24c21-122">Description</span></span>   |
|---|---|
| <span data-ttu-id="24c21-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="24c21-123">GetScript</span></span>| <span data-ttu-id="24c21-124">Çağırdığınızda, çalıştırılan Windows PowerShell komut dosyası bloğunda sağlar [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="24c21-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="24c21-125">Bu bloğu bir hashtable döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="24c21-125">This block must return a hashtable.</span></span> <span data-ttu-id="24c21-126">Hashtable yalnızca bir anahtar içermelidir **sonuç** ve değer türü olmalıdır **dize**.</span><span class="sxs-lookup"><span data-stu-id="24c21-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>|
| <span data-ttu-id="24c21-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="24c21-127">SetScript</span></span>| <span data-ttu-id="24c21-128">Windows PowerShell komut dosyası bloğunda sağlar.</span><span class="sxs-lookup"><span data-stu-id="24c21-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="24c21-129">Ne zaman çağırmayı [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet'ini **TestScript** bloğu ilk çalışır.</span><span class="sxs-lookup"><span data-stu-id="24c21-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="24c21-130">Varsa **TestScript** engelleme döndürür **$false**, **SetScript** bloğu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="24c21-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="24c21-131">Varsa **TestScript** engelleme döndürür **$true**, **SetScript** blok çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="24c21-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>|
| <span data-ttu-id="24c21-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="24c21-132">TestScript</span></span>| <span data-ttu-id="24c21-133">Windows PowerShell komut dosyası bloğunda sağlar.</span><span class="sxs-lookup"><span data-stu-id="24c21-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="24c21-134">Ne zaman çağırmayı [başlangıç DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet'i, bu bloğu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="24c21-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="24c21-135">Döndürürse **$false**, SetScript blok çalışır.</span><span class="sxs-lookup"><span data-stu-id="24c21-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="24c21-136">Döndürürse **$true**, çalıştırılacak blok olacak SetScript.</span><span class="sxs-lookup"><span data-stu-id="24c21-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="24c21-137">**TestScript** bloğu ayrıca çalışır çağırdığınızda [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="24c21-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="24c21-138">Ancak, bu durumda, **SetScript** bloğu değil çalıştırmak, hangi TestScript değerin olsun engelle döndürür.</span><span class="sxs-lookup"><span data-stu-id="24c21-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="24c21-139">**TestScript** gerçek yapılandırması geçerli istenen durum yapılandırması ve False eşleşirse, eşleşmiyorsa, blok True döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="24c21-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="24c21-140">(Geçerli istenen durum yapılandırması, DSC kullanarak düğümde kamulaştırılmış son yapılandırmadır.)</span><span class="sxs-lookup"><span data-stu-id="24c21-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>|
| <span data-ttu-id="24c21-141">kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="24c21-141">Credential</span></span>| <span data-ttu-id="24c21-142">Bu komut dosyasını çalıştırmak için kimlik bilgileri gerekli olduğunda kullanılacak kimlik bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="24c21-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
| <span data-ttu-id="24c21-143">dependsOn</span><span class="sxs-lookup"><span data-stu-id="24c21-143">DependsOn</span></span>| <span data-ttu-id="24c21-144">Bu kaynak yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmalısınız gösterir.</span><span class="sxs-lookup"><span data-stu-id="24c21-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="24c21-145">Örneğin, kaynak yapılandırması Kimliğini komut dosyası çalıştırmak istediğiniz bloğu ilk ise **ResourceName** ve türünü **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="24c21-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="24c21-146">Örnek 1</span><span class="sxs-lookup"><span data-stu-id="24c21-146">Example 1</span></span>
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript =
        {
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
    }
}
```

## <a name="example-2"></a><span data-ttu-id="24c21-147">Örnek 2</span><span class="sxs-lookup"><span data-stu-id="24c21-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = {
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }
        TestScript = {
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = {
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="24c21-148">Bu kaynak yapılandırma sürümü bir metin dosyasına yazma.</span><span class="sxs-lookup"><span data-stu-id="24c21-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="24c21-149">Bu sürüm, istemci bilgisayarda kullanılabilir, ancak her biri için geçirilecek sahiptir herhangi bir düğüme değil `Script` kaynağın komut dosyası blokları PowerShell'ın ile `using` kapsam.</span><span class="sxs-lookup"><span data-stu-id="24c21-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="24c21-150">Ne zaman oluşturuluyor düğümün MOF dosyası değeri `$version` değişkeni istemci bilgisayardaki bir metin dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="24c21-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="24c21-151">DSC değiştirir `$using:version` her komut dosyası değişkenleri engelleme değeriyle `$version` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="24c21-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>