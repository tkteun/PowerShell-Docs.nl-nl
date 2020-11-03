---
description: Hierin wordt beschreven hoe u transactionele bewerkingen in Power shell beheert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_transactions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Transactions
ms.openlocfilehash: 522e0f727754b0b0153571039f3bf3966d0abf20
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252549"
---
# <a name="about-transactions"></a>Over trans acties

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin wordt beschreven hoe u transactionele bewerkingen in Power shell beheert.

## <a name="long-description"></a>LANGE BESCHRIJVING

Trans acties worden ondersteund in Power shell vanaf Power Shell 2,0. Met deze functie kunt u een trans actie starten, aangeven welke opdrachten deel uitmaken van de trans actie en een trans actie door voeren of terugdraaien.

## <a name="about-transactions"></a>OVER TRANS ACTIES

In Power shell is een trans actie een set van een of meer opdrachten die als een logische eenheid worden beheerd. Een trans actie kan worden voltooid (' doorgevoerd '), waardoor gegevens worden gewijzigd die worden beïnvloed door de trans actie. Het is ook mogelijk dat een trans actie volledig ongedaan kan worden gemaakt (teruggedraaid), zodat de betrokken gegevens niet door de trans actie worden gewijzigd.

Omdat de opdrachten in een trans actie als eenheid worden beheerd, worden alle opdrachten vastgelegd of worden alle opdrachten teruggedraaid.

Trans acties worden veel gebruikt bij het verwerken van gegevens, met name in database bewerkingen en voor financiële trans acties. Trans acties worden meestal gebruikt wanneer het slechtste scenario voor een set opdrachten niet zo is dat ze allemaal mislukken, maar dat sommige opdrachten slagen terwijl anderen mislukken, waardoor het systeem in een beschadigde, onwaar of niet-onderhandel bare status staat die moeilijk te herstellen is.

## <a name="transaction-cmdlets"></a>TRANS ACTIE-CMDLETS

Power shell bevat verschillende cmdlets die zijn ontworpen voor het beheren van trans acties.

- Start-trans actie: start een nieuwe trans actie.
- Use-Trans Action: voegt een opdracht of expressie toe aan de trans actie. De opdracht moet objecten gebruiken waarvoor trans acties zijn ingeschakeld.
- Ongedaan maken-trans actie: Hiermee wordt de trans actie teruggedraaid zodat er geen gegevens door de trans actie worden gewijzigd.
- Volt ooien: de trans actie wordt door doorgevoerd. De gegevens die worden beïnvloed door de trans actie, worden gewijzigd.
- Get-trans actie: haalt informatie op over de actieve trans actie.

Voor een lijst met trans actie-cmdlets typt u:

```powershell
get-command *transaction
```

Voor gedetailleerde informatie over de cmdlets typt u:

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a>ELEMENTEN WAARVOOR TRANS ACTIES ZIJN INGESCHAKELD

Om deel te nemen aan een trans actie, moeten de cmdlet en de provider trans acties ondersteunen. Deze functie is ingebouwd in de objecten die worden beïnvloed door de trans actie.

De Power shell-register provider ondersteunt trans acties in Windows Vista. Het TransactedString-object (Microsoft. Power shell. commands. Management. TransactedString) werkt met elk besturings systeem dat Power shell uitvoert.

Andere Power shell-providers kunnen trans acties ondersteunen. Als u de Power shell-providers in uw sessie wilt vinden die trans acties ondersteunen, gebruikt u de volgende opdracht om de waarde voor ' trans acties ' te vinden in de eigenschap Capabilities van providers:

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

Zie de Help bij de provider voor meer informatie over een provider. Voor hulp bij de provider, typt u:

```
get-help <provider-name>
```

Als u bijvoorbeeld hulp wilt krijgen voor de register provider, typt u:

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a>DE USETRANSACTION-PARA METER

Cmdlets die trans acties kunnen ondersteunen, hebben een UseTransaction-para meter. Deze para meter bevat de opdracht in de actieve trans actie. U kunt de volledige parameter naam of de alias ervan gebruiken, ' usetx '.

De para meter kan alleen worden gebruikt als de sessie een actieve trans actie bevat. Als u een opdracht met de para meter UseTransaction opgeeft wanneer er geen actieve trans actie is, mislukt de opdracht.

Als u cmdlets wilt zoeken met de para meter UseTransaction, typt u:

```powershell
get-help * -parameter UseTransaction
```

