---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: JEA Sessieconfiguraties
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726545"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="98e52-103">JEA Sessieconfiguraties</span><span class="sxs-lookup"><span data-stu-id="98e52-103">JEA Session Configurations</span></span>

<span data-ttu-id="98e52-104">Een JEA-eindpunt is geregistreerd op een systeem door het maken en registreren van een configuratiebestand van de PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="98e52-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="98e52-105">Sessieconfiguraties definiëren die de JEA-eindpunt kunt gebruiken en welke functies ze toegang hebben.</span><span class="sxs-lookup"><span data-stu-id="98e52-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="98e52-106">Ze bepalen ook algemene instellingen die betrekking hebben op alle gebruikers van de JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="98e52-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="98e52-107">Een sessie-configuratiebestand maken</span><span class="sxs-lookup"><span data-stu-id="98e52-107">Create a session configuration file</span></span>

<span data-ttu-id="98e52-108">Voor het registreren van een JEA-eindpunt, moet u opgeven hoe dit eindpunt is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="98e52-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="98e52-109">Er zijn veel opties om te overwegen.</span><span class="sxs-lookup"><span data-stu-id="98e52-109">There are many options to consider.</span></span> <span data-ttu-id="98e52-110">De belangrijkste opties zijn:</span><span class="sxs-lookup"><span data-stu-id="98e52-110">The most important options are:</span></span>

- <span data-ttu-id="98e52-111">Wie heeft toegang tot de JEA-eindpunt</span><span class="sxs-lookup"><span data-stu-id="98e52-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="98e52-112">Welke functies ze worden toegewezen</span><span class="sxs-lookup"><span data-stu-id="98e52-112">Which roles they be assigned</span></span>
- <span data-ttu-id="98e52-113">Welke identiteit JEA wordt gebruikt op de achtergrond</span><span class="sxs-lookup"><span data-stu-id="98e52-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="98e52-114">De naam van de JEA-eindpunt</span><span class="sxs-lookup"><span data-stu-id="98e52-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="98e52-115">Deze opties zijn gedefinieerd in een bestand met PowerShell met een `.pssc` extensie bekend als een configuratiebestand van de PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="98e52-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="98e52-116">Het configuratiebestand van de sessie kan worden bewerkt met behulp van een teksteditor.</span><span class="sxs-lookup"><span data-stu-id="98e52-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="98e52-117">Voer de volgende opdracht om te maken van een lege sjabloon-configuratiebestand.</span><span class="sxs-lookup"><span data-stu-id="98e52-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="98e52-118">Alleen de meest voorkomende configuratieopties zijn standaard opgenomen in het sjabloonbestand.</span><span class="sxs-lookup"><span data-stu-id="98e52-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="98e52-119">Gebruik de `-Full` overschakelen naar alle toepasselijke instellingen worden opgenomen in de gegenereerde voor.</span><span class="sxs-lookup"><span data-stu-id="98e52-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="98e52-120">De `-SessionType RestrictedRemoteServer` veld geeft aan dat de sessieconfiguratie van de wordt gebruikt door JEA voor veilig beheer.</span><span class="sxs-lookup"><span data-stu-id="98e52-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="98e52-121">Sessies van dit type werken in **NoLanguage** modus en hebben alleen toegang tot de volgende standaardopdrachten (en aliassen):</span><span class="sxs-lookup"><span data-stu-id="98e52-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="98e52-122">Clear-Host (cls, wissen)</span><span class="sxs-lookup"><span data-stu-id="98e52-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="98e52-123">Afsluiten PSSession (exsn, afsluiten)</span><span class="sxs-lookup"><span data-stu-id="98e52-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="98e52-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="98e52-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="98e52-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="98e52-125">Get-FormatData</span></span>
- <span data-ttu-id="98e52-126">Get-Help</span><span class="sxs-lookup"><span data-stu-id="98e52-126">Get-Help</span></span>
- <span data-ttu-id="98e52-127">Meting-Object (eenheid)</span><span class="sxs-lookup"><span data-stu-id="98e52-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="98e52-128">Uitgaande standaard</span><span class="sxs-lookup"><span data-stu-id="98e52-128">Out-Default</span></span>
- <span data-ttu-id="98e52-129">Select-Object (selecteren)</span><span class="sxs-lookup"><span data-stu-id="98e52-129">Select-Object (select)</span></span>

