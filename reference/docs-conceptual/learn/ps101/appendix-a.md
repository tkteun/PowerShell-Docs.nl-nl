---
title: Bijlage A-Help-syntaxis
description: In dit artikel wordt uitgelegd hoe u de syntaxis van een cmdlet die wordt weer gegeven door Get-Help, kunt lezen en begrijpen.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8e28f66c02370b098f63a0396ef8a724cf3a1bd
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436300"
---
# <a name="appendix-a---help-syntax"></a>Bijlage A-Help-syntaxis

In het volgende voor beeld wordt de sectie **syntaxis** van de Help voor de cmdlet weer gegeven `Get-EventLog` .

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

In dit voor beeld wordt alleen het relevante gedeelte van de Help weer gegeven.

De syntaxis bestaat voornamelijk uit verschillende sets openings-en afsluit haken ( `[]` ). Er zijn twee verschillende betekenissen, afhankelijk van hoe ze worden gebruikt. Alles tussen vier Kante haken is optioneel, tenzij ze een set lege vier Kante haken zijn `[]` . Lege vier Kante haken worden alleen weer gegeven na een gegevens type zoals `<string[]>` . Dit betekent dat bepaalde para meters meer dan één waarde van dat type kunnen accepteren.

De eerste para meter in de eerste para meter set van `Get-EventLog` is **LogName**. LogName wordt tussen vier Kante haken geplaatst, wat betekent dat het een positionele para meter is. Met andere woorden, waarbij u de naam van de para meter zelf opgeeft, is optioneel zolang deze is opgegeven op de juiste positie. De informatie in de punt haken ( `<>` ) na de parameter naam geeft aan dat er een enkele **teken reeks** waarde nodig is. De volledige parameter naam en het gegevens type worden niet tussen vier Kante haken geplaatst, dus de para meter **LogName** is vereist wanneer u deze para meter set gebruikt.

```powershell
Get-EventLog [-LogName] <String>
```

De tweede para meter is **InstanceId**. U ziet dat de parameter naam en het gegevens type beide volledig tussen vier Kante haken staan. Dit betekent dat de **InstanceId** -para meter optioneel is, niet verplicht. U ziet ook dat **InstanceId** wordt omgeven door een eigen set vier Kante haken. Net als bij de para meter **LogName** betekent dit dat de para meter positioneel is. Er is een laatste set vier Kante haakjes achter het gegevens type. Dit betekent dat het meer dan één waarde kan accepteren in de vorm van een matrix of een door komma's gescheiden lijst.

```
[[-InstanceId] <Int64[]>]
```

De tweede parameterset heeft een **lijst** parameter. Het is een switch parameter omdat er geen gegevens type is volgens de parameter naam. Wanneer de **lijst** parameter is opgegeven, is de waarde **True**. Wanneer deze niet is opgegeven, is de waarde **False**.

```
[-List]
```

De syntaxis gegevens voor een opdracht kunnen ook worden opgehaald met `Get-Command` behulp van de **syntaxis** parameter. Dit is een handige snelkoppeling die ik altijd gebruik. Zo kunt u snel zien hoe u een opdracht kunt gebruiken zonder dat u meerdere pagina's met Help-informatie hoeft te door lopen. Als ik meer informatie nodig heb, keer ik terug naar het gebruik van de werkelijke Help-inhoud.

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

Hoe meer u het Help-systeem in Power shell gebruikt, hoe eenvoudiger alle verschillende nuances worden onthouden. Voordat u het weet, wordt het gebruik van de tweede aard.