In Power shell core hebben alle cmdlets die zijn ontworpen om te werken met Power shell-providers ondersteunings transacties. Als gevolg hiervan kunt u de provider-cmdlets gebruiken voor het beheren van trans acties.

Zie [about_Providers](about_Providers.md)voor meer informatie over Power shell-providers.

## <a name="the-transaction-object"></a>HET TRANSACTIE OBJECT

Trans acties worden weer gegeven in Power shell door een transactie object, System. Management. Automation. Trans Action.

Het object heeft de volgende eigenschappen:

- RollbackPreference: bevat de voor keuren voor terugdraai bewerking die zijn ingesteld voor de huidige trans actie. U kunt de terugdraai voorkeur instellen wanneer u Start-Transaction gebruikt om de trans actie te starten.

  De terugdraai voorkeur bepaalt de voor waarden waaronder de trans actie automatisch wordt teruggedraaid. Geldige waarden zijn error, TerminatingError en Never. De standaard waarde is fout.

- Status: bevat de huidige status van de trans actie. Geldige waarden zijn actief, doorgevoerd en teruggedraaid.

- SubscriberCount: bevat het aantal abonnees van de trans actie. Een abonnee wordt toegevoegd aan een trans actie wanneer u een trans actie start terwijl er een andere trans actie wordt uitgevoerd. Het aantal abonnees wordt verlaagd wanneer een abonnee de trans actie doorvoert.

## <a name="active-transactions"></a>ACTIEVE TRANS ACTIES

In Power shell is slechts één trans actie tegelijk actief, en u kunt alleen de actieve trans actie beheren. In dezelfde sessie kunnen meerdere trans acties tegelijk worden uitgevoerd, maar alleen de meest recent gestarte trans actie is actief.

Als gevolg hiervan kunt u een bepaalde trans actie niet opgeven wanneer u de Trans Action-cmdlets gebruikt. Opdrachten zijn altijd van toepassing op de actieve trans actie.

Dit wordt het meest duidelijk in het gedrag van de cmdlet Get-Transaction. Wanneer u een Get-Transaction opdracht invoert, wordt door Get-Transaction altijd slechts één transactie object opgehaald. Dit object is het object dat de actieve trans actie vertegenwoordigt.

Als u een andere trans actie wilt beheren, moet u eerst de actieve trans actie volt ooien, hetzij door deze door te voeren of terug te draaien. Wanneer u dit doet, wordt de vorige trans actie automatisch actief. Trans acties worden actief bij het terugdraaien van de volg orde waarin ze worden gestart, zodat de meest recent gestarte trans actie altijd actief is.

## <a name="subscribers-and-independent-transactions"></a>ABONNEES EN ONAFHANKELIJKE TRANS ACTIES

Als u een trans actie start terwijl een andere trans actie wordt uitgevoerd, start Power shell niet standaard een nieuwe trans actie. In plaats daarvan wordt een abonnee toegevoegd aan de huidige trans actie.

Wanneer een trans actie meerdere abonnees heeft, wordt een enkele Undo-Transaction-opdracht op een wille keurig punt de volledige trans actie teruggedraaid voor alle abonnees. Als u de trans actie wilt door voeren, moet u voor elke abonnee een Complete-Transaction-opdracht invoeren.

Als u het aantal abonnees voor een trans actie wilt vinden, controleert u de eigenschap SubscriberCount van het transactie object. De volgende opdracht gebruikt bijvoorbeeld de cmdlet Get-Transaction om de waarde van de eigenschap SubscriberCount van de actieve trans actie op te halen:

```powershell
(Get-Transaction).SubscriberCount
```

Het toevoegen van een abonnee is het standaard gedrag omdat de meeste trans acties die worden gestart terwijl een andere trans actie wordt uitgevoerd, betrekking hebben op de oorspronkelijke trans actie. In het typische model roept een script dat een trans actie bevat een hulp script aan dat een eigen trans actie bevat. Omdat de trans acties gerelateerd zijn, moeten ze worden teruggedraaid of als een eenheid worden vastgelegd.

U kunt echter een trans actie starten die onafhankelijk is van de huidige trans actie door gebruik te maken van de onafhankelijke para meter van de cmdlet Start-Transaction.

Wanneer u een onafhankelijke trans actie start, wordt er Start-Transaction een nieuw transactie object gemaakt en de nieuwe trans actie wordt de actieve trans actie.
De onafhankelijke trans actie kan worden doorgevoerd of teruggedraaid zonder dat dit van invloed is op de oorspronkelijke trans actie.

