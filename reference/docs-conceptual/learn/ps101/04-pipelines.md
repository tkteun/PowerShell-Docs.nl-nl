---
title: One-liners en de pijplijn
description: Een Power shell One-line is een doorlopende pijp lijn met meerdere opdrachten om één taak uit te voeren.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fd45e5e5dc408754ebac015757ef4241428978
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "84633342"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a>Hoofd stuk 4: One-Lines en de pijp lijn

Als ik Power shell voor het eerst heb gestart, heb ik dan terug naar de gebruikers interface, als ik een taak met een Power shell-One-line-instructie niet kan uitvoeren. Na verloop van tijd heb ik mijn vaardig heden ontwikkeld voor het schrijven van scripts, functies en modules. Zorg ervoor dat u geen overmatige voor beelden meer kunt zien op internet. Niemand is een natuurlijke expert met Power shell. Alle beginners worden in één keer tegelijk besproken.

Ik heb een stukje advies om gebruikers te bieden die nog steeds gebruikmaken van de GUI voor beheer: Installeer de beheer hulpprogramma's op uw beheer werkstation en beheer uw servers op afstand. Op deze manier is het niet van belang dat de server een GUI of Server Core-installatie van het besturings systeem uitvoert.
U kunt u helpen bij het voorbereiden van het extern beheren van servers met Power shell.

Net als bij vorige hoofd stukken moet u de computer van uw Windows 10-test omgeving volgen.

## <a name="one-liners"></a>One-Liners

Een Power shell One-line is een doorlopende pijp lijn en niet noodzakelijkerwijs een opdracht die zich op één fysieke lijn bevindt. Niet alle opdrachten op één fysieke regel zijn One-Lines.

Hoewel de volgende opdracht zich op meerdere fysieke regels bevindt, is het een Power shell One-line, omdat het een doorlopende pijp lijn is. Het kan op één fysieke regel worden geschreven, maar ik heb ervoor gekozen om op het pipe-symbool een regel afbreek punt te zetten. Het pipe-symbool is een van de tekens waarin een natuurlijke regel afbreeking is toegestaan in Power shell.

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

Natuurlijke lijn onderbrekingen kunnen zich voordoen bij veelgebruikte tekens, zoals komma ( `,` ) en haakjes ( `[` ), accolades () en `{` haakjes () `(` . Andere die niet algemeen zijn, bevatten de punt komma ( `;` ), is gelijk aan teken ( `=` ) en zowel dubbele aanhalings tekens openen ( `'` , `"` ).

