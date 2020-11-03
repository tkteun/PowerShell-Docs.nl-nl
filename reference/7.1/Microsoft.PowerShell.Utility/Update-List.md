---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: c0d5c5b9ed6beed635b9df1ba9523b29c5cac9eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251321"
---
# <span data-ttu-id="d4bd7-103">Update-List</span><span class="sxs-lookup"><span data-stu-id="d4bd7-103">Update-List</span></span>

## <span data-ttu-id="d4bd7-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d4bd7-104">SYNOPSIS</span></span>
<span data-ttu-id="d4bd7-105">Hiermee worden items toegevoegd aan en verwijderd uit een eigenschaps waarde die een verzameling objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-105">Adds items to and removes items from a property value that contains a collection of objects.</span></span>

## <span data-ttu-id="d4bd7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d4bd7-106">SYNTAX</span></span>

### <span data-ttu-id="d4bd7-107">AddRemoveSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="d4bd7-107">AddRemoveSet (Default)</span></span>

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="d4bd7-108">Vervangings</span><span class="sxs-lookup"><span data-stu-id="d4bd7-108">ReplaceSet</span></span>

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## <span data-ttu-id="d4bd7-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d4bd7-109">DESCRIPTION</span></span>

<span data-ttu-id="d4bd7-110">Met de `Update-List` cmdlet worden items toegevoegd, verwijderd of vervangen in een eigenschaps waarde van een object en wordt het bijgewerkte object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-110">The `Update-List` cmdlet adds, removes, or replaces items in a property value of an object and returns the updated object.</span></span> <span data-ttu-id="d4bd7-111">Deze cmdlet is ontworpen voor eigenschappen die verzamelingen objecten bevatten.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-111">This cmdlet is designed for properties that contain collections of objects.</span></span>

<span data-ttu-id="d4bd7-112">Met de para meters **toevoegen** en **verwijderen** kunt u afzonderlijke items toevoegen aan en verwijderen uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-112">The **Add** and **Remove** parameters add individual items to and remove them from the collection.</span></span>
<span data-ttu-id="d4bd7-113">De **Vervang** parameter vervangt de volledige verzameling.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-113">The **Replace** parameter replaces the entire collection.</span></span>

<span data-ttu-id="d4bd7-114">Als u geen eigenschap opgeeft in de opdracht, `Update-List` wordt een object geretourneerd dat de update beschrijft in plaats van het object bij te werken.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-114">If you do not specify a property in the command, `Update-List` returns an object that describes the update instead of updating the object.</span></span> <span data-ttu-id="d4bd7-115">U kunt het update object verzenden naar cmdlets waarmee objecten, zoals cmdlets, worden gewijzigd `Set` .</span><span class="sxs-lookup"><span data-stu-id="d4bd7-115">You can submit the update object to cmdlets that change objects, such as `Set` cmdlets.</span></span>

<span data-ttu-id="d4bd7-116">Deze cmdlet werkt alleen wanneer de eigenschap die wordt bijgewerkt, de **IList** -interface ondersteunt die `Update-List` gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-116">This cmdlet works only when the property that is being updated supports the **IList** interface that `Update-List` uses.</span></span> <span data-ttu-id="d4bd7-117">Daarnaast moeten alle `Set` cmdlets die een update accepteren de **IList** -interface ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-117">Also, any `Set` cmdlets that accept an update must support the **IList** interface.</span></span>

<span data-ttu-id="d4bd7-118">De kern-cmdlets die met Power shell worden geïnstalleerd, bieden geen ondersteuning voor deze interface.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-118">The core cmdlets that are installed with PowerShell do not support this interface.</span></span> <span data-ttu-id="d4bd7-119">`Update-List`Zie het Help-onderwerp van de cmdlet om te bepalen of een cmdlet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-119">To determine whether a cmdlet supports `Update-List`, see the cmdlet Help topic.</span></span>

<span data-ttu-id="d4bd7-120">Deze cmdlet is opnieuw geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-120">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="d4bd7-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d4bd7-121">EXAMPLES</span></span>

