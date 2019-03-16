---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: JEA Sessieconfiguraties
ms.openlocfilehash: b98726ea7ed3aabdfd05034c3b70118e327160cd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056584"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="df00d-103">JEA Sessieconfiguraties</span><span class="sxs-lookup"><span data-stu-id="df00d-103">JEA Session Configurations</span></span>

> <span data-ttu-id="df00d-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="df00d-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="df00d-105">Een JEA-eindpunt is op een systeem door het maken en registreren van een configuratiebestand van de PowerShell-sessie op een specifieke manier geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="df00d-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="df00d-106">Sessieconfiguraties bepalen *die* de JEA-eindpunt kunt gebruiken en welke rollen hebben ze toegang tot.</span><span class="sxs-lookup"><span data-stu-id="df00d-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="df00d-107">Ze bepalen ook algemene instellingen die van toepassing op gebruikers van een rol in de JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="df00d-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="df00d-108">In dit onderwerp wordt beschreven hoe u een PowerShell-sessie-configuratiebestand maken en registreren van een JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="df00d-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="df00d-109">Een sessie-configuratiebestand maken</span><span class="sxs-lookup"><span data-stu-id="df00d-109">Create a session configuration file</span></span>

<span data-ttu-id="df00d-110">Als u wilt een JEA-eindpunt registreren, moet u opgeven hoe dit eindpunt moet worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="df00d-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="df00d-111">Er zijn veel opties om te overwegen, de belangrijkste van welke wordt die toegang moeten hebben tot de JEA-eindpunt, welke functies worden ze worden toegewezen, welke identiteit JEA gebruikt op de achtergrond en wat is de naam van de JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="df00d-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="df00d-112">Deze worden alle gedefinieerd in een configuratiebestand voor PowerShell-sessie die is een PowerShell-gegevensbestand eindigt met de extensie .pssc.</span><span class="sxs-lookup"><span data-stu-id="df00d-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="df00d-113">Voer de volgende opdracht voor het maken van een minimale sessie-configuratiebestand voor de JEA-eindpunten.</span><span class="sxs-lookup"><span data-stu-id="df00d-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="df00d-114">Alleen de meest voorkomende configuratieopties zijn standaard opgenomen in de minimale bestand.</span><span class="sxs-lookup"><span data-stu-id="df00d-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="df00d-115">Gebruik de `-Full` overschakelen naar alle toepasselijke instellingen worden opgenomen in de gegenereerde voor.</span><span class="sxs-lookup"><span data-stu-id="df00d-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="df00d-116">U kunt het configuratiebestand van de sessie openen in een teksteditor.</span><span class="sxs-lookup"><span data-stu-id="df00d-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="df00d-117">De `-SessionType RestrictedRemoteServer` veld geeft aan dat de sessieconfiguratie van de wordt gebruikt door JEA voor veilig beheer.</span><span class="sxs-lookup"><span data-stu-id="df00d-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="df00d-118">Sessies die is geconfigureerd op deze manier wordt uitgevoerd [NoLanguage modus](https://technet.microsoft.com/library/dn433292.aspx) en hebt u alleen de volgende 8 standaardopdrachten (en aliassen) beschikbaar:</span><span class="sxs-lookup"><span data-stu-id="df00d-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="df00d-119">Clear-Host (cls, wissen)</span><span class="sxs-lookup"><span data-stu-id="df00d-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="df00d-120">Afsluiten PSSession (exsn, afsluiten)</span><span class="sxs-lookup"><span data-stu-id="df00d-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="df00d-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="df00d-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="df00d-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="df00d-122">Get-FormatData</span></span>
- <span data-ttu-id="df00d-123">Help ontvangen</span><span class="sxs-lookup"><span data-stu-id="df00d-123">Get-Help</span></span>
- <span data-ttu-id="df00d-124">Meting-Object (eenheid)</span><span class="sxs-lookup"><span data-stu-id="df00d-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="df00d-125">Uitgaande standaard</span><span class="sxs-lookup"><span data-stu-id="df00d-125">Out-Default</span></span>
- <span data-ttu-id="df00d-126">Select-Object (selecteren)</span><span class="sxs-lookup"><span data-stu-id="df00d-126">Select-Object (select)</span></span>

<span data-ttu-id="df00d-127">Er zijn geen PowerShell-providers zijn beschikbaar, noch zijn dat externe programma's (uitvoerbare bestanden, scripts, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="df00d-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="df00d-128">Er zijn diverse andere velden die u wilt configureren voor de JEA-sessie.</span><span class="sxs-lookup"><span data-stu-id="df00d-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="df00d-129">Ze worden behandeld in de volgende secties.</span><span class="sxs-lookup"><span data-stu-id="df00d-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="df00d-130">Kies de JEA-identiteit</span><span class="sxs-lookup"><span data-stu-id="df00d-130">Choose the JEA identity</span></span>

<span data-ttu-id="df00d-131">Achter de schermen moet JEA een identiteit (account) om te gebruiken bij het uitvoeren van de gebruiker van een verbonden-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="df00d-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="df00d-132">U bepalen welke identiteit JEA wordt gebruikt in het configuratiebestand van de sessie.</span><span class="sxs-lookup"><span data-stu-id="df00d-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="df00d-133">Lokale virtueel Account</span><span class="sxs-lookup"><span data-stu-id="df00d-133">Local Virtual Account</span></span>

<span data-ttu-id="df00d-134">Als de rollen die worden ondersteund door dit JEA-eindpunt worden gebruikt voor het beheren van de lokale computer en een lokale administrator-account voldoende is om de opdrachten is uitgevoerd, moet u de JEA voor het gebruik van een lokale virtuele-account configureren.</span><span class="sxs-lookup"><span data-stu-id="df00d-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands successfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="df00d-135">Virtuele accounts zijn tijdelijke accounts die uniek is voor een specifieke gebruiker en alleen de laatste voor de duur van de PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="df00d-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="df00d-136">Op een lidserver of werkstation virtuele accounts deel uitmaken van de lokale computer **beheerders** groep en toegang hebben tot de meeste systeembronnen.</span><span class="sxs-lookup"><span data-stu-id="df00d-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="df00d-137">Op een Active Directory-domeincontroller virtuele accounts deel uitmaken van het domein **Domeinadministrators** groep.</span><span class="sxs-lookup"><span data-stu-id="df00d-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="df00d-138">Als de rollen die worden ondersteund door de sessieconfiguratie geen dergelijke uitgebreide bevoegdheden vereist, kunt u eventueel de beveiligingsgroepen die de virtuele-account behoort.</span><span class="sxs-lookup"><span data-stu-id="df00d-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="df00d-139">Op een lidserver of werkstation zijn de opgegeven beveiligingsgroepen lokale groepen, niet voor groepen van een domein.</span><span class="sxs-lookup"><span data-stu-id="df00d-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="df00d-140">Wanneer een of meer beveiligingsgroepen is opgegeven, wordt niet langer de virtuele account aan de beheerdersgroep lokaal of domein behoren.</span><span class="sxs-lookup"><span data-stu-id="df00d-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="df00d-141">Virtuele accounts krijgen tijdelijk de aanmelden als een service rechts in het beveiligingsbeleid van de lokale server.</span><span class="sxs-lookup"><span data-stu-id="df00d-141">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span>  <span data-ttu-id="df00d-142">Als een van de opgegeven VirtualAccountGroups is al toegekend dit recht in het beleid, worden de afzonderlijke virtuele account niet meer toegevoegd en verwijderd uit het beleid.</span><span class="sxs-lookup"><span data-stu-id="df00d-142">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span>  <span data-ttu-id="df00d-143">Dit kan zijn nuttig in scenario's zoals domeincontrollers waarbij wijzigingen aan het beveiligingsbeleid voor domeincontroller nauw worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="df00d-143">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span>  <span data-ttu-id="df00d-144">Dit is alleen beschikbaar in Windows Server 2016 met de November 2018 of later updatepakket en Windows Server 2019 met de 2019 januari of later updatepakket.</span><span class="sxs-lookup"><span data-stu-id="df00d-144">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="df00d-145">Door groep beheerd serviceaccount</span><span class="sxs-lookup"><span data-stu-id="df00d-145">Group Managed Service Account</span></span>


<span data-ttu-id="df00d-146">Voor scenario's vereisen dat de JEA-gebruiker voor toegang tot netwerkbronnen, zoals andere computers of webservices, is een groep beheerd serviceaccount (gMSA) een geschiktere identiteit te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="df00d-146">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="df00d-147">gMSA-accounts bieden u een domein-id die kan worden gebruikt voor verificatie op basis van resources op elke computer in het domein.</span><span class="sxs-lookup"><span data-stu-id="df00d-147">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="df00d-148">De rechten van het gMSA-account biedt u wordt bepaald door de resources die u wilt openen.</span><span class="sxs-lookup"><span data-stu-id="df00d-148">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="df00d-149">U wordt automatisch geen beheerdersrechten op alle machines of services, tenzij de machine/service-beheerder heeft expliciet verleend voor het gMSA-account beheerdersbevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="df00d-149">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="df00d-150">gMSA-accounts moeten alleen worden gebruikt wanneer toegang tot netwerkbronnen zijn vereist voor een aantal oorzaken hebben:</span><span class="sxs-lookup"><span data-stu-id="df00d-150">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="df00d-151">Is het moeilijker om te traceren terug acties aan een gebruiker bij het gebruik van een gMSA-account, omdat elke gebruiker dezelfde run as-id deelt.</span><span class="sxs-lookup"><span data-stu-id="df00d-151">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="df00d-152">U moet moet u de PowerShell-sessie transcripties en logboeken correleren van gebruikers met hun acties.</span><span class="sxs-lookup"><span data-stu-id="df00d-152">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="df00d-153">Het gMSA-account hebben mogelijk toegang tot veel netwerkbronnen die de gebruiker die de verbinding heeft geen toegang nodig tot.</span><span class="sxs-lookup"><span data-stu-id="df00d-153">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="df00d-154">Probeer altijd aan de effectieve machtigingen beperken in een JEA-sessie te volgen het principe van minimale bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="df00d-154">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="df00d-155">Groep beheerde serviceaccounts zijn alleen beschikbaar in Windows PowerShell 5.1 of hoger en op domein systemen.</span><span class="sxs-lookup"><span data-stu-id="df00d-155">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>

#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="df00d-156">Meer informatie over run as-gebruikers</span><span class="sxs-lookup"><span data-stu-id="df00d-156">More information about run as users</span></span>

<span data-ttu-id="df00d-157">Als u meer informatie over uitvoeren als-id's en hoe ze factor in de beveiliging van een JEA-sessie te vinden in de [beveiligingsoverwegingen](security-considerations.md) artikel.</span><span class="sxs-lookup"><span data-stu-id="df00d-157">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="df00d-158">Transcripten van sessie</span><span class="sxs-lookup"><span data-stu-id="df00d-158">Session transcripts</span></span>

<span data-ttu-id="df00d-159">Het is raadzaam dat u een JEA-sessie-configuratiebestand op automatisch vastleggen Transcripten van gebruikerssessies configureert.</span><span class="sxs-lookup"><span data-stu-id="df00d-159">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="df00d-160">PowerShell-sessie Transcripten bevatten informatie over de gebruiker verbinding maakt, het uitvoeren als-identiteit is toegewezen, en de opdrachten worden uitgevoerd door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="df00d-160">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="df00d-161">Ze kunnen nuttig zijn voor een beoordelingsteam die nodig heeft om te begrijpen wie een specifieke wijziging in een systeem hebt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="df00d-161">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="df00d-162">Voor het configureren van automatische transcriptie in het configuratiebestand van de sessie, Geef een pad naar een map waar de Transcripten moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="df00d-162">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="df00d-163">De opgegeven map moet worden geconfigureerd om te voorkomen dat gebruikers van wijzigt of verwijdert alle gegevens in het.</span><span class="sxs-lookup"><span data-stu-id="df00d-163">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="df00d-164">Transcripten worden geschreven naar de map met het lokale systeemaccount, waarvoor lezen en schrijven toegang tot de map is vereist.</span><span class="sxs-lookup"><span data-stu-id="df00d-164">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="df00d-165">Standaardgebruikers kunnen geen toegang moeten hebben tot de map en een beperkte set van administrators voor rapportbeveiliging moet toegang hebben tot de Transcripten controleren.</span><span class="sxs-lookup"><span data-stu-id="df00d-165">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="df00d-166">Schijf van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="df00d-166">User drive</span></span>

<span data-ttu-id="df00d-167">Als uw verbindende gebruikers moeten het kopiëren van bestanden naar/van de JEA-eindpunt om uit te voeren van een opdracht, kunt u de schijf van de gebruiker in het configuratiebestand van de sessie inschakelen.</span><span class="sxs-lookup"><span data-stu-id="df00d-167">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="df00d-168">De schijf van de gebruiker is een [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) die is toegewezen aan een unieke map voor elke gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="df00d-168">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="df00d-169">Deze map fungeert als een ruimte voor deze bestanden te kopiëren naar/van het systeem zonder zodat ze toegang hebben tot het volledige systeem of de provider bestandssysteem om vrij te geven.</span><span class="sxs-lookup"><span data-stu-id="df00d-169">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="df00d-170">De inhoud van de gebruiker stations zijn persistent in verschillende sessies voor situaties waar de verbinding met het netwerk kan worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="df00d-170">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="df00d-171">Standaard kunt de schijf van de gebruiker u voor het opslaan van een maximum van 50MB aan gegevens per gebruiker.</span><span class="sxs-lookup"><span data-stu-id="df00d-171">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="df00d-172">U kunt de hoeveelheid gegevens die een gebruiker kan worden gebruikt met beperken de *UserDriveMaximumSize* veld.</span><span class="sxs-lookup"><span data-stu-id="df00d-172">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="df00d-173">Als u niet dat gegevens in de schijf van de gebruiker permanent zijn wilt, kunt u een geplande taak configureren op het systeem voor het automatisch opschonen van de map elke nacht.</span><span class="sxs-lookup"><span data-stu-id="df00d-173">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="df00d-174">De schijf van de gebruiker is alleen beschikbaar in Windows PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="df00d-174">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="df00d-175">Roldefinities</span><span class="sxs-lookup"><span data-stu-id="df00d-175">Role definitions</span></span>

<span data-ttu-id="df00d-176">Roldefinities in een sessie-configuratiebestand definieert de toewijzing van *gebruikers* naar *rollen*.</span><span class="sxs-lookup"><span data-stu-id="df00d-176">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="df00d-177">Elke gebruiker of groep die zijn opgenomen in dit veld wordt automatisch een machtiging verleend de JEA-eindpunt wanneer deze is geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="df00d-177">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="df00d-178">Elke gebruiker of groep kan worden opgenomen als een sleutel in de hash-tabel slechts één keer, maar meerdere rollen kan worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="df00d-178">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="df00d-179">De naam van de mogelijkheid van de rol moet de naam van het bestand van een rol mogelijkheid, zonder de extensie .psrc.</span><span class="sxs-lookup"><span data-stu-id="df00d-179">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="df00d-180">Als een gebruiker tot meer dan één groep in het roldefinitie van de behoort, krijgt zij toegang tot de functies van elk.</span><span class="sxs-lookup"><span data-stu-id="df00d-180">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="df00d-181">Als twee rollen toegang tot de dezelfde cmdlets verleent, worden de meest strikte parameterset wordt toegekend aan de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="df00d-181">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="df00d-182">Bij het opgeven van lokale gebruikers en groepen in het veld van de definities rol, zorg ervoor dat u de naam van de computer (niet *localhost* of *.*) voor de backslash opgeeft.</span><span class="sxs-lookup"><span data-stu-id="df00d-182">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="df00d-183">U kunt de naam van de computer controleren door het inspecteren van de `$env:computername` variabele.</span><span class="sxs-lookup"><span data-stu-id="df00d-183">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="df00d-184">Zoekvolgorde van rol mogelijkheid</span><span class="sxs-lookup"><span data-stu-id="df00d-184">Role capability search order</span></span>

<span data-ttu-id="df00d-185">Zoals u in het bovenstaande voorbeeld, rolmogelijkheden zijn waarnaar wordt verwezen door de platte domeinnaam (bestandsnaam zonder extensie) van het bestand van de mogelijkheid rol.</span><span class="sxs-lookup"><span data-stu-id="df00d-185">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="df00d-186">Als meerdere functie-mogelijkheden beschikbaar op het systeem met dezelfde naam platte zijn, kunnen PowerShell de impliciete zoekvolgorde wordt gebruikt om de effectieve rol mogelijkheid-bestand te selecteren.</span><span class="sxs-lookup"><span data-stu-id="df00d-186">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="df00d-187">Het wordt **niet** toegang geven tot alle rol mogelijkheid bestanden met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="df00d-187">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="df00d-188">JEA maakt gebruik van de `$env:PSModulePath` omgevingsvariabele om te bepalen welke paden om te scannen op rol mogelijkheid bestanden.</span><span class="sxs-lookup"><span data-stu-id="df00d-188">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="df00d-189">Binnen elk van deze paden zoekt JEA naar geldige PowerShell-modules die een submap 'RoleCapabilities' bevatten.</span><span class="sxs-lookup"><span data-stu-id="df00d-189">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="df00d-190">Net als bij importeren van modules, verkiest JEA rolmogelijkheden die worden geleverd met Windows op de mogelijkheden van de aangepaste rol met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="df00d-190">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="df00d-191">Voor alle andere naamconflicten wordt prioriteit bepaald door de volgorde waarin Windows de bestanden in de map inventariseert (niet noodzakelijkerwijs worden alfabetisch).</span><span class="sxs-lookup"><span data-stu-id="df00d-191">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="df00d-192">Het eerste bestand van de rol-mogelijkheid gevonden die overeenkomt met de gewenste naam wordt gebruikt voor de gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="df00d-192">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="df00d-193">Aangezien de zoekvolgorde van rol mogelijkheid is niet deterministisch wanneer twee of meer rolmogelijkheden dezelfde naam delen, is het **sterk aanbevolen** Zorg ervoor dat rolmogelijkheden unieke namen hebben op uw computer.</span><span class="sxs-lookup"><span data-stu-id="df00d-193">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="df00d-194">Regels voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="df00d-194">Conditional access rules</span></span>

<span data-ttu-id="df00d-195">Alle gebruikers en groepen die zijn opgenomen in het veld RoleDefinitions worden automatisch verleend voor toegang tot de JEA-eindpunten.</span><span class="sxs-lookup"><span data-stu-id="df00d-195">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="df00d-196">Regels voor voorwaardelijke toegang kunnen u deze toegang verfijnen en vereisen dat gebruikers deel uitmaken van aanvullende beveiligingsgroepen die niet van invloed op de rollen die zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="df00d-196">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="df00d-197">Dit is handig als u integreren een 'just in time wilt' in beschermde modus toegang krijgen tot de oplossing voor het beheer, smartcardverificatie of andere oplossing voor meervoudige verificatie met JEA.</span><span class="sxs-lookup"><span data-stu-id="df00d-197">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="df00d-198">Regels voor voorwaardelijke toegang worden gedefinieerd in het veld RequiredGroups in een sessie-configuratiebestand.</span><span class="sxs-lookup"><span data-stu-id="df00d-198">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="df00d-199">Daar kunt u een hash-tabel (eventueel geneste) die gebruikmaakt van bieden 'En' en 'Of' sleutels te maken van uw regels.</span><span class="sxs-lookup"><span data-stu-id="df00d-199">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="df00d-200">Hier volgen enkele voorbeelden van hoe u dit veld:</span><span class="sxs-lookup"><span data-stu-id="df00d-200">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="df00d-201">Regels voor voorwaardelijke toegang zijn alleen beschikbaar in Windows PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="df00d-201">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="df00d-202">Andere eigenschappen</span><span class="sxs-lookup"><span data-stu-id="df00d-202">Other properties</span></span>

<span data-ttu-id="df00d-203">Sessie-configuratiebestanden kunnen ook doen alles wat die een bestand van de mogelijkheid rol doen kunt, maar wel zonder de mogelijkheid om te verbinden gebruikerstoegang geven tot andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="df00d-203">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="df00d-204">Als u wilt dat alle gebruikers toegang tot bepaalde cmdlets, functies of -providers, kunt u doen rechts in het configuratiebestand van de sessie.</span><span class="sxs-lookup"><span data-stu-id="df00d-204">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="df00d-205">Voor een volledige lijst van ondersteunde eigenschappen in het configuratiebestand van de sessie, voert u `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="df00d-205">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="df00d-206">Testen van een sessie-configuratiebestand</span><span class="sxs-lookup"><span data-stu-id="df00d-206">Testing a session configuration file</span></span>

<span data-ttu-id="df00d-207">U kunt testen met een sessie configureren met behulp van de [Test PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df00d-207">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="df00d-208">Het is raadzaam dat u het configuratiebestand van de sessie testen als u hebt de voor-bestand handmatig met behulp van een teksteditor om te controleren of dat de syntaxis juist is bewerkt.</span><span class="sxs-lookup"><span data-stu-id="df00d-208">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="df00d-209">Als een sessie-configuratiebestand deze test niet slaagt, is het niet mogelijk om te worden geregistreerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="df00d-209">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="df00d-210">Voorbeeldconfiguratiebestand sessie</span><span class="sxs-lookup"><span data-stu-id="df00d-210">Sample session configuration file</span></span>

<span data-ttu-id="df00d-211">Hieronder volgt een compleet voorbeeld waarin wordt getoond hoe maakt en valideert de sessieconfiguratie van een voor JEA.</span><span class="sxs-lookup"><span data-stu-id="df00d-211">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="df00d-212">Houd er rekening mee dat de definities van gebruikersrollen worden gemaakt en opgeslagen in de `$roles` variabele voor uw gemak en leesbaarheid.</span><span class="sxs-lookup"><span data-stu-id="df00d-212">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="df00d-213">Het is niet vereist om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="df00d-213">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="df00d-214">Bijwerken van de sessie-configuratiebestanden</span><span class="sxs-lookup"><span data-stu-id="df00d-214">Updating session configuration files</span></span>

<span data-ttu-id="df00d-215">Als u wijzigen eigenschappen van een JEA-sessieconfiguratie wilt, met inbegrip van de toewijzing van gebruikers aan rollen, moet u [registratie](register-jea.md#unregistering-jea-configurations) en [opnieuw registreren](register-jea.md) de JEA-sessieconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="df00d-215">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="df00d-216">Als u de JEA-sessieconfiguratie opnieuw registreert, een bijgewerkte PowerShell-sessie configuratiebestand gebruiken met de gewenste wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="df00d-216">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="df00d-217">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="df00d-217">Next steps</span></span>

- [<span data-ttu-id="df00d-218">Een JEA-configuratiegegevens registreren</span><span class="sxs-lookup"><span data-stu-id="df00d-218">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="df00d-219">De auteur van JEA-rollen</span><span class="sxs-lookup"><span data-stu-id="df00d-219">Author JEA roles</span></span>](role-capabilities.md)
