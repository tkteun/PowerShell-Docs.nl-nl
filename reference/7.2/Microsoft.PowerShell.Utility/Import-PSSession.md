---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 1a87783f9d12d852d3a6809e9457a55ad6e7be50
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705430"
---
# Import-PSSession

## SAMENVATTING
Importeert opdrachten vanuit een andere sessie in de huidige sessie.

## SYNTAXIS

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## BESCHRIJVING

`Import-PSSession`Met de cmdlet worden opdrachten, zoals cmdlets, functies en aliassen, geïmporteerd van een PSSession op een lokale of externe computer in de huidige sessie. U kunt elke opdracht importeren die met de `Get-Command` cmdlet kan worden gevonden in de PSSession.

Gebruik een `Import-PSSession` opdracht voor het importeren van opdrachten uit een aangepaste shell, zoals een micro soft Exchange server shell, of vanuit een sessie met Windows Power shell-modules en-modules of andere elementen die zich niet in de huidige sessie bevinden.

Voor het importeren van opdrachten moet u eerst de `New-PSSession` cmdlet gebruiken om een PSSession te maken. Gebruik vervolgens de `Import-PSSession` cmdlet om de opdrachten te importeren. Standaard worden `Import-PSSession` alle opdrachten geïmporteerd, met uitzonde ring van opdrachten met dezelfde namen als opdrachten in de huidige sessie. Als u alle opdrachten wilt importeren, gebruikt u de para meter **AllowClobber** .

U kunt geïmporteerde opdrachten op dezelfde manier gebruiken als elke opdracht in de sessie. Wanneer u een geïmporteerde opdracht gebruikt, wordt het geïmporteerde deel van de opdracht impliciet uitgevoerd in de sessie van waaruit het is geïmporteerd. De externe bewerkingen worden echter volledig verwerkt door Windows Power shell. U hoeft er niet eens op te letten, behalve dat u de verbinding met de andere sessie (PSSession) open moet houden. Als u het sluit, zijn de geïmporteerde opdrachten niet meer beschikbaar.

Omdat geïmporteerde opdrachten mogelijk langer duren om te worden uitgevoerd dan lokale opdrachten, `Import-PSSession` voegt een **AsJob** -para meter toe aan elke geïmporteerde opdracht. Met deze para meter kunt u de opdracht uitvoeren als een Windows Power shell-achtergrond taak. Zie [About Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) (Taken) voor meer informatie.

Wanneer u gebruikt `Import-PSSession` , voegt Windows Power shell de geïmporteerde opdrachten toe aan een tijdelijke module die alleen in uw sessie bestaat en wordt een object geretourneerd dat de module vertegenwoordigt. Als u een permanente module wilt maken die u in toekomstige sessies kunt gebruiken, gebruikt u de `Export-PSSession` cmdlet.

De `Import-PSSession` cmdlet maakt gebruik van de impliciete externe functie van Windows Power shell. Wanneer u opdrachten in de huidige sessie importeert, worden deze impliciet uitgevoerd in de oorspronkelijke sessie of in een vergelijk bare sessie op de oorspronkelijke computer.

Vanaf Windows Power Shell 3,0 kunt u met de `Import-Module` cmdlet modules uit een externe sessie importeren in de huidige sessie. Deze functie maakt gebruik van impliciete externe communicatie. Het is gelijk aan `Import-PSSession` het gebruik van om geselecteerde modules vanuit een externe sessie te importeren in de huidige sessie.

## VOORBEELDEN

### Voor beeld 1: alle opdrachten uit een PSSession importeren

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

Met deze opdracht worden alle opdrachten van een PSSession op de Server01-computer in de huidige sessie geïmporteerd, met uitzonde ring van opdrachten met dezelfde namen als opdrachten in de huidige sessie.

Omdat met deze opdracht de para meter **opdracht** naam niet wordt gebruikt, worden ook alle opmaak gegevens die nodig zijn voor de geïmporteerde opdrachten geïmporteerd.

