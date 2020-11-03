---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: eccee5ad302395116430006ed4dc0395946696b6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250353"
---
# Update-List

## SAMENVATTING
Hiermee worden items toegevoegd aan en verwijderd uit een eigenschaps waarde die een verzameling objecten bevat.

## SYNTAXIS

### AddRemoveSet (standaard)

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### Vervangings

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Update-List` cmdlet worden items toegevoegd, verwijderd of vervangen in een eigenschaps waarde van een object en wordt het bijgewerkte object geretourneerd. Deze cmdlet is ontworpen voor eigenschappen die verzamelingen objecten bevatten.

Met de para meters **toevoegen** en **verwijderen** kunt u afzonderlijke items toevoegen aan en verwijderen uit de verzameling.
De **Vervang** parameter vervangt de volledige verzameling.

Als u geen eigenschap opgeeft in de opdracht, `Update-List` wordt een object geretourneerd dat de update beschrijft in plaats van het object bij te werken. U kunt het update object verzenden naar cmdlets waarmee objecten, zoals cmdlets, worden gewijzigd `Set` .

Deze cmdlet werkt alleen wanneer de eigenschap die wordt bijgewerkt, de **IList** -interface ondersteunt die `Update-List` gebruikt. Daarnaast moeten alle `Set` cmdlets die een update accepteren de **IList** -interface ondersteunen.

De kern-cmdlets die met Power shell worden geïnstalleerd, bieden geen ondersteuning voor deze interface. `Update-List`Zie het Help-onderwerp van de cmdlet om te bepalen of een cmdlet ondersteunt.

## VOORBEELDEN

### Voor beeld 1: items toevoegen aan een eigenschaps waarde

In dit voor beeld maken we een klasse die een deck van kaarten vertegenwoordigt waarin de kaarten worden opgeslagen als een **lijst** verzamelings object. De methode **NewDeck ()** gebruikt `Update-List` om een volledig deck of kaart waarden toe te voegen aan de verzameling **kaarten** .

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = [char]0x2663,[char]0x2666,[char]0x2665,[char]0x2660
        $_values = 'A',2,3,4,5,6,7,8,9,10,'J','Q','K'
        $_deck = foreach ($s in $_suits){ foreach ($v in $_values){ "$v$s"} }
        $this | Update-List -Property cards -Add $_deck | Out-Null
    }

    Show() {
        Write-Host
        Write-Host $this.name ": " $this.cards[0..12]
        if ($this.cards.count -gt 13) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[13..25]
        }
        if ($this.cards.count -gt 26) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[26..38]
        }
        if ($this.cards.count -gt 39) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[39..51]
        }
    }

    Shuffle() { $this.cards = Get-Random -InputObject $this.cards -Count 52 }

    Sort() { $this.cards.Sort() }
}
```

> [!NOTE]
> De `Update-List` cmdlet voert het bijgewerkte object uit naar de pijp lijn. We sluizen de uitvoer naar `Out-Null` om de ongewenste weer gave te onderdrukken.

### Voor beeld 2: items van een verzamelings eigenschap toevoegen en verwijderen

Als u doorgaat met de code in voor beeld 1, worden er exemplaren van de klasse **kaarten** gemaakt die een deck of kaarten en de kaarten van twee spelers vertegenwoordigen. We gebruiken de `Update-List` cmdlet om kaarten toe te voegen aan de handen van de spelers en om kaarten uit het dek te verwijderen.

```powershell
$player1 = [Cards]::new('Player 1')
$player2 = [Cards]::new('Player 2')

$deck = [Cards]::new('Deck')
$deck.NewDeck()
$deck.Shuffle()
$deck.Show()

# Deal two hands
$player1 | Update-List -Property cards -Add $deck.cards[0,2,4,6,8] | Out-Null
$player2 | Update-List -Property cards -Add $deck.cards[1,3,5,7,9] | Out-Null
$deck | Update-List -Property cards -Remove $player1.cards | Out-Null
$deck | Update-List -Property cards -Remove $player2.cards | Out-Null

$player1.Show()
$player2.Show()
$deck.Show()
```

```Output
Deck :  4♦ 7♥ J♦ 5♣ A♣ 8♦ J♣ Q♥ 6♦ 3♦ 9♦ 6♣ 2♣
        K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥ Q♠
        3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠ 2♥
        6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣ 8♥

Player 1 :  4♦ J♦ A♣ J♣ 6♦

Player 2 :  7♥ 5♣ 8♦ Q♥ 3♦

Deck :  9♦ 6♣ 2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣
        Q♣ A♥ Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠
        4♣ 2♠ 2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣
        A♦ K♣ 8♥
```

In de uitvoer ziet u de status van het deck voordat de kaarten aan de spelers werden door gegeven. U kunt zien dat elke speler vijf kaarten van het dek heeft ontvangen. In de laatste uitvoer ziet u de status van de deck nadat de kaarten aan de spelers zijn door gegeven. `Update-List` is gebruikt om de kaarten van het dek te selecteren en toe te voegen aan de verzameling spelers. Vervolgens worden de kaarten van de spelers uit het dek verwijderd met `Update-List` .

### Voor beeld 3: items toevoegen aan en verwijderen uit één opdracht

`Update-List` Hiermee kunt u de para meters **toevoegen** en **verwijderen** gebruiken in één opdracht. In dit voor beeld wil speler 1 de `4♦` en ontvangen en `6♦` twee nieuwe kaarten ophalen.

```powershell
# Player 1 wants two new cards - remove 2 cards & add 2 cards
$player1 | Update-List -Property cards -Remove $player1.cards[0,4] -Add $deck.cards[0..1] | Out-Null
$player1.Show()

# remove dealt cards from deck
$deck | Update-List -Property cards -Remove $deck.cards[0..1] | Out-Null
$deck.Show()
```

```Output
Player 1 :  J♦ A♣ J♣ 9♦ 6♣

Deck :  2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥
        Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠
        2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣
        8♥
```

## PARAMETERS

### -Toevoegen

Hiermee geeft u de eigenschaps waarden op die moeten worden toegevoegd aan de verzameling. Voer de waarden in de volg orde in die moeten worden weer gegeven in de verzameling.

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de objecten op die moeten worden bijgewerkt. U kunt ook het object pipeen dat moet worden bijgewerkt naar `Update-List` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Eigenschap

Hiermee geeft u de eigenschap op die de verzameling bevat die wordt bijgewerkt. Als u deze para meter weglaat, `Update-List` wordt een object geretourneerd dat de wijziging vertegenwoordigt in plaats van het object te wijzigen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Remove

Hiermee geeft u de eigenschaps waarden op die uit de verzameling moeten worden verwijderd.

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Vervangen

Hiermee geeft u een nieuwe verzameling op. Met deze para meter worden alle items in de oorspronkelijke verzameling vervangen door de items die door deze para meter worden opgegeven.

```yaml
Type: System.Object[]
Parameter Sets: ReplaceSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt de objecten die moeten worden bijgewerkt, door sluizen naar `Update-List` .

## UITVOER

### Objecten of System. Management. Automation. PSListModifier

`Update-List` retourneert het bijgewerkte object of retourneert een-object dat de bijwerk actie vertegenwoordigt.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Format-List](Format-List.md)

[Select-Object](Select-Object.md)
