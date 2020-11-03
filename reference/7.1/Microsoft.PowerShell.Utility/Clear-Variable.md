---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: e42371a58b49a25a9aaf0cc60551ff4bf27e2ec4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251343"
---
# Clear-Variable

## SAMENVATTING
Hiermee verwijdert u de waarde van een variabele.

## SYNTAXIS

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Clear-variable** worden de gegevens verwijderd die zijn opgeslagen in een variabele, maar wordt de variabele niet verwijderd.
Als gevolg hiervan is de waarde van de variabele NULL (leeg).
Als de variabele een opgegeven gegevens-of object type heeft, behoudt deze cmdlet het type van het object dat is opgeslagen in de variabele.

## VOORBEELDEN

### Voor beeld 1: de waarde van globale variabelen verwijderen die beginnen met een zoek reeks

```
PS C:\> Clear-Variable my* -Scope Global
```

Met deze opdracht wordt de waarde van globale variabelen verwijderd die namen hebben die met mijn beginnen.

### Voor beeld 2: een variabele in een onderliggend bereik wissen, maar niet het bovenliggende bereik

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

Deze opdrachten laten zien dat het wissen van een variabele in een onderliggend bereik de waarde in het bovenliggende bereik niet wist.
Met de eerste opdracht wordt de waarde van de variabele $A ingesteld op 3.
Met de tweede opdracht wordt de operator Invoke (&) gebruikt voor het uitvoeren van de opdracht voor het **wissen van variabelen** in een nieuwe scope.
De variabele wordt in het onderliggende bereik gewist (hoewel deze niet bestaat), maar wordt niet gewist in het lokale bereik.
De derde opdracht, waarmee de waarde van $A wordt opgehaald, geeft aan dat de waarde 3 niet van invloed is.

### Voor beeld 3: de waarde van de opgegeven variabele verwijderen

```
PS C:\> Clear-Variable -Name "Processes"
```

Met deze opdracht wordt de waarde van de variabele met de naam processs verwijderd.
Nadat de-cmdlet de bewerking heeft voltooid, bestaat de variabele met de naam processen nog steeds, maar is de waarde Null.

## PARAMETERS

### -Uitsluiten

Hiermee wordt een matrix opgegeven met items die met deze cmdlet worden wegge laten in de bewerking.
De waarde van deze para meter komt in aanmerking voor de para meter *name* .
Voer een naam element of patroon in, zoals ' s * '.
Joker tekens zijn toegestaan.

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

### -Force

Hiermee kan de cmdlet een variabele wissen, zelfs als deze alleen-lezen is.
Zelfs met de para meter Forces kan de cmdlet geen constanten wissen.

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

### -Include

Hiermee geeft u een matrix van items op die met deze cmdlet worden opgenomen in de bewerking.
De waarde van deze para meter komt in aanmerking voor de para meter *name* .
Voer een naam element of patroon in, zoals ' s * '.
Joker tekens zijn toegestaan.

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

Hiermee geeft u de naam van de variabele die moet worden gewist.
Joker tekens zijn toegestaan.
Deze para meter is vereist, maar de parameter naam ("naam") is optioneel.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
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

### -Bereik

Hiermee geeft u het bereik op waarin deze alias geldig is.

De aanvaardbare waarden voor deze parameter zijn:

- Globaal
- Lokaal
- Script

U kunt ook een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken), waarbij 0 het huidige bereik is en 1 de bovenliggende Scope.
Local is de standaard instelling.
Zie about_Scopes voor meer informatie.

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

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen of System. Management. Automation. PSVariable

Wanneer u de para meter *PassThru* gebruikt, genereert deze cmdlet een **System. Management. Automation. PSVariable** -object dat de gewiste variabele vertegenwoordigt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* Als u een variabele wilt verwijderen, samen met de bijbehorende waarde, gebruikt u Remove-Variable of verwijderen.

  Met deze cmdlet worden de waarden van variabelen die zijn ingesteld als constanten of het eigendom van het systeem, zelfs niet verwijderd als u de para meter *Forces* gebruikt.

  Als de variabele die u wist niet bestaat, heeft de cmdlet geen effect.
Er wordt geen variabele met een null-waarde gemaakt.

  U kunt ook verwijzen naar een **duidelijke variabele** met de ingebouwde alias CLV.
Zie about_Aliases voor meer informatie.

*

## GERELATEERDE KOPPELINGEN

[Get-variabele](Get-Variable.md)

[Nieuwe variabele](New-Variable.md)

[Remove-variabele](Remove-Variable.md)

[Set-variabele](Set-Variable.md)