### <span data-ttu-id="d4bd7-122">Voor beeld 1: items toevoegen aan een eigenschaps waarde</span><span class="sxs-lookup"><span data-stu-id="d4bd7-122">Example 1: Add items to a property value</span></span>

<span data-ttu-id="d4bd7-123">In dit voor beeld maken we een klasse die een deck van kaarten vertegenwoordigt waarin de kaarten worden opgeslagen als een **lijst** verzamelings object.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-123">In this example we create a class that represents a deck of cards where the cards are stored as a **List** collection object.</span></span> <span data-ttu-id="d4bd7-124">De methode **NewDeck ()** gebruikt `Update-List` om een volledig deck of kaart waarden toe te voegen aan de verzameling **kaarten** .</span><span class="sxs-lookup"><span data-stu-id="d4bd7-124">The **NewDeck()** method uses `Update-List`to add a complete deck of card values to the **cards** collection.</span></span>

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = "`u{2663}","`u{2666}","`u{2665}","`u{2660}"
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
> <span data-ttu-id="d4bd7-125">De `Update-List` cmdlet voert het bijgewerkte object uit naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-125">The `Update-List` cmdlet outputs the updated object to the pipeline.</span></span> <span data-ttu-id="d4bd7-126">We sluizen de uitvoer naar `Out-Null` om de ongewenste weer gave te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-126">We pipe the output to `Out-Null` to suppress the unwanted display.</span></span>

### <span data-ttu-id="d4bd7-127">Voor beeld 2: items van een verzamelings eigenschap toevoegen en verwijderen</span><span class="sxs-lookup"><span data-stu-id="d4bd7-127">Example 2: Add and remove items of a collection property</span></span>

<span data-ttu-id="d4bd7-128">Als u doorgaat met de code in voor beeld 1, worden er exemplaren van de klasse **kaarten** gemaakt die een deck of kaarten en de kaarten van twee spelers vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-128">Continuing with the code in Example 1, we will create instances of the **Cards** class to represent a deck of cards and the cards held by two players.</span></span> <span data-ttu-id="d4bd7-129">We gebruiken de `Update-List` cmdlet om kaarten toe te voegen aan de handen van de spelers en om kaarten uit het dek te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-129">We use the `Update-List` cmdlet to add cards to the players' hands and to remove cards from the deck.</span></span>

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

<span data-ttu-id="d4bd7-130">In de uitvoer ziet u de status van het deck voordat de kaarten aan de spelers werden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-130">The output shows the state of the deck before the cards were dealt to the players.</span></span> <span data-ttu-id="d4bd7-131">U kunt zien dat elke speler vijf kaarten van het dek heeft ontvangen.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-131">You can see that each player received five cards from the deck.</span></span> <span data-ttu-id="d4bd7-132">In de laatste uitvoer ziet u de status van de deck nadat de kaarten aan de spelers zijn door gegeven.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-132">The final output shows the state of the deck after dealing the cards to the players.</span></span> <span data-ttu-id="d4bd7-133">`Update-List` is gebruikt om de kaarten van het dek te selecteren en toe te voegen aan de verzameling spelers.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-133">`Update-List` was used to select the cards from the deck and add them to the players' collection.</span></span> <span data-ttu-id="d4bd7-134">Vervolgens worden de kaarten van de spelers uit het dek verwijderd met `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="d4bd7-134">Then the players' cards were removed from the deck using `Update-List`.</span></span>

### <span data-ttu-id="d4bd7-135">Voor beeld 3: items toevoegen aan en verwijderen uit één opdracht</span><span class="sxs-lookup"><span data-stu-id="d4bd7-135">Example 3: Add and remove items in a single command</span></span>

<span data-ttu-id="d4bd7-136">`Update-List` Hiermee kunt u de para meters **toevoegen** en **verwijderen** gebruiken in één opdracht.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-136">`Update-List` allows you to use the **Add** and **Remove** parameters in a single command.</span></span> <span data-ttu-id="d4bd7-137">In dit voor beeld wil speler 1 de `4♦` en ontvangen en `6♦` twee nieuwe kaarten ophalen.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-137">In this example, Player 1 wants to discard the `4♦` and `6♦` and get two new cards.</span></span>

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

