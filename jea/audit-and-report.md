---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: Controle en rapportage over JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726751"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="0d0e8-103">Controle en rapportage over JEA</span><span class="sxs-lookup"><span data-stu-id="0d0e8-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="0d0e8-104">Nadat u de JEA hebt geïmplementeerd, moet u regelmatige controle van de JEA-configuratie.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="0d0e8-105">Controle kunt beoordelen u dat de juiste personen toegang tot de JEA-eindpunt hebben en hun rollen nog steeds geschikt zijn.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="0d0e8-106">Geregistreerde JEA-sessies op een virtuele machine zoeken</span><span class="sxs-lookup"><span data-stu-id="0d0e8-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="0d0e8-107">Als u wilt controleren welke JEA-sessies op een virtuele machine zijn geregistreerd, gebruikt u de [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

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

<span data-ttu-id="0d0e8-108">De effectieve machtigingen voor het eindpunt worden weergegeven in de **machtiging** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="0d0e8-109">Deze gebruikers hebben het recht om te verbinden met de JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="0d0e8-110">Echter, de functies en ze toegang tot hebben opdrachten wordt bepaald door de **RoleDefinitions** eigenschap in de [sessie configuratiebestand](session-configurations.md) die is gebruikt voor het registreren van het eindpunt.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="0d0e8-111">Vouw de **RoleDefinitions** eigenschap voor de evaluatie van de toewijzingen van de rol in een geregistreerde JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="0d0e8-112">Beschikbare rolmogelijkheden zoeken op de machine</span><span class="sxs-lookup"><span data-stu-id="0d0e8-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="0d0e8-113">JEA opgehaald rolmogelijkheden uit de `.psrc` bestanden die zijn opgeslagen de **RoleCapabilities** map in een PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="0d0e8-114">De volgende functie vindt alle rolmogelijkheden die beschikbaar zijn op een computer.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-114">The following function finds all role capabilities available on a computer.</span></span>

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
> <span data-ttu-id="0d0e8-115">De volgorde van de resultaten van deze functie is niet noodzakelijkerwijs de volgorde waarin de rolmogelijkheden worden geselecteerd als meerdere rolmogelijkheden dezelfde naam delen.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="0d0e8-116">Effectieve rechten voor een specifieke gebruiker controleren</span><span class="sxs-lookup"><span data-stu-id="0d0e8-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="0d0e8-117">De [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet inventariseren alle opdrachten die beschikbaar zijn in een JEA-eindpunt op basis van groepslidmaatschappen van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="0d0e8-118">De uitvoer van `Get-PSSessionCapability` is vrijwel identiek aan die van de opgegeven gebruiker uitgevoerd `Get-Command -CommandType All` in een JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="0d0e8-119">Als uw gebruikers niet permanent lid zijn van groepen die zou hun aanvullende JEA rechten verleend, kan deze extra machtigingen niet overeen met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="0d0e8-120">Dit gebeurt wanneer u met behulp van just-in-time bevoegde toegang beheersystemen zodat gebruikers kunnen tijdelijk deel uitmaken van een beveiligingsgroep.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="0d0e8-121">Evalueer zorgvuldig de toewijzing van gebruikers aan functies en mogelijkheden om te zorgen dat gebruikers alleen het niveau van toegang die nodig zijn voor hun werk doen.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="0d0e8-122">PowerShell-gebeurtenislogboeken</span><span class="sxs-lookup"><span data-stu-id="0d0e8-122">PowerShell event logs</span></span>

<span data-ttu-id="0d0e8-123">Als u de module of script blokkeren die zich aanmelden op het systeem hebt ingeschakeld, ziet u gebeurtenissen in de Windows-gebeurtenislogboeken voor elke opdracht die wordt uitgevoerd door een gebruiker in een JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="0d0e8-124">Als u wilt deze gebeurtenissen vinden, opent u **Microsoft-Windows-PowerShell/Operational** gebeurtenislogboek en zoek naar gebeurtenissen met de gebeurtenis-ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="0d0e8-125">Elke logboekvermelding bevat informatie over de sessie waarin de opdracht is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="0d0e8-126">Voor de JEA-sessies, de gebeurtenis vindt u informatie over de **ConnectedUser** en de **uitvoerenals**.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="0d0e8-127">De **ConnectedUser** is de werkelijke gebruiker die de JEA-sessie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="0d0e8-128">De **uitvoerenals** is het account JEA gebruikt voor het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="0d0e8-129">Gebeurtenislogboeken van toepassingen weergeven wijzigingen van de **uitvoerenals**.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="0d0e8-130">Dus script logboekregistratie is ingeschakeld en het juiste module vereist tracering van de aanroep van een specifieke opdracht terug naar de **ConnectedUser**.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="0d0e8-131">Logboeken voor toepassingen</span><span class="sxs-lookup"><span data-stu-id="0d0e8-131">Application event logs</span></span>

