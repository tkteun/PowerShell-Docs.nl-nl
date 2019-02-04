---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: Configuraties van JEA registreren
ms.openlocfilehash: 160aa95283da57a10aad5fdd4043adb1354a5db5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55689062"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="132c9-103">Configuraties van JEA registreren</span><span class="sxs-lookup"><span data-stu-id="132c9-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="132c9-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="132c9-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="132c9-105">Zodra u hebt uw [rolmogelijkheden](role-capabilities.md) en [sessie configuratiebestand](session-configurations.md) gemaakt, de laatste stap voordat u de JEA kunt gebruiken is de JEA-eindpunt registreren.</span><span class="sxs-lookup"><span data-stu-id="132c9-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="132c9-106">De JEA-eindpunt registreren met het systeem, wordt het eindpunt beschikbaar voor gebruik door gebruikers en automation-engines.</span><span class="sxs-lookup"><span data-stu-id="132c9-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="132c9-107">De configuratie van één machine</span><span class="sxs-lookup"><span data-stu-id="132c9-107">Single machine configuration</span></span>

<span data-ttu-id="132c9-108">Voor kleine omgevingen, kunt u JEA implementeren door het registreren van de sessie configuratie bestand met de [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="132c9-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="132c9-109">Voordat u begint, zorg ervoor dat de volgende vereisten wordt voldaan:</span><span class="sxs-lookup"><span data-stu-id="132c9-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="132c9-110">Een of meer rollen is gemaakt en opgeslagen in de map 'RoleCapabilities' van een geldig PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="132c9-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="132c9-111">Een configuratiebestand voor de sessie is gemaakt en getest.</span><span class="sxs-lookup"><span data-stu-id="132c9-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="132c9-112">De gebruiker die de configuratie van de JEA registreren heeft administrator-rechten op de systemen.</span><span class="sxs-lookup"><span data-stu-id="132c9-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="132c9-113">U moet ook een naam voor uw JEA-eindpunt selecteren.</span><span class="sxs-lookup"><span data-stu-id="132c9-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="132c9-114">De naam van de JEA-eindpunt is vereist wanneer gebruikers op het systeem met JEA verbinding wilt maken.</span><span class="sxs-lookup"><span data-stu-id="132c9-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="132c9-115">U kunt de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet om te controleren of de namen van bestaande eindpunten op het systeem.</span><span class="sxs-lookup"><span data-stu-id="132c9-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="132c9-116">Eindpunten die met 'microsoft beginnen' worden doorgaans geleverd met Windows.</span><span class="sxs-lookup"><span data-stu-id="132c9-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="132c9-117">Het eindpunt 'microsoft.powershell' is de standaardeindpunt dat wordt gebruikt bij het verbinden met een externe PowerShell-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="132c9-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="132c9-118">Wanneer u een passende naam voor uw JEA-eindpunt hebt bepaald, voer de volgende opdracht voor het registreren van het eindpunt.</span><span class="sxs-lookup"><span data-stu-id="132c9-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="132c9-119">De bovenstaande opdracht de WinRM-service op het systeem opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="132c9-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="132c9-120">Dit wordt beëindigd voor alle externe communicatie van PowerShell-sessies, evenals alle lopende DSC-configuraties.</span><span class="sxs-lookup"><span data-stu-id="132c9-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="132c9-121">Het is raadzaam dat u een productiemachines offline nemen voordat de opdracht uit om te voorkomen dat zakelijke verstoren.</span><span class="sxs-lookup"><span data-stu-id="132c9-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="132c9-122">Als de registratie is geslaagd, bent u klaar om te [JEA gebruiken](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="132c9-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="132c9-123">U kunt het configuratiebestand van de sessie op elk gewenst moment; verwijderen het wordt niet gebruikt na de registratie van het eindpunt.</span><span class="sxs-lookup"><span data-stu-id="132c9-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="132c9-124">Configuratie met meerdere machines met DSC</span><span class="sxs-lookup"><span data-stu-id="132c9-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="132c9-125">Als u JEA op meerdere machines implementeert, wordt het eenvoudigste implementatiemodel is het gebruik van de JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource die u wilt snel en consistent JEA implementeren op elke computer.</span><span class="sxs-lookup"><span data-stu-id="132c9-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="132c9-126">Voor het implementeren van JEA met DSC, die u wilt controleren of dat de volgende vereisten wordt voldaan:</span><span class="sxs-lookup"><span data-stu-id="132c9-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="132c9-127">Een of meer rolmogelijkheden zijn gemaakt en toegevoegd aan een geldig PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="132c9-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="132c9-128">De PowerShell-module met de rollen die zijn opgeslagen op een toegankelijke (alleen-lezen) bestandsshare elke machine.</span><span class="sxs-lookup"><span data-stu-id="132c9-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="132c9-129">Instellingen voor de sessieconfiguratie van de zijn vastgesteld.</span><span class="sxs-lookup"><span data-stu-id="132c9-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="132c9-130">U hoeft niet te maken van een configuratiebestand voor de sessie bij het gebruik van de JEA-DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="132c9-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="132c9-131">U hebt de referenties waarmee u kunt beheeracties uitvoeren op elke machine of toegang hebben tot een DSC-pull-server gebruikt voor het beheren van de machines.</span><span class="sxs-lookup"><span data-stu-id="132c9-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="132c9-132">U hebt gedownload de [JEA DSC-resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="132c9-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="132c9-133">Op een doel (of pull-server, als u van een gebruikmaakt), een DSC-configuratie voor de JEA-eindpunt te maken.</span><span class="sxs-lookup"><span data-stu-id="132c9-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="132c9-134">In deze configuratie gebruikt u de JustEnoughAdministration DSC-resource voor het instellen van het configuratiebestand van de sessie en de resource bestand moeten worden gekopieerd van de rolmogelijkheden van de bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="132c9-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="132c9-135">De volgende eigenschappen kunnen worden geconfigureerd met behulp van de DSC-resource:</span><span class="sxs-lookup"><span data-stu-id="132c9-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="132c9-136">Roldefinities</span><span class="sxs-lookup"><span data-stu-id="132c9-136">Role Definitions</span></span>
- <span data-ttu-id="132c9-137">Virtuele groepen</span><span class="sxs-lookup"><span data-stu-id="132c9-137">Virtual Account groups</span></span>
- <span data-ttu-id="132c9-138">Naam van groep beheerd serviceaccount</span><span class="sxs-lookup"><span data-stu-id="132c9-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="132c9-139">Transcript directory</span><span class="sxs-lookup"><span data-stu-id="132c9-139">Transcript directory</span></span>
- <span data-ttu-id="132c9-140">Schijf van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="132c9-140">User drive</span></span>
- <span data-ttu-id="132c9-141">Regels voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="132c9-141">Conditional access rules</span></span>
- <span data-ttu-id="132c9-142">Opstartscripts voor de JEA-sessie</span><span class="sxs-lookup"><span data-stu-id="132c9-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="132c9-143">De syntaxis voor elk van deze eigenschappen in een DSC-configuratie is consistent met het configuratiebestand van de PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="132c9-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="132c9-144">Hieronder volgt een voorbeeld van DSC-configuratie voor een algemene server Onderhoud-module.</span><span class="sxs-lookup"><span data-stu-id="132c9-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="132c9-145">Hierbij wordt ervan uitgegaan dat een geldig PowerShell-module met de rolmogelijkheden in een submap 'RoleCapabilities' bevindt zich op de '\\\\myfileshare\\JEA'-bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="132c9-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="132c9-146">Deze configuratie kan vervolgens worden toegepast op een systeem met [rechtstreeks aanroepen van de Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) of bijwerken van de [pull-serverconfiguratie](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="132c9-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="132c9-147">De DSC-resources kunt u het standaardeindpunt voor de externe communicatie van Microsoft.PowerShell vervangen.</span><span class="sxs-lookup"><span data-stu-id="132c9-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="132c9-148">Als u dit doet, wordt een back-up unconstrainted-eindpunt met de naam 'Microsoft.PowerShell.Restricted' met de standaard-WinRM-ACL (zodat gebruikers van extern beheer- en lokale beheerders groepsleden om deze te openen) automatisch geregistreerd in de resource.</span><span class="sxs-lookup"><span data-stu-id="132c9-148">If you do this, the resource automatically registers a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="132c9-149">De registratie JEA-configuraties</span><span class="sxs-lookup"><span data-stu-id="132c9-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="132c9-150">Als u wilt een JEA-eindpunt op een systeem verwijderen, gebruikt u de [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="132c9-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="132c9-151">Registratie van een JEA-eindpunt wordt voorkomen dat nieuwe gebruikers van het maken van nieuwe JEA-sessies op het systeem.</span><span class="sxs-lookup"><span data-stu-id="132c9-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="132c9-152">U kunt er ook een JEA-configuratie bijwerken door een bijgewerkte sessie-configuratiebestand met dezelfde naam van het eindpunt opnieuw te registreren.</span><span class="sxs-lookup"><span data-stu-id="132c9-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="132c9-153">Een JEA registratie eindpunt zorgt ervoor dat de WinRM-service opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="132c9-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="132c9-154">Dit meest externe bewerkingen wordt uitgevoerd, met inbegrip van andere PowerShell-sessies, WMI-aanroepen en sommige beheerprogramma's-interrupts.</span><span class="sxs-lookup"><span data-stu-id="132c9-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="132c9-155">Alleen de registratie PowerShell eindpunten verwijderen tijdens gepland onderhoud.</span><span class="sxs-lookup"><span data-stu-id="132c9-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="132c9-156">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="132c9-156">Next steps</span></span>

- [<span data-ttu-id="132c9-157">De JEA-eindpunt testen</span><span class="sxs-lookup"><span data-stu-id="132c9-157">Test the JEA endpoint</span></span>](using-jea.md)
