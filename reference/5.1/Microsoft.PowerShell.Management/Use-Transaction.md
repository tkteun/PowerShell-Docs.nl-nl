---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/use-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Use-Transaction
ms.openlocfilehash: db8423aef6dc4b25c4ddd13f9b29b774463c6a6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250532"
---
# Use-Transaction

## SAMENVATTING
Voegt het script blok toe aan de actieve trans actie.

## SYNTAXIS

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **use-trans actie** wordt een script blok toegevoegd aan een actieve trans actie.
Hiermee kunt u scripts transactioneel uitvoeren met behulp van Microsoft .NET Framework-objecten met trans acties.
Het script blok kan alleen objecten bevatten waarvoor trans acties zijn ingeschakeld .NET Framework, zoals exemplaren van de klasse micro soft. Power shell. commands. Management. TransactedString.

De para meter *UseTransaction* , die optioneel is voor de meeste cmdlets, is vereist wanneer u deze cmdlet gebruikt.

**Use-Trans Action** is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.
Zie about_Transactions voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: script met behulp van een object waarvoor trans acties zijn ingeschakeld

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> $transactedString.ToString()
Hello
PS C:\> Use-Transaction -TransactedScript { $transactedString.ToString() } -UseTransaction
Hello, World
PS C:\> Complete-Transaction
PS C:\> $transactedString.ToString()
Hello, World
```

In dit voor beeld ziet u hoe u **met behulp van-trans actie** script kunt gebruiken voor een .NET Framework object waarvoor een trans actie is ingeschakeld.
In dit geval is het object een **TransactedString** -object.

De eerste opdracht gebruikt de cmdlet Start-Transaction om een trans actie te starten.

De tweede opdracht maakt gebruik van de New-Object opdracht voor het maken van een **TransactedString** -object.
Het object wordt opgeslagen in de variabele $TransactedString.

De derde en vierde opdracht gebruiken beide de methode **Append** van het object **TransactedString** om tekst toe te voegen aan de waarde van $TransactedString.
Eén opdracht maakt deel uit van de trans actie.
De andere opdracht is niet.

De derde opdracht maakt gebruik van de methode **Append** van de transactionele teken reeks om Hello toe te voegen aan de waarde van $TransactedString.
Omdat de opdracht geen deel uitmaakt van de trans actie, wordt de wijziging onmiddellijk toegepast.

De vierde opdracht maakt **gebruik van een trans actie** om tekst toe te voegen aan de teken reeks in de trans actie.
De opdracht gebruikt de methode **Append** om ', World ' toe te voegen aan de waarde van $TransactedString.
De opdracht bevindt zich tussen accolades ( {} ) om het een script blok te maken.
De para meter *UseTransaction* is vereist in deze opdracht.

De vijfde en zesde opdrachten gebruiken de **toString** -methode van het object **TransactedString** om de waarde van de **TransactedString** als een teken reeks weer te geven.
De ene opdracht maakt deel uit van de trans actie.
De andere trans actie is niet.

De vijfde opdracht maakt gebruik van de **toString** -methode om de huidige waarde van de variabele $TransactedString weer te geven.
Omdat deze geen deel uitmaakt van de trans actie, wordt alleen de huidige status van de teken reeks weer gegeven.

De zesde opdracht gebruikt **gebruik-trans actie** om dezelfde opdracht uit te voeren in de trans actie.
Omdat de opdracht deel uitmaakt van de trans actie, wordt de huidige waarde van de teken reeks in de trans actie weer gegeven, net zoals een voor beeld van de trans actie wordt gewijzigd.

De zevende opdracht maakt gebruik van de Complete-Transaction cmdlet om de trans actie door te voeren.

De laatste opdracht gebruikt de **toString** -methode om de resulterende waarde van de variabele als een teken reeks weer te geven.

### Voor beeld 2: terugdraaien van een trans actie

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

In dit voor beeld ziet u het effect van het terugdraaien van een trans actie met de opdrachten voor **gebruik van trans acties** .
Net als bij alle opdrachten in een trans actie, worden de transactionele wijzigingen genegeerd en blijven de gegevens ongewijzigd wanneer de trans actie wordt teruggedraaid.

De eerste opdracht maakt gebruik van **Start-trans actie** om een trans actie te starten.

De tweede opdracht maakt gebruik van **New-object** om een **TransactedString** -object te maken.
Het object wordt opgeslagen in de variabele $TransactedString.

De derde opdracht, die geen deel uitmaakt van de trans actie, gebruikt de methode **Append** om ' Hello ' toe te voegen aan de waarde van $TransactedString.

De vierde opdracht gebruikt **gebruik-trans actie** om een andere opdracht uit te voeren die gebruikmaakt van de methode **Append** in de trans actie.
De opdracht gebruikt de methode **Append** om ', World ' toe te voegen aan de waarde van $TransactedString.

De vijfde opdracht maakt gebruik van de cmdlet Undo-Transaction om de trans actie terug te draaien.
Als gevolg hiervan worden alle opdrachten die in de trans actie worden uitgevoerd, omgekeerd.

De laatste opdracht gebruikt de **toString** -methode om de resulterende waarde van $TransactedString als een teken reeks weer te geven.
De resultaten geven aan dat alleen de wijzigingen die buiten de trans actie zijn aangebracht, zijn toegepast op het object.

## PARAMETERS

### -TransactedScript
Hiermee geeft u het script blok op dat in de trans actie wordt uitgevoerd.
Voer een geldig script blok in tussen accolades ({}).
Deze parameter is vereist.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction
Hiermee wordt de opdracht opgenomen in de actieve transactie.
Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.
Zie about_transactions voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

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
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### PSObject
Met deze cmdlet wordt het resultaat van de trans actie geretourneerd.

## OPMERKINGEN

* De para meter *UseTransaction* bevat de opdracht in de actieve trans actie. Omdat de cmdlet **use-Trans Action** altijd wordt gebruikt in trans acties, is deze para meter vereist om een **use-trans actie-** opdracht van kracht te laten worden.

*

## GERELATEERDE KOPPELINGEN

[Volt ooien-trans actie](Complete-Transaction.md)

[Get-trans actie](Get-Transaction.md)

[Start-trans actie](Start-Transaction.md)

[Ongedaan maken-trans actie](Undo-Transaction.md)
