---
title: Ondersteuning van jokertekens in de Cmdlet-Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059606"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Ondersteuning voor jokertekens in de cmdlet-parameters

U moet vaak ontwerpen van een cmdlet uit te voeren op basis van een groep resources in plaats van op basis van één resource. Bijvoorbeeld, moet een cmdlet mogelijk Zoek alle bestanden in een gegevensarchief met dezelfde naam of -extensie. U moet ondersteuning bieden voor jokertekens bij het ontwerpen van een cmdlet die wordt uitgevoerd op basis van een groep resources.

> [!NOTE]
> Met jokertekens wordt soms aangeduid als *bij globbing*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Windows PowerShell-Cmdlets die gebruikmaken van jokertekens

 Veel Windows PowerShell-cmdlets voor ondersteuning voor jokertekens voor hun parameterwaarden. Bijna elke cmdlet die heeft bijvoorbeeld een `Name` of `Path` parameter ondersteunt jokertekens voor deze parameters. (Hoewel de meeste cmdlets die beschikken over een `Path` parameter hebben ook een `LiteralPath` parameter die geen ondersteuning biedt voor jokertekens bevatten.) De volgende opdracht laat zien hoe een jokerteken wordt gebruikt voor het retourneren van alle cmdlets in de huidige sessie waarvan de naam van de Get-bewerking bevat.

 **PS > get-opdracht get -\***

## <a name="supported-wildcard-characters"></a>Ondersteunde jokertekens

Windows PowerShell ondersteunt de volgende jokertekens bevatten.

|Jokerteken|Description|Voorbeeld|Overeenkomsten|Komt niet overeen met|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Komt overeen met nul of meer tekens, vanaf de opgegeven positie|a*|Een, ag, Apple||
|?|Komt overeen met anycharacter op de opgegeven positie|? n|Een in het geval is, op|is uitgevoerd|
|[ ]|Komt overeen met een bereik met tekens|[a-l]ook|het adresboek, Cookeilanden, zoekt u naar|duurde|
|[ ]|Komt overeen met de opgegeven tekens|[bc]ook|boek, Cookeilanden|zoeken|

Bij het ontwerpen van cmdlets die ondersteuning bieden voor jokertekens bevatten, kunt u voor combinaties van jokertekens bevatten. Bijvoorbeeld, de volgende opdracht maakt gebruik van de `Get-ChildItem` cmdlet voor het ophalen van alle txt-bestanden die zijn opgenomen in de map c:\Techdocs en die beginnen met de letter 'a"via 'l'.

**get-childitem c:\techdocs\\[a-l]\*.txt**

De vorige opdracht maakt gebruik van het jokerteken bereik **[a-l]** om op te geven dat de naam moet beginnen met de tekens 'a"via 'l'. Vervolgens gebruikt de opdracht de * jokerteken als tijdelijke aanduiding voor alle tekens tussen de eerste letter van de bestandsnaam en de extensie .txt.

Het volgende voorbeeld wordt een bereik wildcard-patroon dat niet van toepassing op de letter "d", maar bevat alle andere letters uit 'a"via 'f'.

**get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Afhandeling van letterlijke tekens in jokertekenpatronen

Als het jokerteken-patroon dat u opgeeft letterlijke tekens bevat, gebruikt u het backtick-teken (') als een escape-teken. Wanneer u via een programma letterlijke tekens opgeeft, gebruikt u een enkele backtick. Wanneer u letterlijke tekens bij de opdrachtprompt opgeeft, gebruikt u twee graves. Het volgende patroon bevat bijvoorbeeld twee haakjes letterlijk moeten worden genomen.

' John Smith \`[*'] ' (opgegeven via een programma)

' John Smith \` \`[*\`'] ' (opgegeven bij de opdrachtprompt)

Dit patroon komt overeen met 'John Smith [Marketing]' of 'John Smith [ontwikkeling]'.

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet-uitvoer en jokertekens

Als parameters van de cmdlet jokertekens ondersteunt, genereert een cmdlet-bewerking gewoonlijk de matrixuitvoer van een. Soms kan zinvol het geen ter ondersteuning van een matrix uitgevoerd omdat de gebruiker kan slechts één item tegelijk gebruiken. Bijvoorbeeld, de `Set-Location` cmdlet biedt ondersteuning voor een matrix uitgevoerd omdat de gebruiker wordt ingesteld alleen één locatie. In dit geval de cmdlet nog steeds jokertekens worden ondersteund, maar het zorgt ervoor dat het probleem zou moeten op één locatie.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern klasse](/dotnet/api/system.management.automation.wildcardpattern)
