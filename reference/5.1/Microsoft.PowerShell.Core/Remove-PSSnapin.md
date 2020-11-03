---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250146"
---
# Remove-PSSnapin

## SAMENVATTING
Hiermee verwijdert u de Windows Power shell-modules uit de huidige sessie.

## SYNTAXIS

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Remove-PSSnapin** verwijdert een Windows Power shell-module uit de huidige sessie.
U kunt deze gebruiken om modules die u hebt toegevoegd aan Windows Power shell te verwijderen, u kunt deze cmdlet niet gebruiken om de modules te verwijderen die met Windows Power shell zijn geïnstalleerd.

Nadat u een module uit de huidige sessie hebt verwijderd, wordt de module nog steeds geladen, maar zijn de cmdlets en providers in de module niet meer beschikbaar in de sessie.

## VOORBEELDEN

### Voor beeld 1: een module verwijderen

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

Met deze opdracht wordt de **micro soft. Exchange** -module verwijderd uit de huidige sessie.
Wanneer de opdracht is voltooid, zijn de cmdlets en providers die door de module worden ondersteund, niet beschikbaar in de sessie.

### Voor beeld 2: modules verwijderen door gebruik te maken van namen met de pijp lijn

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

Met deze opdracht verwijdert u de Windows Power shell-modules die namen hebben die beginnen met smp vanuit de huidige sessie.

De opdracht maakt gebruik van de cmdlet **Get-PSSnapin** om objecten op te halen die de modules vertegenwoordigen. De pijplijn operator (|) verzendt de resultaten naar de cmdlet **Remove-PSSnapin** , die deze uit de sessie verwijdert.
De providers en cmdlets die in deze invoeg toepassing worden ondersteund, zijn niet meer beschikbaar in de sessie.

Wanneer u objecten pipet om **-PSSnapin te verwijderen** , worden de namen van de objecten gekoppeld aan de para meter *name* , waarmee objecten van de pijp lijn met een **naam** eigenschap worden geaccepteerd.

### Voor beeld 3: modules verwijderen met behulp van namen

```
PS C:\> Remove-PSSnapin -Name *event*
```

Met deze opdracht worden alle Windows Power shell-modules verwijderd met namen die gebeurtenis bevatten.

## PARAMETERS

### -Name
Hiermee geeft u de namen van Windows Power shell-modules die u wilt verwijderen uit de huidige sessie.
Joker tekens (*) zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru
Retourneert een object dat de module vertegenwoordigt.
Deze cmdlet genereert standaard geen uitvoer.

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
Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

### System. Management. Automation. PSSnapInInfo
U kunt een module-object door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. Management. Automation. PSSnapInInfo
Met deze cmdlet wordt een **System. Management. Automation. PSSnapInInfo** -object gegenereerd dat de module vertegenwoordigt, als u de para meter *PassThru* opgeeft.
Standaard wordt met **Remove-PSSnapin** geen uitvoer gegenereerd.

## OPMERKINGEN

* **Remove-PSSnapin** controleert de versie van Windows Power shell niet voordat een module uit de sessie wordt verwijderd. Als een module niet kan worden verwijderd, wordt een waarschuwing weer gegeven en mislukt de opdracht.
* **Remove-PSSnapin** is alleen van invloed op de huidige sessie. Als u een Add-PSSnapin-opdracht aan uw Windows Power shell-profiel hebt toegevoegd, moet u de opdracht verwijderen om de module uit toekomstige sessies te verwijderen. Typ voor instructies `Get-Help about_Profiles` .

## GERELATEERDE KOPPELINGEN

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)
