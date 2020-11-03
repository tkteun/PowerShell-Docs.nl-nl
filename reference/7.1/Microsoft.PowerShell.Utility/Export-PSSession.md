---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 2fda80c934db3e868f0e49e131e6721c7b899f7c
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "93251435"
---
# Export-PSSession

## SAMENVATTING

Exporteert opdrachten vanuit een andere sessie en slaat ze op in een Power shell-module.

## SYNTAXIS

### Alles

```
Export-PSSession [-OutputModule] <String> [-Force] [-Encoding <Encoding>]
 [[-CommandName] <String[]>] [-AllowClobber] [-ArgumentList <Object[]>]
 [-CommandType <CommandTypes>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-FormatTypeName] <String[]>] [-Certificate <X509Certificate2>] [-Session] <PSSession>
 [<CommonParameters>]
```

## BESCHRIJVING

De `Export-PSSession` cmdlet haalt cmdlets, functies, aliassen en andere opdracht typen van een andere Power shell-sessie (PSSession) op een lokale of externe computer op en slaat ze op in een Power shell-module. Gebruik de cmdlet om de opdrachten van de module toe te voegen aan de huidige sessie `Import-Module` .

In tegens telling tot `Import-PSSession` , waarmee opdrachten vanuit een andere PSSession worden geïmporteerd in de huidige sessie, `Export-PSSession` worden de opdrachten in een module opgeslagen. De opdrachten worden niet in de huidige sessie geïmporteerd.

Voor het exporteren van opdrachten gebruikt u de `New-PSSession` cmdlet om een PSSession te maken met de opdrachten die u wilt exporteren. Gebruik vervolgens de `Export-PSSession` cmdlet om de opdrachten te exporteren.

Om conflicten met opdracht namen te voor komen, is de standaard instelling voor het `Export-PSSession` exporteren van alle opdrachten, met uitzonde ring van opdrachten die voor komen in de huidige sessie. U kunt de para meter **opdrachtnaam** gebruiken om de opdrachten op te geven die moeten worden geëxporteerd.

De `Export-PSSession` cmdlet maakt gebruik van de impliciete externe functie van Power shell. Wanneer u opdrachten in de huidige sessie importeert, worden deze impliciet uitgevoerd in de oorspronkelijke sessie of in een vergelijk bare sessie op de oorspronkelijke computer.

## VOORBEELDEN

### Voor beeld 1: opdrachten van een PSSession exporteren

In dit voor beeld wordt een nieuwe PSSession van de lokale computer gemaakt op de Server01-computer. Alle opdrachten, behalve die in de huidige sessie, worden geëxporteerd naar de module met de naam Server01 op de lokale computer. De export bevat de opmaak gegevens voor de opdrachten.

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

`New-PSSession`Met de opdracht maakt u een PSSession op de Server01-computer. De PSSession wordt opgeslagen in de `$S` variabele. De `Export-PSSession` opdracht exporteert de `$S` opdrachten van de variabele en formatteert gegevens in de Server01-module.

### Voor beeld 2: de opdrachten Get en set exporteren

In dit voor beeld worden alle- `Get` en- `Set` opdrachten van een server geëxporteerd.

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

Met deze opdrachten exporteert `Get` `Set` u de opdrachten en van een micro soft Exchange Server-module op een externe computer naar een Exchange-module in de `$PSHOME\Modules` map op de lokale computer.
Als de module in de `$PSHOME\Modules` Directory wordt geplaatst, is deze toegankelijk voor alle gebruikers van de computer.

### Voor beeld 3: opdrachten van een externe computer exporteren

In dit voor beeld worden de cmdlets van een PSSession op een externe computer geëxporteerd en opgeslagen in een module op de lokale computer. De cmdlets van de module worden toegevoegd aan de huidige sessie, zodat ze kunnen worden gebruikt.

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

Met de `New-PSSession` opdracht maakt u een PSSession op de Server01-computer en slaat u deze op in de `$S` variabele. De `Export-PSSession` opdracht exporteert de cmdlets waarvan de naam begint met testen van de PSSession in `$S` naar de TestCmdlets-module op de lokale computer.

De `Remove-PSSession` cmdlet verwijdert de PSSession `$S` uit de huidige sessie. Met deze opdracht wordt aangegeven dat de PSSession niet actief moet zijn om de opdrachten te gebruiken die uit de sessie zijn geïmporteerd. De `Import-Module` cmdlet voegt de cmdlets in de TestCmdlets-module toe aan de huidige sessie. De opdracht kan op elk gewenst moment in elke sessie worden uitgevoerd.

