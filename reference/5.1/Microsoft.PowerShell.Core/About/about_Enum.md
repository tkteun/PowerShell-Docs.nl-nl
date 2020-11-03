---
description: De `enum` instructie wordt gebruikt voor het declareren van een opsomming. Een opsomming is een afzonderlijk type dat bestaat uit een set benoemde labels, de lijst enumerator genoemd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 0b1959ba009119769535c3d39231ff8dab9dc5de
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252810"
---
# <a name="about-enum"></a><span data-ttu-id="245fb-105">Over Enum</span><span class="sxs-lookup"><span data-stu-id="245fb-105">About Enum</span></span>

## <a name="short-description"></a><span data-ttu-id="245fb-106">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="245fb-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="245fb-107">De `enum` instructie wordt gebruikt voor het declareren van een opsomming.</span><span class="sxs-lookup"><span data-stu-id="245fb-107">The `enum` statement is used to declare an enumeration.</span></span> <span data-ttu-id="245fb-108">Een opsomming is een afzonderlijk type dat bestaat uit een set benoemde labels, de lijst enumerator genoemd.</span><span class="sxs-lookup"><span data-stu-id="245fb-108">An enumeration is a distinct type that consists of a set of named labels called the enumerator list.</span></span>

## <a name="long-description"></a><span data-ttu-id="245fb-109">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="245fb-109">LONG DESCRIPTION</span></span>

<span data-ttu-id="245fb-110">Met de- `enum` instructie kunt u een sterk getypeerde set labels maken.</span><span class="sxs-lookup"><span data-stu-id="245fb-110">The `enum` statement allows you to create a strongly typed set of labels.</span></span> <span data-ttu-id="245fb-111">Deze opsomming kan worden gebruikt in de code zonder spel fouten te hoeven parseren of te controleren.</span><span class="sxs-lookup"><span data-stu-id="245fb-111">That enumeration can be used in the code without having to parse or check for spelling errors.</span></span>

<span data-ttu-id="245fb-112">Opsommingen worden intern vertegenwoordigd als gehele getallen met de begin waarde nul.</span><span class="sxs-lookup"><span data-stu-id="245fb-112">Enumerations are internally represented as integers with a starting value of zero.</span></span> <span data-ttu-id="245fb-113">De waarde nul wordt toegewezen aan het eerste label in de lijst.</span><span class="sxs-lookup"><span data-stu-id="245fb-113">The first label in the list is assigned the value zero.</span></span> <span data-ttu-id="245fb-114">De overige labels worden toegewezen met opeenvolgende cijfers.</span><span class="sxs-lookup"><span data-stu-id="245fb-114">The remaining labels are assigned with consecutive numbers.</span></span>

<span data-ttu-id="245fb-115">In de definitie kunnen labels elk wille keurig geheel getal worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="245fb-115">In the definition, labels can be given any integer value.</span></span> <span data-ttu-id="245fb-116">Labels waaraan geen waarde is toegewezen, nemen de volgende gehele waarde.</span><span class="sxs-lookup"><span data-stu-id="245fb-116">Labels with no value assigned take the next integer value.</span></span>

## <a name="syntax-basic"></a><span data-ttu-id="245fb-117">Syntaxis (Basic)</span><span class="sxs-lookup"><span data-stu-id="245fb-117">Syntax (basic)</span></span>

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a><span data-ttu-id="245fb-118">Voor beeld van gebruik</span><span class="sxs-lookup"><span data-stu-id="245fb-118">Usage example</span></span>

<span data-ttu-id="245fb-119">In het volgende voor beeld ziet u een inventarisatie van objecten die kunnen worden gezien als media bestanden.</span><span class="sxs-lookup"><span data-stu-id="245fb-119">The following example shows an enumeration of objects that can be seen as media files.</span></span> <span data-ttu-id="245fb-120">De definitie wijst expliciete waarden toe aan de onderliggende waarden van `music` , `picture` ,, `video` .</span><span class="sxs-lookup"><span data-stu-id="245fb-120">The definition assigns explicit values to the underlying values of `music`, `picture`, `video`.</span></span> <span data-ttu-id="245fb-121">Labels direct na een expliciete toewijzing krijgen de volgende gehele waarde.</span><span class="sxs-lookup"><span data-stu-id="245fb-121">Labels immediately following an explicit assignment get the next integer value.</span></span> <span data-ttu-id="245fb-122">Synoniemen kunnen worden gemaakt door dezelfde waarde toe te wijzen aan een ander label. Zie de geconstrueerde waarden voor: `ogg` , `oga` , `mogg` , of,, `jpg` `jpeg` of `mpg` , `mpeg` .</span><span class="sxs-lookup"><span data-stu-id="245fb-122">Synonyms can be created by assigning the same value to another label; see the constructed values for: `ogg`, `oga`, `mogg`, or `jpg`, `jpeg`, or `mpg`, `mpeg`.</span></span>

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

