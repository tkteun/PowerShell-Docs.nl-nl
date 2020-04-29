---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Huidige locatie beheren
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030200"
---
# <a name="managing-current-location"></a>Huidige locatie beheren

Bij het navigeren door map-systemen in Verkenner, hebt u meestal een specifieke werk locatie, namelijk de huidige geopende map. Items in de huidige map kunnen eenvoudig worden gemanipuleerd door erop te klikken. Voor opdracht regel interfaces zoals cmd. exe, wanneer u zich in dezelfde map bevindt als een bepaald bestand, kunt u deze openen door een relatief korte naam op te geven in plaats van het volledige pad naar het bestand op te geven. De huidige map wordt de werkmap genoemd.

Windows Power shell gebruikt de **locatie** van het zelfstandig naam woord om te verwijzen naar de werkmap en implementeert een groep cmdlets om uw locatie te onderzoeken en te manipuleren.

## <a name="getting-your-current-location-get-location"></a>Uw huidige locatie ophalen (Get-locatie)

Als u het pad van de huidige maplocatie wilt bepalen, voert u de opdracht **Get-location** in:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> De cmdlet Get-locatie is vergelijkbaar met de opdracht **pwd** in de bash-shell. De cmdlet Set-Location is vergelijkbaar met de **cd** -opdracht in cmd. exe.

## <a name="setting-your-current-location-set-location"></a>Uw huidige locatie instellen (Set-Location)

De opdracht **Get-locatie** wordt gebruikt met de opdracht **Set-Location** . Met de opdracht **Set-Location** kunt u de huidige maplocatie opgeven.

```powershell
Set-Location -Path C:\Windows
```

Nadat u de opdracht hebt ingevoerd, zult u merken dat u geen directe feedback krijgt over het effect van de opdracht. De meeste Windows Power shell-opdrachten die een actie uitvoeren, produceren weinig of geen uitvoer omdat de uitvoer niet altijd nuttig is. Als u wilt controleren of er een gewijzigde Directory is gewijzigd wanneer u de opdracht **Set-Location** opgeeft, neemt u de para meter **-PassThru** op wanneer u de opdracht **Set-Location** opgeeft:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

De para meter **-PassThru** kan worden gebruikt met veel set-opdrachten in Windows Power shell om informatie over het resultaat te retour neren in gevallen waarin er geen standaard uitvoer is.

U kunt paden ten opzichte van uw huidige locatie opgeven op dezelfde manier als in de meeste UNIX-en Windows-opdracht shells. In de standaard notatie voor relatieve paden, een punt (**.**) vertegenwoordigt de huidige map en een dubbele punt (**..**) vertegenwoordigt de bovenliggende map van uw huidige locatie.

Bijvoorbeeld, als u zich in de map **C:\\Windows** bevindt, een punt (**.**) vertegenwoordigt **c:\\Windows** en dubbele punten (**..**) vertegenwoordigen **c:**. U kunt van uw huidige locatie naar de hoofdmap van station C: overschakelen door het volgende te typen:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

Dezelfde techniek werkt op Windows Power Shell-stations die geen bestandssysteem stations zijn, zoals **HKLM:**. U kunt uw locatie in het REGI ster\\instellen op de HKLM-Software sleutel door het volgende te typen:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

U kunt de maplocatie vervolgens wijzigen in de bovenliggende map. Dit is de hoofdmap van het station Windows Power shell HKLM:, met behulp van een relatief pad:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

U kunt een set-locatie typen of een van de ingebouwde Windows Power shell-aliassen gebruiken voor de ingestelde locatie (cd, chdir, SL). Bijvoorbeeld:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Recente locaties opslaan en intrekken (push-locatie en pop-locatie)

Wanneer u locaties wijzigt, is het handig om bij te houden waar u bent geweest en te kunnen terugkeren naar uw vorige locatie. Met de cmdlet **Push-location** in Windows Power Shell maakt u een geordende geschiedenis (een ' stack ') van directory paden waar u zich bevindt, en kunt u de geschiedenis van mappaden door lopen met behulp van de complementaire cmdlet van de **pop-locatie** .

Windows Power shell wordt bijvoorbeeld doorgaans gestart in de basismap van de gebruiker.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> De woord *stack* heeft een speciale betekenis in veel programma-instellingen, waaronder .NET Framework. Net als bij een fysieke stack met items is het laatste item dat u op de stack plaatst het eerste item dat u de stack kunt afhalen. Het toevoegen van een item aan een stack is colloquially ' het item ' pushen ' naar de stack. Het ophalen van een item uit de stack is colloquially bekend als ' het opzeggen ' van het item van de stack.

Als u de huidige locatie naar de stack wilt pushen en vervolgens naar de map Local Settings wilt gaan, typt u:

```powershell
Push-Location -Path "Local Settings"
```

U kunt vervolgens de locatie van de lokale instellingen naar de stack pushen en naar de map Temp gaan door het volgende te typen:

```powershell
Push-Location -Path Temp
```

U kunt controleren of u de mappen hebt gewijzigd door de opdracht **Get-locatie** in te voeren:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

U kunt vervolgens weer terug naar de meest recent bezochte map door de opdracht **pop-locatie** in te voeren en de wijziging te controleren door de opdracht **Get-locatie** in te voeren:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Net als bij de cmdlet **Set-Location** kunt u de para meter **-PassThru** toevoegen wanneer u de **pop-locatie** -cmdlet invoert om de door u ingevoerde map weer te geven:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

U kunt ook de locatie-cmdlets met netwerk paden gebruiken. Als u een server met de naam FS01 hebt met een share met de naam Public, kunt u uw locatie wijzigen door het volgende te typen:

```powershell
Set-Location \\FS01\Public
```

of

```powershell
Push-Location \\FS01\Public
```

U kunt de opdrachten **Push-locatie** en **Stel locatie** gebruiken om de locatie te wijzigen in alle beschik bare stations. Als u bijvoorbeeld een lokaal CD-ROM-station hebt met stationsletter D dat een gegevens-CD bevat, kunt u de locatie wijzigen in het CD-station door de opdracht **Set-Location D:** in te voeren.

Als het station leeg is, wordt het volgende fout bericht weer gegeven:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Wanneer u een opdracht regel interface gebruikt, is het niet handig om bestanden Verkenner te gebruiken om de beschik bare fysieke stations te controleren. Daarnaast worden de alle Windows Power Shell-stations niet weer gegeven in de Verkenner. Windows Power shell biedt een reeks opdrachten voor het bewerken van Windows Power Shell-stations, en we zullen hierover over de volgende stappen gaan.
