---
ms.date: 07/09/2020
ms.topic: reference
title: Overzicht van uitgebreid type systeem
description: Overzicht van uitgebreid type systeem
ms.openlocfilehash: f4a789f779fa8a52f0fe524abff7ec3311e93b6c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655725"
---
# <a name="extended-type-system-overview"></a>Overzicht van uitgebreid type systeem

Power shell gebruikt het object **PSObject** om de typen objecten op twee manieren uit te breiden. Eerst biedt het **PSObject** -object een manier om verschillende weer gaven van specifieke object typen weer te geven. Dit wordt aangeduid met een aangepaste weer gave van een object. Ten tweede biedt het **PSObject** -object een manier om leden toe te voegen aan een bestaand object. Samen met een bestaand object dat wordt aangeduid als het basis object, biedt het **PSObject** -object een Extended-type systeem (ETS) dat script-en cmdlet-ontwikkel aars kunnen gebruiken voor het bewerken van .net-objecten in de shell.

## <a name="cmdlet-and-script-development-issues"></a>Problemen met de implementatie van cmdlets en scripts

Met ETS worden twee fundamentele problemen opgelost:

Ten eerste hebben sommige .NET-objecten niet het vereiste standaard gedrag voor het fungeren als de gegevens tussen cmdlets.

- Sommige .NET-objecten zijn meta-objecten (bijvoorbeeld: WMI-objecten, ADO-objecten en XML-objecten) waarvan de leden de gegevens beschrijven die ze bevatten. In een script omgeving is het echter de Inge sloten gegevens die het interessantst zijn, niet de beschrijving van de Inge sloten gegevens. ETS lost dit probleem op door het begrip te introduceren van adapters die het onderliggende .NET-object aanpassen om de verwachte standaard semantiek te krijgen.
- Sommige .NET-object leden zijn niet consistent met de naam, bieden een ontoereikende set van open bare leden of bieden onvoldoende mogelijkheden. ETS lost dit probleem op door de mogelijkheid te bieden om het .NET-object uit te breiden met aanvullende leden.

Ten tweede is de Power shell-script taal _typeloos_ omdat een variabele niet van een bepaald type moet worden gedeclareerd. Dat wil zeggen dat de variabelen die een script ontwikkelaar maakt, op hetzelfde _type_ zijn. Het Power shell-systeem is echter "type-aangedreven" in dat is afhankelijk van een type naam die kan worden gebruikt voor basis bewerkingen, zoals het uitvoeren van resultaten of het sorteren.

Daarom moet een script ontwikkelaar de mogelijkheid hebben om het type van een van de variabelen te vermelden en hun eigen set dynamisch getypte ' objecten ' te bouwen die eigenschappen en methoden bevatten en kunnen deel nemen aan het type systeem. ETS lost dit probleem op door een gemeen schappelijk object te bieden voor de script taal die de mogelijkheid heeft om het type dynamisch in te stellen en leden dynamisch toe te voegen.

Met de functie **PSObject** wordt het eerder genoemde probleem opgelost door het object voor de gegevens uitwisseling op te geven, dat fungeert als de basis van alle object toegang vanuit de script taal en een standaard abstractie voor de cmdlet-ontwikkelaar biedt.

### <a name="cmdlet-developers"></a>Cmdlet-ontwikkel aars

Voor de cmdlet-ontwikkel aars biedt ETS de volgende ondersteuning:

- De abstractie voor het werken met objecten op een algemene manier met behulp van het **PSObject** -object. ETS biedt ook de mogelijkheid om in te zoomen op deze samen vattingen, indien nodig.
- De mechanismen voor het maken van een standaard gedrag voor opmaak, sortering, serialisatie en andere systeem bewerkingen van het object type met behulp van een bekende set uitgebreide leden.
- De methode voor het uitvoeren van een object met dezelfde semantiek als de script taal met behulp van een LanguagePrimitives-object.
- De methode om een hash-tabel dynamisch te ' typen ' zodat de rest van het systeem effectief kan worden uitgevoerd.

### <a name="script-developers"></a>Script ontwikkelaars

Voor de script ontwikkelaars biedt ETS de volgende ondersteuning:

- De mogelijkheid om te verwijzen naar een onderliggend object type met dezelfde syntaxis ( `$a.x` ).
- De mogelijkheid om toegang te krijgen tot meer dan de abstractie van het **PSObject** -object (zoals het openen van alleen aangepaste leden of het openen van het basis object zelf).
- De mogelijkheid om bekende leden te definiëren die de opmaak, sortering, serialisatie en andere bewerkingen van een object exemplaar of type bepalen.
- De manier om een object als een specifiek type te noemen en zo de overname van de op type gebaseerde leden te beheren.
- De mogelijkheid om uitgebreide leden toe te voegen, te verwijderen en te wijzigen.
- De mogelijkheid om het **PSObject** -object zelf te bewerken als dat nodig is.

## <a name="the-psobject-class"></a>De PSObject-klasse

