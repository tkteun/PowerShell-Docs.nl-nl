---
title: Opmaak, aliassen, providers, vergelijking
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: Dit hoofd stuk bevat een inleiding tot de concepten van uitvoer opmaak, opdracht aliassen, providers en vergelijkings bewerkingen.
ms.openlocfilehash: efe70d2d220f8451e781603b6000c3553dda910c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501606"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a><span data-ttu-id="f20ce-103">Hoofd stuk 5: opmaak, aliassen, providers, vergelijking</span><span class="sxs-lookup"><span data-stu-id="f20ce-103">Chapter 5 - Formatting, aliases, providers, comparison</span></span>

## <a name="requirements"></a><span data-ttu-id="f20ce-104">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f20ce-104">Requirements</span></span>

<span data-ttu-id="f20ce-105">De SQL Server Power shell-module is vereist voor enkele van de voor beelden die in dit hoofd stuk worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f20ce-105">The SQL Server PowerShell module is required by some of the examples shown in this chapter.</span></span> <span data-ttu-id="f20ce-106">De module wordt geïnstalleerd als onderdeel van [SQL Server Management Studio (smss)][SMSS].</span><span class="sxs-lookup"><span data-stu-id="f20ce-106">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="f20ce-107">Het wordt ook gebruikt in volgende hoofd stukken.</span><span class="sxs-lookup"><span data-stu-id="f20ce-107">It's also used in subsequent chapters.</span></span> <span data-ttu-id="f20ce-108">Down load en installeer dit op uw computer met Windows 10 lab-omgeving.</span><span class="sxs-lookup"><span data-stu-id="f20ce-108">Download and install it on your Windows 10 lab environment computer.</span></span>

## <a name="format-right"></a><span data-ttu-id="f20ce-109">Rechts Format teren</span><span class="sxs-lookup"><span data-stu-id="f20ce-109">Format Right</span></span>

<span data-ttu-id="f20ce-110">In hoofd stuk 4 hebt u geleerd om zoveel mogelijk naar links te filteren.</span><span class="sxs-lookup"><span data-stu-id="f20ce-110">In Chapter 4, you learned to filter as far to the left as possible.</span></span> <span data-ttu-id="f20ce-111">De regel voor het hand matig Format teren van de uitvoer van een opdracht is vergelijkbaar met die regel, behalve dat deze zoveel mogelijk moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f20ce-111">The rule for manually formatting a command's output is similar to that rule except it needs to occur as far to the right as possible.</span></span>

