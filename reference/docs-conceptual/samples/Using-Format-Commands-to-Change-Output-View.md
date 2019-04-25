---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Format-opdrachten gebruiken om de uitvoerweergave te wijzigen
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: fba37b1d0479bf605d8f2171da27cd1bceb9976e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058264"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="cdde8-103">Format-opdrachten gebruiken om de uitvoerweergave te wijzigen</span><span class="sxs-lookup"><span data-stu-id="cdde8-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="cdde8-104">Windows PowerShell is een set van cmdlets waarmee u kunt om te bepalen welke eigenschappen voor bepaalde objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="cdde8-105">De namen van alle cmdlets beginnen met de term **indeling**.</span><span class="sxs-lookup"><span data-stu-id="cdde8-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="cdde8-106">U kunt selecteren van een of meer eigenschappen om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="cdde8-107">De **indeling** -cmdlets zijn **indeling hele**, **lijst indeling**, **Format-Table**, en **indeling-aangepaste**.</span><span class="sxs-lookup"><span data-stu-id="cdde8-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="cdde8-108">We alleen worden beschreven de **indeling hele**, **lijst indeling**, en **Format-Table** cmdlets in deze handleiding.</span><span class="sxs-lookup"><span data-stu-id="cdde8-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="cdde8-109">Elke cmdlet indeling heeft standaardeigenschappen die worden gebruikt als u geen specifieke eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="cdde8-110">Elke cmdlet maakt ook gebruik van dezelfde parameternamen, **eigenschap**om op te geven welke eigenschappen u wilt weergeven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="cdde8-111">Omdat **indeling hele** ziet u slechts één eigenschap, de **eigenschap** parameter duurt slechts één waarde, maar de Eigenschapsparameters van **lijst indeling** en **Format-Table** accepteert een lijst met namen van eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="cdde8-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="cdde8-112">Als u de opdracht **Get-Process - naam powershell** met twee exemplaren van Windows PowerShell wordt uitgevoerd, ontvangt u uitvoer die er als uitzien volgt:</span><span class="sxs-lookup"><span data-stu-id="cdde8-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="cdde8-113">In de rest van deze sectie wordt toegelicht hoe u **indeling** cmdlets voor het wijzigen van de manier waarop de uitvoer van deze opdracht wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="cdde8-114">Met behulp van de indeling hele voor één Item uitvoer</span><span class="sxs-lookup"><span data-stu-id="cdde8-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="cdde8-115">De `Format-Wide` cmdlet, wordt standaard alleen de standaardeigenschap van een object.</span><span class="sxs-lookup"><span data-stu-id="cdde8-115">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span>
<span data-ttu-id="cdde8-116">De informatie die is gekoppeld aan elk object wordt in één kolom weergegeven:</span><span class="sxs-lookup"><span data-stu-id="cdde8-116">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```output
Format-Custom                          Format-Hex
Format-List                            Format-Table
Format-Wide
```

