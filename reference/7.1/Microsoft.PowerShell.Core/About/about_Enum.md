---
description: De `enum` instructie wordt gebruikt voor het declareren van een opsomming. Een opsomming is een afzonderlijk type dat bestaat uit een set benoemde labels, de lijst enumerator genoemd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 1ffb18ab98fbd40b407abfe32c71027315b69621
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252455"
---
# <a name="about-enum"></a>Over Enum

## <a name="short-description"></a>KORTE BESCHRIJVING
De `enum` instructie wordt gebruikt voor het declareren van een opsomming. Een opsomming is een afzonderlijk type dat bestaat uit een set benoemde labels, de lijst enumerator genoemd.

## <a name="long-description"></a>LANGE BESCHRIJVING

Met de- `enum` instructie kunt u een sterk getypeerde set labels maken. Deze opsomming kan worden gebruikt in de code zonder spel fouten te hoeven parseren of te controleren.

Opsommingen worden intern vertegenwoordigd als gehele getallen met de begin waarde nul. De waarde nul wordt toegewezen aan het eerste label in de lijst. De overige labels worden toegewezen met opeenvolgende cijfers.

In de definitie kunnen labels elk wille keurig geheel getal worden opgegeven. Labels waaraan geen waarde is toegewezen, nemen de volgende gehele waarde.

## <a name="syntax-basic"></a>Syntaxis (Basic)

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a>Voor beeld van gebruik

In het volgende voor beeld ziet u een inventarisatie van objecten die kunnen worden gezien als media bestanden. De definitie wijst expliciete waarden toe aan de onderliggende waarden van `music` , `picture` ,, `video` . Labels direct na een expliciete toewijzing krijgen de volgende gehele waarde. Synoniemen kunnen worden gemaakt door dezelfde waarde toe te wijzen aan een ander label. Zie de geconstrueerde waarden voor: `ogg` , `oga` , `mogg` , of,, `jpg` `jpeg` of `mpg` , `mpeg` .

```powershell
enum MediaTypes {
    unknown
    music = 10
    mp3
    aac
    ogg = 15
    oga = 15
    mogg = 15
    picture = 20
    jpg
    jpeg = 21
    png
    video = 40
    mpg
    mpeg = 41
    avi
    m4v
}
```

De `GetEnumNames()` methode retourneert de lijst met labels voor de opsomming.

```powershell
[MediaTypes].GetEnumNames()
unknown
music
mp3
aac
ogg
oga
mogg
picture
jpg
jpeg
png
video
mpg
mpeg
avi
m4v
```

De `GetEnumValues()` methode retourneert de lijst met de waarden voor de opsomming.

```powershell
[MediaTypes].GetEnumValues()
unknown
music
mp3
aac
oga
oga
oga
picture
jpeg
jpeg
png
video
mpeg
mpeg
avi
m4v
```

**Opmerking** : GetEnumNames () en GetEnumValues () lijken dezelfde resultaten te retour neren.
In Power shell worden waarden echter gewijzigd in labels. Lees de lijst zorgvuldig en u zult zien dat `oga` en `mogg` wordt vermeld onder de resultaten van ' Get names ', maar niet onder de ' Get values '-Vergelijk bare uitvoer voor `jpg` , `jpeg` , en `mpg` `mpeg` .

```powershell
[MediaTypes].GetEnumName(15)
oga

[MediaTypes].GetEnumNames() | ForEach-Object {
  "{0,-10} {1}" -f $_,[int]([MediaTypes]::$_)
}
unknown    0
music      10
mp3        11
aac        12
ogg        15
oga        15
mogg       15
picture    20
jpg        21
jpeg       21
png        22
video      40
mpg        41
mpeg       41
avi        42
m4v        43
```

## <a name="enumerations-as-flags"></a>Opsommingen als vlaggen

Opsommingen kunnen worden gedefinieerd als een verzameling van bitvlaggen.
Waarbij op een bepaald moment de opsomming een of meer van deze vlaggen vertegenwoordigt die zijn ingeschakeld.

Voor opsommingen als vlaggen goed werken, moet elk label een macht van twee waarde hebben.

## <a name="syntax-flags"></a>Syntaxis (vlaggen)

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a>Gebruiks voorbeeld van vlaggen

In het volgende voor beeld wordt de *FileAttributes* -inventarisatie gemaakt.

```powershell
[Flags()] enum FileAttributes {
    Archive = 1
    Compressed = 2
    Device = 4
    Directory = 8
    Encrypted = 16
    Hidden = 32
}

[FileAttributes]$file1 = [FileAttributes]::Archive
[FileAttributes]$file1 +=[FileAttributes]::Compressed
[FileAttributes]$file1 +=  [FileAttributes]::Device
"file1 attributes are: $file1"

[FileAttributes]$file2 = [FileAttributes]28 ## => 16 + 8 + 4
"file2 attributes are: $file2"
```

```output
file1 attributes are: Archive, Compressed, Device
file2 attributes are: Device, Directory, Encrypted
```

Als u wilt testen of een specifieke set is ingesteld, kunt u de binaire vergelijkings operator gebruiken `-band` . In dit voor beeld testen we op het **apparaat** en de **Archief** kenmerken in de waarde van `$file2` .

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```

