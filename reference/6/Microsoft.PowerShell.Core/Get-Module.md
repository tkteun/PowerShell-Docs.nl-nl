---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 5dfc21a4586b5af8ab436177dd1e5be33380e6f2
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387478"
---
# Get-Module

## SAMENVATTING
Hiermee worden de modules opgehaald die zijn geïmporteerd of die in de huidige sessie kunnen worden geïmporteerd.

## SYNTAXIS

### Geladen (standaard)

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### Beschikbaar

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### PsSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### CimSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Module` cmdlet haalt de Power shell-modules die zijn geïmporteerd of die kunnen worden geïmporteerd, op in een Power shell-sessie. Het module-object dat `Get-Module` retourneert, bevat waardevolle informatie over de module. U kunt de module-objecten ook door sluizen naar andere cmdlets, zoals de- `Import-Module` en- `Remove-Module` cmdlets.

Zonder para meters worden `Get-Module` modules opgehaald die in de huidige sessie zijn geïmporteerd. Geef de para meter **ListAvailable** op om alle geïnstalleerde modules op te halen.

`Get-Module` Hiermee worden modules opgehaald, maar niet geïmporteerd. Vanaf Windows Power Shell 3,0 worden modules automatisch geïmporteerd wanneer u een opdracht in de module gebruikt, maar met een `Get-Module` opdracht wordt een automatische import bewerking niet geactiveerd. U kunt de modules ook importeren in uw-sessie met behulp van de- `Import-Module` cmdlet.

Vanaf Windows Power Shell 3,0 kunt u modules ophalen en vervolgens importeren van externe sessies in de lokale sessie. Deze strategie maakt gebruik van de impliciete externe functie van Power shell en komt overeen met het gebruik van de `Import-PSSession` cmdlet. Wanneer u opdrachten gebruikt in modules die vanuit een andere sessie worden geïmporteerd, worden de opdrachten impliciet uitgevoerd in de externe sessie. Met deze functie kunt u de externe computer vanuit de lokale sessie beheren.

Met ingang van Windows Power Shell 3,0 kunt u ook `Get-Module` `Import-Module` de modules van Common Information Model (CIM) gebruiken en weer geven, waarin de cmdlets worden gedefinieerd in de CMDLET definition XML-bestanden (CDXML). Met deze functie kunt u cmdlets gebruiken die zijn geïmplementeerd in niet-beheerde code-assembly's, zoals die zijn geschreven in C++.

Met deze nieuwe functies worden de- `Get-Module` en- `Import-Module` cmdlets primaire hulp middelen voor het beheren van heterogene ondernemingen die computers bevatten waarop het Windows-besturings systeem wordt uitgevoerd en computers met andere besturings systemen.

Als u externe computers wilt beheren waarop het Windows-besturings systeem wordt uitgevoerd en externe communicatie van Power shell is ingeschakeld, maakt u een **PSSession** op de externe computer en gebruikt u vervolgens de para meter **PSSession** van `Get-Module` om de Power shell-modules op te halen in de **PSSession**. Wanneer u de modules importeert en vervolgens de geïmporteerde opdrachten in de huidige sessie gebruikt, worden de opdrachten impliciet uitgevoerd in de **PSSession** op de externe computer. U kunt deze strategie gebruiken om de externe computer te beheren.

U kunt een vergelijk bare strategie gebruiken voor het beheren van computers waarop geen externe communicatie van Power shell is ingeschakeld.
Dit zijn onder andere computers waarop het Windows-besturings systeem niet wordt uitgevoerd en computers met Power shell, maar waarvoor geen externe communicatie van Power shell is ingeschakeld.

Maak eerst een CIM-sessie op de externe computer. Een CIM-sessie is een verbinding met Windows Management Instrumentation (WMI) op de externe computer. Gebruik vervolgens de para meter **CIMSession** van `Get-Module` om CIM-modules op te halen uit de CIM-sessie. Wanneer u een CIM-module importeert met behulp van de- `Import-Module` cmdlet en vervolgens de geïmporteerde opdrachten uitvoert, worden de opdrachten impliciet uitgevoerd op de externe computer. U kunt deze WMI-en CIM-strategie gebruiken om de externe computer te beheren.

