---
description: Hierin wordt beschreven hoe u Opera tors kunt gebruiken om waarden toe te wijzen aan variabelen.
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: 4e21c9d0f2b0a47cd4db10ee515ceb07548eb971
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706128"
---
# <a name="about-assignment-operators"></a>Over toewijzings operatoren

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u Opera tors kunt gebruiken om waarden toe te wijzen aan variabelen.

## <a name="long-description"></a>Lange beschrijving

Toewijzings operatoren wijzen een of meer waarden toe aan een variabele. Ze kunnen numerieke bewerkingen uitvoeren op de waarden vóór de toewijzing.

Power shell ondersteunt de volgende toewijzings operatoren.

|Operator|Beschrijving                                                  |
|--------|-------------------------------------------------------------|
|=       |Hiermee stelt u de waarde van een variabele in op de opgegeven waarde.         |
|+=      |Verhoogt de waarde van een variabele met de opgegeven waarde, of |
|        |Hiermee wordt de opgegeven waarde aan de bestaande waarde toegevoegd.           |
|-=      |Hiermee verkleint u de waarde van een variabele met de opgegeven waarde.    |
|*=      |Vermenigvuldigt de waarde van een variabele met de opgegeven waarde, of|
|        |Hiermee wordt de opgegeven waarde aan de bestaande waarde toegevoegd.           |
|/=      |Hiermee wordt de waarde van een variabele opgedeeld op basis van de opgegeven waarde.      |
|%=      |Hiermee wordt de waarde van een variabele opgedeeld op basis van de opgegeven waarde en   |
|        |wijst vervolgens de rest (modulus) toe aan de variabele.        |
|++      |Verhoogt de waarde van een variabele, toewijs bare eigenschap of   |
|        |matrix element door 1.                                          |
|--      |Hiermee verkleint u de waarde van een variabele, toewijs bare eigenschap of   |
|        |matrix element door 1.                                          |

## <a name="syntax"></a>Syntax

De syntaxis van de toewijzings operators is als volgt:

`<assignable-expression>` `<assignment-operator>` `<value>`

Toewijs bare expressies bevatten variabelen en eigenschappen. De waarde kan één waarde, een matrix met waarden of een opdracht, expressie of instructie zijn.

De Opera tors voor verhogen en verlagen zijn unaire Opera tors. Elk heeft een voor voegsel-en achtervoegsel-versie.

`<assignable-expression><operator>`
`<operator><assignable-expression>`

De toewijs bare expressie moet een getal zijn of moet worden geconverteerd naar een getal.

## <a name="assigning-values"></a>Waarden toewijzen

Variabelen hebben de naam geheugen ruimten die waarden opslaan. U slaat de waarden in variabelen op met behulp van de toewijzings operator `=` . De nieuwe waarde kan de bestaande waarde van de variabele vervangen, of u kunt een nieuwe waarde toevoegen aan de bestaande waarde.

De operator basis toewijzing is het gelijkteken `=` `(ASCII 61)` . Met de volgende instructie wordt de waarde Power shell bijvoorbeeld toegewezen aan de `$MyShell` variabele:

```powershell
$MyShell = "PowerShell"
```

Wanneer u een waarde aan een variabele toewijst in Power shell, wordt de variabele gemaakt als deze nog niet bestaat. De eerste van de volgende twee toewijzings instructies maakt bijvoorbeeld de `$a` variabele en wijst de waarde 6 toe aan `$a` . De tweede toewijzings instructie wijst een waarde van 12 toe aan `$a` . Met de eerste instructie maakt u een nieuwe variabele. De tweede instructie wijzigt alleen de waarde:

```powershell
$a = 6
$a = 12
```

Variabelen in Power Shell hebben geen specifiek gegevens type tenzij u ze cast.
Wanneer een variabele slechts één object bevat, neemt de variabele het gegevens type van dat object. Wanneer een variabele een verzameling objecten bevat, heeft de variabele het gegevens type System. object. Daarom kunt u elk type object toewijzen aan de verzameling. In het volgende voor beeld ziet u dat u proces objecten, service objecten, teken reeksen en gehele getallen kunt toevoegen aan een variabele zonder een fout te genereren:

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

Omdat de toewijzings operator `=` een lagere prioriteit heeft dan de pijplijn operator `|` , zijn haakjes niet vereist om het resultaat van een opdracht pijplijn aan een variabele toe te wijzen. Met de volgende opdracht worden bijvoorbeeld de services op de computer gesorteerd en vervolgens de gesorteerde services toegewezen aan de `$a` variabele:

```powershell
$a = Get-Service | Sort-Object -Property name
```

