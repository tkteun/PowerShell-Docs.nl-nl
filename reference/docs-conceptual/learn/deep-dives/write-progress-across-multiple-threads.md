---
title: Voortgang weer geven tijdens meerdere threads
description: Het gebruik van schrijf voortgang over meerdere threads met foreach-object-parallel
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: 640646992955116def23d16dd12c221857d37b68
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2020
ms.locfileid: "89410839"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a>Voortgang van het schrijven over meerdere threads met foreach parallel

Vanaf Power shell 7,0 is de mogelijkheid om in meerdere threads tegelijk te werken mogelijk te maken met behulp van de **parallelle** para meter in de [foreach-object-](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdlet. Het bewaken van de voortgang van deze threads kan echter een uitdaging zijn. Normaal gesp roken kunt u de voortgang van een proces bewaken met behulp van [schrijven](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).
Omdat Power shell echter gebruikmaakt van een afzonderlijke runs Pace voor elke thread wanneer **parallelle**verbinding wordt gebruikt, is het rapporteren van de voortgang aan de host niet zo meteen als normaal gebruik van `Write-Progress` .

## <a name="using-a-synced-hashtable-to-track-progress"></a>Een gesynchroniseerde hashtabel gebruiken om de voortgang bij te houden

Wanneer u de voortgang van meerdere threads schrijft, wordt het bijhouden lastig omdat bij het uitvoeren van parallelle processen in Power shell elk proces een eigen runs Pace heeft. U kunt dit doen door een [gesynchroniseerde hashtabel](/dotnet/api/system.collections.hashtable.synchronized)te gebruiken. Een gesynchroniseerde hashtabel is een veilige gegevens structuur die door meerdere threads tegelijk kan worden gewijzigd zonder dat er een fout optreedt.

### <a name="set-up"></a>Instellen

Een van de verzekeringen van deze benadering is dat er een, even complexe set wordt gebruikt om ervoor te zorgen dat alles zonder fouten wordt uitgevoerd.

```powershell
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)
```

In deze sectie worden drie verschillende gegevens structuren gemaakt, voor drie verschillende doel einden.

De `$dataSet` variabele bevat een matrix met hashtabellen die wordt gebruikt voor het coördineren van de volgende stappen zonder dat het risico wordt gewijzigd. Als een object verzameling wordt gewijzigd tijdens het sequentieel door de verzameling, genereert Power shell een fout. U moet de object verzameling in de lus gescheiden houden van de objecten die worden gewijzigd. De `Id` sleutel in elke hashtabel is de id voor een model proces. De `Wait` sleutel simuleert de werk belasting van elk getraceerd proces.

`$origin`Met de variabele wordt een geneste hashtabel opgeslagen waarbij elke sleutel een van de proces-id van de model is.
Vervolgens wordt deze gebruikt om de gesynchroniseerde hashtabel te laten ontdubbelt die is opgeslagen in de `$sync` variabele. De `$sync` variabele is verantwoordelijk voor het rapporteren van de voortgang terug naar de bovenliggende runs Pace, waarin de voortgang wordt weer gegeven.

### <a name="running-the-processes"></a>De processen uitvoeren

In deze sectie worden de processen met meerdere threads uitgevoerd en wordt een deel van de uitvoer gemaakt die wordt gebruikt om de voortgang weer te geven.

```powershell
$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}
```

De model processen worden verzonden naar `Foreach-Object` en gestart als taken. De **ThrottleLimit** is ingesteld op **3** om het uitvoeren van meerdere processen in een wachtrij te markeren. De taken worden opgeslagen in de `$job` variabele en kunnen ons laten weten wanneer alle processen later zijn voltooid.

Wanneer u de- `using:` instructie gebruikt om te verwijzen naar een bovenliggende bereik variabele in Power shell, kunt u geen expressies gebruiken om deze dynamisch te maken. Als u bijvoorbeeld probeert de `$process` variabele als volgt te maken, wordt er `$process = $using:sync.$($PSItem.id)` een fout melding weer gegeven waarin u geen expressies kunt gebruiken. Daarom maken we de `$syncCopy` variabele om de variabele te kunnen verwijzen en te wijzigen, `$sync` zonder het risico dat er een fout optreedt.

Vervolgens bouwen we een hashtabel op om de voortgang van het proces dat zich momenteel in de lus begeeft aan te geven met behulp `$process` van de variabele door te verwijzen naar de gesynchroniseerde hash-sleutels. De **activiteit** en de **status** sleutels worden gebruikt als parameter waarden voor `Write-Progress` om de status van een bepaald model proces weer te geven in de volgende sectie.

De `foreach` lus is een manier om te simuleren dat het proces werkt en dat wille keurig wordt gemaakt op basis van het `$dataSet` **wacht** kenmerk dat wordt ingesteld `Start-Sleep` met behulp van milliseconden. Hoe u de voortgang van uw proces berekent, kan variëren.

### <a name="displaying-the-progress-of-multiple-processes"></a>De voortgang van meerdere processen weer geven

Nu de Modeler-processen worden uitgevoerd als taken, kunnen we de voortgang van processen in het Power shell-venster gaan schrijven.

```powershell
while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

De `$job` variabele bevat de bovenliggende **taak** en heeft een onderliggende **taak** voor elk van de model processen. Terwijl een van de onderliggende taken nog steeds wordt uitgevoerd, blijft de **status** van de bovenliggende taak actief. Hierdoor kunnen we de lus gebruiken `while` om de voortgang van elk proces continu bij te werken totdat alle processen zijn voltooid.

In de lus while worden alle sleutels in de variabele door lopen `$sync` . Aangezien dit een gesynchroniseerde hashtabel is, wordt deze voortdurend bijgewerkt, maar kan deze nog steeds worden gebruikt zonder dat er fouten optreden.

Er wordt gecontroleerd of het proces dat wordt gerapporteerd, daad werkelijk wordt uitgevoerd met behulp van de- `IsNullOrEmpty()` methode. Als het proces niet is gestart, wordt de lus niet op de lijst gerapporteerd en gaat u verder met de volgende stap totdat het proces wordt gestart. Als het proces wordt gestart, wordt de hashtabel van de huidige sleutel gebruikt voor het splat van de para meters voor `Write-Progress` .

### <a name="full-example"></a>Volledig voor beeld

```powershell
# Example workload
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)

$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}

while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

## <a name="related-links"></a>Verwante koppelingen

- [about_Jobs](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [about_Scopes](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [about_Splatting](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
