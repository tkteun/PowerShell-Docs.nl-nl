---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: Controleren en rapporteren op JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017921"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="bf7ea-103">Controleren en rapporteren op JEA</span><span class="sxs-lookup"><span data-stu-id="bf7ea-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="bf7ea-104">Nadat u JEA hebt geïmplementeerd, moet u de JEA-configuratie regel matig controleren.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="bf7ea-105">Met controle kunt u beoordelen of de juiste personen toegang hebben tot het JEA-eind punt en hun toegewezen rollen nog steeds geschikt zijn.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="bf7ea-106">Geregistreerde JEA-sessies op een computer zoeken</span><span class="sxs-lookup"><span data-stu-id="bf7ea-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="bf7ea-107">Als u wilt controleren welke JEA-sessies op een computer zijn geregistreerd, gebruikt u de cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="bf7ea-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="bf7ea-108">De juiste rechten voor het eind punt worden weer gegeven in de eigenschap **Permission** .</span><span class="sxs-lookup"><span data-stu-id="bf7ea-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="bf7ea-109">Deze gebruikers hebben het recht om verbinding te maken met het JEA-eind punt.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="bf7ea-110">De rollen en opdrachten waartoe ze toegang hebben, worden echter bepaald door de eigenschap **RoleDefinitions** in het [sessie configuratie bestand](session-configurations.md) dat is gebruikt voor het registreren van het eind punt.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="bf7ea-111">Vouw de eigenschap **RoleDefinitions** uit om de roltoewijzingen in een geregistreerd JEA-eind punt te evalueren.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="bf7ea-112">Beschik bare functies op de computer zoeken</span><span class="sxs-lookup"><span data-stu-id="bf7ea-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="bf7ea-113">JEA haalt de functie mogelijkheden van `.psrc` de bestanden die zijn opgeslagen in de map **RoleCapabilities** binnen een Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="bf7ea-114">Met de volgende functie vindt u alle functie mogelijkheden die beschikbaar zijn op een computer.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-114">The following function finds all role capabilities available on a computer.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="bf7ea-115">De volg orde van de resultaten van deze functie is niet noodzakelijkerwijs de volg orde waarin de functie mogelijkheden worden geselecteerd als meerdere functie mogelijkheden dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="bf7ea-116">De juiste rechten voor een specifieke gebruiker controleren</span><span class="sxs-lookup"><span data-stu-id="bf7ea-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="bf7ea-117">De cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) inventariseert alle opdrachten die beschikbaar zijn op een JEA-eind punt op basis van de groepslid maatschappen van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="bf7ea-118">De uitvoer van `Get-PSSessionCapability` is identiek aan die van de opgegeven gebruiker die `Get-Command -CommandType All` in een JEA-sessie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="bf7ea-119">Als uw gebruikers geen permanente leden zijn van groepen die hen extra JEA-rechten verlenen, is het mogelijk dat deze cmdlet deze extra machtigingen niet weerspiegelt.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="bf7ea-120">Dit gebeurt wanneer u just-in-time privileged Access Management-systemen gebruikt om gebruikers toe te staan om tijdelijk te behoren tot een beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="bf7ea-121">Evalueer zorgvuldig de toewijzing van gebruikers aan rollen en mogelijkheden om ervoor te zorgen dat gebruikers alleen het toegangs niveau krijgen dat nodig is om hun taken uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="bf7ea-122">Power shell-gebeurtenis logboeken</span><span class="sxs-lookup"><span data-stu-id="bf7ea-122">PowerShell event logs</span></span>

<span data-ttu-id="bf7ea-123">Als u logboek registratie van de module of het script blok op het systeem hebt ingeschakeld, kunt u gebeurtenissen in de Windows-gebeurtenis logboeken zien voor elke opdracht die een gebruiker in een JEA-sessie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="bf7ea-124">Als u deze gebeurtenissen wilt vinden, opent u het gebeurtenis logboek van **micro soft-Windows-Power shell/operationeel** en zoekt u naar gebeurtenissen met gebeurtenis-id **4104**.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="bf7ea-125">Elke vermelding in het gebeurtenis logboek bevat informatie over de sessie waarin de opdracht is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="bf7ea-126">Voor JEA-sessies bevat de gebeurtenis informatie over de **ConnectedUser** en de **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="bf7ea-127">De **ConnectedUser** is de daad werkelijke gebruiker die de JEA-sessie heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="bf7ea-128">De **RunAsUser** is het account dat JEA gebruikt om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="bf7ea-129">De gebeurtenis logboeken van de toepassing tonen wijzigingen die worden aangebracht door de **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="bf7ea-130">Daarom is het inschakelen van module-en script registratie vereist voor het traceren van een specifieke opdracht aanroep naar de **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="bf7ea-131">Toepassings gebeurtenis logboeken</span><span class="sxs-lookup"><span data-stu-id="bf7ea-131">Application event logs</span></span>