De `Get-Help` cmdlet krijgt Help-informatie voor cmdlets waarvan de naam begint met testen. Nadat de opdrachten in een module aan de huidige sessie zijn toegevoegd, kunt u de `Get-Help` `Get-Command` cmdlets en gebruiken om meer te weten te komen over de geïmporteerde opdrachten. De `Test-Files` cmdlet is geëxporteerd van de Server01-computer en aan de sessie toegevoegd. De `Test-Files` cmdlet wordt uitgevoerd in een externe sessie op de computer van waaruit de opdracht is geïmporteerd. Power Shell maakt een sessie van informatie die is opgeslagen in de TestCmdlets-module.

### Voor beeld 4: opdrachten in de huidige sessie exporteren en Clobber

In dit voor beeld worden opdrachten geëxporteerd die in een variabele zijn opgeslagen in de huidige sessie.

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

Met deze `Export-PSSession` opdracht worden alle opdrachten en alle opmaak gegevens van de PSSession in de `$S` variabele geëxporteerd naar de huidige sessie. De para meter **AllowClobber** bevat opdrachten met dezelfde namen als opdrachten in de huidige sessie.

### Voor beeld 5: opdrachten van een gesloten PSSession exporteren

In dit voor beeld ziet u hoe u de geëxporteerde opdrachten uitvoert met speciale opties wanneer de PSSession die de geëxporteerde opdrachten heeft gemaakt, is gesloten.

Als de oorspronkelijke externe sessie wordt gesloten wanneer een module wordt geïmporteerd, wordt in de module een open externe sessie gebruikt die verbinding maakt met de oorspronkelijke computer. Als er geen huidige sessie naar de oorspronkelijke computer is, wordt een sessie door de module opnieuw tot stand gebracht.

Als u geëxporteerde opdrachten met speciale opties wilt uitvoeren in een externe sessie, moet u een externe sessie met die opties maken voordat u de module importeert. De `New-PSSession` cmdlet gebruiken met de para meter **SessionOption**

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

De `New-PSSessionOption` cmdlet maakt een **PSSessionOption** -object en slaat het object op in de `$Options` variabele. `New-PSSession`Met de opdracht maakt u een PSSession op de Server01-computer.
De para meter **SessionOption** maakt gebruik van het object dat is opgeslagen in `$Options` . De sessie wordt opgeslagen in de `$S` variabele.

De `Export-PSSession` cmdlet exporteert opdrachten van de PSSession in `$S` naar de Server01-module.
De `Remove-PSSession` cmdlet verwijdert de PSSession in de `$S` variabele.

De `New-PSSession` cmdlet maakt een nieuwe PSSession die verbinding maakt met de Server01-computer. De para meter **SessionOption** maakt gebruik van het object dat is opgeslagen in `$Options` . `Import-Module`Met de cmdlet worden de opdrachten uit de Server01-module geïmporteerd. De opdrachten in de module worden uitgevoerd in de PSSession op de Server01-computer.

## PARAMETERS

### -AllowClobber

Exporteert de opgegeven opdrachten, zelfs als ze dezelfde namen hebben als opdrachten in de huidige sessie.

Als u een opdracht exporteert met dezelfde naam als een opdracht in de huidige sessie, worden de oorspronkelijke opdrachten verborgen of vervangen door de geëxporteerde opdracht. Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)voor meer informatie.

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

Exporteert de variant van de opdracht die het resultaat is van het gebruik van de opgegeven argumenten (parameter waarden).