U kunt de waarde die is gemaakt door een instructie ook toewijzen aan een variabele, zoals in het volgende voor beeld:

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

In dit voor beeld wordt nul toegewezen aan de `$a` variabele als de waarde van `$b` kleiner dan nul is. De waarde van `$b` wordt toegewezen aan `$a` als de waarde van `$b` is niet kleiner dan nul.

### <a name="the-assignment-operator"></a>De toewijzings operator

De toewijzings operator `=` wijst waarden toe aan variabelen. Als de variabele al een waarde heeft, vervangt de toewijzings operator `=` de waarde zonder waarschuwing.

Met de volgende instructie wordt de waarde 6 van het gehele getal toegewezen aan de `$a` variabele:

```powershell
$a = 6
```

Als u een teken reeks waarde wilt toewijzen aan een variabele, plaatst u de teken reeks waarde tussen aanhalings tekens, als volgt:

```powershell
$a = "baseball"
```

Als u een matrix (meerdere waarden) wilt toewijzen aan een variabele, scheidt u de waarden met komma's, als volgt:

```powershell
$a = "apple", "orange", "lemon", "grape"
```

Als u een hash-tabel aan een variabele wilt toewijzen, gebruikt u de standaard hash-tabel notatie in Power shell. Typ een at `@` -teken gevolgd door sleutel-waardeparen, gescheiden door punt komma's `;` en tussen accolades `{ }` . Als u bijvoorbeeld een hash-tabel aan de variabele wilt toewijzen `$a` , typt u:

```powershell
$a = @{one=1; two=2; three=3}
```

Voor het toewijzen van hexadecimale waarden aan een variabele, wordt de waarde voorafgegaan door `0x` .
Power shell converteert de hexadecimale waarde (0x10) naar een decimale waarde (in dit geval 16) en wijst die waarde toe aan de `$a` variabele. Als u bijvoorbeeld een waarde van 0x10 wilt toewijzen aan de `$a` variabele, typt u:

```powershell
$a = 0x10
```

Als u een exponentiële waarde aan een variabele wilt toewijzen, typt u het hoofd nummer, de letter `e` en een getal dat een meervoud van 10 vertegenwoordigt. Als u bijvoorbeeld een waarde van 3,1415 wilt toewijzen aan de kracht van 1.000 `$a` , typt u:

```powershell
$a = 3.1415e3
```

In Power shell kunnen KB `KB` , mega bytes en gigabytes ook worden geconverteerd `MB` `GB` naar bytes. Als u bijvoorbeeld een waarde van 10 kilo bytes wilt toewijzen aan de `$a` variabele, typt u:

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a>De operator Assignment by plus

De operator Assignment by plus `+=` verhoogt de waarde van een variabele of voegt de opgegeven waarde toe aan de bestaande waarde. De actie is afhankelijk van het feit of de variabele een numeriek of een teken reeks type heeft en of de variabele een enkele waarde (scalair) of meerdere waarden (een verzameling) bevat.

De `+=` operator combineert twee bewerkingen. Eerst wordt toegevoegd en vervolgens toegewezen.
Daarom zijn de volgende instructies gelijkwaardig:

```powershell
$a += 2
$a = ($a + 2)
```

Wanneer de variabele één numerieke waarde bevat, wordt de `+=` huidige waarde verhoogd met de hoeveelheid aan de rechter kant van de operator. Vervolgens wijst de operator de resulterende waarde toe aan de variabele. In het volgende voor beeld ziet u hoe u de operator kunt gebruiken `+=` om de waarde van een variabele te verhogen:

```powershell
$a = 4
$a += 2
$a
```

```
6
```

Wanneer de waarde van de variabele een teken reeks is, wordt de waarde aan de rechter kant van de operator toegevoegd aan de teken reeks, als volgt:

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

Wanneer de waarde van de variabele een matrix is, `+=` voegt de operator de waarden aan de rechter kant van de operator toe aan de matrix. Tenzij de matrix expliciet wordt getypeerd door cast, kunt u als volgt een wille keurig type waarde aan de matrix toevoegen:

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

en

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

Wanneer de waarde van een variabele een hash-tabel is, `+=` voegt de operator de waarde aan de rechter kant van de operator toe aan de hashtabel. Omdat het enige type dat u aan een hashtabel kunt toevoegen, echter een andere hash-tabel is, mislukken alle andere toewijzingen.

Met de volgende opdracht wordt bijvoorbeeld een hash-tabel aan de `$a` variabele toegewezen.
Vervolgens wordt de operator gebruikt `+=` om een andere hash-tabel toe te voegen aan de bestaande hash-tabel, waardoor een nieuwe sleutel/waarde-paar in feite wordt toegevoegd aan de bestaande hash-tabel.
Deze opdracht is geslaagd, zoals wordt weer gegeven in de uitvoer:

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

