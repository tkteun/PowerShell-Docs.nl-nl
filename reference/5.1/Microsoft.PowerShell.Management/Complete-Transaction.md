---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/complete-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Complete-Transaction
ms.openlocfilehash: 20fbdd86aab07dda065492eff2da4f358fb2ffca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250830"
---
# Complete-Transaction

## SAMENVATTING
Hiermee wordt de actieve trans actie doorgevoerd.

## SYNTAXIS

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De **volledige-trans actie-** cmdlet voert een actieve trans actie door.
Wanneer u een trans actie doorvoert, worden de opdrachten in de trans actie voltooid en worden de gegevens die worden beïnvloed door de opdrachten, gewijzigd.

Als de trans actie meerdere abonnees bevat, moet u voor elke Start-Transaction-opdracht één opdracht voor **volt ooien van trans acties** invoeren.

De **volledige-trans actie-** cmdlet is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.
Zie about_Transactions voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: een trans actie door voeren

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}
```

In dit voor beeld ziet u wat er gebeurt wanneer u de cmdlet **complete-trans** actie gebruikt om een trans actie door te voeren.

De trans actie wordt gestart met de opdracht **Start-trans actie** .
De New-Item opdracht gebruikt de para meter *UseTransaction* om de opdracht in de trans actie op te neemt.

De eerste dir-opdracht (Get-Child item) laat zien dat het nieuwe item nog niet is toegevoegd aan het REGI ster.

De opdracht **volt ooien-trans actie** voert de trans actie door, waardoor de wijziging van het REGI ster effectief wordt.
Als gevolg hiervan wordt met de tweede opdracht dir aangegeven dat het REGI ster is gewijzigd.

### Voor beeld 2: een trans actie met meer dan één abonnee vastleggen

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
0   0 MyCompany                      {}

PS HKCU:\software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                2                Active

PS HKCU:\software> New-ItemProperty -Path MyCompany -Name MyKey -Value -UseTransaction

MyKey
-----
123

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                1                Active

PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   1 MyCompany                      {MyKey}
```

In dit voor beeld ziet u hoe u met **volledige trans actie** een trans actie met meer dan één abonnee kunt door voeren.

Als u een trans actie met meerdere abonnees wilt door voeren, moet u één opdracht voor **volt ooien van trans** acties invoeren voor elke opdracht voor **het starten van de trans actie** .
De gegevens worden alleen gewijzigd wanneer de laatste **voltooide-trans actie-** opdracht wordt verzonden.

In het volgende voor beeld ziet u een reeks opdrachten die zijn ingevoerd op de opdracht regel.
In de praktijk worden trans acties waarschijnlijk uitgevoerd in scripts, waarbij de secundaire trans actie wordt uitgevoerd door een functie of hulp script dat wordt aangeroepen door het hoofd script.

In dit voor beeld wordt met een **Start-trans actie-** opdracht de trans actie gestart.
Met de opdracht **Nieuw item** met de para meter *UseTransaction* wordt de sleutel mijn bedrijf toegevoegd aan de software sleutel.
Hoewel met de cmdlet **New-item** een sleutel object wordt geretourneerd, zijn de gegevens in het REGI ster nog niet gewijzigd.

Een tweede **Start-trans actie-** opdracht voegt een tweede abonnee toe aan de bestaande trans actie.
Met de cmdlet **Get-trans actie** wordt bevestigd dat het aantal abonnees 2 is.
Een New-ItemProperty opdracht met de para meter *UseTransaction* voegt een register vermelding toe aan de nieuwe mijn bedrijf-sleutel.
Opnieuw, de opdracht retourneert een waarde, maar het REGI ster wordt niet gewijzigd.

Met de eerste opdracht **volt ooien-trans actie** wordt het aantal abonnees verminderd met 1.
Dit wordt bevestigd door de opdracht **Get-trans actie** .
Er worden echter geen gegevens gewijzigd, zoals wordt weer gegeven door een dir m * ( **Get-Child item** ) opdracht.

Met de tweede opdracht **volt ooien-trans actie** wordt de hele trans actie door gegeven en worden de gegevens in het REGI ster gewijzigd.
Dit wordt bevestigd door een tweede dir m * opdracht, waarin de wijzigingen worden weer gegeven.

### Voor beeld 3: een trans actie uitvoeren waarbij geen gegevens worden gewijzigd

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> dir m* -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}

PS HKCU:\software> Complete-Transaction
```

Dit voor beeld toont de waarde van het gebruik van Get- \* opdrachten en andere opdrachten die geen gegevens wijzigen in een trans actie.
Wanneer een Get- \* opdracht wordt gebruikt in een trans actie, worden de objecten opgehaald die deel uitmaken van de trans actie.
Zo kunt u een voor beeld van de wijzigingen in de trans actie bekijken voordat de wijzigingen worden doorgevoerd.

In dit voor beeld wordt een trans actie gestart.
Een New-Item opdracht met de para meter *UseTransaction* voegt een nieuwe sleutel toe aan het REGI ster als onderdeel van de trans actie.

Omdat de nieuwe register sleutel pas wordt toegevoegd aan het REGI ster als de opdracht **volt ooien-trans actie** is uitgevoerd, wordt in een eenvoudige dir-opdracht ( **Get-Child item** ) het REGI ster zonder de nieuwe sleutel weer gegeven.

Wanneer u echter de para meter *UseTransaction* toevoegt aan de opdracht dir, wordt de opdracht onderdeel van de trans actie en worden de items in de trans actie opgehaald, zelfs als ze nog niet zijn toegevoegd aan de gegevens.

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
U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* U kunt een trans actie die is doorgevoerd, niet terugdraaien of een trans actie die is teruggedraaid door voeren.

  U kunt geen andere trans actie terugdraaien dan de actieve trans actie.
Als u een andere trans actie wilt terugdraaien, moet u eerst de actieve trans actie door voeren of terugdraaien.

  Als een deel van een trans actie niet kan worden doorgevoerd, bijvoorbeeld wanneer een opdracht in de trans actie resulteert in een fout, wordt de hele trans actie teruggedraaid.

*

## GERELATEERDE KOPPELINGEN

[Get-trans actie](Get-Transaction.md)

[Start-trans actie](Start-Transaction.md)

[Ongedaan maken-trans actie](Undo-Transaction.md)

[Gebruik-trans actie](Use-Transaction.md)

[Get-Child item](Get-ChildItem.md)

[Nieuw-item](New-Item.md)

[Nieuw-item Property](New-ItemProperty.md)
