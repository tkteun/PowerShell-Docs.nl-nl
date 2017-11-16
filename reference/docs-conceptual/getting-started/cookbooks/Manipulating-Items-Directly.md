---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Rechtstreeks bewerken van Items
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: d9aa95dcb0da2e8203cbe32d64b95bf33d914166
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="manipulating-items-directly"></a>Rechtstreeks bewerken van Items
De elementen die u in Windows PowerShell-stations, zoals de bestanden en mappen in het bestand systeemstations en de sleutels in de Windows PowerShell register-stations ziet worden genoemd *items* in Windows PowerShell. De cmdlets voor het werken met hen item hebben het zelfstandig naamwoord **Item** in hun naam.

De uitvoer van de **Get-Command - zelfstandig naamwoord Item** opdracht geeft aan dat negen item Windows PowerShell-cmdlets.

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

### <a name="creating-new-items-new-item"></a>Maken van nieuwe Items (Nieuw Item)
Gebruik voor het maken van een nieuw item in het bestandssysteem de **New Item** cmdlet. Bevatten de **pad** parameter met het pad naar het item en de **ItemType** parameter met de waarde 'file' of 'map'.

Bijvoorbeeld, om een nieuwe map maken met de naam ' New.Directory"in C:\\Temp-directory, type:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Voor het maken van een bestand, wijzig de waarde van de **ItemType** parameter 'file'. Typ bijvoorbeeld de volgende opdracht voor het maken van een bestand met de naam 'bestand1.txt' in de map New.Directory:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

U kunt dezelfde techniek gebruiken voor het maken van een nieuwe registersleutel. Er is in feite een registersleutel gemakkelijker te maken, omdat het enige itemtype in het Windows-register een sleutel is. (Registervermeldingen zijn item *eigenschappen*.) Typ bijvoorbeeld de volgende opdracht voor het maken van een sleutel met de naam '_Test' in de subsleutel CurrentVersion:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Wanneer een registerpad te typen, zorg ervoor dat u de dubbele punt (**:**) in de Windows PowerShell-station namen, HKLM: en HKCU:. Zonder de dubbele punt, wordt de stationsnaam van het in het pad niet herkend door Windows PowerShell.

### <a name="why-registry-values-are-not-items"></a>Waarom registerwaarden niet kunnen worden Items
Wanneer u gebruikt de **Get-ChildItem** cmdlet vinden van de items in een registersleutel, wordt nooit werkelijke registervermeldingen of de waarden weergegeven.

Bijvoorbeeld, de registersleutel **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\uitvoeren** bevat meestal verschillende registervermeldingen die staan voor toepassingen die worden uitgevoerd wanneer het systeem wordt gestart.

Wanneer u echter gebruiken **Get-ChildItem** onderliggende items in de sleutel zoekt, ziet u alleen de **voor OptionalComponents** subsleutels van de sleutel:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Hoewel het normaal zou handig om te behandelen registervermeldingen als items zijn, kunt u een pad naar een register-item kan niet opgeven op een manier die ervoor zorgt dat deze uniek is. De notatie van het pad wordt geen onderscheid gemaakt tussen de registersubsleutel met de naam **uitvoeren** en de **(standaard)** register-item in de **uitvoeren** subsleutel. Bovendien, omdat de namen van vermeldingen register mag het backslash-teken (**\\**), als regsitry vermeldingen items, zou u kan de notatie van het pad niet gebruiken om te onderscheiden van een registervermelding met de naam  **Windows\\CurrentVersion\\uitvoeren** uit de subsleutel dat in dat pad bevindt zich.

### <a name="renaming-existing-items-rename-item"></a>Naam van bestaande Items (Rename-Item) wijzigen
De naam van een bestand of map wijzigen, gebruikt u de **Rename-Item** cmdlet. De volgende opdracht wordt de naam van de **Bestand1.txt** van het bestand in **fileOne.txt**.

