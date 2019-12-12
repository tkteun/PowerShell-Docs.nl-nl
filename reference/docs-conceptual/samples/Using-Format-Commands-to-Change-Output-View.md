---
ms.date: 11/22/2019
keywords: Power shell, cmdlet
title: Format-opdrachten gebruiken om de uitvoerweergave te wijzigen
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417585"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="4c216-103">Format-opdrachten gebruiken om de uitvoerweergave te wijzigen</span><span class="sxs-lookup"><span data-stu-id="4c216-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="4c216-104">Power Shell heeft een set cmdlets waarmee u kunt bepalen hoe eigenschappen voor bepaalde objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c216-104">PowerShell has a set of cmdlets that allow you to control how properties are displayed for particular objects.</span></span> <span data-ttu-id="4c216-105">De namen van alle cmdlets beginnen met de term `Format`.</span><span class="sxs-lookup"><span data-stu-id="4c216-105">The names of all the cmdlets begin with the verb `Format`.</span></span> <span data-ttu-id="4c216-106">Hiermee kunt u selecteren welke eigenschappen u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="4c216-106">They let you select which properties you want to show.</span></span>

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

<span data-ttu-id="4c216-107">In dit artikel worden de cmdlets `Format-Wide`, `Format-List`en `Format-Table` beschreven.</span><span class="sxs-lookup"><span data-stu-id="4c216-107">This article describes the `Format-Wide`, `Format-List`, and `Format-Table` cmdlets.</span></span>

<span data-ttu-id="4c216-108">Elk object type in Power Shell heeft standaard eigenschappen die worden gebruikt wanneer u niet opgeeft welke eigenschappen moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c216-108">Each object type in PowerShell has default properties that are used when you don't specify which properties to display.</span></span> <span data-ttu-id="4c216-109">Elke cmdlet gebruikt ook dezelfde **eigenschaps** parameter om op te geven welke eigenschappen u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="4c216-109">Each cmdlet also uses the same **Property** parameter to specify which properties you want to display.</span></span> <span data-ttu-id="4c216-110">Omdat `Format-Wide` slechts één eigenschap toont, neemt de **eigenschaps** parameter slechts één waarde in beslag, maar de eigenschaps parameters van `Format-List` en `Format-Table` een lijst met eigenschaps namen accepteren.</span><span class="sxs-lookup"><span data-stu-id="4c216-110">Because `Format-Wide` only shows a single property, its **Property** parameter only takes a single value, but the property parameters of `Format-List` and `Format-Table` accept a list of property names.</span></span>

<span data-ttu-id="4c216-111">In dit voor beeld toont de standaard uitvoer van `Get-Process`-cmdlet dat er twee exemplaren van Internet Explorer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c216-111">In this example, the default output of `Get-Process` cmdlet shows that we have two instances of Internet Explorer running.</span></span>

```powershell
Get-Process -Name iexplore
```

<span data-ttu-id="4c216-112">De standaard indeling voor **proces** objecten toont de eigenschappen die hier worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="4c216-112">The default format for **Process** objects displays the properties shown here:</span></span>

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="4c216-113">Indeling-breed gebruiken voor uitvoer met één item</span><span class="sxs-lookup"><span data-stu-id="4c216-113">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="4c216-114">De cmdlet `Format-Wide` geeft standaard alleen de eigenschap default van een object weer.</span><span class="sxs-lookup"><span data-stu-id="4c216-114">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="4c216-115">De gegevens die aan elk object zijn gekoppeld, worden in één kolom weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="4c216-115">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

<span data-ttu-id="4c216-116">U kunt ook een niet-standaard eigenschap opgeven:</span><span class="sxs-lookup"><span data-stu-id="4c216-116">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="4c216-117">Weer gave met volledige indeling beheren met kolom</span><span class="sxs-lookup"><span data-stu-id="4c216-117">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="4c216-118">Met de `Format-Wide` cmdlet kunt u slechts één eigenschap tegelijk weer geven.</span><span class="sxs-lookup"><span data-stu-id="4c216-118">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="4c216-119">Dit maakt het handig voor het weer geven van grote lijsten in meerdere kolommen.</span><span class="sxs-lookup"><span data-stu-id="4c216-119">This makes it useful for displaying large lists in multiple columns.</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="4c216-120">Indelings lijst gebruiken voor een lijst weergave</span><span class="sxs-lookup"><span data-stu-id="4c216-120">Using Format-List for a List View</span></span>

<span data-ttu-id="4c216-121">Met de cmdlet `Format-List` wordt een object in de vorm van een vermelding weer gegeven, waarbij elke eigenschap wordt aangeduid en op een afzonderlijke regel wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="4c216-121">The `Format-List` cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

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

