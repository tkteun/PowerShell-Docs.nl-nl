---
title: Stoombeheer
description: Power shell biedt methoden om lussen te maken, beslissingen te nemen en de stroom van code in scripts logisch te beheren.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "84436307"
---
# <a name="chapter-6---flow-control"></a>Hoofd stuk 6-Datatransport besturing

## <a name="scripting"></a>Uitvoeren van scripts

Wanneer u de Power shell-One-Lines schrijft voor het schrijven van scripts, klinkt het veel ingewik kelder dan echt. Een script is niets meer dan dezelfde of vergelijk bare opdrachten die u interactief zou uitvoeren in de Power shell-console, behalve dat ze worden opgeslagen als een `.PS1` bestand. Er zijn een aantal script constructies die u kunt gebruiken, zoals een `foreach` lus in plaats van de `ForEach-Object` cmdlet. Voor beginners kunnen de verschillen verwarrend zijn, vooral als u rekening `foreach` houdt met een script constructie en een alias voor de `ForEach-Object` cmdlet.

## <a name="looping"></a>Lussen

Een van de fantastische dingen over Power shell is, wanneer u hebt nagegaan hoe u een item kunt uitvoeren, is het bijna net zo eenvoudig om dezelfde taak uit te voeren voor honderden items. Door loop de items met een van de vele verschillende typen lussen in Power shell.

### <a name="foreach-object"></a>ForEach-Object

`ForEach-Object` is een cmdlet voor het door lopen van items in een pijp lijn, zoals met One-line Power shell. `ForEach-Object` streamt de objecten via de pijp lijn.

Hoewel de **module** parameter van `Get-Command` meerdere waarden accepteert die teken reeksen zijn, worden deze alleen geaccepteerd via pijplijn invoer door de naam van de eigenschap of via de invoer van para meters. Als ik in het volgende scenario twee teken reeksen wil pipeen op waarde `Get-Command` voor gebruik met de **module** parameter, moet ik de `ForEach-Object` cmdlet gebruiken.

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

In het vorige voor beeld `$_` is het huidige object. Vanaf Power shell versie 3,0 `$PSItem` kan worden gebruikt in plaats van `$_` . Maar ik vind dat de meeste ervaren Power shell-gebruikers nog steeds gebruikmaken `$_` van de voor keur omdat deze compatibel is met het type.

Wanneer u het `foreach` tref woord gebruikt, moet u alle items in het geheugen opslaan voordat u deze kunt door lopen. Dit kan lastig zijn als u niet weet hoeveel items u aan het werk hebt.

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

Vaak een lus zoals `foreach` of `ForEach-Object` is nodig. Anders wordt er een fout bericht weer gegeven.

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

Andere keren, kunt u dezelfde resultaten verkrijgen terwijl de lus helemaal niet meer wordt gebruikt. Raadpleeg de Help van de cmdlet voor meer informatie over uw opties.

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

Zoals u in de voor gaande voor beelden kunt zien, accepteert de para meter **Identity** `Get-ADComputer` alleen een enkele waarde wanneer deze wordt opgegeven via de invoer van para meters, maar is het mogelijk om meerdere items toe te staan wanneer de invoer wordt opgegeven via pijplijn invoer.

### <a name="for"></a>Voor

Een `for` lus wordt herhaald terwijl een opgegeven voor waarde waar is. De `for` lus is niet iets dat ik vaak gebruik, maar wel het gebruik ervan.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

In het vorige voor beeld wordt de lus vier keer herhaald door te beginnen met het cijfer 1 en wordt de teller variabel `$i` kleiner dan 5. In slaap stand wordt in totaal tien seconden geslapen.

### <a name="do"></a>Wel doen

Er zijn twee verschillende `do` lussen in Power shell. `Do Until` wordt uitgevoerd terwijl de opgegeven voor waarde False is.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

Het vorige voor beeld is een nummer dat wordt voortgezet totdat de waarde die u hebt geschat gelijk is aan het nummer dat de `Get-Random` cmdlet heeft gegenereerd.

`Do While` is precies het tegenovergestelde. Het wordt uitgevoerd zolang de opgegeven voor waarde resulteert in waar.

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

Dezelfde resultaten worden met een lus behaald `Do While` door de test voorwaarde om te keren naar niet gelijk aan.

`Do` lussen worden altijd ten minste één keer uitgevoerd, omdat de voor waarde aan het einde van de lus wordt geëvalueerd.

### <a name="while"></a>Het

Net als bij de `Do While` lus wordt een `While` lus uitgevoerd zolang de opgegeven voor waarde waar is. Het verschil is echter dat een `While` lus de voor waarde aan de bovenkant van de lus evalueert voordat een wille keurige code wordt uitgevoerd. Het wordt dus niet uitgevoerd als de voor waarde resulteert in ONWAAR.

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

In het vorige voor beeld wordt berekend op welke dag Thanksgiving Day is in de Verenigde Staten. Het is altijd op de vierde donderdag van november. De lus begint dus met de 22 dag van november en voegt een dag toe wanneer de dag van de week niet gelijk is aan donderdag. Als de 22 een donderdag is, wordt de lus helemaal niet uitgevoerd.

## <a name="break-continue-and-return"></a>Onderbreken, door gaan en retour neren

`Break` is ontworpen om een lus te verstoren. Het wordt ook vaak gebruikt met de `switch` instructie.

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

De `break` instructie die in het vorige voor beeld wordt weer gegeven, zorgt ervoor dat de lus wordt afgesloten bij de eerste iteratie.

Door gaan is ontworpen om naar de volgende herhaling van een lus over te slaan.

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

In het vorige voor beeld worden de getallen 1, 2, 4 en 5 uitgevoerd. Nummer 3 wordt overgeslagen en gaat verder met de volgende herhaling van de lus. Vergelijkbaar met `break` , wordt `continue` de lus onderbroken, behalve alleen voor de huidige iteratie. De uitvoering wordt voortgezet met de volgende iteratie in plaats van de lus af te breken en te stoppen.

Retour is ontworpen om uit te sluiten van de bestaande scope.

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

U ziet dat in het vorige voor beeld het eerste resultaat wordt geretourneerd en vervolgens uit de lus bestaat. Een uitgebreidere uitleg van de resultaten verklaring vindt u in een van mijn blog artikelen: [' het Power shell-retour trefwoord '][].

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u geleerd over de verschillende typen lussen die voor komen in Power shell.

## <a name="review"></a>Beoordelen

1. Wat is het verschil in de `ForEach-Object` cmdlet en de script constructie foreach?
1. Wat is het belangrijkste voor deel van het gebruik van een while-lus in plaats van een do while-of do until-lus.
1. Wat is het verschil tussen de instructies voor onderbreken en hervatten?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

- [ForEach-object][]
- [about_ForEach][]
- [about_For][]
- [about_Do][]
- [about_While][]
- [about_Break][]
- [about_Continue][]
- [about_Return][]

<!-- link references -->
[ForEach-object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
["Het Power shell-retour trefwoord"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