Wanneer de onafhankelijke trans actie is voltooid (doorgevoerd of teruggedraaid), wordt de oorspronkelijke trans actie opnieuw de actieve trans actie.

## <a name="changing-data"></a>GEGEVENS WIJZIGEN

Wanneer u trans acties gebruikt om gegevens te wijzigen, worden de gegevens die worden beïnvloed door de trans actie, pas gewijzigd nadat u de trans actie hebt door gegeven. Dezelfde gegevens kunnen echter worden gewijzigd door opdrachten die geen deel uitmaken van de trans actie.

Houd dit in acht wanneer u trans acties gebruikt om gedeelde gegevens te beheren.
Data bases hebben doorgaans mechanismen waarmee de gegevens worden vergrendeld terwijl u aan het werk bent, zodat andere gebruikers en andere opdrachten, scripts en functies deze niet kunnen wijzigen.

De vergren deling is echter een functie van de-data base. Het is niet gerelateerd aan trans acties. Als u werkt met een bestands systeem dat is ingeschakeld voor trans acties of een ander gegevens archief, kunnen de gegevens worden gewijzigd terwijl de trans actie wordt uitgevoerd.

## <a name="examples"></a>VOORBEELDEN

In de voor beelden in deze sectie wordt de Power shell-register provider gebruikt en wordt ervan uitgegaan dat u ermee vertrouwd bent. Typ "Get-Help Registry" voor meer informatie over de register provider.

### <a name="example-1-committing-a-transaction"></a>VOOR BEELD 1: EEN TRANS ACTIE DOOR VOEREN

Als u een trans actie wilt maken, gebruikt u de cmdlet Start-Transaction. Met de volgende opdracht wordt een trans actie gestart met de standaard instellingen.

```powershell
start-transaction
```

Als u opdrachten in de trans actie wilt toevoegen, gebruikt u de para meter UseTransaction van de cmdlet. Standaard worden opdrachten niet in de trans actie opgenomen,

De volgende opdracht, waarmee de huidige locatie in de software sleutel van de HKCU: station, wordt ingesteld, is niet opgenomen in de trans actie.

```powershell
cd hkcu:\Software
```

Met de volgende opdracht, die de sleutel mijn bedrijf maakt, gebruikt de para meter UseTransaction van de cmdlet New-Item om de opdracht in de actieve trans actie op te neemt.

```powershell
new-item MyCompany -UseTransaction
```

De opdracht retourneert een object dat de nieuwe sleutel vertegenwoordigt, maar omdat de opdracht deel uitmaakt van de trans actie, is het REGI ster nog niet gewijzigd.

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

Gebruik de cmdlet Complete-Transaction om de trans actie door te voeren. Omdat deze altijd van invloed is op de actieve trans actie, kunt u de trans actie niet opgeven.

```powershell
complete-transaction
```

Als gevolg hiervan wordt de sleutel mijn bedrijf toegevoegd aan het REGI ster.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-2-rolling-back-a-transaction"></a>VOOR BEELD 2: EEN TRANS ACTIE TERUGDRAAIEN

Als u een trans actie wilt maken, gebruikt u de cmdlet Start-Transaction. Met de volgende opdracht wordt een trans actie gestart met de standaard instellingen.

```powershell
start-transaction
```

Met de volgende opdracht, die de sleutel MyOtherCompany maakt, gebruikt de para meter UseTransaction van de cmdlet New-Item om de opdracht in de actieve trans actie op te neemt.

```powershell
new-item MyOtherCompany -UseTransaction
```

De opdracht retourneert een object dat de nieuwe sleutel vertegenwoordigt, maar omdat de opdracht deel uitmaakt van de trans actie, is het REGI ster nog niet gewijzigd.

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

Gebruik de cmdlet Undo-Transaction om de trans actie terug te draaien. Omdat deze altijd van invloed is op de actieve trans actie, geeft u de trans actie niet op.

```powershell
Undo-transaction
```

Het resultaat is dat de MyOtherCompany-sleutel niet aan het REGI ster is toegevoegd.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-3-previewing-a-transaction"></a>VOOR BEELD 3: EEN VOOR BEELD VAN EEN TRANS ACTIE BEKIJKEN

Normaal gesp roken worden de opdrachten die worden gebruikt in een wijzigings gegevens van trans acties. De opdrachten voor het ophalen van gegevens zijn echter handig in een trans actie, omdat deze gegevens in de trans actie worden opgehaald. Dit geeft een voor beeld van de wijzigingen die de trans actie door voeren.

