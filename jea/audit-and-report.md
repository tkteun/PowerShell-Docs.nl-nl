---
ms.date: 06/12/2017
keywords: jea powershell beveiliging
title: Controle en rapportage over JEA
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188849"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="32f30-103">Controle en rapportage over JEA</span><span class="sxs-lookup"><span data-stu-id="32f30-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="32f30-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="32f30-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="32f30-105">Nadat u JEA hebt geïmplementeerd, wilt u de configuratie van de JEA regelmatig te controleren.</span><span class="sxs-lookup"><span data-stu-id="32f30-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="32f30-106">Dit helpt u vast te stellen als de juiste personen toegang tot het eindpunt JEA hebben en hun rollen steeds van toepassing.</span><span class="sxs-lookup"><span data-stu-id="32f30-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="32f30-107">Dit onderwerp beschrijft de verschillende manieren waarop u een eindpunt JEA kunt controleren.</span><span class="sxs-lookup"><span data-stu-id="32f30-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="32f30-108">Geregistreerde JEA sessies op een machine vinden</span><span class="sxs-lookup"><span data-stu-id="32f30-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="32f30-109">Gebruiken om te controleren welke JEA-sessies zijn geregistreerd op een computer, de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32f30-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="32f30-110">De effectieve rechten voor het eindpunt worden weergegeven in de eigenschap 'Permission'.</span><span class="sxs-lookup"><span data-stu-id="32f30-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="32f30-111">Deze gebruikers hebben het recht om te verbinden met het eindpunt JEA, maar welke rollen (en, bij uitbreiding, opdrachten) die toegang hebben tot wordt bepaald door het veld 'RoleDefinitions' in de [sessie configuratiebestand](session-configurations.md) die is gebruikt voor het registreren van de het eindpunt.</span><span class="sxs-lookup"><span data-stu-id="32f30-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="32f30-112">U kunt de toewijzingen van de rol in een geregistreerde JEA eindpunt evalueren door het uitbreiden van de gegevens in de eigenschap 'RoleDefinitions'.</span><span class="sxs-lookup"><span data-stu-id="32f30-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="32f30-113">Mogelijkheden van de rol die beschikbaar is op de machine vinden</span><span class="sxs-lookup"><span data-stu-id="32f30-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="32f30-114">Rol capability-bestanden wordt alleen gebruikt door JEA als ze zijn opgeslagen in een map 'RoleCapabilities' binnen een geldig PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="32f30-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="32f30-115">U vindt alle rol mogelijkheden die beschikbaar zijn op een computer door te zoeken in de lijst met beschikbare modules.</span><span class="sxs-lookup"><span data-stu-id="32f30-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="32f30-116">De volgorde van de resultaten van deze functie is niet per se de volgorde waarin de mogelijkheden van de rol worden geselecteerd als meerdere mogelijkheden van de functie dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="32f30-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="32f30-117">Controleer de rechten voor effectieve voor een specifieke gebruiker</span><span class="sxs-lookup"><span data-stu-id="32f30-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="32f30-118">Nadat u een eindpunt JEA hebt ingesteld, wilt u mogelijk controleren welke opdrachten beschikbaar zijn voor een specifieke gebruiker in een sessie JEA.</span><span class="sxs-lookup"><span data-stu-id="32f30-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="32f30-119">U kunt [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) opsommen van de opdrachten die van toepassing op een gebruiker alsof ze een JEA-sessie starten met hun huidige groepslidmaatschap.</span><span class="sxs-lookup"><span data-stu-id="32f30-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="32f30-120">De uitvoer van `Get-PSSessionCapability` is gelijk aan dat de opgegeven gebruiker uitgevoerd `Get-Command -CommandType All` in een sessie JEA.</span><span class="sxs-lookup"><span data-stu-id="32f30-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="32f30-121">Als uw gebruikers niet permanent lid zijn van groepen die u zou hen aanvullende JEA rechten verleend zijn, kan deze extra machtigingen niet overeen met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32f30-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="32f30-122">Dit is doorgaans het geval bij gebruik van systemen voor just-in-time privileged access management zodat gebruikers tijdelijk aan een beveiligingsgroep horen.</span><span class="sxs-lookup"><span data-stu-id="32f30-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="32f30-123">De toewijzing van gebruikers aan rollen altijd zorgvuldig te evalueren en de inhoud van elke rol zodat gebruikers krijgen alleen toegang tot de kortste opdrachten die nodig zijn voor hun werk te doen.</span><span class="sxs-lookup"><span data-stu-id="32f30-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="32f30-124">PowerShell-gebeurtenislogboeken</span><span class="sxs-lookup"><span data-stu-id="32f30-124">PowerShell event logs</span></span>

<span data-ttu-id="32f30-125">Als u de module en/of script blok logboekregistratie op het systeem hebt ingeschakeld, wordt u mogelijk zijn om te zoeken die in de Windows-gebeurtenislogboeken voor elke opdracht die een gebruiker wordt uitgevoerd in hun JEA-sessies.</span><span class="sxs-lookup"><span data-stu-id="32f30-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="32f30-126">Als u deze gebeurtenissen zoekt, de Windows-Logboeken te openen, gaat u naar de **Microsoft-Windows-PowerShell/operationeel** gebeurtenislogboek en zoeken naar gebeurtenissen met de gebeurtenis-ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="32f30-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="32f30-127">Elke logboekvermelding bevat informatie over de sessie waarin de opdracht is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32f30-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="32f30-128">JEA sessies, dit omvat voor belangrijke informatie over de **ConnectedUser**, dit is de werkelijke gebruiker die de sessie JEA gemaakt, evenals de **uitvoerenals** die het account JEA waarmee wordt aangegeven de opdracht niet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="32f30-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="32f30-129">Gebeurtenislogboeken van toepassingen wordt weergeven van wijzigingen van de uitvoerenals rekening transcripties of module-script-logboekregistratie ingeschakeld is essentieel om te kunnen traceren van een aanroep van de specifieke opdracht terug naar een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="32f30-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="32f30-130">Gebeurtenislogboeken van toepassingen</span><span class="sxs-lookup"><span data-stu-id="32f30-130">Application event logs</span></span>

