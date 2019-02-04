---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Huidige locatie beheren
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: d1ebc9507a45841e6d4d8219e45c002990e1328c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686507"
---
# <a name="managing-current-location"></a>Huidige locatie beheren

Bij het navigeren door systemen van de map in Verkenner, hebt u meestal een specifieke locatie in de werkmap - dat wil zeggen de huidige map openen. Items in de huidige map kunnen eenvoudig worden bewerkt door erop te klikken. Opdrachtregelinterfaces zoals Cmd.exe, wanneer u zich in dezelfde map als een bepaald bestand, u kunt toegang tot deze door een relatief korte naam op te geven in plaats van telkens opgeven van het volledige pad naar het bestand. De huidige map heet de werkmap.

Windows PowerShell maakt gebruik van het zelfstandig naamwoord **locatie** om te verwijzen naar de werkmap en een reeks cmdlets kunt bekijken en bewerken van uw locatie implementeert.

### <a name="getting-your-current-location-get-location"></a>Ophalen van uw huidige locatie (Get-locatie)

Om te bepalen het pad van uw huidige locatie van de directory, voer de **Get-locatie** opdracht:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> De cmdlet Get-locatie is vergelijkbaar met de **pwd** opdracht in de BASH-shell. De cmdlet Set-locatie is vergelijkbaar met de **cd** opdracht in Cmd.exe.

### <a name="setting-your-current-location-set-location"></a>Instellen van uw huidige locatie (locatie instellen)

De **Get-locatie** opdracht wordt gebruikt met de **locatie instellen** opdracht. De **locatie instellen** opdracht kunt u uw huidige maplocatie opgeven.

```powershell
Set-Location -Path C:\Windows
```

Nadat u de opdracht hebt ingevoerd, zult u merken dat u direct feedback over het effect van de opdracht geen ontvangt. De meeste Windows PowerShell-opdrachten die een actie uitvoert er weinig of geen uitvoer geproduceerd, omdat de uitvoer niet altijd handig is. Om te controleren dat de wijziging van een geslaagde directory is opgetreden bij het invoeren van de **locatie instellen** opdracht, bevatten de **- PassThru gebruikt** parameter bij het invoeren van de **locatie instellen**opdracht:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

De **- PassThru gebruikt** parameter kan worden gebruikt met veel Set-opdrachten in Windows PowerShell om te retourneren informatie over het resultaat in gevallen waarin er geen standaarduitvoer wordt.

U kunt paden ten opzichte van uw huidige locatie opgeven op dezelfde manier zoals u in de meeste UNIX- en Windows shells opdracht zou. In de standard-notatie voor relatieve paden, een periode (**.**) Hiermee geeft u de huidige map en een dubbele punt (**...** ) staat voor de bovenliggende map van uw huidige locatie.

Bijvoorbeeld, als u zich in de **C:\\Windows** map, een punt (**.**) Hiermee geeft u **C:\\Windows** en dubbele punten (**...** ) vertegenwoordigen **C:**. U kunt van uw huidige locatie naar de hoofdmap van station wijzigen door te typen:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Dezelfde techniek werkt op Windows PowerShell-stations die niet bestand systeemstations, zoals zijn **HKLM:**. U kunt uw locatie instellen op de HKLM\\softwaresleutel in het register door te typen:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Vervolgens kunt u de locatie van de map wijzigen naar de bovenliggende map, dit de hoofdmap van de Windows PowerShell-HKLM is: station, met behulp van een relatief pad:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

U kunt Set-locatie typen of gebruik een van de ingebouwde Windows PowerShell-aliassen voor Set-locatie (cd, chdir, sl). Bijvoorbeeld:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Opslaan en terughalen van recente locaties (Push-locatie en Pop-locatie)

Wanneer u locaties wijzigt, is het handig bijhouden waar u zijn en kunnen worden gebruikt om terug te keren naar de vorige locatie. De **Push-locatie** cmdlet in Windows PowerShell maakt u een geordende geschiedenis (een ' stack') van mappaden waar u zijn, en u kunt stap voor stap terug via de geschiedenis van directory-paden met behulp van de aanvullende  **Pop-locatie** cmdlet.

Bijvoorbeeld, Windows PowerShell wordt doorgaans begint in de basismap van de gebruiker.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Het woord *stack* heeft een speciale betekenis in veel programmeertalen instellingen, met inbegrip van .NET Framework. Als een fysieke stack van items is het laatste item dat u in de stack het eerste item dat u uit de stack ophalen kunt. Een item toe te voegen aan een stapel wordt term aangeduid als 'pushen' van het item in de stack. Binnenhalen van een item uit de stack wordt term aangeduid als 'Apparaatpagina' van het item uit de stack.

Als u de huidige locatie in de stack pushen en vervolgens verplaatsen naar de map lokale instellingen, typt u:

```powershell
Push-Location -Path "Local Settings"
```

U kunt vervolgens de locatie van de lokale instellingen in de stack pushen en verplaatsen naar de map Temp door te typen:

```powershell
Push-Location -Path Temp
```

U kunt controleren of u mappen gewijzigd door in te voeren de **Get-locatie** opdracht:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

U kunt vervolgens terug naar de meest recent bezochte map pop door in te voeren de **Pop-locatie** opdracht in en controleer of de wijziging door te voeren de **Get-locatie** opdracht:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Net als met de **locatie instellen** cmdlet, u kunt opnemen de **- PassThru gebruikt** parameter bij het invoeren van de **Pop-locatie** cmdlet om weer te geven van de map die u hebt ingevoerd:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

U kunt ook de locatie-cmdlets gebruiken met netwerkpaden. Als u een server met de naam FS01 met een bestandsshare met de openbare naam hebt, kunt u uw locatie wijzigen door te typen

```powershell
Set-Location \\FS01\Public
```

of

```powershell
Push-Location \\FS01\Public
```

U kunt de **Push-locatie** en **locatie instellen** opdrachten om te wijzigen van de locatie op elk beschikbaar station. Bijvoorbeeld, als u een lokale cd-rom-station met de stationsletter D met een gegevens-CD hebt, kunt u de locatie naar het cd-rom-station door in te voeren de **locatie instellen D:** opdracht.

Als de schijf leeg is, krijgt u de volgende strekking weergegeven:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Wanneer u een opdrachtregelinterface gebruikt, is het niet handig is dat de Bestandenverkenner gebruikt om de beschikbare fysieke stations te controleren. Ook toont Verkenner niet u de alle van de Windows PowerShell-stations. Windows PowerShell biedt een reeks opdrachten voor het manipuleren van Windows PowerShell-stations en we zullen praten over deze volgende.
