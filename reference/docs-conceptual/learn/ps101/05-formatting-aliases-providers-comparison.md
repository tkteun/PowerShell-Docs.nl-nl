---
title: Opmaak, aliassen, providers, vergelijking
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: Dit hoofd stuk bevat een inleiding tot de concepten van uitvoer opmaak, opdracht aliassen, providers en vergelijkings bewerkingen.
ms.openlocfilehash: efe70d2d220f8451e781603b6000c3553dda910c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501606"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a>Hoofd stuk 5: opmaak, aliassen, providers, vergelijking

## <a name="requirements"></a>Vereisten

De SQL Server Power shell-module is vereist voor enkele van de voor beelden die in dit hoofd stuk worden weer gegeven. De module wordt geïnstalleerd als onderdeel van [SQL Server Management Studio (smss)][SMSS]. Het wordt ook gebruikt in volgende hoofd stukken. Down load en installeer dit op uw computer met Windows 10 lab-omgeving.

## <a name="format-right"></a>Rechts Format teren

In hoofd stuk 4 hebt u geleerd om zoveel mogelijk naar links te filteren. De regel voor het hand matig Format teren van de uitvoer van een opdracht is vergelijkbaar met die regel, behalve dat deze zoveel mogelijk moet worden uitgevoerd.

De meest voorkomende indelings opdrachten zijn `Format-Table` en `Format-List` . `Format-Wide` en `Format-Custom` kunnen ook worden gebruikt, maar zijn minder gangbaar.

Zoals vermeld in hoofd stuk 3, wordt een opdracht die meer dan vier eigenschappen retourneert, standaard ingesteld op een lijst, tenzij aangepaste opmaak wordt gebruikt.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

Gebruik de `Format-Table` cmdlet om de opmaak hand matig te overschrijven en de uitvoer in een tabel in plaats van een lijst weer te geven.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

De standaard uitvoer voor `Get-Service` is drie eigenschappen in een tabel.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Gebruik de `Format-List` cmdlet om de standaard opmaak te overschrijven en de resultaten in een lijst te retour neren.

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

U ziet dat er gewoon pijpleidingen `Get-Service` worden `Format-List` geretourneerd. Dit gebeurt niet bij elke opdracht vanwege de manier waarop de opmaak voor die bepaalde opdracht achter de schermen is ingesteld.

Het cijfer waarvan u op de hoogte wilt zijn van de indelings-cmdlets, produceert objecten die afwijken van de normale objecten in Power shell.

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

Dit betekent dat indelings opdrachten niet kunnen worden gepiped naar de meeste andere opdrachten. Ze kunnen worden omgeleid naar een aantal `Out-*` opdrachten, maar dat is wel het geval. Daarom wilt u de opmaak aan het eind van de regel (rechts Format teren) uitvoeren.

## <a name="aliases"></a>Aliassen

Een alias in Power shell is een kortere naam voor een opdracht. Power shell bevat een reeks ingebouwde aliassen en u kunt ook uw eigen aliassen definiëren.

De `Get-Alias` cmdlet wordt gebruikt om aliassen te vinden. Als u de alias voor een opdracht al kent, wordt de para meter **name** gebruikt om te bepalen aan welke opdracht de alias is gekoppeld.

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

Er kunnen meerdere aliassen worden opgegeven voor de waarde van de para meter **name** .

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

U ziet vaak dat de para meter **name** is wegge laten, omdat het een positionele para meter is.

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

Als u aliassen voor een opdracht wilt vinden, moet u de para meter **definitie** gebruiken.

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

De **definitie** parameter kan niet positioneel worden gebruikt, dus moet worden opgegeven.

Aliassen kunnen u enkele toetsaanslagen besparen en ze zijn prima wanneer u opdrachten in de-console typt.
Ze mogen niet worden gebruikt in scripts of in code die u met anderen opslaat of deelt. Zoals eerder in dit boek is vermeld, is het gebruik van volledige cmdlet-en parameter namen zelf gedocumenteerd en gemakkelijker te begrijpen.

Wees voorzichtig bij het maken van uw eigen aliassen omdat deze alleen voor komen in uw huidige Power shell-sessie op uw computer.

## <a name="providers"></a>Providers

Een provider in Power shell is een interface waarmee bestands systemen, zoals toegang tot een gegevens opslag, kunnen worden geopend. Er zijn een aantal ingebouwde providers in Power shell.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

Zoals u in de vorige resultaten kunt zien, zijn er ingebouwde providers voor het REGI ster, aliassen, omgevings variabelen, bestands systeem, functies, variabelen, certificaten en WSMan.

