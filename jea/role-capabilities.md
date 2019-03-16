---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: Rolmogelijkheden JEA
ms.openlocfilehash: b93d206680de485d6cb7a8cb26d63afda5bf8421
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055050"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="21690-103">Rolmogelijkheden JEA</span><span class="sxs-lookup"><span data-stu-id="21690-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="21690-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="21690-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="21690-105">Bij het maken van een JEA-eindpunt, moet u definiëren een of meer "rolmogelijkheden" die worden beschreven *wat* iemand in een JEA-sessie kunt doen.</span><span class="sxs-lookup"><span data-stu-id="21690-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="21690-106">De mogelijkheid van een rol is een PowerShell-gegevensbestand met de extensie .psrc met een lijst met alle cmdlets, functies, -providers en externe programma's die beschikbaar zijn voor het koppelen van gebruikers moeten worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="21690-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="21690-107">In dit onderwerp wordt beschreven hoe u een PowerShell-rol mogelijkheid-bestand voor uw gebruikers JEA maken.</span><span class="sxs-lookup"><span data-stu-id="21690-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="21690-108">Bepalen welke opdrachten om toe te staan</span><span class="sxs-lookup"><span data-stu-id="21690-108">Determine which commands to allow</span></span>

<span data-ttu-id="21690-109">De eerste stap bij het maken van een bestand van rol mogelijkheid is om te overwegen wat de gebruikers die de rol is toegewezen toegang nodig tot.</span><span class="sxs-lookup"><span data-stu-id="21690-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="21690-110">Even kunnen duren voordat dit proces voor het verzamelen vereisten, maar het is een belangrijk proces.</span><span class="sxs-lookup"><span data-stu-id="21690-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="21690-111">Gebruikers toegang geven tot te weinig cmdlets en -functies kunt voorkomen dat ze aan hun werk gedaan te krijgen.</span><span class="sxs-lookup"><span data-stu-id="21690-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="21690-112">Toegang tot te veel cmdlets en -functies kan leiden tot meer dan u bedoeld met hun impliciete beheerdersbevoegdheden verzwakken van uw beveiliging virtualisatieproducten doen gebruikers.</span><span class="sxs-lookup"><span data-stu-id="21690-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="21690-113">Hoe u gaat over dit proces is afhankelijk van uw organisatie en doelstellingen, maar de volgende tips kunnen helpen Zorg ervoor dat u op de juiste weg bent.</span><span class="sxs-lookup"><span data-stu-id="21690-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="21690-114">**Identificeer** de gebruikers opdrachten wordt gebruikt om hun werk te doen.</span><span class="sxs-lookup"><span data-stu-id="21690-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="21690-115">Hierbij kan het controleren van IT-personeel, automatiseringsscripts controleren of Transcripten van PowerShell-sessie of de logboeken analyseren.</span><span class="sxs-lookup"><span data-stu-id="21690-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="21690-116">**Update** gebruik van opdrachtregelprogramma's voor PowerShell-equivalent, waar mogelijk, voor de beste controle- en JEA aanpassing ervaring.</span><span class="sxs-lookup"><span data-stu-id="21690-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="21690-117">Externe programma's kunnen niet worden beperkt als granulair als systeemeigen PowerShell-cmdlets en functies in JEA.</span><span class="sxs-lookup"><span data-stu-id="21690-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="21690-118">**Beperken** het bereik van de cmdlets als nodig is om alleen bepaalde parameters of parameterwaarden toestaan.</span><span class="sxs-lookup"><span data-stu-id="21690-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="21690-119">Dit is vooral belangrijk als gebruikers moeten alleen deel uitmaken van een systeem te beheren.</span><span class="sxs-lookup"><span data-stu-id="21690-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="21690-120">**Maak** aangepaste functies om complexe opdrachten of opdrachten die moeilijk te beperken in JEA te vervangen.</span><span class="sxs-lookup"><span data-stu-id="21690-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="21690-121">Een eenvoudige functie die loopt van een complexe opdracht of toepassing van extra validatielogica kan bieden extra controle voor het gemak van beheerders en eindgebruikers.</span><span class="sxs-lookup"><span data-stu-id="21690-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="21690-122">**Test** binnen het bereik de lijst met toegestane opdrachten door uw gebruikers en/of de automation-services en pas deze zo nodig.</span><span class="sxs-lookup"><span data-stu-id="21690-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="21690-123">Het is belangrijk te onthouden dat opdrachten in een JEA-sessie vaak uitgevoerd met de beheerder (of anderszins opdrachtprompt met verhoogde bevoegdheid) bevoegdheden zijn.</span><span class="sxs-lookup"><span data-stu-id="21690-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="21690-124">Zorgvuldige selectie van de beschikbare opdrachten is het belangrijk om te controleren of de JEA-eindpunt staat niet toe dat de gebruiker die de verbinding voor het verhogen van hun machtigingen.</span><span class="sxs-lookup"><span data-stu-id="21690-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="21690-125">Hieronder volgen enkele voorbeelden van opdrachten die kunnen worden gebruikt opzettelijk als toegestaan in een onbeperkte status.</span><span class="sxs-lookup"><span data-stu-id="21690-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="21690-126">Houd er rekening mee dat dit geen uitputtende lijst is en mag alleen worden gebruikt als een ook beginpunt.</span><span class="sxs-lookup"><span data-stu-id="21690-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="21690-127">Voorbeelden van mogelijk schadelijke opdrachten</span><span class="sxs-lookup"><span data-stu-id="21690-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="21690-128">Risico 's</span><span class="sxs-lookup"><span data-stu-id="21690-128">Risk</span></span> | <span data-ttu-id="21690-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="21690-129">Example</span></span> | <span data-ttu-id="21690-130">Gerelateerde opdrachten</span><span class="sxs-lookup"><span data-stu-id="21690-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="21690-131">Verlenen van de gebruiker die verbinding maakt beheerdersbevoegdheden voor het overslaan van JEA</span><span class="sxs-lookup"><span data-stu-id="21690-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="21690-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="21690-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="21690-133">Uitvoeren van willekeurige code, zoals malware, aanvallen of aangepaste scripts te omzeilen: beveiliging</span><span class="sxs-lookup"><span data-stu-id="21690-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="21690-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="21690-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="21690-135">Maak een bestand van de mogelijkheid rol</span><span class="sxs-lookup"><span data-stu-id="21690-135">Create a role capability file</span></span>

