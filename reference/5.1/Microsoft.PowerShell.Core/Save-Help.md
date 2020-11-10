---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 3264bdc41d43fdec55ee80514bc988b33772a792
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388515"
---
# Save-Help

## SAMENVATTING
Hiermee worden de nieuwste Help-bestanden gedownload en opgeslagen in een map van het bestands systeem.

## SYNTAXIS

### Pad (standaard)

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [<CommonParameters>]
```

### LiteralPath

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Save-Help` cmdlet downloadt de nieuwste Help-bestanden voor Power shell-modules en slaat deze op in een door u opgegeven map. Met deze functie kunt u de Help-bestanden bijwerken op computers die geen toegang hebben tot internet, en kunt u de Help-bestanden op meerdere computers eenvoudiger bijwerken.

In Windows Power Shell 3,0 heeft `Save-Help` alleen gewerkt met modules die zijn geïnstalleerd op de lokale computer. Hoewel het mogelijk is om een module te importeren vanaf een externe computer, of een verwijzing naar een **PSModuleInfo** -object te verkrijgen van een externe computer met behulp van externe communicatie met Power shell, is de eigenschap **HelpInfoUri** niet behouden en `Save-Help` werkt niet voor de Help van de externe module.

In Windows Power Shell 4,0 wordt de eigenschap **HelpInfoUri** bewaard via externe communicatie met Power shell, waardoor `Save-Help` u kunt werken met modules die op externe computers zijn geïnstalleerd. Het is ook mogelijk om een **PSModuleInfo** -object op te slaan op schijf of verwissel bare media door uit te voeren `Export-Clixml` op een computer die geen toegang heeft tot internet, het object te importeren op een computer die toegang heeft tot internet en vervolgens uit te voeren `Save-Help` op het **PSModuleInfo** -object. De opgeslagen Help kan worden getransporteerd naar de externe computer door gebruik te maken van Verwissel bare opslag media, zoals een USB-station. De Help kan worden geïnstalleerd op de externe computer door uit te voeren `Update-Help` . Dit proces kan worden gebruikt om Help te installeren op computers die geen netwerk toegang hebben.

Als u opgeslagen Help-bestanden wilt installeren, voert u de `Update-Help` cmdlet uit. Voeg de para meter **SourcePath** toe om de map op te geven waarin u de Help-bestanden hebt opgeslagen.

Zonder para meters wordt met een `Save-Help` opdracht de nieuwste Help gedownload voor alle modules in de sessie en voor modules die op de computer zijn geïnstalleerd op een locatie die wordt vermeld in de omgevings variabele **PSModulePath** . Met deze actie worden modules die niet kunnen worden bijgewerkt zonder waarschuwing, overgeslagen.

Met de `Save-Help` cmdlet wordt de versie gecontroleerd van alle Help-bestanden in de doelmap. Als nieuwere Help-bestanden beschikbaar zijn, downloadt deze cmdlet de nieuwste Help-bestanden van Internet en slaat deze vervolgens op in de map. De `Save-Help` cmdlet werkt op dezelfde manier als de `Update-Help` cmdlet, behalve dat de gedownloade cab-bestanden worden opgeslagen in plaats van de Help-bestanden uit de cabinetbestanden te extra heren en op de computer te installeren.

De opgeslagen Help voor elke module bestaat uit één Help-informatie bestand (HelpInfo XML) en één CAB-bestand (CAB) voor de Help-bestanden elke GEBRUIKERSINTERFACE cultuur. U hoeft de Help-bestanden niet uit het CAB-bestand uit te pakken. De `Update-Help` cmdlet extraheert de Help-bestanden, valideert de XML voor beveiliging en installeert vervolgens de Help-bestanden en het Help-informatie bestand in een taalspecifieke submap van de module map.

Als u de Help-bestanden voor modules in de Power shell-installatiemap () wilt opslaan `$pshome\Modules` , start u Power shell met de optie als administrator uitvoeren. U moet lid zijn van de groep Administrators op de computer om de Help-bestanden voor deze modules te downloaden.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: de Help voor de DHCP-module opslaan

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module,
# save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer
# module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

In dit voor beeld ziet u drie verschillende manieren om `Save-Help` de Help voor de **DHCP** -module op te slaan vanaf een client computer met Internet verbinding **DhcpServer** , zonder de DHCP-module of de server functie van de lokale computer te installeren.

### Voor beeld 2: Help installeren voor de DHCP-module

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the
# PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer
# module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and
# then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

In dit voor beeld ziet u hoe u Help kunt installeren die u in voor beeld 1 hebt opgeslagen voor de **DHCP** -module op een computer die geen toegang tot internet heeft.

### Voor beeld 3: Help voor alle modules opslaan

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

Met deze opdracht worden de nieuwste Help-bestanden gedownload voor alle modules in de UI-cultuur die is ingesteld voor Windows op de lokale computer. De Help-bestanden worden opgeslagen in de `\\Server01\Fileshare01` map.

### Voor beeld 4: Help voor een module op de computer opslaan

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

