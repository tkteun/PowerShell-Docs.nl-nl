---
title: Hand leiding voor&#39;Windows Power shell-programmeurs | Microsoft Docs
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
ms.openlocfilehash: f8cbaf464345b8f2b693e72f3dbe781a47605b28
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417774"
---
# <a name="windows-powershell-programmer39s-guide"></a>Hand leiding voor&#39;Windows Power shell-programmeurs

Deze hand leiding voor programmeurs is gericht op ontwikkel aars die geïnteresseerd zijn in een beheer omgeving voor de opdracht regel voor systeem beheerders. Windows Power shell biedt een eenvoudige manier om beheer opdrachten te bouwen die .NET-objecten beschikbaar maken, terwijl Windows Power shell het meeste werk voor u kan doen.

Bij traditionele opdracht ontwikkeling moet u een para meter-parser schrijven, een parameter Binder, filters en alle andere functies die worden weer gegeven door elke opdracht. Windows Power shell biedt de volgende mogelijkheden waarmee u eenvoudig opdrachten kunt schrijven:

- Een krachtige Windows Power shell-runtime (Execution Engine) met een eigen parser en een mechanisme voor het automatisch binden van opdracht parameters.

- Hulpprogram ma's voor het opmaken en weer geven van opdracht resultaten met behulp van een opdracht regel-interpreter (CLI).

- Ondersteuning voor hoge niveaus van functionaliteit (via Windows Power shell-providers) waarmee u eenvoudig toegang hebt tot opgeslagen gegevens.

  U kunt gratis een .NET-object weer geven op basis van een uitgebreide opdracht of reeks opdrachten die een volledige opdracht regel ervaring bieden voor de beheerder.

  In de volgende sectie worden de belangrijkste Windows Power shell-concepten en-voor waarden besproken. Raadpleeg deze concepten en termen voordat u begint met het ontwikkelen.

## <a name="about-windows-powershell"></a>Over Windows PowerShell

Windows Power shell definieert verschillende soorten opdrachten die u in ontwikkeling kunt gebruiken. Deze opdrachten omvatten: functions, filters, scripts, aliassen en uitvoer bare bestanden (toepassingen). Het hoofd opdracht type dat in deze hand leiding wordt besproken, is een eenvoudige, kleine opdracht met de naam ' cmdlet '. Windows Power Shell levert een set cmdlets en biedt volledige ondersteuning voor het aanpassen van cmdlets voor uw omgeving. De Windows Power shell-runtime verwerkt alle opdracht typen net zoals cmdlets, met behulp van pijp lijnen.

