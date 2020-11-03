---
description: Hierin wordt beschreven hoe u Help-onderwerpen op basis van opmerkingen schrijft voor-functies en-scripts.
keywords: powershell,cmdlet
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: cb7ac6e7b4ec3afb95c9864665490633fdad6c5c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252711"
---
# <a name="about-comment-based-help"></a>Informatie over op opmerkingen gebaseerde Help

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u Help-onderwerpen op basis van opmerkingen schrijft voor-functies en-scripts.

## <a name="long-description"></a>Lange beschrijving

U kunt Help-onderwerpen op basis van opmerkingen schrijven voor functies en scripts door speciale tref woorden voor opmerkingen te gebruiken.

Met de cmdlet [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) wordt Help op basis van opmerkingen weer gegeven in dezelfde indeling waarin de Help-onderwerpen over cmdlets worden weer gegeven die zijn gegenereerd op basis van XML-bestanden. Gebruikers kunnen alle para meters van `Get-Help` , zoals **gedetailleerde** , **volledige** , **voor beelden** en **online** , gebruiken om de inhoud van op opmerkingen gebaseerde Help weer te geven.

U kunt ook op XML gebaseerde Help-bestanden voor functies en scripts schrijven. `Get-Help`Gebruik het sleutel woord om de cmdlet in te scha kelen om het op XML gebaseerde Help-bestand voor een functie of script te vinden `.ExternalHelp` . Zonder dit sleutel woord `Get-Help` kunnen geen op XML gebaseerde Help-onderwerpen voor functies of scripts worden gevonden.

In dit onderwerp wordt uitgelegd hoe u Help-onderwerpen voor functies en scripts schrijft. Zie [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)voor informatie over het weer geven van Help-onderwerpen voor functies en scripts.

De cmdlets [Update Help](xref:Microsoft.PowerShell.Core.Update-Help) en [Help voor opslaan](xref:Microsoft.PowerShell.Core.Save-Help) werken alleen op XML-bestanden. Bij te werken Help biedt geen ondersteuning voor Help-onderwerpen op basis van opmerkingen.

## <a name="syntax-for-comment-based-help"></a>Syntaxis voor op opmerkingen gebaseerde Help

De syntaxis voor op opmerkingen gebaseerde Help is als volgt:

```
# .<help keyword>
# <help content>
```

of

```
<#
.<help keyword>
<help content>
#>
```

Help op basis van opmerkingen wordt geschreven als een reeks opmerkingen. U kunt een opmerking toevoegen `#` vóór elke regel met opmerkingen, maar u kunt ook de `<#` symbolen en gebruiken `#>` om een opmerkingen blok te maken. Alle regels in het opmerkingen blok worden geïnterpreteerd als opmerkingen.

Alle regels in een Help-onderwerp op basis van opmerkingen moeten aaneengesloten zijn. Als een Help-onderwerp op basis van opmerkingen een opmerking volgt die geen deel uitmaakt van het Help-onderwerp, moet er ten minste één lege regel tussen de laatste niet-Help opmerkings regel en het begin van de op opmerkingen gebaseerde Help zijn.

Met tref woorden worden elke sectie van op opmerkingen gebaseerde Help gedefinieerd. Elk op opmerkingen gebaseerd Help-tref woord wordt voorafgegaan door een punt `.` . De tref woorden kunnen in elke wille keurige volg orde worden weer gegeven. De namen van tref woorden zijn niet hoofdletter gevoelig.

Het `.Description` sleutel woord gaat bijvoorbeeld vooraf op een beschrijving van een functie of script.

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

Het commentaar blok moet ten minste één sleutel woord bevatten. Sommige tref woorden, zoals `.EXAMPLE` , kunnen vaak in hetzelfde commentaar blok worden weer gegeven. De Help-inhoud voor elk tref woord begint op de regel na het sleutel woord en kan meerdere regels omvatten.

## <a name="syntax-for-comment-based-help-in-functions"></a>Syntaxis voor op opmerkingen gebaseerde Help in functies

Op opmerkingen gebaseerde Help voor een functie kan op een van de volgende drie locaties worden weer gegeven:

- Aan het begin van de hoofd tekst van de functie.
- Aan het einde van de hoofd tekst van de functie.
- Vóór het `function` sleutel woord. Er mag niet meer dan één lege regel zijn tussen de laatste regel van de functie Help en het `function` sleutel woord.

Bijvoorbeeld:

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

of

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

of

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a>Syntaxis voor op opmerkingen gebaseerde Help in scripts

Op opmerkingen gebaseerde Help voor een script kan worden weer gegeven op een van de volgende twee locaties in het script.

