---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Met behulp van de uitbreiding van het tabblad
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 8412bd97a95719f07b16c6671d3b8801bbfab8e3
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2017
---
# <a name="using-tab-expansion"></a>Met behulp van de uitbreiding van het tabblad
Opdrachtregelprogramma houders bevatten vaak een manier om de namen van opdrachten of grote bestanden automatisch te voltooien versnellen van de opdracht vermelding en bieden. Windows PowerShell kunt u in te vullen bestandsnamen en de namen van cmdlets door op de **tabblad** sleutel.

> [!NOTE]
> Tabblad uitbreiding wordt bepaald door de interne functie TabExpansion of TabExpansion2. Omdat deze functie kan worden gewijzigd of overschreven, is deze discussie een handleiding voor het gedrag van de standaardconfiguratie van PowerShell.

Automatisch doorvoeren in een bestandsnaam of het pad van de beschikbare opties, typt u deel van de naam en druk op de **tabblad** sleutel. PowerShell wordt de naam automatisch uitgebreid naar de eerste overeenkomst gevonden. Druk op de **tabblad** sleutel herhaaldelijk wordt doorlopen alle van de beschikbare opties.

De uitbreiding van het tabblad van de namen van de cmdlet verschilt enigszins. Wilt gebruiken tabblad uitbreiding van de naam van een cmdlet, typt u het volledige eerste deel van de naam (de term) en het afbreekstreepje die erop volgt. U kunt ook opgeven in meer van de naam van een gedeeltelijke overeenkomst. Als u bijvoorbeeld **get-co** en druk vervolgens op de **tabblad** sleutel, PowerShell wordt automatisch uitgebreid met deze de **Get-Command** cmdlet (Let op dat deze wordt ook het geval is gewijzigd van letters aan het standaardformulier). Als u op **tabblad** sleutel opnieuw, PowerShell wordt vervangen door dit met alleen andere overeenkomende cmdlet naam, **Get-inhoud**.

U kunt herhaaldelijk tabblad uitbreiding gebruiken op dezelfde lijn. Bijvoorbeeld, kunt u de uitbreiding van het tabblad op de naam van de **Get-inhoud** cmdlet door te voeren:

```
PS> Get-Con<Tab>
```

Wanneer u op drukt de **tabblad** sleutel, de opdracht wordt vergroot tot:

```
PS> Get-Content
```

U kunt gedeeltelijk Geef het pad naar het logboekbestand Active Setup en tabblad uitbreiding opnieuw gebruiken:

```
PS> Get-Content c:\windows\acts<Tab>
```

Wanneer u op drukt de **tabblad** sleutel, de opdracht wordt vergroot tot:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Een beperking van het tabblad uitbreidingsproces is dat tabbladen altijd worden geïnterpreteerd als pogingen tot het voltooien van een woord. Als u kopieert en plakt u opdrachtvoorbeelden in een PowerShell-console, controleert u of het voorbeeld bevat geen tabbladen. Zo ja, wordt de resultaten onvoorspelbaar en bijna zeker niet juist.

