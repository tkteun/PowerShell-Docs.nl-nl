---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 89d1f319bdedc45646fca1cb7ca7e0f78ed88bbf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251305"
---
# Invoke-History

## SAMENVATTING
Voert opdrachten uit vanuit de sessie geschiedenis.

## SYNTAXIS

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Invoke-History` cmdlet voert opdrachten uit vanuit de sessie geschiedenis. U kunt objecten die de opdrachten vertegenwoordigen van Get-History door geven `Invoke-History` , of u kunt opdrachten in de huidige geschiedenis identificeren met behulp van hun **id-** nummer. Gebruik de cmdlet om het id-nummer van een opdracht te vinden `Get-History` .

De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.
Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen. Deze cmdlet werkt alleen met de sessie geschiedenis. Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: de meest recente opdracht in de geschiedenis uitvoeren

In dit voor beeld wordt de laatste, of meest recente, opdracht uitgevoerd in de sessie geschiedenis. U kunt deze opdracht afkorten als `r` de alias voor `Invoke-History` .

```powershell
Invoke-History
```

### Voor beeld 2: Voer de opdracht uit met een opgegeven ID

In dit voor beeld wordt de opdracht uitgevoerd in de sessie geschiedenis met de **Id** 132. Omdat de naam van de para meter **id** optioneel is, kunt u deze opdracht als volgt afkorten: `Invoke-History 132` , `ihy 132` of `r 132` .

```powershell
Invoke-History -Id 132
```

### Voor beeld 3: Voer de meest recente opdracht uit met behulp van de opdracht tekst

In dit voor beeld wordt de meest recente `Get-Process` opdracht uitgevoerd in de sessie geschiedenis. Wanneer u tekens voor de para meter **id** typt, `Invoke-History` wordt de eerste opdracht uitgevoerd die overeenkomt met het patroon, te beginnen met de meest recente opdrachten.

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> Joker tekens zijn niet hoofdletter gevoelig, maar het patroon komt overeen met het begin van de regel.

### Voor beeld 4: een reeks opdrachten uit de geschiedenis uitvoeren

In dit voor beeld worden de opdrachten 16 tot en met 24 uitgevoerd. Omdat u slechts één **id-** waarde kunt vermelden, gebruikt de opdracht de `ForEach-Object` cmdlet voor het uitvoeren `Invoke-History` van de opdracht één keer voor elke **id-** waarde.

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### Voorbeeld 5

In dit voor beeld worden de zeven opdrachten uitgevoerd in de geschiedenis die eindigen op de opdracht 255 (249 tot en met 255). De cmdlet wordt gebruikt `Get-History` om de opdrachten op te halen. Omdat u slechts één **id-** waarde kunt vermelden, gebruikt de opdracht de `ForEach-Object` cmdlet voor het uitvoeren `Invoke-History` van de opdracht één keer voor elke **id-** waarde.

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## PARAMETERS

### -Id

Hiermee geeft u de **id** op van een opdracht in de geschiedenis. U kunt het **id-** nummer van de opdracht of de eerste paar tekens van de opdracht typen.

Als u tekens typt, `Invoke-History` komt het eerst overeen met de meest recente opdrachten. Als u deze para meter weglaat, `Invoke-History` wordt de laatste of meest recente opdracht uitgevoerd. Gebruik de cmdlet om het **id-** nummer van een opdracht te vinden `Get-History` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System. String

U kunt een geschiedenis **-id** door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd, maar de uitvoer kan worden gegenereerd door de opdrachten die worden `Invoke-History` uitgevoerd.

## OPMERKINGEN

De sessie geschiedenis is een lijst met opdrachten die tijdens de sessie zijn ingevoerd. De sessie geschiedenis vertegenwoordigt de volg orde van de uitvoering, de status en de begin-en eind tijd van de opdracht. Bij het invoeren van elke opdracht voegt Power shell deze toe aan de geschiedenis zodat u deze opnieuw kunt gebruiken. Zie [about_History](About/about_History.md)voor meer informatie over de sessie geschiedenis.

U kunt ook verwijzen naar `Invoke-History` de ingebouwde aliassen `r` en `ihy` . Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Toevoegen-geschiedenis](Add-History.md)

[Wissen-geschiedenis](Clear-History.md)

[Get-geschiedenis](Get-History.md)

