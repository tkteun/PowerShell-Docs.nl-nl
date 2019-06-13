---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met behulp van de tabbladuitbreiding
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031022"
---
# <a name="using-tab-expansion"></a>Met behulp van de tabbladuitbreiding

Een manier voor het automatisch voltooien van de namen van grote bestanden of opdrachten bieden opdrachtregel shells vaak opdracht vermelding versnellen en het geven van aanbevolen basisservers. PowerShell kunt u in te vullen in bestandsnamen en namen van de cmdlets door te drukken de <kbd>tabblad</kbd> sleutel.

> [!NOTE]
> Tabbladuitbreiding wordt bepaald door de interne functie TabExpansion of TabExpansion2. Omdat deze functie kan worden gewijzigd of overschreven, is deze discussie een handleiding voor het gedrag van de standaardconfiguratie van PowerShell.

Automatisch doorvoeren in een bestandsnaam of het pad van de beschikbare opties, typt u deel uit van de naam en druk op de <kbd>tabblad</kbd> sleutel. PowerShell wordt de naam van de automatisch uitgebreid naar de eerste overeenkomende reeks gevonden. Druk op de <kbd>tabblad</kbd> sleutel herhaaldelijk wordt bladeren door alle van de beschikbare opties.

Het tabbladuitbreiding van de namen van de cmdlets is enigszins anders. Voor het gebruik van tabbladuitbreiding op de cmdletnaam van een, typt u het hele eerste deel van de naam (de term) en het afbreekstreepje dat erop volgt. U kunt invullen in meer van de naam van een gedeeltelijke overeenkomst. Als u bijvoorbeeld `get-co` en druk vervolgens op de <kbd>tabblad</kbd> sleutel, PowerShell wordt automatisch uitgebreid met deze de `Get-Command` cmdlet (Let op dat deze wordt ook de weergave van letters gewijzigd naar hun standaard vorm). Als u druk op <kbd>tabblad</kbd> sleutel opnieuw, PowerShell vervangt deze door de alleen andere overeenkomende cmdlet-naam, `Get-Content`.

U kunt herhaaldelijk tabbladuitbreiding gebruiken op dezelfde regel. U kunt bijvoorbeeld tabbladuitbreiding gebruiken op de naam van de `Get-Content` cmdlet door in te voeren:

```
PS> Get-Con<Tab>
```

Wanneer u drukt u op de <kbd>tabblad</kbd> sleutel, de opdracht wordt er uitgebreid naar:

```
PS> Get-Content
```

U kunt vervolgens gedeeltelijk Geef het pad op naar het logboekbestand Active Setup en tabbladuitbreiding opnieuw gebruiken:

```
PS> Get-Content c:\windows\acts<Tab>
```

Wanneer u drukt u op de <kbd>tabblad</kbd> sleutel, de opdracht wordt er uitgebreid naar:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Een beperking van het tabblad-uitbreidingsproces is dat tabbladen altijd worden geïnterpreteerd als pogingen om uit te voeren van een woord. Als u kopieert en plakt opdrachtvoorbeelden in een PowerShell-console, controleert u of het voorbeeld bevat geen tabbladen. Als dit het geval is, worden de resultaten onvoorspelbaar en bijna zeker worden niet juist.
