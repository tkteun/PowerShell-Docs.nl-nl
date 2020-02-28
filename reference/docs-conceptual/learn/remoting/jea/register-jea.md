---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: JEA-configuraties registreren
ms.openlocfilehash: 7cc67e891bc14dd667c97e9a8b550b33b4c2b874
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706203"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="27cff-103">JEA-configuraties registreren</span><span class="sxs-lookup"><span data-stu-id="27cff-103">Registering JEA Configurations</span></span>

<span data-ttu-id="27cff-104">Zodra u uw [functie mogelijkheden](role-capabilities.md) en [sessie configuratie bestand](session-configurations.md) hebt gemaakt, is de laatste stap het JEA-eind punt te registreren.</span><span class="sxs-lookup"><span data-stu-id="27cff-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="27cff-105">Als het JEA-eind punt wordt geregistreerd bij het systeem, wordt het eind punt beschikbaar voor gebruik door gebruikers en automatiserings engines.</span><span class="sxs-lookup"><span data-stu-id="27cff-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="27cff-106">Configuratie van één computer</span><span class="sxs-lookup"><span data-stu-id="27cff-106">Single machine configuration</span></span>

<span data-ttu-id="27cff-107">Voor kleine omgevingen kunt u JEA implementeren door het sessie configuratie bestand te registreren met de cmdlet [REGI ster-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="27cff-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="27cff-108">Voordat u begint, moet u ervoor zorgen dat aan de volgende vereisten is voldaan:</span><span class="sxs-lookup"><span data-stu-id="27cff-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="27cff-109">Een of meer rollen zijn gemaakt en geplaatst in de map **RoleCapabilities** van een Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="27cff-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="27cff-110">Er is een sessie configuratie bestand gemaakt en getest.</span><span class="sxs-lookup"><span data-stu-id="27cff-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="27cff-111">De gebruiker die de JEA-configuratie registreert, heeft beheerders rechten op het systeem.</span><span class="sxs-lookup"><span data-stu-id="27cff-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="27cff-112">U hebt een naam geselecteerd voor uw JEA-eind punt.</span><span class="sxs-lookup"><span data-stu-id="27cff-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="27cff-113">De naam van het JEA-eind punt is vereist wanneer gebruikers verbinding maken met het systeem met behulp van JEA.</span><span class="sxs-lookup"><span data-stu-id="27cff-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="27cff-114">De cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) geeft de namen van de eind punten op een systeem weer.</span><span class="sxs-lookup"><span data-stu-id="27cff-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="27cff-115">Eind punten die beginnen met `microsoft` worden doorgaans geleverd met Windows.</span><span class="sxs-lookup"><span data-stu-id="27cff-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="27cff-116">Het `microsoft.powershell`-eind punt is het standaard eindpunt dat wordt gebruikt om verbinding te maken met een extern Power shell-eind punt.</span><span class="sxs-lookup"><span data-stu-id="27cff-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

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

<span data-ttu-id="27cff-117">Voer de volgende opdracht uit om het eind punt te registreren.</span><span class="sxs-lookup"><span data-stu-id="27cff-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="27cff-118">Met de vorige opdracht wordt de WinRM-service opnieuw gestart op het systeem.</span><span class="sxs-lookup"><span data-stu-id="27cff-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="27cff-119">Hiermee worden alle externe sessies met Power shell en alle doorlopende DSC-configuraties beëindigd.</span><span class="sxs-lookup"><span data-stu-id="27cff-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="27cff-120">We raden u aan productie machines offline te zetten voordat u de opdracht uitvoert om te voor komen dat zakelijke activiteiten worden verstoord.</span><span class="sxs-lookup"><span data-stu-id="27cff-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="27cff-121">Na de registratie bent u klaar om [JEA te gebruiken](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="27cff-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="27cff-122">U kunt het sessie configuratie bestand op elk gewenst moment verwijderen.</span><span class="sxs-lookup"><span data-stu-id="27cff-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="27cff-123">Het configuratie bestand wordt niet gebruikt na de registratie van het eind punt.</span><span class="sxs-lookup"><span data-stu-id="27cff-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="27cff-124">Configuratie van meerdere machines met DSC</span><span class="sxs-lookup"><span data-stu-id="27cff-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="27cff-125">Bij het implementeren van JEA op meerdere computers, gebruikt het eenvoudigste implementatie model de JEA [desired state Configuration (DSC)-](../../../dsc/overview/overview.md) resource om snel en consistent JEA op elke computer te implementeren.</span><span class="sxs-lookup"><span data-stu-id="27cff-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="27cff-126">Als u JEA wilt implementeren met DSC, controleert u of aan de volgende vereisten wordt voldaan:</span><span class="sxs-lookup"><span data-stu-id="27cff-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="27cff-127">Een of meer functie mogelijkheden zijn gemaakt en toegevoegd aan een Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="27cff-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="27cff-128">De Power shell-module die de rollen bevat, wordt opgeslagen op een bestands share (alleen-lezen) die toegankelijk is voor elke computer.</span><span class="sxs-lookup"><span data-stu-id="27cff-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="27cff-129">De instellingen voor de sessie configuratie zijn bepaald.</span><span class="sxs-lookup"><span data-stu-id="27cff-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="27cff-130">U hoeft geen sessie configuratie bestand te maken wanneer u de JEA DSC-resource gebruikt.</span><span class="sxs-lookup"><span data-stu-id="27cff-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="27cff-131">U hebt referenties waarmee beheer acties op elke computer of toegang tot de DSC-pull-server die wordt gebruikt voor het beheren van de computers worden toegestaan.</span><span class="sxs-lookup"><span data-stu-id="27cff-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="27cff-132">U hebt de [JEA DSC-resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource)gedownload.</span><span class="sxs-lookup"><span data-stu-id="27cff-132">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="27cff-133">Een DSC-configuratie voor uw JEA-eind punt maken op een doel computer of pull-server.</span><span class="sxs-lookup"><span data-stu-id="27cff-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="27cff-134">In deze configuratie definieert de **JustEnoughAdministration** DSC-resource het sessie configuratie bestand en de **Bestands** resource kopieert de functie mogelijkheden van de bestands share.</span><span class="sxs-lookup"><span data-stu-id="27cff-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="27cff-135">De volgende eigenschappen kunnen worden geconfigureerd met behulp van de DSC-resource:</span><span class="sxs-lookup"><span data-stu-id="27cff-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="27cff-136">Roldefinities</span><span class="sxs-lookup"><span data-stu-id="27cff-136">Role Definitions</span></span>
- <span data-ttu-id="27cff-137">Virtuele-account groepen</span><span class="sxs-lookup"><span data-stu-id="27cff-137">Virtual account groups</span></span>
- <span data-ttu-id="27cff-138">Naam van door groep beheerde service account</span><span class="sxs-lookup"><span data-stu-id="27cff-138">Group-managed service account name</span></span>
- <span data-ttu-id="27cff-139">Transcript Directory</span><span class="sxs-lookup"><span data-stu-id="27cff-139">Transcript directory</span></span>
- <span data-ttu-id="27cff-140">Gebruikers station</span><span class="sxs-lookup"><span data-stu-id="27cff-140">User drive</span></span>
- <span data-ttu-id="27cff-141">Regels voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="27cff-141">Conditional access rules</span></span>
- <span data-ttu-id="27cff-142">Opstart scripts voor de JEA-sessie</span><span class="sxs-lookup"><span data-stu-id="27cff-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="27cff-143">De syntaxis voor elk van deze eigenschappen in een DSC-configuratie is consistent met het configuratie bestand van de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="27cff-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="27cff-144">Hieronder vindt u een voor beeld van een DSC-configuratie voor een algemene server onderhoud module.</span><span class="sxs-lookup"><span data-stu-id="27cff-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="27cff-145">Hierbij wordt ervan uitgegaan dat een geldige Power shell-module met functie mogelijkheden zich op de `\\myfileshare\JEA` bestands share bevindt.</span><span class="sxs-lookup"><span data-stu-id="27cff-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

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

<span data-ttu-id="27cff-146">Vervolgens wordt de configuratie op een systeem toegepast door de [lokale Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) rechtstreeks aan te roepen of de configuratie van de [Pull-server](/powershell/scripting/dsc/pull-server/pullServer)bij te werken.</span><span class="sxs-lookup"><span data-stu-id="27cff-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="27cff-147">Met de DSC-resource kunt u ook het standaard eindpunt van **micro soft. Power shell** vervangen.</span><span class="sxs-lookup"><span data-stu-id="27cff-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="27cff-148">Wanneer deze is vervangen, registreert de resource automatisch een back-upeindpunt met de naam **micro soft. Power shell. restricted**.</span><span class="sxs-lookup"><span data-stu-id="27cff-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="27cff-149">Het back-upeindpunt heeft de standaard-WinRM-ACL waarmee gebruikers van extern beheer en lokale beheerders groeps leden toegang kunnen krijgen.</span><span class="sxs-lookup"><span data-stu-id="27cff-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="27cff-150">Registratie van JEA-configuraties ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="27cff-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="27cff-151">Met de cmdlet [unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) wordt een JEA-eind punt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27cff-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="27cff-152">Wanneer u de registratie van een JEA-eind punt ongedaan maakt, kunnen nieuwe gebruikers geen nieuwe JEA-sessies op het systeem maken.</span><span class="sxs-lookup"><span data-stu-id="27cff-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="27cff-153">U kunt hiermee ook een JEA-configuratie bijwerken door een bijgewerkt sessie configuratie bestand opnieuw te registreren met dezelfde naam voor het eind punt.</span><span class="sxs-lookup"><span data-stu-id="27cff-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="27cff-154">Bij het ongedaan maken van de registratie van een JEA-eind punt wordt de WinRM-service opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="27cff-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="27cff-155">Hiermee worden de meeste beheer bewerkingen van het externe Management onderbroken, waaronder andere Power shell-sessies, WMI-aanroepen en bepaalde beheer hulpprogramma's.</span><span class="sxs-lookup"><span data-stu-id="27cff-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="27cff-156">Registreer Power shell-eind punten alleen tijdens geplande onderhouds Vensters.</span><span class="sxs-lookup"><span data-stu-id="27cff-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="27cff-157">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="27cff-157">Next steps</span></span>

[<span data-ttu-id="27cff-158">Het JEA-eind punt testen</span><span class="sxs-lookup"><span data-stu-id="27cff-158">Test the JEA endpoint</span></span>](using-jea.md)