- Aan het begin van het script bestand. De Help van het script kan alleen worden voorafgegaan door opmerkingen en lege regels in het script.

  Als het eerste item in de hoofd tekst van het script (na de Help) een functie declaratie is, moeten er ten minste twee lege regels tussen het einde van de script-Help en de functie declaratie zijn. Anders wordt de Help geïnterpreteerd als hulp voor de functie, en niet bij het script.

- Aan het einde van het script bestand. Als het script is ondertekend, plaatst u op opmerkingen gebaseerde Help aan het begin van het script bestand. Het einde van het script wordt ingen Omen door het handtekening blok.

Bijvoorbeeld:

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

of

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a>Syntaxis voor op opmerkingen gebaseerde Help in script modules

In een script module `.psm1` gebruikt op opmerkingen gebaseerde Help de syntaxis voor-functies, niet de syntaxis voor scripts. U kunt de script syntaxis niet gebruiken om hulp te bieden voor alle functies die in een script module zijn gedefinieerd.

Als u bijvoorbeeld het `.ExternalHelp` tref woord gebruikt om de op XML gebaseerde Help-bestanden voor de functies in een script module te identificeren, moet u een `.ExternalHelp` Opmerking toevoegen aan elke functie.

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a>Help-tref woorden op basis van opmerkingen

Hieronder vindt u geldige Help-tref woorden op basis van opmerkingen. Ze worden weer gegeven in de volg orde waarin ze doorgaans worden weer gegeven in een Help-onderwerp samen met het beoogde gebruik. Deze tref woorden kunnen in een wille keurige volg orde in de op opmerkingen gebaseerde Help worden weer gegeven en zijn niet hoofdletter gevoelig.

### <a name="synopsis"></a>. SAMEN VATTING

Een korte beschrijving van de functie of het script. Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.

### <a name="description"></a>. BESCHRIJVINGEN

Een gedetailleerde beschrijving van de functie of het script. Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.

### <a name="parameter"></a>. BEPAALDE

De beschrijving van een para meter. Voeg een `.PARAMETER` tref woord toe voor elke para meter in de syntaxis van de functie of het script.

Typ de parameter naam op dezelfde regel als het `.PARAMETER` sleutel woord. Typ de beschrijving van de para meter op de regels die volgen op het `.PARAMETER` sleutel woord. Windows Power shell interpreteert alle tekst tussen de `.PARAMETER` regel en het volgende tref woord of het einde van het commentaar blok als onderdeel van de parameter beschrijving.
De beschrijving kan alinea-einden bevatten.

```
.PARAMETER  <Parameter-Name>
```

De parameter trefwoorden kunnen in een wille keurige volg orde in het blok met opmerkingen worden weer gegeven, maar de functie-of script syntaxis bepaalt de volg orde waarin de para meters (en de bijbehorende beschrijvingen) in het Help-onderwerp worden weer gegeven. Als u de volg orde wilt wijzigen, wijzigt u de syntaxis.

U kunt ook een parameter beschrijving opgeven door een opmerking in de functie-of script syntaxis direct vóór de naam van de parameter variabele in te stellen. Om dit te laten werken, moet u ook een opmerkingen blok met ten minste één sleutel woord hebben.

Als u zowel een syntaxis Opmerking Als een `.PARAMETER` tref woord gebruikt, wordt de beschrijving die is gekoppeld aan het `.PARAMETER` tref woord gebruikt en wordt de syntaxis opmerking genegeerd.

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a>. Hierbij

Een voor beeld van een opdracht die gebruikmaakt van de functie of het script, eventueel gevolgd door voorbeeld uitvoer en een beschrijving. Herhaal dit tref woord voor elk voor beeld.

### <a name="inputs"></a>. INVOER

De .NET-typen objecten die kunnen worden gesluisd met de functie of het script. U kunt ook een beschrijving van de invoer objecten toevoegen.

### <a name="outputs"></a>. UITVOER

Het .NET-type van de objecten die door de cmdlet worden geretourneerd. U kunt ook een beschrijving van de geretourneerde objecten toevoegen.

### <a name="notes"></a>. NOTEN

Aanvullende informatie over de functie of het script.

### <a name="link"></a>. GEKOPPELD

De naam van een verwant onderwerp. De waarde wordt weer gegeven op de regel onder de ". Het sleutel woord LINK en moet worden voorafgegaan door een opmerkings symbool `#` of opgenomen in het opmerkingen blok.

Herhaal het `.LINK` tref woord voor elk verwant onderwerp.

Deze inhoud wordt weer gegeven in de sectie verwante koppelingen van het Help-onderwerp.

De `.Link` inhoud van het sleutel woord kan ook een URI (Uniform Resource Identifier) bevatten naar een online versie van hetzelfde Help-onderwerp. De online versie wordt geopend wanneer u de **online** -para meter van gebruikt `Get-Help` . De URI moet beginnen met http of https.

