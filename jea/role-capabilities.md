---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell beveiliging
title: JEA rol mogelijkheden
ms.openlocfilehash: 10f5f390daccbb012be6ee7272041e777810ee12
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="ed065-103">JEA rol mogelijkheden</span><span class="sxs-lookup"><span data-stu-id="ed065-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="ed065-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ed065-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ed065-105">Wanneer u een eindpunt JEA maakt, moet u een of meer 'rol mogelijkheden' die wordt beschreven definiëren *wat* iemand in een sessie JEA kunt doen.</span><span class="sxs-lookup"><span data-stu-id="ed065-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="ed065-106">De mogelijkheid van een rol is een PowerShell-gegevensbestand met de extensie .psrc met een lijst met alle cmdlets, functies, -providers en externe programma's die beschikbaar zijn voor het verbinden van gebruikers moeten worden gedaan.</span><span class="sxs-lookup"><span data-stu-id="ed065-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="ed065-107">In dit onderwerp wordt beschreven hoe een PowerShell-rol mogelijkheid-bestand voor uw gebruikers JEA te maken.</span><span class="sxs-lookup"><span data-stu-id="ed065-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="ed065-108">Bepalen welke opdrachten om toe te staan</span><span class="sxs-lookup"><span data-stu-id="ed065-108">Determine which commands to allow</span></span>