<span data-ttu-id="4c216-122">U kunt zoveel eigenschappen opgeven als u wilt:</span><span class="sxs-lookup"><span data-stu-id="4c216-122">You can specify as many properties as you want:</span></span>

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

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="4c216-123">Gedetailleerde informatie ophalen met behulp van de indelings lijst met Joker tekens</span><span class="sxs-lookup"><span data-stu-id="4c216-123">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="4c216-124">Met de cmdlet `Format-List` kunt u een Joker teken gebruiken als de waarde van de **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="4c216-124">The `Format-List` cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="4c216-125">Hiermee kunt u gedetailleerde gegevens weer geven.</span><span class="sxs-lookup"><span data-stu-id="4c216-125">This lets you display detailed information.</span></span> <span data-ttu-id="4c216-126">Objecten bevatten vaak meer informatie dan u nodig hebt, waarom Power shell niet alle eigenschaps waarden standaard weergeeft.</span><span class="sxs-lookup"><span data-stu-id="4c216-126">Often, objects include more information than you need, which is why PowerShell doesn't show all property values by default.</span></span> <span data-ttu-id="4c216-127">Als u alle eigenschappen van een object wilt weer geven, gebruikt u de opdracht `Format-List -Property *`.</span><span class="sxs-lookup"><span data-stu-id="4c216-127">To show all of properties of an object, use the `Format-List -Property *` command.</span></span> <span data-ttu-id="4c216-128">Met de volgende opdracht worden meer dan 60 regels uitvoer voor één proces gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="4c216-128">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