### <a name="component"></a>. ONDERDEEL

De naam van de technologie of functie die de functie of het script gebruikt of waaraan deze is gerelateerd. De **onderdeel** parameter van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .

### <a name="role"></a>. ROLVAK

De naam van de gebruikersrol voor het Help-onderwerp. De para meter **Role** van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .

### <a name="functionality"></a>. VOORZIENING

De tref woorden die het beoogde gebruik van de functie beschrijven. De **functie** parameter van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .

### <a name="forwardhelptargetname"></a>. FORWARDHELPTARGETNAME

Omleiding naar het Help-onderwerp voor de opgegeven opdracht. U kunt gebruikers omleiden naar een Help-onderwerp, inclusief Help-onderwerpen voor een functie, script, cmdlet of provider.

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a>. FORWARDHELPCATEGORY

Hiermee geeft u de Help-categorie van het item in op `.ForwardHelpTargetName` . Geldige waarden zijn,,,,,,,,,, `Alias` `Cmdlet` `HelpFile` `Function` `Provider` `General` `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` of `All` . Gebruik dit tref woord om conflicten te voor komen wanneer er opdrachten met dezelfde naam zijn.

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a>. REMOTEHELPRUNSPACE

Hiermee geeft u een sessie die het Help-onderwerp bevat. Voer een variabele in die een **PSSession** -object bevat. Dit sleutel woord wordt gebruikt door de cmdlet [export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) om de Help-onderwerpen voor de geëxporteerde opdrachten te vinden.

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a>. EXTERNALHELP

Hiermee geeft u een XML-Help-bestand voor het script of de functie op.

```powershell
# .EXTERNALHELP <XML Help File>
```

Het `.ExternalHelp` sleutel woord is vereist wanneer een functie of script wordt gedocumenteerd in XML-bestanden. Zonder dit tref woord `Get-Help` kan het op XML gebaseerde Help-bestand niet vinden voor de functie of het script.

Het `.ExternalHelp` tref woord heeft voor rang op andere op opmerkingen gebaseerde Help-tref woorden. Als `.ExternalHelp` is aanwezig, wordt `Get-Help` Help op basis van opmerkingen niet weer gegeven, zelfs niet als er geen Help-onderwerp is gevonden dat overeenkomt met de waarde van het `.ExternalHelp` sleutel woord.

Als de functie wordt geëxporteerd door een module, stelt u de waarde van het `.ExternalHelp` sleutel woord in op een bestands naam zonder een pad. `Get-Help` zoekt naar de opgegeven bestands naam in een taalspecifieke submap van de module directory. Er zijn geen vereisten voor de naam van het op XML gebaseerde Help-bestand voor een functie, maar een best practice is het gebruik van de volgende indeling:

```
<ScriptModule.psm1>-help.xml
```

Als de functie niet is opgenomen in een module, neemt u een pad op naar het op XML gebaseerde Help-bestand. Als de waarde een pad bevat en het pad beschikt over taalspecifieke submappen voor de gebruikers interface, `Get-Help` doorzoekt de submappen recursief voor een XML-bestand met de naam van het script of de functie in overeenstemming met de taal vereisten die zijn ingesteld voor Windows, net zoals in een module directory.

