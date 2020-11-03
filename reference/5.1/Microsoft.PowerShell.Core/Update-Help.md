---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: 4ef0865e81e01746fed77b73e265e68086a7a9e1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/04/2020
ms.locfileid: "93251713"
---
# Update-Help

## SAMENVATTING
Downloadt en installeert de nieuwste Help-bestanden op uw computer.

## SYNTAXIS

### Pad (standaard)

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Update-Help` cmdlet downloadt de nieuwste Help-bestanden voor Power shell-modules en installeert deze op uw computer. U hoeft Power shell niet opnieuw op te starten om de wijziging van kracht te laten worden. U kunt de `Get-Help` cmdlet gebruiken om de nieuwe Help-bestanden onmiddellijk weer te geven.

`Update-Help` Hiermee wordt de versie van de Help-bestanden op uw computer gecontroleerd. Als u geen Help-bestanden voor een module hebt of als uw Help-bestanden zijn verouderd, `Update-Help` downloadt de nieuwste Help-bestanden. De Help-bestanden kunnen worden gedownload en geïnstalleerd via internet of een bestands share.

Zonder para meters worden `Update-Help` de Help-bestanden voor modules in de sessie en voor alle geïnstalleerde modules bijgewerkt die ondersteuning bieden voor bijwerk bare Help. Modules die zijn geïnstalleerd maar niet zijn geladen in de huidige sessie, worden opgenomen. Power shell-modules worden opgeslagen op een locatie die wordt vermeld in de `$env:PSModulePath` omgevings variabele. Zie [about_Updatable_Help](./About/about_Updatable_Help.md) voor meer informatie.

U kunt de **module** parameter gebruiken om Help-bestanden voor een bepaalde module bij te werken. Gebruik de para meter **uiCulture** om Help-bestanden te downloaden in meerdere talen en land instellingen.

U kunt ook gebruiken `Update-Help` op computers die niet zijn verbonden met internet. Gebruik eerst de `Save-Help` cmdlet om Help-bestanden te downloaden van Internet en deze op te slaan in een gedeelde map die toegankelijk is voor het systeem dat niet is verbonden met internet. Vervolgens gebruikt u de para meter **SourcePath** van `Update-Help` om de bijgewerkte Help-bestanden te downloaden van de gedeelde en te installeren op de computer.

U kunt de Help-updates automatiseren door de cmdlet toe te voegen `Update-Help` aan uw Power shell-profiel. Standaard `Update-Help` wordt slechts één keer per dag op elke computer uitgevoerd. Als u de limiet van één dag wilt overschrijven, gebruikt u de para meter **Force** .

De `Update-Help` cmdlet is geïntroduceerd in Windows Power shell 3,0.

> [!IMPORTANT]
> `Update-Help` beheerders bevoegdheden zijn vereist.
>
> U moet lid zijn van de groep Administrators op de computer om de Help-bestanden voor de Power shell core-modules bij te werken.
>
> Als u de Help-bestanden voor modules in de Power shell-installatie directory ( `$PSHOME\Modules` ), inclusief de Power shell-kern modules, wilt downloaden of bijwerken, start u Power shell met de optie als administrator uitvoeren.
> Bijvoorbeeld: `Start-Process powershell.exe -Verb RunAs`.
>
> U kunt ook Help-bestanden bijwerken met behulp van het menu-item Windows Power shell Help bijwerken in het menu Help in Windows Power shell Integrated Scripting Environment (ISE).
>
> Het Help-item update Windows Power Shell voert een `Update-Help` cmdlet zonder para meters uit.
> Als u de Help voor modules in de map wilt bijwerken `$PSHOME` , start u Windows PowerShell ISE met de optie als administrator uitvoeren.

## VOORBEELDEN

### Voor beeld 1: Help-bestanden voor alle modules bijwerken

De `Update-Help` cmdlet werkt Help-bestanden bij voor geïnstalleerde modules die kunnen worden bijgewerkt met ondersteuning. De cultuur taal van de gebruikers interface (UI) is ingesteld in het besturings systeem.

```powershell
Update-Help
```

### Voor beeld 2: Help-bestanden voor opgegeven modules bijwerken

De `Update-Help` cmdlet updatet alleen Help-bestanden voor module namen die beginnen met **micro soft. Power shell**.

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### Voor beeld 3: Help-bestanden voor verschillende talen bijwerken

`Update-Help`Met de cmdlet worden de Japanse (ja-JP) en de Engelse (en-US) Help-bestanden voor alle modules bijgewerkt.

Als een module geen Help-bestanden voor een opgegeven UI-cultuur biedt, wordt een fout bericht weer gegeven voor de module en de UI-cultuur. In dit voor beeld geeft het fout bericht aan dat de Help-bestanden van **ja-jp** niet zijn gevonden voor de module **micro soft. Power shell. Utility**.

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### Voor beeld 4: Help-bestanden automatisch bijwerken

In dit voor beeld wordt een geplande taak gemaakt die elke dag om 3:00 uur Help voor alle modules bijwerkt.

```powershell
$jobParams = @{
  Name = 'UpdateHelpJob'
  Credential = 'Domain01\User01'
  ScriptBlock = '{Update-Help}'
  Trigger = (New-JobTrigger -Daily -At "3 AM")
}
Register-ScheduledJob @jobParams
```

```Output
Id         Name            JobTriggers     Command                                  Enabled
--         ----            -----------     -------                                  -------
1          UpdateHelpJob   1               Update-Help                              True
```

`Register-ScheduledJob`Met de cmdlet wordt een geplande taak gemaakt waarmee een opdracht wordt uitgevoerd `Update-Help` . De opdracht gebruikt de para meter **Credential** om uit te voeren met `Update-Help` behulp van de referenties van een lid van de groep Administrators op de computer. De waarde van de **trigger** parameter is een `New-JobTrigger` opdracht waarmee een taak trigger wordt gemaakt waarmee de taak elke dag om 3:00 uur wordt gestart.

Als u de `Register-ScheduledJob` opdracht wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** . Power shell vraagt u om het wacht woord van de gebruiker opgegeven in de para meter **Credential** . De referenties worden opgeslagen met de geplande taak. U wordt niet gevraagd wanneer de taak wordt uitgevoerd.

U kunt de `Get-ScheduledJob` cmdlet gebruiken om de geplande taak weer te geven, de `Set-ScheduledJob` cmdlet te gebruiken om deze te wijzigen en de `Unregister-ScheduledJob` cmdlet te gebruiken om deze te verwijderen. U kunt de geplande taak ook weer geven en beheren in taak planner in het volgende pad:

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.

### Voor beeld 5: Help-bestanden op meerdere computers bijwerken vanuit een bestands share

In dit voor beeld worden bijgewerkte Help-bestanden gedownload van Internet en opgeslagen in een bestands share. Er zijn gebruikers referenties nodig die machtigingen hebben voor toegang tot de bestands share en om updates te installeren. Wanneer een bestands share wordt gebruikt, is het mogelijk om computers bij te werken die zich achter een firewall bevinden of die niet zijn verbonden met internet.

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

`Save-Help`Met de opdracht worden de nieuwste Help-bestanden gedownload voor alle modules die kunnen worden bijgewerkt met ondersteuning.
Met de para meter **doelpad** worden de bestanden opgeslagen in de `\\Server01\Share\PSHelp` Bestands share. De **referentie** parameter geeft u een gebruiker op die toegang heeft tot de bestands share.

`Invoke-Command`Met de cmdlet worden externe `Update-Help` opdrachten op meerdere computers uitgevoerd. De para meter **ComputerName** haalt een lijst op met externe computers uit het **Servers.txt** -bestand. De para meter **script Block** voert de `Update-Help` opdracht uit en gebruikt de para meter **SourcePath** om de bestands share op te geven die de bijgewerkte Help-bestanden bevat. De **referentie** parameter geeft u een gebruiker die toegang heeft tot de bestands share en voert u de opdracht extern uit `Update-Help` .

### Voor beeld 6: een lijst met bijgewerkte Help-bestanden ophalen

De `Update-Help` cmdlet Update Help voor een opgegeven module. De cmdlet gebruikt de **uitgebreide** para meter common om de lijst met Help-bestanden weer te geven die zijn bijgewerkt. U kunt **uitgebreid** gebruiken om de uitvoer voor alle Help-bestanden of Help-bestanden voor een specifieke module weer te geven.

Zonder de para meter **uitgebreid** worden `Update-Help` de resultaten van de opdracht niet weer gegeven. De **uitgebreide** para meter uitvoer is handig om te controleren of de Help-bestanden zijn bijgewerkt of of de meest recente versie is geïnstalleerd.

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### Voor beeld 7: modules zoeken die kunnen worden bijgewerkt met ondersteuning

In dit voor beeld wordt een lijst weer gegeven met de modules die kunnen worden bijgewerkt. De opdracht maakt gebruik van de eigenschap **HelpInfoUri** van de module om modules te identificeren die ondersteunende Help kunnen ondersteunen. De eigenschap **HelpInfoUri** bevat een adres dat wordt omgeleid wanneer de `Update-Help` cmdlet wordt uitgevoerd.

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### Voor beeld 8: bijgewerkte Help-bestanden met voor Raad

In dit voor beeld maakt het script `Get-UpdateHelpVersion.ps1` een inventarisatie van de Help-bestanden die kunnen worden bijgewerkt voor elke module en de bijbehorende versie nummers.

Met het script worden modules geïdentificeerd die ondersteuning bieden voor Help bij het gebruik van de eigenschap **HelpInfoUri** van modules. Voor modules die kunnen worden bijgewerkt met ondersteuning, zoekt het script naar het Help-informatie bestand (* helpinfo.xml) en parseert het naar het meest recente versie nummer.

Het script maakt gebruik van de **PSCustomObject** -klasse en een hash-tabel om een aangepast uitvoer object te maken.

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## PARAMETERS

### -Credential

Hiermee geeft u de referenties op van een gebruiker die toegang heeft tot de locatie van het bestands systeem die is opgegeven door **SourcePath**. Deze para meter is alleen geldig als de para meter **SourcePath** of **LiteralPath** in de opdracht wordt gebruikt.

Met de para meter **Credential** kunt u `Update-Help` opdrachten uitvoeren met de para meter **SourcePath** op externe computers. Door expliciete referenties op te geven, kunt u de opdracht uitvoeren op een externe computer en toegang krijgen tot een bestands share op een derde computer zonder dat er een fout wordt geweigerd of als CredSSP-verificatie wordt gebruikt voor het delegeren van referenties.

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
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Geeft aan dat deze cmdlet niet de beperking van één dag volgt, de versie controle overs laat en bestanden downloadt die de limiet van 1 GB overschrijden.

Zonder deze para meter `Update-Help` wordt slechts één keer per periode van 24 uur uitgevoerd. Down loads zijn beperkt tot 1 GB aan niet-gecomprimeerde inhoud per module en Help-bestanden worden alleen geïnstalleerd wanneer ze nieuwer zijn dan de bestaande bestanden op de computer.

De limiet van één dag beveiligt de servers die als host dienen voor de Help-bestanden en maken het praktisch om een opdracht toe te voegen `Update-Help` aan uw Power shell-profiel zonder de resource kosten van herhaalde verbindingen of down loads te maken.

Als u de Help voor een module in meerdere GEBRUIKERSINTERFACE culturen wilt bijwerken zonder de para meter **Force** , neemt u alle gebruikersinterface culturen op in dezelfde opdracht, zoals:

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### -FullyQualifiedModule

Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten.
Deze modules worden beschreven in de sectie opmerkingen van de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in de indeling:

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

of

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.

U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.

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

Hiermee geeft u de map op voor bijgewerkte Help-bestanden in plaats van ze van Internet te downloaden. Gebruik deze para meter of **bronpad** als u de cmdlet hebt gebruikt `Save-Help` om Help-bestanden te downloaden naar een map.

U kunt een Directory-object, zoals uit de `Get-Item` `Get-ChildItem` -of-cmdlets, uitlijnen naar `Update-Help` .

In tegens telling tot de waarde van **SourcePath** , wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Er worden geen tekens geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module

Help bij updates voor de opgegeven modules. Voer een of meer module namen of naam patronen in een lijst met door komma's gescheiden waarden in, of geef een bestand op waarin één module naam op elke regel wordt weer gegeven. Joker tekens zijn toegestaan. U kunt modules van de `Get-Module` cmdlet naar de cmdlet pijp lijnen `Update-Help` .

De modules die u opgeeft, moeten op de computer zijn geïnstalleerd, maar ze hoeven niet in de huidige sessie te worden geïmporteerd. U kunt een wille keurige module opgeven in de sessie of een module die is geïnstalleerd op een locatie die wordt vermeld in de `$env:PSModulePath` omgevings variabele.

De waarde van `*` (alle) probeert de Help bij te werken voor alle modules die op de computer zijn geïnstalleerd.
Modules die geen ondersteuning bieden voor bijwerk bare Help zijn opgenomen. Deze waarde kan fouten genereren wanneer de opdracht modules detecteert die geen ondersteuning bieden voor de Help die kan worden bijgewerkt. Voer in plaats daarvan `Update-Help` zonder para meters uit.

De **module** parameter van de `Update-Help` cmdlet accepteert niet het volledige pad naar het manifest bestand van een module bestand of module. Als u de Help wilt bijwerken voor een module die zich niet in een locatie bevindt `$env:PSModulePath` , importeert u de module in de huidige sessie voordat u de `Update-Help` opdracht uitvoert.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Recursief

Voert een recursieve zoek opdracht uit voor Help-bestanden in de opgegeven map. Deze para meter is alleen geldig als de opdracht de para meter **SourcePath** gebruikt.

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

### -Bronpad

Hiermee geeft u een bestandsmap op waarin `Update-Help` bijgewerkte Help-bestanden worden opgehaald, in plaats van ze van Internet te downloaden. Geef het pad van een map op. Geef geen bestands naam of bestandsnaam extensie op. U kunt een map, zoals een, uit de `Get-Item` `Get-ChildItem` cmdlets, naar koppelen `Update-Help` .

`Update-Help`Downloadt standaard bijgewerkte Help-bestanden van het internet. Gebruik **SourcePath** wanneer u de cmdlet hebt gebruikt `Save-Help` om bijgewerkte Help-bestanden te downloaden naar een map.

Als u een standaard waarde voor **SourcePath** wilt opgeven, gaat u naar **Groepsbeleid** , **computer configuratie** en **stelt u het standaard bronpad voor update-Help** in. Met deze groepsbeleid instelling wordt voor komen dat gebruikers `Update-Help` Help-bestanden downloaden van het internet.
Zie [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

Hiermee geeft u de UI-cultuur waarden `Update-Help` op die worden gebruikt voor het ophalen van bijgewerkte Help-bestanden. Voer een of meer taal codes in, zoals **es-es** , een variabele die cultuur objecten bevat of een opdracht die cultuur objecten, zoals een of-opdracht, ophalen `Get-Culture` `Get-UICulture` . Joker tekens zijn niet toegestaan en u kunt geen gedeeltelijke taal code verzenden, zoals **de**.

Hiermee worden standaard `Update-Help` Help-bestanden in de UI-cultuur ingesteld voor het besturings systeem. Als u de para meter **uiCulture** opgeeft, `Update-Help` zoekt alleen naar de opgegeven gebruikersinterface cultuur.

Opdrachten die gebruikmaken van de para meter **uiCulture** , worden alleen uitgevoerd wanneer de module Help-bestanden voor de opgegeven UI-cultuur bevat. Als de opdracht mislukt omdat de opgegeven GEBRUIKERSINTERFACE cultuur niet wordt ondersteund, wordt een fout bericht weer gegeven.

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

Hiermee wordt aangegeven dat `Update-Help` de opdracht wordt uitgevoerd, met inbegrip van het downloaden van Internet, met behulp van de referenties van de huidige gebruiker. Standaard wordt de opdracht uitgevoerd zonder expliciete referenties.

Deze para meter is alleen effectief wanneer het webdownloaden NT LAN Manager (NTLM), onderhandelen of Kerberos-verificatie gebruikt.

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

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. IO. DirectoryInfo

U kunt een mappad door sluizen naar `Update-Help` .

### System. Management. Automation. PSModuleInfo

U kunt een module-object vanuit de `Get-Module` cmdlet door sluizen naar `Update-Help` .

## UITVOER

### Geen

`Update-Help` Er wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Als u de Help voor de Power shell core-modules wilt bijwerken die de opdrachten bevatten die zijn geïnstalleerd met Power shell of een module in de `$PSHOME\Modules` Directory, start u Power shell met de optie om **als Administrator uit te voeren**.

Alleen leden van de groep Administrators op de computer kunnen de Help-informatie voor de Power shell core-modules, de opdrachten die worden geïnstalleerd samen met Power shell en modules in de `$PSHOME\Modules` map bijwerken. Als u geen machtiging hebt om Help-bestanden bij te werken, kunt u de Help-bestanden online lezen. Bijvoorbeeld `Get-Help Update-Help -Online`.

Modules zijn de kleinste eenheid van Help die kan worden bijgewerkt. U kunt de Help voor een bepaalde cmdlet niet bijwerken. Als u de module wilt vinden die een bepaalde cmdlet bevat, gebruikt u **de eigenschap PropertyName** van de `Get-Command` cmdlet, bijvoorbeeld `(Get-Command Update-Help).ModuleName` .

Omdat Help-bestanden in de module directory zijn geïnstalleerd, `Update-Help` kan de cmdlet alleen een bijgewerkt Help-bestand installeren voor modules die op de computer zijn geïnstalleerd. De `Save-Help` cmdlet kan echter de Help opslaan voor modules die niet op de computer zijn geïnstalleerd.

Als er `Update-Help` geen bijgewerkte Help-bestanden kunnen worden gevonden voor een module, of als er geen bijgewerkte Help kan worden gevonden in de opgegeven taal, wordt de installatie zonder fouten voortgezet. Als u de status en Details van de voortgang wilt bekijken, gebruikt u de para meter **uitgebreid** .

De `Update-Help` cmdlet is geïntroduceerd in Windows Power shell 3,0. Deze functie werkt niet in eerdere versies van Power shell. Op computers met Windows Power Shell 2,0 en Windows Power Shell 3,0 gebruikt u de `Update-Help` cmdlet in een Windows Power shell 3,0-sessie om Help-bestanden te downloaden en bij te werken. De Help-bestanden zijn beschikbaar voor zowel Windows Power Shell 2,0 als Windows Power Shell 3,0.

De `Update-Help` `Save-Help` cmdlets en gebruiken de volgende poorten om Help-bestanden te downloaden: poort 80 voor http en poort 443 voor HTTPS.

`Update-Help` ondersteunt alle modules en de Power shell core-modules. Andere modules worden niet ondersteund.

Als u de Help wilt bijwerken voor een module op een locatie die niet wordt weer gegeven in de `$env:PSModulePath` omgevings variabele, importeert u de module in de huidige sessie en voert u vervolgens een `Update-Help` opdracht uit. `Update-Help`Zonder para meters uitvoeren of de **module** parameter gebruiken om de module naam op te geven. Met de **module** parameter van `Update-Help` de `Save-Help` cmdlets en wordt het volledige pad van een module bestand of module manifest bestand niet geaccepteerd.

Elke module kan de Help die kan worden bijgewerkt ondersteunen. Zie [ondersteunende Help-informatie](/powershell/scripting/developer/module/supporting-updatable-help)voor instructies voor het ondersteunen van Help-informatie in de modules die u ontwerpt.

De `Update-Help` `Save-Help` cmdlets en worden niet ondersteund op Windows Preinstallation Environment (Windows PE).

## GERELATEERDE KOPPELINGEN

[Get-cultuur](../Microsoft.PowerShell.Utility/Get-Culture.md)

[Get-Help](Get-Help.md)

[Get-module](Get-Module.md)

[Get-UICulture](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[Begin taak](Start-Job.md)

[Opslaan-Help](Save-Help.md)