<span data-ttu-id="f20ce-112">De meest voorkomende indelings opdrachten zijn `Format-Table` en `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="f20ce-112">The most common format commands are `Format-Table` and `Format-List`.</span></span> <span data-ttu-id="f20ce-113">`Format-Wide` en `Format-Custom` kunnen ook worden gebruikt, maar zijn minder gangbaar.</span><span class="sxs-lookup"><span data-stu-id="f20ce-113">`Format-Wide` and `Format-Custom` can also be used, but are less common.</span></span>

<span data-ttu-id="f20ce-114">Zoals vermeld in hoofd stuk 3, wordt een opdracht die meer dan vier eigenschappen retourneert, standaard ingesteld op een lijst, tenzij aangepaste opmaak wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f20ce-114">As mentioned in Chapter 3, a command that returns more than four properties defaults to a list unless custom formatting is used.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="f20ce-115">Gebruik de `Format-Table` cmdlet om de opmaak hand matig te overschrijven en de uitvoer in een tabel in plaats van een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f20ce-115">Use the `Format-Table` cmdlet to manually override the formatting and show the output in a table instead of a list.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

<span data-ttu-id="f20ce-116">De standaard uitvoer voor `Get-Service` is drie eigenschappen in een tabel.</span><span class="sxs-lookup"><span data-stu-id="f20ce-116">The default output for `Get-Service` is three properties in a table.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="f20ce-117">Gebruik de `Format-List` cmdlet om de standaard opmaak te overschrijven en de resultaten in een lijst te retour neren.</span><span class="sxs-lookup"><span data-stu-id="f20ce-117">Use the `Format-List` cmdlet to override the default formatting and return the results in a list.</span></span>

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

<span data-ttu-id="f20ce-118">U ziet dat er gewoon pijpleidingen `Get-Service` worden `Format-List` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f20ce-118">Notice that simply piping `Get-Service` to `Format-List` made it return additional properties.</span></span> <span data-ttu-id="f20ce-119">Dit gebeurt niet bij elke opdracht vanwege de manier waarop de opmaak voor die bepaalde opdracht achter de schermen is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="f20ce-119">This doesn't occur with every command because of the way the formatting for that particular command is set up behind the scenes.</span></span>

<span data-ttu-id="f20ce-120">Het cijfer waarvan u op de hoogte wilt zijn van de indelings-cmdlets, produceert objecten die afwijken van de normale objecten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="f20ce-120">The number one thing to be aware of with the format cmdlets is they produce format objects that are different than normal objects in PowerShell.</span></span>

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

<span data-ttu-id="f20ce-121">Dit betekent dat indelings opdrachten niet kunnen worden gepiped naar de meeste andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="f20ce-121">What this means is format commands can't be piped to most other commands.</span></span> <span data-ttu-id="f20ce-122">Ze kunnen worden omgeleid naar een aantal `Out-*` opdrachten, maar dat is wel het geval.</span><span class="sxs-lookup"><span data-stu-id="f20ce-122">They can be piped to some of the `Out-*` commands, but that's about it.</span></span> <span data-ttu-id="f20ce-123">Daarom wilt u de opmaak aan het eind van de regel (rechts Format teren) uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="f20ce-123">This is why you want to perform any formatting at the very end of the line (format right).</span></span>

## <a name="aliases"></a><span data-ttu-id="f20ce-124">Aliassen</span><span class="sxs-lookup"><span data-stu-id="f20ce-124">Aliases</span></span>

<span data-ttu-id="f20ce-125">Een alias in Power shell is een kortere naam voor een opdracht.</span><span class="sxs-lookup"><span data-stu-id="f20ce-125">An alias in PowerShell is a shorter name for a command.</span></span> <span data-ttu-id="f20ce-126">Power shell bevat een reeks ingebouwde aliassen en u kunt ook uw eigen aliassen definiëren.</span><span class="sxs-lookup"><span data-stu-id="f20ce-126">PowerShell includes a set of built-in aliases and you can also define your own aliases.</span></span>

<span data-ttu-id="f20ce-127">De `Get-Alias` cmdlet wordt gebruikt om aliassen te vinden.</span><span class="sxs-lookup"><span data-stu-id="f20ce-127">The `Get-Alias` cmdlet is used to find aliases.</span></span> <span data-ttu-id="f20ce-128">Als u de alias voor een opdracht al kent, wordt de para meter **name** gebruikt om te bepalen aan welke opdracht de alias is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="f20ce-128">If you already know the alias for a command, the **Name** parameter is used to determine what command the alias is associated with.</span></span>

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

<span data-ttu-id="f20ce-129">Er kunnen meerdere aliassen worden opgegeven voor de waarde van de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="f20ce-129">Multiple aliases can be specified for the value of the **Name** parameter.</span></span>

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="f20ce-130">U ziet vaak dat de para meter **name** is wegge laten, omdat het een positionele para meter is.</span><span class="sxs-lookup"><span data-stu-id="f20ce-130">You'll often see the **Name** parameter omitted since it's a positional parameter.</span></span>

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

<span data-ttu-id="f20ce-131">Als u aliassen voor een opdracht wilt vinden, moet u de para meter **definitie** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f20ce-131">If you want to find aliases for a command, you'll need to use the **Definition** parameter.</span></span>

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="f20ce-132">De **definitie** parameter kan niet positioneel worden gebruikt, dus moet worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f20ce-132">The **Definition** parameter can't be used positionally so it must be specified.</span></span>

<span data-ttu-id="f20ce-133">Aliassen kunnen u enkele toetsaanslagen besparen en ze zijn prima wanneer u opdrachten in de-console typt.</span><span class="sxs-lookup"><span data-stu-id="f20ce-133">Aliases can save you a few keystrokes and they're fine when you're typing commands into the console.</span></span>
<span data-ttu-id="f20ce-134">Ze mogen niet worden gebruikt in scripts of in code die u met anderen opslaat of deelt.</span><span class="sxs-lookup"><span data-stu-id="f20ce-134">They shouldn't be used in scripts or any code that you're saving or sharing with others.</span></span> <span data-ttu-id="f20ce-135">Zoals eerder in dit boek is vermeld, is het gebruik van volledige cmdlet-en parameter namen zelf gedocumenteerd en gemakkelijker te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="f20ce-135">As mentioned earlier in this book, using full cmdlet and parameter names is self-documenting and easier to understand.</span></span>

<span data-ttu-id="f20ce-136">Wees voorzichtig bij het maken van uw eigen aliassen omdat deze alleen voor komen in uw huidige Power shell-sessie op uw computer.</span><span class="sxs-lookup"><span data-stu-id="f20ce-136">Use caution when creating your own aliases because they'll only exist in your current PowerShell session on your computer.</span></span>

## <a name="providers"></a><span data-ttu-id="f20ce-137">Providers</span><span class="sxs-lookup"><span data-stu-id="f20ce-137">Providers</span></span>

<span data-ttu-id="f20ce-138">Een provider in Power shell is een interface waarmee bestands systemen, zoals toegang tot een gegevens opslag, kunnen worden geopend.</span><span class="sxs-lookup"><span data-stu-id="f20ce-138">A provider in PowerShell is an interface that allows file system like access to a datastore.</span></span> <span data-ttu-id="f20ce-139">Er zijn een aantal ingebouwde providers in Power shell.</span><span class="sxs-lookup"><span data-stu-id="f20ce-139">There are a number of built-in providers in PowerShell.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

<span data-ttu-id="f20ce-140">Zoals u in de vorige resultaten kunt zien, zijn er ingebouwde providers voor het REGI ster, aliassen, omgevings variabelen, bestands systeem, functies, variabelen, certificaten en WSMan.</span><span class="sxs-lookup"><span data-stu-id="f20ce-140">As you can see in the previous results, there are built-in providers for the registry, aliases, environment variables, the file system, functions, variables, certificates, and WSMan.</span></span>

<span data-ttu-id="f20ce-141">De daad werkelijke schijven die deze providers gebruiken om hun gegevens opslag beschikbaar te maken, kunnen worden bepaald met de `Get-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f20ce-141">The actual drives that these providers use to expose their datastore can be determined with the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="f20ce-142">De `Get-PSDrive` cmdlet geeft niet alleen stations weer die worden weer gegeven door providers, maar er worden ook logische Windows-stations weer gegeven, inclusief stations die zijn toegewezen aan netwerk shares.</span><span class="sxs-lookup"><span data-stu-id="f20ce-142">The `Get-PSDrive` cmdlet not only displays drives exposed by providers, but it also displays Windows logical drives including drives mapped to network shares.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="f20ce-143">Modules van derden, zoals de Active Directory Power shell-module en de SQLServer Power shell-module, voegen hun eigen Power shell-provider en PSDrive toe.</span><span class="sxs-lookup"><span data-stu-id="f20ce-143">Third-party modules such as the Active Directory PowerShell module and the SQLServer PowerShell module both add their own PowerShell provider and PSDrive.</span></span>

