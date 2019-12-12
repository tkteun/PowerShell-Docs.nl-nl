---
ms.date: 08/24/2018
keywords: Power shell, cmdlet
title: Power shell-opdracht namen leren
ms.openlocfilehash: a65ffcdca6510093b0a77234e20546b6cc1f02bf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030425"
---
# <a name="learning-powershell-command-names"></a>Power shell-opdracht namen leren

Voor het leren van namen van opdrachten en para meters is een aanzienlijke investering met de meeste opdracht regel interfaces vereist. Het probleem is dat er weinig patronen zijn. Het is de enige manier om de opdrachten en para meters te leren die u regel matig moet gebruiken.

Wanneer u met een nieuwe opdracht of para meter werkt, kunt u niet altijd gebruiken wat u al kent. U moet een nieuwe naam zoeken en leren. Normaal gesp roken beginnen opdracht regel interfaces met een kleine set hulpprogram ma's en groeien met incrementele toevoegingen. Het is eenvoudig om te zien waarom er geen standaard structuur is.
Dit lijkt logisch voor opdracht namen, aangezien elke opdracht een afzonderlijk hulp programma is. Power Shell heeft een betere manier om opdracht namen af te handelen.

## <a name="learning-command-names-in-traditional-shells"></a>Opdracht namen leren in traditionele schalen

De meeste opdrachten zijn gebouwd om elementen van het besturings systeem of toepassingen, zoals services of processen, te beheren. De opdrachten hebben namen die al dan niet in een familie passen. U kunt bijvoorbeeld op Windows-systemen de opdrachten `net start` en `net stop` gebruiken om een service te starten en te stoppen. **Sc. exe** is een ander Service beheer programma voor Windows. Deze naam past niet bij het naamgevings patroon voor de **net. exe** -service opdrachten. Voor proces beheer heeft Windows de opdracht **tasklist. exe** voor het weer geven van processen en de opdracht **taskkill. exe** om processen af te breken.

Deze opdrachten hebben ook onregelmatige parameter specificaties. U kunt de opdracht `net start` niet gebruiken om een service op een externe computer te starten. Met de opdracht **sc. exe** kunt u een service op een externe computer starten. Maar om de externe computer op te geven, moet u een voor voegsel van de naam met een dubbele back slash opgeven. Als u de Spooler-service wilt starten op een externe computer met de naam DC01, typt u `sc.exe \\DC01 start spooler`.
Als u taken wilt weer geven die worden uitgevoerd op DC01, gebruikt u de **/s** para meter en de computer naam zonder backslashes. Voorbeeld: `tasklist /S DC01`.

> [!NOTE]
> Vóór Power shell V6 was `sc` een alias voor de `Set-Content`-cmdlet. Daarom moet u, om de **sc. exe** -opdracht uit te voeren in een versie van Power shell vóór V6, de volledige bestands naam **sc. exe** opnemen, inclusief de bestands extensie **exe**.

Services en processen zijn voor beelden van beheer bare elementen op een computer met goed gedefinieerde levens cycli. U kunt Services en processen starten of stoppen of een lijst ophalen van alle services of processen die momenteel worden uitgevoerd. Hoewel er belang rijke technische verschillen tussen hen zijn, zijn de acties die u uitvoert op Services en processen conceptueel gezien hetzelfde. Bovendien is het mogelijk om een actie aan te passen door para meters op te geven. Dit kan ook conceptueel zijn.

Power Shell maakt gebruik van deze overeenkomsten om het aantal afzonderlijke namen te beperken dat u moet weten om te begrijpen en cmdlets te gebruiken.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlets maken gebruik van termen van naam woorden uit de werk woorden om het onthouden van de opdracht te verminderen

Power Shell maakt gebruik van een naamgevings systeem voor werk woorden. Elke cmdlet-naam bestaat uit een standaard woord dat is afgebroken met een specifieke naam. Power shell-werk woorden zijn niet altijd Engels, maar ze drukken specifieke acties uit in Power shell. Zelfstandige naam woorden zijn veel hetzelfde als zelfstandige naam woorden in elke taal. Hierin worden specifieke typen objecten beschreven die belang rijk zijn in systeem beheer. Het is eenvoudig om te laten zien hoe deze twee deel namen de leer inspanningen verminderen door enkele voor beelden te bekijken.

