---
ms.date: 12/12/2018
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC yapılandırmaları için yardım sayfasını yazma
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688857"
---
# <a name="writing-help-for-dsc-configurations"></a>DSC yapılandırmaları için yardım sayfasını yazma

>Şunun için geçerlidir: Windows PowerShell 5.0

DSC yapılandırmalarında, açıklama tabanlı Yardım kullanabilirsiniz. Kullanıcıların, Yardım çağırarak erişebileceği **yapılandırma** ile `-?`, kullanarak veya [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet'i. Açıklama tabanlı Yardım doğrudan yukarıdaki yerleştirin `Configuration` anahtar sözcüğü.
Parametre Yardım satır içi ile parametre bildirimi veya her ikisini de aşağıdaki örnekte olduğu gibi doğrudan yukarıda, açıklama bloğu yerleştirebilirsiniz.

PowerShell açıklama tabanlı Yardım hakkında daha fazla bilgi için bkz: [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

> [!NOTE]
> Açıklama bloğu şablonları otomatik olarak eklemenize izin vermek için kod parçacıkları VSCode ve ISE gibi PowerShell geliştirme ortamları de var.

Aşağıdaki örnek, bir yapılandırma ve bunun için açıklama tabanlı Yardım içeren bir komut dosyası gösterir. Bu örnekte, parametreler içeren bir yapılandırma gösterilmektedir. Parametreleri yapılandırmalarınızı içinde kullanma hakkında daha fazla bilgi için bkz [yapılandırmalarınızı parametreler ekleme](add-parameters-to-a-configuration.md).

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a>Yapılandırma Yardımı görüntüleme

Bir yapılandırma için Yardım görüntülemek için kullanın `Get-Help` cmdlet'i işlev veya tür adıyla işlevin adını ve ardından `-?`. Geçirilen önceki yapılandırmayı çıktısı aşağıdaki gibidir `Get-Help`.

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> Otomatik olarak sizin için söz dizimi alanları ve parametre öznitelikleri PowerShell tarafından oluşturulur.

## <a name="see-also"></a>Ayrıca bkz:

- [DSC yapılandırmaları](configurations.md)
- [Yazma, derlemek ve bir yapılandırmasını Uygula](write-compile-apply-configuration.md)
- [İçin yapılandırma parametreleri Ekle](add-parameters-to-a-configuration.md)