<span data-ttu-id="f20ce-144">Importeer de Active Directory-en SQL Server Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="f20ce-144">Import the Active Directory and SQL Server PowerShell modules.</span></span>

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

<span data-ttu-id="f20ce-145">Controleer of er extra Power shell-providers zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f20ce-145">Check to see if any additional PowerShell providers were added.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

<span data-ttu-id="f20ce-146">In de vorige set met resultaten bestaan nu twee nieuwe Power shell-providers, een voor Active Directory en een andere voor SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f20ce-146">Notice that in the previous set of results, two new PowerShell providers now exist, one for Active Directory and another one for SQL Server.</span></span>

<span data-ttu-id="f20ce-147">Er is ook een PSDrive toegevoegd voor elk van deze modules.</span><span class="sxs-lookup"><span data-stu-id="f20ce-147">A PSDrive for each of those modules was also added.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="f20ce-148">PSDrives kan net als een traditioneel bestands systeem worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f20ce-148">PSDrives can be accessed just like a traditional file system.</span></span>

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a><span data-ttu-id="f20ce-149">Vergelijkingsoperators</span><span class="sxs-lookup"><span data-stu-id="f20ce-149">Comparison Operators</span></span>

<span data-ttu-id="f20ce-150">Power shell bevat een aantal vergelijkings operators die worden gebruikt om waarden te vergelijken of waarden te vinden die overeenkomen met bepaalde patronen.</span><span class="sxs-lookup"><span data-stu-id="f20ce-150">PowerShell contains a number of comparison operators that are used to compare values or find values that match certain patterns.</span></span> <span data-ttu-id="f20ce-151">Tabel 5-1 bevat een lijst met vergelijkings operatoren in Power shell.</span><span class="sxs-lookup"><span data-stu-id="f20ce-151">Table 5-1 contains a list of comparison operators in PowerShell.</span></span>

