---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met bestanden, mappen en registersleutels werken
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: cd20cc50b573435ba80b52b51e164e60625dc1b6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085999"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Werken met bestanden, mappen en registersleutels

Windows PowerShell maakt gebruik van het zelfstandig naamwoord **Item** om te verwijzen naar items gevonden op een Windows PowerShell-station. Wanneer er sprake is van het bestandssysteem van Windows PowerShell-provider, een **Item** mogelijk een bestand, een map of het Windows PowerShell-station. Lijst van en werken met de volgende items is een kritieke eenvoudige taak in de meeste instellingen voor de administratieve, zodat we willen deze taken in detail bespreken.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Het inventariseren van bestanden, mappen en registersleutels (Get-ChildItem)

Sinds het ophalen van een verzameling items uit een bepaalde locatie is een veelvoorkomende taak, de **Get-ChildItem** cmdlet is speciaal ontworpen om te retourneren van alle items gevonden in een container, zoals een map.

Als u wilt retourneren van alle bestanden en mappen die zich rechtstreeks in de map C:\\Windows, type:

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

De aanbieding lijkt op wat u zien wilt bij het invoeren van de **dir** opdracht in **Cmd.exe**, of de **ls** opdracht in een UNIX-opdrachtshell.

U kunt zeer complex aanbiedingen uitvoeren met behulp van parameters van de **Get-ChildItem** cmdlet. We kijken we enkele scenario's vervolgens. U kunt zien dat de syntaxis van de **Get-ChildItem** cmdlet door te typen:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Deze parameters kunnen worden gecombineerd en afgestemd om uitvoer op maat gemaakte te halen.

### <a name="listing-all-contained-items--recurse"></a>Alle opgenomen objecten te bieden (-Recurse)

Als zowel de items in een Windows-map en alle items die zijn opgenomen in de submappen weergeven, gebruikt u de **Recurse** parameter van **Get-ChildItem**. De aanbieding wordt weergegeven dat alles in de Windows-map en de items in submappen. Bijvoorbeeld:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a>Items met de naam filteren (-naam)

Als u alleen de namen van items weergeven, gebruiken de **naam** parameter van **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Geforceerd verborgen Items weergeven (-Force)

Items die normaal gesproken niet zichtbaar in Verkenner of Cmd.exe zijn worden niet weergegeven in de uitvoer van een **Get-ChildItem** opdracht. Als u verborgen items weergeven, gebruiken de **Force** parameter van **Get-ChildItem**. Bijvoorbeeld:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Deze parameter is met de naam Force omdat u kunt het normale gedrag van geforceerd overschrijven de **Get-ChildItem** opdracht. Force is een veelgebruikte parameter die ervoor zorgt een actie die een cmdlet niet normaal kunt uitvoeren, dat hoewel een actie op die de beveiliging van het systeem wordt aangetast wordt niet uitgevoerd.

### <a name="matching-item-names-with-wildcards"></a>Overeenkomende itemnamen met jokertekens

**De Get-ChildItem** opdracht jokertekens in het pad van de items om weer te geven.

Omdat jokertekens worden verwerkt door de Windows PowerShell-engine, worden alle cmdlets die jokertekens gebruiken de dezelfde notatie en hebben hetzelfde gedrag overeenkomende. De notatie van de Windows PowerShell-jokertekens bevat:

- Sterretje (\*) komt overeen met nul of meer exemplaren van een willekeurig teken.

- Vraagteken (?) komt overeen met precies één teken.

- Haakje openen (\[) en teken rechte haak sluiten (]) rondom een reeks tekens worden vergeleken.

Hier volgen enkele voorbeelden van de werking van jokertekens-specificatie.

Zoeken naar alle bestanden in de Windows-map met het achtervoegsel **.log** en exact vijf tekens in de naam van de basis, voer de volgende opdracht:

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

Zoeken naar alle bestanden die met de letter beginnen **x** in de Windows-map, typ:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Zoeken naar alle bestanden waarvan de namen met beginnen **x** of **z**, type:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a>Items uitsluiten (-uitsluiten)

U kunt specifieke objecten uitsluiten met behulp van de **uitsluiten** parameter van Get-ChildItem. Hiermee kunt u complexe filteren in één instructie uitvoeren.

Stel bijvoorbeeld dat u wilt het DLL-bestand van Windows Time-Service niet vinden in de map System32 en u kunt meer weet over de dll-naam, is dat het begint met de letter "W" en "32" bevat.

Een expressie, zoals **w\&#42; 32\&#42;. DLL-bestand** vindt u alle dll-bestanden die voldoen aan de voorwaarden, maar het kan ook de Windows 95 en 16-bits Windows-compatibiliteit dll-bestanden die zijn '95' of '16' terug in hun namen. U kunt weglaten bestanden die een van deze getallen in hun namen met behulp van hebben de **uitsluiten** parameter met het patroon  **\&#42;\[ 9516]\&#42;**:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a>Met een combinatie van Parameters voor Get-ChildItem

U kunt meerdere van de parameters van de **Get-ChildItem** cmdlet in dezelfde opdracht. Voordat u parameters combineren, moet u dat u bekend bent met jokertekens. De volgende opdracht retourneert bijvoorbeeld geen resultaten:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Er zijn geen resultaten, zelfs als er zijn twee dll-bestanden die met de letter 'z' in de Windows-map beginnen.

Er zijn geen resultaten geretourneerd omdat we het jokerteken is opgegeven als onderdeel van het pad. Hoewel de opdracht recursieve, is de **Get-ChildItem** cmdlet beperkt de items die zich in de Windows-map met namen die eindigen op '.dll'.

Als u wilt een recursieve zoekopdracht voor bestanden waarvan de namen overeenkomen met een speciale patroon opgeven, gebruikt u de **-opnemen** parameter.

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