### Voor beeld 2: opdrachten importeren die met een specifieke teken reeks eindigen

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

Met deze opdrachten worden de opdrachten met namen die eindigen op '-test ' van een PSSession in de lokale sessie geïmporteerd. vervolgens wordt weer gegeven hoe u een geïmporteerde cmdlet gebruikt.

De eerste opdracht gebruikt de `New-PSSession` cmdlet om een PSSession te maken. De PSSession wordt opgeslagen in de `$S` variabele.

Met de tweede opdracht wordt de `Import-PSSession` cmdlet gebruikt voor het importeren van opdrachten uit de PSSession in `$S` de huidige sessie. De para meter **opdracht** naam wordt gebruikt om opdrachten op te geven met het zelfstandig naam woord test en de para meter **FormatTypeName** om de opmaak gegevens voor de test opdrachten te importeren.

De derde en vierde opdracht gebruiken de geïmporteerde opdrachten in de huidige sessie. Omdat geïmporteerde opdrachten daad werkelijk aan de huidige sessie worden toegevoegd, gebruikt u de lokale syntaxis om ze uit te voeren. U hoeft de cmdlet niet te gebruiken `Invoke-Command` om een geïmporteerde opdracht uit te voeren.

### Voor beeld 3: cmdlets importeren uit een PSSession

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

Dit voor beeld laat zien dat u geïmporteerde cmdlets kunt gebruiken, net zoals u lokale cmdlets zou gebruiken.

Met deze opdrachten worden de- `New-Test` en- `Get-Test` cmdlets van een PSSession op de Server01-computer en de `Set-Test` cmdlet van een PSSession op de Server02-computer geïmporteerd.

Hoewel de cmdlets uit verschillende PSSessions zijn geïmporteerd, kunt u zonder fouten een object van de ene naar de andere cmdlet sluizen.

### Voor beeld 4: een geïmporteerde opdracht uitvoeren als een achtergrond taak

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

In dit voor beeld ziet u hoe u een geïmporteerde opdracht als achtergrond taak uitvoert.

Omdat geïmporteerde opdrachten mogelijk langer duren om te worden uitgevoerd dan lokale opdrachten, `Import-PSSession` voegt een **AsJob** -para meter toe aan elke geïmporteerde opdracht. Met de para meter **AsJob** kunt u de opdracht uitvoeren als een achtergrond taak.

Met de eerste opdracht maakt u een PSSession op de Server01-computer en slaat u het PSSession-object op in de `$S` variabele.

De tweede opdracht gebruikt `Import-PSSession` voor het importeren van de test-cmdlets van de PSSession in `$S` naar de huidige sessie.

De derde opdracht maakt gebruik van de para meter **AsJob** van de geïmporteerde `New-Test` cmdlet om een `New-Test` opdracht als achtergrond taak uit te voeren. Met de opdracht slaat u het taak object `New-Test` op dat in de variabele wordt geretourneerd `$batch` .

De vierde opdracht gebruikt de `Receive-Job` cmdlet om de resultaten van de taak in de variabele op te halen `$batch` .

### Voor beeld 5: cmdlets en functies importeren vanuit een Windows Power shell-module

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

In dit voor beeld ziet u hoe u de cmdlets en functies van een Windows Power shell-module op een externe computer kunt importeren in de huidige sessie.

Met de eerste opdracht maakt u een PSSession op de Server01-computer en slaat u deze op in de `$S` variabele.

