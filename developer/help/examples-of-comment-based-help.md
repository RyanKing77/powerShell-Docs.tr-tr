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
# <a name="examples-of-comment-based-help"></a>Yorum Tabanlı Yardım Örnekleri

Bu konuda, açıklama tabanlı Yardım betikleri ve İşlevler için nasıl kullanılacağını gösteren bir örnek içerir.

## <a name="example-1-comment-based-help-for-a-function"></a>Örnek 1: Bir işlev için açıklama tabanlı Yardım

 Aşağıdaki örnek işlev açıklama tabanlı Yardım içerir.

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

Aşağıdaki çıktı, Add-uzantı işlevi için Yardım görüntüleyen bir Get-Help komutunu sonuçları gösterilmektedir.

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

## <a name="example-2-comment-based-help-for-a-script"></a>Örnek 2: Bir komut dosyası için açıklama tabanlı Yardım

Aşağıdaki örnek işlev açıklama tabanlı Yardım içerir.

Boş satırlar kapatma arasındaki fark **#>** ve `Param` deyimi. Sahip olmayan bir betikte bir `Param` deyimi, Yardım konusundaki son açıklama ve ilk işlev bildirimi arasında en az iki boş satırlar olmalıdır. Bu boş satırlar, Get-Help komut dosyası yerine işlevi Yardım konusuna ilişkilendirir.

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

Aşağıdaki komut, komut dosyasını Yardım alır. Betik n olmadığı için yol ortam değişkeninde Yardım komut dosyasını alır Get-Help komutunu listelenen bir dizin betik yolu belirtmeniz gerekir.

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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a>Örnek 3: Param deyimi içinde parametre açıklamaları

Bu örnek içinde parameterdescriptions nasıl ekleneceğini gösterir `Param` bir işlev veya komut dosyası ifadesi. Bu biçim parametre açıklamaları kısa en yararlı olur.

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

Sonuçları örneğin 1 sonuç aynıdır. Get-Help yorumlar parametre açıklamaları olabilmek gibi sorgulamanıza `.Parameter` anahtar sözcüğü.

## <a name="example-4--redirecting-to-an-xml-file"></a>Örnek 4:  Bir XML dosyasına yeniden yönlendirme

XML-tabanlı Yardım konuları için işlev ve betik yazabilirsiniz. Açıklama tabanlı Yardım uygulamak daha kolay olsa da, XML tabanlı Yardım Yardım içeriğini veya birden fazla dilde çevireceğiniz Yardım konuları üzerinde daha kesin denetim istiyorsanız gereklidir. Aşağıdaki örnek, güncelleştirme Month.ps1 betiğin ilk birkaç satırı gösterir. Betik kullanır `.ExternalHelp` anahtar sözcüğünü XML tabanlı bir Yardım konusu betik için yolu belirtin.

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

Aşağıdaki örnek kullanımını gösterir `.ExternalHelp` anahtar sözcüğü bir işlev.

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a>Örnek 5:  Farklı bir Yardım konusu için'yeniden yönlendirme

Aşağıdaki kod bir alıntı yerleşik başından itibaren olan `Help` her seferinde Yardım metni, bir ekran görüntüler Windows PowerShell'de işlevi. Yardım işlevi kullanır, Get-Help cmdlet için Yardım konusuna Yardım işlevi açıklar çünkü `.ForwardHelpTargetName` ve `.ForwardHelpCategory` kullanıcı için Get-Help cmdlet Yardım konusunun yönlendirmek için anahtar sözcükler.

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

Bu özellik aşağıdaki komutu kullanır. Bir kullanıcı bir Get-Help komut için Yardım işlevi yazdığında, Get-Help Get-Help cmdlet için Yardım konusunu görüntüler.

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