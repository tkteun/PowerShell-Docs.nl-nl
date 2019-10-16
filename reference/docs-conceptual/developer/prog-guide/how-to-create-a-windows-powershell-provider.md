---
title: Een Windows Power shell-provider maken | Microsoft Docs
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
ms.openlocfilehash: ffbf8028ba2b52e77d8e22c061baa9b8b67f6da3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357076"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Een Windows PowerShell-provider maken

In deze sectie wordt beschreven hoe u een Windows Power shell-provider bouwt. Een Windows Power shell-provider kan op twee manieren worden beschouwd. De provider vertegenwoordigt een set opgeslagen gegevens voor de gebruiker. De opgeslagen gegevens kunnen bijvoorbeeld de Internet Information Services (IIS) meta Base, het micro soft Windows-REGI ster, het Windows-Bestands systeem, Active Directory en de variabele en alias gegevens zijn opgeslagen door Windows Power shell.

Voor de ontwikkelaar is de Windows Power shell-provider de interface tussen de gebruiker en de gegevens waartoe de gebruiker toegang moet hebben. Vanuit dit perspectief ondersteunt elk type provider dat in deze sectie wordt beschreven, een set specifieke basis klassen en interfaces waarmee de Windows Power shell-runtime bepaalde cmdlets op een gemeen schappelijke manier kan weer geven aan de gebruiker.

## <a name="providers-provided-by-windows-powershell"></a>Providers van Windows Power shell

Windows Power shell biedt verschillende providers (zoals de bestandssysteem provider, register provider en alias provider) die worden gebruikt voor toegang tot bekende gegevens archieven. Voor meer informatie over de providers die worden geleverd door Windows Power shell, gebruikt u de volgende opdracht om de online-Help te openen:

**PS > Get-Help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Toegang tot de opgeslagen gegevens met behulp van Windows Power shell-paden

Windows Power shell-providers zijn toegankelijk voor de Windows Power shell-runtime en opdrachten programmatisch door middel van het gebruik van Windows Power shell-paden. Meestal worden deze paden gebruikt om rechtstreeks toegang te krijgen tot de gegevens via de provider. Sommige paden kunnen echter worden omgezet naar provider-interne paden waarmee een cmdlet niet-Windows Power shell-Api's (Application Programming Interfaces) kan gebruiken om toegang te krijgen tot de gegevens. Zie [How Windows Power shell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)(Engelstalig) voor meer informatie over de werking van Windows Power shell-providers in Windows Power shell.

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Provider-cmdlets weer geven met behulp van Windows Power Shell-stations

Een Windows Power shell-provider toont de ondersteunde cmdlets met behulp van virtuele Windows Power Shell-stations. Windows Power shell past de volgende regels toe voor een Windows Power Shell-station:

- De naam van een station kan een wille keurige alfanumerieke reeks zijn.

- Een station kan worden opgegeven op een wille keurig geldig punt in een pad, een ' root ' genoemd.

- Een station kan worden geïmplementeerd voor alle opgeslagen gegevens, niet alleen voor het bestands systeem.

- Elk station behoudt zijn eigen huidige werk locatie, waardoor de gebruiker context kan behouden bij het verschuiven van de stations.

## <a name="in-this-section"></a>In deze sectie

De volgende tabel bevat onderwerpen met code voorbeelden die op elkaar zijn gebaseerd. Met ingang van het tweede onderwerp kan de basis provider van Windows Power shell worden geïnitialiseerd en niet geïnitialiseerd door de Windows Power shell-runtime, het volgende onderwerp voegt functionaliteit toe voor het openen van de gegevens. het volgende onderwerp voegt functionaliteit toe voor het bewerken van de gegevens ( de items in de opgeslagen gegevens), enzovoort.

|Onderwerp|De definitie van|
|-----------|----------------|
|[Uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)|In dit onderwerp wordt beschreven wat u moet overwegen voordat u een Windows Power shell-provider implementeert. Het bevat een overzicht van de basis klassen en-interfaces van de Windows Power shell-provider die worden gebruikt.|
|[Een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md)|In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee de Windows Power shell-runtime de provider kan initialiseren en deinitialiseeren.|
|[Een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md)|In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee de gebruiker via een Windows Power Shell-station toegang kan krijgen tot een gegevens archief.|
|[Een Windows Power shell-item provider maken](./creating-a-windows-powershell-item-provider.md)|In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee de gebruiker de items in een gegevens archief kan bewerken.|
|[Een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md)|In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee de gebruiker op meerdere laag gegevens archieven kan werken.|
|[Een Windows Power shell-navigatie provider maken](./creating-a-windows-powershell-navigation-provider.md)|In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee de gebruiker op een hiërarchische manier door de items in een gegevens archief kan navigeren.|
|[Een Windows Power shell-inhouds provider maken](./creating-a-windows-powershell-content-provider.md)|In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee de gebruiker de inhoud van items in een gegevens archief kan bewerken.|
|[Een Windows Power shell-eigenschaps provider maken](./creating-a-windows-powershell-property-provider.md)|In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee de gebruiker de eigenschappen van items in een gegevens archief kan bewerken.|

## <a name="see-also"></a>Zie ook

[Hoe Windows Power shell werkt](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows Power shell SDK](../windows-powershell-reference.md)

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)
