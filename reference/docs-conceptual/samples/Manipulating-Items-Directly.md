---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Items rechtstreeks bewerken
ms.openlocfilehash: 50aed569cf6b876297abe3cf1544eba70f6279ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030127"
---
# <a name="manipulating-items-directly"></a>Items rechtstreeks bewerken

De elementen die u ziet in Windows Power Shell-stations, zoals de bestanden en mappen in de bestandssysteem stations en de register sleutels in de Windows Power shell-register stations, worden *items* genoemd in Windows Power shell. De cmdlets voor het werken met deze items hebben het zelfstandige naam **item** .

De uitvoer van de opdracht **Get-opdracht-item** van het zelfstandig naam woord laat zien dat er negen Windows Power shell-cmdlets voor items zijn.

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

## <a name="creating-new-items-new-item"></a>Nieuwe items maken (nieuw item)

Gebruik de cmdlet **New-item** om een nieuw item in het bestands systeem te maken. Neem de para meter **Path** op met het pad naar het item en de **item** type-para meter met de waarde "file" of "directory".

Als u bijvoorbeeld een nieuwe map met de naam ' New. Directory ' wilt maken in de map C:\\Temp, typt u:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Als u een bestand wilt maken, wijzigt u de waarde van de para meter **item** type in "bestand". Als u bijvoorbeeld een bestand met de naam ' bestand1. txt ' in de nieuwe map wilt maken, typt u:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

U kunt dezelfde techniek gebruiken om een nieuwe register sleutel te maken. Een register sleutel is eigenlijk eenvoudiger te maken, omdat het enige item type in het Windows-REGI ster een sleutel is. (Register vermeldingen zijn item *Eigenschappen*.) Als u bijvoorbeeld een sleutel met de naam ' _Test ' wilt maken in de subsleutel CurrentVersion, typt u:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Wanneer u een registerpad typt, moet u de dubbele punt ( **:** ) in de namen van Windows Power Shell-stations, HKLM: en HKCU: toevoegen. Zonder de dubbele punt herkent Windows Power shell de naam van het station niet in het pad.

## <a name="why-registry-values-are-not-items"></a>Waarom register waarden geen items zijn

Wanneer u de cmdlet **Get-Child item** gebruikt om de items in een register sleutel te vinden, zult u nooit de werkelijke Register vermeldingen of hun waarden zien.

De register sleutel **HKEY_LOCAL_MACHINE\\Software\\micro soft\\Windows\\CurrentVersion\\run** bevat doorgaans diverse register vermeldingen die toepassingen vertegenwoordigen die worden uitgevoerd wanneer het systeem wordt gestart.

Als u echter **Get-Child item** gebruikt om te zoeken naar onderliggende items in de sleutel, ziet u de subsleutel **OptionalComponents** van de sleutel:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Hoewel het handig is om Register vermeldingen als items te behandelen, kunt u geen pad naar een register vermelding opgeven op een manier die ervoor zorgt dat deze uniek is. De pad-notatie maakt geen onderscheid tussen de registersubsleutel **Run** en de **(standaard)** register vermelding in de **Run** -subsleutel. Omdat Register vermeldingen echter de back slash-teken ( **\\** ) kunnen bevatten, kunt u, als register items items zijn, de pad-notatie niet gebruiken om onderscheid te maken tussen een register vermelding met de naam **Windows\\CurrentVersion\\worden uitgevoerd** vanuit de subsleutel die zich in dat pad bevindt.

## <a name="renaming-existing-items-rename-item"></a>De naam van bestaande items wijzigen (naam wijzigen-item)

Als u de naam van een bestand of map wilt wijzigen, gebruikt u de cmdlet **Rename-item** . Met de volgende opdracht wordt de naam van het bestand **bestand1. txt** gewijzigd in **fileOne. txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

De cmdlet **Rename-item** kan de naam van een bestand of map wijzigen, maar een item kan niet worden verplaatst. De volgende opdracht mislukt omdat er wordt geprobeerd het bestand te verplaatsen van de nieuwe map. Directory naar de map Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>Items verplaatsen (verplaatsen-item)

Als u een bestand of map wilt verplaatsen, gebruikt u de cmdlet **Move-item** .

Met de volgende opdracht wordt bijvoorbeeld de nieuwe Directory Directory verplaatst van de map C:\\Temp naar de hoofdmap van station C:. Als u wilt controleren of het item is verplaatst, neemt u de para meter **PassThru** van de cmdlet **Move-item** op. Zonder **PassThru**worden met de cmdlet **Move-item** geen resultaten weer gegeven.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>Items kopiëren (kopiëren-item)

Als u bekend bent met de Kopieer bewerkingen in andere shells, kunt u het gedrag van de cmdlet **copy-item** in Windows Power shell ongebruikelijk vinden. Wanneer u een item van de ene locatie naar een andere kopieert, wordt de inhoud niet standaard gekopieerd.

Als u bijvoorbeeld de map **New. Directory** van station c: kopieert naar de map c:\\Temp, is de opdracht geslaagd, maar de bestanden in de nieuwe directory-map worden niet gekopieerd.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Als u de inhoud van **C:\\temp\\New. Directory**weergeeft, ziet u dat deze geen bestanden bevat:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Waarom kopieert de cmdlet **copy-item** de inhoud niet naar de nieuwe locatie?

De cmdlet **copy-item** is ontworpen als algemeen; het is niet alleen bedoeld voor het kopiëren van bestanden en mappen. Ook als u bestanden en mappen kopieert, wilt u misschien alleen de container kopiëren en niet de items hierin.

Als u alle inhoud van een map wilt kopiëren, neemt u de para meter **recursieve** van de cmdlet **copy-item** op in de opdracht. Als u de map al hebt gekopieerd zonder de inhoud, voegt u de para meter **Force** toe, waarmee u de lege map kunt overschrijven.

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

## <a name="deleting-items-remove-item"></a>Items verwijderen (verwijderen-item)

Als u bestanden en mappen wilt verwijderen, gebruikt u de cmdlet **Remove-item** . Windows Power shell-cmdlets, zoals **Remove-item**, die aanzienlijke, onherstelbare wijzigingen kunnen aanbrengen, worden vaak gevraagd om bevestiging wanneer u de opdrachten opgeeft. Als u bijvoorbeeld probeert de **nieuwe map.** map te verwijderen, wordt u gevraagd om de opdracht te bevestigen, omdat de map bestanden bevat:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Omdat **Ja** de standaard reactie is, kunt u de map en de bijbehorende bestanden verwijderen door op **Enter** te drukken. Als u de map wilt verwijderen zonder te bevestigen, gebruikt u de para meter **-recursief** .

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>Items uitvoeren (invoke-item)

Windows Power shell gebruikt de cmdlet **invoke-item** om een standaard actie uit te voeren voor een bestand of map. Deze standaard actie wordt bepaald door de standaard toepassings-handler in het REGI ster. het effect is hetzelfde als wanneer u dubbelklikt op het item in Verkenner.

Stel bijvoorbeeld dat u de volgende opdracht uitvoert:

```powershell
Invoke-Item C:\WINDOWS
```

Een Verkenner-venster dat zich bevindt in C:\\Windows wordt weer gegeven, net zoals als u op de map C:\\Windows hebt gedubbelklikt.

Als u het bestand **boot. ini** aanroept op een systeem vóór Windows Vista:

```powershell
Invoke-Item C:\boot.ini
```

Als het ini-bestands type is gekoppeld aan Klad blok, wordt het bestand Boot. ini geopend in Klad blok.
