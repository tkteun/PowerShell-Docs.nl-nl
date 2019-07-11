---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: Configuraties van JEA registreren
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726625"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="6203a-103">Configuraties van JEA registreren</span><span class="sxs-lookup"><span data-stu-id="6203a-103">Registering JEA Configurations</span></span>

<span data-ttu-id="6203a-104">Zodra u hebt uw [rolmogelijkheden](role-capabilities.md) en [sessie configuratiebestand](session-configurations.md) gemaakt, de laatste stap bestaat uit het registreren van de JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="6203a-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="6203a-105">De JEA-eindpunt registreren met het systeem, wordt het eindpunt beschikbaar voor gebruik door gebruikers en automation-engines.</span><span class="sxs-lookup"><span data-stu-id="6203a-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="6203a-106">De configuratie van één machine</span><span class="sxs-lookup"><span data-stu-id="6203a-106">Single machine configuration</span></span>

<span data-ttu-id="6203a-107">Voor kleine omgevingen, kunt u JEA implementeren door het registreren van de sessie configuratie bestand met de [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6203a-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="6203a-108">Voordat u begint, zorg ervoor dat de volgende vereisten wordt voldaan:</span><span class="sxs-lookup"><span data-stu-id="6203a-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="6203a-109">Een of meer rollen zijn gemaakt en geplaatst de **RoleCapabilities** map van een PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="6203a-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="6203a-110">Een configuratiebestand voor de sessie is gemaakt en getest.</span><span class="sxs-lookup"><span data-stu-id="6203a-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="6203a-111">De gebruiker die de configuratie van de JEA registreren heeft beheerdersrechten op het systeem.</span><span class="sxs-lookup"><span data-stu-id="6203a-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="6203a-112">U kunt een naam voor uw JEA-eindpunt hebt geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="6203a-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="6203a-113">De naam van de JEA-eindpunt is vereist wanneer gebruikers verbinding maken met het systeem JEA gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6203a-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="6203a-114">De [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet worden de namen van de eindpunten in een systeem.</span><span class="sxs-lookup"><span data-stu-id="6203a-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="6203a-115">Eindpunten die met beginnen `microsoft` worden doorgaans geleverd met Windows.</span><span class="sxs-lookup"><span data-stu-id="6203a-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="6203a-116">De `microsoft.powershell` -eindpunt is de standaardeindpunt dat wordt gebruikt bij het verbinden met een externe PowerShell-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="6203a-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="6203a-117">Voer de volgende opdracht om het registreren van het eindpunt.</span><span class="sxs-lookup"><span data-stu-id="6203a-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="6203a-118">De vorige opdracht de WinRM-service op het systeem opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="6203a-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="6203a-119">Dit wordt beëindigd voor alle PowerShell-sessies voor externe toegang en alle lopende DSC-configuraties.</span><span class="sxs-lookup"><span data-stu-id="6203a-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="6203a-120">Wij raden dat u productiemachines offline nemen voordat de opdracht uit om te voorkomen dat zakelijke verstoren.</span><span class="sxs-lookup"><span data-stu-id="6203a-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="6203a-121">Na de registratie, kunt u [JEA gebruiken](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="6203a-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="6203a-122">U kunt het configuratiebestand van de sessie op elk gewenst moment verwijderen.</span><span class="sxs-lookup"><span data-stu-id="6203a-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="6203a-123">Het configuratiebestand wordt niet na de registratie van het eindpunt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6203a-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="6203a-124">Configuratie met meerdere machines met DSC</span><span class="sxs-lookup"><span data-stu-id="6203a-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="6203a-125">Bij het implementeren van JEA op meerdere machines, het eenvoudigste implementatiemodel gebruikmaakt van de JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource die u wilt snel en consistent JEA implementeren op elke computer.</span><span class="sxs-lookup"><span data-stu-id="6203a-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="6203a-126">Voor het implementeren van JEA met DSC, zorg ervoor dat de volgende vereisten wordt voldaan:</span><span class="sxs-lookup"><span data-stu-id="6203a-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="6203a-127">Een of meer rolmogelijkheden zijn gemaakt en toegevoegd aan een PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="6203a-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="6203a-128">De PowerShell-module met de rollen die zijn opgeslagen op een toegankelijke (alleen-lezen) bestandsshare elke machine.</span><span class="sxs-lookup"><span data-stu-id="6203a-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="6203a-129">Instellingen voor de sessieconfiguratie van de zijn vastgesteld.</span><span class="sxs-lookup"><span data-stu-id="6203a-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="6203a-130">U hoeft te maken van een configuratiebestand voor de sessie bij het gebruik van de JEA-DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="6203a-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="6203a-131">Hebt u referenties waarmee administratieve taken op elke computer of de toegang tot de DSC-pull-server gebruikt voor het beheren van de virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="6203a-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="6203a-132">U hebt gedownload de [JEA DSC-resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="6203a-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="6203a-133">Maak een DSC-configuratie voor de JEA-eindpunt op een computer of een pull-server.</span><span class="sxs-lookup"><span data-stu-id="6203a-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="6203a-134">In deze configuratie de **JustEnoughAdministration** DSC-resource definieert het configuratiebestand van de sessie en de **bestand** resource kopieert de rolmogelijkheden van de bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="6203a-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="6203a-135">De volgende eigenschappen kunnen worden geconfigureerd met behulp van de DSC-resource:</span><span class="sxs-lookup"><span data-stu-id="6203a-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="6203a-136">Roldefinities</span><span class="sxs-lookup"><span data-stu-id="6203a-136">Role Definitions</span></span>
- <span data-ttu-id="6203a-137">Virtuele groepen</span><span class="sxs-lookup"><span data-stu-id="6203a-137">Virtual account groups</span></span>
- <span data-ttu-id="6203a-138">Naam van groep beheerd serviceaccount</span><span class="sxs-lookup"><span data-stu-id="6203a-138">Group-managed service account name</span></span>
- <span data-ttu-id="6203a-139">Transcript directory</span><span class="sxs-lookup"><span data-stu-id="6203a-139">Transcript directory</span></span>
- <span data-ttu-id="6203a-140">Schijf van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="6203a-140">User drive</span></span>
- <span data-ttu-id="6203a-141">Regels voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="6203a-141">Conditional access rules</span></span>
- <span data-ttu-id="6203a-142">Opstartscripts voor de JEA-sessie</span><span class="sxs-lookup"><span data-stu-id="6203a-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="6203a-143">De syntaxis voor elk van deze eigenschappen in een DSC-configuratie is consistent met het configuratiebestand van de PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="6203a-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="6203a-144">Hieronder volgt een voorbeeld van DSC-configuratie voor een algemene server Onderhoud-module.</span><span class="sxs-lookup"><span data-stu-id="6203a-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="6203a-145">Hierbij wordt ervan uitgegaan dat een geldig PowerShell-module met rolmogelijkheden bevindt zich op de `\\myfileshare\JEA` -bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="6203a-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="6203a-146">Vervolgens de configuratie is toegepast op een systeem door het rechtstreeks aanroepen van de [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) of bijwerken van de [pull-serverconfiguratie](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="6203a-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="6203a-147">De DSC-resource ook kunt u de standaard vervangen **Microsoft.PowerShell** eindpunt.</span><span class="sxs-lookup"><span data-stu-id="6203a-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="6203a-148">Wanneer de vervangen, registreert de resource automatisch een back-eindpunt met de naam **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="6203a-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="6203a-149">Het eindpunt van de back-up is de standaard-WinRM-ACL waarmee u kunt gebruikers van extern beheer- en lokale beheerders groepsleden om deze te openen.</span><span class="sxs-lookup"><span data-stu-id="6203a-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="6203a-150">De registratie JEA-configuraties</span><span class="sxs-lookup"><span data-stu-id="6203a-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="6203a-151">De [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet een JEA-eindpunt wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6203a-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="6203a-152">Registratie van een JEA-eindpunt wordt voorkomen dat nieuwe gebruikers van het maken van nieuwe JEA-sessies op het systeem.</span><span class="sxs-lookup"><span data-stu-id="6203a-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="6203a-153">U kunt er ook een JEA-configuratie bijwerken door een bijgewerkte sessie-configuratiebestand met dezelfde naam van het eindpunt opnieuw te registreren.</span><span class="sxs-lookup"><span data-stu-id="6203a-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="6203a-154">Een JEA registratie eindpunt zorgt ervoor dat de WinRM-service opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="6203a-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="6203a-155">Dit meest externe bewerkingen wordt uitgevoerd, met inbegrip van andere PowerShell-sessies, WMI-aanroepen en sommige beheerprogramma's-interrupts.</span><span class="sxs-lookup"><span data-stu-id="6203a-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="6203a-156">Alleen de registratie PowerShell eindpunten verwijderen tijdens gepland onderhoud.</span><span class="sxs-lookup"><span data-stu-id="6203a-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6203a-157">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="6203a-157">Next steps</span></span>

[<span data-ttu-id="6203a-158">De JEA-eindpunt testen</span><span class="sxs-lookup"><span data-stu-id="6203a-158">Test the JEA endpoint</span></span>](using-jea.md)
