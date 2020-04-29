---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: PowerShell-scripts
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "62058485"
---
# <a name="powershell"></a>PowerShell

Power shell is een op taken gebaseerde opdracht regel shell en script taal die is gebaseerd op .NET.
Power shell helpt systeem beheerders en hoofd gebruikers om snel taken te automatiseren die besturings systemen (Linux, macOS en Windows) en processen beheren.

Met Power shell-opdrachten kunt u computers beheren vanaf de opdracht regel. Met Power shell-providers kunt u toegang krijgen tot gegevens archieven, zoals het REGI ster en het certificaat archief, net zo eenvoudig als u toegang hebt tot het bestands systeem. Power shell bevat een uitgebreide expressie-parser en een volledig ontwikkelde script taal.

## <a name="powershell-is-open-source"></a>Power shell is open source

Power shell-basis bron code is nu beschikbaar in GitHub en open voor bijdragen van de community.
Zie [Power shell-bron op github](https://github.com/powershell/powershell).

U kunt beginnen met de bits die u nodig hebt om [Power shell](https://github.com/PowerShell/PowerShell#get-powershell)op te halen.
Of, misschien, met een korte rond leiding om aan de [slag](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)te gaan.

## <a name="powershell-design-goals"></a>Power shell-ontwerp doelen

Power shell is ontworpen voor het verbeteren van de opdracht regel-en script omgeving door langdurige problemen te elimineren en nieuwe functies toe te voegen.

### <a name="discoverability"></a>Detectie

Power Shell maakt het eenvoudig om de functies te ontdekken. Als u bijvoorbeeld een lijst met cmdlets wilt vinden waarmee Windows-Services worden weer gegeven en gewijzigd, typt u:

```powershell
Get-Command *-Service
```

Nadat u hebt gedetecteerd welke cmdlet een taak uitvoert, kunt u meer informatie over de cmdlet vinden met behulp `Get-Help` van de-cmdlet. Als u bijvoorbeeld Help over de `Get-Service` cmdlet wilt weer geven, typt u:

```powershell
Get-Help Get-Service
```

De meeste cmdlets retour neren objecten die kunnen worden gemanipuleerd en vervolgens weer gegeven als tekst voor weer gave. Als u de uitvoer van een cmdlet volledig wilt begrijpen, pipet u `Get-Member` de uitvoer naar de cmdlet. Met de volgende opdracht wordt bijvoorbeeld informatie weer gegeven over de leden van het object dat door `Get-Service` de cmdlet wordt uitgevoerd.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistentie

Het beheren van systemen kan een complexe taak zijn. Hulpprogram ma's die een consistente interface hebben, helpen de inherente complexiteit te beheren. Helaas zijn opdracht regel Programma's en COM-objecten (scriptable Component Object Model) niet bekend voor hun consistentie.

De consistentie van Power shell is een van de primaire activa. Als u bijvoorbeeld leert hoe u de `Sort-Object` cmdlet gebruikt, kunt u die kennis gebruiken om de uitvoer van een cmdlet te sorteren. U hoeft niet meer te weten te komen over de verschillende sorteer routines van elke cmdlet.

Daarnaast hoeven cmdlet-ontwikkel aars geen sorteer functies te ontwerpen voor hun cmdlets. Power shell biedt een Framework met de basis functies die consistentie afdwingt. Het Framework elimineert enkele keuzes die resteren voor de ontwikkelaar. Maar als resultaat wordt de ontwikkeling van cmdlets veel eenvoudiger.

### <a name="interactive-and-scripting-environments"></a>Interactieve en script omgevingen

De opdracht prompt van Windows biedt een interactieve shell met toegang tot opdracht regel Programma's en basis scripts. Windows Script Host (WSH) heeft script bare opdracht regel Programma's en COM Automation-objecten, maar biedt geen interactieve shell.

Power shell combineert een interactieve shell en een script omgeving. Power shell kan toegang krijgen tot opdracht regel Programma's, COM-objecten en .NET-klassen bibliotheken. Deze combi natie van functies breidt de mogelijkheden van de interactieve gebruiker, de script schrijver en de systeem beheerder uit.

### <a name="object-orientation"></a>Object stand

Power shell is gebaseerd op object niet tekst. De uitvoer van een opdracht is een object. U kunt het uitvoer object, via de pijp lijn, naar een andere opdracht verzenden als invoer.

Deze pijp lijn biedt een bekende interface voor personen die ervaring hebben met andere shells. Power shell breidt dit concept uit door objecten te verzenden in plaats van tekst.

### <a name="easy-transition-to-scripting"></a>Eenvoudige overgang naar scripts

Met de opdracht detectie van Power shell kunt u eenvoudig een migratie uitvoeren van opdrachten die interactief worden getypt om scripts te maken en uit te voeren. Met Power shell-transcripten en-geschiedenis kunt u eenvoudig opdrachten kopiëren naar een bestand voor gebruik als een script.