<span data-ttu-id="4c216-129">Hoewel de `Format-List` opdracht nuttig is voor het weer geven van Details als u een overzicht wilt van de uitvoer die veel items bevat, is een eenvoudigere tabellaire weer gave vaak handiger.</span><span class="sxs-lookup"><span data-stu-id="4c216-129">Although the `Format-List` command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="4c216-130">Indelings tabel gebruiken voor tabel uitvoer</span><span class="sxs-lookup"><span data-stu-id="4c216-130">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="4c216-131">Als u de cmdlet `Format-Table` zonder eigenschaps namen hebt opgegeven om de uitvoer van de `Get-Process` opdracht op te maken, krijgt u precies dezelfde uitvoer als u zonder een `Format`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c216-131">If you use the `Format-Table` cmdlet with no property names specified to format the output of the `Get-Process` command, you get exactly the same output as you do without a `Format` cmdlet.</span></span> <span data-ttu-id="4c216-132">Standaard worden **proces** objecten in Power shell weer gegeven in tabel vorm.</span><span class="sxs-lookup"><span data-stu-id="4c216-132">By default, PowerShell displays **Process** objects in a tabular format.</span></span>

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

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="4c216-133">De indeling van de tabel uitvoer verbeteren (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="4c216-133">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="4c216-134">Hoewel een tabellarische weer gave nuttig is voor het weer geven van veel informatie, kan het lastig zijn om te interpreteren of de weer gave te smal is voor de gegevens.</span><span class="sxs-lookup"><span data-stu-id="4c216-134">Although a tabular view is useful for displaying lots of information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="4c216-135">In het vorige voor beeld wordt de uitvoer afgekapt.</span><span class="sxs-lookup"><span data-stu-id="4c216-135">In the previous example, the output is truncated.</span></span> <span data-ttu-id="4c216-136">Als u de para meter **AutoSize** opgeeft wanneer u de `Format-Table` opdracht uitvoert, worden in Power shell kolom breedten berekend op basis van de werkelijke gegevens die worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c216-136">If you specify the **AutoSize** parameter when you run the `Format-Table` command, PowerShell calculates column widths based on the actual data displayed.</span></span> <span data-ttu-id="4c216-137">Hierdoor kunnen de kolommen worden gelezen.</span><span class="sxs-lookup"><span data-stu-id="4c216-137">This makes the columns readable.</span></span>

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

<span data-ttu-id="4c216-138">De `Format-Table`-cmdlet kan echter nog steeds gegevens afkappen, maar deze worden alleen afgekapt aan het einde van het scherm.</span><span class="sxs-lookup"><span data-stu-id="4c216-138">The `Format-Table` cmdlet might still truncate data, but it only truncates at the end of the screen.</span></span> <span data-ttu-id="4c216-139">Andere eigenschappen dan de laatste die worden weer gegeven, krijgen een groot deel van de grootte, zoals ze nodig hebben voor een juiste weer gave van het langste gegevens element.</span><span class="sxs-lookup"><span data-stu-id="4c216-139">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span>

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

<span data-ttu-id="4c216-140">De `Format-Table` opdracht gaat ervan uit dat de eigenschappen worden weer gegeven in volg orde van belang.</span><span class="sxs-lookup"><span data-stu-id="4c216-140">The `Format-Table` command assumes that properties are listed in order of importance.</span></span> <span data-ttu-id="4c216-141">Hiermee wordt geprobeerd de eigenschappen die het dichtst bij het begin liggen volledig weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4c216-141">So it attempts to fully display the properties nearest the beginning.</span></span> <span data-ttu-id="4c216-142">Als met de `Format-Table` opdracht niet alle eigenschappen kunnen worden weer gegeven, worden sommige kolommen uit de weer gave verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4c216-142">If the `Format-Table` command can't display all the properties, it removes some columns from the display.</span></span> <span data-ttu-id="4c216-143">U kunt dit gedrag zien in het vorige voor beeld van de eigenschap **DependentServices** .</span><span class="sxs-lookup"><span data-stu-id="4c216-143">You can see this behavior in the **DependentServices** property previous example.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="4c216-144">Terugloop indeling-tabel uitvoer in kolommen (terugloop)</span><span class="sxs-lookup"><span data-stu-id="4c216-144">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="4c216-145">U kunt met behulp van de para meter voor langdurige `Format-Table` gegevens afdwingen in **de weergave** kolom.</span><span class="sxs-lookup"><span data-stu-id="4c216-145">You can force lengthy `Format-Table` data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="4c216-146">Het gebruik van de para meter **wrap** kan niet wat u verwacht, omdat deze standaard instellingen gebruikt als u niet ook **AutoSize**opgeeft:</span><span class="sxs-lookup"><span data-stu-id="4c216-146">Using the **Wrap** parameter may not do what you expect, since it uses default settings if you don't also specify **AutoSize**:</span></span>

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

<span data-ttu-id="4c216-147">**Het gebruik** van de para meter voor hand matig vertraagt de verwerking zeer veel.</span><span class="sxs-lookup"><span data-stu-id="4c216-147">Using the **Wrap** parameter by itself doesn't slow down processing very much.</span></span> <span data-ttu-id="4c216-148">Het gebruik van **AutoSize** voor het opmaken van een recursieve bestands vermelding van een grote mappen structuur kan echter lang duren en veel geheugen gebruiken voordat de eerste uitvoer items worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c216-148">However, using **AutoSize** to format a recursive file listing of a large directory structure can take a long time and use lots of memory before displaying the first output items.</span></span>

<span data-ttu-id="4c216-149">Als u zich geen zorgen maakt over systeem belasting, werkt **AutoSize** goed met de para meter voor de **Terugloop** .</span><span class="sxs-lookup"><span data-stu-id="4c216-149">If you aren't concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span>
<span data-ttu-id="4c216-150">De oorspronkelijke kolommen gebruiken nog steeds zoveel breedte als nodig is om items op één regel weer te geven, maar de laatste kolom wordt zo nodig verpakt.</span><span class="sxs-lookup"><span data-stu-id="4c216-150">The initial columns still use as much width as needed to display items on one line, but the final column is wrapped, if necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="4c216-151">Sommige kolommen worden mogelijk niet weer gegeven wanneer u eerst de breedste kolommen opgeeft.</span><span class="sxs-lookup"><span data-stu-id="4c216-151">Some columns may not be displayed when you specify the widest columns first.</span></span> <span data-ttu-id="4c216-152">Geef eerst de kleinste gegevens elementen op voor de beste resultaten.</span><span class="sxs-lookup"><span data-stu-id="4c216-152">For best results, specify the smallest data elements first.</span></span>

<span data-ttu-id="4c216-153">In het volgende voor beeld geven we eerst de breedste eigenschappen op.</span><span class="sxs-lookup"><span data-stu-id="4c216-153">In the following example, we specify the widest properties first.</span></span>

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

<span data-ttu-id="4c216-154">Zelfs bij het inpakken wordt de kolom laatste **id** wegge laten:</span><span class="sxs-lookup"><span data-stu-id="4c216-154">Even with wrapping, the final **Id** column is omitted:</span></span>

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

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="4c216-155">Tabel uitvoer (-GroupBy) ordenen</span><span class="sxs-lookup"><span data-stu-id="4c216-155">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="4c216-156">Een andere handige para meter voor de besturings elementen voor tabellarische uitvoer is **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="4c216-156">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="4c216-157">Het is mogelijk dat er meer gegevens in de tabel in de lijst worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="4c216-157">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="4c216-158">De **GroupBy** -parameter groepen worden uitgevoerd op basis van een eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="4c216-158">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="4c216-159">We kunnen bijvoorbeeld services groeperen op **starttype** voor een betere inspectie, waarbij de **starttype** -waarde wordt wegge laten uit de eigenschaps vermelding:</span><span class="sxs-lookup"><span data-stu-id="4c216-159">For example, we can group services by **StartType** for easier inspection, omitting the **StartType** value from the property listing:</span></span>

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