<span data-ttu-id="cdde8-117">U kunt ook een niet-standaard-eigenschap opgeven:</span><span class="sxs-lookup"><span data-stu-id="cdde8-117">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```output
Custom                                 Hex
List                                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="cdde8-118">Indeling hele weergeven met kolom beheren</span><span class="sxs-lookup"><span data-stu-id="cdde8-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="cdde8-119">Met de `Format-Wide` cmdlet, kunt u slechts één eigenschap tegelijk weergeven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-119">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span>
<span data-ttu-id="cdde8-120">Dit maakt het handig voor het weergeven van eenvoudige lijsten die slechts één element per regel.</span><span class="sxs-lookup"><span data-stu-id="cdde8-120">This makes it useful for displaying simple lists that show only one element per line.</span></span>
<span data-ttu-id="cdde8-121">Als u een eenvoudige lijst, stel de waarde van de **kolom** parameter 1 door te typen:</span><span class="sxs-lookup"><span data-stu-id="cdde8-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="cdde8-122">Met behulp van de lijst van de indeling voor een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="cdde8-122">Using Format-List for a List View</span></span>

<span data-ttu-id="cdde8-123">De **lijst indeling** cmdlet geeft een object in de vorm van een lijst weer met elke eigenschap met het label en wordt weergegeven op een afzonderlijke regel:</span><span class="sxs-lookup"><span data-stu-id="cdde8-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="cdde8-124">U kunt zo veel eigenschappen als u wilt opgeven:</span><span class="sxs-lookup"><span data-stu-id="cdde8-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="cdde8-125">Om gedetailleerde informatie met behulp van lijst indelen met jokertekens</span><span class="sxs-lookup"><span data-stu-id="cdde8-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="cdde8-126">De **lijst indeling** cmdlet kunt u een jokerteken gebruiken als de waarde van de **eigenschap** parameter.</span><span class="sxs-lookup"><span data-stu-id="cdde8-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="cdde8-127">Hiermee kunt u gedetailleerde informatie weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-127">This lets you display detailed information.</span></span> <span data-ttu-id="cdde8-128">Objecten bevatten vaak meer gegevens dan u nodig hebt, daarom zijn Windows PowerShell wordt alle eigenschapswaarden niet standaard weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="cdde8-129">Als u alle eigenschappen van een object, gebruiken de **Format-List-eigenschap \&#42;** opdracht.</span><span class="sxs-lookup"><span data-stu-id="cdde8-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="cdde8-130">Meer dan 60 regels van de uitvoer voor een enkel proces worden gegenereerd door de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="cdde8-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="cdde8-131">Hoewel de **lijst indeling** opdracht is handig voor het weergeven van details, als u een overzicht van de uitvoer die veel objecten bevat, een eenvoudigere tabellarische weergave is het vaak nuttig.</span><span class="sxs-lookup"><span data-stu-id="cdde8-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="cdde8-132">Met behulp van de tabel opmaken voor uitvoer in tabelvorm</span><span class="sxs-lookup"><span data-stu-id="cdde8-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="cdde8-133">Als u de **Format-Table** cmdlet met geen namen van eigenschappen die zijn opgegeven om de uitvoer van de **Get-Process** opdracht, krijgt u exact dezelfde uitvoer zoals u dat wel doet zonder uit te voeren zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="cdde8-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="cdde8-134">De reden is dat processen meestal worden weergegeven in tabelvorm, omdat de meeste Windows PowerShell-objecten zijn.</span><span class="sxs-lookup"><span data-stu-id="cdde8-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="cdde8-135">Verbetering van Format-Table-uitvoer (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="cdde8-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="cdde8-136">Hoewel een tabellarische weergave handig is voor het weergeven van een groot aantal vergelijkbare informatie, kan het lastig zijn om te interpreteren als de weergave te klein voor de gegevens is.</span><span class="sxs-lookup"><span data-stu-id="cdde8-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="cdde8-137">Bijvoorbeeld, als u probeert om Procespad, -ID, naam en bedrijf weer te geven, krijgt u afgekapte uitvoer voor de Procespad en de kolom van het bedrijf:</span><span class="sxs-lookup"><span data-stu-id="cdde8-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="cdde8-138">Als u opgeeft de **AutoSize** parameter tijdens het uitvoeren van de **Format-Table** opdracht, berekent Windows PowerShell kolombreedten op basis van de werkelijke gegevens die u wilt weergeven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="cdde8-139">Dit maakt het **pad** kolom kan worden gelezen, maar de kolom bedrijf blijft afgekapt:</span><span class="sxs-lookup"><span data-stu-id="cdde8-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="cdde8-140">De **Format-Table** cmdlet mogelijk nog steeds gegevens worden afgekapt, maar dit zal alleen dit doen aan het einde van het scherm.</span><span class="sxs-lookup"><span data-stu-id="cdde8-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="cdde8-141">Eigenschappen dan de laatste weergegeven, krijgen zoveel grootte als ze nodig hebben voor hun langste gegevenselement om correct weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="cdde8-142">U kunt zien dat bedrijfsnaam weergegeven wordt, maar pad wordt afgekapt als u de locaties van wisselen **pad** en **bedrijf** in de **eigenschap** lijst met waarden:</span><span class="sxs-lookup"><span data-stu-id="cdde8-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="cdde8-143">De **Format-Table** opdracht wordt ervan uitgegaan dat de nearer is een eigenschap aan het begin van de lijst met eigenschappen, met hoe belangrijk het is.</span><span class="sxs-lookup"><span data-stu-id="cdde8-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="cdde8-144">Zo wordt geprobeerd om weer te geven van de eigenschappen dichtst bij het begin volledig.</span><span class="sxs-lookup"><span data-stu-id="cdde8-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="cdde8-145">Als de **Format-Table** opdracht kan niet alle eigenschappen weergeven, het aantal kolommen uit de weergave verwijderen en een waarschuwing wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cdde8-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="cdde8-146">U kunt dit gedrag zien als u **naam** de laatste eigenschap in de lijst:</span><span class="sxs-lookup"><span data-stu-id="cdde8-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="cdde8-147">De ID-kolom is afgebroken zodat het past binnen de vermelding in de bovenstaande uitvoer en de kolomkoppen zijn gestapeld van.</span><span class="sxs-lookup"><span data-stu-id="cdde8-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="cdde8-148">Automatisch vergroten of verkleinen van de kolommen doet niet altijd wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="cdde8-148">Automatically resizing the columns does not always do what you want.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="cdde8-149">Tekstterugloop Format-Table uitvoer in de kolommen (terugloop)</span><span class="sxs-lookup"><span data-stu-id="cdde8-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="cdde8-150">U kunt afdwingen dat lange **Format-Table** gegevens om in te verpakken in de kolom weergeven met behulp van de **verpakken** parameter.</span><span class="sxs-lookup"><span data-stu-id="cdde8-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="cdde8-151">Met behulp van de **verpakken** parameter alleen niet per se doet wat u verwacht, omdat deze standaardinstellingen gebruikt als u niet ook opgeeft **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="cdde8-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="cdde8-152">Een voordeel van het gebruik van de **verpakken** parameter op zichzelf is dat deze niet wordt vertraagd verwerking van zeer veel.</span><span class="sxs-lookup"><span data-stu-id="cdde8-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="cdde8-153">Als u een overzicht van het bestand recursieve van een grote directory-systeem uitvoert, kan lange tijd in beslag nemen en kunt u een grote hoeveelheid geheugen gebruiken voordat de eerste Uitvoeritems wordt weergegeven als u **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="cdde8-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="cdde8-154">Als u vervolgens niet betrokken zijn bij het laden van het systeem, **AutoSize** werkt goed samen met de **verpakken** parameter.</span><span class="sxs-lookup"><span data-stu-id="cdde8-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="cdde8-155">De oorspronkelijke kolommen worden altijd zoveel breedte die ze nodig hebben om weer te geven items op één regel, net zoals wanneer u opgeeft toegewezen **AutoSize** zonder de **verpakken** parameter.</span><span class="sxs-lookup"><span data-stu-id="cdde8-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="cdde8-156">Het enige verschil is dat de laatste kolom zal worden verpakt, indien nodig:</span><span class="sxs-lookup"><span data-stu-id="cdde8-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="cdde8-157">Sommige kolommen mogelijk niet weergegeven als u eerst de breedste kolommen opgeeft dus is het verstandig om op te geven van de kleinste gegevenselementen eerst.</span><span class="sxs-lookup"><span data-stu-id="cdde8-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="cdde8-158">In het volgende voorbeeld geven we de zeer grote padelement eerst en zelfs met onmiddellijke, verliezen we nog steeds de laatste **naam** kolom:</span><span class="sxs-lookup"><span data-stu-id="cdde8-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="cdde8-159">Tabeluitvoer ordenen (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="cdde8-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="cdde8-160">Is een andere handige parameter voor uitvoer in tabelvorm besturingselement **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="cdde8-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="cdde8-161">Meer in tabelvorm vermeldingen in het bijzonder mogelijk moeilijk om te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="cdde8-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="cdde8-162">De **GroupBy** parameter gegroepeerd op basis van een eigenschapswaarde uitvoer.</span><span class="sxs-lookup"><span data-stu-id="cdde8-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="cdde8-163">We kunnen bijvoorbeeld processen door bedrijf voor eenvoudiger inspectie, als de waarde van het bedrijf in de lijst in de eigenschap groeperen:</span><span class="sxs-lookup"><span data-stu-id="cdde8-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```