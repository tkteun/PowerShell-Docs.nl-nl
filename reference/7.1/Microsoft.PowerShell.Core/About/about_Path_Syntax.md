---
description: Hierin worden de volledige en relatieve padnaam-indelingen in Power shell beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: 388ebb6a613f02f71ca630e13d20c9e5ade82d02
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252437"
---
# <a name="about-path-syntax"></a>Syntaxis van pad

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de volledige en relatieve padnaam-indelingen in Power shell beschreven.

## <a name="long-description"></a>LANGE BESCHRIJVING

Alle items in een gegevens opslag die toegankelijk zijn via een Power shell-provider, kunnen uniek worden aangeduid met hun padnamen. Een padnaam is een combi natie van de naam van het item, de container en de subcontainers waarin het item zich bevindt en het Power Shell-station waarmee de containers worden geopend.

In Power shell worden padnamen onderverdeeld in een van de volgende twee typen: volledig gekwalificeerd en relatief. Een volledig gekwalificeerde padnaam bestaat uit alle elementen die een pad vormen. Met de volgende syntaxis worden de elementen in een volledig gekwalificeerde padnaam weer gegeven:

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

De \<provider\> tijdelijke aanduiding verwijst naar de Power shell-provider waarmee u toegang hebt tot het gegevens archief. Zo kunt u met de File System provider toegang krijgen tot de bestanden en mappen op uw computer. Dit element van de syntaxis is optioneel en is nooit nodig omdat de namen van de stations uniek zijn voor alle providers.

De \<drive\> tijdelijke aanduiding verwijst naar het Power Shell-station dat wordt ondersteund door een bepaalde Power shell-provider. In het geval van de bestandssysteem provider wordt de Power shell-schijf toegewezen aan de Windows-stations die zijn geconfigureerd op uw systeem. Als uw systeem bijvoorbeeld een station en een C: station bevat, maakt de File System Provider dezelfde stations in Power shell.

Nadat u het station hebt opgegeven, moet u alle containers en subcontainers opgeven die het item bevatten. De containers moeten worden opgegeven in de hiërarchische volg orde waarin ze voor komen in de gegevens opslag. Met andere woorden, u moet beginnen met de bovenliggende container, vervolgens de onderliggende container in die bovenliggende container, enzovoort. Daarnaast moet elke container worden voorafgegaan door een back slash. (Houd er rekening mee dat Power shell voorwaartse slashes voor compatibiliteit met andere Power shells kan gebruiken.)

Nadat de container en de subcontainers zijn opgegeven, moet u de naam van het item opgeven, voorafgegaan door een back slash. De volledig gekwalificeerde padnaam voor het Shell.dll bestand in de map C: \\ Windows \\ System32 is bijvoorbeeld als volgt:

```powershell
C:\Windows\System32\Shell.dll
```

In dit geval is het station waarmee de containers worden geopend, het station C:, de container op het hoogste niveau Windows, is de subcontainer System32 (in de Windows-container) en wordt het item Shell.dll.

In sommige gevallen hoeft u geen volledig gekwalificeerde pad naam op te geven en kunt u in plaats daarvan een relatieve padnaam gebruiken. De naam van een relatief pad is gebaseerd op de huidige werk locatie. Met Power shell kunt u een item identificeren op basis van de locatie relatief ten opzichte van de huidige werk locatie. U kunt relatieve padnamen opgeven door speciale tekens te gebruiken. In de volgende tabel worden deze tekens beschreven en vindt u voor beelden van relatieve padnamen en volledige padnamen. De voor beelden in de tabel zijn gebaseerd op de huidige werkmap die is ingesteld op C:\Windows.

|Symbool|Beschrijving               |Relatief pad    |Volledig pad          |
|------|--------------------------|-----------------|-------------------|
|.     |Huidige locatie          |.\\ Opgehaald        |c: \\ Windows- \\ systeem|
|..    |Bovenliggend item van huidige locatie|..\\ Programma bestanden|c: \\ Program Files  |
|\     |Hoofdmap van huidige station     |\\Programma 's  |c: \\ Program Files  |
|      |location                  |                 |                   |
|geen|Geen speciale tekens     |Systeem           |c: \\ Windows- \\ systeem|

Wanneer u een padnaam in een opdracht gebruikt, voert u deze naam op dezelfde manier in als u een volledig gekwalificeerde padnaam of een relatief pad gebruikt. Stel bijvoorbeeld dat uw huidige werkmap C:\Windows. is Met de volgende Get-ChildItem opdracht worden alle items in de C:\Techdocs-map opgehaald:

```powershell
Get-ChildItem \techdocs
```

De back slash geeft aan dat de hoofdmap van het station van de huidige werk locatie moet worden gebruikt. De werkmap is C: \\ Windows, de hoofdmap van het station is station c:. Omdat de TechDocs-map zich in de hoofdmap bevindt, hoeft u alleen de back slash op te geven.

U kunt dezelfde resultaten krijgen met behulp van de volgende opdracht:

```powershell
Get-ChildItem c:\techdocs
```

Ongeacht of u een volledig gekwalificeerde padnaam of een relatief pad-naam gebruikt, is een padnaam belang rijk, omdat hiermee een item wordt gevonden, maar ook omdat het item op unieke wijze wordt geïdentificeerd, zelfs als dat item dezelfde naam heeft als een ander item in een andere container.

Stel bijvoorbeeld dat u twee bestanden hebt die elk een naam hebben Results.txt.
Het eerste bestand bevindt zich in een map met de naam C: \\ TechDocs \\ januari en het tweede bestand bevindt zich in een map met de naam c: \\ TechDocs \\ feb. Met de padnaam voor het eerste bestand (C: \\ TechDocs \\ Jan \\Results.txt) en de padnaam voor het tweede bestand (c: \\ TechDocs \\ februari \\Results.txt) kunt u duidelijk onderscheid maken tussen de twee bestanden.

## <a name="see-also"></a>ZIE OOK

[about_Locations](about_Locations.md)