Als u bijvoorbeeld de variant van de `Get-Item` opdracht in het certificaat (CERT:) wilt exporteren, in het PSSession-station in `$S` , typt u `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .

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

Hiermee geeft u het client certificaat op dat wordt gebruikt voor het ondertekenen van de indelings bestanden (* .Format.ps1XML) of script module bestanden (. psm1) in de module die `Export-PSSession` wordt gemaakt. Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.

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

Exporteert alleen de opdrachten met de opgegeven namen of naam patronen. Joker tekens zijn toegestaan. Gebruik de **naam** van de **opdracht** of de alias.

`Export-PSSession`Exporteert standaard alle opdrachten van de PSSession, met uitzonde ring van opdrachten die dezelfde namen hebben als opdrachten in de huidige sessie. Zo voor komt u dat opdrachten worden verborgen of vervangen door opdrachten in de huidige sessie. Gebruik de para meter **AllowClobber** om alle opdrachten te exporteren, zelfs wanneer deze andere opdrachten verbergen of vervangen.

Als u de para meter **opdrachtnaam** gebruikt, worden de opmaak bestanden voor de opdrachten niet geëxporteerd, tenzij u de para meter **FormatTypeName** gebruikt. Ook als u de para meter **FormatTypeName** gebruikt, worden er geen opdrachten geëxporteerd, tenzij u de para meter **opdrachtnaam** gebruikt.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### -CommandType

Exporteert alleen de opgegeven typen opdracht objecten. Gebruik **CommandType** of de alias, **Typ**.

De acceptabele waarden voor deze para meter zijn als volgt:

- Toe. Alle Power shell-aliassen in de huidige sessie.
- Hele. Alle opdracht typen. Het is het equivalent van `Get-Command -Name *` .
- Modules. Alle bestanden met uitzonde ring van Power Shell-bestanden in paden die worden vermeld in de Path-omgevings variabele ( `$env:path` ), inclusief. txt,. exe en. dll-bestanden.
- Cmdlet. De cmdlets in de huidige sessie. Cmdlet is de standaard waarde.
- Configuratie. Een Power shell-configuratie. Zie [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)voor meer informatie.
- ExternalScript. Alle. ps1-bestanden in de paden die worden vermeld in de Path-omgevings variabele ( `$env:path` ).
- Filter en functie. Alle Power shell-functies.
- Schriften. Script blokken in de huidige sessie.
- Workflowconfiguraties. Een Power shell-werk stroom. Zie [about_Workflows](/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1)voor meer informatie.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Hiermee geeft u het type code ring voor het doel bestand op. De standaardwaarde is `utf8NoBOM`.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).
- `bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.
- `bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.
- `oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.
- `unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- `utf7`: Wordt gecodeerd in de indeling UTF-7.
- `utf8`: Wordt gecodeerd in UTF-8-indeling.
- `utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)
- `utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)
- `utf32`: Gecodeerd in UTF-32-indeling.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Overschrijft een of meer bestaande uitvoer bestanden, zelfs als het bestand het kenmerk alleen-lezen heeft.

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

Exporteert opmaak instructies alleen voor de opgegeven Microsoft .NET Framework typen. Voer de type namen in. `Export-PSSession`Exporteert standaard opmaak instructies voor alle .NET Framework typen die zich niet in de naam ruimte **System. Management. Automation** bevinden.

De waarde van deze para meter moet de naam van een type zijn dat wordt geretourneerd door een `Get-FormatData` opdracht in de sessie van waaruit de opdrachten worden geïmporteerd. Als u alle opmaak gegevens in de externe sessie wilt ophalen, typt u `*` .

Als u de para meter **FormatTypeName** gebruikt, worden er geen opdrachten geëxporteerd, tenzij u de para meter **opdrachtnaam** gebruikt.

Als u de para meter **opdrachtnaam** gebruikt, worden de opmaak bestanden voor de opdrachten niet geëxporteerd, tenzij u de para meter **FormatTypeName** gebruikt.

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

Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten.
Zie de sectie opmerkingen van de [ModuleSpecification-constructor (hashtabel)](https://msdn.microsoft.com/library/jj136290).

De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in een van de volgende indelingen:

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel. U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter; de twee para meters sluiten elkaar wederzijds uit.

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

Exporteert alleen de opdrachten in de opgegeven Power shell-modules en-modules. Voer de module-en module namen in. Joker tekens zijn niet toegestaan.

Zie `Import-Module` en [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputModule

Hiermee geeft u een optioneel pad en een naam voor de module gemaakt door `Export-PSSession` . Het standaardpad is `$home\Documents\WindowsPowerShell\Modules` . Deze parameter is vereist.

Als de subdirectory van de module of een van de bestanden die `Export-PSSession` al bestaan, mislukt de opdracht. Als u bestaande bestanden wilt overschrijven, gebruikt u de para meter **Force** .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie

Hiermee geeft u de PSSession op waaruit de opdrachten worden geëxporteerd. Voer een variabele in die een sessie object bevat of een opdracht waarmee een sessie object wordt opgehaald, zoals een `Get-PSSession` opdracht. Deze parameter is vereist.

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

U kunt geen objecten pipeen naar `Export-PSSession` .

## UITVOER

### System. IO. file info

`Export-PSSession` retourneert een lijst met bestanden waaruit de module bestaat die deze heeft gemaakt.

## OPMERKINGEN

`Export-PSSession` is afhankelijk van de externe infra structuur van Power shell. Als u deze cmdlet wilt gebruiken, moet de computer zijn geconfigureerd voor externe toegang. Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.

U kunt niet gebruiken `Export-PSSession` om een Power shell-provider te exporteren.

Geëxporteerde opdrachten worden impliciet uitgevoerd in de PSSession van waaruit ze zijn geëxporteerd. De details van het extern uitvoeren van de opdrachten worden volledig verwerkt door Power shell. U kunt de geëxporteerde opdrachten uitvoeren op dezelfde manier als u lokale opdrachten uitvoert.

`Export-ModuleMember` Hiermee worden gegevens vastgelegd en opgeslagen over de PSSession in de module die wordt geëxporteerd. Als de PSSession van waaruit de opdrachten zijn geëxporteerd, is gesloten wanneer u de module importeert en er geen actieve PSSessions op dezelfde computer zijn, proberen de opdrachten in de module de PSSession opnieuw te maken. Als pogingen om de PSSession opnieuw te maken mislukken, worden de geëxporteerde opdrachten niet uitgevoerd.

De sessie gegevens die `Export-ModuleMember` in de module worden vastgelegd en opgeslagen, bevatten geen sessie opties, zoals die u opgeeft in de `$PSSessionOption` Voorkeurs variabele of met behulp van de para meter **SessionOption** van de `New-PSSession` -, `Enter-PSSession` -of- `Invoke-Command` cmdlets. Als de oorspronkelijke PSSession is gesloten wanneer u de module importeert, gebruikt de module een andere PSSession naar dezelfde computer, als er een beschikbaar is. Als u wilt dat de geïmporteerde opdrachten kunnen worden uitgevoerd in een correct geconfigureerde sessie, maakt u een PSSession met de gewenste opties voordat u de module importeert.

Voor het zoeken naar de te exporteren opdrachten `Export-PSSession` gebruikt u de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-Command` in de PSSession. Voor het ophalen en opslaan van opmaak gegevens voor de opdrachten, worden de- `Get-FormatData` en- `Export-FormatData` cmdlets gebruikt. U ziet mogelijk fout berichten van `Invoke-Command` , `Get-Command` , `Get-FormatData` en `Export-FormatData` Wanneer u een opdracht uitvoert `Export-PSSession` . Daarnaast `Export-PSSession` kunt u geen opdrachten exporteren vanuit een sessie die geen-,-, `Get-Command` `Get-FormatData` `Select-Object` -en- `Get-Help` cmdlets bevat.

