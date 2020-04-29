---
ms.date: 08/23/2018
keywords: Power shell, cmdlet
title: Informatie over belangrijke PowerShell-concepten
ms.openlocfilehash: 8f9af370db46ea47dbccbabb7cc90fc27b8f2765
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030980"
---
# <a name="understanding-important-powershell-concepts"></a>Informatie over belangrijke PowerShell-concepten

Het Power shell-ontwerp integreert concepten uit verschillende omgevingen. Diverse concepten zijn bekend voor mensen die ervaring hebben met het gebruik van shells of programmeer omgevingen. Maar weinig mensen zullen over al deze informatie beschikken. Enkele van deze concepten bevat een handig overzicht van de shell.

## <a name="output-is-object-based"></a>Uitvoer is op objecten gebaseerd

In tegens telling tot traditionele opdracht regel interfaces, zijn Power shell-cmdlets ontworpen om objecten te verwerken.
Een object is gestructureerde informatie die meer is dan alleen de teken reeks die wordt weer gegeven op het scherm. De opdracht uitvoer bevat altijd extra informatie die u kunt gebruiken als u deze nodig hebt.

Als u hulpprogram ma's voor tekst verwerking hebt gebruikt voor het verwerken van gegevens in het verleden, zult u merken dat ze anders werken wanneer ze worden gebruikt in Power shell. In de meeste gevallen hebt u geen hulp middelen voor tekst verwerking nodig om specifieke gegevens op te halen. U hebt rechtstreeks toegang tot delen van de gegevens met behulp van de standaard syntaxis van Power shell-objecten.

## <a name="the-command-family-is-extensible"></a>De opdracht familie is uitbreidbaar

Interfaces zoals **cmd. exe** bieden u niet de mogelijkheid om de ingebouwde opdracht set direct uit te breiden. U kunt externe opdracht regel Programma's maken die worden uitgevoerd in **cmd. exe**. Deze externe hulpprogram ma's hebben echter geen services, zoals Help-integratie. **cmd. exe** weet niet automatisch dat deze externe hulpprogram ma's geldige opdrachten zijn.

De systeem eigen opdrachten in Power shell worden ' *cmdlets* ' (uitgesp roken opdracht-staat) genoemd. U kunt uw eigen cmdlets-modules en-functies maken met behulp van gecompileerde code of scripts. Met modules kunnen cmdlets en providers aan de shell worden toegevoegd. Power shell ondersteunt ook scripts die vergelijkbaar zijn met UNIX-shell scripts en **cmd. exe** batch-bestanden.

## <a name="powershell-handles-console-input-and-display"></a>Power shell verwerkt console-invoer en-weer gave

Wanneer u een opdracht typt, verwerkt Power shell de invoer van de opdracht regel altijd rechtstreeks. Power shell formatteert ook de uitvoer die op het scherm wordt weer gegeven. Dit verschil is aanzienlijk omdat het de vereiste werk van elke cmdlet vermindert. Zo zorgt u ervoor dat u altijd op dezelfde manier kunt werken met elke cmdlet. Cmdlet-ontwikkel aars hoeven geen code te schrijven voor het parseren van de opdracht regel argumenten of het format teren van de uitvoer.

Traditionele opdracht regel Programma's hebben hun eigen schema's voor het aanvragen en weer geven van Help. Sommige opdracht regel Programma's gebruiken **/?** de Help-weer gave activeren; andere gebruiken **-?**, **/h**of zelfs **//**. De Help wordt in een GUI-venster weer gegeven, in plaats van in de-console weer te geven. Als u de verkeerde para meter gebruikt, kan het hulp programma mogelijk negeren wat u hebt getypt en de uitvoering van een taak automatisch starten.
Omdat Power shell de opdracht regel automatisch parseert en verwerkt, wordt de **-?** de para meter betekent altijd Help voor deze opdracht weer geven.

> [!NOTE]
> Als u een grafische toepassing uitvoert in Power shell, wordt het venster voor de toepassing geopend.
> Power shell is alleen van toepassing op het verwerken van de opdracht regel invoer die u opgeeft of de toepassings uitvoer die wordt geretourneerd naar het console venster. Dit heeft geen invloed op de manier waarop de toepassing intern werkt.

## <a name="powershell-uses-some-c-syntax"></a>Power shell gebruikt een van de C#-syntaxis

Power shell is gebaseerd op de .NET Framework. Er worden enkele syntaxis functies en tref woorden gedeeld met de programmeer taal C#. Met Power shell leren is het veel eenvoudiger om C# te leren. Als u al bekend bent met C#, kunnen deze overeenkomsten eenvoudiger worden gemaakt met Power shell.