Met de volgende opdracht wordt geprobeerd een geheel getal ' 1 ' toe te voegen aan de hash-tabel in de `$a` variabele. Deze opdracht mislukt:

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a>De operator Assignment door aftrekken

De operator Assignment door aftrekken `-=` verlaagt de waarde van een variabele met de waarde die aan de rechter kant van de operator is opgegeven. Deze operator kan niet worden gebruikt met teken reeks variabelen en kan niet worden gebruikt om een element uit een verzameling te verwijderen.

De `-=` operator combineert twee bewerkingen. Eerst wordt de waarde afgetrokken en vervolgens toegewezen. Daarom zijn de volgende instructies gelijkwaardig:

```powershell
$a -= 2
$a = ($a - 2)
```

In het volgende voor beeld ziet u hoe u de operator kunt gebruiken `-=` om de waarde van een variabele te verlagen:

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

U kunt ook de `-=` toewijzings operator gebruiken om de waarde van een lid van een numerieke matrix te verlagen. U doet dit door de index op te geven van het matrix element dat u wilt wijzigen. In het volgende voor beeld wordt de waarde van het derde element van een matrix (element 2) verlaagd met 1:

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

U kunt de operator niet gebruiken `-=` om de waarden van een variabele te verwijderen. Als u alle waarden wilt verwijderen die aan een variabele zijn toegewezen, gebruikt u de cmdlets [Clear-item](xref:Microsoft.PowerShell.Management.Clear-Item) of [Clear-variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) om een waarde van `$null` of `""` toe te wijzen aan de variabele.

```powershell
$a = $null
```

Als u een bepaalde waarde uit een matrix wilt verwijderen, gebruikt u matrix notatie om een waarde `$null` toe te wijzen aan een bepaald item. Met de volgende instructie wordt bijvoorbeeld de tweede waarde (index positie 1) uit een matrix verwijderd:

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

Als u een variabele wilt verwijderen, gebruikt u de cmdlet [Remove-variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) . Deze methode is handig wanneer de variabele expliciet wordt geconverteerd naar een bepaald gegevens type en u een variabele zonder type wilt gebruiken. Met de volgende opdracht wordt de `$a` variabele verwijderd:

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a>De operator Assignment door vermenigvuldigen

De operator Assignment door vermenigvuldigen `*=` vermenigvuldigt een numerieke waarde of voegt het opgegeven aantal kopieën van de teken reeks waarde van een variabele toe.

Wanneer een variabele één numerieke waarde bevat, wordt die waarde vermenigvuldigd met de waarde aan de rechter kant van de operator. In het volgende voor beeld ziet u bijvoorbeeld hoe u de `*=` operator kunt gebruiken om de waarde van een variabele te vermenigvuldigen:

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

In dit geval combineert de `*=` operator twee bewerkingen. Eerst wordt de waarde vermenigvuldigd en vervolgens toegewezen. Daarom zijn de volgende instructies gelijkwaardig:

```powershell
$a *= 2
$a = ($a * 2)
```

Wanneer een variabele een teken reeks waarde bevat, voegt Power shell het opgegeven aantal teken reeksen toe aan de waarde, als volgt:

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

Als u een element van een matrix wilt vermenigvuldigen, gebruikt u een index om het element te identificeren dat u wilt vermenigvuldigen. De volgende opdracht vermenigvuldigt bijvoorbeeld het eerste element in de matrix (index positie 0) door 2:

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a>De operator Assignment per divisie

De operator Assignment per divisie `/=` deelt een numerieke waarde door de waarde die aan de rechter kant van de operator is opgegeven. De operator kan niet worden gebruikt met teken reeks variabelen.

De `/=` operator combineert twee bewerkingen. Eerst wordt de waarde gedeeld en vervolgens toegewezen. Daarom zijn de volgende twee instructies gelijkwaardig:

```powershell
$a /= 2
$a = ($a / 2)
```

Met de volgende opdracht wordt bijvoorbeeld de `/=` operator gebruikt om de waarde van een variabele te verdelen:

```powershell
$a = 8
$a /=2
$a
```

```
4
```

Als u een element van een matrix wilt delen, gebruikt u een index om het element te identificeren dat u wilt wijzigen. De volgende opdracht deelt bijvoorbeeld het tweede element in de matrix (index positie 1) door 2:

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a>De operator Assignment door modulus

