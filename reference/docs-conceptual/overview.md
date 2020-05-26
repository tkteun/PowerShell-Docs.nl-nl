---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: Wat is Power shell?
ms.openlocfilehash: f9fcd536747d2063fe34c7104d0088bc70d39c1d
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808449"
---
# <a name="what-is-powershell"></a>Wat is Power shell?

Power shell is een framework voor taak automatisering en configuratie beheer, bestaande uit een opdracht regel shell en script taal. In tegens telling tot de meeste shells, die tekst accepteren en retour neren, is Power shell gebaseerd op de .NET common language runtime (CLR) en worden .NET-objecten geaccepteerd en geretourneerd. Deze fundamentele wijziging brengt volledig nieuwe hulpprogram ma's en methoden voor automatisering in.

## <a name="output-is-object-based"></a>Uitvoer is op objecten gebaseerd

In tegens telling tot traditionele opdracht regel interfaces, zijn Power shell-cmdlets ontworpen om objecten te verwerken.
Een object is gestructureerde informatie die meer is dan alleen de teken reeks die wordt weer gegeven op het scherm. De opdracht uitvoer bevat altijd extra informatie die u kunt gebruiken als u deze nodig hebt.

Als u hulpprogram ma's voor tekst verwerking hebt gebruikt voor het verwerken van gegevens in het verleden, zult u merken dat ze anders werken wanneer ze worden gebruikt in Power shell. In de meeste gevallen hebt u geen hulp middelen voor tekst verwerking nodig om specifieke gegevens op te halen. U hebt rechtstreeks toegang tot delen van de gegevens met behulp van de standaard syntaxis van Power shell-objecten.

## <a name="the-command-family-is-extensible"></a>De opdracht familie is uitbreidbaar

Interfaces zoals `cmd.exe` geen manier om u de ingebouwde opdrachtset direct uit te breiden. U kunt externe opdracht regel Programma's maken die worden uitgevoerd in `cmd.exe` . Deze externe hulpprogram ma's hebben echter geen services, zoals Help-integratie. `cmd.exe`niet automatisch weet dat deze externe hulpprogram ma's geldige opdrachten zijn.

De opdrachten in Power shell worden _cmdlets_genoemd. U kunt elke cmdlet afzonderlijk gebruiken, maar de kracht ervan wordt gerealiseerd wanneer u deze combineert om complexe taken uit te voeren. Net als bij veel shells krijgt u toegang tot het bestands systeem op de computer. Met Power shell- _providers_ kunt u toegang krijgen tot andere gegevens archieven, zoals het REGI ster en de certificaat archieven, net zo eenvoudig als u toegang hebt tot het bestands systeem.

U kunt uw eigen cmdlet-en functie modules maken met behulp van gecompileerde code of scripts. Met modules kunnen cmdlets en providers aan de shell worden toegevoegd. Power shell ondersteunt ook scripts die vergelijkbaar zijn met UNIX-shell scripts en `cmd.exe` batch-bestanden.

## <a name="support-for-command-aliases"></a>Biedt ondersteuning voor opdrachtaliassen

Power shell ondersteunt aliassen om te verwijzen naar opdrachten op alternatieve namen. Met aliasing kunnen gebruikers ervaring hebben met andere shells om algemene opdracht namen te gebruiken die ze al kennen voor vergelijk bare bewerkingen in Power shell.

Met aliasing wordt een nieuwe naam gekoppeld aan een andere opdracht. Power Shell heeft bijvoorbeeld een interne functie `Clear-Host` met de naam waarmee het uitvoer venster wordt gewist. U kunt ofwel de `cls` alias typen `clear` bij een opdracht prompt. Power shell interpreteert deze aliassen en voert de `Clear-Host` functie uit.

Deze functie helpt gebruikers bij het leren van Power shell. `cmd.exe`De meeste en UNIX-gebruikers hebben een grote aanbod opdrachten die gebruikers al op naam kennen. De Power shell-equivalenten kunnen geen identieke resultaten opleveren. De resultaten zijn echter bijna genoeg dat gebruikers kunnen werken zonder de naam van de Power shell-opdracht te weten. ' Spier geheugen ' is een andere belang rijke bron van frustraties bij het leren van een nieuwe opdracht shell. Als u jaren hebt gebruikt `cmd.exe` , kunt u reflexively de `cls` opdracht om het scherm te wissen. Zonder de alias voor `Clear-Host` ontvangt u een fout bericht en weet u niet wat u kunt doen om de uitvoer te wissen.

## <a name="powershell-handles-console-input-and-display"></a>Power shell verwerkt console-invoer en-weer gave

