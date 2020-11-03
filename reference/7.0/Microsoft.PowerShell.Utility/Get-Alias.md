---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: 98f68cff8501fec375e3a2b8ac446e41d5721fc7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249637"
---
# Get-Alias

## SAMENVATTING
Hiermee worden de aliassen opgehaald voor de huidige sessie.

## SYNTAXIS

### Standaard (standaard instelling)

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### Definitie

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Get-alias** worden de aliassen in de huidige sessie opgehaald.
Dit omvat ingebouwde aliassen, aliassen die u hebt ingesteld of geïmporteerd en aliassen die u hebt toegevoegd aan uw Power shell-profiel.

**Get-alias** gebruikt standaard een alias en retourneert de naam van de opdracht.
Wanneer u de para meter *definitie* gebruikt, neemt **Get-alias** de naam van een opdracht en worden de aliassen ervan geretourneerd.

Vanaf Windows Power Shell 3,0 worden met **Get-alias** niet-afgebroken alias namen weer gegeven in een `<alias> -> <definition>` indeling zodat u de informatie die u nodig hebt, nog gemakkelijker kunt vinden.

## VOORBEELDEN

### Voor beeld 1: alle aliassen in de huidige sessie ophalen

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

Met deze opdracht worden alle aliassen in de huidige sessie opgehaald.

In de uitvoer ziet u de `<alias> -> <definition>` indeling die is geïntroduceerd in Windows Power shell 3,0.
Deze indeling wordt alleen gebruikt voor aliassen die geen afbreek streepjes bevatten, omdat aliassen met afbreek streepjes doorgaans voorkeurs namen voor cmdlets en functions zijn, in plaats van bijnamen.

### Voor beeld 2: aliassen op naam ophalen

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

Met deze opdracht worden alle aliassen opgehaald die beginnen met GP of SP, met uitzonde ring van aliassen die eindigen op PS.

### Voor beeld 3: aliassen voor een cmdlet ophalen

```powershell
Get-Alias -Definition Get-ChildItem
```

Met deze opdracht worden de aliassen voor de Get-ChildItem-cmdlet opgehaald.

Standaard haalt de **Get-alias** -cmdlet de item naam op wanneer u de alias kent.
De para meter *definitie* haalt de alias op wanneer u de naam van het item kent.

### Voor beeld 4: aliassen ophalen op basis van eigenschap

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

Met deze opdracht worden alle aliassen opgehaald waarin de waarde van de eigenschap Options alleen-lezen is.
Deze opdracht biedt een snelle manier om de aliassen te vinden die zijn ingebouwd in Power shell, omdat ze de optie ReadOnly hebben.

Opties is slechts één eigenschap van de AliasInfo-objecten die **Get-alias** krijgt.
Als u alle eigenschappen en methoden van AliasInfo-objecten wilt zoeken, typt u `Get-Alias | get-member` .

### Voor beeld 5: aliassen ophalen op naam en filteren op begin letter

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

In dit voor beeld worden aliassen opgehaald voor opdrachten die een naam hebben die eindigt op '-PSSession ', met uitzonde ring van die beginnen met ' e '.

De opdracht maakt gebruik van de para meter *Scope* om de opdracht in het globale bereik toe te passen.
Dit is handig in scripts wanneer u de aliassen in de sessie wilt ophalen.

## PARAMETERS

### -Definitie

Hiermee worden de aliassen voor het opgegeven item opgehaald.
Voer de naam in van een cmdlet, een functie, een script, een bestand of een uitvoerbaar bestand.

Deze para meter wordt *definitie* genoemd, omdat hiermee wordt gezocht naar de naam van het item in de eigenschap definitie van het object alias.

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Uitsluiten

De opgegeven items worden wegge laten.
De waarde van deze para meter komt in aanmerking voor de naam en de definitie parameters.
Voer een naam, een definitie of een patroon in, zoals ' s * '.
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

Hiermee geeft u de aliassen op die met deze cmdlet worden opgehaald.
Joker tekens zijn toegestaan.
`Get-Alias`Haalt standaard alle aliassen op die zijn gedefinieerd voor de huidige sessie.
De parameter naam **naam** is optioneel.
U kunt ook de namen van de aliassen door sluizen naar `Get-Alias` .

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Bereik

Hiermee geeft u het bereik waarvoor deze cmdlet aliassen ophaalt.
De aanvaardbare waarden voor deze parameter zijn:

- Globaal
- Lokaal
- Script
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)

Local is de standaard instelling.
Zie about_Scopes voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt de namen van de aliassen van een sluis naar **Get-alias**.

## UITVOER

### System. Management. Automation. AliasInfo

**Get-alias** retourneert een object dat staat voor elke alias.
**Get-alias** retourneert hetzelfde object voor elke alias, maar Power shell gebruikt een op een pijl gebaseerde indeling om de namen van niet-afgebroken aliassen weer te geven.

## OPMERKINGEN

- Als u een nieuwe alias wilt maken, gebruikt u Set-Alias of New alias. Als u een alias wilt verwijderen, gebruikt u Remove-item.
- De op de pijl gebaseerde alias naam indeling wordt niet gebruikt voor aliassen die een koppel teken bevatten. Dit zijn waarschijnlijk de voorkeurs vervangende namen voor cmdlets en functions, in plaats van gebruikelijke afkortingen of bijnamen.

## GERELATEERDE KOPPELINGEN

[Exporteren-alias](Export-Alias.md)

[Import-alias](Import-Alias.md)

[Nieuwe alias](New-Alias.md)

[Set-alias](Set-Alias.md)

[Alias provider](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)