De operator Assignment door modulus `%=` verdeelt de waarde van een variabele met de waarde aan de rechter kant van de operator. Vervolgens wijst de `%=` operator de rest (ook wel de modulus) toe aan de variabele. U kunt deze operator alleen gebruiken wanneer een variabele een enkele numerieke waarde bevat. U kunt deze operator niet gebruiken wanneer een variabele een teken reeks variabele of een matrix bevat.

De `%=` operator combineert twee bewerkingen. Eerst wordt het restant gesplitst en bepaald en vervolgens wordt de rest aan de variabele toegewezen. Daarom zijn de volgende instructies gelijkwaardig:

```powershell
$a %= 2
$a = ($a % 2)
```

In het volgende voor beeld ziet u hoe u de operator kunt gebruiken `%=` om de modulus van een quotiënt op te slaan:

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a>De Opera tors voor verhogen en verlagen

De operator voor oplopen `++` verhoogt de waarde van een variabele met 1. Wanneer u de operator voor verhogen in een eenvoudige instructie gebruikt, wordt er geen waarde geretourneerd. Als u het resultaat wilt weer geven, geeft u de waarde van de variabele als volgt weer:

```powershell
$a = 7
++$a
$a
```

```
8
```

Als u wilt afdwingen dat een waarde wordt geretourneerd, plaatst u de variabele en de operator tussen haakjes, als volgt:

```powershell
$a = 7
(++$a)
```

```
8
```

De operator voor oplopen kan vóór (voor voegsel) of na (achtervoegsel) een variabele worden geplaatst. De voorvoegsel versie van de operator verhoogt een variabele voordat de waarde ervan in de instructie wordt gebruikt, als volgt:

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

De achtervoegsel-versie van de operator verhoogt een variabele nadat de waarde ervan wordt gebruikt in de instructie. In het volgende voor beeld `$c` hebben de `$a` variabelen en verschillende waarden, omdat de waarde wordt toegewezen aan `$c` vóór `$a` wijzigingen:

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

De operator `--` voor verlagen vermindert de waarde van een variabele met 1. Net als bij de operator voor verhogen, wordt er geen waarde geretourneerd wanneer u de operator in een eenvoudige instructie gebruikt. Gebruik haakjes om een waarde te retour neren, als volgt:

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

De voorvoegsel versie van de operator vermindert een variabele voordat de waarde ervan in de instructie wordt gebruikt, als volgt:

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

De achtervoegsel-versie van de operator verlaagt een variabele nadat de waarde ervan is gebruikt in de instructie. In het volgende voor beeld `$d` hebben de `$a` variabelen en verschillende waarden, omdat de waarde wordt toegewezen aan `$d` vóór `$a` wijzigingen:

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a>Microsoft .NET Framework-typen

Wanneer een variabele slechts één waarde heeft, bepaalt de waarde die is toegewezen aan de variabele standaard het gegevens type van de variabele. Met de volgende opdracht maakt u bijvoorbeeld een variabele met het type geheel getal (System. Int32):

```powershell
$a = 6
```

Als u wilt zoeken naar het .NET Framework type van een variabele, gebruikt u de methode **gettype** en de eigenschap **FullName** als volgt. Zorg ervoor dat u de haakjes achter de **gettype** -methode naam opgeeft, zelfs als de aanroep van de methode geen argumenten heeft:

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

Als u een variabele wilt maken die een teken reeks bevat, wijst u een teken reeks waarde toe aan de variabele. Om aan te geven dat de waarde een teken reeks is, plaatst u deze tussen aanhalings tekens als volgt:

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

Als de eerste waarde die is toegewezen aan de variabele een teken reeks is, behandelt Power shell alle bewerkingen als teken reeks bewerkingen en worden nieuwe waarden naar teken reeksen gecast.
Dit doet zich voor in het volgende voor beeld:

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

Als de eerste waarde een geheel getal is, behandelt Power shell alle bewerkingen als gehele getallen en worden nieuwe waarden gecast naar gehele getallen. Dit doet zich voor in het volgende voor beeld:

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

U kunt een nieuwe scalaire variabele als .NET Framework type casten door de type naam tussen vier Kante haken te plaatsen die voorafgaat aan de naam van de variabele of de eerste toewijzings waarde. Wanneer u een variabele casteert, kunt u bepalen welke typen gegevens in de variabele kunnen worden opgeslagen. En u kunt bepalen hoe de variabele zich gedraagt wanneer u deze bewerkt.

Met de volgende opdracht wordt de variabele bijvoorbeeld gecast als een teken reeks type:

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

In het volgende voor beeld wordt de eerste waarde geconverteerd, in plaats van de variabele te casten:

```powershell
$a = [string]27
```