Wanneer u een opdracht typt, verwerkt Power shell de invoer van de opdracht regel altijd rechtstreeks. Power shell formatteert ook de uitvoer die op het scherm wordt weer gegeven. Dit verschil is aanzienlijk omdat het de vereiste werk van elke cmdlet vermindert. Zo zorgt u ervoor dat u altijd op dezelfde manier kunt werken met elke cmdlet. Cmdlet-ontwikkel aars hoeven geen code te schrijven voor het parseren van de opdracht regel argumenten of het format teren van de uitvoer.

Traditionele opdracht regel Programma's hebben hun eigen schema's voor het aanvragen en weer geven van Help. Sommige opdracht regel Programma's gebruiken `/?` voor het activeren van de Help-weer gave; anderen gebruiken `-?` , `/H` of zelfs `//` . De Help wordt in een GUI-venster weer gegeven, in plaats van in de-console weer te geven. Als u de verkeerde para meter gebruikt, kan het hulp programma mogelijk negeren wat u hebt getypt en de uitvoering van een taak automatisch starten.
Omdat Power shell de opdracht regel automatisch parseert en verwerkt, `-?` betekent de para meter altijd Help voor deze opdracht weer geven.

> [!NOTE]
> Als u een grafische toepassing uitvoert in Power shell, wordt het venster voor de toepassing geopend.
> Power shell is alleen van toepassing op het verwerken van de opdracht regel invoer die u opgeeft of de toepassings uitvoer die wordt geretourneerd naar het console venster. Dit heeft geen invloed op de manier waarop de toepassing intern werkt.

## <a name="powershell-has-a-pipeline"></a>Power Shell heeft een pijp lijn

Pijp lijnen zijn weliswaar het meest waardevolle concept dat wordt gebruikt in opdracht regel interfaces. Wanneer u correct gebruikt, kunnen pijp lijnen de moeite van het gebruik van complexe opdrachten verminderen en is het eenvoudiger om de werk stroom te zien. Elke opdracht in een pijp lijn geeft de uitvoer, item op item, door aan de volgende opdracht. Opdrachten hoeven niet meer dan één item tegelijk te verwerken. Het resultaat is een gereduceerd Resource verbruik en de mogelijkheid om de uitvoer direct te verkrijgen.

De notatie die wordt gebruikt voor pijp lijnen, is vergelijkbaar met de notatie die wordt gebruikt in andere schalen. In eerste instantie is het mogelijk niet duidelijk hoe pijp lijnen anders zijn in Power shell. Hoewel er tekst op het scherm wordt weer gegeven, Power shell pipes-objecten, geen tekst, tussen opdrachten.

Als u bijvoorbeeld de `Out-Host` cmdlet gebruikt om een pagina-op-pagina weer te geven van uitvoer van een andere opdracht, ziet de uitvoer er net zo uit als de normale tekst die op het scherm wordt weer gegeven, onderverdeeld in pagina's:

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

Paginering vermindert ook het CPU-gebruik omdat er `Out-Host` een volledige pagina kan worden weer gegeven. De cmdlets die voorafgaan aan de pijp lijn worden uitgevoerd, totdat de volgende pagina van uitvoer beschikbaar is.

### <a name="objects-in-the-pipeline"></a>Objecten in de pijp lijn

Wanneer u een cmdlet in Power shell uitvoert, wordt tekst uitvoer weer gegeven, omdat het nodig is om objecten als tekst in een console venster aan te duiden. In de tekst uitvoer worden mogelijk niet alle eigenschappen weer gegeven van het object dat wordt uitgevoerd.

Denk bijvoorbeeld aan de `Get-Location` cmdlet. De tekst uitvoer is een samen vatting van informatie, niet een volledige weer gave van het object dat wordt geretourneerd door `Get-Location` . De kop in de uitvoer wordt toegevoegd door het proces waarmee de gegevens voor het scherm worden opgemaakt.

```powershell
Get-Location
```

```Output
Path
----
C:\
```

Sluizen de uitvoer naar de `Get-Member` cmdlet geeft informatie weer over het object dat wordt geretourneerd door `Get-Location` .

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location`retourneert een **PathInfo** -object dat het huidige pad en andere informatie bevat.

## <a name="built-in-help-system"></a>Ingebouwd Help-systeem

Net als Unix `man` -pagina's bevat Power shell gedetailleerde Help-artikelen waarin Power shell-concepten en opdracht syntaxis worden uitgelegd. Gebruik de cmdlet [Get-Help][] om deze artikelen weer te geven bij de opdracht prompt of Bekijk de meest recent bijgewerkte versies van deze artikelen in de Power shell-documentatie online.

## <a name="next-steps"></a>Volgende stappen

Zie de sectie **Power shell** van deze site voor meer informatie over Power shell.

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