De tweede opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Import-Module` in de PSSession in `$S` .

Normaal gesp roken wordt de module toegevoegd aan alle sessies met een `Import-Module` opdracht in een Windows Power shell-profiel, maar profielen worden niet uitgevoerd in PSSessions.

De derde opdracht maakt gebruik van de para meter **module** van `Import-PSSession` om de cmdlets en functies in de module te importeren in de huidige sessie.

### Voor beeld 6: een module maken in een tijdelijk bestand

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

Dit voor beeld laat zien dat `Import-PSSession` een module maakt in een tijdelijk bestand op schijf. Er wordt ook weer gegeven dat alle opdrachten worden geconverteerd naar functies voordat ze in de huidige sessie worden geïmporteerd.

De opdracht gebruikt de `Import-PSSession` cmdlet om een `Get-Date` cmdlet en een SearchHelp-functie te importeren in de huidige sessie.

De `Import-PSSession` cmdlet retourneert een **PSModuleInfo** -object dat de tijdelijke module vertegenwoordigt. De waarde van de eigenschap **Path** geeft `Import-PSSession` aan dat er een script module-bestand (. psm1) op een tijdelijke locatie is gemaakt. De eigenschap **ExportedFunctions** geeft aan dat de `Get-Date` cmdlet en de functie SearchHelp als functies zijn geïmporteerd.

### Voor beeld 7: een opdracht uitvoeren die is verborgen met een geïmporteerde opdracht

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

In dit voor beeld ziet u hoe u een opdracht uitvoert die verborgen is door een geïmporteerde opdracht.

Met de eerste opdracht wordt een `Get-Date` cmdlet uit de PSSession in de `$S` variabele geïmporteerd. Omdat de huidige sessie een `Get-Date` cmdlet bevat, is de para meter **AllowClobber** vereist in de opdracht.

Met de tweede opdracht wordt de para meter **all** van de `Get-Command` cmdlet gebruikt om alle `Get-Date` opdrachten in de huidige sessie op te halen. De uitvoer laat zien dat de sessie de oorspronkelijke `Get-Date` cmdlet en een `Get-Date` functie bevat. De `Get-Date` functie voert de geïmporteerde `Get-Date` cmdlet uit in de PSSession in `$S` .

Met de derde opdracht wordt een `Get-Date` opdracht uitgevoerd. Omdat functies voor rang hebben boven cmdlets, voert Windows Power shell de geïmporteerde `Get-Date` functie uit, waardoor een Juliaanse datum wordt geretourneerd.

De vierde en vijfde opdrachten laten zien hoe u een gekwalificeerde naam kunt gebruiken om een opdracht uit te voeren die verborgen is door een geïmporteerde opdracht.

Met de vierde opdracht haalt u de naam op van de Windows Power shell-module waarmee de oorspronkelijke cmdlet is toegevoegd `Get-Date` aan de huidige sessie.

De vijfde opdracht maakt gebruik van de met de module gekwalificeerde naam van de `Get-Date` cmdlet om een opdracht uit te voeren `Get-Date` .

Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)voor meer informatie over de prioriteit van opdrachten en verborgen opdrachten.

### Voor beeld 8: opdrachten importeren die een specifieke teken reeks in hun namen hebben

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

Met deze opdracht worden opdrachten geïmporteerd waarvan de naam item uit de PSSession bevat `$S` . Omdat de opdracht de para meter **opdrachtnaam** , maar niet de para meter **FormatTypeData** bevat, wordt alleen de opdracht geïmporteerd.

Gebruik deze opdracht wanneer u gebruikt `Import-PSSession` om een opdracht uit te voeren op een externe computer en u beschikt al over de indelings gegevens voor de opdracht in de huidige sessie.

### Voor beeld 9: de module parameter gebruiken om te ontdekken welke opdrachten in de sessie zijn geïmporteerd

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

Met deze opdracht wordt uitgelegd hoe u de **module** parameter van gebruikt `Get-Command` om te ontdekken welke opdrachten in de sessie zijn geïmporteerd door een `Import-PSSession` opdracht.

De eerste opdracht gebruikt de `Import-PSSession` cmdlet om opdrachten te importeren waarvan de naam ' bits ' bevat uit de PSSession in de `$S` variabele. De `Import-PSSession` opdracht retourneert een tijdelijke module en de opdracht slaat de module op in de `$m` variabele.

De tweede opdracht gebruikt de `Get-Command` cmdlet om de opdrachten op te halen die worden geëxporteerd door de module in de `$M` variabele.

De **module** parameter heeft een teken reeks waarde die is ontworpen voor de module naam. Wanneer u echter een module object verzendt, gebruikt Windows Power shell de **toString** -methode voor het module object, waarmee de module naam wordt geretourneerd.

De `Get-Command` opdracht is het equivalent van `Get-Command $M.Name` '.

## PARAMETERS

### -AllowClobber

Geeft aan dat met deze cmdlet de opgegeven opdrachten worden geïmporteerd, zelfs als ze dezelfde namen hebben als opdrachten in de huidige sessie.

Als u een opdracht importeert met dezelfde naam als een opdracht in de huidige sessie, worden de oorspronkelijke opdrachten verborgen of vervangen door de geïmporteerde opdracht. Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)voor meer informatie.

`Import-PSSession`Opdrachten die dezelfde naam hebben als opdrachten in de huidige sessie, worden standaard niet geïmporteerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Argument List

Hiermee geeft u een matrix met opdrachten op die het resultaat zijn van het gebruik van de opgegeven argumenten (parameter waarden).

Om bijvoorbeeld de variant van de `Get-Item` opdracht in het certificaat te importeren (CERT:) in het PSSession-station in `$S` , typt u `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Certificaat

