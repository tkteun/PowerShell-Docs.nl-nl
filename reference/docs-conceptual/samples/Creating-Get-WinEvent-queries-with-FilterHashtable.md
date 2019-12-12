---
ms.date: 09/13/2019
title: Get-WinEvent-query's maken met FilterHashtable
ms.openlocfilehash: 35d18dc894d90e698b38395b79ff4cf395515909
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444385"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="504a0-102">Get-WinEvent-query's maken met FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="504a0-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="504a0-103">Zie [FilterHashTable gebruiken om gebeurtenis logboeken te filteren met Power shell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/)voor meer informatie over de oorspronkelijke blog post van 3 juni 2014 **Scripting Guy** .</span><span class="sxs-lookup"><span data-stu-id="504a0-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="504a0-104">Dit artikel is een uittreksel van het oorspronkelijke blog bericht en legt uit hoe u de **FilterHashtable** -para meter van de `Get-WinEvent`-cmdlet kunt gebruiken om gebeurtenis logboeken te filteren.</span><span class="sxs-lookup"><span data-stu-id="504a0-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="504a0-105">De cmdlet `Get-WinEvent` van Power shell is een krachtige methode voor het filteren van Windows-gebeurtenis-en Diagnostische logboeken.</span><span class="sxs-lookup"><span data-stu-id="504a0-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="504a0-106">Prestaties verbeteren wanneer een `Get-WinEvent` query de para meter **FilterHashtable** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="504a0-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="504a0-107">Wanneer u werkt met grote gebeurtenis logboeken, is het niet efficiënt om objecten naar een `Where-Object` opdracht naar de pijp lijn te verzenden.</span><span class="sxs-lookup"><span data-stu-id="504a0-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="504a0-108">Vóór Power shell 6 was de `Get-EventLog` cmdlet een andere optie om logboek gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="504a0-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="504a0-109">De volgende opdrachten zijn bijvoorbeeld inefficiënt om de logboeken van **micro soft-Windows-defragmentatie** te filteren:</span><span class="sxs-lookup"><span data-stu-id="504a0-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

<span data-ttu-id="504a0-110">De volgende opdracht maakt gebruik van een hash-tabel waarmee de prestaties worden verbeterd:</span><span class="sxs-lookup"><span data-stu-id="504a0-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="504a0-111">Blog berichten over inventarisatie</span><span class="sxs-lookup"><span data-stu-id="504a0-111">Blog posts about enumeration</span></span>