<span data-ttu-id="98e52-130">Er zijn geen PowerShell-providers zijn beschikbaar, noch zijn dat externe programma's (uitvoerbare bestanden of scripts).</span><span class="sxs-lookup"><span data-stu-id="98e52-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="98e52-131">Zie voor meer informatie over de modi van taal [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="98e52-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="98e52-132">Kies de JEA-identiteit</span><span class="sxs-lookup"><span data-stu-id="98e52-132">Choose the JEA identity</span></span>

<span data-ttu-id="98e52-133">Achter de schermen moet JEA een identiteit (account) om te gebruiken bij het uitvoeren van de gebruiker van een verbonden-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="98e52-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="98e52-134">Definieert u welke identiteit JEA wordt gebruikt in het configuratiebestand van de sessie.</span><span class="sxs-lookup"><span data-stu-id="98e52-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="98e52-135">Lokale virtueel Account</span><span class="sxs-lookup"><span data-stu-id="98e52-135">Local Virtual Account</span></span>

<span data-ttu-id="98e52-136">Lokale virtuele accounts zijn handig als alle rollen die zijn gedefinieerd voor de JEA-eindpunt worden gebruikt voor het beheren van de lokale computer en een lokale administrator-account voldoende is voor een geslaagde uitvoering van de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="98e52-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="98e52-137">Virtuele accounts zijn tijdelijke accounts die uniek is voor een specifieke gebruiker en alleen de laatste voor de duur van de PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="98e52-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="98e52-138">Op een lidserver of werkstation virtuele accounts deel uitmaken van de lokale computer **beheerders** groep.</span><span class="sxs-lookup"><span data-stu-id="98e52-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="98e52-139">Op een Active Directory-domeincontroller virtuele accounts deel uitmaken van het domein **Domeinadministrators** groep.</span><span class="sxs-lookup"><span data-stu-id="98e52-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="98e52-140">Als de rollen die zijn gedefinieerd door de sessieconfiguratie is volledige Administrator-bevoegdheden niet vereist, kunt u de beveiligingsgroepen die de virtuele-account behoort.</span><span class="sxs-lookup"><span data-stu-id="98e52-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="98e52-141">Op een lidserver of werkstation zijn de opgegeven beveiligingsgroepen lokale groepen, niet voor groepen van een domein.</span><span class="sxs-lookup"><span data-stu-id="98e52-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="98e52-142">Wanneer een of meer beveiligingsgroepen zijn opgegeven, worden de virtuele-account is niet toegewezen aan de beheerdersgroep lokaal of domein.</span><span class="sxs-lookup"><span data-stu-id="98e52-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="98e52-143">Virtuele accounts krijgen tijdelijk de aanmelden als een service rechts in het beveiligingsbeleid van de lokale server.</span><span class="sxs-lookup"><span data-stu-id="98e52-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="98e52-144">Als een van de opgegeven VirtualAccountGroups is al toegekend dit recht in het beleid, worden de afzonderlijke virtuele account niet meer toegevoegd en verwijderd uit het beleid.</span><span class="sxs-lookup"><span data-stu-id="98e52-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="98e52-145">Dit kan zijn nuttig in scenario's zoals domeincontrollers waarbij wijzigingen aan het beveiligingsbeleid voor domeincontroller nauw worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="98e52-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="98e52-146">Dit is alleen beschikbaar in Windows Server 2016 met de November 2018 of later updatepakket en Windows Server 2019 met de 2019 januari of later updatepakket.</span><span class="sxs-lookup"><span data-stu-id="98e52-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="98e52-147">Groep beheerd serviceaccount</span><span class="sxs-lookup"><span data-stu-id="98e52-147">Group-managed service account</span></span>

