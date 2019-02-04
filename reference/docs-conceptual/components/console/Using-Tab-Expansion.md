---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met behulp van de tabbladuitbreiding
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686199"
---
# <a name="using-tab-expansion"></a>Met behulp van de tabbladuitbreiding

Een manier voor het automatisch voltooien van de namen van grote bestanden of opdrachten bieden opdrachtregel shells vaak opdracht vermelding versnellen en het geven van. Windows PowerShell kunt u in te vullen in bestandsnamen en namen van de cmdlets door te drukken de **tabblad** sleutel.

> [!NOTE]
> Tabbladuitbreiding wordt bepaald door de interne functie TabExpansion of TabExpansion2. Omdat deze functie kan worden gewijzigd of overschreven, is deze discussie een handleiding voor het gedrag van de standaardconfiguratie van PowerShell.

Automatisch doorvoeren in een bestandsnaam of het pad van de beschikbare opties, typt u deel uit van de naam en druk op de **tabblad** sleutel. PowerShell wordt de naam van de automatisch uitgebreid naar de eerste overeenkomende reeks gevonden. Druk op de **tabblad** sleutel herhaaldelijk wordt bladeren door alle van de beschikbare opties.

Het tabbladuitbreiding van de namen van de cmdlets is enigszins anders. Voor het gebruik van tabbladuitbreiding op de cmdletnaam van een, typt u het hele eerste deel van de naam (de term) en het afbreekstreepje dat erop volgt. U kunt invullen in meer van de naam van een gedeeltelijke overeenkomst. Als u bijvoorbeeld **get-co** en druk vervolgens op de **tabblad** sleutel, PowerShell wordt automatisch uitgebreid met deze de **Get-Command** cmdlet (Let op dat deze wordt ook het geval is gewijzigd van letters aan het standaardformulier). Als u druk op **tabblad** sleutel opnieuw, PowerShell vervangt deze door de alleen andere overeenkomende cmdlet-naam, **Get-inhoud**.

U kunt herhaaldelijk tabbladuitbreiding gebruiken op dezelfde regel. U kunt bijvoorbeeld tabbladuitbreiding gebruiken op de naam van de **Get-inhoud** cmdlet door in te voeren:

```
PS> Get-Con<Tab>
```

Wanneer u drukt u op de **tabblad** sleutel, de opdracht wordt er uitgebreid naar:

```
PS> Get-Content
```

U kunt vervolgens gedeeltelijk Geef het pad op naar het logboekbestand Active Setup en tabbladuitbreiding opnieuw gebruiken:

```
PS> Get-Content c:\windows\acts<Tab>
```

Wanneer u drukt u op de **tabblad** sleutel, de opdracht wordt er uitgebreid naar:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Een beperking van het tabblad-uitbreidingsproces is dat tabbladen altijd worden geïnterpreteerd als pogingen om uit te voeren van een woord. Als u kopieert en plakt opdrachtvoorbeelden in een PowerShell-console, controleert u of het voorbeeld bevat geen tabbladen. Als dit het geval is, worden de resultaten onvoorspelbaar en bijna zeker worden niet juist.