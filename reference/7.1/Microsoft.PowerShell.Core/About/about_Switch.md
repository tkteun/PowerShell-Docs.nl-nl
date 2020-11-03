---
description: Hierin wordt uitgelegd hoe u met een switch meerdere `If` instructies kunt verwerken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 4d70d765086ad49ed0e5cd955fc3be3094fc79a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252934"
---
# <a name="about-switch"></a>Over Switch

## <a name="short-description"></a>Korte beschrijving
Hierin wordt uitgelegd hoe u met een switch meerdere `If` instructies kunt verwerken.

## <a name="long-description"></a>Lange beschrijving

Als u een voor waarde in een script of functie wilt controleren, gebruikt u een- `If` instructie. De `If` instructie kan veel soorten voor waarden controleren, met inbegrip van de waarde van variabelen en de eigenschappen van de objecten.

Als u meerdere voor waarden wilt controleren, gebruikt u een- `Switch` instructie. De `Switch` instructie is gelijk aan een reeks `If` instructies, maar is eenvoudiger. De `Switch` instructie vermeldt elke voor waarde en een optionele actie. Als een voor waarde wordt opgehaald, wordt de actie uitgevoerd.

De- `Switch` instructie kan de `$_` en `$switch` automatische variabelen gebruiken. Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.

Een Basic- `Switch` instructie heeft de volgende indeling:

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

De volgende `Switch` instructie vergelijkt bijvoorbeeld de test waarde, 3, op elk van de voor waarden. Wanneer de test waarde overeenkomt met de voor waarde, wordt de actie uitgevoerd.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

In dit eenvoudige voor beeld wordt de waarde vergeleken met elke voor waarde in de lijst, zelfs als er een overeenkomst is voor de waarde 3. De volgende `Switch` instructie heeft twee voor waarden voor de waarde 3. Er wordt gedemonstreerd dat alle voor waarden standaard worden getest.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

`Switch`Gebruik de instructie om de te stoppen om te vergelijken na een overeenkomst `Break` . De instructie `Break` beëindigt de `Switch` instructie.

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

Als de test waarde een verzameling is, zoals een matrix, wordt elk item in de verzameling geëvalueerd in de volg orde waarin deze wordt weer gegeven. In de volgende voor beelden wordt 4 en vervolgens 2 geëvalueerd.

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

Alle `Break` instructies zijn van toepassing op de verzameling, niet op elke waarde, zoals wordt weer gegeven in het volgende voor beeld. De `Switch` instructie wordt beëindigd door de `Break` instructie in de voor waarde van de waarde 4.

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a>Syntax

De syntaxis van de `Switch` instructie complete is als volgt:

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

of

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

Als er geen para meters worden gebruikt, `Switch` werkt hetzelfde als met de **exacte** para meter. Er wordt een niet-hoofdletter gevoelige overeenkomst voor de waarde uitgevoerd. Als de waarde een verzameling is, wordt elk element geëvalueerd in de volg orde waarin het wordt weer gegeven.

De `Switch` instructie moet ten minste één voorwaarde instructie bevatten.

De `Default` component wordt geactiveerd wanneer de waarde niet overeenkomt met een van de voor waarden. Deze is gelijk aan een- `Else` component in een- `If` instructie. `Default`In elke instructie is slechts één component toegestaan `Switch` .

`Switch` heeft de volgende para meters:

- **Joker** teken: geeft aan dat de voor waarde een Joker teken reeks is. Als de match-component geen teken reeks is, wordt de para meter genegeerd. De vergelijking is hoofdletter gevoelig.
- **Exact** : geeft aan dat de match-component als deze een teken reeks is, exact moet overeenkomen. Als de match-component geen teken reeks is, wordt deze para meter genegeerd. De vergelijking is hoofdletter gevoelig.
- **CaseSensitive** : Hiermee wordt een hoofdletter gevoelige overeenkomst uitgevoerd. Als de match-component geen teken reeks is, wordt deze para meter genegeerd.
- **File** -voert invoer uit vanuit een bestand in plaats van een waarde-instructie. Als er meerdere **Bestands** parameters zijn opgenomen, wordt alleen de laatste gebruikt. Elke regel van het bestand wordt gelezen en geëvalueerd door de `Switch` instructie. De vergelijking is hoofdletter gevoelig.
- **Regex** -voert een reguliere expressie die overeenkomt met de waarde aan de voor waarde. Als de match-component geen teken reeks is, wordt deze para meter genegeerd.
  De vergelijking is hoofdletter gevoelig. De `$matches` Automatische variabele is beschikbaar voor gebruik binnen het overeenkomende instructie blok.

> [!NOTE]
> Wanneer er conflicterende waarden worden opgegeven, zoals **regex** en **Joker teken** , heeft de laatste para meter prioriteit en worden alle conflicterende para meters genegeerd. Er zijn ook meerdere exemplaren van para meters toegestaan. Alleen de laatste para meter die wordt gebruikt, is echter effectief.

In dit voor beeld wordt een object dat geen teken reeks of numerieke gegevens is door gegeven aan de `Switch` . `Switch`Hiermee wordt een teken reeks afgedwongen voor het object en wordt het resultaat geëvalueerd.

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

In dit voor beeld is er geen overeenkomende case, dus er is geen uitvoer.

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

Door de component toe te voegen `Default` , kunt u een actie uitvoeren wanneer er geen andere voor waarden slagen.

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

Als u wilt dat het woord ' veer tien ' overeenkomt met een aanvraag, moet u de `-Wildcard` `-Regex` para meter or gebruiken.

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

In het volgende voor beeld wordt de `-Regex` para meter gebruikt.

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

De voor waarde van een switch instructie kan bestaan uit:

- Een expressie waarvan de waarde wordt vergeleken met de invoer waarde
- Een script blok dat moet worden geretourneerd `$true` als aan een voor waarde wordt voldaan.

De `$_` Automatische variabele bevat de waarde die is door gegeven aan de switch-instructie en is beschikbaar voor evaluatie en gebruik binnen het bereik van de voor waarden-instructies.

De actie voor elke voor waarde is onafhankelijk van de acties in andere omstandigheden.

In het volgende voor beeld wordt het gebruik van script blokken als instructie voorwaarden gedemonstreerd `Switch` .

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

Als de waarde overeenkomt met meerdere voor waarden, wordt de actie voor elke voor waarde uitgevoerd. Gebruik de `Break` tref woorden of om dit gedrag te wijzigen `Continue` .

Het `Break` sleutel woord stopt met de verwerking en sluit de `Switch` instructie af.

Het `Continue` sleutel woord stopt met het verwerken van de huidige waarde, maar gaat verder met de verwerking van alle volgende waarden.

In het volgende voor beeld wordt een matrix met getallen verwerkt en wordt weer gegeven als ze oneven of even zijn. Negatieve getallen worden overgeslagen met het `Continue` sleutel woord. Als er een niet-nummer wordt aangetroffen, wordt de uitvoering beëindigd met het `Break` sleutel woord.

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a>Zie ook

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)
