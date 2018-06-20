---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC yapılandırmaları için yardım sayfasını yazma
ms.openlocfilehash: 316fd69ab1eae66ebe141b2575a05b502fc261ea
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222672"
---
# <a name="writing-help-for-dsc-configurations"></a>DSC yapılandırmaları için yardım sayfasını yazma

>İçin geçerlidir: Windows Windows PowerShell 5.0

DSC yapılandırmalarında açıklama tabanlı Yardım kullanabilirsiniz. Kullanıcıların, Yardım ile yapılandırma işlevini çağırarak erişebileceği `-?`, veya kullanarak [Get-Help](https://technet.microsoft.com/library/hh849696.aspx) cmdlet'i. PowerShell açıklama tabanlı Yardım hakkında daha fazla bilgi için bkz: [about_Comment_Based_Help](https://technet.microsoft.com/library/hh847834.aspx).

Aşağıdaki örnek bir yapılandırma ve onun için açıklama tabanlı Yardım içeren bir komut dosyası gösterilmektedir:

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

.PARAMETER FilePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$ComputerName,[string]$FilePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## <a name="viewing-configuration-help"></a>Yapılandırma Yardımı görüntüleme

Bir yapılandırması için Yardım görüntülemek için kullanın **Get-Help** işlevi veya türü adını cmdlet'iyle işlevin adını ve ardından `-?`. Önceki işlevi için geçirildiğinde çıkışı aşağıdadır **Get-Help**:

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName]
    <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## <a name="see-also"></a>Ayrıca bkz:
* [DSC yapılandırmaları](configurations.md)