## VOORBEELDEN

### Voor beeld 1: modules ophalen die in de huidige sessie zijn geïmporteerd

```powershell
Get-Module
```

Met deze opdracht worden modules opgehaald die in de huidige sessie zijn geïmporteerd.

### Voor beeld 2: geïnstalleerde modules en beschik bare modules ophalen

```powershell
Get-Module -ListAvailable
```

Met deze opdracht worden de modules opgehaald die op de computer zijn geïnstalleerd en die in de huidige sessie kunnen worden geïmporteerd.

`Get-Module` zoekt naar beschik bare modules in het pad dat is opgegeven door de omgevings variabele **$env:P smodulepath** . Zie [about_Modules](About/about_Modules.md) en [about_Environment_Variables](About/about_Environment_Variables.md)voor meer informatie over **PSModulePath**.

### Voor beeld 3: alle geëxporteerde bestanden ophalen

```powershell
Get-Module -ListAvailable -All
```

Met deze opdracht worden alle geëxporteerde bestanden voor alle beschik bare modules opgehaald.

### Voor beeld 4: een module ophalen met de volledig gekwalificeerde naam

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

Met deze opdracht wordt de module **micro soft. Power shell. Management** opgehaald door de volledig gekwalificeerde naam van de module op te geven met behulp van de para meter **FullyQualifiedName** . De opdracht Pipet de resultaten vervolgens `Format-Table` naar de cmdlet om de resultaten op te maken als een tabel met de **naam** en **versie** als kolom koppen.

### Voor beeld 5: eigenschappen van een module ophalen

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

Met deze opdracht worden de eigenschappen opgehaald van het **PSModuleInfo** -object dat `Get-Module` retourneert. Er is één object voor elk module bestand.

U kunt de eigenschappen gebruiken om de module-objecten te Format teren en te filteren. Zie [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo)(Engelstalig) voor meer informatie over de eigenschappen.

De uitvoer bevat de nieuwe eigenschappen, zoals **Auteur** en **CompanyName** , die zijn geïntroduceerd in Windows Power Shell 3,0.

### Voor beeld 6: alle modules op naam groeperen

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

Met deze opdracht worden alle module bestanden, zowel geïmporteerd als beschikbaar, opgehaald en vervolgens gegroepeerd op module naam. Zo kunt u de module bestanden zien die elk script exporteert.

### Voor beeld 7: de inhoud van een module manifest weer geven

Met deze opdrachten wordt de inhoud van het module manifest voor de Windows Power shell **BitsTransfer** -module weer gegeven.

Modules hoeven geen manifest bestanden te bevatten. Wanneer ze een manifest bestand hebben, is het manifest bestand alleen vereist voor het toevoegen van een versie nummer. Manifest bestanden bevatten echter vaak nuttige informatie over een module, de vereisten en de inhoud ervan.

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

Met de eerste opdracht wordt het PSModuleInfo-object opgehaald dat de BitsTransfer-module vertegenwoordigt. Hiermee wordt het object in de `$m` variabele opgeslagen.

Met de tweede opdracht wordt de `Get-Content` cmdlet gebruikt om de inhoud van het manifest bestand in het opgegeven pad op te halen. De teken punt notatie wordt gebruikt om het pad naar het manifest bestand op te halen dat is opgeslagen in de eigenschap Path van het object. De uitvoer toont de inhoud van het module manifest.

### Voor beeld 8: bestanden in de module directory weer geven

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

Met deze opdracht worden de bestanden in de map van de module weer gegeven. Dit is een andere manier om te bepalen wat zich in een module bevindt voordat u deze importeert. Sommige modules hebben mogelijk Help-bestanden of leesmij-bestanden waarin de module wordt beschreven.

### Voor beeld 9: modules ophalen die op een computer zijn geïnstalleerd

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

Met deze opdrachten worden de modules opgehaald die zijn geïnstalleerd op de Server01-computer.

