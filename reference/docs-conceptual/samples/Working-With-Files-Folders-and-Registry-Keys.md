---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Met bestanden, mappen en registersleutels werken
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030758"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Werken met bestanden, mappen en register sleutels

Windows Power shell gebruikt het **item** van de zelfstandig naam om te verwijzen naar items die op een Windows Power Shell-station zijn gevonden. Bij de verwerking van de Windows Power shell-bestandssysteem provider kan een **item** een bestand, een map of het Windows Power Shell-station zijn. Het weer geven en werken met deze items is een kritieke basis taak in de meeste beheer instellingen, dus we willen deze taken in detail bespreken.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Bestanden, mappen en register sleutels opsommen (Get-Child item)

Omdat het ophalen van een verzameling items van een bepaalde locatie een veelvoorkomende taak is, is de cmdlet **Get-Child item** specifiek ontworpen om alle items te retour neren die zijn gevonden in een container, zoals een map.

Als u alle bestanden en mappen wilt retour neren die zich rechtstreeks in de map C bevinden:\\Windows, typt u:

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

De vermelding lijkt op wat u ziet wanneer u de opdracht **dir** in **cmd. exe**of de **ls** -opdracht in een UNIX-opdracht shell opgeeft.

U kunt zeer complexe vermeldingen uitvoeren met behulp van para meters van de cmdlet **Get-Child item** . We gaan nu een paar scenario's bekijken. U kunt de syntaxis van de cmdlet **Get-Child item** zien door het volgende te typen:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Deze para meters kunnen worden gecombineerd en overeenkomen om een zeer aangepaste uitvoer te krijgen.

### <a name="listing-all-contained-items--recurse"></a>Alle opgenomen items weer geven (-recursief)

Als u beide items in een Windows-map en alle items in de submappen wilt weer geven, gebruikt u de para meter **recursieve** van **Get-Child item**. De vermelding bevat alles in de Windows-map en de items in de submappen. Bijvoorbeeld:

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

Als u alleen de namen van items wilt weer geven, gebruikt u de para meter **name** van **Get-Child item**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Geforceerde vermelding van verborgen items (-Force)

Items die normaal gesp roken onzichtbaar zijn in Verkenner of Cmd. exe worden niet weer gegeven in de uitvoer van de opdracht **Get-Child item** . Als u verborgen items wilt weer geven, gebruikt u de para meter **Forces** van **Get-Child item**. Bijvoorbeeld:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Deze para meter heeft de naam Force omdat u het normale gedrag van de opdracht **Get-Child item** kunt negeren. Force is een veelgebruikte para meter die een actie afdwingt die een cmdlet normaal gesp roken niet zou uitvoeren, hoewel er geen actie wordt uitgevoerd die de beveiliging van het systeem in de hand brengt.

### <a name="matching-item-names-with-wildcards"></a>Overeenkomende item namen met Joker tekens

**De opdracht Get-Child item** accepteert joker tekens in het pad van de items die moeten worden weer geven.

Omdat het vergelijken van het Joker teken wordt verwerkt door de Windows Power shell-engine, gebruiken alle cmdlets die joker tekens accepteren, dezelfde notatie en hebben hetzelfde overeenkomstige gedrag. De Windows Power shell-Joker teken notatie bevat:

- Asterisk (\*) komt overeen met nul of meer exemplaren van elk wille keurig teken.

- Vraag teken (?) komt overeen met één teken.

- Teken voor haakje links (\[) en haakje (]) rond een reeks tekens die moeten worden vergeleken.

Hier volgen enkele voor beelden van de werking van joker tekens.

Als u alle bestanden in de Windows-map wilt zoeken met het achtervoegsel **. log** en precies vijf tekens in de basis naam, voert u de volgende opdracht in:

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

Als u alle bestanden wilt vinden die beginnen met de letter **x** in de map Windows, typt u:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Als u wilt zoeken naar alle bestanden waarvan de naam begint met **x** of **z**, typt u:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a>Uitsluiten van items (-uitsluiten)

U kunt specifieke items uitsluiten met behulp van de **exclude** -para meter van Get-Child item. Zo kunt u complexe filters uitvoeren in één instructie.

Stel dat u de Windows Time-service-DLL wilt vinden in de map System32 en dat u meer weet over de DLL-naam dat deze begint met ' W ' en dat deze ' 32 ' bevat.

Een expressie zoals **w\&#42; 32\&#42;. het dll** -bestand bevat alle dll-bestanden die voldoen aan de voor waarden, maar deze kunnen ook de Windows-compatibiliteits-dll's (95 en 16-bits) retour neren die "95" of "16" in hun namen bevatten. U kunt bestanden met een van deze getallen in hun namen weglaten met de **exclude** -para meter met het patroon **\&#42;\[9516]\&#42;** :

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

### <a name="mixing-get-childitem-parameters"></a>Get-Child item-para meters combi neren

U kunt verschillende para meters van de cmdlet **Get-Child item** in dezelfde opdracht gebruiken. Voordat u para meters gaat mengen, moet u ervoor zorgen dat u begrijpt dat er joker tekens overeenkomen. De volgende opdracht retourneert bijvoorbeeld geen resultaten:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Er zijn geen resultaten, hoewel er twee Dll's zijn die beginnen met de letter ' z ' in de map Windows.

Er zijn geen resultaten geretourneerd omdat het Joker teken is opgegeven als onderdeel van het pad. Hoewel de opdracht recursief is, heeft de cmdlet **Get-Child item** de items beperkt tot die in de Windows-map met namen die eindigen op '. dll '.

Als u een recursieve zoek opdracht wilt opgeven voor bestanden waarvan de namen overeenkomen met een speciaal patroon, gebruikt u de para meter **-include** .

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
