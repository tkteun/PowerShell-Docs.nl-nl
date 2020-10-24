---
ms.date: 11/22/2019
keywords: powershell,cmdlet
title: Format-opdrachten gebruiken om de uitvoerweergave te wijzigen
description: Power Shell heeft een uitbreidbaar systeem waarmee u uitvoer kunt presen teren in lijsten, tabellen of aangepaste indelingen.
ms.openlocfilehash: ebb285a19c7fe1bc80608385f9e2842469e95817
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500943"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="7da6b-104">Format-opdrachten gebruiken om de uitvoerweergave te wijzigen</span><span class="sxs-lookup"><span data-stu-id="7da6b-104">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="7da6b-105">Power Shell heeft een set cmdlets waarmee u kunt bepalen hoe eigenschappen voor bepaalde objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-105">PowerShell has a set of cmdlets that allow you to control how properties are displayed for particular objects.</span></span> <span data-ttu-id="7da6b-106">De namen van alle cmdlets beginnen met de bewerking `Format` .</span><span class="sxs-lookup"><span data-stu-id="7da6b-106">The names of all the cmdlets begin with the verb `Format`.</span></span> <span data-ttu-id="7da6b-107">Hiermee kunt u selecteren welke eigenschappen u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-107">They let you select which properties you want to show.</span></span>

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