In het volgende voor beeld ziet u hoe u de Get-ChildItem-opdracht (de alias is ' dir ') gebruikt om de wijzigingen in een trans actie te bekijken.

Met de volgende opdracht wordt een trans actie gestart.

```powershell
start-transaction
```

De volgende opdracht maakt gebruik van de cmdlet New-ItemProperty om de register vermelding MyKey toe te voegen aan de mijn bedrijf-sleutel. De opdracht gebruikt de para meter UseTransaction voor het toevoegen van de opdracht in de trans actie.

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

De opdracht retourneert een object dat de nieuwe register vermelding vertegenwoordigt, maar de register vermelding is niet gewijzigd.

```
MyKey
-----
123
```

Als u de items wilt ophalen die zich momenteel in het REGI ster bevinden, gebruikt u een Get-ChildItem opdracht (' dir ') zonder de para meter UseTransaction. Met de volgende opdracht worden items opgehaald die beginnen met ' M '.

```powershell
dir m*
```

Het resultaat geeft aan dat er nog geen items zijn toegevoegd aan de mijn bedrijf-sleutel.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

Als u een voor beeld wilt zien van het effect van het door voeren van de trans actie, voert u de opdracht Get-ChildItem ("dir") in met de para meter UseTransaction. Met deze opdracht wordt een overzicht gegeven van de gegevens in de trans actie.

```powershell
dir m* -useTransaction
```

Het resultaat geeft aan dat, als de trans actie is doorgevoerd, de vermelding MyKey wordt toegevoegd aan de sleutel mijn bedrijf.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a>VOOR BEELD 4: TRANSACTIONELE EN NIET-TRANSACTIONELE OPDRACHTEN COMBI NEREN

U kunt niet-transactionele opdrachten opgeven tijdens een trans actie. De niet-transactionele opdrachten beïnvloeden de gegevens onmiddellijk, maar ze hebben geen invloed op de trans actie.
Met de volgende opdracht wordt een trans actie gestart in de register sleutel HKCU: \ software.

```powershell
start-transaction
```

De volgende drie opdrachten gebruiken de New-Item cmdlet om sleutels aan het REGI ster toe te voegen.
De eerste en derde opdracht gebruiken de para meter UseTransaction om de opdrachten in de trans actie op te genomen. Met de tweede opdracht wordt de para meter wegge laten. Omdat de tweede opdracht niet in de trans actie is opgenomen, is deze onmiddellijk van kracht.

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

Als u de huidige status van het REGI ster wilt weer geven, gebruikt u de opdracht Get-ChildItem ("dir") zonder de para meter UseTransaction. Met deze opdracht worden items opgehaald die beginnen met ' M '.

```powershell
dir m*
```

Het resultaat toont aan dat de sleutel MyCompany2 is toegevoegd aan het REGI ster, maar de MyCompany1-en MyCompany3-sleutels, die deel uitmaken van de trans actie, worden niet toegevoegd.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

Met de volgende opdracht wordt de trans actie door doorgevoerd.

```powershell
complete-transaction
```

