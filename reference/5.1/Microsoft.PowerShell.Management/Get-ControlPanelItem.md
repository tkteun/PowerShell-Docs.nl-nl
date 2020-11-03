---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250810"
---
# Get-ControlPanelItem

## SAMENVATTING
Hiermee worden de onderdelen van het configuratie scherm opgehaald.

## SYNTAXIS

### Regulierenaam (standaard)

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### Canoniekenaam

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

`Get-ControlPanelItem`Met de cmdlet worden configuratie scherm-onderdelen op de lokale computer opgehaald. U kunt het gebruiken om de onderdelen van het configuratie scherm te vinden op naam, categorie of beschrijving, zelfs op systemen die geen gebruikers interface hebben.

Met deze cmdlet worden alleen de onderdelen van het configuratie scherm opgehaald die op het systeem kunnen worden geopend. Op computers die geen configuratie scherm of bestanden Verkenner hebben, worden met deze cmdlet alleen de onderdelen van het configuratie scherm weer gegeven die zonder deze onderdelen kunnen worden geopend.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0. Het werkt alleen op Windows 8 en Windows Server 2012 en nieuwer.

## VOORBEELDEN

### Voor beeld 1: alle configuratie scherm-items ophalen

Met deze opdracht worden alle configuratie scherm-onderdelen op de lokale computer opgehaald.

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### Voor beeld 2: onderdelen van het configuratie scherm op naam ophalen

In dit voor beeld worden de onderdelen van het configuratie scherm met het programma of de app in hun naam opgehaald.

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### Voor beeld 3: onderdelen van het configuratie scherm op categorie ophalen

Met deze opdracht worden alle configuratie scherm-items in categorieën met beveiliging in hun namen.

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### Voor beeld 4: een configuratie scherm-item openen

In dit voor beeld wordt het onderdeel Windows Firewall configuratie scherm op de lokale computer geopend.

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem`Met de cmdlet wordt het onderdeel van het configuratie scherm opgehaald. De `Show-ControlPanelItem` cmdlet wordt geopend.

### Voor beeld 5: onderdelen van het configuratie scherm ophalen op een externe computer

In dit voor beeld wordt het BitLocker-stationsversleuteling onderdeel van het configuratie scherm op de externe computer Server01.
De `Invoke-Command` cmdlet voert de `Get-ControlPanelItem` cmdlet op afstand uit.

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### Voor beeld 6: zoeken in de beschrijvingen van de onderdelen van het configuratie scherm

In dit voor beeld wordt gezocht naar de eigenschap **Description** van de onderdelen van het configuratie scherm om alleen de eigenschappen te verkrijgen die het naam **apparaat** bevatten.

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

`Get-ControlPanelItem`Met de cmdlet worden alle configuratie scherm-items opgehaald. `Where-Object`Met de cmdlet worden de items gefilterd op de waarde van de eigenschap **Description** .

## PARAMETERS

### -Canoniekenaam

Hiermee geeft u als een teken reeks matrix de onderdelen van het configuratie scherm op basis van hun canonieke namen of naam patronen die met deze cmdlet worden opgehaald. Joker tekens zijn toegestaan. Als u meerdere namen opgeeft, haalt deze cmdlet configuratie scherm-items die overeenkomen met een van de namen, alsof de items in de naam lijst zijn gescheiden door een ' or '-operator.

Met deze cmdlet worden standaard alle configuratie scherm-onderdelen in het systeem opgehaald.

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Categorie

Hiermee geeft u als een teken reeks matrix de categorieën van de onderdelen van het configuratie scherm in de opgegeven categorieën op die met deze cmdlet worden opgehaald. Voer een categorie naam of naam patroon in. Joker tekens zijn toegestaan. Als u meerdere namen opgeeft, haalt deze cmdlet configuratie scherm-items die overeenkomen met een van de namen, alsof de items in de naam lijst zijn gescheiden door een ' or '-operator. Met deze cmdlet worden standaard alle configuratie scherm-onderdelen in het systeem opgehaald.

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

### -Name

Hiermee geeft u als een teken reeks matrix de namen of naam patronen van het configuratie scherm die met deze cmdlet worden opgehaald.
Joker tekens zijn toegestaan. U kunt ook een naam-of naam patroon door geven aan deze cmdlet.

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een naam-of naam patroon door sluizen naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. ControlPanelItem

Met deze cmdlet worden configuratie scherm-onderdelen op de lokale computer opgehaald.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Show-ControlPanelItem](Show-ControlPanelItem.md)
