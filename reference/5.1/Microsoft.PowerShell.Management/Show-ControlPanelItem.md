---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250544"
---
# Show-ControlPanelItem

## SAMENVATTING
Hiermee opent u configuratie scherm-onderdelen.

## SYNTAXIS

### Regulierenaam (standaard)

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### Canoniekenaam

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### ControlPanelItem

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet worden de `Show-ControlPanelItem` onderdelen van het configuratie scherm op de lokale computer geopend. U kunt het gebruiken om de onderdelen van het configuratie scherm te openen op naam, categorie of beschrijving, zelfs op systemen die geen gebruikers interface hebben. U kunt de onderdelen van het configuratie scherm van de `Get-ControlPanelItem` cmdlet naar gebruiken `Show-ControlPanelItem` .

`Show-ControlPanelItem` doorzoekt alleen configuratie scherm-items die kunnen worden geopend op het systeem. Op computers die geen **configuratie scherm** of **bestanden Verkenner** hebben, worden `Show-ControlPanelItem` alleen de configuratie scherm-items die zonder deze onderdelen kunnen worden geopend, doorzocht.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0 en werkt onder Windows 8, Windows Server 2012 en hogere versies.

## VOORBEELDEN

### Voor beeld 1: een onderdeel van het configuratie scherm weer geven

In dit voor beeld wordt het onderdeel **AutoPlay** van het configuratie scherm gestart.

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### Voor beeld 2: een item van het configuratie scherm naar deze cmdlet Pipeen

In dit voor beeld wordt het onderdeel **Windows Defender firewall** -configuratie scherm op de lokale computer geopend.
De naam van het onderdeel Windows Firewall configuratie scherm is gewijzigd via de Windows-versies. In dit voor beeld wordt een Joker patroon gebruikt om het onderdeel van het configuratie scherm te vinden.

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem` Hiermee wordt het onderdeel van het configuratie scherm opgehaald en de `Show-ControlPanelItem` cmdlet wordt geopend.

### Voor beeld 3: een bestands naam gebruiken om een onderdeel van het configuratie scherm te openen

In dit voor beeld wordt het onderdeel **Program ma's en onderdelen** van het configuratie scherm geopend met behulp van de toepassings naam.

```powershell
appwiz.cpl
```

Deze methode is een alternatief voor het gebruik van een `Show-ControlPanelItem` opdracht.

> [!NOTE]
> In Power shell kunt u de extensie. cpl voor configuratie scherm-bestanden weglaten, omdat deze deel uitmaakt van de waarde van de `$env:PathExt` omgevings variabele.

## PARAMETERS

### -Canoniekenaam

Hiermee geeft u onderdelen van het configuratie scherm met behulp van de opgegeven canonieke namen of naam patronen. Joker tekens zijn toegestaan. Als u meerdere namen opgeeft, opent deze cmdlet configuratie scherm-items die overeenkomen met een van de namen, alsof de items in de naam lijst zijn gescheiden door een **or** -operator.

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

### -Input object

Hiermee geeft u de configuratie scherm-items die moeten worden geopend door het verzenden van item objecten van het configuratie scherm. Voer een variabele in die onderdeel objecten van het configuratie scherm bevat, of typ een opdracht of expressie waarmee de object objecten van het configuratie scherm worden opgehaald, zoals `Get-ControlPanelItem` .

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen van de onderdelen van het configuratie scherm. Joker tekens zijn toegestaan. Als u meerdere namen opgeeft, opent deze cmdlet configuratie scherm-items die overeenkomen met een van de namen, alsof de items in de naam lijst zijn gescheiden door een **or** -operator.

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String, micro soft. Power shell. commands. ControlPanelItem

U kunt een naam of item object van het configuratie scherm door geven aan deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-ControlPanelItem](Get-ControlPanelItem.md)
