---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: Controle en rapportage over JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688600"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="4bd40-103">Controle en rapportage over JEA</span><span class="sxs-lookup"><span data-stu-id="4bd40-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="4bd40-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4bd40-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4bd40-105">Nadat u de JEA hebt geïmplementeerd, wilt u regelmatige controle van de JEA-configuratie.</span><span class="sxs-lookup"><span data-stu-id="4bd40-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="4bd40-106">Dit helpt u bij het bepalen als de juiste personen toegang tot de JEA-eindpunt hebben en hun rollen nog steeds geschikt zijn.</span><span class="sxs-lookup"><span data-stu-id="4bd40-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="4bd40-107">Dit onderwerp beschrijft de verschillende manieren waarop u een JEA-eindpunt kunt controleren.</span><span class="sxs-lookup"><span data-stu-id="4bd40-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="4bd40-108">Geregistreerde JEA-sessies op een virtuele machine zoeken</span><span class="sxs-lookup"><span data-stu-id="4bd40-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="4bd40-109">Als u wilt controleren welke JEA-sessies op een virtuele machine zijn geregistreerd, gebruikt u de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4bd40-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="4bd40-110">De effectieve machtigingen voor het eindpunt worden weergegeven in de eigenschap 'Permission'.</span><span class="sxs-lookup"><span data-stu-id="4bd40-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="4bd40-111">Deze gebruikers hebben het recht om te verbinden met de JEA-eindpunt, maar welke functies (en, bij uitbreiding, opdrachten) ze toegang hebben tot wordt bepaald door het veld 'RoleDefinitions' in de [sessie configuratiebestand](session-configurations.md) die is gebruikt voor het registreren van de het eindpunt.</span><span class="sxs-lookup"><span data-stu-id="4bd40-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="4bd40-112">U kunt de toewijzingen van de rol in een geregistreerde JEA-eindpunt evalueren door het uitbreiden van de gegevens in de eigenschap 'RoleDefinitions'.</span><span class="sxs-lookup"><span data-stu-id="4bd40-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="4bd40-113">Beschikbare rolmogelijkheden zoeken op de machine</span><span class="sxs-lookup"><span data-stu-id="4bd40-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="4bd40-114">Rol mogelijkheid bestanden wordt alleen worden gebruikt door JEA als ze zijn opgeslagen in een map "RoleCapabilities" binnen een geldig PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="4bd40-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="4bd40-115">U kunt alle functie mogelijkheden die beschikbaar zijn op een computer vinden door te zoeken naar de lijst met beschikbare modules.</span><span class="sxs-lookup"><span data-stu-id="4bd40-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

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
> <span data-ttu-id="4bd40-116">De volgorde van de resultaten van deze functie is niet noodzakelijkerwijs de volgorde waarin de rolmogelijkheden worden geselecteerd als meerdere rolmogelijkheden dezelfde naam delen.</span><span class="sxs-lookup"><span data-stu-id="4bd40-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="4bd40-117">Effectieve rechten voor een specifieke gebruiker controleren</span><span class="sxs-lookup"><span data-stu-id="4bd40-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="4bd40-118">Wanneer u een JEA-eindpunt hebt ingesteld, kunt u om te controleren welke opdrachten zijn beschikbaar voor een specifieke gebruiker in een JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="4bd40-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="4bd40-119">U kunt [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) opsommen van de opdrachten die van toepassing op een gebruiker als ze een JEA-sessie starten met de huidige groepslidmaatschappen.</span><span class="sxs-lookup"><span data-stu-id="4bd40-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="4bd40-120">De uitvoer van `Get-PSSessionCapability` is vrijwel identiek aan die van de opgegeven gebruiker uitgevoerd `Get-Command -CommandType All` in een JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="4bd40-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="4bd40-121">Als uw gebruikers niet permanent lid zijn van groepen die zou hun aanvullende JEA rechten verleend, kan deze extra machtigingen niet overeen met deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4bd40-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="4bd40-122">Dit is meestal het geval is bij het gebruik van just-in-time privileged access management systemen kunnen gebruikers tijdelijk deel uitmaken van een beveiligingsgroep.</span><span class="sxs-lookup"><span data-stu-id="4bd40-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="4bd40-123">Evalueer altijd zorgvuldig de toewijzing van gebruikers aan rollen en de inhoud van elke rol om te controleren of gebruikers alleen toegang tot de opdrachten die nodig zijn voor hun werk doen zo min mogelijk krijgen.</span><span class="sxs-lookup"><span data-stu-id="4bd40-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="4bd40-124">PowerShell-gebeurtenislogboeken</span><span class="sxs-lookup"><span data-stu-id="4bd40-124">PowerShell event logs</span></span>

