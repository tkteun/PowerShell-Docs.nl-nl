---
title: Voorbeelden van de Help op basis van een opmerking | Microsoft Docs
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
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083498"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="77064-102">Voorbeelden van de Help op basis van opmerkingen</span><span class="sxs-lookup"><span data-stu-id="77064-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="77064-103">In dit onderwerp vindt u een voorbeeld die laten zien hoe u Help-informatie op basis van een opmerking voor scripts en functies.</span><span class="sxs-lookup"><span data-stu-id="77064-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="77064-104">Voorbeeld 1: Help voor een functie op basis van een opmerking</span><span class="sxs-lookup"><span data-stu-id="77064-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="77064-105">Het volgende voorbeeld van de functie bevat hulp op basis van een opmerking.</span><span class="sxs-lookup"><span data-stu-id="77064-105">The following sample function includes comment-based Help.</span></span>

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

<span data-ttu-id="77064-106">De volgende uitvoer toont de resultaten van een Get-Help-opdracht de help voor de functie extensie toevoegen geeft.</span><span class="sxs-lookup"><span data-stu-id="77064-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

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

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="77064-107">Voorbeeld 2: Help voor een Script op basis van een opmerking</span><span class="sxs-lookup"><span data-stu-id="77064-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="77064-108">Het volgende voorbeeld van de functie bevat hulp op basis van een opmerking.</span><span class="sxs-lookup"><span data-stu-id="77064-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="77064-109">U ziet de lege regels tussen de afsluitende **#>** en de `Param` instructie.</span><span class="sxs-lookup"><span data-stu-id="77064-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="77064-110">In een script dat niet beschikt over een `Param` -instructie, er moet ten minste twee lege regels tussen de laatste opmerking in het Help-onderwerp en de functiedeclaratie van de eerste.</span><span class="sxs-lookup"><span data-stu-id="77064-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="77064-111">Get-Help Hiermee zonder deze lege regels koppelt u het Help-onderwerp met de functie, in plaats van het script.</span><span class="sxs-lookup"><span data-stu-id="77064-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

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

<span data-ttu-id="77064-112">De volgende opdracht wordt het Help-script.</span><span class="sxs-lookup"><span data-stu-id="77064-112">The following command gets the script Help.</span></span> <span data-ttu-id="77064-113">Omdat het script niet n moet een map die wordt vermeld in de omgevingsvariabele Path, de opdracht Get-Help, waarmee het script Help worden opgehaald in het scriptpad opgeven.</span><span class="sxs-lookup"><span data-stu-id="77064-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="77064-114">Voorbeeld 3: Beschrijvingen van de parameters in een instructie Param</span><span class="sxs-lookup"><span data-stu-id="77064-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="77064-115">In dit voorbeeld ziet u hoe u invoegen parameterdescriptions in de `Param` instructie van een functie of script.</span><span class="sxs-lookup"><span data-stu-id="77064-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="77064-116">Deze indeling is vooral nuttig zijn wanneer de parameterbeschrijvingen van de korte zijn.</span><span class="sxs-lookup"><span data-stu-id="77064-116">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="77064-117">De resultaten zijn hetzelfde als het resultaat bijvoorbeeld 1.</span><span class="sxs-lookup"><span data-stu-id="77064-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="77064-118">Get-Help interpreteert de beschrijvingen van de parameters alsof ze zijn voorzien van de `.Parameter` trefwoord.</span><span class="sxs-lookup"><span data-stu-id="77064-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="77064-119">Voorbeeld 4:  Omleiden naar een XML-bestand</span><span class="sxs-lookup"><span data-stu-id="77064-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="77064-120">U kunt de Help-onderwerpen op basis van XML voor functies en scripts schrijven.</span><span class="sxs-lookup"><span data-stu-id="77064-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="77064-121">Hoewel Help op basis van een opmerking eenvoudiger is te implementeren, is op basis van een XML-Help is vereist als u meer nauwkeurige controle over de Help-inhoud of wilt als u Help-onderwerpen zijn zetten in meerdere talen. Het volgende voorbeeld ziet de eerste paar regels van de Update-Month.ps1-script.</span><span class="sxs-lookup"><span data-stu-id="77064-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="77064-122">Het script gebruikt de `.ExternalHelp` trefwoord om op te geven van het pad naar een Help-onderwerp XML-indeling voor het script.</span><span class="sxs-lookup"><span data-stu-id="77064-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="77064-123">Het volgende voorbeeld ziet u het gebruik van de `.ExternalHelp` sleutelwoord in een functie.</span><span class="sxs-lookup"><span data-stu-id="77064-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="77064-124">Voorbeeld 5:  Omleiden naar een andere Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="77064-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="77064-125">De volgende code is een fragment uit het begin van de ingebouwde `Help` functie in Windows PowerShell, waarin een scherm van Help-tekst op een tijdstip.</span><span class="sxs-lookup"><span data-stu-id="77064-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="77064-126">Omdat het Help-onderwerp voor de cmdlet Get-Help wordt de Help-functie beschreven, wordt de Help-functie gebruikt de `.ForwardHelpTargetName` en `.ForwardHelpCategory` trefwoorden voor de gebruiker omgeleid naar de Get-Help cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="77064-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="77064-127">De volgende opdracht maakt gebruik van deze functie.</span><span class="sxs-lookup"><span data-stu-id="77064-127">The following command uses this feature.</span></span> <span data-ttu-id="77064-128">Wanneer een gebruiker een opdracht Get-Help voor de Help-functie, wordt het Help-onderwerp voor de cmdlet Get-Help door Get-Help weergegeven.</span><span class="sxs-lookup"><span data-stu-id="77064-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

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