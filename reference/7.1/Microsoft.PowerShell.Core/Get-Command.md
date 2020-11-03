---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 60b6d2e380685650a86f74056a992afb4051ddc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251365"
---
# Get-Command

## SAMENVATTING
Hiermee worden alle opdrachten opgehaald.

## SYNTAXIS

### Cmdletset (standaard)

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### AllCommandSet

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [-UseAbbreviationExpansion] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Command` cmdlet haalt alle opdrachten op die zijn geïnstalleerd op de computer, zoals cmdlets, aliassen, functies, filters, scripts en toepassingen. `Get-Command` Hiermee worden de opdrachten opgehaald van Power shell-modules en-opdrachten die zijn geïmporteerd uit andere sessies. Als u alleen opdrachten wilt ophalen die in de huidige sessie zijn geïmporteerd, gebruikt u de para meter **ListImported** .

Zonder para meters worden `Get-Command` Alle cmdlets, functies en aliassen die op de computer zijn geïnstalleerd, opgehaald. `Get-Command *` Hiermee worden alle typen opdrachten opgehaald, inclusief alle niet-Power Shell-bestanden in de Path-omgevings variabele ( `$env:Path` ), die wordt vermeld in het opdracht type van de toepassing.

`Get-Command` met de exacte naam van de opdracht, zonder joker tekens, wordt automatisch de module met de opdracht geïmporteerd zodat u de opdracht direct kunt gebruiken. Als u het automatisch importeren van modules wilt in-en uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele. Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.

`Get-Command` de gegevens worden rechtstreeks opgehaald uit de opdracht code, in tegens telling tot `Get-Help` , waardoor de informatie wordt opgehaald uit de Help-onderwerpen.

Vanaf Windows Power shell 5,0 worden de resultaten van de `Get-Command` cmdlet standaard een **versie** kolom weer gegeven. Er is een nieuwe **versie** -eigenschap toegevoegd aan de klasse **CommandInfo** .

## VOORBEELDEN

### Voor beeld 1: cmdlets, functies en aliassen ophalen

Met deze opdracht worden de Power shell-cmdlets, functies en aliassen opgehaald die op de computer zijn geïnstalleerd.

```powershell
Get-Command
```

### Voor beeld 2: opdrachten in de huidige sessie ophalen

Met deze opdracht wordt de para meter **ListImported** gebruikt om alleen de opdrachten in de huidige sessie op te halen.

```powershell
Get-Command -ListImported
```

### Voor beeld 3: cmdlets ophalen en weer geven in volg orde

Met deze opdracht worden alle cmdlets opgehaald, alfabetisch gesorteerd op het zelfstandig naam woord in de cmdletnaam en worden deze vervolgens weer gegeven in groepen op basis van zelfstandig naam woord. Deze weer gave kan u helpen de cmdlets voor een taak te vinden.

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### Voor beeld 4: opdrachten in een module ophalen

Met deze opdracht wordt de para meter **module** gebruikt om de opdrachten in de modules micro soft. Power shell. Security en micro soft. Power shell. Utility op te halen.

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### Voor beeld 5: informatie over een cmdlet ophalen

Met deze opdracht wordt informatie over de `Get-AppLockerPolicy` cmdlet opgehaald. Ook wordt de **AppLocker** -module geïmporteerd, waarmee alle opdrachten in de **AppLocker** -module worden toegevoegd aan de huidige sessie.

```powershell
Get-Command Get-AppLockerPolicy
```

Wanneer een module automatisch wordt geïmporteerd, is het effect hetzelfde als het gebruik van de Import-Module-cmdlet.
De module kan opdrachten, typen en indelings bestanden toevoegen en scripts uitvoeren in de sessie. Als u het automatisch importeren van modules wilt inschakelen, uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele. Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.

### Voor beeld 6: de syntaxis van een cmdlet ophalen

Deze opdracht maakt gebruik van de para meters **argument List** en **syntax** om de syntaxis van de cmdlet op te halen `Get-ChildItem` wanneer deze wordt gebruikt in het certificaat: station. Het certificaat: station is een Power Shell-station dat door de certificaat provider aan de sessie wordt toegevoegd.

```powershell
Get-Command  -Name Get-Childitem -Args Cert: -Syntax
```

Wanneer u de syntaxis die wordt weer gegeven in de uitvoer vergelijkt met de syntaxis die wordt weer gegeven wanneer u de para meter **args** ( **argument List** ) weglaat, ziet u dat de **certificaat provider** een dynamische para meter, **CodeSigningCert** , toevoegt aan de `Get-ChildItem` cmdlet.

Zie [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)voor meer informatie over de certificaat provider.

### Voor beeld 7: dynamische para meters ophalen

De opdracht in het voor beeld gebruikt de `Get-DynamicParameters` functie om de dynamische para meters op te halen die de certificaat provider toevoegt aan de `Get-ChildItem` cmdlet wanneer deze wordt gebruikt in het certificaat: station.

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command -Name $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

Met de `Get-DynamicParameters` functie in dit voor beeld worden de dynamische para meters van een cmdlet opgehaald. Dit is een alternatief voor de methode die wordt gebruikt in het vorige voor beeld. Dynamische para meter kan worden toegevoegd aan een cmdlet door een andere cmdlet of een provider.

### Voor beeld 8: alle opdrachten van alle typen ophalen

Met deze opdracht worden alle opdrachten van alle typen op de lokale computer opgehaald, met inbegrip van uitvoer bare bestanden in de paden van de omgevings variabele **Path** ( `$env:path` ).

```powershell
Get-Command *
```

Er wordt een **ApplicationInfo** -object (System. Management. Automation. ApplicationInfo) geretourneerd voor elk bestand, niet een **file info** -object (System. io. file info).

### Voor beeld 9: cmdlets ophalen met behulp van de naam en het type van de para meter

Met deze opdracht worden cmdlets opgehaald die een para meter hebben waarvan de naam auth bevat en waarvan het type **AuthenticationMechanism** is.

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

U kunt een opdracht als deze gebruiken om cmdlets te vinden waarmee u de methode kunt opgeven die wordt gebruikt om de gebruiker te verifiëren.

De para meter **parameter type** onderscheidt para meters die een **AuthenticationMechanism** -waarde overnemen van de para meter **authenticationLevel** , zelfs wanneer deze vergelijk bare namen hebben.

### Voor beeld 10: een alias ophalen

In dit voor beeld ziet u hoe u de `Get-Command` cmdlet gebruikt met een alias.

```powershell
Get-Command Name dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