<span data-ttu-id="245fb-123">De `GetEnumNames()` methode retourneert de lijst met labels voor de opsomming.</span><span class="sxs-lookup"><span data-stu-id="245fb-123">The `GetEnumNames()` method returns the list of the labels for the enumeration.</span></span>

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

<span data-ttu-id="245fb-124">De `GetEnumValues()` methode retourneert de lijst met de waarden voor de opsomming.</span><span class="sxs-lookup"><span data-stu-id="245fb-124">The `GetEnumValues()` method returns the list of the values for the enumeration.</span></span>

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

<span data-ttu-id="245fb-125">**Opmerking** : GetEnumNames () en GetEnumValues () lijken dezelfde resultaten te retour neren.</span><span class="sxs-lookup"><span data-stu-id="245fb-125">**Note** : GetEnumNames() and GetEnumValues() seem to return the same results.</span></span>
<span data-ttu-id="245fb-126">In Power shell worden waarden echter gewijzigd in labels.</span><span class="sxs-lookup"><span data-stu-id="245fb-126">However, internally, PowerShell is changing values into labels.</span></span> <span data-ttu-id="245fb-127">Lees de lijst zorgvuldig en u zult zien dat `oga` en `mogg` wordt vermeld onder de resultaten van ' Get names ', maar niet onder de ' Get values '-Vergelijk bare uitvoer voor `jpg` , `jpeg` , en `mpg` `mpeg` .</span><span class="sxs-lookup"><span data-stu-id="245fb-127">Read the list carefully and you'll notice that `oga` and `mogg` are mentioned under the 'Get Names' results, but not under the 'Get Values' similar output for `jpg`, `jpeg`, and `mpg`, `mpeg`.</span></span>

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

## <a name="enumerations-as-flags"></a><span data-ttu-id="245fb-128">Opsommingen als vlaggen</span><span class="sxs-lookup"><span data-stu-id="245fb-128">Enumerations as flags</span></span>

<span data-ttu-id="245fb-129">Opsommingen kunnen worden gedefinieerd als een verzameling van bitvlaggen.</span><span class="sxs-lookup"><span data-stu-id="245fb-129">Enumerations can be defined as a collection of bit flags.</span></span>
<span data-ttu-id="245fb-130">Waarbij op een bepaald moment de opsomming een of meer van deze vlaggen vertegenwoordigt die zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="245fb-130">Where, at any given point the enumeration represents one or more of those flags turned on.</span></span>

<span data-ttu-id="245fb-131">Voor opsommingen als vlaggen goed werken, moet elk label een macht van twee waarde hebben.</span><span class="sxs-lookup"><span data-stu-id="245fb-131">For enumerations as flags to work properly, each label should have a power of two value.</span></span>

## <a name="syntax-flags"></a><span data-ttu-id="245fb-132">Syntaxis (vlaggen)</span><span class="sxs-lookup"><span data-stu-id="245fb-132">Syntax (flags)</span></span>

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a><span data-ttu-id="245fb-133">Gebruiks voorbeeld van vlaggen</span><span class="sxs-lookup"><span data-stu-id="245fb-133">Flags usage example</span></span>

<span data-ttu-id="245fb-134">In het volgende voor beeld wordt de *FileAttributes* -inventarisatie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="245fb-134">In the following example the *FileAttributes* enumeration is created.</span></span>

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

<span data-ttu-id="245fb-135">Als u wilt testen of een specifieke set is ingesteld, kunt u de binaire vergelijkings operator gebruiken `-band` .</span><span class="sxs-lookup"><span data-stu-id="245fb-135">To test that a specific is set, you can use the binary comparison operator `-band`.</span></span> <span data-ttu-id="245fb-136">In dit voor beeld testen we op het **apparaat** en de **Archief** kenmerken in de waarde van `$file2` .</span><span class="sxs-lookup"><span data-stu-id="245fb-136">In this example, we test for the **Device** and the **Archive** attributes in the value of `$file2`.</span></span>

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```