<span data-ttu-id="7da6b-108">In dit artikel worden `Format-Wide` de `Format-List` cmdlets, en en beschreven `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="7da6b-108">This article describes the `Format-Wide`, `Format-List`, and `Format-Table` cmdlets.</span></span>

<span data-ttu-id="7da6b-109">Elk object type in Power Shell heeft standaard eigenschappen die worden gebruikt wanneer u niet opgeeft welke eigenschappen moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-109">Each object type in PowerShell has default properties that are used when you don't specify which properties to display.</span></span> <span data-ttu-id="7da6b-110">Elke cmdlet gebruikt ook dezelfde **eigenschaps** parameter om op te geven welke eigenschappen u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-110">Each cmdlet also uses the same **Property** parameter to specify which properties you want to display.</span></span> <span data-ttu-id="7da6b-111">Omdat `Format-Wide` slechts één eigenschap wordt weer gegeven, gebruikt de **eigenschaps** parameter alleen één waarde, maar de eigenschaps parameters van `Format-List` en `Format-Table` accepteren een lijst met eigenschaps namen.</span><span class="sxs-lookup"><span data-stu-id="7da6b-111">Because `Format-Wide` only shows a single property, its **Property** parameter only takes a single value, but the property parameters of `Format-List` and `Format-Table` accept a list of property names.</span></span>

<span data-ttu-id="7da6b-112">In dit voor beeld toont de standaard uitvoer van de `Get-Process` cmdlet dat er twee exemplaren van Internet Explorer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7da6b-112">In this example, the default output of `Get-Process` cmdlet shows that we have two instances of Internet Explorer running.</span></span>

```powershell
Get-Process -Name iexplore
```

<span data-ttu-id="7da6b-113">De standaard indeling voor **proces** objecten toont de eigenschappen die hier worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="7da6b-113">The default format for **Process** objects displays the properties shown here:</span></span>

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="7da6b-114">Format-Wide gebruiken voor Single-Item uitvoer</span><span class="sxs-lookup"><span data-stu-id="7da6b-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="7da6b-115">De `Format-Wide` cmdlet geeft standaard alleen de eigenschap default van een object weer.</span><span class="sxs-lookup"><span data-stu-id="7da6b-115">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="7da6b-116">De gegevens die aan elk object zijn gekoppeld, worden in één kolom weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="7da6b-116">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

<span data-ttu-id="7da6b-117">U kunt ook een niet-standaard eigenschap opgeven:</span><span class="sxs-lookup"><span data-stu-id="7da6b-117">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="7da6b-118">Format-Wide weer geven met kolom</span><span class="sxs-lookup"><span data-stu-id="7da6b-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="7da6b-119">Met de `Format-Wide` cmdlet kunt u slechts één eigenschap tegelijk weer geven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-119">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="7da6b-120">Dit maakt het handig voor het weer geven van grote lijsten in meerdere kolommen.</span><span class="sxs-lookup"><span data-stu-id="7da6b-120">This makes it useful for displaying large lists in multiple columns.</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="7da6b-121">Format-List gebruiken voor een lijst weergave</span><span class="sxs-lookup"><span data-stu-id="7da6b-121">Using Format-List for a List View</span></span>

<span data-ttu-id="7da6b-122">`Format-List`Met de cmdlet wordt een object in de vorm van een vermelding weer gegeven, waarbij elke eigenschap wordt aangeduid en op een afzonderlijke regel wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="7da6b-122">The `Format-List` cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

<span data-ttu-id="7da6b-123">U kunt zoveel eigenschappen opgeven als u wilt:</span><span class="sxs-lookup"><span data-stu-id="7da6b-123">You can specify as many properties as you want:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="7da6b-124">Gedetailleerde informatie ophalen met behulp van Format-List met Joker tekens</span><span class="sxs-lookup"><span data-stu-id="7da6b-124">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="7da6b-125">`Format-List`Met de cmdlet kunt u een Joker teken gebruiken als de waarde van de **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="7da6b-125">The `Format-List` cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="7da6b-126">Hiermee kunt u gedetailleerde gegevens weer geven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-126">This lets you display detailed information.</span></span> <span data-ttu-id="7da6b-127">Objecten bevatten vaak meer informatie dan u nodig hebt, waarom Power shell niet alle eigenschaps waarden standaard weergeeft.</span><span class="sxs-lookup"><span data-stu-id="7da6b-127">Often, objects include more information than you need, which is why PowerShell doesn't show all property values by default.</span></span> <span data-ttu-id="7da6b-128">Als u alle eigenschappen van een object wilt weer geven, gebruikt u de `Format-List -Property *` opdracht.</span><span class="sxs-lookup"><span data-stu-id="7da6b-128">To show all of properties of an object, use the `Format-List -Property *` command.</span></span> <span data-ttu-id="7da6b-129">Met de volgende opdracht worden meer dan 60 regels uitvoer voor één proces gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="7da6b-129">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

<span data-ttu-id="7da6b-130">Hoewel de `Format-List` opdracht handig is om details weer te geven. Als u een overzicht wilt van de uitvoer die veel items bevat, is een eenvoudigere tabellaire weer gave vaak handiger.</span><span class="sxs-lookup"><span data-stu-id="7da6b-130">Although the `Format-List` command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="7da6b-131">Format-Table gebruiken voor tabel uitvoer</span><span class="sxs-lookup"><span data-stu-id="7da6b-131">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="7da6b-132">Als u de cmdlet gebruikt zonder `Format-Table` eigenschaps namen die zijn opgegeven om de uitvoer van de opdracht op te maken `Get-Process` , krijgt u precies dezelfde uitvoer als u zonder een `Format` cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7da6b-132">If you use the `Format-Table` cmdlet with no property names specified to format the output of the `Get-Process` command, you get exactly the same output as you do without a `Format` cmdlet.</span></span> <span data-ttu-id="7da6b-133">Standaard worden **proces** objecten in Power shell weer gegeven in tabel vorm.</span><span class="sxs-lookup"><span data-stu-id="7da6b-133">By default, PowerShell displays **Process** objects in a tabular format.</span></span>

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="7da6b-134">Format-Table-uitvoer verbeteren (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="7da6b-134">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="7da6b-135">Hoewel een tabellarische weer gave nuttig is voor het weer geven van veel informatie, kan het lastig zijn om te interpreteren of de weer gave te smal is voor de gegevens.</span><span class="sxs-lookup"><span data-stu-id="7da6b-135">Although a tabular view is useful for displaying lots of information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="7da6b-136">In het vorige voor beeld wordt de uitvoer afgekapt.</span><span class="sxs-lookup"><span data-stu-id="7da6b-136">In the previous example, the output is truncated.</span></span> <span data-ttu-id="7da6b-137">Als u de para meter **AutoSize** opgeeft wanneer u de `Format-Table` opdracht uitvoert, worden in Power shell kolom breedten berekend op basis van de werkelijke gegevens die worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-137">If you specify the **AutoSize** parameter when you run the `Format-Table` command, PowerShell calculates column widths based on the actual data displayed.</span></span> <span data-ttu-id="7da6b-138">Hierdoor kunnen de kolommen worden gelezen.</span><span class="sxs-lookup"><span data-stu-id="7da6b-138">This makes the columns readable.</span></span>

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

<span data-ttu-id="7da6b-139">De `Format-Table` cmdlet kan echter nog steeds gegevens afkappen, maar deze worden alleen afgekapt aan het einde van het scherm.</span><span class="sxs-lookup"><span data-stu-id="7da6b-139">The `Format-Table` cmdlet might still truncate data, but it only truncates at the end of the screen.</span></span> <span data-ttu-id="7da6b-140">Andere eigenschappen dan de laatste die worden weer gegeven, krijgen een groot deel van de grootte, zoals ze nodig hebben voor een juiste weer gave van het langste gegevens element.</span><span class="sxs-lookup"><span data-stu-id="7da6b-140">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="7da6b-141">De `Format-Table` opdracht gaat ervan uit dat de eigenschappen worden weer gegeven in volg orde van belang.</span><span class="sxs-lookup"><span data-stu-id="7da6b-141">The `Format-Table` command assumes that properties are listed in order of importance.</span></span> <span data-ttu-id="7da6b-142">Hiermee wordt geprobeerd de eigenschappen die het dichtst bij het begin liggen volledig weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-142">So it attempts to fully display the properties nearest the beginning.</span></span> <span data-ttu-id="7da6b-143">Als `Format-Table` met de opdracht niet alle eigenschappen kunnen worden weer gegeven, worden er een aantal kolommen uit de weer gave verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7da6b-143">If the `Format-Table` command can't display all the properties, it removes some columns from the display.</span></span> <span data-ttu-id="7da6b-144">U kunt dit gedrag zien in het vorige voor beeld van de eigenschap **DependentServices** .</span><span class="sxs-lookup"><span data-stu-id="7da6b-144">You can see this behavior in the **DependentServices** property previous example.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="7da6b-145">Format-Table uitvoer in kolommen (terugloop) inpakken</span><span class="sxs-lookup"><span data-stu-id="7da6b-145">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="7da6b-146">`Format-Table`Met de para meter voor de **Terugloop** kunt u de hoeveelheid gegevens die in de weergave kolom loopt, afdwingen.</span><span class="sxs-lookup"><span data-stu-id="7da6b-146">You can force lengthy `Format-Table` data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="7da6b-147">Het gebruik van de para meter **wrap** kan niet wat u verwacht, omdat deze standaard instellingen gebruikt als u niet ook **AutoSize**opgeeft:</span><span class="sxs-lookup"><span data-stu-id="7da6b-147">Using the **Wrap** parameter may not do what you expect, since it uses default settings if you don't also specify **AutoSize**:</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="7da6b-148">**Het gebruik** van de para meter voor hand matig vertraagt de verwerking zeer veel.</span><span class="sxs-lookup"><span data-stu-id="7da6b-148">Using the **Wrap** parameter by itself doesn't slow down processing very much.</span></span> <span data-ttu-id="7da6b-149">Het gebruik van **AutoSize** voor het opmaken van een recursieve bestands vermelding van een grote mappen structuur kan echter lang duren en veel geheugen gebruiken voordat de eerste uitvoer items worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7da6b-149">However, using **AutoSize** to format a recursive file listing of a large directory structure can take a long time and use lots of memory before displaying the first output items.</span></span>

<span data-ttu-id="7da6b-150">Als u zich geen zorgen maakt over systeem belasting, werkt **AutoSize** goed met de para meter voor de **Terugloop** .</span><span class="sxs-lookup"><span data-stu-id="7da6b-150">If you aren't concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span>
<span data-ttu-id="7da6b-151">De oorspronkelijke kolommen gebruiken nog steeds zoveel breedte als nodig is om items op één regel weer te geven, maar de laatste kolom wordt zo nodig verpakt.</span><span class="sxs-lookup"><span data-stu-id="7da6b-151">The initial columns still use as much width as needed to display items on one line, but the final column is wrapped, if necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="7da6b-152">Sommige kolommen worden mogelijk niet weer gegeven wanneer u eerst de breedste kolommen opgeeft.</span><span class="sxs-lookup"><span data-stu-id="7da6b-152">Some columns may not be displayed when you specify the widest columns first.</span></span> <span data-ttu-id="7da6b-153">Geef eerst de kleinste gegevens elementen op voor de beste resultaten.</span><span class="sxs-lookup"><span data-stu-id="7da6b-153">For best results, specify the smallest data elements first.</span></span>

<span data-ttu-id="7da6b-154">In het volgende voor beeld geven we eerst de breedste eigenschappen op.</span><span class="sxs-lookup"><span data-stu-id="7da6b-154">In the following example, we specify the widest properties first.</span></span>

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

<span data-ttu-id="7da6b-155">Zelfs bij het inpakken wordt de kolom laatste **id** wegge laten:</span><span class="sxs-lookup"><span data-stu-id="7da6b-155">Even with wrapping, the final **Id** column is omitted:</span></span>

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="7da6b-156">Tabel uitvoer (-GroupBy) ordenen</span><span class="sxs-lookup"><span data-stu-id="7da6b-156">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="7da6b-157">Een andere handige para meter voor de besturings elementen voor tabellarische uitvoer is **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="7da6b-157">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="7da6b-158">Het is mogelijk dat er meer gegevens in de tabel in de lijst worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="7da6b-158">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="7da6b-159">De **GroupBy** -parameter groepen worden uitgevoerd op basis van een eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="7da6b-159">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="7da6b-160">We kunnen bijvoorbeeld services groeperen op **starttype** voor een betere inspectie, waarbij de **starttype** -waarde wordt wegge laten uit de eigenschaps vermelding:</span><span class="sxs-lookup"><span data-stu-id="7da6b-160">For example, we can group services by **StartType** for easier inspection, omitting the **StartType** value from the property listing:</span></span>

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