<span data-ttu-id="0d0e8-132">Opdrachten uitvoeren in een JEA-sessie die interactie hebben met externe toepassingen of services mogelijk gebeurtenissen op hun eigen Logboeken.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="0d0e8-133">In tegenstelling tot de PowerShell-logboeken en transcripties vastleggen geen andere mechanismen voor logboekregistratie van gebruiker met de verbinding van de JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="0d0e8-134">In plaats daarvan deze toepassingen alleen Meld u aan de virtuele run as-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="0d0e8-135">Om te bepalen wie de opdracht is uitgevoerd, moet u raadplegen een [sessie transcript](#session-transcripts) of PowerShell-logboeken correleren met de tijd en de gebruiker wordt weergegeven in het logboek voor toepassingsgebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="0d0e8-136">De WinRM-logboek kunt u het correleren van run as-gebruikers aan de gebruiker verbinding maakt in een logboek voor toepassingsgebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="0d0e8-137">Gebeurtenis-ID **193** in de **Microsoft-Windows-Windows Remote Management/operationeel** log registreert de beveiligings-id (SID) en de accountnaam voor het maken van verbinding en zowel gebruikers uitvoeren als gebruiker voor elke nieuwe JEA de sessie.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="0d0e8-138">Transcripten van sessie</span><span class="sxs-lookup"><span data-stu-id="0d0e8-138">Session transcripts</span></span>

<span data-ttu-id="0d0e8-139">Als u de JEA voor het maken van een transcript voor elke gebruikerssessie hebt geconfigureerd, wordt een tekstkopie van acties van elke gebruiker worden opgeslagen in de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="0d0e8-140">De volgende opdracht (als een beheerder) vindt u alle transcript mappen.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="0d0e8-141">Elke transcript begint met informatie over de tijd van de sessie is gestart, welke gebruiker verbinding maken met de sessie en welke identiteit JEA aan hen is toegewezen.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="0d0e8-142">De hoofdtekst van het transcript bevat informatie over elke opdracht die de gebruiker wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="0d0e8-143">De exacte syntaxis van de opdracht die wordt gebruikt, is niet beschikbaar in JEA-sessies vanwege de manier waarop opdrachten worden getransformeerd voor externe communicatie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="0d0e8-144">U kunt echter nog steeds te bepalen de effectieve opdracht die is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="0d0e8-145">Hieronder vindt u een fragment voor het transcript van voorbeeld van een gebruiker die de `Get-Service Dns` in een JEA-sessie:</span><span class="sxs-lookup"><span data-stu-id="0d0e8-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="0d0e8-146">Een **CommandInvocation** regel is geschreven voor elke opdracht die een gebruiker wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="0d0e8-147">**ParameterBindings** opnemen van elke parameter en de waarde die is opgegeven met de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="0d0e8-148">In het vorige voorbeeld, kunt u zien dat de parameter **naam** is opgegeven voor de waarde **Dns** voor de `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="0d0e8-149">De uitvoer van elke opdracht ook triggers een **CommandInvocation**, meestal naar `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="0d0e8-150">De **InputObject** van `Out-Default` wordt de PowerShell-object geretourneerd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="0d0e8-151">De details van dat object worden afgedrukt een paar regels onder nauw mimicking wat de gebruiker zou hebben gezien.</span><span class="sxs-lookup"><span data-stu-id="0d0e8-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d0e8-152">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0d0e8-152">See also</span></span>

[<span data-ttu-id="0d0e8-153">*PowerShell ♥ het Blue Team* blogbericht over beveiliging</span><span class="sxs-lookup"><span data-stu-id="0d0e8-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