Naast de opdrachten ondersteunt Windows Power shell diverse aanpas bare Windows Power shell-providers die beschik bare specifieke sets van cmdlets maken. De shell werkt in de Windows Power shell-opgegeven host-toepassing (Windows Power shell. exe), maar is ook gelijk toegankelijk vanuit een aangepaste Host-toepassing die u kunt ontwikkelen om te voldoen aan specifieke vereisten. Zie [How Windows Power shell](/previous-versions//ms714658(v=vs.85))(Engelstalig) voor meer informatie.

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell-Cmdlets

Een cmdlet is een licht gewicht opdracht die wordt gebruikt in de Windows Power shell-omgeving. De Windows Power shell-runtime roept deze cmdlets aan in de context van automatiserings scripts die op de opdracht regel worden gegeven en de Windows Power shell-runtime roept deze ook programmatisch via Windows Power shell-Api's aan.

Zie [een Windows Power shell-cmdlet schrijven](../cmdlet/writing-a-windows-powershell-cmdlet.md)voor meer informatie over cmdlets.

### <a name="windows-powershell-providers"></a>Windows Power shell-providers

Bij het uitvoeren van beheer taken moet de gebruiker mogelijk gegevens onderzoeken die zijn opgeslagen in een gegevens archief (bijvoorbeeld het bestands systeem, het Windows-REGI ster of een certificaat archief). Windows Power shell definieert een module met de naam een Windows Power shell-provider die kan worden gebruikt voor toegang tot een specifiek gegevens archief, zoals het Windows-REGI ster, om deze bewerkingen eenvoudiger te maken. Elke provider ondersteunt een set gerelateerde cmdlets om de gebruiker een symmetrische weer gave van de gegevens in de Store te geven.

Windows Power shell biedt verschillende standaard providers van Windows Power shell. De register provider ondersteunt bijvoorbeeld navigatie en manipulatie van het Windows-REGI ster. Register sleutels worden weer gegeven als items en register waarden worden beschouwd als eigenschappen.

Als u een gegevens archief beschikbaar maakt waartoe de gebruiker toegang moet hebben, moet u mogelijk uw eigen Windows Power shell-provider schrijven, zoals wordt beschreven in [Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md). Zie [How Windows Power shell Works](/previous-versions//ms714658(v=vs.85))(Engelstalig) voor meer informatie AboutWindows Power shell-providers.

### <a name="host-application"></a>Hosttoepassing

Windows Power shell bevat de standaard toepassing Power shell. exe van de host, een console toepassing die samenwerkt met de gebruiker en de Windows Power shell-runtime host met behulp van een console venster.

U hoeft slechts zelden uw eigen hosttoepassing te schrijven voor Windows Power shell, hoewel aanpassing wordt ondersteund. Eén geval waarin u mogelijk uw eigen toepassing nodig hebt, is wanneer u een interface hebt die uitgebreid is dan de interface van de standaardhost-toepassing. Mogelijk wilt u ook een aangepaste toepassing maken wanneer u de grafische gebruikers interface baseert op de opdracht regel. Zie [How to Create a Windows Power shell host Application](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application)(Engelstalig) voor meer informatie.

### <a name="windows-powershell-runtime"></a>Windows Power shell-runtime

De Windows Power shell-runtime is de uitvoerings engine die opdracht verwerking implementeert. Het bevat de klassen die de interface bieden tussen de hosttoepassing en Windows Power shell-opdrachten en-providers. De Windows Power shell-runtime wordt geïmplementeerd als een runs Pace-object voor de huidige Windows Power shell-sessie. Dit is de operationele omgeving waarin de shell en de opdrachten worden uitgevoerd. Zie [How Windows Power shell](/previous-versions//ms714658(v=vs.85))(Engelstalig) voor operationele informatie.

### <a name="windows-powershell-language"></a>Windows Power shell-taal

De Windows Power shell-taal biedt script functies en mechanismen voor het aanroepen van opdrachten. Zie de Windows Power shell-taal referentie die wordt geleverd bij Windows Power shell voor meer informatie over het uitvoeren van scripts.

### <a name="extended-type-system-ets"></a>Uitgebreid type systeem (ETS)

Windows Power shell biedt toegang tot verschillende objecten, zoals .NET en XML-objecten. Als gevolg hiervan wordt een gemeen schappelijke samen vatting voor alle object typen weer gegeven, maar wordt het uitgebreide type systeem (ETS) gebruikt. De meeste ETS-functionaliteit is transparant voor de gebruiker, maar het script of .NET-ontwikkel aars gebruiken deze voor de volgende doel einden:

- Een subset van de leden van specifieke objecten weer geven. Windows Power shell biedt een ' aangepaste ' weer gave van verschillende specifieke object typen.

- Leden aan bestaande objecten toevoegen.

- Toegang tot geserialiseerde objecten.

- Aangepaste objecten schrijven.

  Met behulp van ETS kunt u flexibele nieuwe typen maken die compatibel zijn met de Windows Power shell-taal. Als u een .NET-ontwikkelaar bent, kunt u met objecten werken met dezelfde semantiek als de Windows Power shell-taal van toepassing op scripting, bijvoorbeeld om te bepalen of een object `true`.

  Zie [Windows Power shell-object concepten](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6)voor meer informatie over ETS en hoe Windows Power shell objecten gebruikt.

## <a name="programming-for-windows-powershell"></a>Program meren voor Windows Power shell

Windows Power shell definieert de code voor opdrachten, providers en andere programma modules met behulp van de .NET Framework. U bent niet beperkt tot het gebruik van micro soft Visual Studio voor het maken van aangepaste modules voor Windows Power shell, hoewel de voor beelden in deze hand leiding bekend zijn om te worden uitgevoerd in dit hulp programma. U kunt elke .NET-taal gebruiken die de overname van klassen en het gebruik van kenmerken ondersteunt. In sommige gevallen vereist de programmeer taal voor Windows Power shell-Api's om toegang te kunnen krijgen tot generieke typen.

## <a name="programmers-reference"></a>Naslag informatie voor programmeurs

Zie de [Windows Power shell SDK](../windows-powershell-reference.md)voor naslag informatie over het ontwikkelen van Windows Power shell.

## <a name="getting-started-using-windows-powershell"></a>Aan de slag met Windows Power shell

Zie voor meer informatie over het gebruik van de Windows Power shell-shell [aan de slag met Windows Power shell die is](/powershell/scripting/getting-started/getting-started-with-windows-powershell) geleverd bij Windows Power shell. Een snel naslag document voor een drie puntige vouw wordt ook geleverd als een primer voor het gebruik van de cmdlet.

## <a name="contents-of-this-guide"></a>Inhoud van deze hand leiding

|Onderwerp|De definitie van|
|-----------|----------------|
|[Een Windows Power shell-provider maken](./how-to-create-a-windows-powershell-provider.md)|In deze sectie wordt beschreven hoe u een Windows Power shell-provider voor Windows Power shell bouwt.|
|[Een Windows Power shell-hosttoepassing maken](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application)|In deze sectie wordt beschreven hoe u een hosttoepassing schrijft die een runs Pace bewerkt en hoe u een hosttoepassing schrijft die zijn eigen aangepaste host implementeert.|
|[Een Windows Power shell-module maken](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|In deze sectie wordt beschreven hoe u een module maakt die wordt gebruikt voor het registreren van alle cmdlets en providers in een assembly en het maken van een aangepaste module.|
|[Een console shell maken](./how-to-create-a-console-shell.md)|In deze sectie wordt beschreven hoe u een console Shell maakt die niet uitbreidbaar is.|
|[Windows Power shell-concepten](./windows-powershell-concepts.md)|Deze sectie bevat conceptuele informatie waarmee u inzicht krijgt in Windows Power shell vanuit het oogpunt van een ontwikkelaar.|

## <a name="see-also"></a>Zie ook

[Windows Power shell SDK](../windows-powershell-reference.md)