Nu worden de sleutels die als onderdeel van de trans actie zijn toegevoegd, weer gegeven in het REGI ster.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
83   1 Microsoft                      {(default)}
0    0 MyCompany1                     {}
0    0 MyCompany2                     {}
0    0 MyCompany3                     {}
```

### <a name="example-5-using-automatic-rollback"></a>VOOR BEELD 5: AUTOMATISCH TERUGDRAAIEN GEBRUIKEN

Wanneer een opdracht in een trans actie een fout genereert, wordt de trans actie automatisch teruggezet.

Dit standaard gedrag is bedoeld voor scripts die trans acties uitvoeren. Scripts zijn doorgaans goed getest en bevatten logica voor fout afhandeling, waardoor fouten niet worden verwacht en de trans actie moet worden beëindigd.

Met de eerste opdracht wordt een trans actie gestart in de register sleutel HKCU: \ software.

```powershell
start-transaction
```

De volgende opdracht maakt gebruik van de cmdlet New-Item om de sleutel mijn bedrijf toe te voegen aan het REGI ster. De opdracht maakt gebruik van de para meter UseTransaction (de alias is ' usetx ') om de opdracht in de trans actie op te neemt.

```powershell
New-Item MyCompany -UseTX
```

Omdat de mijn bedrijf-sleutel al in het REGI ster bestaat, mislukt de opdracht en wordt de trans actie teruggedraaid.

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

Met een Get-Transaction-opdracht wordt bevestigd dat de trans actie is teruggedraaid en dat de SubscriberCount 0 is.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a>VOOR BEELD 6: DE TERUGDRAAI VOORKEUR WIJZIGEN

Als u wilt dat de trans actie meer fout tolerant is, kunt u de para meter RollbackPreference van Start-Transaction gebruiken om de voor keur te wijzigen.

Met de volgende opdracht wordt een trans actie gestart met de voor keur voor ongedaan maken van ' Never '.

```powershell
start-transaction -rollbackpreference Never
```

In dit geval wordt de trans actie niet automatisch teruggezet wanneer de opdracht mislukt.

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

Omdat de trans actie nog steeds actief is, kunt u de opdracht opnieuw verzenden als onderdeel van de trans actie.

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a>VOOR BEELD 7: DE CMDLET USE-TRANS ACTION GEBRUIKEN

Met de cmdlet Use-Transaction kunt u direct scripts uitvoeren op Microsoft .NET Framework-objecten die trans acties ondersteunen. Use-Transaction neemt een script blok dat alleen opdrachten en expressies kan bevatten die gebruikmaken van .NET Framework objecten waarvoor trans acties zijn ingeschakeld, zoals exemplaren van de klasse micro soft. Power shell. commands. Management. TransactedString.

Met de volgende opdracht wordt een trans actie gestart.

```powershell
start-transaction
```

Met de volgende New-Object opdracht maakt u een instantie van de klasse TransactedString en slaat u deze op in de $t variabele.

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

Met de volgende opdracht wordt de methode Append van het object TransactedString gebruikt om tekst toe te voegen aan de teken reeks. Omdat de opdracht geen deel uitmaakt van de trans actie, is de wijziging direct van kracht.

```powershell
$t.append("Windows")
```

De volgende opdracht maakt gebruik van dezelfde toevoeg methode om tekst toe te voegen, maar voegt de tekst toe als onderdeel van de trans actie. De opdracht bevindt zich tussen accolades en wordt ingesteld als de waarde van de para meter script Block van use-Trans Action. De para meter UseTransaction (UseTx) is vereist.

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

Als u de huidige inhoud van de transactie teken reeks in $t wilt zien, gebruikt u de methode ToString van het object TransactedString.

```powershell
$t.tostring()
```

In de uitvoer ziet u dat alleen de niet-transactionele wijzigingen van kracht zijn.

```output
Windows
```

Als u de huidige inhoud van de transactionele teken reeks in $t vanuit de trans actie wilt zien, sluit u de expressie in een Use-Transaction opdracht.

```powershell
use-transaction {$s.tostring()} -usetx
```

De weer gave van de trans actie wordt weer gegeven in de uitvoer.

```output
PowerShell
```

Met de volgende opdracht wordt de trans actie door doorgevoerd.

```powershell
complete-transaction
```

De laatste teken reeks weer geven:

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a>VOOR BEELD 8: MEERDERE ABONNEE TRANSACTIES BEHEREN

Wanneer u een trans actie start terwijl een andere trans actie wordt uitgevoerd, maakt Power Shell standaard geen tweede trans actie. In plaats daarvan wordt een abonnee toegevoegd aan de huidige trans actie.

In dit voor beeld ziet u hoe u een trans actie met meerdere abonnees kunt weer geven en beheren.

Begin met het starten van een trans actie in de sleutel HKCU: \ software.

```powershell
start-transaction
```

De volgende opdracht maakt gebruik van de Get-Transaction-opdracht voor het ophalen van de actieve trans actie.

```powershell
get-transaction
```

Het resultaat toont het object dat de actieve trans actie vertegenwoordigt.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Met de volgende opdracht wordt de sleutel mijn bedrijf toegevoegd aan het REGI ster. De opdracht gebruikt de para meter UseTransaction voor het toevoegen van de opdracht in de trans actie.

```powershell
new-item MyCompany -UseTransaction
```

De volgende opdracht maakt gebruik van de Start-Transaction-opdracht voor het starten van een trans actie. Hoewel deze opdracht bij de opdracht prompt wordt getypt, is dit scenario waarschijnlijker wanneer u een script uitvoert dat een trans actie bevat.

```powershell
start-transaction
```

Een Get-Transaction opdracht geeft aan dat het aantal abonnees van het transactie object wordt verhoogd. De waarde is nu 2.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

De volgende opdracht maakt gebruik van de cmdlet New-ItemProperty om de register vermelding MyKey toe te voegen aan de mijn bedrijf-sleutel. De para meter UseTransaction wordt gebruikt voor het toevoegen van de opdracht in de trans actie.

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

De mijn bedrijf-sleutel bestaat niet in het REGI ster, maar deze opdracht is geslaagd omdat de twee opdrachten deel uitmaken van dezelfde trans actie.

Met de volgende opdracht wordt de trans actie door doorgevoerd. Als de trans actie wordt teruggedraaid, wordt de trans actie teruggedraaid voor alle abonnees.

```powershell
complete-transaction
```

Een Get-Transaction-opdracht laat zien dat het aantal abonnees van het transactie object 1 is, maar dat de waarde van status nog steeds actief is (niet doorgevoerd).

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Voer een tweede volledige-trans actie-opdracht in om het door voeren van de trans actie te volt ooien. Als u een trans actie met meerdere abonnees wilt door voeren, moet u voor elke Start-Transaction opdracht een Complete-Transaction-opdracht invoeren.

```powershell
complete-transaction
```

Een andere Get-Transaction-opdracht laat zien dat de trans actie is doorgevoerd.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a>VOOR BEELD 9: ONAFHANKELIJKE TRANS ACTIES BEHEREN

Wanneer u een trans actie start terwijl er een andere trans actie wordt uitgevoerd, kunt u de onafhankelijke para meter van Start-Transaction gebruiken om de nieuwe trans actie onafhankelijk van de oorspronkelijke trans actie te maken.

Wanneer u dit doet, wordt door Start-Transaction een nieuw transactie object gemaakt en wordt de actieve trans actie door de nieuwe trans acties uitgevoerd.

Begin met het starten van een trans actie in de sleutel HKCU: \\ software.

```powershell
start-transaction
```

De volgende opdracht maakt gebruik van de Get-Transaction-opdracht voor het ophalen van de actieve trans actie.

```powershell
get-transaction
```

Het resultaat toont het object dat de actieve trans actie vertegenwoordigt.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Met de volgende opdracht wordt de register sleutel mijn bedrijf toegevoegd als onderdeel van de trans actie. De para meter UseTransaction (UseTx) wordt gebruikt voor het toevoegen van de opdracht in de actieve trans actie.

```powershell
new-item MyCompany -use
```

Met de volgende opdracht wordt een nieuwe trans actie gestart. De opdracht gebruikt de onafhankelijke para meter om aan te geven dat deze trans actie geen abonnee van de actieve trans actie is.

```powershell
start-transaction -independent
```

Wanneer u een onafhankelijke trans actie maakt, wordt de nieuwe (meest recent gemaakte) trans actie de actieve trans actie. U kunt een Get-Transaction opdracht gebruiken om de actieve trans actie op te halen.

```powershell
get-transaction
```

Houd er rekening mee dat de SubscriberCount van de trans actie 1 is, wat aangeeft dat er geen andere abonnees zijn en dat de trans actie nieuw is.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

De nieuwe trans actie moet worden voltooid (doorgevoerd of teruggedraaid) voordat u de oorspronkelijke trans actie kunt beheren.

Met de volgende opdracht wordt de sleutel MyOtherCompany toegevoegd aan het REGI ster. De para meter UseTransaction (UseTx) wordt gebruikt voor het toevoegen van de opdracht in de actieve trans actie.

```powershell
new-item MyOtherCompany -usetx
```

Ga nu terug naar de trans actie. Als er sprake is van een enkele trans actie met twee abonnees, wordt de trans actie teruggedraaid voor alle abonnees.

Omdat deze trans acties echter onafhankelijk zijn, wordt de nieuwste trans actie teruggedraaid, worden de wijzigingen in het REGI ster geannuleerd en wordt de oorspronkelijke trans actie gemaakt.

```powershell
undo-transaction
```

Met een Get-Transaction-opdracht wordt bevestigd dat de oorspronkelijke trans actie nog steeds actief is in de sessie.

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Met de volgende opdracht wordt de actieve trans actie doorgevoerd.

```powershell
complete-transaction
```

Een Get-ChildItem-opdracht laat zien dat het REGI ster is gewijzigd.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

## <a name="see-also"></a>ZIE OOK

[Start-trans actie](xref:Microsoft.PowerShell.Management.Start-Transaction)

[Get-trans actie](xref:Microsoft.PowerShell.Management.Get-Transaction)

[Volt ooien-trans actie](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[Ongedaan maken-trans actie](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[Gebruik-trans actie](xref:Microsoft.PowerShell.Management.Use-Transaction)

[Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[about_Providers](about_Providers.md)