|    <span data-ttu-id="f20ce-152">Operator</span><span class="sxs-lookup"><span data-stu-id="f20ce-152">Operator</span></span>    |                          <span data-ttu-id="f20ce-153">Definitie</span><span class="sxs-lookup"><span data-stu-id="f20ce-153">Definition</span></span>                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | <span data-ttu-id="f20ce-154">Gelijk aan</span><span class="sxs-lookup"><span data-stu-id="f20ce-154">Equal to</span></span>                                                     |
| `-ne`          | <span data-ttu-id="f20ce-155">Niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="f20ce-155">Not equal to</span></span>                                                 |
| `-gt`          | <span data-ttu-id="f20ce-156">Groter dan</span><span class="sxs-lookup"><span data-stu-id="f20ce-156">Greater than</span></span>                                                 |
| `-ge`          | <span data-ttu-id="f20ce-157">Groter dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="f20ce-157">Greater than or equal to</span></span>                                     |
| `-lt`          | <span data-ttu-id="f20ce-158">Kleiner dan</span><span class="sxs-lookup"><span data-stu-id="f20ce-158">Less than</span></span>                                                    |
| `-le`          | <span data-ttu-id="f20ce-159">Kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="f20ce-159">Less than or equal to</span></span>                                        |
| `-Like`        | <span data-ttu-id="f20ce-160">Overeenkomst met het `*` Joker teken</span><span class="sxs-lookup"><span data-stu-id="f20ce-160">Match using the `*` wildcard character</span></span>                       |
| `-NotLike`     | <span data-ttu-id="f20ce-161">Komt niet overeen met het `*` Joker teken</span><span class="sxs-lookup"><span data-stu-id="f20ce-161">Does not match using the `*` wildcard character</span></span>              |
| `-Match`       | <span data-ttu-id="f20ce-162">Komt overeen met de opgegeven reguliere expressie</span><span class="sxs-lookup"><span data-stu-id="f20ce-162">Matches the specified regular expression</span></span>                     |
| `-NotMatch`    | <span data-ttu-id="f20ce-163">Komt niet overeen met de opgegeven reguliere expressie</span><span class="sxs-lookup"><span data-stu-id="f20ce-163">Does not match the specified regular expression</span></span>              |
| `-Contains`    | <span data-ttu-id="f20ce-164">Hiermee wordt bepaald of een verzameling een opgegeven waarde bevat</span><span class="sxs-lookup"><span data-stu-id="f20ce-164">Determines if a collection contains a specified value</span></span>        |
| `-NotContains` | <span data-ttu-id="f20ce-165">Hiermee wordt bepaald of een verzameling geen specifieke waarde bevat</span><span class="sxs-lookup"><span data-stu-id="f20ce-165">Determines if a collection does not contain a specific value</span></span> |
| `-In`          | <span data-ttu-id="f20ce-166">Hiermee wordt bepaald of een opgegeven waarde zich in een verzameling bevindt</span><span class="sxs-lookup"><span data-stu-id="f20ce-166">Determines if a specified value is in a collection</span></span>           |
| `-NotIn`       | <span data-ttu-id="f20ce-167">Hiermee wordt bepaald of een opgegeven waarde zich niet in een verzameling bevindt</span><span class="sxs-lookup"><span data-stu-id="f20ce-167">Determines if a specified value is not in a collection</span></span>       |
| `-Replace`     | <span data-ttu-id="f20ce-168">Vervangt de opgegeven waarde</span><span class="sxs-lookup"><span data-stu-id="f20ce-168">Replaces the specified value</span></span>                                 |

