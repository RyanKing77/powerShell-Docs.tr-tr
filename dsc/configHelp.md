---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "DSC yapılandırması için Yardım yazma"
ms.openlocfilehash: c868fa0565baff833423db090a5d62824ab4cad8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="34a35-103">DSC yapılandırması için Yardım yazma</span><span class="sxs-lookup"><span data-stu-id="34a35-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="34a35-104">İçin geçerlidir: Windows Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="34a35-104">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="34a35-105">DSC yapılandırmalarında açıklama tabanlı Yardım kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34a35-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="34a35-106">Kullanıcıların, Yardım ile yapılandırma işlevini çağırarak erişebileceği `-?`, veya kullanarak [Get-Help](https://technet.microsoft.com/en-us/library/hh849696.aspx) cmdlet'i.</span><span class="sxs-lookup"><span data-stu-id="34a35-106">Users can access the help by calling the configuration function with `-?`, or by using the [Get-Help](https://technet.microsoft.com/en-us/library/hh849696.aspx) cmdlet.</span></span> <span data-ttu-id="34a35-107">PowerShell açıklama tabanlı Yardım hakkında daha fazla bilgi için bkz: [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/hh847834.aspx).</span><span class="sxs-lookup"><span data-stu-id="34a35-107">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/hh847834.aspx).</span></span>

<span data-ttu-id="34a35-108">Aşağıdaki örnek bir yapılandırma ve onun için açıklama tabanlı Yardım içeren bir komut dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="34a35-108">The following example shows a script that contains a configuration and comment-based help for it:</span></span>

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

## <a name="viewing-configuration-help"></a><span data-ttu-id="34a35-109">Yapılandırma Yardımı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="34a35-109">Viewing configuration help</span></span>

<span data-ttu-id="34a35-110">Bir yapılandırması için Yardım görüntülemek için kullanın **Get-Help** işlevi veya türü adını cmdlet'iyle işlevin adını ve ardından `-?`.</span><span class="sxs-lookup"><span data-stu-id="34a35-110">To view the help for a configuration, use the **Get-Help** cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="34a35-111">Önceki işlevi için geçirildiğinde çıkışı aşağıdadır **Get-Help**:</span><span class="sxs-lookup"><span data-stu-id="34a35-111">The following is the output of the previous function when passed to **Get-Help**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34a35-112">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="34a35-112">See Also</span></span>
* [<span data-ttu-id="34a35-113">DSC yapılandırmaları</span><span class="sxs-lookup"><span data-stu-id="34a35-113">DSC Configurations</span></span>](configurations.md)

