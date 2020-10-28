---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Schrijfhulp voor DSC-configuraties
description: U kunt op opmerkingen gebaseerde hulp gebruiken in DSC-configuraties. Gebruikers kunnen toegang krijgen tot de Help door de configuratie aan te roepen met `-?` para meter of door gebruik te maken van de Get-Help-cmdlet.
ms.openlocfilehash: 01c4f43253f4d4d8421ea3e0dfca797776acd426
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658639"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="d3091-105">Schrijfhulp voor DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="d3091-105">Writing help for DSC configurations</span></span>

> <span data-ttu-id="d3091-106">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="d3091-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d3091-107">U kunt op opmerkingen gebaseerde hulp gebruiken in DSC-configuraties.</span><span class="sxs-lookup"><span data-stu-id="d3091-107">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="d3091-108">Gebruikers kunnen toegang krijgen tot de Help door de **configuratie** aan te roepen met `-?` of door gebruik te maken van de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) .</span><span class="sxs-lookup"><span data-stu-id="d3091-108">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="d3091-109">Plaats de op opmerkingen gebaseerde Help direct boven het `Configuration` tref woord.</span><span class="sxs-lookup"><span data-stu-id="d3091-109">Place your Comment-based help directly above the `Configuration` keyword.</span></span> <span data-ttu-id="d3091-110">U kunt de Help van de para meter in-line plaatsen met uw commentaar blok, direct boven de parameter declaratie of beide zoals in het onderstaande voor beeld.</span><span class="sxs-lookup"><span data-stu-id="d3091-110">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="d3091-111">Zie [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)voor meer informatie over Help op basis van een opmerking.</span><span class="sxs-lookup"><span data-stu-id="d3091-111">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="d3091-112">Ontwikkel omgevingen van Power shell, zoals VS code en de ISE, bevatten ook fragmenten waarmee u automatisch opmerkingen blok sjablonen kunt invoegen.</span><span class="sxs-lookup"><span data-stu-id="d3091-112">PowerShell development environments, like VS Code and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="d3091-113">In het volgende voor beeld ziet u een script met daarin een Help-informatie over de configuratie en opmerking.</span><span class="sxs-lookup"><span data-stu-id="d3091-113">The following example shows a script that contains a configuration and comment-based help for it.</span></span>
<span data-ttu-id="d3091-114">In dit voor beeld wordt een configuratie met para meters weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d3091-114">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="d3091-115">Zie [para meters toevoegen aan uw configuraties](add-parameters-to-a-configuration.md)voor meer informatie over het gebruik van para meters in uw configuraties.</span><span class="sxs-lookup"><span data-stu-id="d3091-115">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each
configuration.

.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or
script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description
on the lines following the .PARAMETER keyword. Windows PowerShell interprets all text between the
.PARAMETER line and the next keyword or the end of the comment block as part of the parameter
description. The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script
syntax determines the order in which the parameters (and their descriptions) appear in help topic.
To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a
description. Repeat this keyword for each example. PowerShell automatically prefaces the first line
with a PowerShell prompt. Additional lines are treated as output and description. The example can
contain spaces, newlines and PowerShell code.

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

## <a name="viewing-configuration-help"></a><span data-ttu-id="d3091-116">Help bij configuratie weer geven</span><span class="sxs-lookup"><span data-stu-id="d3091-116">Viewing configuration help</span></span>

<span data-ttu-id="d3091-117">Als u de Help voor een configuratie wilt weer geven, gebruikt u de `Get-Help` cmdlet met de naam van de functie of typt u de naam van de functie gevolgd door `-?` .</span><span class="sxs-lookup"><span data-stu-id="d3091-117">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="d3091-118">Hier volgt de uitvoer van de vorige configuratie die is door gegeven aan `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="d3091-118">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```Output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>]
      [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>]
      [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function
        or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter
        description on the lines following the .PARAMETER keyword. Windows PowerShell interprets all
        text between the .PARAMETER line and the next keyword or the end of the comment block as
        part of the parameter description. The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or
        script syntax determines the order in which the parameters (and their descriptions) appear
        in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a
    description. Repeat this keyword for each example. PowerShell automatically prefaces the first
    line with a PowerShell prompt. Additional lines are treated as output and description. The
    example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the
    examples in help text.


    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.


REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="d3091-119">Syntaxis velden en parameter kenmerken worden automatisch voor u gegenereerd door Power shell.</span><span class="sxs-lookup"><span data-stu-id="d3091-119">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3091-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d3091-120">See Also</span></span>

- [<span data-ttu-id="d3091-121">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="d3091-121">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="d3091-122">Een configuratie schrijven, compileren en toepassen</span><span class="sxs-lookup"><span data-stu-id="d3091-122">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="d3091-123">Parameters toevoegen aan een configuratie</span><span class="sxs-lookup"><span data-stu-id="d3091-123">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