<span data-ttu-id="f20ce-169">Alle in tabel 5-1 genoemde Opera tors zijn hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="f20ce-169">All of the operators listed in Table 5-1 are case-insensitive.</span></span> <span data-ttu-id="f20ce-170">Plaats een `c` voor kant van de operator die wordt weer gegeven in tabel 5-1 om het hoofdletter gevoelig te maken.</span><span class="sxs-lookup"><span data-stu-id="f20ce-170">Place a `c` in front of the operator listed in Table 5-1 to make it case-sensitive.</span></span> <span data-ttu-id="f20ce-171">`-ceq`Is bijvoorbeeld de hoofdletter gevoelige versie van de `-eq` vergelijkings operator.</span><span class="sxs-lookup"><span data-stu-id="f20ce-171">For example, `-ceq` is the case-sensitive version of the `-eq` comparison operator.</span></span>

<span data-ttu-id="f20ce-172">De juiste case ' Power shell ' is gelijk aan ' Power shell ' met de vergelijkings operator equals.</span><span class="sxs-lookup"><span data-stu-id="f20ce-172">Proper case "PowerShell" is equal to lower case "powershell" using the equals comparison operator.</span></span>

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

<span data-ttu-id="f20ce-173">Het is niet gelijk aan het gebruik van de hoofdletter gevoelige versie van de vergelijkings operator gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="f20ce-173">It's not equal using the case-sensitive version of the equals comparison operator.</span></span>

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

<span data-ttu-id="f20ce-174">De operator niet gelijk aan vergelijkings operatoren keert de voor waarde om.</span><span class="sxs-lookup"><span data-stu-id="f20ce-174">The not equal comparison operator reverses the condition.</span></span>

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

<span data-ttu-id="f20ce-175">Groter dan, groter dan of gelijk aan, kleiner dan en kleiner dan of gelijk aan alles werk met teken reeks-of numerieke waarden.</span><span class="sxs-lookup"><span data-stu-id="f20ce-175">Greater than, greater than or equal to, less than, and less than or equal all work with string or numeric values.</span></span>

```powershell
5 -gt 5
```

```Output
False
```

<span data-ttu-id="f20ce-176">Als u meer dan of gelijk aan gebruikt in plaats van groter dan met het vorige voor beeld, wordt de **Booleaanse** waarde True geretourneerd, omdat vijf gelijk is aan vijf.</span><span class="sxs-lookup"><span data-stu-id="f20ce-176">Using greater than or equal to instead of greater than with the previous example returns the **Boolean** true since five is equal to five.</span></span>

```powershell
5 -ge 5
```

```Output
True
```

<span data-ttu-id="f20ce-177">Op basis van de resultaten van de vorige twee voor beelden kunt u waarschijnlijk bepalen hoe kleiner dan en kleiner dan of gelijk aan het werk zijn.</span><span class="sxs-lookup"><span data-stu-id="f20ce-177">Based on the results from the previous two examples, you can probably guess how both less than and less than or equal to work.</span></span>

```powershell
5 -lt 10
```

```Output
True
```

<span data-ttu-id="f20ce-178">De `-Like` `-Match` Opera tors en kunnen verwarrend zijn, zelfs voor ervaren Power shell-gebruikers.</span><span class="sxs-lookup"><span data-stu-id="f20ce-178">The `-Like` and `-Match` operators can be confusing, even for experienced PowerShell users.</span></span> <span data-ttu-id="f20ce-179">`-Like` wordt gebruikt met Joker tekens `*` en `?` voor het uitvoeren van "like"-overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="f20ce-179">`-Like` is used with wildcard the characters `*` and `?` to perform "like" matches.</span></span>

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

<span data-ttu-id="f20ce-180">`-Match` maakt gebruik van een reguliere expressie voor het uitvoeren van de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="f20ce-180">`-Match` uses a regular expression to perform the matching.</span></span>

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