De daad werkelijke schijven die deze providers gebruiken om hun gegevens opslag beschikbaar te maken, kunnen worden bepaald met de `Get-PSDrive` cmdlet. De `Get-PSDrive` cmdlet geeft niet alleen stations weer die worden weer gegeven door providers, maar er worden ook logische Windows-stations weer gegeven, inclusief stations die zijn toegewezen aan netwerk shares.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

Modules van derden, zoals de Active Directory Power shell-module en de SQLServer Power shell-module, voegen hun eigen Power shell-provider en PSDrive toe.

Importeer de Active Directory-en SQL Server Power shell-modules.

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

Controleer of er extra Power shell-providers zijn toegevoegd.

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

In de vorige set met resultaten bestaan nu twee nieuwe Power shell-providers, een voor Active Directory en een andere voor SQL Server.

Er is ook een PSDrive toegevoegd voor elk van deze modules.

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

PSDrives kan net als een traditioneel bestands systeem worden gebruikt.

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a>Vergelijkingsoperators

Power shell bevat een aantal vergelijkings operators die worden gebruikt om waarden te vergelijken of waarden te vinden die overeenkomen met bepaalde patronen. Tabel 5-1 bevat een lijst met vergelijkings operatoren in Power shell.

|    Operator    |                          Definitie                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | Gelijk aan                                                     |
| `-ne`          | Niet gelijk aan                                                 |
| `-gt`          | Groter dan                                                 |
| `-ge`          | Groter dan of gelijk aan                                     |
| `-lt`          | Kleiner dan                                                    |
| `-le`          | Kleiner dan of gelijk aan                                        |
| `-Like`        | Overeenkomst met het `*` Joker teken                       |
| `-NotLike`     | Komt niet overeen met het `*` Joker teken              |
| `-Match`       | Komt overeen met de opgegeven reguliere expressie                     |
| `-NotMatch`    | Komt niet overeen met de opgegeven reguliere expressie              |
| `-Contains`    | Hiermee wordt bepaald of een verzameling een opgegeven waarde bevat        |
| `-NotContains` | Hiermee wordt bepaald of een verzameling geen specifieke waarde bevat |
| `-In`          | Hiermee wordt bepaald of een opgegeven waarde zich in een verzameling bevindt           |
| `-NotIn`       | Hiermee wordt bepaald of een opgegeven waarde zich niet in een verzameling bevindt       |
| `-Replace`     | Vervangt de opgegeven waarde                                 |

Alle in tabel 5-1 genoemde Opera tors zijn hoofdletter gevoelig. Plaats een `c` voor kant van de operator die wordt weer gegeven in tabel 5-1 om het hoofdletter gevoelig te maken. `-ceq`Is bijvoorbeeld de hoofdletter gevoelige versie van de `-eq` vergelijkings operator.

De juiste case ' Power shell ' is gelijk aan ' Power shell ' met de vergelijkings operator equals.

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

Het is niet gelijk aan het gebruik van de hoofdletter gevoelige versie van de vergelijkings operator gelijk aan.

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

De operator niet gelijk aan vergelijkings operatoren keert de voor waarde om.

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

Groter dan, groter dan of gelijk aan, kleiner dan en kleiner dan of gelijk aan alles werk met teken reeks-of numerieke waarden.

```powershell
5 -gt 5
```

```Output
False
```

Als u meer dan of gelijk aan gebruikt in plaats van groter dan met het vorige voor beeld, wordt de **Booleaanse** waarde True geretourneerd, omdat vijf gelijk is aan vijf.

```powershell
5 -ge 5
```

```Output
True
```

Op basis van de resultaten van de vorige twee voor beelden kunt u waarschijnlijk bepalen hoe kleiner dan en kleiner dan of gelijk aan het werk zijn.

```powershell
5 -lt 10
```

```Output
True
```

De `-Like` `-Match` Opera tors en kunnen verwarrend zijn, zelfs voor ervaren Power shell-gebruikers. `-Like` wordt gebruikt met Joker tekens `*` en `?` voor het uitvoeren van "like"-overeenkomsten.

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

`-Match` maakt gebruik van een reguliere expressie voor het uitvoeren van de overeenkomst.

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

Gebruik de operator Range om de getallen 1 t/m 10 in een variabele op te slaan.

```powershell
$Numbers = 1..10
```

```Output
```

Bepaal of de `$Numbers` variabele 15 bevat.

```powershell
$Numbers -contains 15
```

```Output
False
```

Bepaal of het getal 10 bevat.

```powershell
$Numbers -contains 10
```

```Output
True
```

