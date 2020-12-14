---
title: Functions
description: Met Power shell-functies kunt u hulpprogram ma's maken die opnieuw kunnen worden gebruikt in scripts.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 18566263f29b97834d78cb5572fa73b58c3a26bb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96616009"
---
# <a name="chapter-9---functions"></a>Hoofd stuk 9-functies

Als u de Power shell-One-lines of-scripts schrijft en u deze vaak moet wijzigen voor verschillende scenario's, is het een goed idee om een goede kandidaat in te scha kelen die opnieuw kan worden gebruikt.

Als dat mogelijk is, is het handig om functies te schrijven, omdat deze meer hulp middelen zijn. Ik kan de functies in een script module plaatsen, die module in de toevoegen `$env:PSModulePath` en de functies aanroepen zonder dat ze fysiek moeten zoeken waar ze worden opgeslagen. Met behulp van de PowerShellGet-module kunt u deze modules eenvoudig delen in een NuGet-opslag plaats. PowerShellGet wordt geleverd met Power shell versie 5,0 en hoger. Het is beschikbaar als afzonderlijke down load voor Power shell versie 3,0 en hoger.

U hoeft zich niet meer te bemoeilijken. Bewaar het eenvoudig en gebruik de meest directe voorwaartse manier om een taak uit te voeren. Vermijd aliassen en positionele para meters in code die u opnieuw gebruikt. Maak uw code op voor de Lees baarheid. Geen voorlopig hardcoderen we-waarden; gebruik para meters en variabelen. Schrijf geen overbodige code, zelfs niet als dat niet zo is. Het voegt overbodige complexiteit toe. Het is belang rijk om de details van een Power shell-code te schrijven.

## <a name="naming"></a>Naamgeving

Gebruik bij het benoemen van uw functies in Power shell een [Pascal-Case][] naam met een goedgekeurd werk woord en een enkelvoudige zelfstandignaam. U kunt ook het voor voegsel van het zelfstandig naam woord aanraden. Bijvoorbeeld: `<ApprovedVerb>-<Prefix><SingularNoun>`.

In Power shell is er een specifieke lijst met goedgekeurde woorden die kunnen worden verkregen door uit te voeren `Get-Verb` .

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

In het vorige voor beeld heb ik de resultaten gesorteerd op de kolom **term** . In de kolom **groep** vindt u een idee van de manier waarop deze woorden worden gebruikt. Het is belang rijk dat u een goedgekeurde werk woord in Power shell kiest wanneer er functies aan een module worden toegevoegd. De module genereert een waarschuwings bericht bij de laad tijd als u een niet-goedgekeurde term kiest. Dit waarschuwings bericht zorgt ervoor dat uw functies worden weer gegeven als unprofessional. Niet-goedgekeurde werk woorden beperken ook de vind baarheid van uw functies.

## <a name="a-simple-function"></a>Een eenvoudige functie

Een functie in Power shell is gedeclareerd met het gereserveerde woord function gevolgd door de functie naam en vervolgens een accolade openen en sluiten. De code die de functie uitvoert, bevindt zich in deze accolades.

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

De functie die wordt weer gegeven, is een eenvoudig voor beeld van het retour neren van de versie van Power shell.

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Er is een goede kans op een naam conflict met functies met de naam iets zoals `Get-Version` en standaard opdrachten in Power shell of opdrachten die anderen kunnen schrijven. Daarom raden we u aan om het onderdeel van de zelfstandig naam woord van uw functies voor te stellen om conflicten met namen te voor komen. In het volgende voor beeld gebruiken we het voor voegsel "PS".

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

Met uitzonde ring van de naam is deze functie gelijk aan die van de voor gaande.

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Zelfs bij het voor voegsel van het zelfstandige naam woord, zoals PS, is er nog steeds een goede kans op conflicten. Ik maak normaal gesp roken voor voegsel mijn eigen naam woorden met mijn initialen. Ontwikkel een Standard-en-stick.

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

Deze functie wijkt af van de vorige twee andere dan het gebruik van een meer herkenbaar naam om conflicten met andere Power shell-opdrachten te voor komen.

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Wanneer u in het geheugen hebt geladen, kunt u functies zien op de **functie** PSDrive.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