<span data-ttu-id="f20ce-181">Gebruik de operator Range om de getallen 1 t/m 10 in een variabele op te slaan.</span><span class="sxs-lookup"><span data-stu-id="f20ce-181">Use the range operator to store the numbers 1 through 10 in a variable.</span></span>

```powershell
$Numbers = 1..10
```

```Output
```

<span data-ttu-id="f20ce-182">Bepaal of de `$Numbers` variabele 15 bevat.</span><span class="sxs-lookup"><span data-stu-id="f20ce-182">Determine if the `$Numbers` variable includes 15.</span></span>

```powershell
$Numbers -contains 15
```

```Output
False
```

<span data-ttu-id="f20ce-183">Bepaal of het getal 10 bevat.</span><span class="sxs-lookup"><span data-stu-id="f20ce-183">Determine if it includes the number 10.</span></span>

```powershell
$Numbers -contains 10
```

```Output
True
```

<span data-ttu-id="f20ce-184">`-NotContains` keert de logica om te zien of de `$Numbers` variabele geen waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="f20ce-184">`-NotContains` reverses the logic to see if the `$Numbers` variable doesn't contain a value.</span></span>

```powershell
$Numbers -notcontains 15
```

```Output
True
```

<span data-ttu-id="f20ce-185">In het vorige voor beeld wordt de **Booleaanse** waarde True geretourneerd, omdat het True is dat de `$Numbers` variabele geen 15 bevat.</span><span class="sxs-lookup"><span data-stu-id="f20ce-185">The previous example returns the **Boolean** true because it's true that the `$Numbers` variable doesn't contain 15.</span></span> <span data-ttu-id="f20ce-186">Het bevat echter het getal 10 zodat het onwaar is wanneer het is getest.</span><span class="sxs-lookup"><span data-stu-id="f20ce-186">It does however contain the number 10 so it's false when it's tested.</span></span>

```powershell
$Numbers -notcontains 10
```

```Output
False
```

<span data-ttu-id="f20ce-187">De vergelijkings operator in is voor het eerst geïntroduceerd in Power shell versie 3,0.</span><span class="sxs-lookup"><span data-stu-id="f20ce-187">The "in" comparison operator was first introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="f20ce-188">Dit wordt gebruikt om te bepalen of een waarde een matrix is.</span><span class="sxs-lookup"><span data-stu-id="f20ce-188">It's used to determine if a value is "in" an array.</span></span> <span data-ttu-id="f20ce-189">De `$Numbers` variabele is een matrix omdat deze meerdere waarden bevat.</span><span class="sxs-lookup"><span data-stu-id="f20ce-189">The `$Numbers` variable is an array since it contains multiple values.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="f20ce-190">Met andere woorden, `-in` voert dezelfde test uit als de vergelijkings operator bevat, met uitzonde ring van de tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="f20ce-190">In other words, `-in` performs the same test as the contains comparison operator except from the opposite direction.</span></span>

```powershell
10 -in $Numbers
```

```Output
True
```

<span data-ttu-id="f20ce-191">15 bevindt zich niet in de `$Numbers` matrix, dus false wordt in het volgende voor beeld geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f20ce-191">15 isn't in the `$Numbers` array so false is returned in the following example.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="f20ce-192">Net als de `-contains` operator, `not` keert u de logica voor de `-in` operator om.</span><span class="sxs-lookup"><span data-stu-id="f20ce-192">Just like the `-contains` operator, `not` reverses the logic for the `-in` operator.</span></span>

```powershell
10 -notin $Numbers
```

```Output
False
```

<span data-ttu-id="f20ce-193">Het vorige voor beeld retourneert False omdat de `$Numbers` matrix 10 bevat en de voor waarde is getest om te bepalen of deze geen 10 bevat.</span><span class="sxs-lookup"><span data-stu-id="f20ce-193">The previous example returns false because the `$Numbers` array does include 10 and the condition was testing to determine if it didn't contain 10.</span></span>

<span data-ttu-id="f20ce-194">15 is ' niet in ' de `$Numbers` matrix, zodat de **Booleaanse** waarde True wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f20ce-194">15 is "not in" the `$Numbers` array so it returns the **Boolean** true.</span></span>

```powershell
15 -notin $Numbers
```

```Output
True
```