<span data-ttu-id="4bd40-125">Als u de module en/of scripts blokkeren die zich aanmelden op het systeem hebt ingeschakeld, kunt u zich om gebeurtenissen te zoeken in de Windows-gebeurtenislogboeken voor elke opdracht die een gebruiker in de JEA-sessies worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4bd40-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="4bd40-126">Als u wilt deze gebeurtenissen vinden, opent u de Windows-Logboeken, gaat u naar de **Microsoft-Windows-PowerShell/Operational** gebeurtenislogboek en zoek naar gebeurtenissen met de gebeurtenis-ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="4bd40-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="4bd40-127">Elke logboekvermelding bevat informatie over de sessie waarin de opdracht is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4bd40-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="4bd40-128">JEA-sessies, dit omvat voor belangrijke informatie over de **ConnectedUser**, dit is de werkelijke gebruiker die de JEA-sessie gemaakt, evenals de **uitvoerenals** waarin het account waarmee JEA de opdracht niet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4bd40-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="4bd40-129">Gebeurtenislogboeken van toepassingen wordt weergeven van wijzigingen van de uitvoerenals, dus met de uitgeschreven of module/script logboekregistratie is ingeschakeld is van cruciaal belang kunnen zijn voor het traceren van de aanroep van een specifieke opdracht terug naar een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="4bd40-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="4bd40-130">Logboeken voor toepassingen</span><span class="sxs-lookup"><span data-stu-id="4bd40-130">Application event logs</span></span>

<span data-ttu-id="4bd40-131">Wanneer u een opdracht in een JEA-sessie die met een externe toepassing of service uitvoert communiceert, kunnen deze toepassingen gebeurtenissen registreren bij hun eigen Logboeken.</span><span class="sxs-lookup"><span data-stu-id="4bd40-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="4bd40-132">In tegenstelling tot de PowerShell-logboeken en transcripties, andere mechanismen voor logboekregistratie geen informatie over de gebruiker met de verbinding van de JEA-sessie en zich in plaats daarvan alleen aanmelden de virtuele run as-gebruiker of groep beheerd serviceaccount.</span><span class="sxs-lookup"><span data-stu-id="4bd40-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="4bd40-133">Om te bepalen wie de opdracht is uitgevoerd, moet u raadplegen een [sessie transcript](#session-transcripts) of PowerShell-logboeken correleren met de tijd en de gebruiker wordt weergegeven in het logboek voor toepassingsgebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="4bd40-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="4bd40-134">Het logboek kunt u ook correleren WinRM worden uitgevoerd als gebruikers in een logboek voor toepassingsgebeurtenissen aan de gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="4bd40-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="4bd40-135">Gebeurtenis-ID **193** in de **Microsoft-Windows-Windows Remote Management/operationeel** logboekregistratie van records de beveiligings-id (SID)-account een naam voor zowel de gebruiker verbinding maakt en uitvoeren als gebruiker telkens wanneer een JEA sessie wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4bd40-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="4bd40-136">Transcripten van sessie</span><span class="sxs-lookup"><span data-stu-id="4bd40-136">Session transcripts</span></span>

<span data-ttu-id="4bd40-137">Als u de JEA voor het maken van een transcript voor elke gebruikerssessie hebt geconfigureerd, wordt een tekstkopie van acties van elke gebruiker worden opgeslagen in de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="4bd40-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="4bd40-138">Alle mappen van het transcript zoeken, de volgende opdracht uitvoeren als beheerder op de computer geconfigureerd met JEA:</span><span class="sxs-lookup"><span data-stu-id="4bd40-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="4bd40-139">Elke transcript begint met informatie over de tijd van de sessie is gestart, welke gebruiker verbinding maken met de sessie en welke identiteit JEA aan hen is toegewezen.</span><span class="sxs-lookup"><span data-stu-id="4bd40-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="4bd40-140">In de hoofdtekst van het transcript, wordt informatie over elke opdracht die wordt aangeroepen voor de gebruiker geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="4bd40-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="4bd40-141">De exacte syntaxis van de opdracht uitgevoerd voor de gebruiker is niet beschikbaar in JEA-sessies door de manier waarop opdrachten worden getransformeerd voor externe communicatie van PowerShell, maar u kunt nog steeds bepalen de effectieve opdracht die is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4bd40-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="4bd40-142">Hieronder vindt u een fragment voor het transcript van voorbeeld van een gebruiker die de `Get-Service Dns` in een JEA-sessie:</span><span class="sxs-lookup"><span data-stu-id="4bd40-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="4bd40-143">Voor elke opdracht die wordt uitgevoerd door een gebruiker, een regel 'CommandInvocation' worden geschreven, met een beschrijving van de cmdlet of functie van de gebruiker die wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="4bd40-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="4bd40-144">ParameterBindings Volg elke CommandInvocation voor informatie over elke parameter en de waarde die is opgegeven met de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4bd40-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="4bd40-145">In het bovenstaande voorbeeld ziet u dat de parameter 'Naam' is de waarde 'Dns' voor de cmdlet 'Get-Service' verstrekt.</span><span class="sxs-lookup"><span data-stu-id="4bd40-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="4bd40-146">De uitvoer van elke opdracht ook activeert een CommandInvocation meestal uitgaande standaardwaarden.</span><span class="sxs-lookup"><span data-stu-id="4bd40-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="4bd40-147">De InputObject Out-Default is het PowerShell-object geretourneerd door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4bd40-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="4bd40-148">De details van dat object worden afgedrukt een paar regels onder nauw mimicking wat de gebruiker zou hebben gezien.</span><span class="sxs-lookup"><span data-stu-id="4bd40-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bd40-149">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4bd40-149">See also</span></span>

- [<span data-ttu-id="4bd40-150">*PowerShell ♥ het Blue Team* blogbericht over beveiliging</span><span class="sxs-lookup"><span data-stu-id="4bd40-150">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
