---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250811"
---
# Get-ComputerRestorePoint

## SAMENVATTING
Hiermee worden de herstel punten op de lokale computer opgehaald.

## SYNTAXIS

### ID (standaard)

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### LastStatus

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## BESCHRIJVING

De `Get-ComputerRestorePoint` cmdlet haalt de systeem herstel punten van de lokale computer op. En kan de status van de meest recente poging voor het herstellen van de computer weer geven.

U kunt de informatie uit gebruiken `Get-ComputerRestorePoint` om een herstel punt te selecteren. Gebruik bijvoorbeeld een Volg nummer om een herstel punt voor de cmdlet te identificeren `Restore-Computer` .

Systeem herstel punten en de `Get-ComputerRestorePoint` cmdlet worden alleen ondersteund op client besturingssystemen zoals Windows 10, Windows 7, Windows Vista en Windows XP.

## VOORBEELDEN

### Voor beeld 1: alle systeem herstel punten ophalen

In dit voor beeld worden `Get-ComputerRestorePoint` alle systeem herstel punten van de lokale computer opgehaald.

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### Voor beeld 2: specifieke Volg nummers ophalen

In dit voor beeld worden systeem herstel punten voor specifieke Volg nummers opgehaald.

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

`Get-ComputerRestorePoint` maakt gebruik van de para meter **RestorePoint** om een door komma's gescheiden matrix met Volg nummers op te geven.

### Voor beeld 3: de status van een systeem herstel weer geven

In dit voor beeld wordt de status van de meest recente systeem herstel op de lokale computer weer gegeven.

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

`Get-ComputerRestorePoint` maakt gebruik van de para meter **LastStatus** om het resultaat van de meest recente systeem herstel weer te geven.

### Voor beeld 4: een expressie gebruiken om de CreationTime te converteren

`Get-ComputerRestorePoint` Hiermee wordt de **CreationTime** uitgevoerd als een datum-en tijd teken reeks van het Windows Management Instrumentation (WMI).

In dit voor beeld slaat een variabele een expressie op die de **CreationTime** -teken reeks converteert naar een **DateTime** -object. Als u **CreationTime** -teken reeksen wilt bekijken voordat ze worden geconverteerd, gebruikt u een opdracht zoals `((Get-ComputerRestorePoint).CreationTime)` . Zie [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime)voor meer informatie over de datum en tijd van de WMI-teken reeks.

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

De `$date` variabele bevat een hash-tabel met de expressie die gebruikmaakt van de methode **ConvertToDateTime** . Met de expressie wordt de waarde van de eigenschap **CreationTime** van een WMI-teken reeks geconverteerd naar een **DateTime** -object.

`Get-ComputerRestorePoint` Hiermee verzendt u de systeem herstel punt objecten omlaag in de pijp lijn. `Select-Object` gebruikt de para meter **Property** om de eigenschappen op te geven die moeten worden weer gegeven. Voor elk object in de pijp lijn wordt met de expressie in de `$date` **CreationTime** geconverteerd en wordt het resultaat in de **datum** eigenschap uitgevoerd.

### Voor beeld 5: een eigenschap gebruiken om een Volg nummer op te halen

In dit voor beeld wordt een Volg nummer opgehaald met behulp van de eigenschap **SequenceNumber** en een matrix index. De uitvoer bevat alleen het volgorde nummer.

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

`Get-ComputerRestorePoint` maakt gebruik van de eigenschap **SequenceNumber** met een matrix index. De matrix index van `-1` haalt het meest recente volgorde nummer op in de matrix.

## PARAMETERS

### -LastStatus

Hiermee wordt aangegeven dat `Get-ComputerRestorePoint` de status van de meest recente systeem herstel bewerking wordt opgehaald.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePoint

Hiermee geeft u de Volg nummers van de systeem herstel punten. U kunt een enkel volg nummer of een door komma's gescheiden matrix met Volg nummers opgeven.

Als de para meter **RestorePoint** niet is opgegeven, `Get-ComputerRestorePoint` retourneert alle systeem herstel punten van de lokale computer.

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar beneden verplaatsen in de pijp lijn `Get-ComputerRestorePoint` .

## UITVOER

### System. Management. ManagementObject # root\default\SystemRestore of String

`Get-ComputerRestorePoint` retourneert een **SystemRestore** -object, een exemplaar van de klasse Windows Management INSTRUMENTATION (WMI) **SystemRestore** .

Wanneer u de para meter **LastStatus** gebruikt, `Get-ComputerRestorePoint` retourneert een teken reeks.

## OPMERKINGEN

Als u een `Get-ComputerRestorePoint` opdracht wilt uitvoeren in Windows Vista en latere versies van Windows, opent u Power shell met de optie **als administrator uitvoeren** .

`Get-ComputerRestorePoint` maakt gebruik van de WMI-klasse **SystemRestore** .

## GERELATEERDE KOPPELINGEN

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Enable-ComputerRestore](Enable-ComputerRestore.md)

[Restart-Computer](Restart-Computer.md)

[Herstellen-computer](Restore-Computer.md)

[SystemRestore](/windows/win32/sr/systemrestore)
