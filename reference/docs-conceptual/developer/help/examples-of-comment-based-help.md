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
# <a name="examples-of-comment-based-help"></a>Voorbeelden van de Help op basis van opmerkingen

Dit onderwerp bevat voor beelden van informatie over het gebruik van op opmerkingen gebaseerde hulp voor scripts en functies.

## <a name="example-1-comment-based-help-for-a-function"></a>Voor beeld 1: Help-Comment-Based voor een functie

 De volgende voorbeeld functie bevat Help op basis van opmerkingen.

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

In de volgende uitvoer ziet u de resultaten van een `Get-Help` opdracht die de Help voor de `Add-Extension` functie weergeeft.

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

## <a name="example-2-comment-based-help-for-a-script"></a>Voor beeld 2: Help-Comment-Based voor een script

De volgende voorbeeld functie bevat Help op basis van opmerkingen.

Let op de lege regels tussen de afsluitende **#>** en de `Param` instructie. In een script zonder `Param` instructie moeten er ten minste twee lege regels tussen de laatste opmerking in het Help-onderwerp en de eerste functie declaratie zijn. Zonder deze lege regels wordt `Get-Help` het Help-onderwerp gekoppeld aan de functie, in plaats van het script.

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

Met de volgende opdracht wordt de Help van het script opgehaald. Omdat het script zich niet in een map bevindt die wordt vermeld in de omgevings variabele PATH, `Get-Help` moet de opdracht die het script ophaalt het pad naar het script opgeven.

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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a>Voor beeld 3: parameter beschrijvingen in een para meter-instructie

In dit voor beeld ziet u hoe u parameter beschrijvingen kunt invoegen in de `Param` instructie van een functie of script. Deze indeling is het handigst wanneer de parameter beschrijvingen kort zijn.

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

De resultaten zijn hetzelfde als de resultaten voor bijvoorbeeld 1. `Get-Help` interpreteert de parameter beschrijvingen alsof ze vergezeld gaan van het `.Parameter` sleutel woord.

## <a name="example-4--redirecting-to-an-xml-file"></a>Voor beeld 4: omleiden naar een XML-bestand

U kunt op XML gebaseerde Help-onderwerpen voor functies en scripts schrijven. Hoewel Help op basis van opmerkingen eenvoudiger kan worden geïmplementeerd, is Help op basis van XML vereist als u meer controle wilt over Help-inhoud of als u Help-onderwerpen vertaalt in meerdere talen. In het volgende voor beeld worden de eerste regels van het script weer gegeven `Update-Month.ps1` . Het script maakt gebruik `.ExternalHelp` van het sleutel woord om het pad naar een op XML gebaseerd Help-onderwerp voor het script op te geven.

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

In het volgende voor beeld ziet u het gebruik van het `.ExternalHelp` sleutel woord in een functie.

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a>Voor beeld 5: omleiden naar een ander Help-onderwerp

De volgende code is een uittreksel van het begin van de ingebouwde `Help` functie in Power shell, waarmee een scherm met Help-tekst per keer wordt weer gegeven. Omdat in het Help-onderwerp voor de Get-Help-cmdlet de Help-functie wordt beschreven, gebruikt de Help-functie de `.ForwardHelpTargetName` sleutel woorden en wordt de `.ForwardHelpCategory` gebruiker omgeleid naar het Help-onderwerp van de Get-Help-cmdlet.

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

De volgende opdracht maakt gebruik van deze functie. Wanneer een gebruiker een `Get-Help` opdracht voor de `Help` functie typt, `Get-Help` wordt het Help-onderwerp voor de cmdlet weer gegeven `Get-Help` .

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
