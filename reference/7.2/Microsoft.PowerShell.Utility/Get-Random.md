---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 4922124569550012223d441099dc94b228fd93d4
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2021
ms.locfileid: "99495966"
---
# Get-Random

## SAMENVATTING
Haalt een wille keurig getal op of selecteert objecten wille keurig van een verzameling.

## SYNTAXIS

### RandomNumberParameterSet (standaard)

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### RandomListItemParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### ShuffleParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Random` cmdlet haalt een wille keurig geselecteerd getal op. Als u een verzameling objecten indient, worden er `Get-Random` een of meer wille keurig geselecteerde objecten uit de verzameling opgehaald.

Zonder para meters of invoer `Get-Random` retourneert een opdracht een wille keurig geselecteerd 32-bits geheel getal van 0 (nul) en **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).

Standaard wordt `Get-Random` cryptografische, veilige wille keurigheid gegenereerd met behulp van de [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) -klasse.

U kunt de para meters van gebruiken `Get-Random` om de minimum-en maximum waarden op te geven, het aantal objecten dat wordt geretourneerd door een verzameling of een Seed-nummer.

> [!CAUTION]
> Als u de Seed opzettelijk instelt, wordt het niet-wille keurig Herhaal bare gedrag veroorzaakt. Het mag alleen worden gebruikt bij het reproduceren van gedrag, zoals bij het opsporen van fouten of het analyseren van een script dat `Get-Random` opdrachten bevat.
>
> Deze Seed-waarde wordt gebruikt voor de huidige opdracht en voor alle volgende `Get-Random` opdrachten in de huidige sessie totdat u **SetSeed** opnieuw gebruikt of de sessie sluit. U kunt de Seed niet opnieuw instellen op de standaard waarde.

## VOORBEELDEN

### Voor beeld 1: een wille keurig geheel getal ophalen

Met deze opdracht wordt een wille keurig geheel getal opgehaald tussen 0 (nul) en **Int32. MaxValue**.

```powershell
Get-Random
```

```Output
3951433
```

### Voor beeld 2: een wille keurig geheel getal ophalen tussen 0 en 99

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### Voor beeld 3: een wille keurig geheel getal ophalen tussen-100 en 99

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### Voor beeld 4: een wille keurig getal met drijvende komma ophalen

Met deze opdracht wordt een wille keurig drijvende-komma nummer opgehaald dat groter is dan of gelijk is aan 10,7 en kleiner is dan 20,92.

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### Voor beeld 5: een wille keurig geheel getal uit een matrix ophalen

Met deze opdracht wordt een wille keurig geselecteerd getal uit de opgegeven matrix opgehaald.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### Voor beeld 6: meerdere wille keurige gehele getallen ophalen uit een matrix

Met deze opdracht worden drie wille keurig geselecteerde getallen in wille keurige volg orde uit een matrix opgehaald.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### Voor beeld 7: een hele verzameling wille keurig toekennen

Vanaf Power shell 7,1 kunt u de para meter voor **wille keurige** volg orde gebruiken om de volledige verzameling te retour neren.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Shuffle
```

```Output
2
3
5
1
8
13
```

### Voor beeld 8: een wille keurige, niet-numerieke waarde ophalen

Met deze opdracht wordt een wille keurige waarde uit een niet-numerieke collectie geretourneerd.

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### Voor beeld 9: de para meter SetSeed gebruiken

In dit voor beeld ziet u het effect van het gebruik van de para meter **SetSeed** .

Omdat **SetSeed** niet-wille keurig gedrag produceert, wordt het doorgaans alleen gebruikt om de resultaten te reproduceren, bijvoorbeeld bij het opsporen van fouten in een script of het analyseren van een-bestand.

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### Voor beeld 10: wille keurige bestanden ophalen

Deze opdrachten krijgen een wille keurig geselecteerd voor beeld van 50 bestanden van het `C:` station van de lokale computer.

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### Voor beeld 11: roll-Fair-dobbel stenen

In dit voor beeld wordt een billijke dobbel steen van 1200 keer Gerolt en worden de resultaten geteld. Met de eerste opdracht wordt `ForEach-Object` de aanroep herhaald `Get-Random` van de sluis in getallen (1-6). De resultaten worden gegroepeerd op basis van de waarde `Group-Object` en opgemaakt als een tabel met `Select-Object` .

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

### Voor beeld 12: de para meter aantal gebruiken

U kunt nu de para meter **aantal** gebruiken zonder pijpleiding objecten aan `Get-Random` .
In het volgende voor beeld worden drie wille keurige getallen opgehaald die kleiner zijn dan 10.

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### Voor beeld 13: gebruik de para meter input object met een lege teken reeks of $null

In dit voor beeld wordt met de para meter **input object** een matrix opgegeven die een lege teken reeks ( `''` ) en bevat `$null` .

```powershell
Get-Random -InputObject @('a','',$null)
```

`Get-Random` retourneert, een `a` lege teken reeks of `$null` . De lege Sting wordt weer gegeven als een lege regel en `$null` keert terug naar een Power shell-prompt.

## PARAMETERS

### -Aantal

Hiermee geeft u het aantal wille keurige objecten of getallen op dat moet worden geretourneerd. De standaardwaarde is 1.

Als in combi natie met de `InputObject` waarde van **Count** het aantal objecten in de verzameling overschrijdt, `Get-Random` retourneert alle objecten in wille keurige volg orde.

```yaml
Type: System.Int32
Parameter Sets: RandomNumberParameterSet, RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee wordt een verzameling objecten opgegeven. `Get-Random` Hiermee worden wille keurig geselecteerde objecten in wille keurige volg orde opgehaald uit de verzameling tot het aantal dat is opgegeven door **Count**. Voer de objecten, een variabele die de objecten bevat of een opdracht of expressie waarmee de objecten worden opgehaald. U kunt ook een verzameling van objecten door sluizen naar `Get-Random` .

