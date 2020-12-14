---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 491292253578f287940490bad198698fc4b87e37
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705892"
---
# Start-Job

## SAMENVATTING
Start een Power shell-achtergrond taak.

## SYNTAXIS

### Computer naam (standaard)

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Definitie

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### FilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### LiteralFilePathComputerName

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## BESCHRIJVING

`Start-Job`Met de cmdlet wordt een Power shell-achtergrond taak gestart op de lokale computer.

Met een Power shell-achtergrond taak wordt een opdracht uitgevoerd zonder interactie met de huidige sessie. Wanneer u een achtergrond taak start, retourneert een taak object onmiddellijk, zelfs als de taak een lange tijd kost om te volt ooien. U kunt zonder onderbreking in de sessie blijven werken terwijl de taak wordt uitgevoerd.

Het taak object bevat nuttige informatie over de taak, maar bevat geen taak resultaten.
Wanneer de taak is voltooid, gebruikt `Receive-Job` u de cmdlet om de resultaten van de taak op te halen. Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over achtergrond taken.

Als u een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u de para meter **AsJob** die beschikbaar is in veel cmdlets of gebruikt `Invoke-Command` u de cmdlet om een opdracht uit te voeren `Start-Job` op de externe computer. Zie [about_Remote_Jobs](./About/about_Remote_Jobs.md)voor meer informatie.

Vanaf Power Shell 3,0 `Start-Job` kunnen exemplaren van aangepaste taak typen worden gestart, zoals geplande taken. `Start-Job`Zie de Help-documenten voor de functie type taak voor meer informatie over het gebruik van om taken met aangepaste typen te starten.

Vanaf Power shell 6,0 kunt u taken starten met de-ampersand ( `&` )-achtergrond operator. De functionaliteit van de operator achtergrond is vergelijkbaar met `Start-Job` . Met beide methoden voor het starten van een taak maakt u een **PSRemotingJob** -taak object. Zie about_Operators voor meer informatie over het gebruik van het `&` en [](./about/about_operators.md#background-operator-)-teken ().

Power shell 7 heeft de **variabele workingdirectory** -para meter geïntroduceerd waarmee de oorspronkelijke werkmap van een achtergrond taak wordt opgegeven. Als de para meter niet is opgegeven, wordt `Start-Job` standaard de actieve werkmap gebruikt van de aanroeper waarmee de taak is gestart.

> [!NOTE]
> Het maken van een out-of-process-achtergrond taak met `Start-Job` wordt niet ondersteund in het scenario waarin Power shell wordt gehost in andere toepassingen, zoals de Power shell-Azure functions.
>
> Dit is standaard, omdat `Start-Job` het `pwsh` uitvoer bare bestand dat beschikbaar is voor het `$PSHOME` starten van een out-of-process-achtergrond taak, maar wanneer een toepassing Power shell host, rechtstreeks gebruikmaakt van de Power shell NuGet SDK-pakketten en deze niet heeft `pwsh` verzonden.
>
> De vervanging in dat scenario is `Start-ThreadJob` afkomstig uit de module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)**.

## VOORBEELDEN

### Voor beeld 1: een achtergrond taak starten

In dit voor beeld wordt een achtergrond taak gestart die wordt uitgevoerd op de lokale computer.

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

`Start-Job` maakt gebruik van de para meter **script Block** om te worden uitgevoerd `Get-Process` als een achtergrond taak. De para meter **name** geeft aan dat Power shell-processen moeten worden gevonden `pwsh` . De taak informatie wordt weer gegeven en Power shell keert terug naar een prompt wanneer de taak op de achtergrond wordt uitgevoerd.

Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` . Bijvoorbeeld `Receive-Job -Id 1`.

### Voor beeld 2: de operator achtergrond gebruiken om een achtergrond taak te starten

In dit voor beeld wordt de ampersand ( `&` )-achtergrond operator gebruikt om een achtergrond taak op de lokale computer te starten. De taak krijgt hetzelfde resultaat als `Start-Job` in voor beeld 1.

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

`Get-Process` maakt gebruik van de para meter **name** voor het opgeven van Power shell-processen `pwsh` . Met het ampersand ( `&` ) wordt de opdracht als achtergrond taak uitgevoerd. De taak informatie wordt weer gegeven en Power shell keert terug naar een prompt wanneer de taak op de achtergrond wordt uitgevoerd.

Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` . Bijvoorbeeld `Receive-Job -Id 5`.

