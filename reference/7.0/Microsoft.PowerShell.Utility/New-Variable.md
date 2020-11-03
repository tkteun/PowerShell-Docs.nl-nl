---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: 8d45f8b6b0272394fe855be07243412bd3a15d71
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249546"
---
# New-Variable

## SAMENVATTING
Hiermee maakt u een nieuwe variabele.

## SYNTAXIS

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **new-variable** maakt u een nieuwe variabele in Power shell.
U kunt een waarde aan de variabele toewijzen tijdens het maken of de waarde toewijzen of wijzigen nadat deze is gemaakt.

U kunt de para meters van **new-variable** gebruiken om de eigenschappen van de variabele in te stellen, het bereik van een variabele in te stellen en te bepalen of variabelen openbaar of privé zijn.

Normaal gesp roken maakt u een nieuwe variabele door de naam van de variabele en de bijbehorende waarde te typen, zoals `$Var = 3` , maar u kunt de cmdlet **new-variable** gebruiken om de para meters te gebruiken.

## VOORBEELDEN

### Voor beeld 1: een variabele maken

```
PS C:\> New-Variable days
```

Met deze opdracht maakt u een nieuwe variabele met de naam Days.
U hoeft de para meter *name* niet te typen.

### Voor beeld 2: een variabele maken en hieraan een waarde toewijzen

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

Met deze opdracht maakt u een variabele met de naam ZipCode en wijst u deze toe aan de waarde 98033.

### Voor beeld 3: een variabele met de optie ReadOnly maken

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

In dit voor beeld ziet u hoe u de optie ReadOnly van **new-variable** gebruikt om een variabele te beschermen tegen overschrijven.

Met de eerste opdracht maakt u een nieuwe variabele met de naam Max en stelt u de waarde ervan in op 256.
De para meter *Option* wordt gebruikt met de waarde readonly.

Met de tweede opdracht wordt geprobeerd een tweede variabele met dezelfde naam te maken.
Met deze opdracht wordt een fout geretourneerd omdat de optie alleen-lezen is ingesteld voor de variabele.

De derde opdracht maakt gebruik van de para meter *Force* om de alleen-lezen beveiliging voor de variabele te onderdrukken.
In dit geval wordt de opdracht voor het maken van een nieuwe variabele met dezelfde naam geslaagd.

### Voor beeld 4: een persoonlijke variabele maken

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

Met deze opdracht wordt het gedrag van een persoonlijke variabele in een module gedemonstreerd.
De module bevat de cmdlet Get-Counter, die een persoonlijke variabele met de naam counter heeft.
De opdracht gebruikt de *zichtbaarheids* parameter met de waarde privé om de variabele te maken.

De voorbeeld uitvoer toont het gedrag van een persoonlijke variabele.
De gebruiker die de module heeft geladen kan de waarde van de item variabele niet weer geven of wijzigen, maar de teller variabele kan worden gelezen en gewijzigd door de opdrachten in de module.

### Voor beeld 5: een variabele met een spatie maken

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

Met deze opdracht wordt gedemonstreerd dat variabelen met spaties kunnen worden gemaakt.
De variabelen zijn toegankelijk met de cmdlet **Get-variable** of rechtstreeks door een variabele met accolades te scheiden.

## PARAMETERS

### -Beschrijving
Hiermee geeft u een beschrijving van de variabele.

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

### -Force
Geeft aan dat de cmdlet een variabele met dezelfde naam maakt als een bestaande alleen-lezen variabele.

Standaard kunt u een variabele overschrijven, tenzij de variabele een optie waarde ReadOnly of constant heeft.
Zie de para meter *Option* voor meer informatie.

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

### -Name
Hiermee geeft u een naam op voor de nieuwe variabele.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Optie
Hiermee geeft u de waarde van de eigenschap **Options** van de variabele. De acceptabele waarden voor deze para meter zijn:

- Geen.
Hiermee stelt u geen opties in.
(Geen is de standaard instelling.)
- Kenmerk.
Kan worden verwijderd.
Kan niet worden gewijzigd, behalve door gebruik te maken van de para meter *Forces* .
- Eigen.
De variabele is alleen beschikbaar in het huidige bereik.
- AllScope.
De variabele wordt gekopieerd naar nieuwe bereiken die worden gemaakt.
- Constant hoog.
Kan niet worden verwijderd of gewijzigd.
Constante is alleen geldig wanneer u een variabele maakt.
U kunt de opties van een bestaande variabele niet wijzigen in constante.

Als u de eigenschap **Options** van alle variabelen in de sessie wilt weer geven, typt u `Get-Variable | Format-Table -Property name, options -autosize` .

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
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
Hiermee wordt het bereik van de nieuwe variabele opgegeven.
De aanvaardbare waarden voor deze parameter zijn:

- Internationaal.
Variabelen die in het globale bereik zijn gemaakt, zijn overal toegankelijk in een Power Shell-proces.
- Lokale.
Het lokale bereik verwijst naar het huidige bereik. Dit kan elk bereik zijn, afhankelijk van de context.
- Schriften.
Variabelen die in het script bereik zijn gemaakt, zijn alleen toegankelijk in het script bestand of de module waarin ze zijn gemaakt.
- Eigen.
Variabelen die in het persoonlijke bereik zijn gemaakt, zijn niet toegankelijk buiten het bereik waarin ze zich bevinden.
U kunt een privé bereik gebruiken om een persoonlijke versie van een item met dezelfde naam in een ander bereik te maken.
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is, 1 de bovenliggende Scope, 2 het bovenliggende bereik, enzovoort).
Negatieve getallen kunnen niet worden gebruikt.

Local is het standaard bereik wanneer de para meter bereik niet is opgegeven.

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

### -Waarde
Hiermee geeft u de begin waarde van de variabele.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Zicht baarheid
Hiermee wordt bepaald of de variabele zichtbaar is buiten de sessie waarin deze is gemaakt.
Deze para meter is ontworpen voor gebruik in scripts en opdrachten die aan andere gebruikers worden geleverd.
De aanvaardbare waarden voor deze parameter zijn:

- Open.
De variabele is zichtbaar.
(Openbaar is de standaard instelling.)
- Eigen.
De variabele is niet zichtbaar.

Wanneer een variabele privé is, wordt deze niet weer gegeven in lijst met variabelen, zoals die worden geretourneerd door Get-variable of in weer gaven van de variabele: station.
Opdrachten om de waarde van een persoonlijke variabele te lezen of te wijzigen, retour neren een fout.
De gebruiker kan echter opdrachten uitvoeren die een persoonlijke variabele gebruiken als de opdrachten zijn geschreven in de sessie waarin de variabele is gedefinieerd.

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

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

### System. object
U kunt een waarde door sluizen naar een **nieuwe variabele**.

## UITVOER

### Geen of System. Management. Automation. PSVariable
Wanneer u de para meter *PassThru* gebruikt, genereert **new-variable** een **System. Management. Automation. PSVariable** -object dat de nieuwe variabele vertegenwoordigt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Clear-variabele](Clear-Variable.md)

[Get-variabele](Get-Variable.md)

[Remove-variabele](Remove-Variable.md)

[Set-variabele](Set-Variable.md)
