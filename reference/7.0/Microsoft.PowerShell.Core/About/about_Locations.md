---
description: Hierin wordt beschreven hoe u toegang krijgt tot items vanaf de werk locatie in Power shell.
Locale: en-US
ms.date: 03/15/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: 8129331353724f4c1c57019b01ac58c8b9fa5a03
ms.sourcegitcommit: 15f759ca68d17acecab46b52250298d4f2037c4d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103575624"
---
# <a name="about_locations"></a>about_Locations

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u toegang krijgt tot items vanaf de werk locatie in Power shell.

## <a name="long-description"></a>Lange beschrijving

De huidige werk locatie is de standaard locatie waarnaar opdrachten verwijzen.
Met andere woorden, dit is de locatie die Power shell gebruikt als u geen expliciet pad opgeeft naar het item of de locatie waarop de opdracht betrekking heeft.

> [!NOTE]
> Power shell ondersteunt meerdere runspaces per proces. Elke runs Pace heeft zijn eigen _huidige map_. Dit is niet hetzelfde als de huidige map van het proces: `[System.Environment]::CurrentDirectory` .

In de meeste gevallen is de huidige werk locatie een station dat toegankelijk is via de Power shell-bestands provider en, in sommige gevallen, een map op dat station.
U kunt bijvoorbeeld uw huidige werk locatie op de volgende locatie instellen:

```powershell
C:\Program Files\Windows PowerShell
```

Als gevolg hiervan worden alle opdrachten vanaf deze locatie verwerkt, tenzij er expliciet een ander pad wordt gegeven.

Power shell onderhoudt de huidige werk locatie voor elk station, zelfs wanneer het station niet het huidige station is. Hiermee hebt u toegang tot items vanaf de huidige werk locatie door alleen naar het station van een andere locatie te verwijzen.
Stel bijvoorbeeld dat uw huidige werk locatie is `C:\Windows` . Stel nu dat u de volgende opdracht gebruikt om de huidige werk locatie te wijzigen in HKLM: station:

```powershell
Set-Location HKLM:
```

Hoewel uw huidige locatie nu het register station is, kunt u nog steeds toegang krijgen tot items in de `C:\Windows` map met behulp van het station C:, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
Get-ChildItem C:
```

Power shell onthoudt dat uw huidige werk locatie voor dat station de Windows-map is, zodat er items uit die map worden opgehaald. De resultaten zijn hetzelfde als u de volgende opdracht hebt uitgevoerd:

```powershell
Get-ChildItem C:\Windows
```

In Power shell kunt u de opdracht Get-Location gebruiken om de huidige werk locatie te bepalen en kunt u de Set-Location opdracht gebruiken om de huidige werk locatie in te stellen. Met de volgende opdracht wordt bijvoorbeeld de huidige werk locatie ingesteld op de Windows-map van station C:.

```powershell
Set-Location c:\windows
```

Nadat u de huidige werk locatie hebt ingesteld, kunt u nog steeds toegang krijgen tot items vanaf andere stations door simpelweg de stationsnaam (gevolgd door een dubbele punt) op te nemen in de opdracht, zoals in het volgende voor beeld wordt weer gegeven:

```powershell
Get-ChildItem HKLM:\software
```

De voorbeeld opdracht haalt een lijst met items op in de software container van de HKEY lokale machine-component in het REGI ster.

Met Power shell kunt u ook speciale tekens gebruiken om de huidige werk locatie en de bovenliggende locatie ervan te vertegenwoordigen. Gebruik één punt om de huidige werk locatie weer te geven. Gebruik twee Peri Oden om het bovenliggende item van de huidige werk locatie weer te geven. In het volgende voor beeld wordt de submap System op de huidige werk locatie opgegeven:

```powershell
Get-ChildItem .\system
```

Als de huidige werk locatie is `C:\Windows` , retourneert deze opdracht een lijst met alle items in `C:\Windows\System` . Als u echter twee Peri Oden gebruikt, wordt de bovenliggende map van de huidige werkmap gebruikt, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
Get-ChildItem ..\"program files"
```

In dit geval behandelt Power shell de twee Peri Oden als station C:, zodat de opdracht alle items in de map ophaalt `C:\Program Files` .

Een pad dat begint met een slash identificeert een pad van de hoofdmap van het huidige station. Als uw huidige werk locatie bijvoorbeeld is `C:\Program Files\PowerShell` , is de hoofdmap van uw station C. Daarom worden met de volgende opdracht alle items in de `C:\Windows` map weer gegeven:

```powershell
Get-ChildItem \windows
```

Als u geen pad opgeeft dat begint met een stationsnaam, slash of periode bij het opgeven van de naam van een container of item, wordt ervan uitgegaan dat de container of het item zich op de huidige werk locatie bevindt. Als uw huidige werk locatie bijvoorbeeld is `C:\Windows` , retourneert de volgende opdracht alle items in de `C:\Windows\System` map:

```powershell
Get-ChildItem system
```

Als u een bestands naam opgeeft in plaats van een mapnaam, retourneert Power shell Details over dat bestand (ervan uitgaande dat het bestand zich op de huidige werk locatie bevindt).

## <a name="see-also"></a>Zie ook

[Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

[about_Providers](about_Providers.md)

[about_Path_Syntax](about_Path_Syntax.md)
