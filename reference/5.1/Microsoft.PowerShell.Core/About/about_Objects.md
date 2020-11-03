---
description: Biedt essentiële informatie over objecten in Windows Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: 678eececc2625bf02a706e8ef61c83056443a12f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252783"
---
# <a name="about-objects"></a>Over objecten

## <a name="short-description"></a>Korte beschrijving

Biedt essentiële informatie over objecten in Windows Power shell.

## <a name="long-description"></a>Lange beschrijving

Elke actie die u in Windows Power shell uitvoert, vindt plaats in de context van de objecten. Wanneer gegevens worden verplaatst van de ene opdracht naar de volgende, wordt deze verplaatst als een of meer Identificeer bare objecten. Een object en vervolgens is een verzameling gegevens die een item vertegenwoordigt. Een object bestaat uit drie soorten gegevens: het object type, de bijbehorende methoden en de bijbehorende eigenschappen.

## <a name="types-methods-and-properties"></a>Typen, methoden en eigenschappen

Het object type geeft aan wat voor soort object het is. Een object dat een bestand vertegenwoordigt, is bijvoorbeeld een file info-object.

De object methoden zijn acties die u op het object kunt uitvoeren.
Zo hebben file info-objecten een CopyTo-methode die u kunt gebruiken om het bestand te kopiëren.

Object eigenschappen slaan informatie over het object op. Zo hebben file info-objecten bijvoorbeeld een eigenschap LastWriteTime die de datum en tijd opslaat waarop het bestand het laatst is geopend.

Wanneer u met objecten werkt, kunt u de methoden en eigenschappen van opdrachten gebruiken om actie te ondernemen en gegevens te beheren.

## <a name="objects-in-pipelines"></a>Objecten in pijp lijnen

Wanneer opdrachten worden gecombineerd in een pijp lijn, geven ze informatie aan elkaar door als objecten. Wanneer de eerste opdracht wordt uitgevoerd, verzendt het een of meer objecten omlaag in de pijp lijn naar de tweede opdracht. Met de tweede opdracht worden de objecten van de eerste opdracht ontvangen, worden de objecten verwerkt en worden nieuwe of gereviseerde objecten door gegeven aan de volgende opdracht in de pijp lijn.
Dit wordt voortgezet totdat alle opdrachten in de pijplijn worden uitgevoerd.

In het volgende voor beeld ziet u hoe objecten worden door gegeven van één opdracht aan de volgende:

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

De eerste opdracht `Get-ChildItem C:` retourneert een bestands-of Directory-object voor elk item in de hoofdmap van het bestands systeem. De bestands-en Directory objecten worden naar de tweede opdracht door gegeven aan de pijp lijn.

De tweede opdracht `where { $_.PsIsContainer -eq $false }` maakt gebruik van de eigenschap PsIsContainer van alle bestandssysteem objecten om alleen bestanden te selecteren die de waarde False ( \$ False) hebben in de eigenschap PsIsContainer. Mappen, die containers zijn en die dus de waarde True ( \$ waar) hebben in de eigenschap PsIsContainer, worden niet geselecteerd.

Met de tweede opdracht worden alleen de bestands objecten door gegeven aan de derde opdracht `Format-List` , waarin de bestands objecten in een lijst worden weer gegeven.

## <a name="see-also"></a>Zie ook

[about_Methods](about_Methods.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[Get-member](xref:Microsoft.PowerShell.Utility.Get-Member)