## <span data-ttu-id="d4bd7-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d4bd7-138">PARAMETERS</span></span>

### <span data-ttu-id="d4bd7-139">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="d4bd7-139">-Add</span></span>

<span data-ttu-id="d4bd7-140">Hiermee geeft u de eigenschaps waarden op die moeten worden toegevoegd aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-140">Specifies the property values to be added to the collection.</span></span> <span data-ttu-id="d4bd7-141">Voer de waarden in de volg orde in die moeten worden weer gegeven in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-141">Enter the values in the order that they should appear in the collection.</span></span>

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

### <span data-ttu-id="d4bd7-142">-Input object</span><span class="sxs-lookup"><span data-stu-id="d4bd7-142">-InputObject</span></span>

<span data-ttu-id="d4bd7-143">Hiermee geeft u de objecten op die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-143">Specifies the objects to be updated.</span></span> <span data-ttu-id="d4bd7-144">U kunt ook het object pipeen dat moet worden bijgewerkt naar `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="d4bd7-144">You can also pipe the object to be updated to `Update-List`.</span></span>

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

### <span data-ttu-id="d4bd7-145">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d4bd7-145">-Property</span></span>

<span data-ttu-id="d4bd7-146">Hiermee geeft u de eigenschap op die de verzameling bevat die wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-146">Specifies the property that contains the collection that is being updated.</span></span> <span data-ttu-id="d4bd7-147">Als u deze para meter weglaat, `Update-List` wordt een object geretourneerd dat de wijziging vertegenwoordigt in plaats van het object te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-147">If you omit this parameter, `Update-List` returns an object that represents the change instead of changing the object.</span></span>

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

### <span data-ttu-id="d4bd7-148">-Remove</span><span class="sxs-lookup"><span data-stu-id="d4bd7-148">-Remove</span></span>

<span data-ttu-id="d4bd7-149">Hiermee geeft u de eigenschaps waarden op die uit de verzameling moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-149">Specifies the property values to be removed from the collection.</span></span>

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

### <span data-ttu-id="d4bd7-150">-Vervangen</span><span class="sxs-lookup"><span data-stu-id="d4bd7-150">-Replace</span></span>

<span data-ttu-id="d4bd7-151">Hiermee geeft u een nieuwe verzameling op.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-151">Specifies a new collection.</span></span> <span data-ttu-id="d4bd7-152">Met deze para meter worden alle items in de oorspronkelijke verzameling vervangen door de items die door deze para meter worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-152">This parameter replaces all items in the original collection with the items specified by this parameter.</span></span>

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

### <span data-ttu-id="d4bd7-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d4bd7-153">CommonParameters</span></span>

<span data-ttu-id="d4bd7-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d4bd7-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d4bd7-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="d4bd7-156">INPUTS</span></span>

### <span data-ttu-id="d4bd7-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="d4bd7-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="d4bd7-158">U kunt de objecten die moeten worden bijgewerkt, door sluizen naar `Update-List` .</span><span class="sxs-lookup"><span data-stu-id="d4bd7-158">You can pipe the objects to be updated to `Update-List`.</span></span>

## <span data-ttu-id="d4bd7-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d4bd7-159">OUTPUTS</span></span>

### <span data-ttu-id="d4bd7-160">Objecten of System. Management. Automation. PSListModifier</span><span class="sxs-lookup"><span data-stu-id="d4bd7-160">Objects or System.Management.Automation.PSListModifier</span></span>

<span data-ttu-id="d4bd7-161">`Update-List` retourneert het bijgewerkte object of retourneert een-object dat de bijwerk actie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="d4bd7-161">`Update-List` returns the updated object, or it returns an object that represents the update action.</span></span>

## <span data-ttu-id="d4bd7-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d4bd7-162">NOTES</span></span>

## <span data-ttu-id="d4bd7-163">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d4bd7-163">RELATED LINKS</span></span>

[<span data-ttu-id="d4bd7-164">Format-List</span><span class="sxs-lookup"><span data-stu-id="d4bd7-164">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="d4bd7-165">Select-Object</span><span class="sxs-lookup"><span data-stu-id="d4bd7-165">Select-Object</span></span>](Select-Object.md)

