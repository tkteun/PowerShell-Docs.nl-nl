---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: PowerShell-scripts
ms.openlocfilehash: 754805148dc815a12c5c77e4894fb598c6927f7e
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43133990"
---
# <a name="powershell"></a>PowerShell

PowerShell is een taakgebaseerde opdrachtregel-shell en scripttaal die is gebouwd op het .NET Framework.
PowerShell helpt beheerders en Hoofdgebruikers kunnen snel automatiseren van taken die besturingssystemen (Linux, macOS en Windows) en processen te beheren.

PowerShell-opdrachten kunnen u computers beheren vanaf de opdrachtregel. PowerShell-providers, kunt u toegang tot gegevensarchieven, zoals het register en het certificaatarchief, net zo gemakkelijk als u toegang het bestandssysteem tot. PowerShell bevat een parser voor uitgebreide expressies en een volledig ontwikkelde scripttaal.

## <a name="powershell-is-open-source"></a>PowerShell is open source

PowerShell-basis broncode is nu beschikbaar is in GitHub en geopend zodat u kunt bijdragen van de community.
Zie [PowerShell source op GitHub](https://github.com/powershell/powershell).

U kunt beginnen met de bits die u nodig hebt in [ophalen PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Of misschien met een korte Tour langs op [aan de slag](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>Ontwerpdoelstellingen van PowerShell

PowerShell is ontworpen voor het verbeteren van de opdrachtregel en scripting-omgeving door langdurige problemen en nieuwe functies toe te voegen.

### <a name="discoverability"></a>Zichtbaarheid

PowerShell kunt gemakkelijk detecteren van de functies ervan. Bijvoorbeeld, als u zoekt een lijst met cmdlets die bekijken en wijzigen van de Windows-services, typt u:

```powershell
Get-Command *-Service
```

Nadat u ontdekte welke cmdlet voert een taak, u kunt meer informatie over de cmdlet met behulp van de `Get-Help` cmdlet. Als u bijvoorbeeld op het Help-informatie weergeven over de `Get-Service` cmdlet, type:

```powershell
Get-Help Get-Service
```

De meeste cmdlets geretourneerde objecten die kunnen worden bewerkt en vervolgens weergegeven als tekst om weer te geven. Voor volledig inzicht in de uitvoer van een cmdlet, de uitvoer doorsluizen naar de `Get-Member` cmdlet. Bijvoorbeeld, de volgende opdracht geeft informatie weer over de leden van de uitvoer van object met de `Get-Service` cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency

Systemen beheren, kan een complexe taak zijn. Hulpprogramma's die een consistente interface Help-informatie voor het beheren van de inherente complexiteit. Helaas worden niet opdrachtregelprogramma's en scripts COM-objecten bekend zijn voor hun consistentie.

De consistentie van PowerShell is een van de primaire activa. Als u informatie over het gebruik bijvoorbeeld de `Sort-Object` cmdlet, kunt u deze kennis gebruiken om te sorteren van de uitvoer van een cmdlet. U hebt geen voor meer informatie over de verschillende sorteren routines van elke cmdlet.

Bovendien hoeft cmdlet ontwikkelaars te ontwerpen sorteren functies voor de cmdlets. PowerShell biedt een raamwerk met de belangrijkste functies die ervoor zorgt consistentie dat. Het framework wordt voorkomen dat bepaalde opties die voor de ontwikkelaar worden geplaatst. Maar hierna wordt de ontwikkeling van cmdlets veel eenvoudiger.

### <a name="interactive-and-scripting-environments"></a>Interactieve en scripting-omgevingen

De opdrachtprompt van Windows biedt een interactieve shell met toegang tot de opdrachtregelprogramma's en eenvoudige scripts worden uitgevoerd. Windows Script Host (WSH) scriptbare opdrachtregelprogramma's en COM automation-objecten heeft, maar biedt geen een interactieve shell.

PowerShell combineert een interactieve shell en scripts. PowerShell kan toegang krijgen tot de opdrachtregelprogramma's, COM-objecten en .NET-klassebibliotheken. Dankzij deze combinatie van functies breidt de mogelijkheden van de interactieve gebruiker schrijver van het script en de systeembeheerder.

### <a name="object-orientation"></a>Object-richting

PowerShell is gebaseerd op het object niet als tekst. De uitvoer van een opdracht is een object. U kunt de uitvoerobject via de pijplijn verzenden naar een andere opdracht als invoer.

Deze pijplijn biedt een vertrouwde-interface voor mensen met andere shells ervaren. Dit concept uitbreidt PowerShell door te sturen van objecten in plaats van tekst.

### <a name="easy-transition-to-scripting"></a>Eenvoudig overgang naar het uitvoeren van scripts

PowerShell van opdracht vindbaarheid maakt eenvoudig overgang van het typen van opdrachten interactief te maken en uitvoeren van scripts. Transcripten van PowerShell en de geschiedenis van eenvoudig opdrachten kopiëren naar een bestand voor gebruik als een script.
