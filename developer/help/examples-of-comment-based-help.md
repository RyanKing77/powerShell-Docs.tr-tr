---
title: Açıklama tabanlı Yardım örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: 30e98bfcf06b1720005a73ee8294aeba7e1ae066
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083510"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="64750-102">Yorum Tabanlı Yardım Örnekleri</span><span class="sxs-lookup"><span data-stu-id="64750-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="64750-103">Bu konuda, açıklama tabanlı Yardım betikleri ve İşlevler için nasıl kullanılacağını gösteren bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="64750-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="64750-104">Örnek 1: Bir işlev için açıklama tabanlı Yardım</span><span class="sxs-lookup"><span data-stu-id="64750-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="64750-105">Aşağıdaki örnek işlev açıklama tabanlı Yardım içerir.</span><span class="sxs-lookup"><span data-stu-id="64750-105">The following sample function includes comment-based Help.</span></span>

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="64750-106">Aşağıdaki çıktı, Add-uzantı işlevi için Yardım görüntüleyen bir Get-Help komutunu sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="64750-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="64750-107">Örnek 2: Bir komut dosyası için açıklama tabanlı Yardım</span><span class="sxs-lookup"><span data-stu-id="64750-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="64750-108">Aşağıdaki örnek işlev açıklama tabanlı Yardım içerir.</span><span class="sxs-lookup"><span data-stu-id="64750-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="64750-109">Boş satırlar kapatma arasındaki fark **#>** ve `Param` deyimi.</span><span class="sxs-lookup"><span data-stu-id="64750-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="64750-110">Sahip olmayan bir betikte bir `Param` deyimi, Yardım konusundaki son açıklama ve ilk işlev bildirimi arasında en az iki boş satırlar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64750-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="64750-111">Bu boş satırlar, Get-Help komut dosyası yerine işlevi Yardım konusuna ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="64750-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="64750-112">Aşağıdaki komut, komut dosyasını Yardım alır.</span><span class="sxs-lookup"><span data-stu-id="64750-112">The following command gets the script Help.</span></span> <span data-ttu-id="64750-113">Betik n olmadığı için yol ortam değişkeninde Yardım komut dosyasını alır Get-Help komutunu listelenen bir dizin betik yolu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="64750-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="64750-114">Örnek 3: Param deyimi içinde parametre açıklamaları</span><span class="sxs-lookup"><span data-stu-id="64750-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="64750-115">Bu örnek içinde parameterdescriptions nasıl ekleneceğini gösterir `Param` bir işlev veya komut dosyası ifadesi.</span><span class="sxs-lookup"><span data-stu-id="64750-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="64750-116">Bu biçim parametre açıklamaları kısa en yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="64750-116">This format is most useful when the parameter descriptions are brief.</span></span>

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

<span data-ttu-id="64750-117">Sonuçları örneğin 1 sonuç aynıdır.</span><span class="sxs-lookup"><span data-stu-id="64750-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="64750-118">Get-Help yorumlar parametre açıklamaları olabilmek gibi sorgulamanıza `.Parameter` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="64750-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="64750-119">Örnek 4:  Bir XML dosyasına yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="64750-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="64750-120">XML-tabanlı Yardım konuları için işlev ve betik yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64750-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="64750-121">Açıklama tabanlı Yardım uygulamak daha kolay olsa da, XML tabanlı Yardım Yardım içeriğini veya birden fazla dilde çevireceğiniz Yardım konuları üzerinde daha kesin denetim istiyorsanız gereklidir. Aşağıdaki örnek, güncelleştirme Month.ps1 betiğin ilk birkaç satırı gösterir.</span><span class="sxs-lookup"><span data-stu-id="64750-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="64750-122">Betik kullanır `.ExternalHelp` anahtar sözcüğünü XML tabanlı bir Yardım konusu betik için yolu belirtin.</span><span class="sxs-lookup"><span data-stu-id="64750-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="64750-123">Aşağıdaki örnek kullanımını gösterir `.ExternalHelp` anahtar sözcüğü bir işlev.</span><span class="sxs-lookup"><span data-stu-id="64750-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="64750-124">Örnek 5:  Farklı bir Yardım konusu için'yeniden yönlendirme</span><span class="sxs-lookup"><span data-stu-id="64750-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="64750-125">Aşağıdaki kod bir alıntı yerleşik başından itibaren olan `Help` her seferinde Yardım metni, bir ekran görüntüler Windows PowerShell'de işlevi.</span><span class="sxs-lookup"><span data-stu-id="64750-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="64750-126">Yardım işlevi kullanır, Get-Help cmdlet için Yardım konusuna Yardım işlevi açıklar çünkü `.ForwardHelpTargetName` ve `.ForwardHelpCategory` kullanıcı için Get-Help cmdlet Yardım konusunun yönlendirmek için anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="64750-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

<span data-ttu-id="64750-127">Bu özellik aşağıdaki komutu kullanır.</span><span class="sxs-lookup"><span data-stu-id="64750-127">The following command uses this feature.</span></span> <span data-ttu-id="64750-128">Bir kullanıcı bir Get-Help komut için Yardım işlevi yazdığında, Get-Help Get-Help cmdlet için Yardım konusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="64750-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```