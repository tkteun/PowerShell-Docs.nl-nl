---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250341"
---
# Test-DscConfiguration

## SAMENVATTING
Test of de werkelijke configuratie van de knoop punten overeenkomt met de gewenste configuratie.

## SYNTAXIS

### ComputerNameSet (standaard)

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### ComputerNameAndPathSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### ComputerNameAndReferenceConfigurationSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionAndPathSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### CimSessionAndReferenceConfigurationSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **test-DscConfiguration** wordt getest of de werkelijke configuratie van de knoop punten overeenkomt met de gewenste configuratie.
Geef op welke computers u wilt testen configuraties met behulp van computer namen of Common Information Model (CIM)-sessies.
Als u geen doel computer opgeeft, test de cmdlet de configuratie van de lokale computer.

Als de gewenste en werkelijke configuraties overeenkomen, retourneert de cmdlet de teken reeks waarde ' True '.
Anders wordt de teken reeks waarde ' false ' geretourneerd.

## VOORBEELDEN

### Voor beeld 1: configuratie testen voor de lokale computer

```
PS C:\> Test-DscConfiguration
```

Met deze opdracht wordt de configuratie voor de lokale computer getest.

### Voor beeld 2: configuratie testen voor een opgegeven computer

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

Dit voor beeld test configuratie van een computer die is opgegeven door een CIM-sessie.
In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.
U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.

Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.
De opdracht vraagt u om een wacht woord.
Typ `Get-Help New-CimSession` voor meer informatie.

Met de tweede opdracht wordt de configuratie getest voor de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de variabele $Session, in dit geval de computer met de naam Server01.

### Voor beeld 3: test configuraties met gedetailleerde resultaten

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

Met deze opdracht worden configuraties getest voor een set computers die is opgegeven door de para meter *ComputerName* en wordt gedetailleerde informatie geretourneerd die de algehele status bevat, resources die de gewenste status hebben, resources die niet de gewenste status en computer naam hebben.

### Voor beeld 4: test configuraties die zijn opgegeven in een map

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

Met deze opdracht worden configuraties getest die zijn gedefinieerd in een map die is opgegeven door de para meter *Path* .
De configuraties worden getest op basis van een set computers, die elk worden geïdentificeerd door de bestands naam van het configuratie bestand.

### Voor beeld 5: test configuraties die zijn opgegeven in een bestand

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

Met deze opdracht test u een configuratie die is gedefinieerd in een bestand op basis van een set computers die is opgegeven door de para meter *ComputerName* .

## PARAMETERS

### -AsJob
Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.

Als u de para meter *AsJob* opgeeft, retourneert de opdracht een object dat de taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.
U kunt in de sessie blijven werken totdat de taak is voltooid.
De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer.
Gebruik de taak-cmdlets om de taak te beheren.
Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.

Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang en op Windows Vista en latere versies van het Windows-besturings systeem, moet u Windows Power shell openen met de optie als administrator uitvoeren.
Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.

Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.

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

### -CimSession
Voert de cmdlet uit in een externe sessie of op een externe computer.
Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .
De standaard waarde is de huidige sessie op de lokale computer.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Hiermee geeft u een matrix met computer namen op waarop met deze cmdlet de configuratie wordt getest.
De cmdlet test het configuratie document op de locatie die is opgegeven door de para meter *Path* naar deze computers.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
Hiermee geeft u een gebruikers naam en wacht woord op als een **PSCredential** -object voor de doel computer.
Als u een **PSCredential** -object wilt ophalen, gebruikt u de cmdlet Get-Credential.
Typ `Get-Help Get-Credential` voor meer informatie.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Gedetailleerd
Geeft aan dat deze cmdlet een gedetailleerd resultaat retourneert van het vergelijken van het configuratie document met de gewenste status van de knoop punten.
Het resultaat bevat informatie zoals de algemene status, resources met de gewenste status, resources die niet de gewenste status hebben en de computer naam.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Hiermee geeft u het pad op van een map die configuratie document bestanden bevat.
De cmdlet test de configuratie op basis van de gewenste status van de computers die zijn opgegeven door de para meter *ComputerName* of *CimSession* .

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceConfiguration
Hiermee geeft u het pad van het configuratie document bestand.
Met deze cmdlet wordt de configuratie getest op basis van de werkelijke status van de computers die zijn opgegeven door de para meter *ComputerName* of *CimSession* .

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.
Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.
De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.

```yaml
Type: System.Int32
Parameter Sets: (All)
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

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)