<span data-ttu-id="504a0-112">Dit artikel bevat informatie over het gebruik van opgesomde waarden in een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="504a0-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="504a0-113">Lees deze **Scripting Guy** blog-berichten voor meer informatie over inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="504a0-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="504a0-114">Als u een functie wilt maken die de opgesomde waarden retourneert, raadpleegt u [opsommingen en waarden](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span><span class="sxs-lookup"><span data-stu-id="504a0-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="504a0-115">Zie de [Scripting Guy-serie blog berichten over inventarisatie](https://devblogs.microsoft.com/scripting/?s=about+enumeration)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="504a0-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-key-value-pairs"></a><span data-ttu-id="504a0-116">Hash-tabel sleutel-waardeparen</span><span class="sxs-lookup"><span data-stu-id="504a0-116">Hash table key-value pairs</span></span>

<span data-ttu-id="504a0-117">Voor het bouwen van efficiënte query's gebruikt u de cmdlet `Get-WinEvent` met de para meter **FilterHashtable** .</span><span class="sxs-lookup"><span data-stu-id="504a0-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="504a0-118">**FilterHashtable** accepteert een hash-tabel als een filter voor het ophalen van specifieke informatie uit Windows-gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="504a0-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="504a0-119">Een hash-tabel gebruikt **sleutel-** waardeparen.</span><span class="sxs-lookup"><span data-stu-id="504a0-119">A hash table uses **key-value** pairs.</span></span> <span data-ttu-id="504a0-120">Zie voor meer informatie over hashtabellen [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="504a0-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="504a0-121">Als de **sleutel-** waardeparen zich op dezelfde regel bevinden, moeten ze worden gescheiden door een punt komma.</span><span class="sxs-lookup"><span data-stu-id="504a0-121">If the **key-value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="504a0-122">Als elk **sleutel/waarde-** paar zich op een afzonderlijke regel bevindt, hoeft u geen punt komma te koppelen.</span><span class="sxs-lookup"><span data-stu-id="504a0-122">If each **key-value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="504a0-123">Dit artikel plaatst bijvoorbeeld **sleutel-** waardeparen op afzonderlijke regels en maakt geen gebruik van punt komma's.</span><span class="sxs-lookup"><span data-stu-id="504a0-123">For example, this article places **key-value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="504a0-124">In dit voor beeld wordt gebruikgemaakt van een aantal **sleutel-** waardeparen van de **FilterHashtable** -para meter.</span><span class="sxs-lookup"><span data-stu-id="504a0-124">This sample uses several of the **FilterHashtable** parameter's **key-value** pairs.</span></span> <span data-ttu-id="504a0-125">De voltooide query bevat **LogName**, **ProviderName**, **tref woorden**, **id**en **niveau**.</span><span class="sxs-lookup"><span data-stu-id="504a0-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="504a0-126">De geaccepteerde **sleutel-** waardeparen worden weer gegeven in de volgende tabel en zijn opgenomen in de documentatie voor de para meter [Get-Wine vent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** .</span><span class="sxs-lookup"><span data-stu-id="504a0-126">The accepted **key-value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="504a0-127">De volgende tabel geeft de sleutel namen, gegevens typen en of joker tekens worden geaccepteerd voor een gegevens waarde.</span><span class="sxs-lookup"><span data-stu-id="504a0-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

|    <span data-ttu-id="504a0-128">Sleutelnaam</span><span class="sxs-lookup"><span data-stu-id="504a0-128">Key name</span></span>    | <span data-ttu-id="504a0-129">Waarde gegevens type</span><span class="sxs-lookup"><span data-stu-id="504a0-129">Value data type</span></span> | <span data-ttu-id="504a0-130">Joker tekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="504a0-130">Accepts wildcard characters?</span></span> |
| -------------- | --------------- | ---------------------------- |
| <span data-ttu-id="504a0-131">LogName</span><span class="sxs-lookup"><span data-stu-id="504a0-131">LogName</span></span>        | `<String[]>`    | <span data-ttu-id="504a0-132">Ja</span><span class="sxs-lookup"><span data-stu-id="504a0-132">Yes</span></span>                          |
| <span data-ttu-id="504a0-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="504a0-133">ProviderName</span></span>   | `<String[]>`    | <span data-ttu-id="504a0-134">Ja</span><span class="sxs-lookup"><span data-stu-id="504a0-134">Yes</span></span>                          |
| <span data-ttu-id="504a0-135">Pad</span><span class="sxs-lookup"><span data-stu-id="504a0-135">Path</span></span>           | `<String[]>`    | <span data-ttu-id="504a0-136">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-136">No</span></span>                           |
| <span data-ttu-id="504a0-137">Trefwoorden</span><span class="sxs-lookup"><span data-stu-id="504a0-137">Keywords</span></span>       | `<Long[]>`      | <span data-ttu-id="504a0-138">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-138">No</span></span>                           |
| <span data-ttu-id="504a0-139">ID</span><span class="sxs-lookup"><span data-stu-id="504a0-139">ID</span></span>             | `<Int32[]>`     | <span data-ttu-id="504a0-140">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-140">No</span></span>                           |
| <span data-ttu-id="504a0-141">Niveau</span><span class="sxs-lookup"><span data-stu-id="504a0-141">Level</span></span>          | `<Int32[]>`     | <span data-ttu-id="504a0-142">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-142">No</span></span>                           |
| <span data-ttu-id="504a0-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="504a0-143">StartTime</span></span>      | `<DateTime>`    | <span data-ttu-id="504a0-144">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-144">No</span></span>                           |
| <span data-ttu-id="504a0-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="504a0-145">EndTime</span></span>        | `<DateTime>`    | <span data-ttu-id="504a0-146">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-146">No</span></span>                           |
| <span data-ttu-id="504a0-147">Gebruikers-id</span><span class="sxs-lookup"><span data-stu-id="504a0-147">UserID</span></span>         | `<SID>`         | <span data-ttu-id="504a0-148">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-148">No</span></span>                           |
| <span data-ttu-id="504a0-149">Gegevens</span><span class="sxs-lookup"><span data-stu-id="504a0-149">Data</span></span>           | `<String[]>`    | <span data-ttu-id="504a0-150">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-150">No</span></span>                           |
| `<named-data>` | `<String[]>`    | <span data-ttu-id="504a0-151">Nee</span><span class="sxs-lookup"><span data-stu-id="504a0-151">No</span></span>                           |

<span data-ttu-id="504a0-152">De `<named-data>` sleutel vertegenwoordigt een benoemd gebeurtenis gegevens veld.</span><span class="sxs-lookup"><span data-stu-id="504a0-152">The `<named-data>` key represents a named event data field.</span></span> <span data-ttu-id="504a0-153">De perflib-gebeurtenis 1008 kan bijvoorbeeld de volgende gebeurtenis gegevens bevatten:</span><span class="sxs-lookup"><span data-stu-id="504a0-153">For example, the Perflib event 1008 can contain the following event data:</span></span>

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

<span data-ttu-id="504a0-154">Met de volgende opdracht kunt u een query uitvoeren voor deze gebeurtenissen:</span><span class="sxs-lookup"><span data-stu-id="504a0-154">You can query for these events using the following command:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> <span data-ttu-id="504a0-155">De mogelijkheid om een query uit te zoeken voor `<named-data>` is toegevoegd aan Power shell 6.</span><span class="sxs-lookup"><span data-stu-id="504a0-155">The ability to query for `<named-data>` was added in PowerShell 6.</span></span>

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="504a0-156">Een query bouwen met een hash-tabel</span><span class="sxs-lookup"><span data-stu-id="504a0-156">Building a query with a hash table</span></span>

<span data-ttu-id="504a0-157">Om de resultaten te controleren en problemen op te lossen, kunt u de hash-tabel één **sleutel/waarde-** paar tegelijk maken.</span><span class="sxs-lookup"><span data-stu-id="504a0-157">To verify results and troubleshoot problems, it helps to build the hash table one **key-value** pair at a time.</span></span> <span data-ttu-id="504a0-158">De query haalt gegevens op uit het **toepassings** logboek.</span><span class="sxs-lookup"><span data-stu-id="504a0-158">The query gets data from the **Application** log.</span></span> <span data-ttu-id="504a0-159">De hash-tabel is gelijk aan `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="504a0-159">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="504a0-160">Maak de `Get-WinEvent` query om te beginnen.</span><span class="sxs-lookup"><span data-stu-id="504a0-160">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="504a0-161">Gebruik het **sleutel-** waardepaar van de para meter **FilterHashtable** met de sleutel, **LogName**en de waarde **toepassings**.</span><span class="sxs-lookup"><span data-stu-id="504a0-161">Use the **FilterHashtable** parameter's **key-value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="504a0-162">Ga door met het samen stellen van de hash-tabel met de sleutel van de **provider** .</span><span class="sxs-lookup"><span data-stu-id="504a0-162">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="504a0-163">De **ProviderName** is de naam die wordt weer gegeven in het **bron** veld in het **Windows logboeken**.</span><span class="sxs-lookup"><span data-stu-id="504a0-163">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="504a0-164">Bijvoorbeeld **.NET runtime** in de volgende scherm afbeelding:</span><span class="sxs-lookup"><span data-stu-id="504a0-164">For example, **.NET Runtime** in the following screenshot:</span></span>

![Afbeelding van Windows-Logboeken bronnen.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="504a0-166">Werk de hash-tabel bij en neem het **sleutel-** waardepaar op met de sleutel, \* \* ProviderName en de waarde **.NET runtime**.</span><span class="sxs-lookup"><span data-stu-id="504a0-166">Update the hash table and include the **key-value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="504a0-167">Als uw query gegevens moet ophalen uit gearchiveerde gebeurtenis logboeken, gebruikt u de **pad** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="504a0-167">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="504a0-168">De waarde van het **pad** geeft het volledige pad naar het logboek bestand aan.</span><span class="sxs-lookup"><span data-stu-id="504a0-168">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="504a0-169">Zie het blog bericht van **Scripting Guy** voor meer informatie. [gebruik Power shell om opgeslagen gebeurtenis logboeken te parseren op fouten](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span><span class="sxs-lookup"><span data-stu-id="504a0-169">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="504a0-170">Opsommings waarden gebruiken in een hash-tabel</span><span class="sxs-lookup"><span data-stu-id="504a0-170">Using enumerated values in a hash table</span></span>

<span data-ttu-id="504a0-171">**Tref woorden** is de volgende sleutel in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="504a0-171">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="504a0-172">Het gegevens type **Keywords** is een matrix van het `[long]` waardetype dat een groot getal bevat.</span><span class="sxs-lookup"><span data-stu-id="504a0-172">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="504a0-173">Gebruik de volgende opdracht om de maximale waarde van `[long]`te vinden:</span><span class="sxs-lookup"><span data-stu-id="504a0-173">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="504a0-174">Voor de sleutel **tref woorden** gebruikt Power shell een getal, geen teken reeks zoals **beveiliging**.</span><span class="sxs-lookup"><span data-stu-id="504a0-174">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="504a0-175">De **sleutel woorden** worden door **Windows logboeken** als teken reeksen weer gegeven, maar de waarden worden opgesomd.</span><span class="sxs-lookup"><span data-stu-id="504a0-175">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="504a0-176">Als u in de tabel hash de sleutel **tref woorden** gebruikt met een teken reeks waarde, wordt een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="504a0-176">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="504a0-177">Open de **Windows-logboeken** en klik in het deel venster **acties** op **Huidig logboek filteren**.</span><span class="sxs-lookup"><span data-stu-id="504a0-177">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="504a0-178">De vervolg keuzelijst **tref woorden** bevat de beschik bare tref woorden, zoals wordt weer gegeven in de volgende scherm afbeelding:</span><span class="sxs-lookup"><span data-stu-id="504a0-178">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Afbeelding van Windows-Logboeken tref woorden.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="504a0-180">Gebruik de volgende opdracht om de namen van de `StandardEventKeywords`-eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="504a0-180">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="504a0-181">De opgesomde waarden worden gedocumenteerd in de **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="504a0-181">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="504a0-182">Zie [StandardEventKeywords Enumeration (Engelstalig)](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="504a0-182">For more information, see [StandardEventKeywords Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="504a0-183">De namen van de **tref woorden** en opgesomde waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="504a0-183">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="504a0-184">Naam</span><span class="sxs-lookup"><span data-stu-id="504a0-184">Name</span></span>             |  <span data-ttu-id="504a0-185">Value</span><span class="sxs-lookup"><span data-stu-id="504a0-185">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="504a0-186">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="504a0-186">AuditFailure</span></span>     | <span data-ttu-id="504a0-187">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="504a0-187">4503599627370496</span></span>  |
| <span data-ttu-id="504a0-188">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="504a0-188">AuditSuccess</span></span>     | <span data-ttu-id="504a0-189">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="504a0-189">9007199254740992</span></span>  |
| <span data-ttu-id="504a0-190">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="504a0-190">CorrelationHint2</span></span> | <span data-ttu-id="504a0-191">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="504a0-191">18014398509481984</span></span> |
| <span data-ttu-id="504a0-192">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="504a0-192">EventLogClassic</span></span>  | <span data-ttu-id="504a0-193">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="504a0-193">36028797018963968</span></span> |
| <span data-ttu-id="504a0-194">Sqm</span><span class="sxs-lookup"><span data-stu-id="504a0-194">Sqm</span></span>              | <span data-ttu-id="504a0-195">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="504a0-195">2251799813685248</span></span>  |
| <span data-ttu-id="504a0-196">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="504a0-196">WdiDiagnostic</span></span>    | <span data-ttu-id="504a0-197">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="504a0-197">1125899906842624</span></span>  |
| <span data-ttu-id="504a0-198">WdiContext</span><span class="sxs-lookup"><span data-stu-id="504a0-198">WdiContext</span></span>       | <span data-ttu-id="504a0-199">562949953421312</span><span class="sxs-lookup"><span data-stu-id="504a0-199">562949953421312</span></span>   |
| <span data-ttu-id="504a0-200">Respons tijd</span><span class="sxs-lookup"><span data-stu-id="504a0-200">ResponseTime</span></span>     | <span data-ttu-id="504a0-201">281474976710656</span><span class="sxs-lookup"><span data-stu-id="504a0-201">281474976710656</span></span>   |
| <span data-ttu-id="504a0-202">Geen</span><span class="sxs-lookup"><span data-stu-id="504a0-202">None</span></span>             | <span data-ttu-id="504a0-203">0</span><span class="sxs-lookup"><span data-stu-id="504a0-203">0</span></span>                 |

<span data-ttu-id="504a0-204">Werk de hash-tabel bij en neem het **sleutel-** waardepaar op met de sleutel, **tref woorden**en de **EventLogClassic** -opsommings waarde **36028797018963968**.</span><span class="sxs-lookup"><span data-stu-id="504a0-204">Update the hash table and include the **key-value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="504a0-205">Waarde van de eigenschap static van tref woorden (optioneel)</span><span class="sxs-lookup"><span data-stu-id="504a0-205">Keywords static property value (optional)</span></span>

<span data-ttu-id="504a0-206">De sleutel **tref woorden** wordt opgesomd, maar u kunt een statische eigenschaps naam gebruiken in de hash-tabel query.</span><span class="sxs-lookup"><span data-stu-id="504a0-206">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="504a0-207">In plaats van de geretourneerde teken reeks te gebruiken, moet de naam van de eigenschap worden geconverteerd naar een waarde met de eigenschap **Value__** .</span><span class="sxs-lookup"><span data-stu-id="504a0-207">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="504a0-208">Het volgende script maakt bijvoorbeeld gebruik van de eigenschap **Value__** .</span><span class="sxs-lookup"><span data-stu-id="504a0-208">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="504a0-209">Filteren op gebeurtenis-id</span><span class="sxs-lookup"><span data-stu-id="504a0-209">Filtering by Event Id</span></span>

<span data-ttu-id="504a0-210">Om meer specifieke gegevens te verkrijgen, worden de resultaten van de query gefilterd op **gebeurtenis-id**. Er wordt in de hash-tabel naar de **gebeurtenis-id** verwezen als sleutel **-id** en de waarde is een specifieke **gebeurtenis-id**. De **gebeurtenis-id**wordt weer gegeven in de **Windows-logboeken** . In dit voor beeld wordt **gebeurtenis-Id 1023**gebruikt.</span><span class="sxs-lookup"><span data-stu-id="504a0-210">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="504a0-211">Werk de hash-tabel bij en neem het **sleutel-** waardepaar op met de sleutel, **id** en de waarde **1023**.</span><span class="sxs-lookup"><span data-stu-id="504a0-211">Update the hash table and include the **key-value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="504a0-212">Filteren op niveau</span><span class="sxs-lookup"><span data-stu-id="504a0-212">Filtering by Level</span></span>

<span data-ttu-id="504a0-213">Gebruik de **niveau** sleutel om de resultaten verder te verfijnen en alleen gebeurtenissen toe te voegen die fouten bevatten.</span><span class="sxs-lookup"><span data-stu-id="504a0-213">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="504a0-214">**Windows logboeken** geeft het **niveau** weer als teken reeks waarden, maar ze zijn opsommings waarden.</span><span class="sxs-lookup"><span data-stu-id="504a0-214">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="504a0-215">Als u in de tabel hash de **niveau** sleutel met een teken reeks waarde gebruikt, wordt er een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="504a0-215">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="504a0-216">**Niveau** heeft waarden zoals **fout**, **waarschuwing**of **informatief**.</span><span class="sxs-lookup"><span data-stu-id="504a0-216">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="504a0-217">Gebruik de volgende opdracht om de namen van de `StandardEventLevel`-eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="504a0-217">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="504a0-218">De opgesomde waarden worden gedocumenteerd in de **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="504a0-218">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="504a0-219">Zie [StandardEventLevel Enumeration (Engelstalig)](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="504a0-219">For more information, see [StandardEventLevel Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="504a0-220">De namen van de **niveau** sleutel en opgesomde waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="504a0-220">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="504a0-221">Naam</span><span class="sxs-lookup"><span data-stu-id="504a0-221">Name</span></span>           | <span data-ttu-id="504a0-222">Value</span><span class="sxs-lookup"><span data-stu-id="504a0-222">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="504a0-223">Verbose</span><span class="sxs-lookup"><span data-stu-id="504a0-223">Verbose</span></span>        |   <span data-ttu-id="504a0-224">5</span><span class="sxs-lookup"><span data-stu-id="504a0-224">5</span></span>   |
| <span data-ttu-id="504a0-225">Ter informatie</span><span class="sxs-lookup"><span data-stu-id="504a0-225">Informational</span></span>  |   <span data-ttu-id="504a0-226">4</span><span class="sxs-lookup"><span data-stu-id="504a0-226">4</span></span>   |
| <span data-ttu-id="504a0-227">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="504a0-227">Warning</span></span>        |   <span data-ttu-id="504a0-228">3</span><span class="sxs-lookup"><span data-stu-id="504a0-228">3</span></span>   |
| <span data-ttu-id="504a0-229">Fout</span><span class="sxs-lookup"><span data-stu-id="504a0-229">Error</span></span>          |   <span data-ttu-id="504a0-230">2</span><span class="sxs-lookup"><span data-stu-id="504a0-230">2</span></span>   |
| <span data-ttu-id="504a0-231">Kritieke</span><span class="sxs-lookup"><span data-stu-id="504a0-231">Critical</span></span>       |   <span data-ttu-id="504a0-232">1</span><span class="sxs-lookup"><span data-stu-id="504a0-232">1</span></span>   |
| <span data-ttu-id="504a0-233">LogAlways</span><span class="sxs-lookup"><span data-stu-id="504a0-233">LogAlways</span></span>      |   <span data-ttu-id="504a0-234">0</span><span class="sxs-lookup"><span data-stu-id="504a0-234">0</span></span>   |

<span data-ttu-id="504a0-235">De hash-tabel voor de voltooide query bevat de sleutel, het **niveau**en de waarde **2**.</span><span class="sxs-lookup"><span data-stu-id="504a0-235">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="504a0-236">Niveau static-eigenschap in opsomming (optioneel)</span><span class="sxs-lookup"><span data-stu-id="504a0-236">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="504a0-237">De **niveau** sleutel wordt opgesomd, maar u kunt een statische eigenschaps naam in de hash-tabel query gebruiken.</span><span class="sxs-lookup"><span data-stu-id="504a0-237">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="504a0-238">In plaats van de geretourneerde teken reeks te gebruiken, moet de naam van de eigenschap worden geconverteerd naar een waarde met de eigenschap **Value__** .</span><span class="sxs-lookup"><span data-stu-id="504a0-238">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="504a0-239">Het volgende script maakt bijvoorbeeld gebruik van de eigenschap **Value__** .</span><span class="sxs-lookup"><span data-stu-id="504a0-239">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```