Als u deze functies uit uw huidige sessie wilt verwijderen, moet u deze verwijderen uit de **functie** PSDrive of de Power shell sluiten en opnieuw openen.

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

Controleer of de functies inderdaad zijn verwijderd.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

Als de functies zijn geladen als onderdeel van een module, kan de module worden verwijderd om ze te verwijderen.

```powershell
Remove-Module -Name <ModuleName>
```

Met de `Remove-Module` cmdlet worden modules uit het geheugen verwijderd uit de huidige Power shell-sessie, worden deze niet verwijderd van uw systeem of van schijf.

## <a name="parameters"></a>Parameters

Geen statische waarden toewijzen. Gebruik para meters en variabelen. Wanneer het gaat om de naam van uw para meters, moet u, indien mogelijk, dezelfde naam gebruiken als de standaard-cmdlets voor uw parameter namen.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Waarom heb ik **ComputerName** en niet **computer**, **servername** of **host** gebruikt voor mijn parameter naam? De reden hiervoor is dat ik mijn functie wil gebruiken zoals de standaard-cmdlets.

Ik maak een functie om alle opdrachten op een systeem te doorzoeken en het aantal te retour neren met specifieke parameter namen.

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

Zoals u kunt zien in de onderstaande resultaten, 39 opdrachten met de para meter **ComputerName** . Er zijn geen cmdlets met para meters zoals **computer**, **servername**, **host** of **machine**.

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

Het is ook raadzaam om hetzelfde hoofdletter gebruik te gebruiken voor uw parameter namen als de standaard-cmdlets. Gebruiken `ComputerName` , niet `computername` . Dit zorgt ervoor dat uw functies eruitzien zoals de standaard-cmdlets. Mensen die al bekend zijn met Power shell, kunnen thuis.

Met de- `param` instructie kunt u een of meer para meters definiëren. De parameter definities worden gescheiden door een komma ( `,` ). Zie [about_Functions_Advanced_Parameters][]voor meer informatie.

## <a name="advanced-functions"></a>Geavanceerde functies

Het is heel eenvoudig om een functie in Power shell in te scha kelen in een geavanceerde functie. Een van de verschillen tussen een functie en een geavanceerde functie is dat geavanceerde functies beschikken over een aantal algemene para meters die automatisch aan de functie worden toegevoegd. Deze algemene para meters zijn para meters zoals **uitgebreid** en **fout opsporing**.

Ik begin met de `Test-MrParameter` functie die is gebruikt in de vorige sectie.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Wat ik wil dat de `Test-MrParameter` functie geen algemene para meters bevat. Er zijn verschillende manieren om de algemene para meters weer te geven. Een voor beeld is de syntaxis met behulp van `Get-Command` .

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

Een andere is om in te zoomen op de para meters met `Get-Command` .

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

Toevoegen `CmdletBinding` om de functie in te scha kelen in een geavanceerde functie.

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

`CmdletBinding`De algemene para meters worden automatisch toegevoegd. `CmdletBinding` vereist een `param` blok, maar het `param` blok kan leeg zijn.

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

Inzoomen op de para meters met `Get-Command` toont de werkelijke parameter namen met inbegrip van de gemeen schappelijke para meters.

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

`SupportsShouldProcess` Hiermee worden **WhatIf** -en **confirm** -para meters toegevoegd. Deze zijn alleen nodig voor opdrachten die wijzigingen aanbrengen.

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

U ziet dat er nu **WhatIf** en-para meters worden **bevestigd** .

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Opnieuw kunt u ook gebruiken `Get-Command` om een lijst met de werkelijke parameter namen te retour neren, met inbegrip van de gemeen schappelijke para meters, samen met WhatIf en bevestigen.

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a>Validatie van de para meter

Valideer invoer vroegtijdig op. Waarom staat uw code toe om door te gaan op een pad wanneer het niet mogelijk is om zonder geldige invoer uit te voeren?

Typ altijd de variabelen die voor de para meters worden gebruikt (Geef een gegevens type op).

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

In het vorige voor beeld is de **teken reeks** opgegeven als het gegevens type voor de para meter **ComputerName** . Hierdoor kan er slechts één computer naam worden opgegeven. Als meer dan een computer naam is opgegeven via een lijst met door komma's gescheiden waarden, wordt er een fout gegenereerd.

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

