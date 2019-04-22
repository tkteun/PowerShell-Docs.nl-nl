---
title: Windows PowerShell-programmeurs&#39;s handleiding | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 75425fbd38141fc82dd834835912c357ecfa6d2b
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58920387"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell-programmeurs&#39;s-handleiding

Deze programmeergids is gericht op ontwikkelaars die geïnteresseerd zijn in een opdrachtregel beheeromgeving voor systeembeheerders te bieden. Windows PowerShell biedt een eenvoudige manier om u opdrachten voor het beheer die beschikbaar maken van .NET-objecten, terwijl u Windows PowerShell met het meeste werk voor u doen kunt maken.

U moet bij de ontwikkeling van traditionele opdracht wordt een parameter-parser, een parameter binder, filters en alle andere functionaliteit die door elke opdracht schrijven. Windows PowerShell biedt het volgende om door te gemakkelijk voor u het schrijven van opdrachten:

- Een krachtige Windows PowerShell-runtime (uitvoeringsengine) met een eigen parser en een mechanisme voor automatisch opdrachtparameters-binding.

- Hulpprogramma's voor het formatteren en weergeven van opdrachtresultaten met behulp van een opdrachtregel-interpreter (CLI).

- Ondersteuning voor een hoge mate van de functionaliteit (via Windows PowerShell-providers), waarmee u eenvoudig toegang krijgen tot opgeslagen gegevens.

  Weinig kosten, kunt u een .NET-object door een uitgebreide opdracht of een reeks opdrachten die een volledige opdrachtregelervaring wordt aangeboden door de beheerder vertegenwoordigen.

  De volgende sectie bevat informatie over de belangrijkste concepten van Windows PowerShell en de voorwaarden. Maak uzelf bekend met deze concepten en termen voordat u begint met ontwikkelen.

## <a name="about-windows-powershell"></a>Over Windows PowerShell

Windows PowerShell definieert verschillende soorten opdrachten die u kunt gebruiken in ontwikkeling. Deze opdrachten zijn: functies, filters, scripts, aliassen en uitvoerbare bestanden (toepassingen). Het belangrijkste opdrachttype besproken in deze handleiding is een eenvoudige, kleine opdracht met de naam van een 'cmdlet'. Windows PowerShell het levert een set cmdlets en biedt volledige ondersteuning voor aanpassing van de cmdlet aan de behoeften van uw omgeving. De Windows PowerShell-runtime verwerkt alle opdrachttypen net als cmdlets, met behulp van pijplijnen.

