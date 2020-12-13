---
ms.date: 09/12/2016
ms.topic: reference
title: Voorbeelden van de Help op basis van opmerkingen
description: Voorbeelden van de Help op basis van opmerkingen
ms.openlocfilehash: 35fe9103a261483c56af629f620dbd6b3c642e68
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667637"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="68d7e-103">Voorbeelden van de Help op basis van opmerkingen</span><span class="sxs-lookup"><span data-stu-id="68d7e-103">Examples of Comment-Based Help</span></span>

<span data-ttu-id="68d7e-104">Dit onderwerp bevat voor beelden van informatie over het gebruik van op opmerkingen gebaseerde hulp voor scripts en functies.</span><span class="sxs-lookup"><span data-stu-id="68d7e-104">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="68d7e-105">Voor beeld 1: Help-Comment-Based voor een functie</span><span class="sxs-lookup"><span data-stu-id="68d7e-105">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="68d7e-106">De volgende voorbeeld functie bevat Help op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="68d7e-106">The following sample function includes comment-based Help.</span></span>

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

<span data-ttu-id="68d7e-107">In de volgende uitvoer ziet u de resultaten van een `Get-Help` opdracht die de Help voor de `Add-Extension` functie weergeeft.</span><span class="sxs-lookup"><span data-stu-id="68d7e-107">The following output shows the results of a `Get-Help` command that displays the help for the `Add-Extension` function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```Output
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

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="68d7e-108">Voor beeld 2: Help-Comment-Based voor een script</span><span class="sxs-lookup"><span data-stu-id="68d7e-108">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="68d7e-109">De volgende voorbeeld functie bevat Help op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="68d7e-109">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="68d7e-110">Let op de lege regels tussen de afsluitende **#>** en de `Param` instructie.</span><span class="sxs-lookup"><span data-stu-id="68d7e-110">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="68d7e-111">In een script zonder `Param` instructie moeten er ten minste twee lege regels tussen de laatste opmerking in het Help-onderwerp en de eerste functie declaratie zijn.</span><span class="sxs-lookup"><span data-stu-id="68d7e-111">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="68d7e-112">Zonder deze lege regels wordt `Get-Help` het Help-onderwerp gekoppeld aan de functie, in plaats van het script.</span><span class="sxs-lookup"><span data-stu-id="68d7e-112">Without these blank lines, `Get-Help` associates the Help topic with the function, instead of the script.</span></span>

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

<span data-ttu-id="68d7e-113">Met de volgende opdracht wordt de Help van het script opgehaald.</span><span class="sxs-lookup"><span data-stu-id="68d7e-113">The following command gets the script Help.</span></span> <span data-ttu-id="68d7e-114">Omdat het script zich niet in een map bevindt die wordt vermeld in de omgevings variabele PATH, `Get-Help` moet de opdracht die het script ophaalt het pad naar het script opgeven.</span><span class="sxs-lookup"><span data-stu-id="68d7e-114">Because the script is not in a directory that is listed in the Path environment variable, the `Get-Help` command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```Output
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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="68d7e-115">Voor beeld 3: parameter beschrijvingen in een para meter-instructie</span><span class="sxs-lookup"><span data-stu-id="68d7e-115">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="68d7e-116">In dit voor beeld ziet u hoe u parameter beschrijvingen kunt invoegen in de `Param` instructie van een functie of script.</span><span class="sxs-lookup"><span data-stu-id="68d7e-116">This example shows how to insert parameter descriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="68d7e-117">Deze indeling is het handigst wanneer de parameter beschrijvingen kort zijn.</span><span class="sxs-lookup"><span data-stu-id="68d7e-117">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="68d7e-118">De resultaten zijn hetzelfde als de resultaten voor bijvoorbeeld 1.</span><span class="sxs-lookup"><span data-stu-id="68d7e-118">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="68d7e-119">`Get-Help` interpreteert de parameter beschrijvingen alsof ze vergezeld gaan van het `.Parameter` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="68d7e-119">`Get-Help` interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="68d7e-120">Voor beeld 4: omleiden naar een XML-bestand</span><span class="sxs-lookup"><span data-stu-id="68d7e-120">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="68d7e-121">U kunt op XML gebaseerde Help-onderwerpen voor functies en scripts schrijven.</span><span class="sxs-lookup"><span data-stu-id="68d7e-121">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="68d7e-122">Hoewel Help op basis van opmerkingen eenvoudiger kan worden geïmplementeerd, is Help op basis van XML vereist als u meer controle wilt over Help-inhoud of als u Help-onderwerpen vertaalt in meerdere talen. In het volgende voor beeld worden de eerste regels van het script weer gegeven `Update-Month.ps1` .</span><span class="sxs-lookup"><span data-stu-id="68d7e-122">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the `Update-Month.ps1` script.</span></span> <span data-ttu-id="68d7e-123">Het script maakt gebruik `.ExternalHelp` van het sleutel woord om het pad naar een op XML gebaseerd Help-onderwerp voor het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="68d7e-123">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="68d7e-124">In het volgende voor beeld ziet u het gebruik van het `.ExternalHelp` sleutel woord in een functie.</span><span class="sxs-lookup"><span data-stu-id="68d7e-124">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="68d7e-125">Voor beeld 5: omleiden naar een ander Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="68d7e-125">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="68d7e-126">De volgende code is een uittreksel van het begin van de ingebouwde `Help` functie in Power shell, waarmee een scherm met Help-tekst per keer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="68d7e-126">The following code is an excerpt from the beginning of the built-in `Help` function in PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="68d7e-127">Omdat in het Help-onderwerp voor de Get-Help-cmdlet de Help-functie wordt beschreven, gebruikt de Help-functie de `.ForwardHelpTargetName` sleutel woorden en wordt de `.ForwardHelpCategory` gebruiker omgeleid naar het Help-onderwerp van de Get-Help-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="68d7e-127">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="68d7e-128">De volgende opdracht maakt gebruik van deze functie.</span><span class="sxs-lookup"><span data-stu-id="68d7e-128">The following command uses this feature.</span></span> <span data-ttu-id="68d7e-129">Wanneer een gebruiker een `Get-Help` opdracht voor de `Help` functie typt, `Get-Help` wordt het Help-onderwerp voor de cmdlet weer gegeven `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="68d7e-129">When a user types a `Get-Help` command for the `Help` function, `Get-Help` displays the Help topic for the `Get-Help` cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```Output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```
