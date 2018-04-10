---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Format-opdrachten gebruiken om de uitvoerweergave te wijzigen
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="09e29-103">Format-opdrachten gebruiken om de uitvoerweergave te wijzigen</span><span class="sxs-lookup"><span data-stu-id="09e29-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="09e29-104">Windows PowerShell is een set cmdlets waarmee u kunt bepalen welke eigenschappen voor bepaalde objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="09e29-105">De namen van alle cmdlets beginnen met de term **indeling**.</span><span class="sxs-lookup"><span data-stu-id="09e29-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="09e29-106">Ze kunnen u selecteren van een of meer eigenschappen om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="09e29-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="09e29-107">De **indeling** -cmdlets zijn **indeling hele**, **lijst indelen**, **Format-Table**, en **indeling-aangepaste**.</span><span class="sxs-lookup"><span data-stu-id="09e29-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="09e29-108">Er wordt alleen beschreven de **indeling hele**, **lijst indelen**, en **Format-Table** cmdlets in deze handleiding.</span><span class="sxs-lookup"><span data-stu-id="09e29-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="09e29-109">Elke cmdlet indeling heeft standaardeigenschappen die worden gebruikt als u geen specifieke eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="09e29-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="09e29-110">Elke cmdlet gebruikt ook de parameternaam dezelfde **eigenschap**, om op te geven welke eigenschappen u wilt weergeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="09e29-111">Omdat **indeling hele** ziet u slechts één eigenschap, de **eigenschap** parameter duurt slechts een enkele waarde, maar de Eigenschapsparameters van **lijst indelen** en **Format-Table** accepteert een lijst met namen van eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="09e29-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="09e29-112">Als u de opdracht **Get-Process - naam powershell** met twee exemplaren van Windows PowerShell wordt uitgevoerd, beschikt u uitvoer die er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="09e29-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="09e29-113">In de rest van deze sectie wordt besproken hoe u **indeling** -cmdlets voor het wijzigen van de manier waarop de uitvoer van deze opdracht wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="09e29-114">Gebruik van de hele indeling voor één Item uitvoer</span><span class="sxs-lookup"><span data-stu-id="09e29-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="09e29-115">De **indeling hele** cmdlet, wordt standaard alleen de standaardeigenschap van een object.</span><span class="sxs-lookup"><span data-stu-id="09e29-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="09e29-116">De informatie die is gekoppeld aan elk object wordt in één kolom weergegeven:</span><span class="sxs-lookup"><span data-stu-id="09e29-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="09e29-117">U kunt ook een niet-standaard-eigenschap opgeven:</span><span class="sxs-lookup"><span data-stu-id="09e29-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="09e29-118">Indeling Wide weergeven met kolom beheren</span><span class="sxs-lookup"><span data-stu-id="09e29-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="09e29-119">Met de **indeling hele** cmdlet, kunt u slechts één eigenschap tegelijk weergeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-119">With the **Format-Wide** cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="09e29-120">Hierdoor is het nuttig voor het weergeven van eenvoudige lijsten die slechts één element per regel.</span><span class="sxs-lookup"><span data-stu-id="09e29-120">This makes it useful for displaying simple lists that show only one element per line.</span></span> <span data-ttu-id="09e29-121">Als u een eenvoudige lijst, stel de waarde van de **kolom** parameter 1 door te typen:</span><span class="sxs-lookup"><span data-stu-id="09e29-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="09e29-122">Met behulp van de lijst van de indeling voor een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="09e29-122">Using Format-List for a List View</span></span>

<span data-ttu-id="09e29-123">De **lijst indelen** cmdlet geeft een object in de vorm van een lijst weer met elke eigenschap met het label en wordt weergegeven op een afzonderlijke regel:</span><span class="sxs-lookup"><span data-stu-id="09e29-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

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