Windows PowerShell biedt naast opdrachten ondersteuning voor verschillende aanpasbare providers van de Windows PowerShell die beschikbaar op specifieke sets met cmdlets. De shell werkt in de Windows PowerShell-opgegeven hosttoepassing (Windows PowerShell.exe), maar het is even toegankelijk vanuit een aangepaste hosttoepassing die u ontwikkelen kunt om te voldoen aan specifieke vereisten. Zie voor meer informatie, [hoe Windows PowerShell werkt](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell-Cmdlets

Een cmdlet is een lichtgewicht opdracht die wordt gebruikt in de Windows PowerShell-omgeving. De Windows PowerShell-runtime roept deze cmdlets binnen de context van automatiseringsscripts die beschikbaar zijn op de opdrachtregel en de Windows PowerShell-runtime ook roept deze via een programma via Windows PowerShell-APIs.

Zie voor meer informatie over cmdlets, [schrijven van een Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Windows PowerShell Providers

Bij het uitvoeren van beheertaken, moet de gebruiker mogelijk gegevens die zijn opgeslagen in een gegevensarchief (bijvoorbeeld, het bestandssysteem, het Windows-register of een certificaatarchief) te onderzoeken. Windows PowerShell definieert om deze bewerkingen gemakkelijker te maken, een module met de naam van een Windows PowerShell-provider die kan worden gebruikt voor toegang tot een bepaald gegevensarchief, zoals het Windows-register. Elke provider ondersteunt een set gerelateerde cmdlets voor het geven van de gebruiker een symmetrisch weergave van de gegevens in de store.

Windows PowerShell biedt verschillende standaard Windows PowerShell-providers. De Register-provider ondersteunt bijvoorbeeld navigatie en manipuleren van het Windows-register. Registersleutels worden weergegeven als items en registerwaarden worden behandeld als eigenschappen.

Als u beschikbaar maakt voor een gegevensopslag die de gebruiker toegang nodig hebben, moet u mogelijk het schrijven van uw eigen Windows PowerShell-provider, zoals beschreven in [het maken van Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md). Zie voor meer informatie aboutWindows PowerShell-providers, [hoe Windows PowerShell werkt](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="host-application"></a>Host-toepassing

Windows PowerShell bevat de standaard host toepassing powershell.exe, dit is een consoletoepassing die communiceert met de gebruiker en die als host fungeert voor de Windows PowerShell-runtime met behulp van een consolevenster.

Zelden moet u het schrijven van uw eigen hosttoepassing voor Windows PowerShell, hoewel aanpassing wordt ondersteund. Een situatie waarin u uw eigen toepassing mogelijk is wanneer er een vereiste voor een GUI-interface die uitgebreider dan de interface die is geleverd door de standaard-hosttoepassing. U kunt ook een aangepaste toepassing wanneer u uw GUI zijn gebaseerd op de opdrachtregel. Zie voor meer informatie, [over het maken van een Windows PowerShell-hosttoepassing](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).

### <a name="windows-powershell-runtime"></a>Windows PowerShell-Runtime

De Windows PowerShell-runtime is de engine voor het uitvoeren waarmee de verwerking van de opdracht. Het bevat de klassen die de interface tussen de host-toepassing en Windows PowerShell-opdrachten en -providers bieden. De Windows PowerShell-runtime wordt geïmplementeerd als een runspace-object voor de huidige Windows PowerShell-sessie, dit is de operationele omgeving waarin de shell en de opdrachten worden uitgevoerd. Zie voor operationele details [hoe Windows PowerShell werkt](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-language"></a>Windows PowerShell Language

De Windows PowerShell-taal biedt scripting functies en methoden om aan te roepen opdrachten. Voor volledige scripting-informatie, Zie dat de Windows PowerShell-Naslaggids wordt geleverd met Windows PowerShell.

### <a name="extended-type-system-ets"></a>Uitgebreid typesysteem (ETS)

Windows PowerShell biedt toegang tot tal van andere objecten, zoals .NET en XML-objecten. Als u wilt weergeven van een algemene abstractielaag voor alle objecttypen gebruikt de shell als gevolg hiervan zijn uitgebreid typesysteem (ETS). De meeste ETS functionaliteit is transparant voor de gebruiker, maar het script of de .NET-ontwikkelaar gebruikt deze voor de volgende doeleinden:

- Een subset van de leden van specifieke objecten bekijken. Windows PowerShell biedt een 'aangepast' overzicht van enkele specifieke objecttypen.

- Leden toevoegen aan de bestaande objecten.

- Toegang tot objecten geserialiseerd.

- Schrijven aangepaste objecten.

  ETS gebruikt, kunt u nieuwe flexibele 'typen' die compatibel zijn met de Windows PowerShell-taal. Als u een .NET-ontwikkelaar bent, u kunt werken met objecten met dezelfde semantiek als de Windows PowerShell-taal voor het uitvoeren van scripts, bijvoorbeeld geldt, om te bepalen als een object resultaat zijn `true`.

  Zie voor meer informatie over ETS en hoe objecten worden gebruikt door Windows PowerShell, [Windows PowerShell-Object concepten](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).

## <a name="programming-for-windows-powershell"></a>Programmeren voor Windows PowerShell

Windows PowerShell definieert de code voor opdrachten, providers en andere programmamodules met behulp van .NET Framework. U bent niet beperkt tot het gebruik van Microsoft Visual Studio bij het maken van aangepaste modules voor Windows PowerShell, hoewel de voorbeelden in deze handleiding zijn genoemd om uit te voeren in dit hulpprogramma. U kunt een .NET-taal die ondersteuning biedt voor klassenovername van de en het gebruik van kenmerken. In sommige gevallen vereisen Windows PowerShell-APIs de programmeertaal te kunnen zijn voor toegang tot algemene typen.

## <a name="programmers-reference"></a>Naslaggids

Ter referentie bij het ontwikkelen voor Windows PowerShell, Zie de [Windows PowerShell SDK](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Aan de slag met behulp van Windows PowerShell

Zie voor meer informatie over het starten van de Windows PowerShell-shell gebruiken de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) geleverd met Windows PowerShell. Een document van de drie kolommen Naslaggids wordt ook een inleiding voor gebruik van de cmdlet geleverd.

## <a name="contents-of-this-guide"></a>Inhoud van deze handleiding

|Onderwerp|Definitie|
|-----------|----------------|
|[Over het maken van een Windows PowerShell-Provider](./how-to-create-a-windows-powershell-provider.md)|Deze sectie wordt beschreven hoe u een Windows PowerShell-provider voor Windows PowerShell maakt.|
|[Over het maken van een Windows PowerShell-hosttoepassing](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|Deze sectie wordt beschreven hoe u een hosttoepassing die wordt bewerkt een runspace schrijft en over het schrijven van een host-toepassing die een eigen aangepaste host implementeert.|
|[Over het maken van een PowerShell-module Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|Deze sectie beschrijft het maken van een module die wordt gebruikt voor het registreren van alle cmdlets en providers in een assembly en over het maken van een aangepaste module.|
|[Over het maken van een Console-Shell](./how-to-create-a-console-shell.md)|Deze sectie beschrijft het maken van een console-shell die kan niet worden uitgebreid.|
|[Windows PowerShell-concepten](./windows-powershell-concepts.md)|In deze sectie bevat algemene informatie waarmee u inzicht in de Windows PowerShell vanuit het oogpunt van een ontwikkelaar.|

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