Hiermee geeft u het client certificaat op dat wordt gebruikt voor het ondertekenen van de indelings bestanden (* .Format.ps1XML) of script module bestanden (. psm1) in de tijdelijke module die `Import-PSSession` wordt gemaakt.

Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.

Als u een certificaat wilt zoeken, gebruikt u de `Get-PfxCertificate` cmdlet of gebruikt u de `Get-ChildItem` cmdlet in het certificaat (CERT:) stationsletter. Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Opdrachtnaam

Geeft opdrachten met de opgegeven namen of naam patronen. Joker tekens zijn toegestaan. Gebruik de **naam** van de **opdracht** of de alias.

Standaard worden `Import-PSSession` alle opdrachten uit de sessie geïmporteerd, met uitzonde ring van opdrachten die dezelfde namen hebben als opdrachten in de huidige sessie. Zo voor komt u dat geïmporteerde opdrachten opdrachten in de sessie verbergen of vervangen. Gebruik de para meter **AllowClobber** als u alle opdrachten wilt importeren, zelfs op die andere opdrachten.

Als u de para meter **opdrachtnaam** gebruikt, worden de opmaak bestanden voor de opdrachten niet geïmporteerd, tenzij u de para meter **FormatTypeName** gebruikt. Ook als u de para meter **FormatTypeName** gebruikt, worden er geen opdrachten geïmporteerd, tenzij u de para meter **opdrachtnaam** gebruikt.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

Hiermee wordt het type opdracht objecten opgegeven. De standaard waarde is cmdlet. Gebruik **CommandType** of de alias, **Typ**. De aanvaardbare waarden voor deze parameter zijn:

- Toe. De Windows Power shell-aliassen in de externe sessie.
- Hele. De cmdlets en functies in de externe sessie.
- Modules. Alle bestanden met uitzonde ring van Windows-PowerShell bestanden in de paden die worden vermeld in de Path-omgevings variabele ( `$env:path` ) in de externe sessie, inclusief. txt,. exe en. dll-bestanden.
- Cmdlet. De cmdlets in de externe sessie. ' Cmdlet ' is de standaard waarde.
- ExternalScript. De. ps1-bestanden in de paden die worden weer gegeven in de omgevings variabele PATH ( `$env:path` ) in de externe sessie.
- Filter en functie. De Windows Power shell-functies in de externe sessie.
- Schriften. De script blokken in de externe sessie.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableNameChecking

Geeft aan dat deze cmdlet het bericht onderdrukt dat u waarschuwt wanneer u een cmdlet of functie importeert waarvan de naam een niet-goedgekeurde term of een verboden teken bevat.

