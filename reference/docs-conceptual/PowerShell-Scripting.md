---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: PowerShell-scripts
ms.openlocfilehash: 7de5a3f3149d8d464b34101d94a5f9430d9b0f23
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="powershell"></a>PowerShell

Gebaseerd op .NET Framework en is PowerShell een taakgebaseerde opdrachtregel-shell en scripttaal; het is speciaal ontworpen voor systeembeheerders en Hoofdgebruikers, het beheer van meerdere besturingssystemen (Linux, Mac OS-, Unix- en Windows) en de processen die betrekking hebben op de toepassingen die worden uitgevoerd op deze besturingssystemen snel te automatiseren.

## <a name="powershell-is-open-source"></a>PowerShell is open-source

PowerShell base broncode is nu beschikbaar in GitHub en open voor bijdragen vanuit de community. Zie [PowerShell bron op GitHub](https://github.com/powershell/powershell).

U kunt beginnen met de bits moet u op [ophalen PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Of wellicht, met een kort overzicht op [aan de slag](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>Ontwerpdoelstellingen van PowerShell
Windows PowerShell is ontworpen voor het verbeteren van de opdrachtregel en scripting-omgeving door langdurige problemen elimineren en het toevoegen van nieuwe functies.

### <a name="discoverability"></a>Detectie
Windows PowerShell kunt gemakkelijk detecteren van de functies. Bijvoorbeeld: voor een lijst met cmdlets die bekijken en wijzigen van de Windows-services, typt u:

```powershell
Get-Command *-Service
```

Nadat u ontdekte welke cmdlet voert een taak, kunt u meer informatie over de cmdlet met de cmdlet Get-Help. Typ bijvoorbeeld het volgende Help-informatie over de cmdlet Get-Service:

```powershell
Get-Help Get-Service
```
De meeste cmdlets verzenden objecten die kunnen worden bewerkt en vervolgens naar tekst voor de weergave wordt weergegeven. Voor een volledig begrip van de uitvoer van deze cmdlet, de uitvoer doorsluizen naar de cmdlet Get-lid. De volgende opdracht geeft bijvoorbeeld informatie over de leden van de objectuitvoer door de cmdlet Get-Service.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency
Het beheren van systemen kan een complexe datacenterbeheer en hulpprogramma's die u een consistente interface hebt helpen bij het bepalen van de intrinsieke complexiteit. Helaas hebben geen opdrachtregelprogramma's of scripts COM-objecten is bekend dat op de consistentie.

De consistentie van Windows PowerShell is een van haar primaire activa. Bijvoorbeeld, als u informatie over het gebruik van de cmdlet Sort-Object, kunt u deze kennis om te sorteren van de uitvoer van een cmdlet. U beschikt niet over voor meer informatie over de verschillende sorteren routines van elke cmdlet.

Bovendien hoeft cmdlet ontwikkelaars geen ontwerpen sorteren functies voor de cmdlets. Windows PowerShell krijgen ze een framework dat biedt de basisfuncties en zorgt ervoor dat ze consistent veel aspecten van de interface. Het framework gebruikmaking van de opties die doorgaans aan de ontwikkelaar worden geplaatst, maar in ruil maakt de ontwikkeling van cmdlets voor robuuste en eenvoudig te gebruiken veel eenvoudiger.

### <a name="interactive-and-scripting-environments"></a>Interactieve en Scripting-omgevingen
Windows PowerShell is een gecombineerde interactieve en scripting-omgeving die u toegang biedt tot de opdrachtregelprogramma's en COM-objecten en ook kunt u de kracht van .NET Framework Class Library (FCL) gebruiken.

Deze omgeving verbetert bij de Windows-opdrachtprompt, die een interactieve omgeving met meerdere opdrachtregelprogramma's biedt. Het verbetert tevens bij Windows Script Host (WSH)-scripts, waarmee u meerdere opdrachtregelprogramma's en COM automation-objecten gebruiken, maar bieden geen een interactieve omgeving.

Windows PowerShell breidt de mogelijkheid van de interactieve gebruiker en de schrijver van het script en maakt systeembeheer beter kan worden beheerd door een combinatie van toegang tot al deze functies.

### <a name="object-orientation"></a>Stand object
Hoewel u met Windows PowerShell werken door opdrachten te typen in de tekst, wordt Windows PowerShell is gebaseerd op objecten, niet naar tekst. De uitvoer van een opdracht is een object. U kunt de uitvoer-object aan een andere opdracht verzenden als invoer. Windows PowerShell biedt daardoor een vertrouwde interface naar mensen opgetreden met andere houders bij de introductie van een nieuw en krachtig opdrachtregelprogramma paradigma. Dit breidt het concept van het verzenden van gegevens tussen opdrachten doordat u voor het verzenden van objecten in plaats van tekst.

### <a name="easy-transition-to-scripting"></a>Eenvoudig overgang naar het uitvoeren van scripts
Windows PowerShell zorgt ervoor dat er eenvoudig overgang typen opdrachten interactief te maken en uitvoeren van scripts. U kunt de opdrachten typen bij de opdrachtprompt van Windows PowerShell voor het detecteren van de opdrachten die een taak uitvoeren. Vervolgens kunt u deze opdrachten in een van de tekst of een geschiedenis opslaan voordat u ze naar een bestand voor gebruik als een script kopieert.
