---
ms.date: 06/12/2017
keywords: jea powershell beveiliging
title: JEA configuraties registreren
ms.openlocfilehash: cda899b20378b0183a3d88ecfd593aaf7356e967
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188510"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="f65c3-103">JEA configuraties registreren</span><span class="sxs-lookup"><span data-stu-id="f65c3-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="f65c3-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f65c3-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f65c3-105">De laatste stap voordat u JEA kunt zodra u hebt uw [rol mogelijkheden](role-capabilities.md) en [sessie configuratiebestand](session-configurations.md) gemaakt is voor het registreren van het eindpunt JEA.</span><span class="sxs-lookup"><span data-stu-id="f65c3-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="f65c3-106">Dit proces de sessie-configuratie-informatie is van toepassing op het systeem en het eindpunt beschikbaar voor gebruik door gebruikers en de automation-engines.</span><span class="sxs-lookup"><span data-stu-id="f65c3-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="f65c3-107">Configuratie van één machine</span><span class="sxs-lookup"><span data-stu-id="f65c3-107">Single machine configuration</span></span>

<span data-ttu-id="f65c3-108">Voor kleine omgevingen, kunt u JEA implementeren via het registreren van de sessie configuratie bestand met de [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f65c3-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="f65c3-109">Zorg ervoor dat de volgende vereisten is voldaan voordat u begint:</span><span class="sxs-lookup"><span data-stu-id="f65c3-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="f65c3-110">Een of meer rollen is gemaakt en opgeslagen in de map 'RoleCapabilities' van een geldig PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="f65c3-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="f65c3-111">Een sessie-configuratiebestand is gemaakt en getest.</span><span class="sxs-lookup"><span data-stu-id="f65c3-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="f65c3-112">De gebruiker registreren van de configuratie van de JEA heeft administrator-rechten op de systemen.</span><span class="sxs-lookup"><span data-stu-id="f65c3-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="f65c3-113">U moet ook een naam voor uw eindpunt JEA selecteren.</span><span class="sxs-lookup"><span data-stu-id="f65c3-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="f65c3-114">De naam van het eindpunt JEA is vereist wanneer gebruikers verbinding wilt maken met het systeem met JEA.</span><span class="sxs-lookup"><span data-stu-id="f65c3-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="f65c3-115">U kunt de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet om de namen van bestaande eindpunten op het systeem te controleren.</span><span class="sxs-lookup"><span data-stu-id="f65c3-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="f65c3-116">Eindpunten die met 'microsoft beginnen' zijn doorgaans geleverd bij Windows.</span><span class="sxs-lookup"><span data-stu-id="f65c3-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="f65c3-117">Het eindpunt 'microsoft.powershell' is het standaardeindpunt gebruikt bij het verbinden met een externe PowerShell-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="f65c3-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="f65c3-118">Wanneer u een passende naam voor uw eindpunt JEA hebt vastgesteld, voert u de volgende opdracht voor het registreren van het eindpunt.</span><span class="sxs-lookup"><span data-stu-id="f65c3-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="f65c3-119">De bovenstaande opdracht wordt de WinRM-service op het systeem opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="f65c3-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="f65c3-120">Dit wordt beëindigd op alle externe communicatie van PowerShell-sessies, evenals een eventuele lopende DSC-configuraties.</span><span class="sxs-lookup"><span data-stu-id="f65c3-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="f65c3-121">Het is raadzaam dat u eventuele productiemachines offline uitvoeren voordat u de opdracht uit te voeren om te voorkomen dat zakelijke activiteiten verstoren.</span><span class="sxs-lookup"><span data-stu-id="f65c3-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="f65c3-122">Als de registratie gelukt is, bent u klaar om [JEA gebruiken](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="f65c3-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="f65c3-123">U kunt het configuratiebestand van de sessie op elk gewenst moment; verwijderen Dit wordt niet gebruikt na de registratie.</span><span class="sxs-lookup"><span data-stu-id="f65c3-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="f65c3-124">Meerdere machines met DSC-configuratie</span><span class="sxs-lookup"><span data-stu-id="f65c3-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="f65c3-125">Als u JEA op meerdere machines implementeert, wordt het eenvoudigste implementatiemodel is het gebruik van de JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resource snel en consistent JEA implementeren op elke machine.</span><span class="sxs-lookup"><span data-stu-id="f65c3-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="f65c3-126">Als u wilt implementeren JEA met DSC, moet u moet dat de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="f65c3-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="f65c3-127">Een of meer rollen mogelijkheden zijn gemaakt en toegevoegd aan een geldig PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="f65c3-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="f65c3-128">De PowerShell-module met de rollen is opgeslagen op een (alleen-lezen) bestandsshare die toegankelijk door elke computer.</span><span class="sxs-lookup"><span data-stu-id="f65c3-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="f65c3-129">Instellingen voor de sessieconfiguratie van de zijn vastgesteld.</span><span class="sxs-lookup"><span data-stu-id="f65c3-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="f65c3-130">U hoeft niet te maken van een configuratiebestand sessie bij het gebruik van de JEA DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="f65c3-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="f65c3-131">U hebt de referenties die u kunt u beheeracties uitvoeren op elke machine of toegang hebben tot een DSC-pull-server gebruikt voor het beheren van de machines.</span><span class="sxs-lookup"><span data-stu-id="f65c3-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="f65c3-132">U hebt gedownload de [JEA DSC-resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="f65c3-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="f65c3-133">Maak een DSC-configuratie voor uw eindpunt JEA op een doel-machine (of pull-server, als u van een gebruikmaakt).</span><span class="sxs-lookup"><span data-stu-id="f65c3-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="f65c3-134">In deze configuratie gebruikt u de JustEnoughAdministration DSC-resource voor het instellen van het configuratiebestand van de sessie en de resource bestand kopiëren over de mogelijkheden van de rol van de bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="f65c3-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="f65c3-135">De volgende eigenschappen kunnen worden geconfigureerd met behulp van de DSC-resource:</span><span class="sxs-lookup"><span data-stu-id="f65c3-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="f65c3-136">Roldefinities</span><span class="sxs-lookup"><span data-stu-id="f65c3-136">Role Definitions</span></span>
- <span data-ttu-id="f65c3-137">Groepen met virtuele</span><span class="sxs-lookup"><span data-stu-id="f65c3-137">Virtual Account groups</span></span>
- <span data-ttu-id="f65c3-138">De naam van groep beheerd serviceaccount gebruiken</span><span class="sxs-lookup"><span data-stu-id="f65c3-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="f65c3-139">De tekst van directory</span><span class="sxs-lookup"><span data-stu-id="f65c3-139">Transcript directory</span></span>
- <span data-ttu-id="f65c3-140">Schijf van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="f65c3-140">User drive</span></span>
- <span data-ttu-id="f65c3-141">Regels voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="f65c3-141">Conditional access rules</span></span>
- <span data-ttu-id="f65c3-142">Opstartscripts voor de sessie JEA</span><span class="sxs-lookup"><span data-stu-id="f65c3-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="f65c3-143">De syntaxis voor elk van deze eigenschappen in een DSC-configuratie komt overeen met het configuratiebestand van de PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="f65c3-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="f65c3-144">Hieronder volgt een voorbeeld DSC-configuratie voor een algemene server Onderhoud module.</span><span class="sxs-lookup"><span data-stu-id="f65c3-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="f65c3-145">Er wordt ervan uitgegaan dat een geldig PowerShell-module met de mogelijkheden van de rol in een submap 'RoleCapabilities' bevindt zich op de '\\\\myfileshare\\JEA' bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="f65c3-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="f65c3-146">Deze configuratie kan vervolgens worden toegepast op een systeem door [rechtstreeks aanroepen van de lokale Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) of bijwerken van de [pull-serverconfiguratie](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="f65c3-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="f65c3-147">De DSC-resource kunt u het standaardeindpunt van Microsoft.PowerShell remoting vervangen.</span><span class="sxs-lookup"><span data-stu-id="f65c3-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="f65c3-148">Als u dit doet, wordt automatisch een back-unconstrainted-eindpunt met de naam 'Microsoft.PowerShell.Restricted' met de standaardinstellingen van de WinRM-ACL (zodat gebruikers van extern beheer en lokale beheerders groepsleden om deze te openen) geregistreerd in de resource.</span><span class="sxs-lookup"><span data-stu-id="f65c3-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="f65c3-149">Registratie JEA-configuraties</span><span class="sxs-lookup"><span data-stu-id="f65c3-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="f65c3-150">U kunt een JEA-eindpunt op een systeem met de [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f65c3-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="f65c3-151">De registratie van een eindpunt JEA wordt voorkomen dat nieuwe gebruikers maken van nieuwe JEA sessies op het systeem.</span><span class="sxs-lookup"><span data-stu-id="f65c3-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="f65c3-152">Ook kunt u de configuratie van een JEA bijwerken door een bijgewerkte sessie-configuratiebestand met dezelfde naam van het eindpunt opnieuw te registreren.</span><span class="sxs-lookup"><span data-stu-id="f65c3-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="f65c3-153">De registratie van een JEA eindpunt zorgt ervoor dat de WinRM-service opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="f65c3-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="f65c3-154">Hiermee wordt de meeste RAS beheerbewerkingen in voortgang, inclusief andere PowerShell-sessies, WMI-aanroepen en sommige beheerhulpprogramma's onderbroken.</span><span class="sxs-lookup"><span data-stu-id="f65c3-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="f65c3-155">Alleen de PowerShell-eindpunten registratie tijdens gepland onderhoud.</span><span class="sxs-lookup"><span data-stu-id="f65c3-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f65c3-156">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="f65c3-156">Next steps</span></span>

- [<span data-ttu-id="f65c3-157">Het eindpunt JEA testen</span><span class="sxs-lookup"><span data-stu-id="f65c3-157">Test the JEA endpoint</span></span>](using-jea.md)