Zie [instructies voor het schrijven van cmdlets](https://go.microsoft.com/fwlink/?LinkID=123415) in de MSDN-bibliotheek voor meer informatie over de Help-indeling van de cmdlet-Help.

## <a name="autogenerated-content"></a>Automatisch gegenereerde inhoud

De naam, de syntaxis, de parameter lijst, de parameter kenmerk tabel, de algemene para meters en opmerkingen worden automatisch door de `Get-Help` cmdlet gegenereerd.

### <a name="name"></a>Naam

De sectie **naam** van het Help-onderwerp van een functie wordt opgehaald uit de functie naam in de syntaxis van de functie. De **naam** van een script Help-onderwerp wordt opgehaald uit de script bestandsnaam. Als u de naam of het hoofdletter gebruik wilt wijzigen, wijzigt u de syntaxis van de functie of de script bestands naam.

### <a name="syntax"></a>Syntax

De sectie **syntaxis** van het Help-onderwerp wordt gegenereerd met de syntaxis van de functie of het script. Als u details wilt toevoegen aan de syntaxis van het Help-onderwerp, zoals het .NET-type van een para meter, voegt u het detail toe aan de syntaxis. Als u geen parameter type opgeeft, wordt het **object** type ingevoegd als de standaard waarde.

### <a name="parameter-list"></a>Parameter lijst

De lijst met para meters in het Help-onderwerp wordt gegenereerd op basis van de functie-of script syntaxis en uit de beschrijvingen die u toevoegt met behulp van het `.Parameter` sleutel woord. De functie parameters worden weer gegeven in de sectie **para meters** van het Help-onderwerp in dezelfde volg orde als waarin ze worden weer gegeven in de syntaxis van de functie of het script. De spelling en het hoofdletter gebruik van parameter namen worden ook overgenomen uit de syntaxis. Dit is niet van invloed op de parameter naam die is opgegeven door het `.Parameter` sleutel woord.

### <a name="common-parameters"></a>Algemene para meters

De **algemene para meters** worden toegevoegd aan de lijst syntaxis en para meters van het Help-onderwerp, zelfs als ze geen effect hebben. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over de algemene para meters.

### <a name="parameter-attribute-table"></a>Parameter kenmerk tabel

`Get-Help` Hiermee wordt de tabel met parameter kenmerken gegenereerd die wordt weer gegeven wanneer u de para meter **Full** of **para meter** van gebruikt `Get-Help` . De waarde van de kenmerken **vereist** , **positie** en **standaard** waarde wordt opgehaald uit de syntaxis van de functie of het script.

Standaard waarden en een waarde voor **joker tekens accepteren** worden niet weer gegeven in de parameter kenmerk tabel, zelfs niet wanneer ze zijn gedefinieerd in de functie of het script. Geef deze informatie op in de parameter beschrijving om gebruikers te helpen.

### <a name="remarks"></a>Opmerkingen

De sectie **opmerkingen** van het Help-onderwerp wordt automatisch gegenereerd op basis van de functie of script naam. U kunt de inhoud niet wijzigen of beïnvloeden.

## <a name="examples"></a>Voorbeelden

### <a name="comment-based-help-for-a-function"></a>Op opmerkingen gebaseerde Help voor een functie

De volgende voorbeeld functie bevat Help op basis van opmerkingen:

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

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

De resultaten zijn als volgt:

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

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

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a>Parameter beschrijvingen in functie syntaxis

Dit voor beeld is hetzelfde als het vorige, behalve dat de parameter beschrijvingen worden ingevoegd in de syntaxis van de functie. Deze indeling is het handigst wanneer de beschrijvingen korter zijn.

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a>Help op basis van opmerkingen voor een script

Het volgende voorbeeld script bevat Help op basis van opmerkingen. Let op de lege regels tussen de afsluitende `#>` en de `Param` instructie. In een script zonder `Param` instructie moeten er ten minste twee lege regels tussen de laatste opmerking in het Help-onderwerp en de eerste functie declaratie zijn. Zonder deze lege regels `Get-Help` koppelt het Help-onderwerp aan de functie en niet aan het script.

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

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

Met de volgende opdracht wordt de Help van het script opgehaald. Omdat het script zich niet in een map bevindt die wordt weer gegeven in de `$env:Path` omgevings variabele, `Get-Help` moet de opdracht die het script ophaalt het pad naar het script opgeven.

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

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

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a>Omleiden naar een XML-bestand

U kunt op XML gebaseerde Help-onderwerpen voor functies en scripts schrijven. Hoewel Help op basis van opmerkingen eenvoudiger kan worden geïmplementeerd, is Help op basis van XML vereist voor bijwerk bare Help en om Help-onderwerpen te bieden in meerdere talen.

In het volgende voor beeld worden de eerste regels van het Update-Month.ps1 script weer gegeven.
Het script maakt gebruik `.ExternalHelp` van het sleutel woord om het pad naar een op XML gebaseerd Help-onderwerp voor het script op te geven.

Houd er rekening mee dat de waarde van het `.ExternalHelp` tref woord op dezelfde regel als het tref woord wordt weer gegeven. Andere plaatsen zijn niet effectief.

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

In de volgende voor beelden worden drie geldige plaatsingen van het `.ExternalHelp` tref woord in een functie weer gegeven.

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a>Omleiden naar een ander Help-onderwerp

De volgende code is een fragment van het begin van de ingebouwde Help-functie in Power shell, waarmee een scherm met Help-tekst per keer wordt weer gegeven.
Omdat in het Help-onderwerp voor de `Get-Help` cmdlet de Help-functie wordt beschreven, gebruikt de Help-functie de `.ForwardHelpTargetName` tref woorden en wordt de `.ForwardHelpCategory` gebruiker omgeleid naar het Help-onderwerp van de `Get-Help` cmdlet.

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

De volgende opdracht maakt gebruik van deze functie:

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a>Zie ook

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Scripts](about_Scripts.md)

[Instructies voor het schrijven van cmdlets](https://go.microsoft.com/fwlink/?LinkID=123415)
