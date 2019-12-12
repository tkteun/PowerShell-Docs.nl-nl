---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Schrijfhulp voor DSC-configuraties
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942074"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="7ec59-103">Schrijfhulp voor DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="7ec59-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="7ec59-104">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="7ec59-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7ec59-105">U kunt op opmerkingen gebaseerde hulp gebruiken in DSC-configuraties.</span><span class="sxs-lookup"><span data-stu-id="7ec59-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="7ec59-106">Gebruikers kunnen toegang krijgen tot de Help door de **configuratie** aan te roepen met `-?`of door de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7ec59-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="7ec59-107">Plaats de Help op basis van opmerkingen direct boven het tref woord `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="7ec59-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="7ec59-108">U kunt de Help van de para meter in-line plaatsen met uw commentaar blok, direct boven de parameter declaratie of beide zoals in het onderstaande voor beeld.</span><span class="sxs-lookup"><span data-stu-id="7ec59-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="7ec59-109">Zie [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)voor meer informatie over Help op basis van een opmerking.</span><span class="sxs-lookup"><span data-stu-id="7ec59-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="7ec59-110">Ontwikkel omgevingen van Power shell, zoals VSCode en ISE, hebben ook fragmenten waarmee u automatisch opmerkingen blok sjablonen kunt invoegen.</span><span class="sxs-lookup"><span data-stu-id="7ec59-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="7ec59-111">In het volgende voor beeld ziet u een script met daarin een Help-informatie over de configuratie en opmerking.</span><span class="sxs-lookup"><span data-stu-id="7ec59-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="7ec59-112">In dit voor beeld wordt een configuratie met para meters weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7ec59-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="7ec59-113">Zie [para meters toevoegen aan uw configuraties](add-parameters-to-a-configuration.md)voor meer informatie over het gebruik van para meters in uw configuraties.</span><span class="sxs-lookup"><span data-stu-id="7ec59-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

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

## <a name="viewing-configuration-help"></a><span data-ttu-id="7ec59-114">Help bij configuratie weer geven</span><span class="sxs-lookup"><span data-stu-id="7ec59-114">Viewing configuration help</span></span>

<span data-ttu-id="7ec59-115">Als u de Help voor een configuratie wilt weer geven, gebruikt u de cmdlet `Get-Help` met de naam van de functie of typt u de naam van de functie, gevolgd door `-?`.</span><span class="sxs-lookup"><span data-stu-id="7ec59-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="7ec59-116">Hier volgt de uitvoer van de vorige configuratie die is door gegeven aan `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="7ec59-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

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
> <span data-ttu-id="7ec59-117">Syntaxis velden en parameter kenmerken worden automatisch voor u gegenereerd door Power shell.</span><span class="sxs-lookup"><span data-stu-id="7ec59-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ec59-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7ec59-118">See Also</span></span>

- [<span data-ttu-id="7ec59-119">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="7ec59-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="7ec59-120">Een configuratie schrijven, compileren en Toep assen</span><span class="sxs-lookup"><span data-stu-id="7ec59-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="7ec59-121">Para meters toevoegen aan een configuratie</span><span class="sxs-lookup"><span data-stu-id="7ec59-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