Vanaf Power shell 7 accepteert de para meter **input object** matrices die een lege teken reeks of kunnen bevatten `$null` . De matrix kan worden verzonden door de pijp lijn of als een **input object** parameter waarde.

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet, ShuffleParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Maximum

Hiermee geeft u een maximum waarde op voor het wille keurig getal. `Get-Random` retourneert een waarde die kleiner is dan het maximum (niet gelijk aan). Voer een geheel getal, een zwevende-komma getal met dubbele precisie of een object in dat kan worden geconverteerd naar een geheel getal of dubbele waarde, zoals een numerieke teken reeks ("100").

De waarde van **maximum** moet groter dan (niet gelijk aan) de waarde van **minimum** zijn. Als de waarde van **maximum** of **minimum** een drijvende-komma getal is, `Get-Random` wordt een wille keurig geselecteerd drijvende-komma getal geretourneerd.

Als de waarde van **minimum** een 32-bits integer is op een 64-bits computer, is de standaard waarde van **maximum** **Int32. MaxValue**.

Als de waarde van **minimum** een double is (een getal met een drijvende komma), is de standaard waarde van **maximum** **Double. MaxValue**. Anders is de standaard waarde **Int32. MaxValue**.

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum

Hiermee geeft u een minimum waarde voor het wille keurig getal op. Voer een geheel getal, een zwevende-komma getal met dubbele precisie of een object in dat kan worden geconverteerd naar een geheel getal of dubbele waarde, zoals een numerieke teken reeks ("100"). De standaardwaarde is 0 (nul).

De waarde van **minimum** moet kleiner zijn dan (niet gelijk aan) de waarde van **maximum**. Als de waarde van **maximum** of **minimum** een drijvende-komma getal is, `Get-Random` wordt een wille keurig geselecteerd drijvende-komma getal geretourneerd.

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SetSeed

Hiermee geeft u een Seed-waarde op voor de generator voor wille keurige getallen. Wanneer u **SetSeed** gebruikt, gebruikt de cmdlet de methode [System. Random](/dotnet/api/system.random) om Pseudorandom-nummers te genereren, die niet cryptografisch veilig zijn.

> [!CAUTION]
> De Seed-resultaten worden ingesteld op niet-wille keurig gedrag. Het mag alleen worden gebruikt bij het reproduceren van gedrag, zoals bij het opsporen van fouten of het analyseren van een script dat `Get-Random` opdrachten bevat.
>
> Deze Seed-waarde wordt gebruikt voor de huidige opdracht en voor alle volgende `Get-Random` opdrachten in de huidige sessie totdat u **SetSeed** opnieuw gebruikt of de sessie sluit. U kunt de Seed niet opnieuw instellen op de standaard waarde.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wille keurige volg orde

Retourneert de volledige verzameling in een wille keurige volg orde.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShuffleParameterSet
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

### System. object

U kunt een of meer objecten door sluizen. `Get-Random` selecteert waarden wille keurig van de objecten met pijp lijn.

## UITVOER

### System. Int32, System. Int64, systeem. Double

`Get-Random` retourneert een geheel getal of getal met een drijvende komma of een object dat wille keurig uit een ingediende verzameling is geselecteerd.

## OPMERKINGEN

Standaard wordt `Get-Random` cryptografische, veilige wille keurigheid gegenereerd met behulp van de [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) -klasse.

`Get-Random` retourneert niet altijd hetzelfde gegevens type als de invoer waarde. In de volgende tabel ziet u het uitvoer type voor elk van de numerieke invoer typen.

| Invoertype | Uitvoer type |
| :--------: | :---------: |
|   SByte    |   Dubbel    |
|    Byte    |   Dubbel    |
|   Int16    |   Dubbel    |
|   UInt16   |   Dubbel    |
|   Int32    |    Int32    |
|   UInt32   |   Dubbel    |
|   Int64    |    Int64    |
|   UInt64   |   Dubbel    |
|   Dubbel   |   Dubbel    |
|   Enkelvoudig   |   Dubbel    |

Vanaf Windows Power Shell 3,0 `Get-Random` ondersteunt 64-bits geheel getal. In Windows Power Shell 2,0 worden alle waarden geconverteerd naar **System. Int32**.

Vanaf Power shell 7 accepteert de para meter **input object** in de para meter set **RandomListItemParameterSet** matrices die een lege teken reeks of bevatten `$null` . In eerdere Power shell-versies heeft alleen de **maximum** para meter in de **RandomNumberParameterSet** -parameterset een lege teken reeks geaccepteerd of `$null` .

## GERELATEERDE KOPPELINGEN

[System. Security. Cryptography. RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[Systeem. wille keurig](/dotnet/api/system.random)
