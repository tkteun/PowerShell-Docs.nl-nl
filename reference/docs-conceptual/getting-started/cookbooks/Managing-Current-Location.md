---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Huidige locatie beheren
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: 8d529bf4a85553b95a9cab2739016859662486f2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="managing-current-location"></a>Huidige locatie beheren

Wanneer de map systemen in Verkenner navigeren, hebt u meestal een specifieke locatie in de werkende - namelijk de momenteel geopende map. Items in de huidige map kunnen eenvoudig worden bewerkt door erop te klikken. Opdrachtregelinterfaces zoals Cmd.exe, wanneer u zich in dezelfde map als een bepaald bestand, u kunt toegang tot deze door een relatief korte naam geven, dan hoeft op te geven van het volledige pad naar het bestand. De huidige map heet de werkmap.

Windows PowerShell maakt gebruik van het zelfstandig naamwoord **locatie** om te verwijzen naar de werkmap en implementeert een serie van cmdlets kunt bekijken en bewerken van uw locatie.

### <a name="getting-your-current-location-get-location"></a>Ophalen van uw huidige locatie (Get-locatie)

Om te bepalen het pad van uw huidige directorylocatie, voer de **Get-Location** opdracht:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> De cmdlet Get-locatie is vergelijkbaar met de **pwd** opdracht in de BASH-shell. De cmdlet Set-Location is vergelijkbaar met de **cd** opdracht in Cmd.exe.

### <a name="setting-your-current-location-set-location"></a>Instellen van uw huidige locatie (Set-Location)

De **Get-Location** opdracht wordt gebruikt met de **Set-Location** opdracht. De **Set-Location** opdracht kunt u uw huidige directory-locatie opgeeft.

```powershell
Set-Location -Path C:\Windows
```

Nadat u de opdracht invoert, ziet u dat er geen directe feedback over het effect van de opdracht. De meeste Windows PowerShell-opdrachten die een actie uitvoeren er weinig of geen uitvoer geproduceerd, omdat de uitvoer niet altijd nuttig is. Om te controleren dat de wijziging in een geslaagde directory heeft plaatsgevonden wanneer u de **Set-Location** opdracht, bevatten de **- PassThru** parameter wanneer u de **Set-Location**opdracht:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

De **- PassThru** parameter kan worden gebruikt met veel Set-opdrachten in Windows PowerShell om informatie te retourneren over het resultaat in gevallen waarin er geen standaarduitvoer wordt.

U kunt paden ten opzichte van uw huidige locatie opgeven op dezelfde manier zoals u in de meeste UNIX- en Windows shells opdracht zou. In de standaardnotatie voor relatieve paden, een periode (**.**) Hiermee geeft u de huidige map en een dubbele punt (**...** ) staat voor de bovenliggende map van uw huidige locatie.

Bijvoorbeeld, als u zich in de **C:\\Windows** map, een periode (**.**) Hiermee geeft u **C:\\Windows** en dubbele punten (**...** ) vertegenwoordigen **C:**. U kunt vanuit uw huidige locatie naar de hoofdmap van station C: wijzigen door te typen:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Dezelfde techniek werkt op Windows PowerShell-stations die niet systeemstations bestand, zoals **HKLM:**. U kunt uw locatie instellen op de HKLM\\softwaresleutel in het register door te typen:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

U kunt de maplocatie vervolgens wijzigen naar de bovenliggende map, de hoofdmap van de Windows PowerShell-HKLM is:-station met behulp van een relatief pad zijn:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

U kunt Set-locatie typen of een van de ingebouwde Windows PowerShell-aliassen gebruiken voor Set-locatie (cd, chdir, sl). Bijvoorbeeld:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Recente locaties (Push-locatie en Pop-locatie) wilt opslaan en

Wanneer u locaties wijzigt, is het handig bijhouden waar u zijn en kunnen om terug te keren naar de vorige locatie. De **Push-Location** cmdlet in Windows PowerShell maakt een geordende geschiedenis (een ' stack') van mappaden waar u zijn, en u kunt stap opnieuw door de geschiedenis van directory-paden met behulp van de aanvullende  **Pop-locatie** cmdlet.

Bijvoorbeeld, Windows PowerShell wordt doorgaans begint in de basismap van de gebruiker.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Het woord *stack* heeft een speciale betekenis in vele programmeertalen-instellingen, inclusief .NET Framework. Zoals een fysieke-stack van items is het laatste item dat u in de stack het eerste item dat u uit de stack ophalen kunt. Item toevoegen aan een stack wordt term aangeduid als 'pushen' van het item in de stack te plaatsen. Binnenhalen van een item uit de stack wordt term aangeduid als 'verschijnen' van het item uit de stack.

Als u push van de huidige locatie in de stack te plaatsen en vervolgens verplaatsen naar de map lokale instellingen, typt u:

```powershell
Push-Location -Path "Local Settings"
```

U kunt vervolgens de locatie van de lokale instellingen in de stack push en en verplaatst naar de map Temp door te typen:

```powershell
Push-Location -Path Temp
```

U kunt controleren of u mappen gewijzigd door te voeren de **Get-Location** opdracht:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

U kunt vervolgens terug naar de meest recent bezochte map pop door te voeren de **Pop-locatie** opdracht in en controleer of de wijziging door te voeren de **Get-Location** opdracht:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Net als met de **locatie instellen** cmdlet, die u kunt opnemen de **- PassThru** parameter wanneer u de **Pop-locatie** cmdlet om de map die u hebt ingevoerd weer te geven:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

U kunt ook de locatie-cmdlets gebruiken met netwerkpaden. Als u een server met de naam FS01 met een share met de openbare naam hebt, kunt u uw locatie wijzigen door te geven

```powershell
Set-Location \\FS01\Public
```

of

```powershell
Push-Location \\FS01\Public
```

U kunt de **Push-Location** en **locatie instellen** opdrachten om te wijzigen van de locatie op elk station beschikbaar is. Bijvoorbeeld, als u een lokale cd-rom-station met stationsletter D een gegevens-CD bevat hebt, kunt u de locatie naar het cd-rom-station door te voeren de **Set-Location D:** opdracht.

Als de schijf leeg is, krijgt u het volgende foutbericht weergegeven:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Wanneer u een opdrachtregelinterface gebruikt, is het niet handig Verkenner gebruiken om de beschikbare fysieke stations te controleren. Bovendien zou Verkenner niet weergegeven. u de alle stations op de Windows PowerShell. Windows PowerShell biedt een reeks opdrachten voor het manipuleren van Windows PowerShell-stations en we zullen hebben over deze volgende.