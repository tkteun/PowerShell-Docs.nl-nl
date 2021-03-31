---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: 63e5fbfcce681a1c3d17959a486ee9ab1998741a
ms.sourcegitcommit: bdd0fedaf9ba534645b2f7eb1fe1241481f58715
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2021
ms.locfileid: "105936543"
---
# Get-TypeData

## Samen vatting
Hiermee worden de uitgebreide type gegevens in de huidige sessie opgehaald.

## Syntax

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## Description

De `Get-TypeData` cmdlet haalt de uitgebreide type gegevens in de huidige sessie op. Dit omvat type gegevens die zijn toegevoegd aan de sessie per `Types.ps1xml` bestand en dynamische type gegevens die zijn toegevoegd met behulp van de para meter van de `Update-TypeData` cmdlet.

U kunt de uitgebreide type gegevens gebruiken die `Get-TypeData` worden geretourneerd om de type gegevens in de sessie te controleren en deze naar `Update-TypeData` de `Remove-TypeData` cmdlets en te verzenden.

Uitgebreide-type gegevens voegen eigenschappen en methoden toe aan objecten in Power shell. U kunt de toegevoegde eigenschappen en methoden op dezelfde manier gebruiken als de eigenschappen en methoden die in het object type zijn gedefinieerd. Bij het schrijven van scripts moet u er echter rekening mee houden dat de toegevoegde eigenschappen en methoden mogelijk niet aanwezig zijn in elke Power shell-sessie.

`Types.ps1xml`Zie [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)voor meer informatie over bestanden. Zie voor meer informatie over dynamische type gegevens die door de `Update-TypeData` cmdlet worden toegevoegd `Update-TypeData` .

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## Voorbeelden

### Voor beeld 1: alle uitgebreide-type gegevens ophalen

In dit voor beeld worden alle uitgebreide type gegevens in de huidige sessie opgehaald.

 ```powershell
Get-TypeData
```

### Voor beeld 2: type gegevens ophalen op naam

In dit voor beeld worden alle type gegevens in de huidige sessie opgehaald waarvan de naam is gekwalificeerd met ' System.IO '.

```powershell
Get-TypeData -TypeName System.IO.*
```

```Output
TypeName                Members
--------                -------
System.IO.DirectoryInfo {[Mode, System.Management.Automation.Runspaces.CodePropert…
System.IO.FileInfo      {[Mode, System.Management.Automation.Runspaces.CodePropert…
```

### Voor beeld 3: het script blok ophalen waarmee een eigenschaps waarde wordt gemaakt

In dit voor beeld wordt het script blok opgehaald waarmee de waarde van de eigenschap **gebeurtenis** -Property van **EventLogEntry** -objecten wordt gemaakt.

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### Voor beeld 4: het script blok ophalen dat een eigenschap definieert voor een opgegeven object

In dit voor beeld wordt het script blok opgehaald dat de eigenschap **DateTime** van **System. datetime** -objecten in Power shell definieert.

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

De opdracht gebruikt de `Get-TypeData` cmdlet om de uitgebreide type gegevens voor het type **System. datum/tijd** op te halen. Met de opdracht wordt de eigenschap **Members** van het **TypeData** -object opgehaald.

De eigenschap **Members** bevat een hash-tabel met eigenschappen en methoden die zijn gedefinieerd door gegevens van uitgebreide typen. Elke sleutel in de hash-tabel van de leden is een eigenschaps-of methode naam en elke waarde is de definitie van de waarde van de eigenschap of methode.

Met de opdracht wordt de sleutel **DateTime** opgehaald in de **leden** en de waarde van de eigenschap **GetScriptBlock** .

In de uitvoer ziet u het script blok waarmee de waarde van de eigenschap **DateTime** van elk **System. datetime** -object in Power shell wordt gemaakt.

## Parameters

### -TypeName

Geeft type gegevens alleen als matrix voor de typen met de opgegeven namen. Standaard worden `Get-TypeData` alle typen in de sessie opgehaald.

Geef type namen of een naam patroon op. Volledige namen of naam patronen met Joker tekens zijn vereist, zelfs voor typen in de naam ruimte van het systeem. Joker tekens worden ondersteund en de para meter naam **TypeName** is optioneel. U kunt ook de naam van een type pipe naar `Get-TypeData` .

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### System. String

U kunt typen van het type sluizen naar `Get-TypeData` .

## Uitvoerwaarden

### System. Management. Automation. Runspaces. TypeData

## Notities

`Get-TypeData` haalt alleen de uitgebreide type gegevens in de huidige sessie op. Er worden geen uitgebreide type gegevens opgehaald die zich op de computer bevinden, maar die niet zijn toegevoegd aan de huidige sessie, zoals uitgebreide typen die zijn gedefinieerd in modules die niet in de huidige sessie zijn geïmporteerd.

## Verwante koppelingen

[about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Remove-TypeData](Remove-TypeData.md)

[Update-TypeData](Update-TypeData.md)