Als een module die u importeert cmdlets of functies met een niet-goedgekeurde term in hun namen, wordt standaard het volgende waarschuwings bericht weer gegeven:

"Waarschuwing: Sommige geïmporteerde opdracht namen bevatten niet-goedgekeurde werk woorden, waardoor ze minder kunnen worden gedetecteerd. Gebruik de para meter uitgebreid voor meer details of type `Get-Verb` om de lijst met goedgekeurde woorden weer te geven. "

Dit bericht wordt alleen een waarschuwing gegeven. De volledige module is nog steeds geïmporteerd, met inbegrip van de niet-conforme opdrachten. Hoewel het bericht wordt weer gegeven voor module gebruikers, moet het naam probleem worden opgelost door de module auteur.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatTypeName

Hiermee geeft u opmaak instructies op voor de opgegeven Microsoft .NET Framework typen.
Voer de type namen in.
Joker tekens zijn toegestaan.

De waarde van deze para meter moet de naam van een type zijn dat wordt geretourneerd door een `Get-FormatData` opdracht in de sessie van waaruit de opdrachten worden geïmporteerd. Als u alle opmaak gegevens in de externe sessie wilt ophalen, typt u `*` .

Als de opdracht geen **opdracht** naam of para meter **FormatTypeName** bevat, worden `Import-PSSession` in de externe sessie opmaak instructies geïmporteerd voor alle .NET Framework typen die door een opdracht worden geretourneerd `Get-FormatData` .

Als u de para meter **FormatTypeName** gebruikt, worden er geen opdrachten geïmporteerd, tenzij u de para meter **opdrachtnaam** gebruikt.