### Voor beeld 3: een taak starten met Invoke-Command

In dit voor beeld wordt een taak op meerdere computers uitgevoerd. De taak wordt opgeslagen in een variabele en wordt uitgevoerd met behulp van de naam van de variabele op de Power shell-opdracht regel.

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

Een taak die gebruikmaakt `Invoke-Command` van wordt gemaakt en opgeslagen in de `$jobWRM` variabele. `Invoke-Command` maakt gebruik van de para meter **ComputerName** om de computers op te geven waarop de taak wordt uitgevoerd. `Get-Content` Hiermee worden de server namen opgehaald uit het `C:\Servers.txt` bestand.

De **script Block** para meter geeft u een opdracht op waarmee `Get-Service` de **WinRM** -service wordt opgehaald. De **JobName** para meter geeft een beschrijvende naam voor de taak, **WinRM**. De para meter **ThrottleLimit** beperkt het aantal gelijktijdige opdrachten tot 16. Met de para meter **AsJob** wordt een achtergrond taak gestart die de opdracht uitvoert op de-servers.

### Voor beeld 4: taak gegevens ophalen

In dit voor beeld wordt informatie over een taak opgehaald en worden de resultaten weer gegeven van een voltooide taak die is uitgevoerd op de lokale computer.

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` maakt gebruik van de para meter **script Block** om een opdracht uit te voeren die opgeeft `Get-WinEvent` om het **systeem** logboek op te halen. De **referentie** parameter geeft een domein gebruikers account op dat is gemachtigd om de taak uit te voeren op de computer. Het taak object wordt opgeslagen in de `$j` variabele.

Het object in de `$j` variabele wordt naar beneden verzonden in de pijp lijn `Select-Object` . De **eigenschap** para meter geeft een asterisk ( `*` ) op om alle eigenschappen van het taak object weer te geven.

### Voor beeld 5: een script uitvoeren als een achtergrond taak

In dit voor beeld wordt een script op de lokale computer uitgevoerd als achtergrond taak.

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

`Start-Job` gebruikt de **filepath** -para meter om een script bestand op te geven dat is opgeslagen op de lokale computer.

### Voor beeld 6: een proces met een achtergrond taak verkrijgen

In dit voor beeld wordt een achtergrond taak gebruikt om een opgegeven proces op naam op te halen.

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

`Start-Job` maakt gebruik van de para meter **name** om een beschrijvende taak naam op te geven, **PShellJob**. De para meter **script Block** geeft `Get-Process` aan dat er processen worden opgehaald met de naam **Power shell**.

### Voor beeld 7: gegevens verzamelen en opslaan met behulp van een achtergrond taak

In dit voor beeld wordt een taak gestart die een grote hoeveelheid kaart gegevens verzamelt en vervolgens opslaat in een `.tif` bestand.

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

`Start-Job` maakt gebruik van de para meter **name** om een beschrijvende taak naam op te geven, **GetMappingFiles**. De para meter **InitializationScript** voert een script blok uit waarmee de **MapFunctions** -module wordt geïmporteerd. De para meter **script Block** wordt uitgevoerd `Get-Map` en `Set-Content` de gegevens worden opgeslagen op de locatie die is opgegeven door de para meter **Path** .

### Voor beeld 8: invoer door geven aan een achtergrond taak

In dit voor beeld wordt de `$input` Automatische variabele gebruikt voor het verwerken van een invoer object. Gebruiken `Receive-Job` om de uitvoer van de taak weer te geven.

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

`Start-Job` maakt gebruik van de para meter **script Block** om te worden uitgevoerd `Get-Content` met de `$input` Automatische variabele. De `$input` variabele haalt objecten op uit de para meter **input object** . `Receive-Job` maakt gebruik van de para meter **name** om de taak op te geven en de resultaten uit te voeren. De **Keep** -para meter slaat de taak uitvoer op zodat deze weer kan worden weer gegeven tijdens de Power shell-sessie.

### Voor beeld 9: de werkmap instellen voor een achtergrond taak

Met de **variabele workingdirectory** kunt u een alternatieve map opgeven voor een taak van waaruit u scripts of geopende bestanden kunt uitvoeren. In dit voor beeld wordt met de achtergrond taak een werkmap opgegeven die afwijkt van de huidige maplocatie.

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

In dit voor beeld is de huidige werkmap `C:\Test` . `Start-Job` maakt gebruik van de para meter **variabele workingdirectory** om de werkmap van de taak op te geven. De para meter **script Block** maakt gebruik `$PWD` van om de werkmap van de taak weer te geven. `Receive-Job` Hiermee wordt de uitvoer van de achtergrond taak weer gegeven.
**AutoRemoveJob** verwijdert de taak en **wacht** op de opdracht prompt totdat alle resultaten zijn ontvangen.

### Voor beeld 10: de para meter argument list gebruiken om een matrix op te geven

In dit voor beeld wordt de para meter **argument List** gebruikt om een matrix met argumenten op te geven. De matrix is een door komma's gescheiden lijst met proces namen.

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

De `Start-Job` cmdlet gebruikt de para meter **script Block** om een opdracht uit te voeren. `Get-Process` maakt gebruik van de para meter **name** om de automatische variabele op te geven `$args` . De **argument List** para meter geeft de matrix van proces namen door aan `$args` . De proces namen Power shell, pwsh en Notepad zijn processen die worden uitgevoerd op de lokale computer.

Gebruik de cmdlet om de uitvoer van de taak weer te geven `Receive-Job` . Bijvoorbeeld `Receive-Job -Id 1`.

### Voor beeld 11: taak uitvoeren in een Windows Power shell 5,1

In dit voor beeld wordt de **PSVersion** -para meter met de waarde **5,1** gebruikt voor het uitvoeren van een taak in een Windows Power shell 5,1-sessie.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Patch  PreReleaseLabel BuildLabel
-----  -----  -----  --------------- ----------
7      0      0      rc.1
```

