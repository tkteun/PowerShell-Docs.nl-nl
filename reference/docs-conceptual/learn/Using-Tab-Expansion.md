---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Met behulp van de tabbladuitbreiding
description: Hierin wordt uitgelegd hoe u de functie voor tabblad uitbreiding gebruikt in Power shell.
ms.openlocfilehash: 658cdf5ddf78bbd6dd431c2170cd5ff643e6bf95
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661338"
---
# <a name="using-tab-expansion"></a>Met behulp van de tabbladuitbreiding

Opdracht regel shells bieden vaak een manier om de namen van lange bestanden of opdrachten automatisch te volt ooien, opdracht invoer te versnellen en hints te bieden. Met Power shell kunt u bestands namen en namen van cmdlets invullen door op de <kbd>Tab</kbd> -toets te drukken.

> [!NOTE]
> Tabblad uitbreiding wordt bepaald door de interne functie TabExpansion of TabExpansion2. Omdat deze functie kan worden gewijzigd of overschreven, is deze discussie een hand leiding voor het gedrag van de standaard-Power shell-configuratie.

Als u automatisch een bestands naam of pad van de beschik bare opties wilt invullen, typt u een deel van de naam en drukt u op de <kbd>Tab</kbd> -toets. Power shell breidt de naam automatisch uit naar het eerste overeenkomende item dat wordt gevonden. Door herhaaldelijk op de <kbd>Tab</kbd> -toets te drukken, worden alle beschik bare opties door lopen.

De tabblad-uitbrei ding van de namen van cmdlets is iets anders. Als u tabblad uitbrei ding wilt gebruiken voor de naam van een cmdlet, typt u het volledige eerste deel van de naam (de opdracht) en het afbreek streepje dat deze volgt. U kunt de naam van een gedeeltelijke overeenkomst invullen. Als u bijvoorbeeld typt `get-co` en vervolgens op de <kbd>Tab</kbd> -toets drukt, wordt dit door Power shell automatisch uitgebreid naar de `Get-Command` cmdlet (u ziet dat het hoofdletter gebruik ook wordt gewijzigd in het standaard formulier). Als u opnieuw op <kbd>Tab</kbd> drukt, wordt dit door Power shell vervangen door de enige andere overeenkomende naam van de cmdlet `Get-Content` .

> [!NOTE]
> Vanaf Power shell 7,0 worden met <kbd>Tab</kbd> ook verkorte cmdlets en functies uitgevouwen. `i-psdf<tab>`Retourneert bijvoorbeeld `Import-PowerShellDataFile` .

U kunt de tab-uitbrei ding herhaaldelijk op dezelfde regel gebruiken. U kunt bijvoorbeeld tabblad uitbrei ding op de naam van de `Get-Content` cmdlet gebruiken door het volgende in te voeren:

```
PS> Get-Con<Tab>
```

Wanneer u op de <kbd>Tab</kbd> -toets drukt, wordt de opdracht uitgebreid naar:

```
PS> Get-Content
```

Vervolgens kunt u het pad naar het actieve Setup-logboek bestand opgeven en de tab-uitbrei ding opnieuw gebruiken:

```
PS> Get-Content c:\windows\acts<Tab>
```

Wanneer u op de <kbd>Tab</kbd> -toets drukt, wordt de opdracht uitgebreid naar:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Een beperking van het tabblad expansie proces is dat tabbladen altijd worden ge??nterpreteerd als pogingen om een woord te volt ooien. Als u voor beelden van de opdracht kopieert en plakt naar een Power shell-console, moet u ervoor zorgen dat het voor beeld geen tabbladen bevat. Als dat het geval is, kunnen de resultaten onvoorspelbaar zijn en is bijna zeker niet wat u hebt beoogd.
