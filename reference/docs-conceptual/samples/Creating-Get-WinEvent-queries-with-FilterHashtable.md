---
ms.date: 3/18/2019
title: Het maken van Get-WinEvent-query's met FilterHashtable
ms.openlocfilehash: fae01cc8be5c1805e2aae008e1f21ed387efa325
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320486"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="047bd-102">Het maken van Get-WinEvent-query's met FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="047bd-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="047bd-103">Lezen van de oorspronkelijke juni 3 2014 **Scripting Guy** blog post, Zie [gebruik FilterHashTable naar Filter gebeurtenislogboek met PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span><span class="sxs-lookup"><span data-stu-id="047bd-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="047bd-104">In dit artikel is een fragment van de oorspronkelijke blogpost en wordt uitgelegd hoe u de `Get-WinEvent` van de cmdlet **FilterHashtable** parameter voor het filteren van gebeurtenislogboeken.</span><span class="sxs-lookup"><span data-stu-id="047bd-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="047bd-105">De PowerShell `Get-WinEvent` cmdlet is een krachtige methode voor het filteren van Windows-gebeurtenissen en logboeken met diagnostische gegevens.</span><span class="sxs-lookup"><span data-stu-id="047bd-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="047bd-106">Verbetert de prestaties wanneer een `Get-WinEvent` query gebruikt de **FilterHashtable** parameter.</span><span class="sxs-lookup"><span data-stu-id="047bd-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="047bd-107">Wanneer u met grote gebeurtenislogboeken werkt, is het niet efficiënt voor het verzenden van objecten in de pijplijn in een `Where-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="047bd-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="047bd-108">Voorafgaand aan PowerShell 6, de `Get-EventLog` cmdlet is een andere optie om op te halen van logboekgegevens.</span><span class="sxs-lookup"><span data-stu-id="047bd-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="047bd-109">De volgende opdrachten zijn bijvoorbeeld inefficiënt filter de **Microsoft-Windows-defragmentatie** Logboeken:</span><span class="sxs-lookup"><span data-stu-id="047bd-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="047bd-110">De volgende opdracht maakt gebruik van een hash-tabel waarmee de prestaties worden verbeterd:</span><span class="sxs-lookup"><span data-stu-id="047bd-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

### <a name="blog-posts-about-enumeration"></a><span data-ttu-id="047bd-111">Blogberichten over de opsomming</span><span class="sxs-lookup"><span data-stu-id="047bd-111">Blog posts about enumeration</span></span>

<span data-ttu-id="047bd-112">In dit artikel bevat informatie over het gebruik van vaste waarden in een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="047bd-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="047bd-113">Lees voor meer informatie over opsomming deze **Scripting Guy** blogberichten.</span><span class="sxs-lookup"><span data-stu-id="047bd-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="047bd-114">Zie voor het maken van een functie waarmee de opsommingswaarden worden geretourneerd, [opsommingen en waarden](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span><span class="sxs-lookup"><span data-stu-id="047bd-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="047bd-115">Zie voor meer informatie de [Scripting Guy blog reeks blogberichten over opsomming](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="047bd-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

### <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="047bd-116">Hash-tabel sleutel/waarde-paren</span><span class="sxs-lookup"><span data-stu-id="047bd-116">Hash table key/value pairs</span></span>

<span data-ttu-id="047bd-117">Voor het bouwen van efficiënte query's, gebruikt u de `Get-WinEvent` cmdlet met de **FilterHashtable** parameter.</span><span class="sxs-lookup"><span data-stu-id="047bd-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="047bd-118">**FilterHashtable** accepteert van een hash-tabel als een filter voor specifieke informatie uit Windows-gebeurtenislogboeken.</span><span class="sxs-lookup"><span data-stu-id="047bd-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="047bd-119">Maakt gebruik van een hash-tabel **sleutel/waarde** paren.</span><span class="sxs-lookup"><span data-stu-id="047bd-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="047bd-120">Zie voor meer informatie over hashtabellen [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="047bd-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="047bd-121">Als de **sleutel/waarde** paren zijn op dezelfde regel, ze moeten worden gescheiden door puntkomma's.</span><span class="sxs-lookup"><span data-stu-id="047bd-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="047bd-122">Als elke **sleutel/waarde** paar is op een afzonderlijke regel, de puntkomma is niet nodig.</span><span class="sxs-lookup"><span data-stu-id="047bd-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="047bd-123">Bijvoorbeeld: in dit artikel wordt geplaatst **sleutel/waarde** paren op afzonderlijke regels en geen gebruik maakt van puntkomma's.</span><span class="sxs-lookup"><span data-stu-id="047bd-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="047bd-124">In dit voorbeeld maakt gebruik van verschillende van de **FilterHashtable** van de parameter **sleutel/waarde** paren.</span><span class="sxs-lookup"><span data-stu-id="047bd-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="047bd-125">De voltooide query bevat **logboeknaam**, **ProviderName**, **trefwoorden**, **ID**, en **niveau**.</span><span class="sxs-lookup"><span data-stu-id="047bd-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="047bd-126">De geaccepteerde **sleutel/waarde** paren in de volgende tabel worden weergegeven en worden opgenomen in de documentatie voor de [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** de parameter.</span><span class="sxs-lookup"><span data-stu-id="047bd-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="047bd-127">De volgende tabel bevat de namen van sleutels, gegevenstypen, en of de jokertekens voor een gegevenswaarde worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="047bd-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="047bd-128">Sleutelnaam</span><span class="sxs-lookup"><span data-stu-id="047bd-128">Key name</span></span>     | <span data-ttu-id="047bd-129">Gegevenstype</span><span class="sxs-lookup"><span data-stu-id="047bd-129">Value data type</span></span>    | <span data-ttu-id="047bd-130">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="047bd-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="047bd-131">LogName</span><span class="sxs-lookup"><span data-stu-id="047bd-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="047bd-132">Ja</span><span class="sxs-lookup"><span data-stu-id="047bd-132">Yes</span></span> |
| <span data-ttu-id="047bd-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="047bd-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="047bd-134">Ja</span><span class="sxs-lookup"><span data-stu-id="047bd-134">Yes</span></span> |
| <span data-ttu-id="047bd-135">Pad</span><span class="sxs-lookup"><span data-stu-id="047bd-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="047bd-136">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-136">No</span></span>  |
| <span data-ttu-id="047bd-137">Trefwoorden</span><span class="sxs-lookup"><span data-stu-id="047bd-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="047bd-138">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-138">No</span></span>  |
| <span data-ttu-id="047bd-139">ID</span><span class="sxs-lookup"><span data-stu-id="047bd-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="047bd-140">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-140">No</span></span>  |
| <span data-ttu-id="047bd-141">Niveau</span><span class="sxs-lookup"><span data-stu-id="047bd-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="047bd-142">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-142">No</span></span>  |
| <span data-ttu-id="047bd-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="047bd-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="047bd-144">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-144">No</span></span>  |
| <span data-ttu-id="047bd-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="047bd-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="047bd-146">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-146">No</span></span>  |
| <span data-ttu-id="047bd-147">Gebruikers-id</span><span class="sxs-lookup"><span data-stu-id="047bd-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="047bd-148">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-148">No</span></span>  |
| <span data-ttu-id="047bd-149">Gegevens</span><span class="sxs-lookup"><span data-stu-id="047bd-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="047bd-150">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="047bd-151">Nee</span><span class="sxs-lookup"><span data-stu-id="047bd-151">No</span></span>  |

### <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="047bd-152">Het bouwen van een query met een hash-tabel</span><span class="sxs-lookup"><span data-stu-id="047bd-152">Building a query with a hash table</span></span>

<span data-ttu-id="047bd-153">Resultaten controleren en problemen oplossen, is het handig om het bouwen van de hash-tabel een **sleutel/waarde** paar op een tijdstip.</span><span class="sxs-lookup"><span data-stu-id="047bd-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="047bd-154">De query haalt gegevens uit de **toepassing** log.</span><span class="sxs-lookup"><span data-stu-id="047bd-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="047bd-155">De hash-tabel is gelijk aan `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="047bd-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="047bd-156">Als u wilt, maakt de `Get-WinEvent` query.</span><span class="sxs-lookup"><span data-stu-id="047bd-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="047bd-157">Gebruik de **FilterHashtable** van de parameter **sleutel/waarde** koppelen aan de sleutel **logboeknaam**, en de waarde **toepassing**.</span><span class="sxs-lookup"><span data-stu-id="047bd-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="047bd-158">Doorgaan met het bouwen van de hash-tabel met de **ProviderName** sleutel.</span><span class="sxs-lookup"><span data-stu-id="047bd-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="047bd-159">De **ProviderName** is de naam die wordt weergegeven in de **bron** veld in de **Windows logboeken**.</span><span class="sxs-lookup"><span data-stu-id="047bd-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="047bd-160">Bijvoorbeeld, **.NET Runtime** in de volgende schermafbeelding:</span><span class="sxs-lookup"><span data-stu-id="047bd-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Afbeelding van Logboeken van Windows-bronnen.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="047bd-162">De hash-tabel bijwerken en bevatten de **sleutel/waarde** koppelen aan de sleutel \*\* ProviderName, en de waarde **.NET Runtime**.</span><span class="sxs-lookup"><span data-stu-id="047bd-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="047bd-163">Als de query gegevens ophalen uit de gearchiveerde gebeurtenislogboeken moet, gebruikt u de **pad** sleutel.</span><span class="sxs-lookup"><span data-stu-id="047bd-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="047bd-164">De **pad** waarde geeft het volledige pad naar het logboekbestand.</span><span class="sxs-lookup"><span data-stu-id="047bd-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="047bd-165">Zie voor meer informatie de **Scripting Guy** blogbericht, [Gebruik PowerShell om te parseren opgeslagen gebeurtenislogboeken voor fouten](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span><span class="sxs-lookup"><span data-stu-id="047bd-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

### <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="047bd-166">Met behulp van de opsommingswaarden zijn in een hash-tabel</span><span class="sxs-lookup"><span data-stu-id="047bd-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="047bd-167">**Trefwoorden** is de volgende sleutel in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="047bd-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="047bd-168">De **trefwoorden** gegevenstype is een matrix met de `[long]` waardetype die een groot aantal bevat.</span><span class="sxs-lookup"><span data-stu-id="047bd-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="047bd-169">Gebruik de volgende opdracht te vinden van de maximale waarde van `[long]`:</span><span class="sxs-lookup"><span data-stu-id="047bd-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="047bd-170">Voor de **trefwoorden** sleutel, PowerShell maakt gebruik van een getal, niet een tekenreeks, zoals **Security**.</span><span class="sxs-lookup"><span data-stu-id="047bd-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="047bd-171">**Windows-logboeken** geeft de **trefwoorden** als tekenreeksen, maar ze zijn opsommingswaarden zijn.</span><span class="sxs-lookup"><span data-stu-id="047bd-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="047bd-172">In de hashtabel, als u de **trefwoorden** sleutel met een string-waarde, een foutbericht wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="047bd-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="047bd-173">Open de **Windows logboeken** en van de **acties** deelvenster, klikt u op **Huidig logboek filteren**.</span><span class="sxs-lookup"><span data-stu-id="047bd-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="047bd-174">De **trefwoorden** vervolgkeuzelijst geeft de beschikbare trefwoorden, zoals wordt weergegeven in de volgende schermafbeelding:</span><span class="sxs-lookup"><span data-stu-id="047bd-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Afbeelding van Windows-Logboeken trefwoorden.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="047bd-176">Gebruik de volgende opdracht om weer te geven de `StandardEventKeywords` namen van eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="047bd-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="047bd-177">De opsommingswaarden worden beschreven in de **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="047bd-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="047bd-178">Zie voor meer informatie, [StandardEventKeywords opsomming](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="047bd-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="047bd-179">De **trefwoorden** namen en opsommingswaarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="047bd-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="047bd-180">Naam</span><span class="sxs-lookup"><span data-stu-id="047bd-180">Name</span></span>             |  <span data-ttu-id="047bd-181">Waarde</span><span class="sxs-lookup"><span data-stu-id="047bd-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="047bd-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="047bd-182">AuditFailure</span></span>     | <span data-ttu-id="047bd-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="047bd-183">4503599627370496</span></span>  |
| <span data-ttu-id="047bd-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="047bd-184">AuditSuccess</span></span>     | <span data-ttu-id="047bd-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="047bd-185">9007199254740992</span></span>  |
| <span data-ttu-id="047bd-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="047bd-186">CorrelationHint2</span></span> | <span data-ttu-id="047bd-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="047bd-187">18014398509481984</span></span> |
| <span data-ttu-id="047bd-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="047bd-188">EventLogClassic</span></span>  | <span data-ttu-id="047bd-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="047bd-189">36028797018963968</span></span> |
| <span data-ttu-id="047bd-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="047bd-190">Sqm</span></span>              | <span data-ttu-id="047bd-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="047bd-191">2251799813685248</span></span>  |
| <span data-ttu-id="047bd-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="047bd-192">WdiDiagnostic</span></span>    | <span data-ttu-id="047bd-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="047bd-193">1125899906842624</span></span>  |
| <span data-ttu-id="047bd-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="047bd-194">WdiContext</span></span>       | <span data-ttu-id="047bd-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="047bd-195">562949953421312</span></span>   |
| <span data-ttu-id="047bd-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="047bd-196">ResponseTime</span></span>     | <span data-ttu-id="047bd-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="047bd-197">281474976710656</span></span>   |
| <span data-ttu-id="047bd-198">Geen</span><span class="sxs-lookup"><span data-stu-id="047bd-198">None</span></span>             | <span data-ttu-id="047bd-199">0</span><span class="sxs-lookup"><span data-stu-id="047bd-199">0</span></span>                 |

<span data-ttu-id="047bd-200">De hash-tabel bijwerken en bevatten de **sleutel/waarde** koppelen aan de sleutel **trefwoorden**, en de **EventLogClassic** -opsommingswaarde, **36028797018963968** .</span><span class="sxs-lookup"><span data-stu-id="047bd-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

#### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="047bd-201">Trefwoorden statische eigenschapswaarde (optioneel)</span><span class="sxs-lookup"><span data-stu-id="047bd-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="047bd-202">De **trefwoorden** sleutel wordt opgesomd, maar kunt u de naam van een statische eigenschap in de query van hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="047bd-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="047bd-203">In plaats van de tekenreeks wordt geretourneerd, de eigenschapsnaam moet worden geconverteerd naar een waarde met de **Value__** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="047bd-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="047bd-204">Bijvoorbeeld, het volgende script maakt gebruik van de **Value__** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="047bd-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

### <a name="filtering-by-event-id"></a><span data-ttu-id="047bd-205">Filteren op gebeurtenis-Id</span><span class="sxs-lookup"><span data-stu-id="047bd-205">Filtering by Event Id</span></span>

<span data-ttu-id="047bd-206">Als u gedetailleerdere gegevens, van de query resultaten worden gefilterd op **gebeurtenis-Id**. De **gebeurtenis-Id** wordt verwezen in de hash-tabel als de sleutel **ID** en de waarde is een specifieke **gebeurtenis-Id**. De **Windows logboeken** geeft de **gebeurtenis-Id**. In dit voorbeeld wordt **gebeurtenis-Id 1023**.</span><span class="sxs-lookup"><span data-stu-id="047bd-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="047bd-207">De hash-tabel bijwerken en bevatten de **sleutel/waarde** koppelen aan de sleutel **ID** en de waarde **1023**.</span><span class="sxs-lookup"><span data-stu-id="047bd-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

### <a name="filtering-by-level"></a><span data-ttu-id="047bd-208">Filteren op niveau</span><span class="sxs-lookup"><span data-stu-id="047bd-208">Filtering by Level</span></span>

<span data-ttu-id="047bd-209">Om verder te verfijnen van de resultaten en alleen de gebeurtenissen die fouten bevatten, gebruikt u de **niveau** sleutel.</span><span class="sxs-lookup"><span data-stu-id="047bd-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="047bd-210">**Windows-logboeken** geeft de **niveau** als tekenreekswaarden, maar ze zijn opsommingswaarden zijn.</span><span class="sxs-lookup"><span data-stu-id="047bd-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="047bd-211">In de hashtabel, als u de **niveau** sleutel met een string-waarde, een foutbericht wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="047bd-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="047bd-212">**Niveau** heeft waarden zoals **fout**, **waarschuwing**, of **ter informatie**.</span><span class="sxs-lookup"><span data-stu-id="047bd-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="047bd-213">Gebruik de volgende opdracht om weer te geven de `StandardEventLevel` namen van eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="047bd-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="047bd-214">De opsommingswaarden worden beschreven in de **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="047bd-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="047bd-215">Zie voor meer informatie, [StandardEventLevel opsomming](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="047bd-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="047bd-216">De **niveau** de namen van de sleutel en de opsommingswaarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="047bd-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="047bd-217">Naam</span><span class="sxs-lookup"><span data-stu-id="047bd-217">Name</span></span>           | <span data-ttu-id="047bd-218">Waarde</span><span class="sxs-lookup"><span data-stu-id="047bd-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="047bd-219">Verbose</span><span class="sxs-lookup"><span data-stu-id="047bd-219">Verbose</span></span>        |   <span data-ttu-id="047bd-220">5</span><span class="sxs-lookup"><span data-stu-id="047bd-220">5</span></span>   |
| <span data-ttu-id="047bd-221">Ter informatie</span><span class="sxs-lookup"><span data-stu-id="047bd-221">Informational</span></span>  |   <span data-ttu-id="047bd-222">4</span><span class="sxs-lookup"><span data-stu-id="047bd-222">4</span></span>   |
| <span data-ttu-id="047bd-223">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="047bd-223">Warning</span></span>        |   <span data-ttu-id="047bd-224">3</span><span class="sxs-lookup"><span data-stu-id="047bd-224">3</span></span>   |
| <span data-ttu-id="047bd-225">Fout</span><span class="sxs-lookup"><span data-stu-id="047bd-225">Error</span></span>          |   <span data-ttu-id="047bd-226">2</span><span class="sxs-lookup"><span data-stu-id="047bd-226">2</span></span>   |
| <span data-ttu-id="047bd-227">Kritieke</span><span class="sxs-lookup"><span data-stu-id="047bd-227">Critical</span></span>       |   <span data-ttu-id="047bd-228">1</span><span class="sxs-lookup"><span data-stu-id="047bd-228">1</span></span>   |
| <span data-ttu-id="047bd-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="047bd-229">LogAlways</span></span>      |   <span data-ttu-id="047bd-230">0</span><span class="sxs-lookup"><span data-stu-id="047bd-230">0</span></span>   |

<span data-ttu-id="047bd-231">De hashtabel voor de voltooide query bevat de sleutel **niveau**, en de waarde **2**.</span><span class="sxs-lookup"><span data-stu-id="047bd-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

#### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="047bd-232">Statische eigenschap in de opsomming is (optioneel)</span><span class="sxs-lookup"><span data-stu-id="047bd-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="047bd-233">De **niveau** sleutel wordt opgesomd, maar kunt u de naam van een statische eigenschap in de query van hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="047bd-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="047bd-234">In plaats van de tekenreeks wordt geretourneerd, de eigenschapsnaam moet worden geconverteerd naar een waarde met de **Value__** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="047bd-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="047bd-235">Bijvoorbeeld, het volgende script maakt gebruik van de **Value__** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="047bd-235">For example, the following script uses the **Value__** property.</span></span>

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