De eerste opdracht gebruikt de `New-PSSession` cmdlet om een **PSSession** te maken op de Server01-computer. Met de opdracht slaat u de **PSSession** op in de variabele $s.

De tweede opdracht maakt gebruik van de **PSSession** -en **ListAvailable** -para meters van `Get-Module` om de modules in de **PSSession** in de variabele op te halen `$s` .

Als u modules van andere sessies naar de cmdlet pipet `Import-Module` , `Import-Module` importeert de module in de huidige sessie met behulp van de functie impliciete externe toegang. Dit is gelijk aan het gebruik van de `Import-PSSession` cmdlet. U kunt de-cmdlets uit de module in de huidige sessie gebruiken, maar met opdrachten die gebruikmaken van deze cmdlets wordt de externe sessie daad werkelijk uitgevoerd. Zie en voor meer informatie [`Import-Module`](Import-Module.md) [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md) .

### Voor beeld 10: een computer beheren waarop het Windows-besturings systeem niet wordt uitgevoerd

Met de opdrachten in dit voor beeld kunt u de opslag systemen beheren van een externe computer waarop het Windows-besturings systeem niet wordt uitgevoerd.
In dit voor beeld, omdat de beheerder van de computer de WMI-provider voor module detectie heeft geïnstalleerd, kunnen de CIM-opdrachten de standaard waarden gebruiken die zijn ontworpen voor de provider.

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

De eerste opdracht gebruikt de `New-CimSession` cmdlet om een sessie te maken op de externe computer RSDGF03. De sessie maakt verbinding met WMI op de externe computer. Met de opdracht wordt de CIM-sessie in de `$cs` variabele opgeslagen.

Met de tweede opdracht wordt de CIM-sessie in de `$cs` variabele gebruikt om een opdracht uit te voeren `Get-Module` op de RSDGF03-computer. De opdracht gebruikt de para meter name om de opslag module op te geven. De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van de opslag module naar de `Import-Module` cmdlet, die deze in de lokale sessie importeert.

Met de derde opdracht voert u de `Get-Command` cmdlet `Get-Disk` uit op de opdracht in de module opslag.
Wanneer u een CIM-module in de lokale sessie importeert, worden de CDXML-bestanden die de CIM-module vertegenwoordigen, omgezet in Power shell-scripts, die als functies in de lokale sessie worden weer gegeven.

Met de vierde opdracht voert u de `Get-Disk` opdracht uit. Hoewel de opdracht in de lokale sessie wordt getypt, wordt deze impliciet uitgevoerd op de externe computer van waaruit deze is geïmporteerd. De opdracht haalt objecten van de externe computer op en retourneert deze naar de lokale sessie.

## PARAMETERS

### -Alle

Geeft aan dat deze cmdlet alle modules in elke module map ophaalt, inclusief geneste modules, manifest bestanden (. psd1), script module bestanden (. psm1) en binaire module bestanden (. dll). Zonder deze para meter `Get-Module` wordt alleen de standaard module in elke module map opgehaald.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimNamespace

Hiermee geeft u de naam ruimte van een alternatieve CIM-provider die CIM-modules beschikbaar stelt. De standaard waarde is de naam ruimte van de WMI-provider van de module detectie.

Gebruik deze para meter om CIM-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

Hiermee geeft u een alternatieve locatie voor CIM-modules op. De standaard waarde is de resource-URI van de module detectie WMI-provider op de externe computer.

Gebruik deze para meter om CIM-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

Hiermee geeft u een CIM-sessie op de externe computer op. Voer een variabele in die de CIM-sessie bevat of een opdracht waarmee de CIM-sessie wordt opgehaald, zoals een [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) opdracht.

`Get-Module` maakt gebruik van de verbinding met de CIM-sessie om modules van de externe computer op te halen. Wanneer u de module importeert met behulp `Import-Module` van de-cmdlet en de opdrachten uit de geïmporteerde module gebruikt in de huidige sessie, worden de opdrachten daad werkelijk uitgevoerd op de externe computer.

