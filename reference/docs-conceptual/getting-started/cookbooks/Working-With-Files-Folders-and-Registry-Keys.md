---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met bestanden, mappen en registersleutels werken
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-files-folders-and-registry-keys"></a>Werken met bestanden, mappen en registersleutels

Windows PowerShell maakt gebruik van het zelfstandig naamwoord **Item** om te verwijzen naar objecten gevonden op een Windows PowerShell-station. Het bestandssysteem van Windows PowerShell-provider betreft een **Item** mogelijk een bestand, een map of het Windows PowerShell-station. Aanbieding van en werken met de volgende items is een kritieke basic taak in de meeste beheerinstellingen, zodat we willen deze taken in detail behandeld.

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Het inventariseren van bestanden, mappen en registersleutels (Get-ChildItem)

Omdat een verzameling items ophalen uit een bepaalde locatie een algemene taak is, de **Get-ChildItem** cmdlet is speciaal ontworpen om te retourneren van alle items gevonden binnen een container, zoals een map.

Als u wilt retourneren van alle bestanden en mappen die zijn opgenomen in de map C: rechtstreeks\\Windows, type:

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

De aanbieding lijkt op wat u ziet wanneer u de **dir** opdracht in **Cmd.exe**, of de **ls** opdracht in een UNIX-opdrachtshell.

U kunt zeer complexe aanbiedingen uitvoeren met behulp van de parameters van de **Get-ChildItem** cmdlet. Kijken we enkele scenario's naast. Ziet u de syntaxis van de **Get-ChildItem** cmdlet door te typen:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Deze parameters kunnen worden gecombineerd en worden aangepast om zeer aangepaste uitvoer te halen.

#### <a name="listing-all-contained-items--recurse"></a>Lijst van alle opgenomen Items (-Recurse)

Als zowel de items in een Windows-map en alle items die deel uitmaken van de submappen wilt weergeven, gebruikt de **Recurse** parameter van **Get-ChildItem**. De aanbieding wordt alles weergegeven in de Windows-map en de items in de submappen ervan. Bijvoorbeeld:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a>Items met de naam filteren (-naam)

Alleen de namen van items weergegeven, gebruikt u de **naam** parameter van **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a>Geforceerd verborgen Items weergeven (-Force)

Items die normaal gesproken niet zichtbaar in Windows Verkenner of Cmd.exe zijn worden niet weergegeven in de uitvoer van een **Get-ChildItem** opdracht. U verborgen items weergeven met behulp de **Force** parameter van **Get-ChildItem**. Bijvoorbeeld:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Deze parameter is met de naam Force omdat kunt u de normale werking van geforceerd overschrijven de **Get-ChildItem** opdracht. Force is een veelgebruikte parameter dat ervoor zorgt een actie die een cmdlet niet normaal kunt uitvoeren, dat hoewel een actie op die de beveiliging van het systeem wordt aangetast wordt niet uitgevoerd.

#### <a name="matching-item-names-with-wildcards"></a>Overeenkomende itemnamen met jokertekens

**De Get-ChildItem** opdracht accepteert jokertekens in het pad van de items om weer te geven.

Omdat met jokertekens worden verwerkt door de Windows PowerShell-engine, alle cmdlets die jokertekens accepteert de dezelfde notatie hebben en hetzelfde gedrag overeenkomende hebt. De Windows PowerShell-notatie hebben jokertekens bevat:

- Sterretje (\*) komt overeen met nul of meer exemplaren van een willekeurig teken.

- Vraagteken (?) komt overeen met precies één teken.

- Vierkante linkerhaak (\[) en vierkante rechterhaak (]) teken rond een reeks tekens worden vergeleken.

Hier volgen enkele voorbeelden van de werking van de specificatie van het jokerteken.

Als u alle bestanden in de Windows-map met het achtervoegsel **.log** en exact vijf tekens in de basisnaam, voer de volgende opdracht:

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

Als u alle bestanden die met de letter beginnen **x** Typ in de Windows-map:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Als u alle bestanden waarvan de naam met begint **x** of **z**, type:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a>Items uitsluiten (-uitsluiten)

U kunt specifieke items uitsluiten door de **uitsluiten** parameter van Get-ChildItem. Hiermee kunt u complexe filteren in één instructie uitvoeren.

Stel dat u wilt zoeken naar het DLL-bestand van Windows Time-Service in de map System32 en alle makkelijk te onthouden over de naam van het DLL-bestand is dat het begint met de letter "W" en '32' bevat.

Een expressie, zoals **w\&#42; 32\&#42;. DLL-bestand** vindt u alle dll-bestanden die voldoen aan de voorwaarden, maar er kan ook de Windows 95 en 16-bits Windows compatibiliteit dll-bestanden met '95' of '16' geretourneerd in hun naam. U kunt bestanden met een van deze getallen in hun namen met behulp van weglaten de **uitsluiten** parameter met het patroon  **\&#42;\[ 9516]\&#42;**:

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

#### <a name="mixing-get-childitem-parameters"></a>De combinatie van Parameters voor Get-ChildItem

U kunt verschillende van de parameters van de **Get-ChildItem** cmdlet in dezelfde opdracht. Voordat u parameters mengen, moet u dat u bekend met jokertekens bent. De volgende opdracht wordt bijvoorbeeld geen resultaten oplevert:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Er zijn geen resultaten, zelfs als er zijn twee dll's die met de letter "z" in de Windows-map beginnen.

Er zijn geen resultaten geretourneerd omdat we het jokerteken als deel van het pad opgegeven. Hoewel de opdracht recursieve, is de **Get-ChildItem** cmdlet de items beperkt tot apparaten die in de Windows-map met namen die eindigen op '.dll'.

Een recursieve zoekopdracht voor bestanden waarvan de namen overeenkomen met een speciale patroon gebruikt u de **-omvatten** parameter.

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