Wanneer u een variabele naar een specifiek type casteert, is de gemeen schappelijke Conventie om de variabele te casten, niet de waarde. U kunt het gegevens type van een bestaande variabele echter niet opnieuw converteren als de waarde ervan niet kan worden geconverteerd naar het nieuwe gegevens type. Als u het gegevens type wilt wijzigen, moet u de waarde als volgt vervangen:

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

Wanneer u de naam van een variabele voorafgaat aan een gegevens type, wordt het type van die variabele bovendien vergrendeld, tenzij u het type expliciet overschrijft door een ander gegevens type op te geven. Als u probeert een waarde toe te wijzen die niet compatibel is met het bestaande type en u het type niet expliciet overschrijft, wordt een fout weer gegeven, zoals in het volgende voor beeld wordt weer gegeven:

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

In Power shell worden de gegevens typen van variabelen die meerdere items in een matrix bevatten, anders afgehandeld dan de gegevens typen van variabelen die één item bevatten. Tenzij een gegevens type specifiek wordt toegewezen aan een matrix variabele, is het gegevens type altijd `System.Object []` . Dit gegevens type is specifiek voor matrices.

Soms kunt u het standaard type overschrijven door een ander type op te geven. Met de volgende opdracht wordt de variabele bijvoorbeeld gecast als een `string []` matrix type:

```powershell
[string []] $a = "one", "two", "three"
```

Power shell-variabelen kunnen elk .NET Framework gegevens type zijn. Daarnaast kunt u een volledig gekwalificeerd .NET Framework gegevens type toewijzen dat in het huidige proces beschikbaar is. Met de volgende opdracht wordt bijvoorbeeld een `System.DateTime` gegevens type opgegeven:

```powershell
[System.DateTime]$a = "5/31/2005"
```

Aan de variabele wordt een waarde toegewezen die voldoet aan het `System.DateTime` gegevens type. De waarde van de `$a` variabele zou het volgende zijn:

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a>Meerdere variabelen toewijzen

In Power shell kunt u waarden toewijzen aan meerdere variabelen met behulp van één opdracht. Het eerste element van de toewijzings waarde wordt toegewezen aan de eerste variabele, het tweede element wordt toegewezen aan de tweede variabele, het derde element aan de derde variabele, enzovoort. Met de volgende opdracht wordt bijvoorbeeld de waarde 1 toegewezen aan de `$a` variabele, de waarde 2 aan de `$b` variabele en de waarde 3 aan de `$c` variabele:

```powershell
$a, $b, $c = 1, 2, 3
```

Als de toewijzings waarde meer elementen dan variabelen bevat, worden alle resterende waarden toegewezen aan de laatste variabele. De volgende opdracht bevat bijvoorbeeld drie variabelen en vijf waarden:

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

Daarom wijst Power shell de waarde 1 toe aan de `$a` variabele en de waarde 2 aan de `$b` variabele. De waarden 3, 4 en 5 worden toegewezen aan de `$c` variabele.
Als u de waarden in de `$c` variabele aan drie andere variabelen wilt toewijzen, gebruikt u de volgende notatie:

```powershell
$d, $e, $f = $c
```

Met deze opdracht wordt de waarde 3 toegewezen aan de `$d` variabele, de waarde 4 voor de `$e` variabele en de waarde 5 voor de `$f` variabele.

Als de toewijzings waarde minder elementen dan variabelen bevat, worden aan alle resterende variabelen aan het einde geen waarden toegewezen. De volgende opdracht bevat bijvoorbeeld drie variabelen en twee waarden:

```powershell
$a, $b, $c = 1, 2
```

Daarom wijst Power shell de waarde 1 toe aan de `$a` variabele en de waarde 2 aan de `$b` variabele. Er wordt geen waarde aan de variabele toegewezen `$c` .

U kunt ook een enkele waarde aan meerdere variabelen toewijzen door de variabelen te koppelen. Met de volgende opdracht wordt bijvoorbeeld de waarde ' drie ' toegewezen aan alle vier de variabelen:

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a>Met variabele gerelateerde cmdlets

Naast het gebruik van een toewijzings bewerking om een variabele waarde in te stellen, kunt u ook de cmdlet [set-variable](xref:Microsoft.PowerShell.Utility.Set-Variable) gebruiken. Met de volgende opdracht wordt bijvoorbeeld `Set-Variable` een matrix van 1, 2, 3 aan de `$a` variabele toegewezen.

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a>Zie ook

[about_Arrays](about_Arrays.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Variables](about_Variables.md)

[Clear-variabele](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[Remove-variabele](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[Set-variabele](xref:Microsoft.PowerShell.Utility.Set-Variable)