U kunt deze para meter gebruiken om-modules op te halen van computers en apparaten waarop het Windows-besturings systeem niet wordt uitgevoerd, en computers met Power shell, maar externe communicatie van Power shell is niet ingeschakeld.

De para meter **CimSession** haalt alle modules op in de **CimSession**. U kunt echter alleen op CIM gebaseerde en cmdlet definition XML-modules (CDXML) importeren.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten. Zie de sectie opmerkingen van de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in een van de volgende indelingen:

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel. U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter. de twee para meters sluiten elkaar wederzijds uit.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

Geeft aan dat met deze cmdlet alle geïnstalleerde modules worden opgehaald. `Get-Module` Hiermee worden modules opgehaald in paden die worden weer gegeven in de omgevings variabele **PSModulePath** . Zonder deze para meter `Get-Module` worden alleen de modules opgehaald die beide zijn opgenomen in de omgevings variabele **PSModulePath** en die worden geladen in de huidige sessie. **ListAvailable** retourneert geen informatie over modules die niet zijn gevonden in de omgevings variabele **PSModulePath** , zelfs niet als deze modules in de huidige sessie worden geladen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee worden namen of naam patronen van modules opgegeven die met deze cmdlet worden opgehaald. Joker tekens zijn toegestaan. U kunt ook de namen door sluizen naar `Get-Module` . U kunt de para meter **FullyQualifiedName** niet opgeven in dezelfde opdracht als de para meter **name** .

De **naam** kan geen module-GUID als waarde accepteren.
Gebruik **FullyQualifiedName** in plaats daarvan om modules te retour neren door een GUID op te geven.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -PSEdition

Hiermee worden de modules opgehaald die de opgegeven editie van Power shell ondersteunen.

De aanvaardbare waarden voor deze parameter zijn:

- Bureaublad
- Kern

De Get-Module-cmdlet controleert de eigenschap **CompatiblePSEditions** van het **PSModuleInfo** -object voor de opgegeven waarde en retourneert alleen de modules die het heeft ingesteld.

> [!NOTE]
>
> - **Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.
> - **Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.