<span data-ttu-id="32f30-131">Wanneer u een opdracht in een sessie JEA die met een externe toepassing of service uitvoert communiceert, kunnen deze toepassingen gebeurtenissen vastleggen in hun eigen Logboeken.</span><span class="sxs-lookup"><span data-stu-id="32f30-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="32f30-132">In tegenstelling tot PowerShell logboeken en transcripties andere mechanismen voor logboekregistratie niet de verbonden gebruiker van de sessie JEA vast en wordt in plaats daarvan alleen Meld u de virtuele run as-gebruiker of groep beheerd serviceaccount.</span><span class="sxs-lookup"><span data-stu-id="32f30-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="32f30-133">Om te bepalen wie de opdracht hebt uitgevoerd, moet u raadpleegt u een [tekst sessie](#session-transcripts) of PowerShell logboeken correleren met de tijd en de gebruiker wordt weergegeven in het logboek voor toepassingsgebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="32f30-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="32f30-134">De WinRM logboek kunt u ook correleren uitgevoerd als gebruikers in een logboek voor toepassingsgebeurtenissen aan de gebruiker verbinding probeert te maken.</span><span class="sxs-lookup"><span data-stu-id="32f30-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="32f30-135">Gebeurtenis-ID **193** in de **Microsoft Windows Windows Remote Management/operationeel** logboekregistratie records de beveiligings-id (SID)-account een naam voor zowel de gebruiker verbinding probeert te maken en uitvoeren als gebruiker telkens wanneer een JEA sessie wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="32f30-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="32f30-136">Sessie transcripties</span><span class="sxs-lookup"><span data-stu-id="32f30-136">Session transcripts</span></span>

<span data-ttu-id="32f30-137">Als u JEA voor het maken van een van de tekst voor elke gebruikerssessie hebt geconfigureerd, wordt een tekstkopie van acties van elke gebruiker opgeslagen in de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="32f30-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="32f30-138">Alle mappen van de tekst zoeken, voer de volgende opdracht als beheerder op de computer geconfigureerd met JEA:</span><span class="sxs-lookup"><span data-stu-id="32f30-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="32f30-139">Elk van de tekst begint met informatie over de tijd van de sessie is gestart, welke gebruiker verbonden met de sessie en welke identiteit JEA aan hen is toegewezen.</span><span class="sxs-lookup"><span data-stu-id="32f30-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="32f30-140">In de hoofdtekst van de tekst van de gegevens vastgelegd over elke opdracht die de gebruiker wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="32f30-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="32f30-141">De syntaxis van de opdracht uitgevoerd voor de gebruiker is niet beschikbaar in JEA sessies vanwege de manier waarop opdrachten zijn getransformeerd voor externe communicatie van PowerShell, maar u kunt nog steeds bepalen de effectieve opdracht die werd uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32f30-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="32f30-142">Hieronder volgt een voorbeeld van de tekst van fragment van een gebruiker met `Get-Service Dns` in een sessie JEA:</span><span class="sxs-lookup"><span data-stu-id="32f30-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="32f30-143">Voor elke opdracht die een gebruiker wordt uitgevoerd, een regel 'CommandInvocation' worden geschreven, met een beschrijving van de cmdlet of functie van de gebruiker die is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="32f30-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="32f30-144">ParameterBindings Volg elke CommandInvocation om aan te geven over elke parameter en de waarde die is opgegeven met de opdracht.</span><span class="sxs-lookup"><span data-stu-id="32f30-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="32f30-145">In het bovenstaande voorbeeld ziet u dat de parameter 'Name' is de waarde 'Dns' voor de cmdlet 'Get-Service' opgegeven.</span><span class="sxs-lookup"><span data-stu-id="32f30-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="32f30-146">De uitvoer van elke opdracht ook activeren een CommandInvocation meestal uitgaande standaardwaarden.</span><span class="sxs-lookup"><span data-stu-id="32f30-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="32f30-147">De InputObject Out-Default is het PowerShell-object geretourneerd van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="32f30-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="32f30-148">De details van dat object worden afgedrukt een paar regels hieronder nauw mimicking wat de gebruiker zou hebben gezien.</span><span class="sxs-lookup"><span data-stu-id="32f30-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="32f30-149">Zie ook</span><span class="sxs-lookup"><span data-stu-id="32f30-149">See also</span></span>

- [<span data-ttu-id="32f30-150">Acties van de gebruiker in een sessie JEA controleren</span><span class="sxs-lookup"><span data-stu-id="32f30-150">Audit user actions in a JEA session</span></span>](audit-and-report.md)
- [<span data-ttu-id="32f30-151">*PowerShell ♥ het Team van blauw* blogbericht op beveiliging</span><span class="sxs-lookup"><span data-stu-id="32f30-151">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)