Ook als u de para meter **opdrachtnaam** gebruikt, worden de opmaak bestanden voor de opdrachten niet geïmporteerd, tenzij u de para meter **FormatTypeName** gebruikt.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten (zoals beschreven in de sectie opmerkingen van [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) in de Power shell-SDK. De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in de indeling:

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}` of
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.

**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.

U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter. De twee para meters sluiten elkaar wederzijds uit.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

Hiermee wordt een matrix met opdrachten in de Windows Power shell-module en-modules opgegeven. Voer de module-en module namen in. Joker tekens zijn niet toegestaan.

`Import-PSSession` kan geen providers importeren vanuit een module.

Zie [about_PSSnapins](/powershell/module/Microsoft.PowerShell.Core/About/about_PSSnapins) en [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Voor voegsel

Hiermee geeft u een voor voegsel op voor de zelfstandige naam woorden in de namen van geïmporteerde opdrachten.

Gebruik deze para meter om naam conflicten te voor komen die zich kunnen voordoen wanneer verschillende opdrachten in de sessie dezelfde naam hebben.

Als u bijvoorbeeld het voor voegsel extern opgeeft en vervolgens een cmdlet importeert `Get-Date` , wordt de cmdlet bekend in de sessie als `Get-RemoteDate` en wordt deze niet verward met de oorspronkelijke `Get-Date` cmdlet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie

Hiermee geeft u de **PSSession** op van waaruit de cmdlets worden geïmporteerd. Voer een variabele in die een sessie object bevat of een opdracht waarmee een sessie object wordt opgehaald, zoals een `New-PSSession` of- `Get-PSSession` opdracht. U kunt slechts één sessie opgeven. Deze parameter is vereist.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### System. Management. Automation. PSModuleInfo

`Import-PSSession` retourneert hetzelfde module-object dat `New-Module` en `Get-Module` cmdlets retour neren.
De geïmporteerde module is echter tijdelijk en bestaat alleen in de huidige sessie. Als u een permanente module op schijf wilt maken, gebruikt u de `Export-PSSession` cmdlet.

## OPMERKINGEN

- `Import-PSSession` is afhankelijk van de externe infra structuur van Power shell. Als u deze cmdlet wilt gebruiken, moet de computer zijn geconfigureerd voor WS-Management externe communicatie. Zie [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) en [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)voor meer informatie.
- `Import-PSSession` variabelen of Power shell-providers worden niet geïmporteerd.
- Wanneer u opdrachten importeert die dezelfde namen hebben als opdrachten in de huidige sessie, kunnen de geïmporteerde opdrachten aliassen, functies en cmdlets in de sessie verbergen en kunnen de functies en variabelen in de sessie worden vervangen. Gebruik de para meter **voor voegsel** om naam conflicten te voor komen. Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)voor meer informatie.
- `Import-PSSession` Hiermee worden alle opdrachten geconverteerd naar functies voordat deze worden geïmporteerd. Als gevolg hiervan werken geïmporteerde opdrachten een beetje anders dan wanneer ze hun oorspronkelijke opdracht type behouden. Als u bijvoorbeeld een cmdlet uit een PSSession importeert en vervolgens een cmdlet met dezelfde naam uit een module of module importeert, wordt de cmdlet die wordt geïmporteerd uit de PSSession altijd standaard uitgevoerd, omdat functies voor rang hebben boven cmdlets. Als u daarentegen een alias importeert in een sessie met een alias met dezelfde naam, wordt de oorspronkelijke alias altijd gebruikt, omdat aliassen voor rang hebben op functies. Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)voor meer informatie.
- `Import-PSSession` gebruikt de `Write-Progress` cmdlet om de voortgang van de opdracht weer te geven. Mogelijk wordt de voortgangs balk weer geven terwijl de opdracht wordt uitgevoerd.
- Voor het zoeken naar de te importeren opdrachten `Import-PSSession` gebruikt u de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-Command` in de PSSession. De-cmdlet wordt gebruikt om de opmaak gegevens voor de opdrachten op te halen `Get-FormatData` . U ziet mogelijk fout berichten van deze cmdlets wanneer u een `Import-PSSession` opdracht uitvoert. Daarnaast `Import-PSSession` kunnen geen opdrachten worden geïmporteerd van een PSSession die geen-,-, `Get-Command` `Get-FormatData` `Select-Object` -en- `Get-Help` cmdlets bevat.
- Geïmporteerde opdrachten hebben dezelfde beperkingen als andere externe opdrachten, waaronder het niet mogelijk is om een programma te starten met een gebruikers interface, zoals Klad blok.
- Omdat Windows Power shell-profielen niet worden uitgevoerd in PSSessions, zijn de opdrachten die een profiel aan een sessie toevoegt, niet beschikbaar voor `Import-PSSession` . Als u opdrachten uit een profiel wilt importeren, gebruikt u een `Invoke-Command` opdracht om het profiel hand matig uit te voeren in de PSSession voordat u opdrachten importeert.
- De tijdelijke module die `Import-PSSession` maakt, kan een opmaak bestand bevatten, zelfs als de opdracht geen indelings gegevens importeert. Als de opdracht geen indelings gegevens importeert, bevatten indelings bestanden die worden gemaakt geen opmaak gegevens.
- `Import-PSSession`Het uitvoerings beleid in de huidige sessie mag niet worden beperkt of alles ondertekend, omdat de tijdelijke module die wordt gemaakt, niet- `Import-PSSession` ondertekende script bestanden bevat die niet zijn toegestaan door dit beleid. Als u wilt gebruiken `Import-PSSession` zonder het uitvoerings beleid voor de lokale computer te wijzigen, gebruikt u de para meter **bereik** van `Set-ExecutionPolicy` om een minder beperkend uitvoerings beleid in te stellen voor één proces.
- In Windows Power Shell 2,0 zijn Help-onderwerpen voor opdrachten die vanuit een andere sessie worden geïmporteerd niet het voor voegsel dat u toewijst met behulp van de para meter **prefix** . Als u hulp nodig hebt bij een geïmporteerde opdracht in Windows Power Shell 2,0, gebruikt u de oorspronkelijke (niet-voor-vaste) opdracht naam.

## GERELATEERDE KOPPELINGEN

[Exporteren-PSSession](Export-PSSession.md)