<span data-ttu-id="f20ce-195">De `-replace` operator heeft precies het gewenste idee.</span><span class="sxs-lookup"><span data-stu-id="f20ce-195">The `-replace` operator does just want you would think.</span></span> <span data-ttu-id="f20ce-196">Dit wordt gebruikt om iets te vervangen.</span><span class="sxs-lookup"><span data-stu-id="f20ce-196">It's used to replace something.</span></span> <span data-ttu-id="f20ce-197">Als u één waarde opgeeft, wordt deze waarde vervangen door niets.</span><span class="sxs-lookup"><span data-stu-id="f20ce-197">Specifying one value replaces that value with nothing.</span></span> <span data-ttu-id="f20ce-198">In het volgende voor beeld vervangt ik ' shell ' door niets.</span><span class="sxs-lookup"><span data-stu-id="f20ce-198">In the following example, I replace "Shell" with nothing.</span></span>

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

<span data-ttu-id="f20ce-199">Als u een waarde wilt vervangen door een andere waarde, geeft u de nieuwe waarde op achter het patroon dat u wilt vervangen.</span><span class="sxs-lookup"><span data-stu-id="f20ce-199">If you want to replace a value with a different value, specify the new value after the pattern you want to replace.</span></span> <span data-ttu-id="f20ce-200">SQL zaterdag in Baton Rouge is een gebeurtenis die ik elk jaar probeer te spreken.</span><span class="sxs-lookup"><span data-stu-id="f20ce-200">SQL Saturday in Baton Rouge is an event that I try to speak at every year.</span></span> <span data-ttu-id="f20ce-201">In het volgende voor beeld wordt het woord ' zaterdag ' vervangen door de afkorting ' SAT '.</span><span class="sxs-lookup"><span data-stu-id="f20ce-201">In the following example, I replace the word "Saturday" with the abbreviation "Sat".</span></span>

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="f20ce-202">Er zijn ook methoden zoals **vervangen ()** die kunnen worden gebruikt voor het vervangen van dingen die vergelijkbaar zijn met de manier waarop de operator vervangen werkt.</span><span class="sxs-lookup"><span data-stu-id="f20ce-202">There are also methods like **Replace()** that can be used to replace things similar to the way the replace operator works.</span></span> <span data-ttu-id="f20ce-203">De `-Replace` operator is echter standaard hoofdletter gevoelig en de methode **replace ()** is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="f20ce-203">However, the `-Replace` operator is case-insensitive by default, and the **Replace()** method is case-sensitive.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

<span data-ttu-id="f20ce-204">U ziet dat het woord ' zaterdag ' niet is vervangen in het vorige voor beeld.</span><span class="sxs-lookup"><span data-stu-id="f20ce-204">Notice that the word "Saturday" wasn't replaced in the previous example.</span></span> <span data-ttu-id="f20ce-205">Dit komt doordat het is opgegeven in een ander geval dan het origineel.</span><span class="sxs-lookup"><span data-stu-id="f20ce-205">This is because it was specified in a different case than the original.</span></span> <span data-ttu-id="f20ce-206">Wanneer het woord ' zaterdag ' is opgegeven in hetzelfde geval als de oorspronkelijke, vervangt de methode **replace ()** deze zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="f20ce-206">When the word "Saturday" is specified in the same case as the original, the **Replace()** method does replace it as expected.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="f20ce-207">Wees voorzichtig wanneer u methoden gebruikt om gegevens te transformeren, omdat u onvoorziene problemen kunt ondervinden, zoals het uitvoeren van de _Turkije-test_.</span><span class="sxs-lookup"><span data-stu-id="f20ce-207">Be careful when using methods to transform data because you can run into unforeseen problems, such as failing the _Turkey Test_.</span></span> <span data-ttu-id="f20ce-208">Zie voor een voor beeld het blog artikel met de titel [met behulp van een schadelijke Power shell-code testen met andere cult uren][].</span><span class="sxs-lookup"><span data-stu-id="f20ce-208">For an example, see the blog article titled [Using Pester to Test PowerShell Code with Other Cultures][].</span></span> <span data-ttu-id="f20ce-209">Mijn aanbeveling is het gebruik van een operator in plaats van een methode waar mogelijk om dit soort problemen te voor komen.</span><span class="sxs-lookup"><span data-stu-id="f20ce-209">My recommendation is to use an operator instead of a method whenever possible to avoid these types of problems.</span></span>