<span data-ttu-id="ed065-109">De eerste stap bij het maken van een rol mogelijkheid-bestand is te overwegen wat de gebruikers die zijn toegewezen aan de rol toegang nodig tot.</span><span class="sxs-lookup"><span data-stu-id="ed065-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="ed065-110">Deze vereisten verzamelingsproces kunnen even duren, maar het is een belangrijk proces.</span><span class="sxs-lookup"><span data-stu-id="ed065-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="ed065-111">Gebruikers toegang geven tot te weinig cmdlets en -functies kunt voorkomen dat ze toegang krijgen tot hun werk kan verrichten.</span><span class="sxs-lookup"><span data-stu-id="ed065-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="ed065-112">Toestaan van toegang tot te veel cmdlets en functies kan leiden tot gebruikers die meer dan u hebt aangebracht met hun impliciete beheerdersbevoegdheden verzwakken uw beveiliging houding ten doen.</span><span class="sxs-lookup"><span data-stu-id="ed065-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="ed065-113">Hoe u over dit proces gaat afhankelijk van uw organisatie en de doelstellingen, maar de volgende tips kunt Zorg ervoor dat u op de juiste weg bent.</span><span class="sxs-lookup"><span data-stu-id="ed065-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="ed065-114">**Identificeren** de opdrachten-gebruikers voor hun werk gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ed065-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="ed065-115">Hierbij kan het controleren van de IT-personeel, automatiseringsscripts controleren of het analyseren van PowerShell-sessie transcripties of Logboeken.</span><span class="sxs-lookup"><span data-stu-id="ed065-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="ed065-116">**Update** gebruik van de opdrachtregelprogramma's voor PowerShell-equivalenten, waar mogelijk, voor de beste controle en JEA aanpassing ervaring.</span><span class="sxs-lookup"><span data-stu-id="ed065-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="ed065-117">Externe programma's kunnen niet als granulair als systeemeigen PowerShell-cmdlets en functies in JEA worden beperkt.</span><span class="sxs-lookup"><span data-stu-id="ed065-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="ed065-118">**Beperken** het bereik van de cmdlets nodig alleen kan bepaalde parameters of parameterwaarden.</span><span class="sxs-lookup"><span data-stu-id="ed065-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="ed065-119">Dit is vooral belangrijk als gebruikers moeten alleen deel uitmaken van een systeem beheren.</span><span class="sxs-lookup"><span data-stu-id="ed065-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="ed065-120">**Maak** aangepaste functies om complexe opdrachten of opdrachten die moeilijk te beperken in JEA te vervangen.</span><span class="sxs-lookup"><span data-stu-id="ed065-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="ed065-121">Een eenvoudige functie die een complexe opdracht terugloopt of, past logica voor aanvullende verificatie te kan bieden extra controles voor beheerders en eindgebruikers eenvoud.</span><span class="sxs-lookup"><span data-stu-id="ed065-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="ed065-122">**Test** de gedefinieerde lijst met toegestane opdrachten met uw gebruikers en/of de automation-services en pas deze zo nodig.</span><span class="sxs-lookup"><span data-stu-id="ed065-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="ed065-123">Het is belangrijk om te onthouden opdrachten in een sessie JEA zijn vaak bevoegdheden uitvoeren met admin (of anderszins met verhoogde bevoegdheden).</span><span class="sxs-lookup"><span data-stu-id="ed065-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="ed065-124">Zorgvuldige selectie van de beschikbare opdrachten is het belangrijk om te controleren of het eindpunt JEA staat niet toe dat de gebruiker verbinding maakt zichzelf machtigingen toekennen.</span><span class="sxs-lookup"><span data-stu-id="ed065-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="ed065-125">Hieronder volgen enkele voorbeelden van opdrachten die kunnen worden gebruikt met kwaadaardige bedoelingen als toegestaan in een onbeperkte status.</span><span class="sxs-lookup"><span data-stu-id="ed065-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="ed065-126">Houd er rekening mee dat dit geen uitputtende lijst is en mag alleen worden gebruikt als een beginpunt uit.</span><span class="sxs-lookup"><span data-stu-id="ed065-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="ed065-127">Voorbeelden van potentieel gevaarlijke opdrachten</span><span class="sxs-lookup"><span data-stu-id="ed065-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="ed065-128">Risico 's</span><span class="sxs-lookup"><span data-stu-id="ed065-128">Risk</span></span> | <span data-ttu-id="ed065-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ed065-129">Example</span></span> | <span data-ttu-id="ed065-130">Gerelateerde opdrachten</span><span class="sxs-lookup"><span data-stu-id="ed065-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="ed065-131">De gebruiker verbinding maakt verlenen beheerdersbevoegdheden om over te slaan JEA</span><span class="sxs-lookup"><span data-stu-id="ed065-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="ed065-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="ed065-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="ed065-133">Uitvoeren van willekeurige code, zoals malware, misbruik of aangepaste scripts voor het overslaan van beveiliging</span><span class="sxs-lookup"><span data-stu-id="ed065-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="ed065-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="ed065-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="ed065-135">Maak een bestand van de mogelijkheid rol</span><span class="sxs-lookup"><span data-stu-id="ed065-135">Create a role capability file</span></span>