<span data-ttu-id="98e52-148">Een groep beheerd serviceaccount (GMSA) is de juiste identiteit moet worden gebruikt wanneer de JEA-gebruikers nodig hebben voor toegang tot netwerkbronnen zoals bestandsshares en webservices.</span><span class="sxs-lookup"><span data-stu-id="98e52-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="98e52-149">Gmsa's bieden u een domein-id die wordt gebruikt voor verificatie met resources op elke computer in het domein.</span><span class="sxs-lookup"><span data-stu-id="98e52-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="98e52-150">De rechten die een GMSA biedt worden bepaald door de resources die u toegang wilt krijgen tot.</span><span class="sxs-lookup"><span data-stu-id="98e52-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="98e52-151">U hebt geen beheerdersrechten op alle machines of services, tenzij deze rechten aan de voor GMSA expliciet door de machine of service-beheerder heeft verleend.</span><span class="sxs-lookup"><span data-stu-id="98e52-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="98e52-152">Gmsa's moeten alleen worden gebruikt wanneer dat nodig is:</span><span class="sxs-lookup"><span data-stu-id="98e52-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="98e52-153">Het is moeilijk te traceren terug acties aan een gebruiker bij het gebruik van een GMSA.</span><span class="sxs-lookup"><span data-stu-id="98e52-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="98e52-154">Elke gebruiker deelt dezelfde run as-id.</span><span class="sxs-lookup"><span data-stu-id="98e52-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="98e52-155">U moet PowerShell-sessie transcripties en logboeken correleren van afzonderlijke gebruikers met hun acties controleren.</span><span class="sxs-lookup"><span data-stu-id="98e52-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="98e52-156">De GMSA hebben mogelijk toegang tot veel netwerkbronnen die gebruiker die de verbinding niet tot nodig.</span><span class="sxs-lookup"><span data-stu-id="98e52-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="98e52-157">Probeer altijd aan de effectieve machtigingen beperken in een JEA-sessie te volgen het principe van minimale bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="98e52-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="98e52-158">Groep beheerde serviceaccounts zijn alleen beschikbaar op een domein machines met behulp van PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="98e52-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="98e52-159">Zie voor meer informatie over het beveiligen van een JEA-sessie de [beveiligingsoverwegingen](security-considerations.md) artikel.</span><span class="sxs-lookup"><span data-stu-id="98e52-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="98e52-160">Transcripten van sessie</span><span class="sxs-lookup"><span data-stu-id="98e52-160">Session transcripts</span></span>

<span data-ttu-id="98e52-161">Het verdient aanbeveling dat u een JEA-eindpunt automatisch vastleggen uitgeschreven van gebruikerssessies configureert.</span><span class="sxs-lookup"><span data-stu-id="98e52-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="98e52-162">PowerShell-sessie Transcripten bevatten informatie over de gebruiker verbinding maakt, het uitvoeren als-identiteit is toegewezen, en de opdrachten worden uitgevoerd door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="98e52-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="98e52-163">Ze kunnen nuttig zijn voor een beoordelingsteam die nodig heeft om te begrijpen die een specifieke wijziging hebt aangebracht in een systeem.</span><span class="sxs-lookup"><span data-stu-id="98e52-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="98e52-164">Voor het configureren van automatische transcriptie in het configuratiebestand van de sessie, Geef een pad naar een map waar de Transcripten moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="98e52-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="98e52-165">Transcripten worden geschreven naar de map met de **lokaal systeem** account waarvoor u lees- en schrijftoegang tot de map.</span><span class="sxs-lookup"><span data-stu-id="98e52-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="98e52-166">Standaardgebruikers moeten geen toegang hebben tot de map.</span><span class="sxs-lookup"><span data-stu-id="98e52-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="98e52-167">Beperk het aantal administrators voor rapportbeveiliging in die toegang hebben tot de Transcripten controleren.</span><span class="sxs-lookup"><span data-stu-id="98e52-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="98e52-168">Schijf van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="98e52-168">User drive</span></span>