```yaml
Type: System.String
Parameter Sets: Available, PsSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSSession

Hiermee worden de modules in de opgegeven door de gebruiker beheerde Power shell-sessie ( **PSSession** ) opgehaald. Voer een variabele in die de sessie bevat, een opdracht waarmee de sessie wordt opgehaald, zoals een `Get-PSSession` opdracht of een opdracht waarmee de sessie wordt gemaakt, zoals een `New-PSSession` opdracht.

Wanneer de sessie is verbonden met een externe computer, moet u de para meter **ListAvailable** opgeven.

Een `Get-Module` opdracht die gebruikmaakt van de para meter **PSSession** is gelijk aan het gebruik van de `Invoke-Command` cmdlet om een `Get-Module -ListAvailable` opdracht uit te voeren in een **PSSession**.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Vernieuwen

Geeft aan dat met deze cmdlet de cache van geïnstalleerde opdrachten wordt vernieuwd. De opdracht cache wordt gemaakt wanneer de sessie wordt gestart. Hiermee kan de `Get-Command` cmdlet opdrachten ophalen uit modules die niet in de sessie zijn geïmporteerd.

Deze para meter is bedoeld voor ontwikkelings-en test scenario's waarin de inhoud van modules is gewijzigd sinds het starten van de sessie.

Wanneer u de **vernieuwings** parameter opgeeft in een opdracht, moet u **ListAvailable** opgeven.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipEditionCheck

De controle van het veld overs Laan `CompatiblePSEditions` .

Get-Module worden standaard modules in de map wegge laten `%windir%\System32\WindowsPowerShell\v1.0\Modules` die niet `Core` in het veld zijn opgegeven `CompatiblePSEditions` .
Als deze schakel optie is ingesteld, worden modules zonder `Core` opgenomen, zodat modules onder het pad van de Windows Power shell-module die incompatibel zijn met Power shell core, worden geretourneerd.

In macOS en Linux heeft deze para meter niets.

Zie [about_PowerShell_Editions](About/about_PowerShell_Editions.md) voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt module namen door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSModuleInfo

Deze cmdlet retourneert objecten die modules vertegenwoordigen.
Wanneer u de para meter **ListAvailable** opgeeft, wordt `Get-Module` een **ModuleInfoGrouping** -object geretourneerd. Dit is een type **PSModuleInfo** -object met dezelfde eigenschappen en methoden.

## OPMERKINGEN

- Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn opgenomen in Power shell, verpakt in modules. De uitzonde ring is **micro soft. Power shell. core** , een module ( **PSSnapin** ). Standaard wordt alleen de module **micro soft. Power shell. core** toegevoegd aan de sessie.
Modules worden automatisch geïmporteerd bij het eerste gebruik en u kunt de `Import-Module` cmdlet gebruiken om ze te importeren.
- Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn geïnstalleerd met Power shell, verpakt in modules. In Windows Power Shell 2,0, en in hostgroepen die oudere sessies maken in latere versies van Power shell, worden de kern opdrachten verpakt in modules ( **PSSnapins** ). De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module. Externe sessies, zoals computers die zijn gestart door de `New-PSSession` cmdlet, zijn ook oudere sessies met kern modules.

  Zie de [methode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)voor informatie over de **CreateDefault2** -methode waarmee nieuwe-stijl sessies met kern modules worden gemaakt.

- `Get-Module` haalt alleen modules op in locaties die zijn opgeslagen in de waarde van de **PSModulePath** -omgevings variabele ($env:P smodulepath). U kunt de para meter **Path** van de `Import-Module` cmdlet gebruiken voor het importeren van modules op andere locaties, maar u kunt de cmdlet niet gebruiken `Get-Module` om deze te downloaden.
- Vanuit Power Shell 3,0 zijn er ook nieuwe eigenschappen toegevoegd aan het object, waardoor `Get-Module` het eenvoudiger wordt om te leren over modules, zelfs voordat ze worden geïmporteerd. Alle eigenschappen worden ingevuld voordat ze worden geïmporteerd. Dit zijn onder andere de eigenschappen **ExportedCommands** , **ExportedCmdlets** en **ExportedFunctions** die de opdrachten vermeld die de module exporteert.
- De para meter **ListAvailable** haalt alleen goed opgemaakte modules op, dat wil zeggen mappen die ten minste één bestand bevatten waarvan de basis naam hetzelfde is als de naam van de module map. De basis naam is de naam zonder de bestandsnaam extensie. Mappen met bestanden die verschillende namen hebben, worden beschouwd als containers, maar niet in modules.

  Als u modules wilt ophalen die als dll-bestanden zijn geïmplementeerd, maar die niet zijn opgenomen in een module-map, geeft u zowel de **ListAvailable** als **alle** para meters op.

- Als u de functie CIM-sessie wilt gebruiken, moet de externe computer beschikken over WS-Management remoting en Windows Management Instrumentation (WMI), de micro soft-implementatie van de Common Information Model (CIM)-standaard. De computer moet ook de WMI-provider voor module detectie hebben of een alternatieve WMI-provider die dezelfde basis functies heeft.

  U kunt de functie CIM-sessie gebruiken op computers waarop het Windows-besturings systeem niet wordt uitgevoerd en op Windows-computers met Power shell, maar externe communicatie van Power shell niet is ingeschakeld.

  U kunt ook de CIM-para meters gebruiken om CIM-modules op te halen van computers waarop externe communicatie van Power shell is ingeschakeld. Dit omvat de lokale computer.
Wanneer u een CIM-sessie op de lokale computer maakt, gebruikt Power shell DCOM in plaats van WMI om de sessie te maken.

## GERELATEERDE KOPPELINGEN

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[about_Modules](About/about_Modules.md)

[Get-PSSession](Get-PSSession.md)

[Import-module](Import-Module.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[New-PSSession](New-PSSession.md)

[Remove-module](Remove-Module.md)

[about_PowerShell_Editions](About/about_PowerShell_Editions.md)
