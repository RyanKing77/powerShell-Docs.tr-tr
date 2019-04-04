---
ms.date: 08/24/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC Script kaynağı
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: 0ca836d1044e46d3a7dcbc69fa93d84f74848559
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920365"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="a4d38-103">DSC Script kaynağı</span><span class="sxs-lookup"><span data-stu-id="a4d38-103">DSC Script Resource</span></span>

> <span data-ttu-id="a4d38-104">Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a4d38-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="a4d38-105">**Betik** kaynak olarak Windows PowerShell Desired State Configuration (DSC), Windows PowerShell komut dosyası blokları hedef düğümleri üzerinde çalışmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4d38-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="a4d38-106">**Betik** kaynak kullanan `GetScript`, `SetScript`, ve `TestScript` tanımladığınız karşılık gelen DSC gerçekleştirmek için komut dosyası blokları içeren özelliğe işlem durumu.</span><span class="sxs-lookup"><span data-stu-id="a4d38-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4d38-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4d38-107">Syntax</span></span>

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

> [!NOTE]
> <span data-ttu-id="a4d38-108">`GetScript`, `TestScript`, Ve `SetScript` blokları, dize olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="a4d38-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="a4d38-109">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a4d38-109">Properties</span></span>

|<span data-ttu-id="a4d38-110">Özellik</span><span class="sxs-lookup"><span data-stu-id="a4d38-110">Property</span></span>|<span data-ttu-id="a4d38-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4d38-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="a4d38-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="a4d38-112">GetScript</span></span>|<span data-ttu-id="a4d38-113">Düğüm geçerli durumunu döndüren bir betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="a4d38-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="a4d38-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="a4d38-114">SetScript</span></span>|<span data-ttu-id="a4d38-115">DSC düğümü istenen durumda olmadığında uyumluluğu zorlamak için kullanan bir betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="a4d38-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="a4d38-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="a4d38-116">TestScript</span></span>|<span data-ttu-id="a4d38-117">Düğüm istenen durumda olup olmadığını belirten bir betik bloğu.</span><span class="sxs-lookup"><span data-stu-id="a4d38-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="a4d38-118">Kimlik bilgisi</span><span class="sxs-lookup"><span data-stu-id="a4d38-118">Credential</span></span>| <span data-ttu-id="a4d38-119">Kimlik bilgileri gerekiyorsa bu betiği çalıştırmak için kullanılacak kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4d38-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="a4d38-120">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a4d38-120">DependsOn</span></span>| <span data-ttu-id="a4d38-121">Bu kaynağı yapılandırılmadan önce başka bir kaynak yapılandırmasını çalıştırmanız gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4d38-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a4d38-122">Örneğin, kaynak yapılandırmasının Kimliğini çalıştırmak istediğiniz bir blok betik ilk ise **ResourceName** ve kendi türünün **ResourceType**, bu özelliği kullanmak için sözdizimi `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a4d38-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="a4d38-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="a4d38-123">GetScript</span></span>

<span data-ttu-id="a4d38-124">DSC çıktısı kullanmayan `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="a4d38-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="a4d38-125">[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet'ini çalıştırır `GetScript` düğümün geçerli durumu alınamadı.</span><span class="sxs-lookup"><span data-stu-id="a4d38-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="a4d38-126">Dönüş değeri, gelen gerekli değildir. `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="a4d38-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="a4d38-127">Dönüş değeri belirtirseniz, olması gereken bir `hashtable` içeren bir **sonucu** anahtar değeri olan bir `String`.</span><span class="sxs-lookup"><span data-stu-id="a4d38-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="a4d38-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="a4d38-128">TestScript</span></span>

<span data-ttu-id="a4d38-129">`TestScript` Belirlemek için DSC tarafından yürütülen `SetScript` çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4d38-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="a4d38-130">Varsa `TestScript` döndürür `$false`, DSC yürütür `SetScript` düğümü istenen duruma geri alma.</span><span class="sxs-lookup"><span data-stu-id="a4d38-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="a4d38-131">Döndürmesi gereken bir `boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="a4d38-131">It must return a `boolean` value.</span></span> <span data-ttu-id="a4d38-132">Sonucu `$true` düğümü uyumlu olduğunu gösterir ve `SetScript` çalıştırılmadı.</span><span class="sxs-lookup"><span data-stu-id="a4d38-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="a4d38-133">[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet'ini çalıştırır `TestScript` düğümleri uyumluluğu alınacak **betik** kaynakları.</span><span class="sxs-lookup"><span data-stu-id="a4d38-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="a4d38-134">Ancak, bu durumda, `SetScript` , ne olursa olsun çalıştırmaz `TestScript` block döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4d38-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="a4d38-135">Tüm çıktı, `TestScript` dönüş değeri bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4d38-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="a4d38-136">PowerShell anlamına unsuppressed çıkış olarak sıfır olmayan, yorumlar, `TestScript` döndüreceği `$true` bakılmaksızın, düğümün durumu.</span><span class="sxs-lookup"><span data-stu-id="a4d38-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="a4d38-137">Bu beklenmeyen sonuç, hatalı pozitif sonuç verir ve sorun giderme sırasında zorluk neden olur.</span><span class="sxs-lookup"><span data-stu-id="a4d38-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="a4d38-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="a4d38-138">SetScript</span></span>

<span data-ttu-id="a4d38-139">`SetScript` Belirttiğiniz istenen duruma uygulamak düğümü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a4d38-139">The `SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="a4d38-140">Bu DSC tarafından çağrılır `TestScript` betik bloğu döndürür `$false`.</span><span class="sxs-lookup"><span data-stu-id="a4d38-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="a4d38-141">`SetScript` Dönüş değeri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4d38-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="a4d38-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a4d38-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="a4d38-143">Örnek 1: Script kaynağı kullanarak örnek metin yazma</span><span class="sxs-lookup"><span data-stu-id="a4d38-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="a4d38-144">Bu örnekte varlığını test `C:\TempFolder\TestFile.txt` her düğümde.</span><span class="sxs-lookup"><span data-stu-id="a4d38-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="a4d38-145">Yoksa, onu kullanarak oluşturur `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="a4d38-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="a4d38-146">`GetScript` İçeriğini dosya ve dönüş değeri kullanılmaz döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4d38-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="a4d38-147">Örnek 2: Sürüm bilgileri kullanarak bir komut dosyası kaynak karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="a4d38-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="a4d38-148">Bu örnek alır *uyumlu* geliştirme bilgisayarında bir metin dosyasından sürüm bilgilerini ve depolar `$version` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a4d38-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="a4d38-149">DSC düğümü MOF dosyası oluşturulurken değiştirir `$using:version` her komut dosyası değişkenleri block değeriyle `$version` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a4d38-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="a4d38-150">Yürütme sırasında *uyumlu* sürümü bir metin dosyasındaki her bir düğümde depolanan ve karşılaştırma ve sonraki yürütmeleri üzerinde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="a4d38-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

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
}
```