Hoewel dit doorgaans wordt gebruikt voor cmdlets en functies, worden `Get-Command` ook scripts, functies, aliassen en uitvoer bare bestanden opgehaald.

In de uitvoer van de opdracht wordt de speciale weer gave van de **naam** eigenschaps waarde voor aliassen weer gegeven. In de weer gave worden de alias en de volledige opdracht naam weer gegeven.

### Voor beeld 11: de syntaxis van een alias ophalen

In dit voor beeld ziet u hoe u de syntaxis krijgt, samen met de standaard naam van een alias.

De uitvoer van de opdracht toont de alias met het label met de standaard naam, gevolgd door de syntaxis.

```powershell
Get-Command -Name dir -Syntax
```

```Output
dir (alias) -> Get-ChildItem

dir [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]

dir [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>] [-Exclude <string[]>] [-Recurse] [-Depth <uint>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### Voor beeld 12: alle exemplaren van de opdracht Notepad ophalen

In dit voor beeld wordt de para meter **all** van de `Get-Command` cmdlet gebruikt om alle exemplaren van de `Notepad` opdracht op de lokale computer weer te geven.

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

De para meter **all** is handig wanneer er meer dan één opdracht is met dezelfde naam in de sessie.

Vanaf Windows Power Shell 3,0 wordt standaard, wanneer de sessie meerdere opdrachten met dezelfde naam bevat, `Get-Command` alleen de opdracht opgehaald die wordt uitgevoerd wanneer u de naam van de opdracht typt. Met de **alle** para meters worden `Get-Command` alle opdrachten met de opgegeven naam opgehaald en worden deze in volg orde van uitvoerings volgorde geretourneerd. Als u een andere opdracht dan de eerste uit de lijst wilt uitvoeren, typt u het volledig gekwalificeerde pad naar de opdracht.

Zie [about_Command_Precedence](About/about_Command_Precedence.md)voor meer informatie over de rang orde van de opdracht.

### Voor beeld 13: de naam van een module met een cmdlet ophalen

Met deze opdracht wordt de naam opgehaald van de module waarin de `Get-Date` cmdlet afkomstig is.
De opdracht maakt gebruik van **de eigenschap PropertyName** van alle opdrachten.

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

Deze opdracht indeling werkt op opdrachten in Power shell-modules, zelfs als deze niet in de sessie worden geïmporteerd.

### Voor beeld 14: cmdlets en functies met een uitvoer type ophalen

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

Met deze opdracht worden de cmdlets en functies opgehaald die een uitvoer type hebben en het type objecten dat ze retour neren.

Het eerste deel van de opdracht haalt alle cmdlets op. Een pijplijn operator ( `|` ) verzendt de-cmdlets naar de `Where-Object` cmdlet, waarmee alleen de waarden worden geselecteerd waarin de eigenschap **output** type wordt ingevuld. Een andere pijplijn operator verzendt de geselecteerde cmdlet-objecten naar de `Format-List` cmdlet, waarin de naam en het uitvoer type van elke cmdlet in een lijst worden weer gegeven.

De eigenschap **output** type van een **CommandInfo** -object heeft alleen een waarde die niet null is wanneer de cmdlet code het kenmerk **output** type voor de cmdlet definieert.

### Voor beeld 15: cmdlets ophalen die een specifiek object type als invoer hebben

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

Met deze opdracht vindt u cmdlets die net-adapter objecten als invoer hebben. U kunt deze opdracht indeling gebruiken om de cmdlets te vinden die het type objecten accepteren dat door een opdracht wordt geretourneerd.

De opdracht maakt gebruik van de intrinsieke eigenschap **PSTypeNames** van alle objecten, waarmee de typen worden opgehaald die het object beschrijven. Als u de eigenschap **PSTypeNames** van een netwerk adapter wilt ophalen en niet de eigenschap **PSTypeNames** van een verzameling netwerk adapters, gebruikt de opdracht matrix notatie om de eerste netadapter op te halen die door de cmdlet wordt geretourneerd.

### Voor beeld 16: opdrachten ophalen met behulp van een benadering van het Zoek resultaat

In dit voor beeld heeft de naam van de opdracht opzettelijk een type ' Get-commnd '.
Met behulp van de `-UseFuzzyMatching` Switch heeft de cmdlet bepaald dat het beste resultaat werd `Get-Command` gevolgd door andere systeem eigen opdrachten op het systeem die een vergelijk bare overeenkomst hebben.

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## PARAMETERS

### -Alle

Geeft aan dat met deze cmdlet alle opdrachten worden opgehaald, met inbegrip van opdrachten van hetzelfde type die dezelfde naam hebben. Standaard worden `Get-Command` alleen de opdrachten opgehaald die worden uitgevoerd wanneer u de naam van de opdracht typt.

Zie [about_Command_Precedence](About/about_Command_Precedence.md)voor meer informatie over de methode die door Power shell wordt gebruikt voor het selecteren van de opdracht die moet worden uitgevoerd wanneer meerdere opdrachten dezelfde naam hebben.
Zie [about_Modules](About/about_Modules.md)voor meer informatie over opdracht namen in de module en het uitvoeren van opdrachten die niet standaard worden uitgevoerd vanwege een naam conflict.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

In Windows Power Shell 2,0 worden `Get-Command` alle opdrachten standaard opgehaald.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Argument List

Hiermee wordt een matrix met argumenten opgegeven. Met deze cmdlet wordt informatie opgehaald over een cmdlet of functie wanneer deze wordt gebruikt met de opgegeven para meters ("argumenten"). De alias voor **argument List** is **args**.

Als u dynamische para meters wilt detecteren die alleen beschikbaar zijn wanneer bepaalde andere para meters worden gebruikt, stelt u de waarde van **argument List** in op de para meters die de dynamische para meters activeren.

Als u de dynamische para meters wilt detecteren die een provider aan een cmdlet toevoegt, stelt u de waarde van de para meter **argument List** in op een pad in het provider station, zoals WSMan:, HKLM: of CERT:. Wanneer de opdracht een Power shell-provider-cmdlet is, voert u slechts één pad in elke opdracht in. De provider-cmdlets retour neren alleen de dynamische para meters voor het eerste pad de waarde van **argument List**. Zie [about_Providers](About/about_Providers.md)voor meer informatie over de provider-cmdlets.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

Hiermee geeft u de typen opdrachten op die met deze cmdlet worden opgehaald. Voer een of meer opdracht typen in. Gebruik **CommandType** of de alias, **Typ**. Hiermee worden standaard `Get-Command` Alle cmdlets, functies en aliassen opgehaald.

De aanvaardbare waarden voor deze parameter zijn:

- Toe. Hiermee worden de aliassen opgehaald van alle Power shell-opdrachten. Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.
- Hele. Hiermee worden alle opdracht typen opgehaald. Deze parameter waarde is gelijk aan `Get-Command *` .
- Modules. Hiermee worden niet-Power Shell-bestanden opgehaald in paden die worden vermeld in de omgevings variabele **Path** ($env:p AD), inclusief txt-, exe-en dll-bestanden. Zie about_Environment_Variables voor meer informatie over de omgevings variabele **Path** .
- Cmdlet. Hiermee worden alle cmdlets opgehaald.
- ExternalScript. Hiermee worden alle. ps1-bestanden opgehaald uit de paden die worden vermeld in de **Path** -omgevings variabele ($env:p AD).
- Filter en functie. Hiermee worden alle geavanceerde en eenvoudige Power shell-functies en-filters opgehaald.
- Schriften. Hiermee worden alle script blokken opgehaald. Als u Power shell-scripts (. ps1-bestanden) wilt ophalen, gebruikt u de ExternalScript-waarde.

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullyQualifiedModule

Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten, zoals beschreven in de sectie **opmerkingen** van [ModuleSpecification constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in een van de volgende indelingen:

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.

U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter. De twee para meters sluiten elkaar wederzijds uit.

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

### -ListImported

Geeft aan dat met deze cmdlet alleen opdrachten in de huidige sessie worden opgehaald.

Vanaf Power Shell 3,0 worden standaard `Get-Command` alle geïnstalleerde opdrachten opgehaald, inclusief, maar niet beperkt tot, de opdrachten in de huidige sessie. In Power Shell 2,0 worden alleen opdrachten in de huidige sessie opgehaald.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module

Hiermee geeft u een matrix met modules op. Met deze cmdlet worden de opdrachten opgehaald die afkomstig zijn van de opgegeven modules.
Voer de namen in van modules of module-objecten.

Deze para meter neemt teken reeks waarden, maar de waarde van deze para meter kan ook een **PSModuleInfo** -object zijn, zoals de objecten die de `Get-Module` en `Import-PSSession` cmdlets retour neren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Name

Hiermee geeft u een matrix met namen op. Met deze cmdlet worden alleen opdrachten met de opgegeven naam opgehaald. Voer een naam of naam patroon in. Joker tekens zijn toegestaan.

Als u opdrachten met dezelfde naam wilt ophalen, gebruikt u de para meter **all** . Wanneer twee opdrachten dezelfde naam hebben, `Get-Command` wordt standaard de opdracht opgehaald die wordt uitgevoerd wanneer u de naam van de opdracht typt.

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Zelfstandig naam woord

Hiermee geeft u een matrix met de naam van de opdracht op. Deze cmdlet haalt opdrachten op, waaronder cmdlets, functies en aliassen, die namen hebben die het opgegeven zelfstandig naam woord bevatten. Voer een of meer zelfstandige naam woorden of een zelfstandige naam op. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Para meternaam

Hiermee geeft u een matrix met parameter namen op. Met deze cmdlet worden opdrachten in de sessie met de opgegeven para meters opgehaald. Voer parameter namen of parameter aliassen in. Joker tekens worden ondersteund.

Met de para meters **para** meters en **parameter type** worden alleen opdrachten in de huidige sessie gezocht.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Parameter type

Hiermee geeft u een matrix met parameter namen op. Deze cmdlet haalt opdrachten op in de sessie die para meters van het opgegeven type hebben. Voer de volledige naam of gedeeltelijke naam van een parameter type in. Joker tekens worden ondersteund.

Met de para meters **para** meters en **parameter type** worden alleen opdrachten in de huidige sessie gezocht.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowCommandInfo

Geeft aan dat met deze cmdlet opdracht gegevens worden weer gegeven.

Deze para meter is geïntroduceerd in Windows Power shell 5,0.

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

### -Syntaxis

Geeft aan dat met deze cmdlet alleen de volgende opgegeven gegevens over de opdracht worden opgehaald:

- Aliassen. Hiermee haalt u de standaard naam en syntaxis op.
- Cmdlets. Hiermee wordt de syntaxis opgehaald.
- Functies en filters. Hiermee wordt de functie definitie opgehaald.
- Scripts en toepassingen of bestanden. Hiermee haalt u het pad en de bestands naam.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

Hiermee geeft u het aantal opdrachten op dat moet worden opgehaald. U kunt deze para meter gebruiken om de uitvoer van een opdracht te beperken.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseAbbreviationExpansion

Hiermee wordt aangegeven dat overeenkomende tekens in de opdracht wordt gebruikt om te zoeken naar hoofd letters in een opdracht. Bijvoorbeeld, `i-psdf` komt overeen met `Import-PowerShellDataFile` de zoek tekens die overeenkomen met een hoofd letter in het resultaat. Wanneer dit type overeenkomst wordt gebruikt, hebben joker tekens geen overeenkomstige resultaten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseFuzzyMatching

Geeft aan dat er een matching-algoritme wordt gebruikt bij het zoeken van opdrachten. De volg orde van de uitvoer is van het meest overeenkomende resultaat dat overeenkomt met de minst waarschijnlijke overeenkomst. Joker tekens mogen niet worden gebruikt met fuzzy match, omdat er wordt geprobeerd opdrachten te vinden die deze Joker tekens kunnen bevatten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verb

Hiermee geeft u een matrix met opdracht woorden op. Deze cmdlet haalt opdrachten op, waaronder cmdlets, functies en aliassen, die namen hebben die de opgegeven term bevatten. Voer een of meer woorden of woord patronen in. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt opdracht namen door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. CommandInfo

Deze cmdlet retourneert objecten die zijn afgeleid van de **CommandInfo** -klasse. Het type van het object dat wordt geretourneerd, is afhankelijk van het type opdracht dat `Get-Command` wordt opgehaald.

### System. Management. Automation. AliasInfo

Vertegenwoordigt aliassen.

### System. Management. Automation. ApplicationInfo

Hiermee worden toepassingen en bestanden aangeduid.

### System. Management. Automation. CmdletInfo

Vertegenwoordigt cmdlets.

### System. Management. Automation. FunctionInfo

Hiermee worden functies en filters aangeduid.

## OPMERKINGEN

* Wanneer er meer dan één opdracht met dezelfde naam beschikbaar is voor de sessie, `Get-Command` wordt de opdracht weer gegeven die wordt uitgevoerd wanneer u de naam van de opdracht typt. Als u opdrachten met dezelfde naam wilt ophalen, gebruikt u de para meter **all** in volg orde uitvoeren. Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)voor meer informatie.
* Wanneer een module automatisch wordt geïmporteerd, is het effect hetzelfde als het gebruik van de `Import-Module` cmdlet. De module kan opdrachten, typen en indelings bestanden toevoegen en scripts uitvoeren in de sessie.
  Als u het automatisch importeren van modules wilt inschakelen, uitschakelen en configureren, gebruikt u de `$PSModuleAutoLoadingPreference` Voorkeurs variabele. Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Exporteren-PSSession](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[Get-Help](Get-Help.md)

[Get-member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Get-PSDrive](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[about_Command_Precedence](About/about_Command_Precedence.md)