<span data-ttu-id="98e52-169">Als uw verbindende gebruikers nodig hebt om bestanden te kopiëren naar of van de JEA-eindpunt, kunt u de schijf van de gebruiker in het configuratiebestand van de sessie inschakelen.</span><span class="sxs-lookup"><span data-stu-id="98e52-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="98e52-170">De schijf van de gebruiker is een **PSDrive** die is toegewezen aan een unieke map voor elke gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="98e52-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="98e52-171">Deze map kan gebruikers bestanden te kopiëren naar of van het systeem zonder zodat ze toegang hebben tot het volledige systeem of de provider bestandssysteem om vrij te geven.</span><span class="sxs-lookup"><span data-stu-id="98e52-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="98e52-172">De inhoud van de gebruiker stations zijn persistent in verschillende sessies voor situaties waar de verbinding met het netwerk kan worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="98e52-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="98e52-173">Standaard kunt de schijf van de gebruiker u voor het opslaan van een maximum van 50MB aan gegevens per gebruiker.</span><span class="sxs-lookup"><span data-stu-id="98e52-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="98e52-174">U kunt de hoeveelheid gegevens die een gebruiker kan worden gebruikt met beperken de *UserDriveMaximumSize* veld.</span><span class="sxs-lookup"><span data-stu-id="98e52-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="98e52-175">Als u niet dat gegevens in de schijf van de gebruiker permanent zijn wilt, kunt u een geplande taak configureren op het systeem voor het automatisch opschonen van de map elke nacht.</span><span class="sxs-lookup"><span data-stu-id="98e52-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="98e52-176">De schijf van de gebruiker is alleen beschikbaar in PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="98e52-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="98e52-177">Zie voor meer informatie over PSDrives [beheren-PowerShell-stations](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="98e52-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="98e52-178">Roldefinities</span><span class="sxs-lookup"><span data-stu-id="98e52-178">Role definitions</span></span>

<span data-ttu-id="98e52-179">Roldefinities in een sessie-configuratiebestand definieert de toewijzing van **gebruikers** naar **rollen**.</span><span class="sxs-lookup"><span data-stu-id="98e52-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="98e52-180">Elke gebruiker of groep die zijn opgenomen in dit veld is gemachtigd voor de JEA-eindpunt wanneer deze geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="98e52-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="98e52-181">Elke gebruiker of groep kan worden opgenomen als een sleutel in de hash-tabel slechts één keer, maar meerdere rollen kan worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="98e52-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="98e52-182">De naam van de mogelijkheid van de rol moet de naam van het bestand van de mogelijkheid rol zonder de `.psrc` extensie.</span><span class="sxs-lookup"><span data-stu-id="98e52-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="98e52-183">Als een gebruiker tot meer dan één groep in het roldefinitie van de behoort, krijgen toegang tot de functies van elk.</span><span class="sxs-lookup"><span data-stu-id="98e52-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="98e52-184">Wanneer twee rollen toegang tot de dezelfde cmdlets verleent, worden de meest strikte parameterset wordt verleend aan de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="98e52-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="98e52-185">Bij het opgeven van lokale gebruikers en groepen in het veld van de definities rol, zorg ervoor dat u de naam van de computer niet **localhost** of jokertekens.</span><span class="sxs-lookup"><span data-stu-id="98e52-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="98e52-186">U kunt de naam van de computer controleren door het inspecteren van de `$env:COMPUTERNAME` variabele.</span><span class="sxs-lookup"><span data-stu-id="98e52-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="98e52-187">Zoekvolgorde van rol mogelijkheid</span><span class="sxs-lookup"><span data-stu-id="98e52-187">Role capability search order</span></span>

<span data-ttu-id="98e52-188">Zoals u in het bovenstaande voorbeeld, rolmogelijkheden zijn waarnaar wordt verwezen door de naam van het bestand van de mogelijkheid rol.</span><span class="sxs-lookup"><span data-stu-id="98e52-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="98e52-189">De naam van een bestand is de bestandsnaam zonder extensie.</span><span class="sxs-lookup"><span data-stu-id="98e52-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="98e52-190">Als meerdere rolmogelijkheden beschikbaar op het systeem met dezelfde naam zijn, wordt de impliciete zoekvolgorde in PowerShell gebruikt om de effectieve rol mogelijkheid-bestand te selecteren.</span><span class="sxs-lookup"><span data-stu-id="98e52-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="98e52-191">JEA heeft **niet** toegang geven tot alle rol mogelijkheid bestanden met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="98e52-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="98e52-192">JEA maakt gebruik van de `$env:PSModulePath` omgevingsvariabele om te bepalen welke paden om te scannen op rol mogelijkheid bestanden.</span><span class="sxs-lookup"><span data-stu-id="98e52-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="98e52-193">Binnen elk van deze paden JEA gezocht naar geldige PowerShell-modules die een submap 'RoleCapabilities' bevatten.</span><span class="sxs-lookup"><span data-stu-id="98e52-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="98e52-194">Net als bij importeren van modules, verkiest JEA rolmogelijkheden die worden geleverd met Windows op de mogelijkheden van de aangepaste rol met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="98e52-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="98e52-195">Voor alle andere naamconflicten wordt prioriteit bepaald door de volgorde waarin Windows de bestanden in de map inventariseren.</span><span class="sxs-lookup"><span data-stu-id="98e52-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="98e52-196">De order wordt niet gegarandeerd alfabetische.</span><span class="sxs-lookup"><span data-stu-id="98e52-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="98e52-197">Het eerste bestand van de rol-mogelijkheid gevonden die overeenkomt met de opgegeven naam wordt gebruikt voor de gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="98e52-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="98e52-198">Omdat de rol mogelijkheid order niet deterministisch is, is het **sterk aanbevolen** dat rolmogelijkheden unieke namen van bestanden hebben.</span><span class="sxs-lookup"><span data-stu-id="98e52-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="98e52-199">Regels voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="98e52-199">Conditional access rules</span></span>

<span data-ttu-id="98e52-200">Alle gebruikers en groepen die zijn opgenomen in de **RoleDefinitions** veld automatisch toegang verleend tot JEA-eindpunten.</span><span class="sxs-lookup"><span data-stu-id="98e52-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="98e52-201">Regels voor voorwaardelijke toegang kunnen u deze toegang verfijnen en vereisen dat gebruikers deel uitmaken van aanvullende beveiligingsgroepen die niet van invloed zijn op de rollen waaraan ze zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="98e52-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="98e52-202">Dit is handig als u wilt een just-in-time privileged access management-oplossing, smartcardverificatie of andere oplossing voor multifactor-verificatie integreren met JEA.</span><span class="sxs-lookup"><span data-stu-id="98e52-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="98e52-203">Regels voor voorwaardelijke toegang worden gedefinieerd in het veld RequiredGroups in een sessie-configuratiebestand.</span><span class="sxs-lookup"><span data-stu-id="98e52-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="98e52-204">Daar kunt u een hash-tabel (eventueel geneste) die gebruikmaakt van bieden 'En' en 'Of' sleutels te maken van uw regels.</span><span class="sxs-lookup"><span data-stu-id="98e52-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="98e52-205">Hier volgen enkele voorbeelden van hoe u dit veld:</span><span class="sxs-lookup"><span data-stu-id="98e52-205">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="98e52-206">Regels voor voorwaardelijke toegang zijn alleen beschikbaar in PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="98e52-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="98e52-207">Andere eigenschappen</span><span class="sxs-lookup"><span data-stu-id="98e52-207">Other properties</span></span>

<span data-ttu-id="98e52-208">Sessie-configuratiebestanden kunnen ook doen alles wat die een bestand van de mogelijkheid rol doen kunt, maar wel zonder de mogelijkheid om te verbinden gebruikerstoegang geven tot andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="98e52-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="98e52-209">Als u wilt dat alle gebruikers toegang tot bepaalde cmdlets, functies of -providers, kunt u doen rechts in het configuratiebestand van de sessie.</span><span class="sxs-lookup"><span data-stu-id="98e52-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="98e52-210">Voor een volledige lijst van ondersteunde eigenschappen in het configuratiebestand van de sessie, voert u `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="98e52-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="98e52-211">Testen van een sessie-configuratiebestand</span><span class="sxs-lookup"><span data-stu-id="98e52-211">Testing a session configuration file</span></span>

<span data-ttu-id="98e52-212">U kunt testen met een sessie configureren met behulp van de [Test PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="98e52-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="98e52-213">Het verdient aanbeveling uw sessie-configuratiebestand te testen, als u handmatig hebt bewerkt de `.pssc` bestand.</span><span class="sxs-lookup"><span data-stu-id="98e52-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="98e52-214">Testen, zorgt ervoor dat de syntaxis juist is.</span><span class="sxs-lookup"><span data-stu-id="98e52-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="98e52-215">Als een sessie-configuratiebestand deze test mislukt, kan deze kan niet worden geregistreerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="98e52-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="98e52-216">Voorbeeldconfiguratiebestand sessie</span><span class="sxs-lookup"><span data-stu-id="98e52-216">Sample session configuration file</span></span>

<span data-ttu-id="98e52-217">Het volgende voorbeeld ziet hoe u maakt en een sessieconfiguratie voor JEA valideren.</span><span class="sxs-lookup"><span data-stu-id="98e52-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="98e52-218">De definities van gebruikersrollen worden gemaakt en opgeslagen in de `$roles` variabele voor uw gemak en leesbaarheid.</span><span class="sxs-lookup"><span data-stu-id="98e52-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="98e52-219">Het is niet vereist om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="98e52-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="98e52-220">Bijwerken van de sessie-configuratiebestanden</span><span class="sxs-lookup"><span data-stu-id="98e52-220">Updating session configuration files</span></span>

<span data-ttu-id="98e52-221">Als u wilt wijzigen van de eigenschappen van een JEA-sessieconfiguratie, met inbegrip van de toewijzing van gebruikers aan rollen, moet u [registratie](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="98e52-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="98e52-222">Vervolgens [opnieuw registreren](register-jea.md) de JEA-sessieconfiguratie met behulp van een configuratiebestand bijgewerkte sessie.</span><span class="sxs-lookup"><span data-stu-id="98e52-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="98e52-223">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="98e52-223">Next steps</span></span>

- [<span data-ttu-id="98e52-224">Een JEA-configuratiegegevens registreren</span><span class="sxs-lookup"><span data-stu-id="98e52-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="98e52-225">De auteur van JEA-rollen</span><span class="sxs-lookup"><span data-stu-id="98e52-225">Author JEA roles</span></span>](role-capabilities.md)