Het object **PSObject** is de basis van alle object toegang vanuit de script taal en biedt een standaard abstractie voor de cmdlet-ontwikkelaar. Het bevat een base-object (een .NET-object) en alle instantie leden (leden, met name uitgebreide leden, die aanwezig zijn op een bepaald object exemplaar en niet noodzakelijkerwijs op andere objecten van hetzelfde type). Afhankelijk van het type van het basis object, kan het **PSObject** -object ook impliciete en expliciete toegang bieden tot aangepaste leden en op type gebaseerde uitgebreide leden.

Het **PSObject** -object biedt de volgende mechanismen:

- De mogelijkheid om een **PSObject** te maken met of zonder een base-object.
- De mogelijkheid om toegang te krijgen tot alle leden van elk geconstrueerd **PSObject** -object via een gemeen schappelijk lookup-algoritme en de mogelijkheid om die algoritme te negeren wanneer dat nodig is.
- De mogelijkheid om de type namen van de geconstrueerde **PSObject** -objecten op te halen en in te stellen, zodat scripts en cmdlets kunnen verwijzen naar vergelijk bare **PSObject** -objecten met dezelfde type naam, ongeacht het type van hun basis object.

### <a name="how-to-construct-a-psobject"></a>Een PSObject maken

In de volgende lijst worden manieren beschreven om een **PSObject** -object te maken:

- Het aanroepen van de **PSObject** . #ctor-constructor maakt een nieuw **PSObject** -object met een basis object van PSCustomObject. Een basis object van dit type geeft aan dat het **PSObject** -object geen zinvol base-object heeft. Een **PSObject** -object met dit type base-object biedt echter een eigenschappen verzameling waarmee cmdlet-ontwikkel aars nuttige informatie kunnen vinden door uitgebreidere leden toe te voegen.

Ontwikkel aars kunnen ook het object type-name opgeven, waarmee dit object de uitgebreide leden met andere **PSObject** -objecten van dezelfde type naam kan delen.

- Als de constructor **PSObject** . #ctor (System. object) wordt aangeroepen, wordt een nieuw **PSObject** -object gemaakt met een basis object van het type System. object.

  In dit geval is de type naam voor het gemaakte object een verzameling van de Afleidings hiërarchie van het basis object. Bijvoorbeeld: de type naam voor de **PSObject** die een ProcessInfo base-object bevat, zou de volgende namen kunnen bevatten.

  - System. Diagnostics. process
  - System. ComponentModel. component
  - System. MarshalByRefObject
  - System. object

- De **PSObject** aanroepen. Methode AsPSObject (System. object) maakt een nieuw **PSObject** -object op basis van een geleverd object.

  Als het opgegeven object van het type System. object is, wordt het geleverde object gebruikt als het basis object voor het nieuwe **PSObject** -object. Als het opgegeven object al een **PSObject** -object is, wordt het geleverde object geretourneerd als is.

### <a name="base-adapted-and-extended-members"></a>Basis, aangepaste en uitgebreide leden

In het algemeen gebruiken ETS de volgende voor waarden om de relatie weer te geven tussen de oorspronkelijke leden van het basis object en de leden die door Power shell zijn toegevoegd. Zie [PSObject-klasse](/dotnet/api/system.management.automation.psobject)voor meer informatie over de specifieke typen leden die worden gebruikt door het **PSObject** -object.

#### <a name="base-object-members"></a>Leden van basis object

Als het basis object wordt opgegeven bij het maken van de **PSObject** -objecten, worden de leden van het basis object beschikbaar gesteld via de eigenschap members.

#### <a name="adapted-members"></a>Aangepaste leden

Wanneer een base-object een meta-object is, een dat gegevens bevat op een algemene manier waarvan de eigenschappen hun Inge sloten gegevens beschrijven, past ETS deze objecten aan een weer gave toe waarmee direct toegang tot de gegevens mogelijk wordt via aangepaste leden van het **PSObject** -object. Aangepaste leden en leden van het basis object worden geopend via de eigenschap members.

#### <a name="extended-members"></a>Uitgebreide leden

Naast de leden die beschikbaar zijn gemaakt via het basis object of de aangepaste leden die zijn gemaakt door Power shell, kan een **PSObject** ook uitgebreide leden definiëren waarmee het oorspronkelijke basis object wordt uitgebreid met aanvullende informatie die nuttig is in de script omgeving.

U kunt bijvoorbeeld alle kern-cmdlets die worden meegeleverd met Power shell, zoals de Get-Content-en Set-Content-cmdlets, een para meter Path gebruiken. Om ervoor te zorgen dat deze cmdlets en anderen kunnen werken tegen objecten van verschillende typen, kan een lid van het pad worden toegevoegd aan die objecten, zodat ze hun informatie op een gemeen schappelijke manier vermelden. Dit uitgebreide pad-lid zorgt ervoor dat de cmdlets kunnen samen werken met al deze typen, zelfs als er geen pad naar de basis klasse is.

Uitgebreide leden, aangepaste leden en base-object leden zijn allemaal toegankelijk via de eigenschap members.