<span data-ttu-id="bf7ea-132">Opdrachten die worden uitgevoerd in een JEA-sessie die interactie met externe toepassingen of services, kunnen gebeurtenissen in hun eigen gebeurtenis logboeken registreren.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="bf7ea-133">In tegens telling tot Power shell-logboeken en-Transcripten worden andere logboek registratie mechanismen niet de verbonden gebruiker van de JEA-sessie vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="bf7ea-134">In plaats daarvan registreren deze toepassingen alleen de gebruiker voor de virtuele uitvoering.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="bf7ea-135">Om te bepalen wie de opdracht heeft uitgevoerd, moet u een [transcript](#session-transcripts) voor de sessie raadplegen of de Power shell-gebeurtenis logboeken correleren met de tijd en gebruiker die wordt weer gegeven in het gebeurtenis logboek van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="bf7ea-136">Het WinRM-logboek kan ook helpen bij het correleren van gebruikers met een gebruikers rechten in een toepassings gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="bf7ea-137">Gebeurtenis-ID **193** in het **micro soft-Windows-Windows-programma voor extern beheer/operationeel** logboek registreert u de BEVEILIGINGS-id (sid) en de account naam voor de gebruiker die verbinding maakt en uitvoeren als gebruiker voor elke nieuwe JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="bf7ea-138">Transcripten van sessies</span><span class="sxs-lookup"><span data-stu-id="bf7ea-138">Session transcripts</span></span>

<span data-ttu-id="bf7ea-139">Als u JEA hebt geconfigureerd om voor elke gebruikers sessie een transcript te maken, wordt een tekst kopie van de acties van elke gebruiker opgeslagen in de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="bf7ea-140">Met de volgende opdracht (als beheerder) vindt u alle transcripten-mappen.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="bf7ea-141">Elke transcript begint met informatie over de tijd dat de sessie is gestart, de gebruiker die verbinding heeft met de sessie en de JEA-identiteit die aan hen is toegewezen.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="bf7ea-142">De hoofd tekst van de transcriptie bevat informatie over elke opdracht die de gebruiker heeft aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="bf7ea-143">De exacte syntaxis van de gebruikte opdracht is niet beschikbaar in JEA-sessies vanwege de manier waarop opdrachten worden getransformeerd voor externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="bf7ea-144">U kunt echter nog steeds de daad werkelijke opdracht bepalen die is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="bf7ea-145">Hieronder vindt u een voor beeld van een transcript fragment `Get-Service Dns` van een gebruiker die wordt uitgevoerd in een JEA-sessie:</span><span class="sxs-lookup"><span data-stu-id="bf7ea-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="bf7ea-146">Er wordt een **CommandInvocation** -regel geschreven voor elke opdracht die door een gebruiker wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="bf7ea-147">**ParameterBindings** registreert elke para meter en waarde die is opgegeven met de opdracht.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="bf7ea-148">In het vorige voor beeld ziet u dat de parameter **naam** is opgegeven met de waarde **DNS** voor de `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="bf7ea-149">Met de uitvoer van elke opdracht wordt ook een **CommandInvocation**geactiveerd, `Out-Default`meestal naar.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="bf7ea-150">De **input object** van `Out-Default` is het Power shell-object dat wordt geretourneerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="bf7ea-151">De details van dat object worden hieronder weer gegeven, met een nauw keurig mimicking wat de gebruiker zou hebben gezien.</span><span class="sxs-lookup"><span data-stu-id="bf7ea-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf7ea-152">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bf7ea-152">See also</span></span>

[<span data-ttu-id="bf7ea-153">*Power shell ♥ blog post van het blauwe team* op beveiliging</span><span class="sxs-lookup"><span data-stu-id="bf7ea-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