Met deze opdracht worden de nieuwste Help-bestanden voor de module Server **Manager** gedownload en opgeslagen in de `\\Server01\Fileshare01` map.

Wanneer een module op de computer is geïnstalleerd, kunt u de module naam als de waarde van de **module** parameter typen, zelfs als de module niet in de huidige sessie is geïmporteerd.

De opdracht gebruikt de para meter **Credential** voor het opgeven van de referenties van een gebruiker die gemachtigd is om naar de bestands share te schrijven.

### Voor beeld 5: Help voor een module op een andere computer opslaan

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

Met deze opdrachten worden de nieuwste Help-bestanden voor de **CustomSQL** -module gedownload en opgeslagen in de `\\Server01\Fileshare01` map.

Omdat de **CustomSQL** -module niet is geïnstalleerd op de computer, bevat de reeks een `Invoke-Command` opdracht die het module object voor de CustomSQL-module van de Server02-computer ophaalt en vervolgens het module object naar de `Save-Help` cmdlet sluizen.

Wanneer een module niet op de computer is geïnstalleerd, `Save-Help` heeft het module-object nodig, dat informatie bevat over de locatie van de nieuwste Help-bestanden.

### Voor beeld 6: Help voor een module in meerdere talen opslaan

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

Met deze opdracht wordt de Help voor de Power shell-kern modules in vier verschillende GEBRUIKERSINTERFACE culturen opgeslagen. De taal pakketten voor deze land instellingen hoeven niet te worden geïnstalleerd op de computer.

`Save-Help` kan Help-bestanden voor modules in verschillende GEBRUIKERSINTERFACE culturen alleen downloaden wanneer de eigenaar van de module de vertaalde bestanden beschikbaar maakt op internet.

### Voor beeld 7: Help meer dan één keer per dag opslaan

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

Met deze opdracht wordt de Help-informatie opgeslagen voor alle modules die op de computer zijn geïnstalleerd. Met de opdracht geeft u de para meter **Force** om de regel te onderdrukken waarmee wordt voor komen dat de `Save-Help` cmdlet meer dan één keer in elke periode van 24 uur Help-informatie downloadt.

De para meter **Force** overschrijft ook de beperking van 1 GB en omzeilt de versie controle.
Daarom kunt u bestanden downloaden, zelfs als de versie niet hoger is dan de versie in de doelmap.

De opdracht gebruikt de `Save-Help` cmdlet om de Help-bestanden te downloaden en op te slaan in de opgegeven map.
De para meter **Force** is vereist wanneer u een `Save-Help` opdracht meer dan één keer per dag moet uitvoeren.

## PARAMETERS

### -Credential

Hiermee geeft u een gebruikers referentie op. Met deze cmdlet wordt de opdracht uitgevoerd met behulp van referenties van een gebruiker die toegang heeft tot de bestandssysteem locatie die is opgegeven door de para meter **doelpad** . Deze para meter is alleen geldig wanneer de para meter **doelpad** of **LiteralPath** wordt gebruikt in de opdracht.

Met deze para meter kunt u `Save-Help` opdrachten uitvoeren die gebruikmaken van de para meter **doelpad** op externe computers. Door expliciete referenties op te geven, kunt u de opdracht uitvoeren op een externe computer en toegang krijgen tot een bestands share op een derde computer zonder dat er een fout wordt geweigerd of als CredSSP-verificatie wordt gebruikt voor het delegeren van referenties.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Doelpad

Hiermee geeft u het pad op van de map waarin de Help-bestanden worden opgeslagen. Geef geen bestands naam of bestands extensie op.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Geeft aan dat deze cmdlet de beperking van eenmalige per dag niet volgt, de versie controle overs laat en bestanden downloadt die de limiet van 1 GB overschrijden.

Zonder deze para meter wordt slechts één `Save-Help` opdracht voor elke module toegestaan in elke periode van 24 uur, worden down loads beperkt tot 1 GB aan ongecomprimeerde inhoud per module, en Help-bestanden voor een module worden alleen geïnstalleerd wanneer ze nieuwer zijn dan de bestanden op de computer.

De limiet van één dag beschermt de servers die als host dienen voor de Help-bestanden en maakt het u mogelijk om een opdracht toe te voegen `Save-Help` aan uw Power shell-profiel.