Het probleem met de huidige definitie is dat de waarde van de para meter **ComputerName** weglaat, maar een waarde is vereist voor het volt ooien van de functie. Hier `Mandatory` komt het parameter kenmerk op de handige manier.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

De syntaxis die in het vorige voor beeld wordt gebruikt, is Power shell versie 3,0 en hoger compatibel.
`[Parameter(Mandatory=$true)]` kan in plaats daarvan worden opgegeven om de functie compatibel te maken met Power shell versie 2,0 en hoger. Nu de **computer naam** is vereist, als deze nog niet is opgegeven, wordt er een prompt weer gegeven.

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

Als u meer dan één waarde wilt toestaan voor de para meter **ComputerName** , gebruikt u het **teken reeks** gegevens type, maar voegt u open en gesloten vier Kante haken toe aan het gegevens type om een matrix van teken reeksen toe te staan.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

Misschien wilt u een standaard waarde opgeven voor de para meter **ComputerName** als er geen is opgegeven.
Het probleem is dat de standaard waarden niet met verplichte para meters kunnen worden gebruikt. In plaats daarvan moet u het `ValidateNotNullOrEmpty` parameter validatie kenmerk gebruiken met een standaard waarde.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

Zelfs wanneer u een standaard waarde instelt, kunt u geen statische waarden gebruiken. In het vorige voor beeld `$env:COMPUTERNAME` wordt gebruikt als de standaard waarde, die automatisch wordt omgezet in de naam van de lokale computer als er geen waarde wordt gegeven.

## <a name="verbose-output"></a>Uitgebreide uitvoer

Inline opmerkingen zijn handig, met name als u complexe code schrijft, ze worden nooit door gebruikers gezien, tenzij ze in de code zelf kijken.

In het volgende voor beeld wordt in de lus een in line opmerking weer gegeven `foreach` . Hoewel deze specifieke opmerking mogelijk niet moeilijk te vinden is, stel dan dat de functie honderden regels code bevat.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

Een betere optie is om `Write-Verbose` in plaats van inline opmerkingen te gebruiken.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

Wanneer de functie wordt aangeroepen zonder de para meter **uitgebreid** , wordt de uitgebreide uitvoer niet weer gegeven.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

Als deze wordt aangeroepen met de para meter **uitgebreid** , wordt de uitgebreide uitvoer weer gegeven.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a>Pijplijn invoer

Wanneer u de invoer van de pijp lijn wilt accepteren, is een extra code ring nodig. Zoals eerder in dit boek wordt vermeld, kunnen opdrachten de invoer van de pijp lijn **op basis van waarde** (per type) of **eigenschaps naam** accepteren. U kunt uw functies schrijven op dezelfde manier als de systeem eigen opdrachten, zodat ze een of beide typen invoer accepteren.

Als u de pijp lijn invoer **per waarde** wilt accepteren, moet u het `ValueFromPipeline` parameter kenmerk voor die specifieke para meter opgeven. Denk eraan dat u alleen pijplijn invoer kunt accepteren **op waarde** uit een van beide gegevens typen. Als u bijvoorbeeld twee para meters hebt die teken reeks invoer accepteren, kan slechts één van deze de pijplijn invoer **door de waarde** accepteren. Als u deze voor beide teken reeks parameters hebt opgegeven, zou de pijplijn invoer niet weten welk item moet worden gekoppeld. Dit is een andere reden dat ik dit type pijplijn invoer aanroept _per type_ in plaats van **met een waarde**.

De invoer van de pijp lijn bevindt zich in één item op hetzelfde tijdstip als de manier waarop items in een lus worden verwerkt `foreach` .
Een blok is mini maal `process` vereist voor het verwerken van elk van deze items als u een matrix als invoer accepteert. Als u slechts één waarde als invoer accepteert, `process` is een blok is niet nodig, maar het wordt nog wel aanbevolen om het op consistentie te geven.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

De invoer van de pijp lijn wordt geaccepteerd **door de naam** van de eigenschap, behalve dat deze is opgegeven met het `ValueFromPipelineByPropertyName` parameter kenmerk en kan worden opgegeven voor een wille keurig aantal para meters ongeacht het gegevens type. De sleutel is de uitvoer van de opdracht die wordt gesluizen in, moet een eigenschaps naam hebben die overeenkomt met de naam van de para meter of een parameter alias van uw functie.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