<span data-ttu-id="f20ce-210">Hoewel de vergelijkings operators kunnen worden gebruikt zoals weer gegeven in de voor gaande voor beelden, kunt u deze zelf gebruiken met de `Where-Object` cmdlet om een bepaald type filtering uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f20ce-210">While the comparison operators can be used as shown in the previous examples, I normally find myself using them with the `Where-Object` cmdlet to perform some type of filtering.</span></span>

## <a name="summary"></a><span data-ttu-id="f20ce-211">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="f20ce-211">Summary</span></span>

<span data-ttu-id="f20ce-212">In dit hoofd stuk hebt u een aantal verschillende onderwerpen geleerd waarin opmaak rechten, aliassen, providers en vergelijkings operatoren worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="f20ce-212">In this chapter, you've learned a number of different topics to include Formatting Right, Aliases, Providers, and Comparison Operators.</span></span>

## <a name="review"></a><span data-ttu-id="f20ce-213">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="f20ce-213">Review</span></span>

1. <span data-ttu-id="f20ce-214">Waarom is het nood zakelijk om zo veel mogelijk opmaak te kunnen uitvoeren?</span><span class="sxs-lookup"><span data-stu-id="f20ce-214">Why is it necessary to perform Formatting as far to the right as possible?</span></span>
1. <span data-ttu-id="f20ce-215">Hoe bepaalt u wat de feitelijke cmdlet voor de alias is `%` ?</span><span class="sxs-lookup"><span data-stu-id="f20ce-215">How do you determine what the actual cmdlet is for the `%` alias?</span></span>
1. <span data-ttu-id="f20ce-216">Waarom moet u geen aliassen gebruiken in scripts die u opslaat of code die u met anderen deelt?</span><span class="sxs-lookup"><span data-stu-id="f20ce-216">Why shouldn't you use aliases in scripts you save or code you share with others?</span></span>
1. <span data-ttu-id="f20ce-217">Voer een adreslijst vermelding uit op de stations die zijn gekoppeld aan een van de register providers.</span><span class="sxs-lookup"><span data-stu-id="f20ce-217">Perform a directory listing on the drives that are associated with one of the registry providers.</span></span>
1. <span data-ttu-id="f20ce-218">Wat is een van de belangrijkste voor delen van het gebruik van de operator replace in plaats van de methode replace?</span><span class="sxs-lookup"><span data-stu-id="f20ce-218">What's one of the main benefits of using the replace operator instead of the replace method?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="f20ce-219">Aanbevolen Lees bewerkingen</span><span class="sxs-lookup"><span data-stu-id="f20ce-219">Recommended Reading</span></span>

- <span data-ttu-id="f20ce-220">[Format-Table][]</span><span class="sxs-lookup"><span data-stu-id="f20ce-220">[Format-Table][]</span></span>
- <span data-ttu-id="f20ce-221">[Format-List][]</span><span class="sxs-lookup"><span data-stu-id="f20ce-221">[Format-List][]</span></span>
- <span data-ttu-id="f20ce-222">[Format-Wide][]</span><span class="sxs-lookup"><span data-stu-id="f20ce-222">[Format-Wide][]</span></span>
- <span data-ttu-id="f20ce-223">[about_Aliases][]</span><span class="sxs-lookup"><span data-stu-id="f20ce-223">[about_Aliases][]</span></span>
- <span data-ttu-id="f20ce-224">[about_Providers][]</span><span class="sxs-lookup"><span data-stu-id="f20ce-224">[about_Providers][]</span></span>
- <span data-ttu-id="f20ce-225">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="f20ce-225">[about_Comparison_Operators][]</span></span>
- <span data-ttu-id="f20ce-226">[about_Arrays][]</span><span class="sxs-lookup"><span data-stu-id="f20ce-226">[about_Arrays][]</span></span>

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Power shell-code met andere cult uren testen met behulp van een schadelijke hand]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
[Using Pester to Test PowerShell Code with Other Cultures]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