```powershell
$job = Start-Job { $PSVersionTable.PSVersion } -PSVersion 5.1
Receive-Job $job
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  3383
```

## PARAMETERS

### -Argument List

Hiermee geeft u een matrix met argumenten, of parameter waarden, op voor het script dat is opgegeven met de para meter **filepath** of een opdracht die is opgegeven met de para meter **script Block** .

Argumenten moeten worden door gegeven aan **argument List** als een matrix argument met één dimensie. Bijvoorbeeld een lijst met door komma's gescheiden waarden. Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van gebruikers referenties.

De acceptabele waarden voor deze para meter zijn als volgt:

- Standaard
- Basic
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaard waarde is standaard.

CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.

Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

> [!CAUTION]
> De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Als de para meter **Credential** niet is opgegeven, gebruikt de opdracht de referenties van de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Definitie

Hiermee geeft u de definitie naam op van de taak die met deze cmdlet wordt gestart. Gebruik deze para meter om aangepaste taak typen te starten die een definitie naam hebben, zoals geplande taken.

Wanneer u gebruikt `Start-Job` om een exemplaar van een geplande taak te starten, wordt de taak onmiddellijk gestart, ongeacht taak triggers of taak opties. Het resulterende taak exemplaar is een geplande taak, maar wordt niet opgeslagen op schijf zoals geactiveerde geplande taken. U kunt de para meter **argument List** niet gebruiken `Start-Job` om waarden op te geven voor para meters van scripts die worden uitgevoerd in een geplande taak.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefinitionPath

Hiermee geeft u het pad op van de definitie voor de taak die met deze cmdlet wordt gestart. Voer het definitie-pad in. De samen voeging van de waarden van de para meters **DefinitionPath** en **rijdefinitie** is het volledig gekwalificeerde pad van de taak definitie. Gebruik deze para meter om aangepaste taak typen met een definitie-pad te starten, zoals geplande taken.

Voor geplande taken is de waarde van de  para meter DefinitionPath `$home\AppData\Local\Windows\PowerShell\ScheduledJob` .

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u een lokaal script op dat `Start-Job` als achtergrond taak wordt uitgevoerd. Voer het pad en de bestands naam van het script in of gebruik de pijp lijn om een scriptpad naar te verzenden `Start-Job` . Het script moet zich op de lokale computer of in een map bevindt waartoe de lokale computer toegang heeft.

Wanneer u deze para meter gebruikt, wordt de inhoud van het opgegeven script bestand door Power shell naar een script blok geconverteerd en wordt het script blok als achtergrond taak uitgevoerd.

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Geeft opdrachten die worden uitgevoerd voordat de taak wordt gestart. Als u een script blok wilt maken, plaatst u de opdrachten in accolades ( `{}` ).