<span data-ttu-id="09e29-124">U kunt zoveel eigenschappen als u wilt opgeven:</span><span class="sxs-lookup"><span data-stu-id="09e29-124">You can specify as many properties as you want:</span></span>

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

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="09e29-125">Gedetailleerde informatie van de ophalen met behulp van de lijst indelen met jokertekens</span><span class="sxs-lookup"><span data-stu-id="09e29-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="09e29-126">De **lijst indelen** cmdlet kunt u een jokerteken gebruiken als de waarde van de **eigenschap** parameter.</span><span class="sxs-lookup"><span data-stu-id="09e29-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="09e29-127">Hiermee kunt u gedetailleerde informatie weergeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-127">This lets you display detailed information.</span></span> <span data-ttu-id="09e29-128">Objecten bevatten vaak meer gegevens dan u nodig hebt, dat is waarom Windows PowerShell biedt niet alle eigenschapswaarden standaard weergegeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="09e29-129">Als u alle eigenschappen van een object, gebruiken de **lijst indelen-eigenschap \&#42;** opdracht.</span><span class="sxs-lookup"><span data-stu-id="09e29-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="09e29-130">Meer dan 60 regels van de uitvoer voor een enkel proces worden gegenereerd door de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="09e29-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="09e29-131">Hoewel de **lijst indelen** opdracht is handig voor het weergeven van details over als u een overzicht van de uitvoer die veel objecten bevat wilt, een eenvoudigere tabelweergave is het vaak nuttig.</span><span class="sxs-lookup"><span data-stu-id="09e29-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="09e29-132">Gebruik tabel opmaken voor uitvoer in tabelvorm</span><span class="sxs-lookup"><span data-stu-id="09e29-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="09e29-133">Als u de **Format-Table** cmdlet met de eigenschapnamen van geen opgegeven voor het formatteren van de uitvoer van de **Get-Process** opdracht, krijgt u exact dezelfde uitvoer als zonder uit te voeren zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="09e29-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="09e29-134">De reden is dat processen worden gewoonlijk weergegeven in tabelvorm, omdat de meeste Windows PowerShell-objecten.</span><span class="sxs-lookup"><span data-stu-id="09e29-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="09e29-135">Verbetering van de uitvoer van de tabel opmaken (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="09e29-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="09e29-136">Hoewel een tabellarische weergave nuttig is voor het weergeven van een groot aantal vergelijkbare informatie, kan het moeilijk te interpreteren als de weergave te klein voor de gegevens is zijn.</span><span class="sxs-lookup"><span data-stu-id="09e29-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="09e29-137">Bijvoorbeeld als u probeert om weer te geven Procespad, -ID, naam en bedrijf, krijgt u ingekorte uitvoer van het Procespad van het en de kolom bedrijf:</span><span class="sxs-lookup"><span data-stu-id="09e29-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="09e29-138">Als u opgeeft de **AutoSize** parameter tijdens het uitvoeren van de **Format-Table** opdracht, berekent Windows PowerShell kolombreedte op basis van de feitelijke gegevens die u wilt weergeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="09e29-139">Hierdoor kan de **pad** kolom kan worden gelezen, maar de kolom van het bedrijf blijft ingekorte:</span><span class="sxs-lookup"><span data-stu-id="09e29-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="09e29-140">De **Format-Table** cmdlet mogelijk nog steeds gegevens afkappen, maar alleen daartoe zal aan het einde van het scherm.</span><span class="sxs-lookup"><span data-stu-id="09e29-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="09e29-141">Eigenschappen dan laatste die wordt weergegeven, krijgen zoveel grootte als ze nodig hebben voor hun langste gegevenselement goed worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="09e29-142">U kunt zien dat bedrijfsnaam weergegeven wordt, maar pad wordt afgekapt als u de locaties van wisselen **pad** en **bedrijf** in de **eigenschap** lijst met waarden:</span><span class="sxs-lookup"><span data-stu-id="09e29-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="09e29-143">De **Format-Table** opdracht wordt ervan uitgegaan dat de nearer is een eigenschap aan het begin van de lijst met eigenschappen met hoe belangrijk het is.</span><span class="sxs-lookup"><span data-stu-id="09e29-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="09e29-144">Daarom wordt geprobeerd om weer te geven van de eigenschappen dichtstbijzijnde het begin volledig.</span><span class="sxs-lookup"><span data-stu-id="09e29-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="09e29-145">Als de **Format-Table** opdracht kan niet alle eigenschappen die worden weergegeven, wordt een aantal kolommen verwijderen uit de weergave en een waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="09e29-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="09e29-146">U kunt dit gedrag zien als u **naam** de laatste eigenschap in de lijst:</span><span class="sxs-lookup"><span data-stu-id="09e29-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="09e29-147">De kolom-ID is afgekapt zodat het past binnen de vermelding in de bovenstaande uitvoer en de kolomkoppen zijn gestapeld.</span><span class="sxs-lookup"><span data-stu-id="09e29-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="09e29-148">Automatisch vergroten of verkleinen van de kolommen biedt niet altijd wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="09e29-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="09e29-149">Onmiddellijke Format-Table-uitvoer in kolommen (terugloop)</span><span class="sxs-lookup"><span data-stu-id="09e29-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="09e29-150">U kunt afdwingen langdurige **Format-Table** gegevens om in te verpakken in de kolom weergeven met behulp van de **teruglopen** parameter.</span><span class="sxs-lookup"><span data-stu-id="09e29-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="09e29-151">Met behulp van de **teruglopen** parameter alleen wordt niet per se te doen wat u verwacht, omdat deze standaardinstellingen gebruikt als u geen ook opgeeft **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="09e29-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="09e29-152">Een voordeel van het gebruik van de **teruglopen** parameter door zichzelf is dat deze niet wordt vertraagd veel verwerken.</span><span class="sxs-lookup"><span data-stu-id="09e29-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="09e29-153">Als u een overzicht van het bestand recursieve van een grote directory-systeem uitvoert, kan erg lang duren en kunt u veel geheugen gebruiken voordat de eerste Uitvoeritems wordt weergegeven als u **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="09e29-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="09e29-154">Als u vervolgens niet betrokken zijn bij de systeembelasting **AutoSize** werkt goed samen met de **teruglopen** parameter.</span><span class="sxs-lookup"><span data-stu-id="09e29-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="09e29-155">De eerste kolommen worden altijd toegewezen zoveel breedte als ze nodig hebben voor het weergeven van items op één regel, net zoals bij het opgeven van **AutoSize** zonder de **teruglopen** parameter.</span><span class="sxs-lookup"><span data-stu-id="09e29-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="09e29-156">Het enige verschil is dat de laatste kolom wordt ingepakt indien nodig:</span><span class="sxs-lookup"><span data-stu-id="09e29-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="09e29-157">Sommige kolommen mogelijk niet weergegeven als u eerst de breedste kolommen opgeven zodat u veiligste eerst de kleinste gegevenselementen opgeven.</span><span class="sxs-lookup"><span data-stu-id="09e29-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="09e29-158">In het volgende voorbeeld wordt het zeer breed padelement eerst specificeren, en zelfs met tekstterugloop, we nog steeds het uiteindelijke verliezen **naam** kolom:</span><span class="sxs-lookup"><span data-stu-id="09e29-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="09e29-159">Tabeluitvoer ordenen (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="09e29-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="09e29-160">Is een andere handige parameter voor uitvoer in tabelvorm besturingselement **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="09e29-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="09e29-161">Meer in tabelvorm aanbiedingen in het bijzonder mogelijk moeilijk te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="09e29-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="09e29-162">De **GroupBy** parameter gegroepeerd op basis van een waarde van de eigenschap uitvoer.</span><span class="sxs-lookup"><span data-stu-id="09e29-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="09e29-163">We kunnen bijvoorbeeld processen door bedrijf voor gemakkelijker inspectie als de waarde van het bedrijf van de eigenschap aanbieding weggelaten groeperen:</span><span class="sxs-lookup"><span data-stu-id="09e29-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```