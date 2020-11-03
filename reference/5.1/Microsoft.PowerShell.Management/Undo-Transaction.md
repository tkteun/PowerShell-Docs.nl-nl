---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/undo-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Undo-Transaction
ms.openlocfilehash: 1acb06ea7b05a2127b04a22c4c51b92cd68056f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250528"
---
# Undo-Transaction

## SAMENVATTING
Hiermee wordt de actieve trans actie teruggedraaid.

## SYNTAXIS

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Undo-trans actie** wordt de actieve trans actie teruggedraaid.
Wanneer u een trans actie terugdraait, worden de wijzigingen die zijn aangebracht door de opdrachten in de trans actie, verwijderd en worden de gegevens hersteld naar het oorspronkelijke formulier.

Als de trans actie meerdere abonnees bevat, wordt met een opdracht voor **ongedaan maken** de gehele trans actie voor alle abonnees teruggedraaid.

Standaard worden trans acties automatisch teruggezet als een opdracht in de trans actie een fout genereert.
Trans acties kunnen echter worden gestart met een andere terugdraai voorkeur en u kunt deze cmdlet gebruiken om de actieve trans actie op elk gewenst moment terug te draaien.

De cmdlet **Undo-trans actie** is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.
Zie about_Transactions voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: de huidige trans actie ongedaan maken

```
PS C:\> Undo-Transaction
```

Met deze opdracht wordt de huidige, actieve trans actie teruggedraaid.

### Voor beeld 2: een trans actie starten en terugdraaien

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

In dit voor beeld wordt een trans actie gestart en vervolgens weer teruggedraaid.
Als gevolg hiervan worden er geen wijzigingen aangebracht in het REGI ster.

### Voor beeld 3: terugdraaien van een trans actie voor alle abonnees

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                1                 Active

PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                2                 Active

PS HKCU:\Software> Undo-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                0                 RolledBack
```

In dit voor beeld wordt gedemonstreerd dat wanneer een abonnee een trans actie terugstuurt, de hele trans actie wordt teruggedraaid voor alle abonnees.

Met de eerste opdracht wordt de locatie gewijzigd in de register sleutel HKCU: \ software.

Met de tweede opdracht wordt een trans actie gestart.

De derde opdracht maakt gebruik van de New-Item cmdlet om een nieuwe register sleutel te maken.
De opdracht maakt gebruik van de para meter *UseTransaction* om de wijziging in de trans actie op te neemt.

De vierde opdracht maakt gebruik van de cmdlet Get-Transaction om de actieve trans actie te verkrijgen.
U ziet dat de status actief is en dat het aantal abonnees 1 is.

De vijfde opdracht maakt gebruik van de Start-Transaction opdracht opnieuw.
Normaal gesp roken wordt een trans actie gestart terwijl er een andere trans actie wordt uitgevoerd wanneer een script dat wordt gebruikt door de hoofd transactie een eigen volledige trans actie bevat.
Dit voor beeld wordt interactief uitgevoerd, zodat u het in fasen kunt onderzoeken.
Wanneer u een **Start-trans actie-** opdracht uitvoert terwijl er een andere trans actie wordt uitgevoerd, worden de opdrachten toegevoegd aan de bestaande trans actie als een nieuwe abonnee en wordt het aantal abonnees verhoogd.

De zesde opdracht maakt gebruik van de cmdlet **Get-trans actie** om de actieve trans actie op te halen.
U ziet dat het aantal abonnees nu 2 is.

De zevende opdracht maakt gebruik van **ongedaan maken-trans** actie voor het terugdraaien van de trans actie.
Met deze opdracht worden geen objecten geretourneerd.

De laatste opdracht is een **Get-trans actie** opdracht die de actieve, of in dit geval de meest recent actieve trans actie haalt.
De resultaten geven aan dat de trans actie wordt teruggedraaid en dat het aantal abonnees 0 is, wat aangeeft dat de trans actie is teruggedraaid voor alle abonnees.

## PARAMETERS

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
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

* U kunt een doorgevoerde trans actie niet terugdraaien.

  U kunt geen andere trans actie terugdraaien dan de actieve trans actie.
Als u een andere, onafhankelijke trans actie wilt terugdraaien, moet u eerst de actieve trans actie door voeren of terugdraaien.

  Als de trans actie wordt teruggedraaid, wordt de trans actie beëindigd.
Als u een trans actie opnieuw wilt gebruiken, moet u een nieuwe trans actie starten.

## GERELATEERDE KOPPELINGEN

[Volt ooien-trans actie](Complete-Transaction.md)

[Get-trans actie](Get-Transaction.md)

[Start-trans actie](Start-Transaction.md)

[Gebruik-trans actie](Use-Transaction.md)