`BEGIN` en `END` blokken zijn optioneel. `BEGIN` moet vóór het blok worden opgegeven `PROCESS` en wordt gebruikt voor het uitvoeren van de eerste werkzaamheden vóór de items die vanuit de pijp lijn worden ontvangen. Dit is belang rijk om te begrijpen. Waarden die worden bepiped in, zijn niet toegankelijk in het `BEGIN` blok. Het `END` blok wordt na het blok opgegeven `PROCESS` en wordt gebruikt voor het opschonen van alle items die in de pipes zijn verwerkt.

## <a name="error-handling"></a>Foutafhandeling

De functie die in het volgende voor beeld wordt weer gegeven, genereert een onverwerkte uitzonde ring wanneer er geen verbinding kan worden gemaakt met een computer.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

Er zijn verschillende manieren om fouten in Power shell af te handelen. `Try/Catch` is de meer moderne manier om fouten af te handelen.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

Hoewel de functie die in het vorige voor beeld wordt weer gegeven, gebruikmaakt van fout afhandeling, wordt er ook een onverwerkte uitzonde ring gegenereerd omdat de opdracht geen afsluit fout genereert. Dit is ook belang rijk om te begrijpen. Alleen afsluit fouten worden geblokkeerd. Geef de para meter **Error Action** op met **stoppen** als de waarde om een niet-afsluit fout te maken naar een beëindiging.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

Wijzig de globale `$ErrorActionPreference` variabele alleen als dat absoluut nood zakelijk is. Als u iets zoals .NET rechtstreeks vanuit uw Power shell-functie gebruikt, kunt u de **Error Action** niet opgeven in de opdracht zelf. In dat geval moet u mogelijk de globale `$ErrorActionPreference` variabele wijzigen, maar als u deze wijzigt, wijzigt u deze direct na het uitvoeren van de opdracht.

## <a name="comment-based-help"></a>Help bij Comment-Based

Het wordt beschouwd als een best practice om Help op basis van opmerkingen toe te voegen aan uw functies, zodat de personen met wie u ze deelt, weten hoe ze kunnen worden gebruikt.

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

Wanneer u op opmerkingen gebaseerde hulp toevoegt aan uw functies, kan Help worden opgehaald, net als de standaard ingebouwde opdrachten.

Alle syntaxis voor het schrijven van een functie in Power shell lijkt bijzonder goed te zijn voor iemand die net aan de slag gaat. Vaak als ik de syntaxis voor iets niet weet, open ik een tweede kopie van de ISE op een afzonderlijke monitor en bekijk ik het ' cmdlet (geavanceerde functie)-volledig ' tijdens het typen van de code voor mijn functie. Fragmenten kunnen worden geopend in de Power shell-ISE met behulp van de toetscombinatie <kbd>CTRL</kbd> + <kbd>J</kbd> .

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u de basis beginselen geleerd van het schrijven van functies in Power shell om te laten zien hoe u een functie kunt omzetten in een geavanceerde functie en een aantal van de belangrijkste elementen waarmee u rekening moet houden wanneer u Power shell-functies schrijft, zoals validatie van de para meters, uitgebreide uitvoer, invoer van de pijp lijn, fout afhandeling en op opmerkingen gebaseerde Help.

## <a name="review"></a>Beoordelen

1. Hoe krijg ik een lijst met goedgekeurde werk woorden in Power shell?
1. Hoe zet u een Power shell-functie om in een geavanceerde functie?
1. Wanneer moet **WhatIf** en **Bevestig** de para meters worden toegevoegd aan uw Power shell-functies?
1. Hoe kan ik een niet-afsluit fout omzetten in een afsluitende?
1. Waarom moet u op opmerkingen gebaseerde hulp toevoegen aan uw functies?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

- [about_Functions][]
- [about_Functions_Advanced_Parameters][]
- [about_CommonParameters][]
- [about_Functions_CmdletBindingAttribute][]
- [about_Functions_Advanced][]
- [about_Try_Catch_Finally][]
- [about_Comment_Based_Help][]
- [Video: Power shell-Toolmaking met geavanceerde functies en script modules][]

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[Video: Power shell-Toolmaking met geavanceerde functies en script modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Pascal-Case]: /dotnet/standard/design-guidelines/capitalization-conventions