Als u de Help wilt opslaan voor een module in meerdere GEBRUIKERSINTERFACE culturen zonder de para meter **Force** , neemt u alle gebruikersinterface culturen op in dezelfde opdracht, zoals: `Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

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

### -LiteralPath

Hiermee geeft u een pad van de doelmap op. In tegens telling tot de waarde van de para meter **doelpad** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt. Er worden geen tekens geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

Hiermee worden modules opgegeven waarvoor deze cmdlet Help kan downloaden. Voer een of meer module namen of naam Patters in een door komma's gescheiden lijst of in een bestand met één module naam op elke regel. Joker tekens zijn toegestaan. U kunt ook module-objecten van de `Get-Module` cmdlet naar gebruiken `Save-Help` .

Standaard is `Save-Help` Dit hulp middel voor het downloaden van alle modules die ondersteuning bieden voor Help-informatie en die op de lokale computer zijn geïnstalleerd op een locatie die wordt vermeld in de omgevings variabele **PSModulePath** .

Als u Help wilt opslaan voor modules die niet op de computer zijn geïnstalleerd, voert u een `Get-Module` opdracht uit op een externe computer. Pipet vervolgens de resulterende module objecten naar de `Save-Help` cmdlet of dien de module-objecten in als de waarde van de **module** -of **input object** -para meters.

Als de module die u opgeeft op de computer is geïnstalleerd, kunt u de module naam of een module-object invoeren. Als de module niet op de computer is geïnstalleerd, moet u een module object invoeren, zoals het item dat door de `Get-Module` cmdlet wordt geretourneerd.

De **module** parameter van de `Save-Help` cmdlet accepteert niet het volledige pad van een module bestand of module manifest bestand. Als u Help wilt opslaan voor een module die zich niet in een **PSModulePath** -locatie bevindt, importeert u de module in de huidige sessie voordat u de `Save-Help` opdracht uitvoert.

De waarde ' * ' (alle) probeert de Help bij te werken voor alle modules die op de computer zijn geïnstalleerd.
Dit omvat modules die geen ondersteuning bieden voor bijwerk bare Help. Deze waarde kan fouten genereren wanneer de opdracht modules detecteert die geen ondersteuning bieden voor bijwerk bare Help.

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -UICulture

Hiermee geeft u de UI-cultuur waarden op waarvoor met deze cmdlet bijgewerkte Help-bestanden worden opgehaald. Voer een of meer taal codes in, zoals `es-ES` een variabele die cultuur objecten bevat of een opdracht die cultuur objecten, zoals een of-opdracht, `Get-Culture` ophalen `Get-UICulture` .

Joker tekens zijn niet toegestaan. Geef geen gedeeltelijke taal code op, zoals ' de '.

Hiermee worden standaard `Save-Help` Help-bestanden in de UI-cultuur ingesteld voor Windows of de terugval cultuur.
Als u de para meter **uiCulture** opgeeft, `Save-Help` zoekt alleen naar de opgegeven gebruikersinterface cultuur, niet in een terugval cultuur.

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd, met inbegrip van het downloaden van het web, met de referenties van de huidige gebruiker. Standaard wordt de opdracht uitgevoerd zonder expliciete referenties.

Deze para meter is alleen effectief als de webdownload gebruikmaakt van NTLM-, Negotiate-of Kerberos-verificatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSModuleInfo

U kunt een module-object vanuit de `Get-Module` cmdlet door sluizen naar de **module** parameter van `Save-Help` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

- Als u Help voor modules wilt opslaan in de map $pshome \Modules, start u Power shell met de optie als administrator uitvoeren. Alleen leden van de groep Administrators op de computer kunnen Help voor modules downloaden in de map $pshome \Modules.
- De opgeslagen Help voor elke module bestaat uit één Help-informatie bestand (HelpInfo XML) en één CAB-bestand (CAB) voor de Help-bestanden elke GEBRUIKERSINTERFACE cultuur. U hoeft de Help-bestanden niet uit het CAB-bestand uit te pakken. De `Update-Help` cmdlet extraheert de Help-bestanden, valideert de XML en installeert vervolgens de Help-bestanden en het Help-informatie bestand in een taalspecifieke submap van de module map.
- `Save-Help`Met de cmdlet kunt u Help opslaan voor modules die niet op de computer zijn geïnstalleerd. Omdat Help-bestanden echter worden geïnstalleerd in de map module, `Update-Help` kan de cmdlet alleen een bijgewerkt Help-bestand installeren voor modules die op de computer zijn geïnstalleerd.
- Als `Save-Help` u geen bijgewerkte Help-bestanden voor een module kunt vinden of als u geen bijgewerkte Help-bestanden kunt vinden in de opgegeven taal, wordt deze op de achtergrond voortgezet zonder dat er een fout bericht wordt weer gegeven. Geef de para meter **uitgebreid** op om te zien welke bestanden zijn opgeslagen met de opdracht.
- Modules zijn de kleinste eenheid van Help die kan worden bijgewerkt. U kunt geen Help-informatie voor een bepaalde cmdlet opslaan, alleen voor alle cmdlets in de module. Als **u de module** wilt vinden die een bepaalde cmdlet bevat, gebruikt u de eigenschap PropertyName in combi natie met de `Get-Command` cmdlet, bijvoorbeeld `(Get-Command \<cmdlet-name\>).ModuleName`
- `Save-Help` ondersteunt alle modules en de Power shell core-modules. Andere modules worden niet ondersteund.
- De `Update-Help` `Save-Help` cmdlets en gebruiken de volgende poorten om Help-bestanden te downloaden: poort 80 voor http en poort 443 voor HTTPS.
- De `Update-Help` `Save-Help` cmdlets en worden niet ondersteund op Windows Preinstallation Environment (Windows PE).

## GERELATEERDE KOPPELINGEN

[Get-Help](Get-Help.md)

[Get-module](Get-Module.md)

[Update-Help](Update-Help.md)
