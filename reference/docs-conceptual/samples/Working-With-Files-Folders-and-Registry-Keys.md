---
ms.date: 07/28/2020
keywords: powershell,cmdlet
title: Met bestanden, mappen en registersleutels werken
ms.openlocfilehash: 7ead5d0e82feb852845468fb3a012a0908a4ce75
ms.sourcegitcommit: 339e5fc8a4cc18b4ff6956fe5180343588e40e30
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410186"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Werken met bestanden, mappen en register sleutels

Windows Power shell gebruikt het **item** van de zelfstandig naam om te verwijzen naar items die op een Windows Power Shell-station zijn gevonden.
Bij de verwerking van de Windows Power shell-bestandssysteem provider kan een **item** een bestand, een map of het Windows Power Shell-station zijn. Het weer geven en werken met deze items is een kritieke basis taak in de meeste beheer instellingen, dus we willen deze taken in detail bespreken.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Bestanden, mappen en register sleutels opsommen (Get-Child item)

Omdat het ophalen van een verzameling items van een bepaalde locatie een veelvoorkomende taak is, `Get-ChildItem` is de cmdlet speciaal ontworpen om alle items te retour neren die zijn gevonden in een container, zoals een map.

Als u alle bestanden en mappen wilt retour neren die zich rechtstreeks in de map C: Windows bevinden \\ , typt u:

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

De vermelding lijkt op wat u ziet wanneer u de `dir` opdracht invoert in **Cmd.exe**of de `ls` opdracht in een UNIX-opdracht shell.

U kunt zeer complexe vermeldingen uitvoeren met behulp van para meters van de `Get-ChildItem` cmdlet. We gaan nu een paar scenario's bekijken. U kunt de syntaxis van de `Get-ChildItem` cmdlet zien door het volgende te typen:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Deze para meters kunnen worden gecombineerd en overeenkomen om een zeer aangepaste uitvoer te krijgen.

### <a name="listing-all-contained-items--recurse"></a>Alle opgenomen items weer geven (-recursief)

Als u beide items in een Windows-map en alle items in de submappen wilt zien, gebruikt u de para meter **recursieve** van `Get-ChildItem` . De vermelding bevat alles in de Windows-map en de items in de submappen. Bijvoorbeeld:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a>Items filteren op naam (-naam)

Als u alleen de namen van items wilt weer geven, gebruikt u de para meter **name** van `Get-Childitem` :

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Geforceerde vermelding van verborgen items (-Force)

Items die normaal gesp roken onzichtbaar zijn in bestanden Verkenner of Cmd.exe worden niet weer gegeven in de uitvoer van een `Get-ChildItem` opdracht. Als u verborgen items wilt weer geven, gebruikt u de para meter **Force** van `Get-ChildItem` .
Bijvoorbeeld:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Deze para meter heeft de naam Force omdat u het normale gedrag van de opdracht kunt negeren `Get-ChildItem` . Force is een veelgebruikte para meter die een actie afdwingt die een cmdlet normaal gesp roken niet zou uitvoeren, hoewel er geen actie wordt uitgevoerd die de beveiliging van het systeem in de hand brengt.

### <a name="matching-item-names-with-wildcards"></a>Overeenkomende item namen met Joker tekens

De `Get-ChildItem` opdracht accepteert joker tekens in het pad van de items die moeten worden weer geven.

Omdat het vergelijken van het Joker teken wordt verwerkt door de Windows Power shell-engine, gebruiken alle cmdlets die joker tekens accepteren, dezelfde notatie en hebben hetzelfde overeenkomstige gedrag. De Windows Power shell-Joker teken notatie bevat:

- Sterretje ( `*` ) komt overeen met nul of meer exemplaren van elk wille keurig teken.

- Vraag teken ( `?` ) komt overeen met één teken.

- Teken voor vier Kante haakjes ( `[` ) en rechter haakje ( `]` ) rond een reeks tekens die moeten worden vergeleken.

Hier volgen enkele voor beelden van de werking van joker tekens.

Voer de volgende opdracht in om alle bestanden in de Windows-map met het achtervoegsel `.log` en exact vijf tekens in de basis naam op te zoeken:

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

Als u alle bestanden wilt vinden die beginnen met de letter `x` in de Windows-map, typt u:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Als u wilt zoeken naar alle bestanden waarvan de naam begint met ' x ' of ' z ', typt u:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

Zie [about_Wildcards](/powershell/module/microsoft.powershell.core/about/about_wildcards)voor meer informatie over joker tekens.

### <a name="excluding-items--exclude"></a>Uitsluiten van items (-uitsluiten)

U kunt specifieke items uitsluiten met behulp van de **exclude** -para meter van `Get-ChildItem` . Zo kunt u complexe filters uitvoeren in één instructie.

Stel dat u de Windows Time-service-DLL wilt vinden in de map **System32** en dat u meer weet over de DLL-naam dat deze begint met ' W ' en dat deze ' 32 ' bevat.

Een expressie Like `w*32*.dll` bevat alle dll's die voldoen aan de voor waarden, maar u wilt mogelijk de bestanden verder uitfilteren en Win32-bestanden weglaten. U kunt deze bestanden weglaten met de para meter **exclude** met het patroon `win*` :

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude win*

    Directory: C:\WINDOWS\System32

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           3/18/2019  9:43 PM         495616 w32time.dll
-a---           3/18/2019  9:44 PM          35328 w32topl.dll
-a---           1/24/2020  5:44 PM         401920 Wldap32.dll
-a---          10/10/2019  5:40 PM         442704 ws2_32.dll
-a---           3/18/2019  9:44 PM          66048 wsnmp32.dll
-a---           3/18/2019  9:44 PM          18944 wsock32.dll
-a---           3/18/2019  9:44 PM          64792 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a>Get-Child item-para meters combi neren

U kunt verschillende para meters van de `Get-ChildItem` cmdlet gebruiken in dezelfde opdracht. Voordat u para meters gaat mengen, moet u ervoor zorgen dat u begrijpt dat er joker tekens overeenkomen. De volgende opdracht retourneert bijvoorbeeld geen resultaten:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Er zijn geen resultaten, hoewel er twee Dll's zijn die beginnen met de letter ' z ' in de map Windows.

Er zijn geen resultaten geretourneerd omdat het Joker teken is opgegeven als onderdeel van het pad. Hoewel de opdracht recursief was, `Get-ChildItem` beperkt de cmdlet de items in de Windows-map met namen die eindigen op `.dll` .

Als u een recursieve zoek opdracht wilt opgeven voor bestanden waarvan de namen overeenkomen met een speciaal patroon, gebruikt u de para meter **include** .

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
