---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 617deb71605462833c3ed816fb4391c88ccd2da8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251043"
---
# New-PSRoleCapabilityFile

## SAMENVATTING
Hiermee maakt u een bestand dat een set mogelijkheden definieert die moeten worden weer gegeven via een sessie configuratie.

## SYNTAXIS

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## BESCHRIJVING

Met de `New-PSRoleCapabilityFile` cmdlet wordt een bestand gemaakt dat een reeks gebruikers mogelijkheden definieert die kunnen worden weer gegeven via sessie configuratie bestanden. Dit omvat het bepalen van de cmdlets, functies en scripts die beschikbaar zijn voor gebruikers. Het Capability-bestand is een bestand met lees bare tekst dat een hash-tabel met eigenschappen en waarden van sessie configuratie bevat. Het bestand heeft de bestandsnaam extensie. psrc en kan worden gebruikt door meer dan één sessie configuratie.

Alle para meters van `New-PSRoleCapabilityFile` zijn optioneel, met uitzonde ring van de para meter **Path** , waarmee het bestandspad voor het bestand wordt opgegeven. Als u geen para meter opneemt tijdens het uitvoeren van de cmdlet, wordt de bijbehorende sleutel in het bestand met de sessie configuratie commentaar gegeven, behalve wanneer vermeld in de parameter beschrijving. Bijvoorbeeld, als u de para meter **AssembliesToLoad** niet opneemt, wordt die sectie van het sessie configuratie bestand uit commentaar genomen.

Als u het bestand voor de functie wilt gebruiken in een sessie configuratie, plaatst u het bestand eerst in een submap **RoleCapabilities** van een geldige map voor de Power shell-module. Ga vervolgens naar het bestand met de naam in het veld **RoleDefinitions** in een Power shell-sessie configuratie bestand (. pssc).

Deze cmdlet is geïntroduceerd in Windows Power shell 5,0.

## VOORBEELDEN

### Voor beeld 1: een functie bestand met een lege rol maken

In dit voor beeld wordt een nieuw bestand met een functie gemaakt waarin de standaard waarden (leeg) worden gebruikt. Het bestand kan later worden bewerkt in een tekst editor om deze configuratie-instellingen te wijzigen.

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### Voor beeld 2: een functie mogelijkheidsprofiel maken waarmee gebruikers services en een VDI-computer opnieuw kunnen starten

In dit voor beeld wordt een mogelijkheidsprofiel gemaakt waarmee gebruikers services en computers die overeenkomen met een specifiek naam patroon, opnieuw kunnen starten. Naam filtering wordt gedefinieerd door de para meter **ValidatePattern** in te stellen op de reguliere expressie `VDI\d+` .

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## PARAMETERS

### -AliasDefinitions

Voegt de opgegeven aliassen toe aan sessies die gebruikmaken van het functie-functionaliteits bestand. Voer een hash-tabel in met de volgende sleutels:

- Naam. De naam van de alias. Deze sleutel is vereist.
- Waarde. De opdracht die wordt vertegenwoordigd door de alias. Deze sleutel is vereist.
- Beschrijving Een teken reeks waarmee de alias wordt beschreven. Deze sleutel is optioneel.
- Opties. Alias opties. Deze sleutel is optioneel. De standaard waarde is geen. De acceptabele waarden voor deze para meter zijn: geen, alleen-lezen, constant, privé of AllScope.

Bijvoorbeeld: `@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

Hiermee geeft u de assembly's op die moeten worden geladen in de sessies die gebruikmaken van het functie-functionaliteits bestand.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Author

Hiermee geeft u de gebruiker die het functie bestand heeft gemaakt.

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

### -CompanyName

Hiermee wordt het bedrijf geïdentificeerd dat het functie gegevensbestand heeft gemaakt.
De standaard waarde is onbekend.

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

### -Copyright

Hiermee geeft u een copyright op voor het functie-functionaliteits bestand. Als u deze para meter weglaat, `New-PSRoleCapabilityFile` genereert een copyright verklaring met behulp van de waarde van de para meter **Auteur** .

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

### -Beschrijving

Hiermee geeft u een beschrijving op voor het bestand met de functie mogelijkheid.

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

### -Omgevings variabelen

Hiermee geeft u de omgevings variabelen op voor sessies die dit functie gegevensbestand beschikbaar maken. Voer een hash-tabel in waarin de sleutels de namen van omgevings variabelen zijn en de waarden zijn de waarden van omgevings variabelen.

Bijvoorbeeld: `EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

Hiermee geeft u de indelings bestanden (. ps1xml) op die worden uitgevoerd in sessies die gebruikmaken van het functie-functionaliteits bestand. De waarde van deze para meter moet een volledig of absoluut pad van de indelings bestanden zijn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FunctionDefinitions

Voegt de opgegeven functies toe aan sessies die de functie mogelijkheid beschikbaar maken. Voer een hash-tabel in met de volgende sleutels:

- Naam. Naam van de functie. Deze sleutel is vereist.
- Script Block. Hoofd tekst van functie. Voer een script blok in. Deze sleutel is vereist.
- Opties. Functie opties. Deze sleutel is optioneel. De standaard waarde is geen. De acceptabele waarden voor deze para meter zijn: zijn geen, alleen-lezen, constant, privé of AllScope.

Bijvoorbeeld:

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GUID

Hiermee geeft u een unieke id op voor het bestand met de functie mogelijkheid. Als u deze para meter weglaat, `New-PSRoleCapabilityFile` genereert een GUID voor het bestand. Als u een nieuwe GUID wilt maken in Power shell, typt u `[guid]::NewGuid()` .

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Hiermee geeft u de modules op die automatisch worden geïmporteerd in sessies die gebruikmaken van het functie-functionaliteits bestand. Standaard zijn alle opdrachten in de weer gegeven modules zichtbaar. In combi natie met **VisibleCmdlets** of **VisibleFunctions** kunnen de opdrachten die zichtbaar zijn in de opgegeven modules worden beperkt.

Elke module die in de waarde van deze para meter wordt gebruikt, kan worden vertegenwoordigd door een teken reeks of een hash-tabel. Een module teken reeks bestaat alleen uit de naam van de module. Een module-hash-tabel kan **module** -, **ModuleVersion** -en **GUID** -sleutels bevatten. Alleen de **module** sleutel is vereist.

De volgende waarde bestaat bijvoorbeeld uit een teken reeks en een hash-tabel. Een combi natie van teken reeksen en hash-tabellen, in een wille keurige volg orde, is geldig.

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad en de bestands naam van het functie gegevensbestand. Het bestand moet een `.psrc` bestands extensie hebben.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

Hiermee geeft u scripts op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-functionaliteits bestand. Geef het pad en de bestands namen van de scripts op. De waarde van deze para meter moet een volledig of absoluut pad zijn van de namen van het script bestand.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypesToProcess

Hiermee geeft u type bestanden (. ps1xml) op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-Capability-bestand. Voer de bestands namen van het type in. De waarde van deze para meter moet een volledig of absoluut pad van het type filenames zijn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariableDefinitions

Hiermee geeft u variabelen op die moeten worden toegevoegd aan sessies die gebruikmaken van het functie-functionaliteits bestand. Voer een hash-tabel in met de volgende sleutels:

- Naam. De naam van de variabele. Deze sleutel is vereist.
- Waarde. Waarde van variabele. Deze sleutel is vereist.
- Opties. Variabele opties. Deze sleutel is optioneel. De standaard waarde is geen. De acceptabele waarden voor deze para meter zijn: zijn geen, alleen-lezen, constant, privé of AllScope.

Bijvoorbeeld: `@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleAliases

Beperkt de aliassen in de sessie met de aliassen die zijn opgegeven in de waarde van deze para meter, plus alle aliassen die u definieert in de para meter **AliasDefinition** . Joker tekens worden ondersteund.
Standaard worden alle aliassen die zijn gedefinieerd door de Power shell-engine en alle aliassen die modules exporteren, weer gegeven in de sessie.

Als u bijvoorbeeld de beschik bare aliassen wilt beperken tot GM en GCM, gebruikt u de volgende syntaxis: `VisibleAliases="gcm", "gp"`

Wanneer een **zicht bare** para meter is opgenomen in het functie-Capability-bestand, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.

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

### -VisibleCmdlets

Hiermee worden de cmdlets in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter. Joker tekens en modules met gekwalificeerde namen worden ondersteund.

Standaard worden alle cmdlets die de modules in de sessie exporteren, weer gegeven in de sessie. Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules en modules in de sessie worden geïmporteerd. Als er geen modules in **ModulesToImport** de cmdlet beschikbaar maken, `New-PSRoleCapabilityFile` probeert de juiste module te laden.

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleExternalCommands

Hiermee beperkt u de externe binaire bestanden, scripts en opdrachten die in de sessie kunnen worden uitgevoerd en die zijn opgegeven in de waarde van deze para meter.

Standaard zijn er in deze sessie geen externe opdrachten zichtbaar.

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VisibleFunctions

Hiermee beperkt u de functies in de sessie die zijn opgegeven in de waarde van deze para meter, plus de functies die u definieert in de para meter **FunctionDefinitions** . Joker tekens worden ondersteund.

Standaard zijn alle functies die door modules in de sessie worden geëxporteerd, zichtbaar in die sessie. Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules in de sessie worden geïmporteerd.

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

Hiermee worden de Power shell-providers in de sessie beperkt tot die welke zijn opgegeven in de waarde van deze para meter.
Joker tekens worden ondersteund.

Standaard worden alle providers die zijn geëxporteerd door een module in de sessie, weer gegeven in de sessie. Gebruik de para meters **SessionType** en **ModulesToImport** om te bepalen welke modules in de sessie worden geïmporteerd.

Wanneer een **zicht bare** para meter is opgenomen in het configuratie bestand van de sessie, verwijdert Power shell de `Import-Module` cmdlet en de bijbehorende `ipmo` alias uit de sessie.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Get-PSSessionCapability](Get-PSSessionCapability.md)
