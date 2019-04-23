---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Items rechtstreeks bewerken
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 4caa7d2e0eecff9783556062d8503fe10e616fe5
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984371"
---
# <a name="manipulating-items-directly"></a>Items rechtstreeks bewerken

De elementen die u in Windows PowerShell-stations, zoals de bestanden en mappen in het bestand system-stations en de registersleutels in de Windows PowerShell-register-stations ziet, heten *items* in Windows PowerShell. De cmdlets voor het werken met hen item hebben het zelfstandig naamwoord **Item** in hun namen.

De uitvoer van de **Get-Command - zelfstandig naamwoord Item** -opdracht laat zien dat er negen item Windows PowerShell-cmdlets zijn.

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a>Het maken van nieuwe Items (Nieuw-Item)

Gebruik voor het maken van een nieuw item in het bestandssysteem de **New Item** cmdlet. Bevatten de **pad** parameter met het pad naar het item en de **ItemType** parameter met de waarde 'file' of 'directory'.

Bijvoorbeeld, een nieuwe map wilt maken met de naam ' New.Directory"in C:\\Temp-map, type:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Voor het maken van een bestand, wijzig de waarde van de **ItemType** parameter 'file'. Bijvoorbeeld, voor het maken van een bestand met de naam 'bestand1.txt' in de map New.Directory, typt u:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

U kunt dezelfde techniek gebruiken om een nieuwe registersleutel te maken. Er is in feite een registersleutel gemakkelijker te maken, omdat het enige itemtype in het Windows-register een sleutel is. (Artikel worden de registervermeldingen *eigenschappen*.) Bijvoorbeeld, voor het maken van een sleutel met de naam '_testen' in de subsleutel CurrentVersion, typt u:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Wanneer u een registerpad, zorg ervoor dat u de dubbele punt (**:**) station in de Windows PowerShell-namen, HKLM: en HKCU:. Zonder de dubbele punt, wordt de naam van de schijf in het pad niet herkend door Windows PowerShell.

## <a name="why-registry-values-are-not-items"></a>Registerwaarden zijn waarom geen Items

Wanneer u gebruikt de **Get-ChildItem** cmdlet voor het vinden van de items in een registersleutel, wordt nooit werkelijke registervermeldingen en hun waarden weergegeven.

Bijvoorbeeld, de registersleutel **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\uitvoeren** bevat meestal verschillende registervermeldingen die staan voor toepassingen die worden uitgevoerd wanneer het systeem wordt gestart.

Echter, wanneer u **Get-ChildItem** om te zoeken naar onderliggende items in de sleutel, wordt alle ziet u de **voor OptionalComponents** subsleutel van de sleutel:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Hoewel het normaal zou zijn handig is dat de registervermeldingen behandelen als items, kunt u een pad naar een register-item niet opgeven op een manier die ervoor zorgt dat deze uniek is. De notatie van het pad wordt geen onderscheid gemaakt tussen de subsleutel in het register met de naam **uitvoeren** en de **(standaard)** register-item in de **uitvoeren** subsleutel. Bovendien, omdat het register vermelding namen mogen de backslash-teken (**\\**), als registervermeldingen items, zou u kan niet de pad-notatie gebruiken om u te onderscheiden van een registervermelding met de naam  **Windows\\CurrentVersion\\uitvoeren** van de subsleutel die zich in het opgegeven pad.

## <a name="renaming-existing-items-rename-item"></a>Naam van bestaande Items (naam wijzigen-Item) wijzigen

Als u wilt de naam van een bestand of map wijzigen, gebruikt u de **Rename-Item** cmdlet. De volgende opdracht wijzigt de naam van de **Bestand1.txt** van het bestand in **fileOne.txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

De **Rename-Item** cmdlet kan de naam van een bestand of map wijzigen, maar het kan een item niet verplaatsen. De volgende opdracht mislukt, omdat deze probeert te verplaatsen van het bestand uit de map New.Directory naar de map Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>Items verplaatsen (Item verplaatsen)

Als u een bestand of map, gebruikt u de **Item verplaatsen** cmdlet.

Bijvoorbeeld, de volgende opdracht uit de map New.Directory verplaatst van de C:\\tijdelijke map in de hoofdmap van station. Om te controleren dat het item is verplaatst, bevatten de **PassThru** parameter van de **Item verplaatsen** cmdlet. Zonder **Passthru**, wordt de **Item verplaatsen** cmdlet geen resultaten weergegeven.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>Kopiëren van Items (Copy-Item)

Als u bekend met de kopieerbewerkingen in andere shells bent, vindt u mogelijk het gedrag van de **Copy-Item** cmdlet in Windows PowerShell om te worden ongebruikelijke. Wanneer u een item van de ene locatie naar een andere kopieert, worden Copy-Item de inhoud ervan niet standaard gekopieerd.

Bijvoorbeeld, als u kopieert de **New.Directory** Active directory van het station naar station C:\\tijdelijke map de opdracht is geslaagd, maar de bestanden in de map New.Directory zijn niet gekopieerd.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Als u de inhoud van weergeeft **C:\\temp\\New.Directory**, ziet u dat deze geen bestanden bevat:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Waarom niet de **Copy-Item** cmdlet Kopieer de inhoud naar de nieuwe locatie?

De **Copy-Item** cmdlet is ontworpen om te worden algemene; het is niet alleen voor het kopiëren van bestanden en mappen. Ook, zelfs bij het kopiëren van bestanden en mappen, kunt u alleen de container en niet op de items in het te kopiëren.

Alle van de inhoud van een map wilt kopiëren, bevatten de **Recurse** parameter van de **Copy-Item** cmdlet in de opdracht. Als u de map zonder de inhoud al hebt gekopieerd, voegt u toe de **Force** parameter, zodat u kunt het overschrijven van de lege map.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a>Verwijderen van Items (Item verwijderen)

Als u wilt verwijderen van bestanden en mappen, gebruikt u de **Remove-Item** cmdlet. Windows PowerShell-cmdlets, zoals **Remove-Item**, die aanzienlijk kunt maken, niet ongedaan worden gemaakt wijzigingen vaak om bevestiging wordt gevraagd bij het invoeren van de opdrachten. Bijvoorbeeld, als u probeert te verwijderen de **New.Directory** map, wordt u gevraagd om te bevestigen van de opdracht, omdat de map bestanden bevat:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Omdat **Ja** is het standaardantwoord, om te verwijderen van de map en de bestanden, drukt u op de **Enter** sleutel. U kunt de map zonder bevestiging verwijderen met de **-Recurse** parameter.

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>Uitvoeren van Items (Invoke-Item)

Windows PowerShell gebruikt de **Invoke-Item** cmdlet voor het uitvoeren van een standaardactie voor een bestand of map. Deze standaardactie wordt bepaald door de handler van de toepassing standaard in het register. het effect is hetzelfde als wanneer u dubbelklikt op het item in de Verkenner.

Stel bijvoorbeeld dat u de volgende opdracht uitvoeren:

```powershell
Invoke-Item C:\WINDOWS
```

Een Explorer-venster dat in C: bevindt zich\\Windows wordt weergegeven, net als de C: had dubbelklikken\\Windows-map.

Als u de **Boot.ini** bestand op een systeem voorafgaand aan Windows Vista:

```powershell
Invoke-Item C:\boot.ini
```

Als het type INI-bestand gekoppeld aan Kladblok is, is het boot.ini-bestand wordt geopend in Kladblok.