Het `` ` `` accent teken apostroffen () of accent grave gebruiken als een regel vervolg teken is een controversieel-onderwerp. Mijn aanbeveling is om dit te voor komen als dat mogelijk is. Er worden vaak Power shell-opdrachten weer geven die zijn geschreven met behulp van een apostroffen direct na een natuurlijk regel teken.
Er is geen reden om het te zijn.

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

De opdrachten die worden weer gegeven in de vorige twee voor beelden, werken prima in de Power shell-console. Maar als u deze probeert uit te voeren in het console venster van de Power shell-ISE, wordt er een fout gegenereerd. Het console venster van de Power shell-ISE wacht niet totdat de rest van de opdracht wordt ingevoerd op de volgende regel, zoals de Power shell-console. Als u dit probleem wilt voor komen in het console venster van de Power shell-ISE, gebruikt u <kbd>SHIFT</kbd> + <kbd>Enter</kbd> in plaats van alleen op <kbd>Enter</kbd> om door te gaan met een opdracht op een andere regel.

Dit volgende voor beeld is geen Power shell One-line, omdat het niet een doorlopende pijp lijn is. Het is twee afzonderlijke opdrachten op één regel, gescheiden door een punt komma.

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Veel programmeer-en script talen vereisen een punt komma aan het einde van elke regel. Hoewel ze op die manier kunnen worden gebruikt in Power shell, wordt het niet aanbevolen, omdat ze niet nodig zijn.

## <a name="filtering-left"></a>Filters links

De resultaten van de opdrachten die in dit hoofd stuk worden weer gegeven, zijn gefilterd op een subset. `Get-Service`Is bijvoorbeeld gebruikt met de para meter **name** voor het filteren van de lijst met services die zijn geretourneerd door alleen de Windows Time-service.

In de pijp lijn wilt u de resultaten altijd filteren op wat u zo snel mogelijk op zoek bent. U kunt dit doen met behulp van para meters op de eerste opdracht of, de één helemaal links.
Dit wordt soms _filters links_ genoemd.

In het volgende voor beeld wordt de para meter **name** van gebruikt `Get-Service` om de resultaten direct te filteren op de Windows Time-service.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Het is niet ongebruikelijk om voor beelden te bekijken waarbij de opdracht wordt gebruikt om `Where-Object` de filtering uit te voeren.

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

Het eerste voor beeld filtert op de bron en retourneert alleen de resultaten voor de Windows Time-service.
In het tweede voor beeld worden alle services geretourneerd, waarna ze naar een andere opdracht worden gesluisd om het filter uit te voeren. In dit voor beeld lijkt dit mogelijk niet op een grote manier als u een query uitvoert op een lijst met Active Directory gebruikers. Weet u zeker dat u de informatie voor veel duizenden gebruikers accounts van Active Directory alleen wilt door sluizen naar een andere opdracht die ze naar een kleine subset gefiltert? Mijn aanbeveling is om altijd naar links te filteren, zelfs wanneer het niet van belang is. U kunt er ook voor zorgen dat u automatisch naar links filtert wanneer dat echt van belang is.

Ik heb een gebruiker verteld dat de volg orde waarin u de opdrachten opgeeft, niet van belang is. Dat kan niet verder van de waarheid zijn. De volg orde waarin de opdrachten worden opgegeven, is inderdaad het uitvoeren van filters. Denk bijvoorbeeld aan het scenario waarin u gebruikt `Select-Object` om slechts enkele eigenschappen te selecteren en `Where-Object` te filteren op eigenschappen die niet in de selectie zijn. In dat scenario moet het filter eerst worden uitgevoerd, anders wordt de eigenschap niet in de pijp lijn opgenomen wanneer het filteren probeert uit te voeren.

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

De opdracht in het vorige voor beeld retourneert geen resultaten omdat de eigenschap **CanStopAndContinue** niet bestaat wanneer de resultaten van `Select-Object` worden gepiped naar `Where-Object` . De betreffende eigenschap is niet geselecteerd. In essentie is het uitgefilterd. De volg orde van `Select-Object` en `Where-Object` de gewenste resultaten worden gegenereerd.

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a>De pijp lijn

Zoals u hebt gezien in veel van de voor beelden die in dit boek tot nu toe zijn weer gegeven, kan de uitvoer van één opdracht vaak worden gebruikt als invoer voor een andere opdracht. In hoofd stuk 3 `Get-Member` is gebruikt om te bepalen welk type object een opdracht produceert. Hoofd stuk 3 heeft ook geleerd hoe u de para meter **parameter type** van gebruikt `Get-Command` om te bepalen welke opdrachten het type invoer hebben geaccepteerd, maar niet per pijp lijn invoer.

Afhankelijk van hoe uitgebreide opdrachten in de Help zijn, kan dit een sectie voor **invoer** en **uitvoer** bevatten.

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

Alleen de relevante sectie van de Help wordt weer gegeven in de vorige resultaten. Zoals u ziet, wordt in de sectie **invoer** aangegeven dat een **ServiceController** of een **teken reeks** object naar de cmdlet kan worden gepiped `Stop-Service` . U weet niet welke para meters dit type invoer accepteren. Een van de eenvoudigste manieren om deze informatie te bepalen, is door de verschillende para meters in de volledige versie van de Help voor de cmdlet te bekijken `Stop-Service` .

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

Daarna hebt u alleen het relevante gedeelte van de Help weer gegeven in de vorige set resultaten. U ziet dat de para meter **DisplayName** geen pijplijn invoer accepteert, de para meter **input object** accepteert invoer **van** de pijp lijn met de waarde voor **ServiceController** -objecten en de para meter **name** accepteert invoer van de pijp lijn **met waarde** voor **teken reeks** objecten. Het accepteert ook pijplijn invoer **per eigenschaps naam**.

Wanneer een para meter invoer van de pijp lijn accepteert door de naam van de eigenschap en op waarde, wordt altijd eerst de **waarde** geprobeerd. Als de **waarde** mislukt, wordt geprobeerd de **naam van de eigenschap**. **Op waarde** is een beetje misleidende. Ik wil het nummer aanroepen **op type**. Dit betekent dat als u de resultaten van een opdracht die een **ServiceController** -object type produceert `Stop-Service` , de-invoer verbindt met de para meter **input object** . Maar als u de resultaten van een opdracht die **teken reeks** uitvoer produceert, in de pipet `Stop-Service` , wordt deze aan de para meter **name** gebonden. Als u de resultaten van een opdracht pipet die geen **ServiceController** of **teken reeks** object produceert `Stop-Service` , maar deze uitvoer een eigenschap met de naam **name** produceert, wordt de eigenschap **name** van de uitvoer met de para meter **name** van weer gegeven `Stop-Service` .

Bepaal welk type uitvoer de `Get-Service` opdracht produceert.

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

`Get-Service` Hiermee wordt een ServiceController-object type gegenereerd.

Zoals u eerder in de Help hebt gezien, accepteert de para meter **input object** van `Stop-Service` **ServiceController** -objecten via de pijp lijn **op waarde** (per type). Dit betekent dat wanneer de resultaten van de `Get-Service` cmdlet worden gepiped naar `Stop-Service` , ze zijn verbonden met de para meter **input object** van `Stop-Service` .

```powershell
Get-Service -Name w32time | Stop-Service
```

Probeer nu teken reeks invoer. Pipe `w32time` om te `Get-Member` bevestigen dat het een teken reeks is.

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

Zoals eerder in de Help wordt weer gegeven, kan een teken reeks worden `Stop-Service` gekoppeld aan de **waarde** van de para meter **name** van `Stop-Service` . Test dit door sluizen `w32time` naar `Stop-Service` .

```powershell
'w32time' | Stop-Service
```

In het vorige voor beeld gebruikte ik enkele aanhalings tekens rond de teken reeks `w32time` . In Power shell moet u altijd enkele aanhalings tekens gebruiken in plaats van een dubbele aanhalings teken, tenzij de inhoud van de reeks aanhalings tekens een variabele bevat die moet worden uitgevouwen naar de werkelijke waarde. Door gebruik te maken van enkele aanhalings tekens is het niet mogelijk om de inhoud binnen de aanhalings tekens te parseren zodat uw code iets sneller wordt uitgevoerd.

Maak een aangepast object om de invoer van de pijp lijn te testen op naam van eigenschap voor de para meter **name** van `Stop-Service` .

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

De inhoud van de variabele **CustomObject** is een object type **PSCustomObject** en bevat een eigenschap met de naam **naam**.

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

Als u de variabele wilt omgeven `$CustomObject` door aanhalings tekens, wilt u dubbele aanhalings tekens gebruiken.
Anders wordt met enkele aanhalings tekens de letterlijke teken reeks in `$CustomObject` `Get-Member` plaats van de waarde die is opgenomen door de variabele.

Hoewel de inhoud van de `$CustomObject` `Stop-Service` cmdlet wordt gekoppeld aan de para meter **name** , wordt deze keer door de **naam** van de eigenschap gebonden, in plaats van **met waarde** , omdat de inhoud van `$CustomObject` een object is dat een eigenschap met de naam **name** heeft.

In dit voor beeld maakt u een ander aangepast object met behulp van een andere eigenschaps naam, zoals de **service**.

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

Er wordt een fout gegenereerd bij het `$CustomObject` maken van een pipe naar `Stop-Service` , omdat deze geen **ServiceController** of **teken reeks** object produceert en geen eigenschap met de naam **name** heeft.

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

Als de uitvoer van één opdracht niet wordt uitgelijnd met de invoer opties voor de pijp lijn voor een andere opdracht, `Select-Object` kan worden gebruikt om de naam van de eigenschap te wijzigen zodat de eigenschappen correct worden genoteerd.

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

In dit voor beeld `Select-Object` is gebruikt om de naam van de **service** -eigenschap te wijzigen in een eigenschap met de naam **name**.

De syntaxis van dit voor beeld lijkt eerst iets ingewikkeld. Wat ik heb geleerd, is dat u de syntaxis nooit leert door code te kopiëren en te plakken. Neem de tijd om de code in te typen. Na een paar keer wordt het tweede karakter. Het gebruik van meerdere monitors is een enorm voor deel omdat u de voorbeeld code op één scherm kunt weer geven en deze op een andere op een andere pagina typt.

Soms wilt u een para meter gebruiken waarvoor geen pijplijn invoer wordt geaccepteerd. In het volgende voor beeld ziet u de uitvoer van een opdracht als invoer voor een andere. Sla de weergave naam voor een aantal Windows-services eerst op in een tekst bestand.

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

U kunt de opdracht uitvoeren die de benodigde uitvoer tussen haakjes levert als de waarde voor de para meter van de opdracht die de invoer vereist.

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

Dit is net als de volg orde van de bewerkingen in algebra voor degene die weet hoe het werkt. De opdracht tussen haakjes wordt altijd uitgevoerd vóór het buitenste gedeelte van de opdracht.

## <a name="powershellget"></a>PowerShellGet

PowerShellGet is een Power shell-module met opdrachten voor het detecteren, installeren, publiceren en bijwerken van Power shell-modules (en andere artefacten) van of naar een NuGet-opslag plaats. PowerShellGet wordt geleverd met Power shell versie 5,0 en hoger. Het is beschikbaar als afzonderlijke down load voor Power shell versie 3,0 en hoger.

Micro soft host een online NuGet-opslag plaats met de naam [PowerShell Gallery][]. Hoewel deze opslag plaats wordt gehost door micro soft, wordt het meren deel van de modules in de opslag plaats niet door micro soft geschreven. Code verkrijgen van de PowerShell Gallery moet grondig worden geëvalueerd in een geïsoleerde test omgeving voordat ze geschikt zijn voor gebruik in een productie omgeving.

De meeste bedrijven willen hun eigen interne persoonlijke NuGet-opslag plaats hosten, waar ze hun intern gebruik alleen modules kunnen plaatsen, evenals modules die ze hebben gedownload van andere bronnen zodra ze ze als niet-schadelijk hebben gevalideerd.

Gebruik de `Find-Module` cmdlet die deel uitmaakt van de PowerShellGet-module om een module te vinden in de PowerShell Gallery die ik heb geschreven met de naam MrToolkit.

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

De eerste keer dat u een van de opdrachten uit de PowerShellGet-module gebruikt, wordt u gevraagd om de NuGet-provider te installeren.

Als u de MrToolkit-module wilt installeren, pipet u de vorige opdracht naar `Install-Module` .

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

Omdat de PowerShell Gallery een niet-vertrouwde opslag plaats is, wordt u gevraagd om de installatie van de module goed te keuren.

## <a name="finding-pipeline-input-the-easy-way"></a>Pijp lijn invoer op eenvoudige wijze zoeken

De MrToolkit-module bevat een functie met de naam `Get-MrPipelineInput` . Met deze cmdlet kunt u eenvoudig bepalen welke para meters van een opdracht pijplijn invoer accepteren, welk type object ze accepteren en of ze de invoer van de pijp lijn **op waarde** of **eigenschaps naam** accepteren.

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

Zoals u kunt zien, kunnen dezelfde gegevens die we eerder hebben bepaald door de Help-informatie, gemakkelijk worden bepaald met deze functie.

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u meer informatie over Power shell-One-Lines geleerd. U hebt geleerd dat het aantal fysieke regels waarop een opdracht zich bevindt, niets hoeft te doen, ongeacht of het een Power shell-regel is. U hebt ook geleerd over filteren links, de pijp lijn en PowerShellGet.

## <a name="review"></a>Beoordelen

1. Wat is een Power shell One-line?
1. Wat zijn de tekens waar natuurlijke lijn onderbrekingen kunnen voor komen in Power shell?
1. Waarom moet u het filter verlaten?
1. Wat zijn de twee manieren waarop een Power shell-opdracht pijplijn invoer kan accepteren?
1. Waarom moet u de opdrachten in de PowerShell Gallery niet vertrouwen?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

- [about_Pipelines][]
- [about_Command_Syntax][]
- [about_Parameters][]
- [PowerShellGet: de grote eenvoudige manier om Power shell-modules te detecteren, te installeren en bij te werken][psget]

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell Gallery]: https://www.powershellgallery.com/
