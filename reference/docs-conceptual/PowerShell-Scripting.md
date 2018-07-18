---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: PowerShell-scripts
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094048"
---
# <a name="powershell"></a>PowerShell

Gebaseerd op .NET Framework en is PowerShell een taakgebaseerde opdrachtregel-shell en scripttaal; het is speciaal ontworpen voor beheerders en Hoofdgebruikers, voor het snel automatiseren van het beheer van meerdere besturingssystemen (Linux, Mac OS-, Unix- en Windows) en de processen met betrekking tot de toepassingen die op deze besturingssystemen worden uitgevoerd.

## <a name="powershell-is-open-source"></a>PowerShell is open-source

PowerShell-basis broncode is nu beschikbaar is in GitHub en geopend zodat u kunt bijdragen van de community.
Zie [PowerShell source op GitHub](https://github.com/powershell/powershell).

U kunt beginnen met de bits die u nodig hebt in [ophalen PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Of misschien met een korte Tour langs op [aan de slag](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>Ontwerpdoelstellingen van PowerShell
PowerShell is ontworpen voor het verbeteren van de opdrachtregel en scripting-omgeving door langdurige problemen en nieuwe functies toe te voegen.

### <a name="discoverability"></a>Zichtbaarheid
PowerShell kunt gemakkelijk detecteren van de functies ervan. Bijvoorbeeld, als u zoekt een lijst met cmdlets die bekijken en wijzigen van de Windows-services, typt u:

```powershell
Get-Command *-Service
```

Nadat u ontdekte welke cmdlet voert een taak, u kunt meer informatie over de cmdlet met behulp van de `Get-Help` cmdlet.
Als u bijvoorbeeld op het Help-informatie weergeven over de `Get-Service` cmdlet, type:

```powershell
Get-Help Get-Service
```
De meeste cmdlets introduceren objecten die kunnen worden bewerkt en vervolgens weergegeven in tekst om weer te geven.
Doorsluizen voor volledig inzicht in de uitvoer van deze cmdlet, de uitvoer naar de `Get-Member` cmdlet.
Bijvoorbeeld, de volgende opdracht geeft informatie weer over de leden van de uitvoer van object met de `Get-Service` cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency
Systemen beheren kan een complexe inspanning en hulpprogramma's die u een consistente interface hebt help voor het beheren van de inherente complexiteit.
Helaas hebben geen opdrachtregelprogramma's of scripts COM-objecten is bekend dat voor de consistentie.

De consistentie van PowerShell is een van de primaire activa.
Als u informatie over het gebruik bijvoorbeeld de `Sort-Object` cmdlet, kunt u deze kennis gebruiken om te sorteren van de uitvoer van een cmdlet.
U hoeft niet voor meer informatie over de verschillende sorteren routines van elke cmdlet.

Ontwikkelaars van de cmdlet geen bovendien ontwerpen sorteren functies voor de cmdlets.
PowerShell biedt hen een framework dat biedt de basisfuncties en zorgt ervoor dat ze consistent over veel aspecten van de interface.
Het framework wordt voorkomen dat enkele van de opties die doorgaans voor de ontwikkelaar worden geplaatst, maar hierna wordt de ontwikkeling van de cmdlets voor robuuste en eenvoudig te gebruiken veel eenvoudiger.

### <a name="interactive-and-scripting-environments"></a>Interactieve en Scripting-omgevingen
PowerShell is een gecombineerde interactief en scripting-omgeving die hebt u toegang tot de opdrachtregelprogramma's en COM-objecten en ook kunt u de kracht van de .NET Framework Class Library (FCL) gebruiken.

Deze omgeving worden bij de Windows-opdrachtprompt een interactieve omgeving met meerdere opdrachtregelprogramma's biedt verbeterd.
Het verbetert tevens bij Windows Script Host (WSH)-scripts, waarmee u kunnen meerdere opdrachtregelprogramma's en COM automation-objecten gebruiken, maar bieden een interactieve omgeving.

Door een combinatie van toegang tot al deze functies, PowerShell breidt de mogelijkheid van de interactieve gebruiker en schrijver van het script en systeembeheer gemakkelijker maakt.

### <a name="object-orientation"></a>Object-richting
Hoewel u met PowerShell werken door te typen van opdrachten in de tekst, moet PowerShell is gebaseerd op objecten, niet als tekst.
De uitvoer van een opdracht is een object.
U kunt het uitvoerobject op verzenden naar een andere opdracht als invoer.
Als gevolg hiervan bevat PowerShell een vertrouwde-interface voor mensen met andere shells er is tijdens de introductie van een nieuwe en krachtige opdrachtregelprogramma paradigma.
Dit breidt het concept van het verzenden van gegevens tussen opdrachten kunt u voor het verzenden van objecten, in plaats van tekst.

### <a name="easy-transition-to-scripting"></a>Eenvoudig overgang naar het uitvoeren van scripts
PowerShell maakt het eenvoudig om een overgang te typen opdrachten interactief te maken en uitvoeren van scripts.
U kunt de opdrachten kunt invoeren bij de PowerShell-opdrachtprompt voor het detecteren van de opdrachten die een taak uitvoeren.
U kunt vervolgens deze opdrachten in een transcript of een geschiedenis opslaan voordat u ze naar een bestand voor gebruik als een script kopieert.
