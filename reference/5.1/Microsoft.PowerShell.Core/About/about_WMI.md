---
description: Windows Management Instrumentation (WMI) gebruikt de Common Information Model (CIM) om systemen, toepassingen, netwerken, apparaten en andere beheer bare onderdelen van de moderne onderneming weer te geven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252731"
---
# <a name="about-wmi"></a>Over WMI

## <a name="short-description"></a>KORTE BESCHRIJVING

Windows Management Instrumentation (WMI) gebruikt de Common Information Model (CIM) om systemen, toepassingen, netwerken, apparaten en andere beheer bare onderdelen van de moderne onderneming weer te geven.

## <a name="long-description"></a>LANGE BESCHRIJVING

Windows Management Instrumentation (WMI) is de micro soft-implementatie van Web-Based Enter prise Management (WBEM), de industrie norm.

Klassieke WMI maakt gebruik van DCOM om te communiceren met apparaten in het netwerk om externe systemen te beheren. Windows Power Shell 3,0 introduceert een CIM-provider model dat gebruikmaakt van WinRM voor het verwijderen van de afhankelijkheid van DCOM. In dit CIM-provider model worden ook nieuwe WMI-provider-Api's gebruikt waarmee ontwikkel aars Windows Power shell-cmdlets kunnen schrijven in systeem eigen code (C \+ \+ ).

Verwar WMI-providers niet met Windows Power shell-providers. Voor veel Windows-onderdelen is een WMI-provider gekoppeld die de beheer mogelijkheden beschikbaar maakt. Als u WMI-providers wilt ophalen, voert u een WMI-query uit die exemplaren van de WMI-klasse __Provider, zoals de volgende query.

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a>DRIE ONDERDELEN VAN WMI

De volgende drie onderdelen van WMI communiceren met Windows Power shell: naam ruimten, providers en klassen.

WMI-naam ruimten worden WMI-providers en WMI-klassen in groepen verwante onderdelen ingedeeld. Op deze manier zijn ze vergelijkbaar met .NET Framework naam ruimten.
Naam ruimten zijn geen fysieke locaties, maar zijn meer dan logische data bases.
Alle WMI-naam ruimten zijn exemplaren van de klasse __Namespace systeem. De standaard-WMI-naam ruimte is root \/ CIMV2 (sinds micro soft Windows 2000). Als u Windows Power shell wilt gebruiken om WMI-naam ruimten in de huidige sessie op te halen, gebruikt u een opdracht met de volgende indeling.

```powershell
Get-WmiObject -Class __Namespace
```

Als u WMI-naam ruimten in andere naam ruimten wilt ophalen, gebruikt u de para meter naam ruimte om de locatie van de zoek opdracht te wijzigen. Met de volgende opdracht vindt u WMI-naam ruimten die zich in de hoofdmap/Cimv2/toepassings naam ruimte bevinden.

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

WMI-naam ruimten zijn hiërarchisch. Daarom moet het verkrijgen van een lijst met alle naam ruimten op een bepaald systeem een recursieve query starten, beginnend bij de hoofd naam ruimte.

WMI-providers bieden informatie over Windows-beheer bare objecten. Een provider haalt gegevens op uit een-onderdeel en geeft die gegevens door aan een beheer toepassing, zoals Windows Power shell. De meeste WMI-providers zijn dynamische providers. Dit betekent dat ze de gegevens dynamisch kunnen ophalen wanneer deze worden aangevraagd via de beheer toepassing.

## <a name="finding-wmi-classes"></a>WMI-KLASSEN ZOEKEN

In een standaard installatie van Windows 8 zijn er meer dan 1.100 WMI-klassen in de hoofdmap \/ Cimv2. Met dit aantal WMI-klassen wordt de uitdaging de juiste WMI-klasse voor het uitvoeren van een specifieke taak geïdentificeerd. Windows Power Shell 3,0 biedt twee manieren om WMI-klassen te vinden die betrekking hebben op een specifiek onderwerp.

Als u bijvoorbeeld WMI-klassen in de \\ WMI-naam ruimte root CIMV2 wilt vinden die gerelateerd zijn aan schijven, kunt u een query gebruiken zoals die hier wordt weer gegeven.

```powershell
Get-WmiObject -List *disk*
```

Als u WMI-klassen wilt vinden die gerelateerd zijn aan het geheugen, kunt u gebruikmaken van een query zoals die hier wordt weer gegeven.

```powershell
Get-WmiObject -List *memory*
```

De CIM-cmdlets bieden ook de mogelijkheid om WMI-klassen te detecteren. U kunt dit doen met behulp van de cmdlet Get-CIMClass. De opdracht die hier wordt weer gegeven, bevat WMI-klassen die betrekking hebben op video.

```powershell
Get-CimClass *video*
```

Tabblad uitbreiding werkt bij het wijzigen van WMI-naam ruimten en daarom kunnen subwmi-naam ruimten gemakkelijk worden gedetecteerd met behulp van een tabblad uitbreiding. In het volgende voor beeld geeft de cmdlet Get-CimClass WMI-klassen weer die zijn gerelateerd aan energie-instellingen.
Als u wilt zoeken, typt u de `root/CIMV2/` naam ruimte en drukt u enkele keren op de tab-toets totdat de energie naam ruimte wordt weer gegeven. Dit is de opdracht:

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
