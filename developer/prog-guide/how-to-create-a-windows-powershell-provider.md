---
title: Over het maken van een Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 286df63e75d6372cb41c974e60e79b02bd13686e
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429666"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Een Windows PowerShell-provider maken

In deze sectie wordt beschreven hoe u een Windows PowerShell-provider maken. Een Windows PowerShell-provider kan op twee manieren worden beschouwd. De provider geeft aan de gebruiker een set van opgeslagen gegevens. De opgeslagen gegevens kan bijvoorbeeld de Internet Information Services (IIS) Metabase, het Microsoft Windows-register, het bestandssysteem van Windows, Active Directory en de variabele en de alias-gegevens die zijn opgeslagen door de Windows PowerShell.

De Windows PowerShell-provider is voor de ontwikkelaar, de interface tussen de gebruiker en de gegevens die de gebruiker moet toegang hebben tot. Elk type provider dat wordt beschreven in deze sectie biedt ondersteuning voor een set specifieke basisklassen en interfaces waarmee de Windows PowerShell-runtime om beschikbaar te stellen bepaalde cmdlets voor de gebruiker in een veelgebruikte manier van dit perspectief.

## <a name="providers-provided-by-windows-powershell"></a>Providers geleverd door Windows PowerShell

Windows PowerShell biedt verschillende providers (zoals de bestandssysteem-provider, de registerprovider en de Alias-provider) die worden gebruikt voor toegang tot bekende gegevensarchieven. Gebruik de volgende opdracht uit voor toegang tot de online-Help voor meer informatie over de providers die is geleverd door Windows PowerShell:

**PS>get-help about_provider**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Toegang tot de opgeslagen gegevens met behulp van Windows PowerShell-paden

Windows PowerShell-providers zijn toegankelijk voor de Windows PowerShell-runtime en opdrachten via een programma door het gebruik van Windows PowerShell-paden. De meeste van de tijd worden deze paden gebruikt voor rechtstreekse toegang tot de gegevens via de provider. Sommige paden kunnen echter worden omgezet in provider-interne paden waardoor een cmdlet voor het gebruiken van Windows PowerShell application programming interfaces (API's) voor toegang tot de gegevens. Zie voor meer informatie over de werking van Windows PowerShell-providers in Windows PowerShell, [hoe Windows PowerShell werkt](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Blootstellen van Provider-Cmdlets met behulp van Windows PowerShell-stations

Een Windows PowerShell-provider bevat de ondersteunde cmdlets met behulp van virtuele schijven met een Windows PowerShell. Windows PowerShell is van toepassing de volgende regels voor een Windows PowerShell-station:

- De naam van een station mag elke alfanumerieke volgorde.

- Een schijf kan worden opgegeven op elk gewenst moment geldig op een pad, een "root" genoemd.

- Een schijf kan worden geïmplementeerd voor opgeslagen gegevens, niet alleen het bestandssysteem.

- Elke schijf blijft een eigen huidige werklocatie, zodat de gebruiker context behouden wanneer verplaatsen tussen schijven.

## <a name="in-this-section"></a>In deze sectie

De volgende tabel geeft een lijst met onderwerpen die bevatten codevoorbeelden die boven op elkaar gebouwd. Beginnen met het tweede onderwerp, de eenvoudige Windows PowerShell-provider kan worden geïnitialiseerd en niet-geïnitialiseerd door de Windows PowerShell-runtime, functionaliteit voor toegang tot de gegevens in het volgende onderwerp wordt toegevoegd, het volgende onderwerp wordt de functionaliteit voor het manipuleren van de gegevens (toegevoegd de items in de opgeslagen gegevens), enzovoort.

|Onderwerp|Definitie|
|-----------|----------------|
|[Het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)|In dit onderwerp wordt beschreven wat die u overwegen moet voordat u implementeert een Windows PowerShell-provider. Het bevat een overzicht van de basisklassen voor Windows PowerShell-provider en de interfaces die worden gebruikt.|
|[Het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md)|In dit onderwerp laat zien hoe een Windows PowerShell-provider waarmee de Windows PowerShell-runtime voor het initialiseren en initialisatie van de provider te maken.|
|[Het maken van een Provider van Windows PowerShell-station](./creating-a-windows-powershell-drive-provider.md)|In dit onderwerp laat zien hoe een Windows PowerShell-provider waarmee de gebruiker toegang tot een gegevensarchief via een Windows PowerShell-station te maken.|
|[Het maken van de Provider van een Windows PowerShell-Item](./creating-a-windows-powershell-item-provider.md)|In dit onderwerp laat zien hoe een Windows PowerShell-provider waarmee de gebruiker voor het bewerken van de items in een gegevensarchief te maken.|
|[Het maken van een Windows PowerShell-Container-Provider](./creating-a-windows-powershell-container-provider.md)|In dit onderwerp laat zien hoe een Windows PowerShell-provider waarmee de gebruiker om te werken op opgeslagen gelaagde gegevens maken.|
|[Het maken van een Windows PowerShell-Provider navigatie](./creating-a-windows-powershell-navigation-provider.md)|In dit onderwerp laat zien hoe een Windows PowerShell-provider waarmee de gebruiker om naar de items van een gegevensarchief in een hiërarchische manier wilt maken.|
|[Het maken van een Provider van Windows PowerShell-inhoud](./creating-a-windows-powershell-content-provider.md)|In dit onderwerp laat zien hoe een Windows PowerShell-provider waarmee de gebruiker voor het bewerken van de inhoud van de items in een gegevensarchief te maken.|
|[Het maken van een Windows PowerShell-eigenschap Provider](./creating-a-windows-powershell-property-provider.md)|In dit onderwerp laat zien hoe een Windows PowerShell-provider waarmee de gebruiker voor het bewerken van de eigenschappen van items in een gegevensarchief te maken.|

## <a name="see-also"></a>Zie ook

[How Windows PowerShell Works](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)