Power Shell heeft een aanbevolen set standaard woorden. Zelfstandige naam woorden zijn minder beperkt, maar geven altijd aan waar de term op reageert. Power Shell heeft opdrachten als `Get-Process`, `Stop-Process`, `Get-Service`en `Stop-Service`.

Voor dit voor beeld van twee zelfstandige naam woorden en termen is consistentie niet vereenvoudigd. Breid deze lijst uit naar een gestandaardiseerde set van 10 werk woorden en tien zelfstandige naam woorden. Nu hebt u slechts twintig woorden om te begrijpen.
Deze woorden kunnen echter worden gecombineerd om 100 afzonderlijke opdracht namen te maken.

Het is eenvoudig om te begrijpen wat een Power shell-opdracht doet door de naam ervan te lezen. De opdracht voor het afsluiten van een computer is `Stop-Computer`. De opdracht voor het weer geven van alle computers in een netwerk is `Get-Computer`. De opdracht voor het ophalen van de systeem datum is `Get-Date`.

U kunt alle opdrachten weer geven die een bepaalde term bevatten met de para meter **Verb** voor `Get-Command`. Als u bijvoorbeeld alle cmdlets wilt zien die gebruikmaken van de term `Get`, typt u:

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Gebruik de para meter van het **zelfstandig naam woord** om een reeks opdrachten te bekijken die van invloed zijn op hetzelfde type object. Voer bijvoorbeeld de volgende opdracht uit om de opdrachten weer te geven die beschikbaar zijn voor het beheren van services:

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Cmdlets gebruiken standaard parameters

Zoals eerder is opgemerkt, hebben opdrachten die worden gebruikt in traditionele opdracht regel interfaces niet altijd consistente parameter namen. Para meters zijn vaak enkelvoudige of korte woorden die eenvoudig kunnen worden getypt, maar niet eenvoudig kunnen worden begrepen door nieuwe gebruikers.

In tegens telling tot de meeste andere traditionele opdracht regel interfaces, worden para meters rechtstreeks door Power shell verwerkt en wordt deze rechtstreekse toegang tot de para meters, samen met de richt lijnen voor ontwikkel aars, gebruikt om parameter namen te standaardiseren. Deze richt lijnen moedigen aan, maar garandeert niet dat elke cmdlet voldoet aan de standaard.

Power Shell standaard het scheidings teken voor para meters. Voor parameter namen wordt altijd een '-' voorafgegaan door een Power shell-opdracht. Kijk eens naar het volgende voorbeeld:

```powershell
Get-Command -Name Clear-Host
```

De naam van de para meter is **naam**, maar wordt getypt als `-Name` wanneer deze wordt gebruikt op de opdracht regel als een para meter.

Hier volgen enkele van de algemene kenmerken van de standaard parameter namen en-gebruik.

### <a name="the-help-parameter-"></a>De Help-para meter (?)

Wanneer u de para meter `-?` opgeeft voor een cmdlet, wordt in Power shell Help voor de cmdlet weer gegeven.
De cmdlet wordt niet uitgevoerd.

### <a name="common-parameters"></a>Algemene para meters

Power Shell heeft verschillende *algemene para meters*. Deze para meters worden bepaald door de Power shell-engine. Algemene para meters gedragen zich altijd op dezelfde manier. De algemene para meters zijn **WhatIf**, **confirm**, **uitgebreidheids**, **debug**, **Warning**, **Error Action**, **ErrorVariable**, **outvariable**en **outbuffer**.

### <a name="recommended-parameter-names"></a>Aanbevolen parameter namen

De Power shell core-cmdlets gebruiken standaard namen voor vergelijk bare para meters. Het gebruik van deze standaard namen wordt niet afgedwongen, maar er is expliciete richt lijnen om standaardisatie te stimuleren.

De aanbevolen naam voor een para meter die verwijst naar een computer is **computer naam**in plaats van server, host, systeem, knoop punt of een ander algemeen alternatief. Andere belang rijke aanbevolen parameter namen zijn **Force**, **exclude**, **include**, **PassThru**, **Path**en **CaseSensitive**.