`-NotContains` keert de logica om te zien of de `$Numbers` variabele geen waarde bevat.

```powershell
$Numbers -notcontains 15
```

```Output
True
```

In het vorige voor beeld wordt de **Booleaanse** waarde True geretourneerd, omdat het True is dat de `$Numbers` variabele geen 15 bevat. Het bevat echter het getal 10 zodat het onwaar is wanneer het is getest.

```powershell
$Numbers -notcontains 10
```

```Output
False
```

De vergelijkings operator in is voor het eerst geïntroduceerd in Power shell versie 3,0. Dit wordt gebruikt om te bepalen of een waarde een matrix is. De `$Numbers` variabele is een matrix omdat deze meerdere waarden bevat.

```powershell
15 -in $Numbers
```

```Output
False
```

Met andere woorden, `-in` voert dezelfde test uit als de vergelijkings operator bevat, met uitzonde ring van de tegenovergestelde richting.

```powershell
10 -in $Numbers
```

```Output
True
```

15 bevindt zich niet in de `$Numbers` matrix, dus false wordt in het volgende voor beeld geretourneerd.

```powershell
15 -in $Numbers
```

```Output
False
```

Net als de `-contains` operator, `not` keert u de logica voor de `-in` operator om.

```powershell
10 -notin $Numbers
```

```Output
False
```

Het vorige voor beeld retourneert False omdat de `$Numbers` matrix 10 bevat en de voor waarde is getest om te bepalen of deze geen 10 bevat.

15 is ' niet in ' de `$Numbers` matrix, zodat de **Booleaanse** waarde True wordt geretourneerd.

```powershell
15 -notin $Numbers
```

```Output
True
```

De `-replace` operator heeft precies het gewenste idee. Dit wordt gebruikt om iets te vervangen. Als u één waarde opgeeft, wordt deze waarde vervangen door niets. In het volgende voor beeld vervangt ik ' shell ' door niets.

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

Als u een waarde wilt vervangen door een andere waarde, geeft u de nieuwe waarde op achter het patroon dat u wilt vervangen. SQL zaterdag in Baton Rouge is een gebeurtenis die ik elk jaar probeer te spreken. In het volgende voor beeld wordt het woord ' zaterdag ' vervangen door de afkorting ' SAT '.

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

Er zijn ook methoden zoals **vervangen ()** die kunnen worden gebruikt voor het vervangen van dingen die vergelijkbaar zijn met de manier waarop de operator vervangen werkt. De `-Replace` operator is echter standaard hoofdletter gevoelig en de methode **replace ()** is hoofdletter gevoelig.

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

U ziet dat het woord ' zaterdag ' niet is vervangen in het vorige voor beeld. Dit komt doordat het is opgegeven in een ander geval dan het origineel. Wanneer het woord ' zaterdag ' is opgegeven in hetzelfde geval als de oorspronkelijke, vervangt de methode **replace ()** deze zoals verwacht.

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

Wees voorzichtig wanneer u methoden gebruikt om gegevens te transformeren, omdat u onvoorziene problemen kunt ondervinden, zoals het uitvoeren van de _Turkije-test_. Zie voor een voor beeld het blog artikel met de titel [met behulp van een schadelijke Power shell-code testen met andere cult uren][]. Mijn aanbeveling is het gebruik van een operator in plaats van een methode waar mogelijk om dit soort problemen te voor komen.

Hoewel de vergelijkings operators kunnen worden gebruikt zoals weer gegeven in de voor gaande voor beelden, kunt u deze zelf gebruiken met de `Where-Object` cmdlet om een bepaald type filtering uit te voeren.

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u een aantal verschillende onderwerpen geleerd waarin opmaak rechten, aliassen, providers en vergelijkings operatoren worden vermeld.

## <a name="review"></a>Beoordelen

1. Waarom is het nood zakelijk om zo veel mogelijk opmaak te kunnen uitvoeren?
1. Hoe bepaalt u wat de feitelijke cmdlet voor de alias is `%` ?
1. Waarom moet u geen aliassen gebruiken in scripts die u opslaat of code die u met anderen deelt?
1. Voer een adreslijst vermelding uit op de stations die zijn gekoppeld aan een van de register providers.
1. Wat is een van de belangrijkste voor delen van het gebruik van de operator replace in plaats van de methode replace?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

- [Format-Table][]
- [Format-List][]
- [Format-Wide][]
- [about_Aliases][]
- [about_Providers][]
- [about_Comparison_Operators][]
- [about_Arrays][]

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Power shell-code met andere cult uren testen met behulp van een schadelijke hand]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