Gebruik deze para meter om de sessie voor te bereiden waarin de taak wordt uitgevoerd. U kunt dit bijvoorbeeld gebruiken om functies, modules en modules toe te voegen aan de sessie.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de invoer aan de opdracht. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden gegenereerd.

Gebruik in de waarde van de para meter **script Block** de `$input` Automatische variabele om de invoer objecten te vertegenwoordigen.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u een lokaal script op dat met deze cmdlet als achtergrond taak wordt uitgevoerd. Geef het pad van een script op de lokale computer op.

`Start-Job` gebruikt de waarde van de para meter **LiteralPath** precies zoals deze wordt getypt. Er worden geen tekens geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een beschrijvende naam op voor de nieuwe taak. U kunt de naam gebruiken om de taak te identificeren in andere taak-cmdlets, zoals de- `Stop-Job` cmdlet.

De standaard beschrijvende naam is `Job#` , waarbij `#` een rang nummer is dat voor elke taak wordt verhoogd.

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSVersion

Hiermee geeft u een versie van Power shell op die moet worden gebruikt voor het uitvoeren van de taak.
Wanneer de waarde van **PSVersion** is **5,1** , wordt de taak uitgevoerd in een Windows Power shell 5,1-sessie.
Voor elke andere waarde wordt de taak uitgevoerd met de huidige versie van Power shell.

Deze para meter is toegevoegd in Power shell 7 en werkt alleen in Windows.

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

Vanaf Power shell 7 werkt de para meter **RunAs32** niet op 64-bits Power shell ( `pwsh` ).
Als **RunAs32** is opgegeven in 64-bits Power shell, wordt `Start-Job` een uitzonderings fout gegenereerd.
Als u een 32-bits Power shell ()-proces wilt starten `pwsh` met **RunAs32**, moet de 32-bits Power shell zijn geïnstalleerd.

In 32-bits Power shell zorgt **RunAs32** ervoor dat de taak wordt uitgevoerd in een 32-bits proces, zelfs op een 64-bits besturings systeem.

In 64-bits versies van Windows 7 en Windows Server 2008 R2, wanneer de `Start-Job` opdracht de para meter **RunAs32** bevat, kunt u de para meter **Credential** niet gebruiken om de referenties van een andere gebruiker op te geven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script Block

Hiermee geeft u de opdrachten op die in de achtergrond taak moeten worden uitgevoerd. Als u een script blok wilt maken, plaatst u de opdrachten in accolades ( `{}` ). Gebruik de `$input` Automatische variabele om toegang te krijgen tot de waarde van de para meter **input object** . Deze parameter is vereist.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

Hiermee geeft u het aangepaste type op voor taken die worden gestart door `Start-Job` . Voer een aangepaste taak type naam in, zoals PSScheduledJob voor geplande taken of PSWorkflowJob voor werk stroom taken. Deze para meter is niet geldig voor standaard achtergrond taken.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variabele workingdirectory

Hiermee geeft u de oorspronkelijke werkmap van de achtergrond taak op. Als de para meter niet is opgegeven, wordt de taak uitgevoerd vanaf de standaard locatie. De standaard locatie is de huidige werkmap van de aanroeper die de taak heeft gestart.

Deze para meter is geïntroduceerd in Power shell 7.

 ```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt de pijp lijn gebruiken om een object met de **naam** -eigenschap naar de para meter **name** te verzenden. U kunt bijvoorbeeld een **file info** -object uitlijnen van `Get-ChildItem` tot `Start-Job` .

## UITVOER

### System. Management. Automation. PSRemotingJob

`Start-Job` retourneert een **PSRemotingJob** -object dat de taak vertegenwoordigt die het heeft gestart.

## OPMERKINGEN

Om op de achtergrond uit te voeren, `Start-Job` wordt uitgevoerd in een eigen sessie in de huidige sessie. Wanneer u de `Invoke-Command` cmdlet gebruikt om een opdracht uit te voeren `Start-Job` in een sessie op een externe computer, `Start-Job` wordt uitgevoerd in een sessie in de externe sessie.

## GERELATEERDE KOPPELINGEN

[about_Arrays](./about/about_arrays.md)

[about_Automatic_Variables](./about/about_automatic_variables.md)

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-job](Get-Job.md)

[Invoke-opdracht](Invoke-Command.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Stoppen-taak](Stop-Job.md)

[Wait-Job](Wait-Job.md)