`Export-PSSession` gebruikt de `Write-Progress` cmdlet om de voortgang van de opdracht weer te geven. Mogelijk wordt de voortgangs balk weer geven terwijl de opdracht wordt uitgevoerd.

Geëxporteerde opdrachten hebben dezelfde beperkingen als andere externe opdrachten, waaronder het niet mogelijk is om een programma te starten met een gebruikers interface, zoals Klad blok.

Omdat Power shell-profielen niet worden uitgevoerd in PSSessions, zijn de opdrachten die door een profiel aan een sessie worden toegevoegd, niet beschikbaar voor `Export-PSSession` . Als u opdrachten uit een profiel wilt exporteren, gebruikt u een `Invoke-Command` opdracht om het profiel hand matig uit te voeren in de PSSession voordat u de opdrachten exporteert.

De module die `Export-PSSession` maakt, kan een opmaak bestand bevatten, zelfs als de opdracht geen indelings gegevens importeert. Als de opdracht geen indelings gegevens importeert, bevatten indelings bestanden die worden gemaakt geen opmaak gegevens.

## GERELATEERDE KOPPELINGEN

[about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)

[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[Import-module](../Microsoft.PowerShell.Core/Import-Module.md)

[Import-PSSession](Import-PSSession.md)

[Invoke-opdracht](../Microsoft.PowerShell.Core/Invoke-Command.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSSessionOption](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[Remove-PSSession](../Microsoft.PowerShell.Core/Remove-PSSession.md)