<span data-ttu-id="21690-136">Kunt u een nieuw bestand rol mogelijkheid PowerShell met de [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21690-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="21690-137">Het resulterende bestand van de rol-mogelijkheid kan worden geopend in een teksteditor en gewijzigd, zodat de gewenste opdrachten voor de rol.</span><span class="sxs-lookup"><span data-stu-id="21690-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="21690-138">De PowerShell-help-documentatie bevat enkele voorbeelden van hoe u het bestand kunt configureren.</span><span class="sxs-lookup"><span data-stu-id="21690-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="21690-139">PowerShell-cmdlets en-functies</span><span class="sxs-lookup"><span data-stu-id="21690-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="21690-140">Voor het autoriseren van gebruikers om uit te voeren PowerShell-cmdlets of functies toevoegen de naam van de cmdlet of functie in de velden VisibleCmdlets of VisibleFunctions.</span><span class="sxs-lookup"><span data-stu-id="21690-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="21690-141">Als u niet zeker weet of een opdracht is een cmdlet of functie, kunt u uitvoeren `Get-Command <name>` en de eigenschap 'CommandType' in de uitvoer controleren.</span><span class="sxs-lookup"><span data-stu-id="21690-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="21690-142">Soms is het bereik van een specifieke cmdlet of de functie is te breed voor de behoeften van uw gebruikers.</span><span class="sxs-lookup"><span data-stu-id="21690-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="21690-143">Een DNS-beheerder, bijvoorbeeld waarschijnlijk enige behoeften toegang om de DNS-service opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="21690-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="21690-144">In een omgeving met meerdere tenants waarbij tenants toegang tot Self-servicebeheer-hulpprogramma's worden verleend, moet tenants beheren met hun eigen resources.</span><span class="sxs-lookup"><span data-stu-id="21690-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="21690-145">Voor deze gevallen kunt u beperken welke parameters beschikbaar worden gesteld van de cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="21690-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="21690-146">In de meer geavanceerde scenario's moet u mogelijk ook beperken welke waarden iemand kan leveren aan deze parameters.</span><span class="sxs-lookup"><span data-stu-id="21690-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="21690-147">Rolmogelijkheden kunnen u bij het definiëren van een set toegestane waarden of een reguliere-expressiepatroon die wordt geëvalueerd om te bepalen of een opgegeven invoer is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="21690-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="21690-148">De [algemene PowerShell-parameters](https://technet.microsoft.com/library/hh847884.aspx) zijn altijd toegestaan, zelfs als u de beschikbare parameters beperken.</span><span class="sxs-lookup"><span data-stu-id="21690-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="21690-149">U dient niet expliciet vermeld in het veld Parameters.</span><span class="sxs-lookup"><span data-stu-id="21690-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="21690-150">De volgende tabel beschrijft de verschillende manieren waarop u kunt een zichtbaar cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="21690-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="21690-151">U kunt combineren en matchen een van de hieronder in de VisibleCmdlets veld.</span><span class="sxs-lookup"><span data-stu-id="21690-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="21690-152">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="21690-152">Example</span></span>                                                                                      | <span data-ttu-id="21690-153">Use-case</span><span class="sxs-lookup"><span data-stu-id="21690-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="21690-154">`'My-Func'` of `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="21690-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="21690-155">Kan de gebruiker om uit te voeren `My-Func` zonder beperkingen voor de parameters.</span><span class="sxs-lookup"><span data-stu-id="21690-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="21690-156">Kan de gebruiker om uit te voeren `My-Func` uit de module `MyModule` zonder beperkingen voor de parameters.</span><span class="sxs-lookup"><span data-stu-id="21690-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="21690-157">Kan de gebruiker een cmdlet of de functie uitvoeren met de term `My`.</span><span class="sxs-lookup"><span data-stu-id="21690-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="21690-158">Hiermee kan de gebruiker een cmdlet of de functie uitvoeren met het zelfstandig naamwoord `Func`.</span><span class="sxs-lookup"><span data-stu-id="21690-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="21690-159">Kan de gebruiker om uit te voeren `My-Func` met de `Param1` en/of `Param2` parameters.</span><span class="sxs-lookup"><span data-stu-id="21690-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="21690-160">Elke waarde kan worden opgegeven met de parameters.</span><span class="sxs-lookup"><span data-stu-id="21690-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="21690-161">Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter.</span><span class="sxs-lookup"><span data-stu-id="21690-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="21690-162">Alleen "Value1" en 'Value2' kan worden opgegeven voor de parameter.</span><span class="sxs-lookup"><span data-stu-id="21690-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="21690-163">Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter.</span><span class="sxs-lookup"><span data-stu-id="21690-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="21690-164">Een willekeurige waarde beginnen met 'contoso' kan worden opgegeven voor de parameter.</span><span class="sxs-lookup"><span data-stu-id="21690-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="21690-165">Het verdient voor aanbevolen procedures voor beveiliging, geen jokertekens gebruiken bij het definiëren van zichtbaar cmdlets of functies.</span><span class="sxs-lookup"><span data-stu-id="21690-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="21690-166">In plaats daarvan moet u elke vertrouwde opdracht om te controleren of er worden geen andere opdrachten die de dezelfde naamgevingsschema delen per ongeluk zijn gemachtigd expliciet vermelden.</span><span class="sxs-lookup"><span data-stu-id="21690-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="21690-167">U kunt een ValidatePattern en ValidateSet toepassen op de dezelfde cmdlet of functie.</span><span class="sxs-lookup"><span data-stu-id="21690-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="21690-168">Als u dit doet, is de ValidatePattern overschrijft de ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="21690-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="21690-169">Bekijk voor meer informatie over ValidatePattern [dit *Hallo, Scripting Guy!* boeken](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) en de [PowerShell reguliere expressies](https://technet.microsoft.com/library/hh847880.aspx) -referentie-inhoud.</span><span class="sxs-lookup"><span data-stu-id="21690-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="21690-170">Externe opdrachten en PowerShell-scripts toestaan</span><span class="sxs-lookup"><span data-stu-id="21690-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="21690-171">Als u wilt toestaan dat gebruikers uitvoerbare bestanden en PowerShell-scripts (.ps1) uitvoeren in een JEA-sessie, moet u het volledige pad toevoegen aan elk programma in het veld VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="21690-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="21690-172">Het wordt aanbevolen, waar mogelijk gebruik van PowerShell-cmdlet/functie equivalenten van elke externe uitvoerbare bestanden verleent u onbevoegde gebruikers nadat u hebt de controle over welke parameters met PowerShell-cmdlets/functies zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="21690-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="21690-173">Veel uitvoerbare bestanden kunt u zowel de huidige status lezen en wijzig deze alleen door op te geven van de verschillende parameters.</span><span class="sxs-lookup"><span data-stu-id="21690-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="21690-174">Neem bijvoorbeeld de rol van een bestand van een serverbeheerder bent om te controleren welke netwerkshares worden gehost door de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="21690-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="21690-175">Een manier om te controleren, is met `net share`.</span><span class="sxs-lookup"><span data-stu-id="21690-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="21690-176">Echter, zodat net.exe is zeer gevaarlijke omdat de beheerder kan net zo eenvoudig gebruik van de opdracht om te krijgen van beheerdersbevoegdheden met `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="21690-176">However, allowing net.exe is very dangerous because the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="21690-177">Er is een betere benadering om toe te staan [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) die geven hetzelfde resultaat, maar een nog veel meer beperkt bereik heeft.</span><span class="sxs-lookup"><span data-stu-id="21690-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="21690-178">Wanneer externe opdrachten beschikbaar maken voor gebruikers in een JEA-sessie, is altijd opgeven van het volledige pad naar het uitvoerbare bestand om te controleren of een gelijknamige (en mogelijk schadelijke) programma elders geplaatst op het systeem niet in plaats daarvan wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="21690-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicious) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="21690-179">Toegang tot de PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="21690-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="21690-180">Er zijn geen PowerShell-providers zijn standaard beschikbaar in JEA-sessies.</span><span class="sxs-lookup"><span data-stu-id="21690-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="21690-181">Dit is vooral vermindert het risico van gevoelige informatie en configuratie-instellingen die worden doorgegeven aan de gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="21690-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="21690-182">Indien nodig, kunt u de toegang tot de PowerShell-providers met behulp van de `VisibleProviders` opdracht.</span><span class="sxs-lookup"><span data-stu-id="21690-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="21690-183">Voor een volledige lijst met providers, voert u `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="21690-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="21690-184">Voor eenvoudige taken waarvoor toegang tot het bestandssysteem, register, certificaatarchief of andere gevoelige-providers, kunt u ook overwegen schrijven van een aangepaste functie die geschikt is voor de provider namens de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="21690-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="21690-185">Functies, -cmdlets en externe programma's die beschikbaar in een JEA-sessie zijn vallen niet onder de dezelfde beperkingen als JEA--ze hebben standaard toegang tot alle elke provider.</span><span class="sxs-lookup"><span data-stu-id="21690-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="21690-186">Ook kunt u overwegen de [schijf van de gebruiker](session-configurations.md#user-drive) wanneer bestanden zijn gekopieerd naar/van een JEA-eindpunt is vereist.</span><span class="sxs-lookup"><span data-stu-id="21690-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="21690-187">Het maken van aangepaste functies</span><span class="sxs-lookup"><span data-stu-id="21690-187">Creating custom functions</span></span>

<span data-ttu-id="21690-188">U kunt aangepaste functies in een bestand rol mogelijkheid complexe taken vereenvoudigen voor uw eindgebruikers maken.</span><span class="sxs-lookup"><span data-stu-id="21690-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="21690-189">Aangepaste functies zijn ook handig wanneer u geavanceerde validatielogica voor cmdlet parameterwaarden vereist.</span><span class="sxs-lookup"><span data-stu-id="21690-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="21690-190">U kunt eenvoudig functies schrijven in de **FunctionDefinitions** veld:</span><span class="sxs-lookup"><span data-stu-id="21690-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

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
> <span data-ttu-id="21690-191">Vergeet niet om toe te voegen van de naam van uw aangepaste functies voor de **VisibleFunctions** veld, zodat ze kunnen worden uitgevoerd door de JEA-gebruikers.</span><span class="sxs-lookup"><span data-stu-id="21690-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="21690-192">De hoofdtekst (scriptblok) van aangepaste functies in de standaardmodus voor de taal voor het systeem wordt uitgevoerd en niet is onderworpen aan beperkingen voor de JEA-taal.</span><span class="sxs-lookup"><span data-stu-id="21690-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="21690-193">Dit betekent dat functies kunnen toegang krijgen het bestandssysteem en register tot en uitvoeren van opdrachten die zijn niet zichtbaar in het bestand van de mogelijkheid rol.</span><span class="sxs-lookup"><span data-stu-id="21690-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="21690-194">Let erop om te voorkomen waardoor arbitraire code moet worden uitgevoerd wanneer met behulp van parameters en te voorkomen dat invoer van de gebruiker rechtstreeks in de cmdlets, zoals uitvoeromleiding `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="21690-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="21690-195">In het bovenstaande voorbeeld ziet u dat de naam van de volledig gekwalificeerde module (FQMN) `Microsoft.PowerShell.Utility\Select-Object` is gebruikt in plaats van de steno `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="21690-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="21690-196">Functies die zijn gedefinieerd in de rol mogelijkheid bestanden zijn nog steeds afhankelijk van het bereik van JEA-sessies, waaronder de proxyfuncties JEA wordt gemaakt voor het beperken van bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="21690-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="21690-197">Select-Object is een standaard beperkte cmdlet in alle JEA-sessies die is niet toegestaan om willekeurige eigenschappen van objecten te selecteren.</span><span class="sxs-lookup"><span data-stu-id="21690-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="21690-198">Voor het gebruik van de onbeperkte Select-Object in de functies, moet u expliciet de volledige implementatie aanvragen door de FQMN op te geven.</span><span class="sxs-lookup"><span data-stu-id="21690-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="21690-199">Een beperkte cmdlet in een JEA-sessie wordt vertonen hetzelfde gedrag wordt aangeroepen vanuit een functie, in overeenstemming met de PowerShell [opdracht prioriteit](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span><span class="sxs-lookup"><span data-stu-id="21690-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="21690-200">Als u een groot aantal aangepaste functies ontwikkelt, kan het zijn gemakkelijker te plaatsen een [PowerShell-Script-Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="21690-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="21690-201">U kunt deze functies vervolgens zichtbaar in de JEA-sessie met behulp van het veld VisibleFunctions zoals u zou met ingebouwde en van derden modules doen maken.</span><span class="sxs-lookup"><span data-stu-id="21690-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="21690-202">Rolmogelijkheden plaatsen in een module</span><span class="sxs-lookup"><span data-stu-id="21690-202">Place role capabilities in a module</span></span>

<span data-ttu-id="21690-203">In de volgorde voor PowerShell om een rol mogelijkheid-bestand te zoeken, moet deze worden opgeslagen in een map 'RoleCapabilities' in een PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="21690-203">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="21690-204">De module kan worden opgeslagen in een map die is opgenomen in de `$env:PSModulePath` omgevingsvariabele, maar u moet niet plaats deze in System32 (gereserveerd voor ingebouwde modules) of een map waar de niet-vertrouwde, verbinding te maken van gebruikers kan de bestanden wijzigen.</span><span class="sxs-lookup"><span data-stu-id="21690-204">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="21690-205">Hieronder volgt een voorbeeld van het maken van een eenvoudige PowerShell-script-module met de naam *ContosoJEA* in het pad 'Program Files'.</span><span class="sxs-lookup"><span data-stu-id="21690-205">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

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

<span data-ttu-id="21690-206">Zie [inzicht krijgen in een PowerShell-Module](https://msdn.microsoft.com/library/dd878324.aspx) voor meer informatie over PowerShell-modules, modulemanifesten en de omgevingsvariabele PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="21690-206">See [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="21690-207">Rolmogelijkheden bijwerken</span><span class="sxs-lookup"><span data-stu-id="21690-207">Updating role capabilities</span></span>

<span data-ttu-id="21690-208">U kunt een bestand van de mogelijkheid rol op elk gewenst moment bijwerken door gewoon wijzigingen aan de rol mogelijkheid bestand worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="21690-208">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="21690-209">Een nieuwe JEA-sessies gestart nadat de mogelijkheid van de rol is bijgewerkt, verschijnt op de nieuwe mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="21690-209">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="21690-210">Dit is de reden waarom het beheren van toegang tot de map van de mogelijkheden van rol is dus belangrijk.</span><span class="sxs-lookup"><span data-stu-id="21690-210">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="21690-211">Alleen uiterst vertrouwde beheerders mogen rol mogelijkheid bestanden te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="21690-211">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="21690-212">Als een niet-vertrouwde gebruiker rol mogelijkheid bestanden wijzigt kan, kunnen ze eenvoudig geven zelf toegang aan de cmdlets waarmee ze zijn bevoegdheden te verhogen.</span><span class="sxs-lookup"><span data-stu-id="21690-212">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>

<span data-ttu-id="21690-213">Voor beheerders het vergrendelen van toegang tot de rolmogelijkheden wilt, zorg ervoor dat lokaal systeem, leestoegang heeft tot de rol mogelijkheid bestanden en met modules.</span><span class="sxs-lookup"><span data-stu-id="21690-213">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="21690-214">Hoe rolmogelijkheden worden samengevoegd</span><span class="sxs-lookup"><span data-stu-id="21690-214">How role capabilities are merged</span></span>

<span data-ttu-id="21690-215">Gebruikers kunnen toegang tot meerdere rolmogelijkheden worden verleend wanneer ze een JEA-sessie, afhankelijk van de rol-toewijzingen in de [sessie configuratiebestand](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="21690-215">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="21690-216">Als dit gebeurt, JEA probeert te geven van de gebruiker de *meest strikte* reeks opdrachten die zijn toegestaan door een van de rollen.</span><span class="sxs-lookup"><span data-stu-id="21690-216">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="21690-217">**VisibleCmdlets en VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="21690-217">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="21690-218">De meest complexe logica voor het samenvoegen van invloed is op de cmdlets en -functies, waarvoor hun parameters en parameterwaarden in JEA beperkt.</span><span class="sxs-lookup"><span data-stu-id="21690-218">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="21690-219">De regels zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="21690-219">The rules are as follows:</span></span>

1. <span data-ttu-id="21690-220">Als een cmdlet is alleen zichtbaar zijn in één rol, worden deze zichtbaar is voor de gebruiker met de beperkingen van toepassing parameter.</span><span class="sxs-lookup"><span data-stu-id="21690-220">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="21690-221">Als een cmdlet is zichtbaar in meer dan één rol, en elke rol de dezelfde beperkingen met betrekking tot de cmdlet heeft, zijn de cmdlet zichtbaar voor de gebruiker met deze beperkingen.</span><span class="sxs-lookup"><span data-stu-id="21690-221">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="21690-222">Als een cmdlet is zichtbaar in meer dan één rol, en elke rol maakt het mogelijk een andere set parameters, zijn de cmdlet en alle parameters gedefinieerd voor elke rol zichtbaar voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="21690-222">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="21690-223">Als één rol geen beperkingen met betrekking tot de parameters heeft, wordt alle parameters worden toegestaan.</span><span class="sxs-lookup"><span data-stu-id="21690-223">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="21690-224">Als één rol een set valideren of patroon valideren voor een cmdlet-parameter definieert en de andere rol kunt u de parameter, maar legt geen beperkingen voor de parameterwaarden, wordt de set valideren of het patroon worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="21690-224">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="21690-225">Als een set valideren voor de dezelfde cmdlet-parameter in meer dan één rol is gedefinieerd, worden alle waarden uit alle valideren sets is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="21690-225">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="21690-226">Als een patroon valideren voor de dezelfde cmdlet-parameter in meer dan één rol is gedefinieerd, worden alle waarden die overeenkomen met een van de patronen worden toegestaan.</span><span class="sxs-lookup"><span data-stu-id="21690-226">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="21690-227">Als een set valideren is gedefinieerd in een of meer rollen, en een patroon valideren is gedefinieerd in een andere rol voor de dezelfde cmdlet-parameter, de set valideren wordt genegeerd en regel (6) is van toepassing op de resterende valideren patronen.</span><span class="sxs-lookup"><span data-stu-id="21690-227">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="21690-228">Hieronder volgt een voorbeeld van hoe de functies worden samengevoegd op basis van deze regels:</span><span class="sxs-lookup"><span data-stu-id="21690-228">Below is an example of how roles are merged according to these rules:</span></span>

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

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

<span data-ttu-id="21690-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="21690-229">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="21690-230">Alle andere velden in het bestand van de mogelijkheid rol worden alleen toegevoegd aan een volledige reeks van toegestane externe opdrachten, aliassen, providers en opstartscripts.</span><span class="sxs-lookup"><span data-stu-id="21690-230">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="21690-231">Elke opdracht, alias, provider of script beschikbaar is in één rol-functie is beschikbaar voor de JEA-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="21690-231">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="21690-232">Wees voorzichtig om ervoor te zorgen dat de gecombineerde set-providers van een rol mogelijkheden en functies-cmdlets/opdrachten van een andere gebruikers niet toestaan verbindende onbedoelde toegang tot systeemresources.</span><span class="sxs-lookup"><span data-stu-id="21690-232">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="21690-233">Bijvoorbeeld, als een functie kan de `Remove-Item` cmdlet en andere kunnen de `FileSystem` provider, zijn op een JEA-gebruiker willekeurige bestanden op uw computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="21690-233">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="21690-234">Als u meer informatie over het identificeren van de effectieve machtigingen van gebruikers te vinden in de [JEA onderwerp controle](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="21690-234">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="21690-235">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="21690-235">Next steps</span></span>

- [<span data-ttu-id="21690-236">Een sessie-configuratiebestand maken</span><span class="sxs-lookup"><span data-stu-id="21690-236">Create a session configuration file</span></span>](session-configurations.md)