<span data-ttu-id="ed065-136">Kunt u een nieuw bestand rol mogelijkheid PowerShell met de [nieuw PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed065-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="ed065-137">Het resulterende rol mogelijkheid bestand kan worden geopend in een teksteditor en gewijzigd zodat de gewenste opdrachten voor de rol.</span><span class="sxs-lookup"><span data-stu-id="ed065-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="ed065-138">De PowerShell-help-documentatie bevat enkele voorbeelden van hoe u het bestand kunt configureren.</span><span class="sxs-lookup"><span data-stu-id="ed065-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="ed065-139">PowerShell-cmdlets en-functies</span><span class="sxs-lookup"><span data-stu-id="ed065-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="ed065-140">Voor het autoriseren van gebruikers om uit te voeren PowerShell-cmdlets of functies toevoegen de naam van de cmdlet of functie aan de VisbibleCmdlets of VisibleFunctions velden.</span><span class="sxs-lookup"><span data-stu-id="ed065-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisbibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="ed065-141">U kunt uitvoeren als u niet zeker weet of een opdracht is een cmdlet of functie `Get-Command <name>` en controleer de eigenschap 'CommandType' in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="ed065-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="ed065-142">Soms is het bereik van een bepaalde cmdlet of functie is te breed voor de behoeften van uw gebruikers.</span><span class="sxs-lookup"><span data-stu-id="ed065-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="ed065-143">Een DNS-beheerder is bijvoorbeeld waarschijnlijk alleen behoeften toegang tot om de DNS-service opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="ed065-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="ed065-144">In een omgeving met meerdere tenants waarbij tenants toegang verleend tot selfservice beheerhulpprogramma's moet tenants beheren met hun eigen resources.</span><span class="sxs-lookup"><span data-stu-id="ed065-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="ed065-145">Voor dergelijke gevallen kunt u beperken welke parameters beschikbaar worden gesteld van de cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="ed065-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="ed065-146">In meer geavanceerde scenario's moet u mogelijk ook beperken welke waarden iemand kan leveren aan deze parameters.</span><span class="sxs-lookup"><span data-stu-id="ed065-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="ed065-147">Mogelijkheden van de rol kunnen u bij het definiëren van een set toegestane waarden of een reguliere-expressiepatroon die wordt geëvalueerd om te bepalen of een opgegeven invoer is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ed065-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="ed065-148">De [algemene PowerShell-parameters](https://technet.microsoft.com/en-us/library/hh847884.aspx) zijn altijd toegestaan, zelfs als u de beschikbare parameters beperken.</span><span class="sxs-lookup"><span data-stu-id="ed065-148">The [common PowerShell parameters](https://technet.microsoft.com/en-us/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="ed065-149">U moet niet expliciet vermeld ze in het veld Parameters.</span><span class="sxs-lookup"><span data-stu-id="ed065-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="ed065-150">De volgende tabel beschrijft de verschillende manieren kunt u een cmdlet zichtbaar of functie aanpassen.</span><span class="sxs-lookup"><span data-stu-id="ed065-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="ed065-151">U kunt combineren en overeen met een van de hieronder in de VisibleCmdlets veld.</span><span class="sxs-lookup"><span data-stu-id="ed065-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="ed065-152">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ed065-152">Example</span></span>                                                                                      | <span data-ttu-id="ed065-153">Gebruiksvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="ed065-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="ed065-154">`'My-Func'` of `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="ed065-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="ed065-155">Kan de gebruiker om uit te voeren `My-Func` zonder beperkingen van de parameters.</span><span class="sxs-lookup"><span data-stu-id="ed065-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="ed065-156">Kan de gebruiker om uit te voeren `My-Func` van de module `MyModule` zonder beperkingen van de parameters.</span><span class="sxs-lookup"><span data-stu-id="ed065-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="ed065-157">Kan de gebruiker een cmdlet of functie uitvoeren met de term `My`.</span><span class="sxs-lookup"><span data-stu-id="ed065-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="ed065-158">Kan de gebruiker een cmdlet of functie uitvoeren met het zelfstandig naamwoord `Func`.</span><span class="sxs-lookup"><span data-stu-id="ed065-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="ed065-159">Kan de gebruiker om uit te voeren `My-Func` met de `Param1` en/of `Param2` parameters.</span><span class="sxs-lookup"><span data-stu-id="ed065-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="ed065-160">Elke waarde kan worden opgegeven voor de parameters.</span><span class="sxs-lookup"><span data-stu-id="ed065-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="ed065-161">Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter.</span><span class="sxs-lookup"><span data-stu-id="ed065-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="ed065-162">Aan de parameter kan alleen 'Waarde1' en 'Waarde2' worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ed065-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="ed065-163">Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter.</span><span class="sxs-lookup"><span data-stu-id="ed065-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="ed065-164">Een waarde die beginnen met 'contoso' kan worden opgegeven voor de parameter.</span><span class="sxs-lookup"><span data-stu-id="ed065-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>


> [!WARNING]
> <span data-ttu-id="ed065-165">Voor de aanbevolen beveiligingsprocedures, is het niet raadzaam jokertekens te gebruiken bij het definiëren van zichtbaar cmdlets of functies.</span><span class="sxs-lookup"><span data-stu-id="ed065-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="ed065-166">In plaats daarvan moet u elke vertrouwde opdracht om te controleren of er geen andere opdrachten die de dezelfde schematische delen per ongeluk zijn gemachtigd expliciet vermelden.</span><span class="sxs-lookup"><span data-stu-id="ed065-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="ed065-167">U kunt een ValidatePattern en de ValidateSet niet toepassen op de dezelfde cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="ed065-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="ed065-168">Als u dit doet, wordt de ValidatePattern de ValidateSet overschreven.</span><span class="sxs-lookup"><span data-stu-id="ed065-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="ed065-169">Bekijk voor meer informatie over ValidatePattern [dit *artikel van Hey, Scripting Guy!* boeken](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) en de [PowerShell reguliere expressies](https://technet.microsoft.com/en-us/library/hh847880.aspx) verwijst naar inhoud.</span><span class="sxs-lookup"><span data-stu-id="ed065-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/en-us/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="ed065-170">Externe opdrachten en PowerShell-scripts toestaan</span><span class="sxs-lookup"><span data-stu-id="ed065-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="ed065-171">U moet het volledige pad toevoegen aan elk programma in het veld VisibleExternalCommands zodat gebruikers uitvoerbare bestanden en PowerShell-scripts (.ps1) in een sessie JEA uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="ed065-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="ed065-172">Het wordt aanbevolen, waar mogelijk, PowerShell-cmdlet/functie equivalenten van elke externe uitvoerbare bestanden die geeft u toestemming omdat hebt u controle gedurende welke parameters zijn toegestaan met PowerShell-cmdlets/functies gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ed065-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="ed065-173">Veel uitvoerbare bestanden kunt u zowel lezen van de huidige status en wijzig deze alleen door te geven van verschillende parameters.</span><span class="sxs-lookup"><span data-stu-id="ed065-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="ed065-174">Neem bijvoorbeeld de rol van een bestand serverbeheerder die wil controleren welke netwerkshares worden gehost door de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ed065-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="ed065-175">Een manier om te controleren om te gebruiken, is `net share`.</span><span class="sxs-lookup"><span data-stu-id="ed065-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="ed065-176">Echter, zodat net.exe is zeer gevaarlijke omdat de beheerder kan net zo eenvoudig gebruik van de opdracht om te krijgen van beheerdersbevoegdheden met `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="ed065-176">However, allowing net.exe is very dangerous becuase the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="ed065-177">Er is een betere benadering om toe te staan [Get-SmbShare](https://technet.microsoft.com/en-us/library/jj635704.aspx) die hetzelfde resultaat bereikt, maar heeft een veel meer beperkt bereik.</span><span class="sxs-lookup"><span data-stu-id="ed065-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/en-us/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="ed065-178">Wanneer externe opdrachten beschikbaar maken voor gebruikers in een sessie JEA, geef altijd het volledige pad naar het uitvoerbare bestand om te controleren of een gelijknamige (en mogelijk malicous) programma elders geplaatst op het systeem niet in plaats daarvan wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ed065-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicous) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="ed065-179">Toegang tot aanbieders van PowerShell toe te staan</span><span class="sxs-lookup"><span data-stu-id="ed065-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="ed065-180">Standaard zijn er geen PowerShell-providers zijn beschikbaar in JEA sessies.</span><span class="sxs-lookup"><span data-stu-id="ed065-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="ed065-181">Hiermee wordt voornamelijk vermindert het risico van vertrouwelijke gegevens en configuratie-instellingen wordt doorgegeven aan de gebruiker verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="ed065-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="ed065-182">Indien nodig, kunt u toegang tot de PowerShell-providers met behulp van de `VisibleProviders` opdracht.</span><span class="sxs-lookup"><span data-stu-id="ed065-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="ed065-183">Voer voor een volledige lijst met providers `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="ed065-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="ed065-184">Voor eenvoudige taken die toegang tot het bestandssysteem, register, certificaatarchief of andere gevoelige providers vereisen, kunt u ook overwegen schrijven geen aangepaste functie die geschikt is voor de provider namens de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="ed065-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="ed065-185">Functies, -cmdlets en externe programma's die beschikbaar in een sessie JEA zijn vallen niet onder de dezelfde beperkingen als JEA--ze hebben standaard toegang tot elke provider.</span><span class="sxs-lookup"><span data-stu-id="ed065-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="ed065-186">Ook kunt u overwegen de [schijf van de gebruiker](session-configurations.md#user-drive) wanneer bestanden zijn gekopieerd naar/van een eindpunt JEA is vereist.</span><span class="sxs-lookup"><span data-stu-id="ed065-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="ed065-187">Maken van aangepaste functies</span><span class="sxs-lookup"><span data-stu-id="ed065-187">Creating custom functions</span></span>

<span data-ttu-id="ed065-188">U kunt aangepaste functies in een bestand van de rol mogelijkheid voor het vereenvoudigen van complexe taken voor uw eindgebruikers schrijven.</span><span class="sxs-lookup"><span data-stu-id="ed065-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="ed065-189">Aangepaste functies zijn ook handig wanneer u geavanceerde validatielogica voor cmdlet parameterwaarden vereist.</span><span class="sxs-lookup"><span data-stu-id="ed065-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="ed065-190">U kunt eenvoudige functies schrijven in de **FunctionDefinitions** veld:</span><span class="sxs-lookup"><span data-stu-id="ed065-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="ed065-191">Vergeet niet om toe te voegen van de naam van uw aangepaste functies voor de **VisibleFunctions** zodat ze kunnen worden uitgevoerd door de gebruikers JEA veld.</span><span class="sxs-lookup"><span data-stu-id="ed065-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>


<span data-ttu-id="ed065-192">De hoofdtekst (scriptblok) van aangepaste functies in de standaardmodus voor de taal voor het systeem wordt uitgevoerd en is niet van JEA taal beperkingen.</span><span class="sxs-lookup"><span data-stu-id="ed065-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="ed065-193">Dit betekent dat functies kunnen krijgen het bestandssysteem en register tot en opdrachten die niet zichtbaar in het bestand van de mogelijkheid rol gemaakt zijn.</span><span class="sxs-lookup"><span data-stu-id="ed065-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="ed065-194">Behandelen wilt willekeurige code worden uitgevoerd wanneer u parameters toe en te voorkomen dat de gebruikersinvoer piping rechtstreeks in cmdlets, zoals `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="ed065-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="ed065-195">In het bovenstaande voorbeeld ziet u dat de naam van de volledig gekwalificeerde module (FQMN) `Microsoft.PowerShell.Utility\Select-Object` is gebruikt in plaats van het steno `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="ed065-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="ed065-196">Functies die zijn gedefinieerd in de rol capability-bestanden zijn nog steeds onderworpen aan het bereik van JEA sessies, waaronder de proxyfuncties JEA wordt gemaakt voor het beperken van bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="ed065-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="ed065-197">Select-Object is een standaard beperkte cmdlet in alle JEA sessies die niet is toegestaan als u willekeurige eigenschappen van objecten te selecteren.</span><span class="sxs-lookup"><span data-stu-id="ed065-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="ed065-198">Als u de onbeperkte Select-Object in de functies, moet u expliciet de volledige implementatie aanvragen door op te geven van de FQMN.</span><span class="sxs-lookup"><span data-stu-id="ed065-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="ed065-199">Een beperkte cmdlet in een sessie JEA zou vertonen hetzelfde gedrag bij het aanroepen van een functie, in overeenstemming met de PowerShell [opdracht voorrang](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="ed065-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="ed065-200">Als u een groot aantal aangepaste functies schrijft, kan het zijn gemakkelijker te plaatsen een [PowerShell-Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="ed065-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="ed065-201">Vervolgens kunt u aanbrengen die functies zichtbaar in de JEA-sessie met behulp van het veld VisibleFunctions zoals u zou met ingebouwde en derden modules doen.</span><span class="sxs-lookup"><span data-stu-id="ed065-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="ed065-202">Rol mogelijkheden plaatsen in een module</span><span class="sxs-lookup"><span data-stu-id="ed065-202">Place role capabilities in a module</span></span>

<span data-ttu-id="ed065-203">In de volgorde voor PowerShell zoeken naar een bestand van de mogelijkheid rol, moet deze worden opgeslagen in een map 'RoleCapabilities' in een PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="ed065-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="ed065-204">De module kan worden opgeslagen in een map die is opgenomen in de `$env:PSModulePath` omgevingsvariabele, maar u moet niet plaats deze in System32 (gereserveerd voor ingebouwde modules) of een map waarin het niet wordt vertrouwd, verbinden van gebruikers kan de bestanden wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ed065-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="ed065-205">Hieronder volgt een voorbeeld van het maken van een PowerShell-script basismodule aangeroepen *ContosoJEA* in het pad 'Program Files'.</span><span class="sxs-lookup"><span data-stu-id="ed065-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="ed065-206">Zie [inzicht in een PowerShell-Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) voor meer informatie over PowerShell-modules, modulemanifesten en de omgevingsvariabele PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="ed065-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="ed065-207">Bijwerken van de mogelijkheden van de rol</span><span class="sxs-lookup"><span data-stu-id="ed065-207">Updating role capabilities</span></span>


<span data-ttu-id="ed065-208">U kunt een rol mogelijkheid-bestand op elk gewenst moment bijwerken door gewoon opslaan van wijzigingen in het bestand van de mogelijkheid rol.</span><span class="sxs-lookup"><span data-stu-id="ed065-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="ed065-209">Een nieuwe JEA sessies gestart nadat de mogelijkheid van de rol is bijgewerkt weerspiegelt de herziene mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="ed065-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="ed065-210">Dit is de reden waarom het beheren van toegang tot de map van de mogelijkheden rol is daarom belangrijk.</span><span class="sxs-lookup"><span data-stu-id="ed065-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="ed065-211">Alleen uiterst vertrouwde beheerders moet kunnen wijzigen van de rol capability-bestanden.</span><span class="sxs-lookup"><span data-stu-id="ed065-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="ed065-212">Als een niet-vertrouwde gebruiker rol capability-bestanden wijzigen kunt, kunnen ze gemakkelijk zelf toegang geven tot cmdlets waarmee ze hun bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="ed065-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>


<span data-ttu-id="ed065-213">Voor beheerders willen toegang tot de mogelijkheden van de rol voor het vergrendelen, zorg ervoor dat het dat lokale systeem leestoegang heeft tot de rol capability-bestanden en met modules.</span><span class="sxs-lookup"><span data-stu-id="ed065-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="ed065-214">Hoe de mogelijkheden van de rol worden samengevoegd</span><span class="sxs-lookup"><span data-stu-id="ed065-214">How role capabilities are merged</span></span>

<span data-ttu-id="ed065-215">Gebruikers toegang kunnen krijgen tot meerdere mogelijkheden voor rol wanneer ze een sessie JEA, afhankelijk van de rol toewijzingen in de [sessie configuratiebestand](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="ed065-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="ed065-216">Als dit gebeurt, JEA dat de gebruiker probeert de *meest strikte* reeks opdrachten die worden toegestaan door een van de rollen.</span><span class="sxs-lookup"><span data-stu-id="ed065-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="ed065-217">**VisibleCmdlets en VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="ed065-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="ed065-218">De meest complexe logica voor het samenvoegen van invloed op cmdlets en -functies, die hun parameters en de parameterwaarden die zijn beperkt in JEA hebben.</span><span class="sxs-lookup"><span data-stu-id="ed065-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="ed065-219">De regels zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="ed065-219">The rules are as follows:</span></span>

1. <span data-ttu-id="ed065-220">Als een cmdlet alleen zichtbaar in één rol gemaakt is, worden deze zichtbaar is voor de gebruiker met beperkingen van toepassing parameter.</span><span class="sxs-lookup"><span data-stu-id="ed065-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="ed065-221">Als een cmdlet zichtbaar is in meer dan één rol wordt uitgevoerd, en elke rol de dezelfde beperkingen voor de cmdlet heeft, worden de cmdlet zichtbaar is voor de gebruiker met deze beperkingen.</span><span class="sxs-lookup"><span data-stu-id="ed065-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="ed065-222">Als een cmdlet zichtbaar is in meer dan één rol wordt uitgevoerd en een andere set parameters voor deze rol zijn toegestaan, zijn de cmdlet en alle parameters gedefinieerd voor elke rol zijn zichtbaar voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="ed065-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="ed065-223">Als een rol geen beperkingen voor de parameters, worden alle parameters mogen.</span><span class="sxs-lookup"><span data-stu-id="ed065-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="ed065-224">Als één rol een valideren set of een patroon valideren voor een cmdlet-parameter definieert en de andere rol mag de parameter, maar geen beperkingen van de parameterwaarden, worden de set valideren of het patroon wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="ed065-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="ed065-225">Als een set valideren is gedefinieerd voor de dezelfde cmdlet-parameter in meer dan één rol, worden alle waarden uit alle valideren sets toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ed065-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="ed065-226">Als een patroon valideren voor de dezelfde cmdlet-parameter in meer dan één rol is gedefinieerd, wordt er een waarden die met de patronen overeenkomen toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ed065-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="ed065-227">Als een set valideren is gedefinieerd in een of meer rollen en een patroon valideren in een andere rol voor de dezelfde cmdlet-parameter is gedefinieerd, wordt de set valideren genegeerd en wordt regel (6) van toepassing op de resterende valideren patronen.</span><span class="sxs-lookup"><span data-stu-id="ed065-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="ed065-228">Hieronder volgt een voorbeeld van hoe de functies volgens deze regels worden samengevoegd:</span><span class="sxs-lookup"><span data-stu-id="ed065-228">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



<span data-ttu-id="ed065-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="ed065-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="ed065-230">Alle andere velden in het bestand van de mogelijkheid rol worden alleen toegevoegd aan een volledige reeks van toegestane externe opdrachten, aliassen providers en opstartscripts.</span><span class="sxs-lookup"><span data-stu-id="ed065-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="ed065-231">Elke opdracht, alias, provider of script in één rol functie beschikbaar zijn voor de gebruiker JEA beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="ed065-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="ed065-232">Zorg ervoor dat u ervoor te zorgen dat de gecombineerde set met providers van een rol mogelijkheden en functies-cmdlets/opdrachten van een andere gebruikers niet toestaan verbindende onbedoelde toegang hebben tot systeembronnen.</span><span class="sxs-lookup"><span data-stu-id="ed065-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="ed065-233">Als een rol kunt bijvoorbeeld de `Remove-Item` cmdlet en andere kunnen de `FileSystem` provider, zijn op een JEA gebruiker willekeurige bestanden op uw computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ed065-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="ed065-234">Als u meer informatie over het identificeren van de effectieve machtigingen van gebruikers kan worden gevonden in de [JEA onderwerp controle](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="ed065-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ed065-235">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="ed065-235">Next steps</span></span>

- [<span data-ttu-id="ed065-236">Een configuratiebestand sessie maken</span><span class="sxs-lookup"><span data-stu-id="ed065-236">Create a session configuration file</span></span>](session-configurations.md)