```
PS> Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

De **Rename-Item** cmdlet kan de naam van een bestand of map wijzigen, maar het kan een item niet verplaatsen. De volgende opdracht mislukt, omdat deze probeert het bestand van de map New.Directory verplaatsen naar de map Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a>Verplaatsen van Items (Item verplaatsen)
Als u een bestand of map, gebruikt u de **Item verplaatsen** cmdlet.

Bijvoorbeeld de map New.Directory in de volgende opdracht wordt verplaatst van de C:\\tijdelijke map naar de hoofdmap van station C:. Om te verifiëren dat het item is verplaatst, omvatten de **PassThru** parameter van de **Item verplaatsen** cmdlet. Zonder **Passthru**, wordt de **Item verplaatsen** cmdlet geeft geen resultaten weer.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a>Kopiëren van Items (Copy-Item)
Als u bekend met de kopieerbewerkingen in andere houders bent, vindt u mogelijk het gedrag van de **Copy-Item** cmdlet in Windows PowerShell om te worden ongebruikelijke. Wanneer u een item van de ene locatie naar een andere kopieert, kopieert Copy-Item niet de inhoud ervan standaard.

Bijvoorbeeld, als u kopieert de **New.Directory** map uit het station C: naar station C:\\tijdelijke map, de opdracht is geslaagd, maar de bestanden in de map New.Directory zijn niet gekopieerd.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Als u de inhoud van weergeven **C:\\temp\\New.Directory**, vindt u bevat geen bestanden:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Waarom heeft niet de **Copy-Item** cmdlet Kopieer de inhoud naar de nieuwe locatie?

De **Copy-Item** cmdlet is ontworpen om te worden algemene; het is niet alleen voor het kopiëren van bestanden en mappen. Bovendien zelfs bij het kopiëren van bestanden en mappen, raadzaam om alleen de container en niet de items erin te kopiëren.

Alle van de inhoud van een map wilt kopiëren, omvatten de **Recurse** parameter van de **Copy-Item** cmdlet in de opdracht. Als u de map zonder de inhoud al hebt gekopieerd, voegt u de **Force** parameter, zodat u kunt de lege map overschrijven.

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

### <a name="deleting-items-remove-item"></a>Verwijderen van Items (Item verwijderen)
Als u wilt verwijderen van bestanden en mappen, gebruiken de **Item verwijderen** cmdlet. Windows PowerShell-cmdlets, zoals **Item verwijderen**, die significante kunt maken, niet ongedaan worden gemaakt wijzigingen vaak om bevestiging wordt gevraagd wanneer u de opdrachten invoert. Bijvoorbeeld, als u probeert te verwijderen de **New.Directory** map, wordt u gevraagd om te bevestigen dat de opdracht, omdat de map bestanden bevat:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Omdat **Ja** is het standaardantwoord verwijderen van de map en de bijbehorende bestanden, drukt u op de **Enter** sleutel. U kunt de map zonder bevestiging verwijderen met de **-Recurse** parameter.

```
PS> Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a>Uitvoeren van Items (Invoke-Item)
Windows PowerShell maakt gebruik van de **Invoke-Item** cmdlet een standaardactie uitvoeren voor een bestand of map. Deze standaardactie wordt bepaald door de handler standaard toepassing in het register. het effect is hetzelfde als wanneer u dubbelklikt op het item in Windows Verkenner.

Stel bijvoorbeeld dat u de volgende opdracht uitvoeren:

```
PS> Invoke-Item C:\WINDOWS
```

Een Explorer-venster dat in C: bevindt zich\\Windows wordt weergegeven, net als de C: had dubbelklikken\\Windows-map.

Als u de **Boot.ini** bestand op een systeem ouder dan Windows Vista:

```
PS> Invoke-Item C:\boot.ini
```

Als het type INI-bestand gekoppeld aan Kladblok is, is het boot.ini-bestand wordt geopend in Kladblok.

