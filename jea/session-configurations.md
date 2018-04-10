---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell beveiliging
title: JEA Sessieconfiguraties
ms.openlocfilehash: 317a549ed20b5800d5bafdabd266e93ba7cd321c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="jea-session-configurations"></a><span data-ttu-id="0e2a4-103">JEA Sessieconfiguraties</span><span class="sxs-lookup"><span data-stu-id="0e2a4-103">JEA Session Configurations</span></span>

> <span data-ttu-id="0e2a4-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0e2a4-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0e2a4-105">Een eindpunt JEA is geregistreerd op een systeem door het maken en registreren van een configuratiebestand van de PowerShell-sessie in een bepaalde manier.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="0e2a4-106">Bepalen van sessieconfiguraties *die* het eindpunt JEA kunt gebruiken, en welke rollen hebben toegang tot.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="0e2a4-107">Ze bepalen ook algemene instellingen die van toepassing op gebruikers van een rol in de sessie JEA.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="0e2a4-108">In dit onderwerp wordt beschreven hoe een configuratiebestand van de PowerShell-sessie maken en een eindpunt JEA registreren.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="0e2a4-109">Een configuratiebestand sessie maken</span><span class="sxs-lookup"><span data-stu-id="0e2a4-109">Create a session configuration file</span></span>

<span data-ttu-id="0e2a4-110">Om een eindpunt JEA registreren, moet u opgeven hoe dat eindpunt moet worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="0e2a4-111">Er zijn veel opties om te overwegen hier, de belangrijkste welke is die toegang moeten hebben tot het eindpunt JEA, welke functies worden ze worden toegewezen, welke identiteit JEA gebruiken onder de dekt en wat de naam van het eindpunt JEA zal zijn.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="0e2a4-112">Deze worden alle gedefinieerd in een configuratiebestand voor PowerShell-sessie die is een PowerShell-gegevensbestand eindigt met de extensie .pssc.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="0e2a4-113">Voer de volgende opdracht voor het maken van een geraamte sessie-configuratiebestand voor JEA eindpunten.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="0e2a4-114">Alleen de meest voorkomende configuratieopties zijn standaard opgenomen in het geraamte bestand.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="0e2a4-115">Gebruik de `-Full` switch in de gegenereerde voor alle toepasselijke instellingen wilt opnemen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="0e2a4-116">U kunt het configuratiebestand van de sessie openen in een teksteditor.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="0e2a4-117">De `-SessionType RestrictedRemoteServer` veld geeft aan dat de sessieconfiguratie van de wordt gebruikt door JEA voor beveiligde management.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="0e2a4-118">Sessies is geconfigureerd op deze manier wordt uitgevoerd [NoLanguage modus](https://technet.microsoft.com/library/dn433292.aspx) en hebt u alleen de volgende standaardopdrachten uit 8-(en aliassen) beschikbaar:</span><span class="sxs-lookup"><span data-stu-id="0e2a4-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="0e2a4-119">Clear-Host (cls, wissen)</span><span class="sxs-lookup"><span data-stu-id="0e2a4-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="0e2a4-120">Exit-PSSession (exsn, afsluiten)</span><span class="sxs-lookup"><span data-stu-id="0e2a4-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="0e2a4-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="0e2a4-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="0e2a4-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="0e2a4-122">Get-FormatData</span></span>
- <span data-ttu-id="0e2a4-123">Help ontvangen</span><span class="sxs-lookup"><span data-stu-id="0e2a4-123">Get-Help</span></span>
- <span data-ttu-id="0e2a4-124">Meetobject (maatregel)</span><span class="sxs-lookup"><span data-stu-id="0e2a4-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="0e2a4-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="0e2a4-125">Out-Default</span></span>
- <span data-ttu-id="0e2a4-126">Select-Object (geselecteerd)</span><span class="sxs-lookup"><span data-stu-id="0e2a4-126">Select-Object (select)</span></span>

<span data-ttu-id="0e2a4-127">Geen PowerShell-providers beschikbaar zijn en worden dat alle externe programma's (uitvoerbare bestanden, scripts, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="0e2a4-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="0e2a4-128">Er zijn diverse andere velden die u wilt configureren voor de sessie JEA.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="0e2a4-129">Ze worden in de volgende secties besproken.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="0e2a4-130">Kies de identiteit JEA</span><span class="sxs-lookup"><span data-stu-id="0e2a4-130">Choose the JEA identity</span></span>

<span data-ttu-id="0e2a4-131">JEA moet achter de schermen wordt een identiteit (account) moet worden gebruikt wanneer een gebruiker verbonden opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="0e2a4-132">U besluiten welke identiteit JEA wordt gebruikt in het configuratiebestand van de sessie.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="0e2a4-133">Lokale virtuele-Account</span><span class="sxs-lookup"><span data-stu-id="0e2a4-133">Local Virtual Account</span></span>

<span data-ttu-id="0e2a4-134">Als de rollen die worden ondersteund door dit eindpunt JEA worden gebruikt voor het beheren van de lokale computer en een lokaal beheerdersaccount volstaat om de opdrachten succes is uitgevoerd, moet u JEA voor het gebruik van een lokale virtuele-account configureren.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="0e2a4-135">Virtuele accounts zijn tijdelijke accounts die uniek is voor een specifieke gebruiker en alleen de laatste voor de duur van de PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="0e2a4-136">Op een lidserver of werkstation virtuele accounts deel uitmaken van de lokale computer **beheerders** groeperen en hebben toegang tot de meeste systeembronnen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="0e2a4-137">Op een Active Directory-domeincontroller virtuele accounts deel uitmaken van het domein **Domeinadministrators** groep.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="0e2a4-138">Als de rollen die worden ondersteund door de sessieconfiguratie geen dergelijke brede bevoegdheden vereist, kunt u eventueel de beveiligingsgroepen waartoe het virtuele-account behoort.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="0e2a4-139">De opgegeven beveiligingsgroepen moet op een lidserver of werkstation lokale groepen, niet voor groepen van een domein.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="0e2a4-140">Wanneer een of meer beveiligingsgroepen wordt opgegeven, wordt niet langer virtueel account aan de beheerdersgroep lokaal of domeinbeheerder behoren.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="0e2a4-141">Door groep beheerd serviceaccount</span><span class="sxs-lookup"><span data-stu-id="0e2a4-141">Group Managed Service Account</span></span>


<span data-ttu-id="0e2a4-142">Een beheerd serviceaccount (gMSA) is voor scenario's vereisen dat de gebruiker JEA voor toegang tot netwerkbronnen zoals andere machines of webservices, een geschiktere identiteit moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="0e2a4-143">gMSA accounts bieden u de identiteit van een domein dat kan worden gebruikt voor verificatie op basis van bronnen op elke computer in het domein.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="0e2a4-144">De rechten van het gMSA-account biedt u wordt bepaald door de bronnen die u wilt openen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="0e2a4-145">U wordt automatisch geen beheerdersrechten op alle machines of services tenzij de beheerder van de machine-service heeft expliciet verleend voor het gMSA-account beheerdersbevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="0e2a4-146">accounts van gMSA mag alleen worden gebruikt wanneer toegang tot netwerkbronnen zijn vereist voor een aantal oorzaken hebben:</span><span class="sxs-lookup"><span data-stu-id="0e2a4-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="0e2a4-147">Is het moeilijker te traceren terug acties voor een gebruiker wanneer u een beheerd serviceaccount omdat elke gebruiker dezelfde run as-id deelt.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="0e2a4-148">U moet Raadpleeg Logboeken correleren van gebruikers met hun acties en transcripties van PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="0e2a4-149">Het gMSA-account hebben mogelijk toegang tot veel netwerkbronnen die de gebruiker die de verbinding heeft geen toegang tot nodig.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="0e2a4-150">Probeert altijd effectieve machtigingen beperken in een sessie JEA volgen het principe van minimale bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="0e2a4-151">Groep beheerde serviceaccounts zijn alleen beschikbaar in Windows PowerShell 5.1 of nieuwere en op computers die lid zijn van een domein.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="0e2a4-152">Meer informatie over run as-gebruikers</span><span class="sxs-lookup"><span data-stu-id="0e2a4-152">More information about run as users</span></span>

<span data-ttu-id="0e2a4-153">Meer informatie over uitvoeren als identiteiten en hoe ze rekening te houden in de beveiliging van een sessie JEA vindt u in de [beveiligingsoverwegingen](security-considerations.md) artikel.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="0e2a4-154">Sessie transcripties</span><span class="sxs-lookup"><span data-stu-id="0e2a4-154">Session transcripts</span></span>

<span data-ttu-id="0e2a4-155">Het verdient aanbeveling dat u een configuratiebestand voor JEA sessie automatisch vastleggen uitgeschreven gebruikerssessies configureert.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="0e2a4-156">PowerShell-sessie transcripties bevatten informatie over de gebruiker verbinding maakt, het run as-identiteit is toegewezen, en de opdrachten uitgevoerd door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="0e2a4-157">Ze kunnen nuttig zijn voor een controle team wil weten wie een bepaalde wijziging in een systeem uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="0e2a4-158">Voor het configureren van automatische schrijffouten in het configuratiebestand van de sessie, Geef een pad naar een map waar de transcripties moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="0e2a4-159">De opgegeven map moet worden geconfigureerd om te voorkomen dat gebruikers wijzigen of verwijderen van alle gegevens in dit.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="0e2a4-160">Transcripties worden geschreven naar de map door het lokale systeemaccount, waarvoor lees- en schrijftoegang tot de map is vereist.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="0e2a4-161">Standaardgebruikers moeten hebben geen toegang tot de map en een beperkt aantal Beveiligingsbeheerders moet toegang hebben tot de transcripties controleren.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="0e2a4-162">Schijf van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="0e2a4-162">User drive</span></span>

<span data-ttu-id="0e2a4-163">Als uw gebruikers verbinding moeten voor het kopiëren van bestanden naar het eindpunt JEA om een opdracht wordt uitgevoerd, kunt u de schijf van de gebruiker in het configuratiebestand van de sessie inschakelen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="0e2a4-164">De schijf van de gebruiker is een [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) die is toegewezen aan een unieke map voor elke gebruiker die verbinding maakt.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-164">The user drive is a [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="0e2a4-165">Deze map fungeert als een ruimte voor deze bestanden te kopiëren van het systeem zonder zodat ze toegang hebben tot het volledige bestandssysteem of de provider bestandssysteem blootstellen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="0e2a4-166">De inhoud van de gebruiker stations zijn permanent over de sessies voor situaties waarin de verbinding met het netwerk mag worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="0e2a4-167">Standaard kunt de schijf van de gebruiker u voor het opslaan van een maximum van 50MB aan gegevens per gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="0e2a4-168">U kunt de hoeveelheid gegevens die een gebruiker met gebruiken kunt beperken de *UserDriveMaximumSize* veld.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="0e2a4-169">Als u niet dat de gegevens in het station gebruiker permanent zijn wilt, kunt u een geplande taak op het systeem automatisch opschonen van de map elke nacht configureren.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="0e2a4-170">De schijf van de gebruiker is alleen beschikbaar in Windows PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="0e2a4-171">Roldefinities</span><span class="sxs-lookup"><span data-stu-id="0e2a4-171">Role definitions</span></span>

<span data-ttu-id="0e2a4-172">Roldefinities in een configuratiebestand sessie definiëren de toewijzing van *gebruikers* naar *rollen*.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="0e2a4-173">Elke gebruiker of groep die zijn opgenomen in dit veld wordt automatisch worden gemachtigd voor het eindpunt JEA wanneer deze is geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="0e2a4-174">Elke gebruiker of groep kan worden opgenomen als de sleutel in de hash-tabel slechts één keer, maar kan meerdere functies worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="0e2a4-175">De naam van de mogelijkheid van de rol moet de naam van het bestand van de rol mogelijkheid zonder de extensie .psrc.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="0e2a4-176">Als een gebruiker tot meer dan één groep in de roldefinitie van de behoort, krijgen ze toegang tot de functies van elk.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="0e2a4-177">Als twee rollen toegang tot de dezelfde cmdlets verlenen, wordt de meest strikte parameterset worden toegekend aan de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="0e2a4-178">Bij het opgeven van lokale gebruikers en groepen in het veld rol-definities, moet u de naam van de computer gebruikt (geen *localhost* of *.*) voordat u de backslash.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="0e2a4-179">U kunt de naam van de computer controleren door te inspecteren de `$env:computername` variabele.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="0e2a4-180">Zoekvolgorde van rol mogelijkheid</span><span class="sxs-lookup"><span data-stu-id="0e2a4-180">Role capability search order</span></span>
<span data-ttu-id="0e2a4-181">Zoals u in het bovenstaande voorbeeld, rol mogelijkheden zijn waarnaar wordt verwezen door de platte domeinnaam (bestandsnaam zonder de extensie) van het bestand van de mogelijkheid rol.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="0e2a4-182">Als meerdere rol mogelijkheden beschikbaar op het systeem met dezelfde naam platte zijn, kunnen PowerShell de impliciete zoekvolgorde wordt gebruikt om de effectieve rol mogelijkheid-bestand te selecteren.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="0e2a4-183">Het **niet** toegang geven tot alle rol capability-bestanden met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="0e2a4-184">JEA gebruikt de `$env:PSModulePath` omgevingsvariabele om te bepalen welke paden om te scannen op rol capability-bestanden.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="0e2a4-185">In elk van die paden zoekt JEA naar geldige PowerShell-modules die een submap 'RoleCapabilities' bevatten.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="0e2a4-186">Net als bij het importeren van modules, verkiest JEA rol mogelijkheden die worden geleverd met Windows tot mogelijkheden van de aangepaste rol met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="0e2a4-187">Voor alle andere naamconflicten wordt prioriteit bepaald door de volgorde waarin Windows de bestanden in de map somt (niet noodzakelijkerwijs alfabetisch).</span><span class="sxs-lookup"><span data-stu-id="0e2a4-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="0e2a4-188">Het eerste rol mogelijkheid bestand gevonden die overeenkomt met de gewenste naam voor de gebruiker die de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="0e2a4-189">Aangezien de zoekvolgorde van rol mogelijkheid is niet deterministisch wanneer twee of meer mogelijkheden van de functie dezelfde naam delen, is het **sterk aanbevolen** Zorg ervoor dat functie-mogelijkheden unieke namen hebben op uw computer.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="0e2a4-190">Regels voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="0e2a4-190">Conditional access rules</span></span>

<span data-ttu-id="0e2a4-191">Alle gebruikers en groepen die zijn opgenomen in het veld RoleDefinitions krijgen automatisch toegang tot JEA eindpunten.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="0e2a4-192">Regels voor voorwaardelijke toegang kunnen u deze toegang verfijnen en gebruikers moeten behoren tot meer beveiligingsgroepen die hebben geen invloed op de rollen die ze zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="0e2a4-193">Dit is handig als u integreren van een 'just-in tijd wilt' bevoegde toegang tot oplossing voor het beheer, smartcardverificatie of een andere oplossing multifactor-verificatie met JEA.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="0e2a4-194">Regels voor voorwaardelijke toegang worden gedefinieerd in het veld RequiredGroups in een sessie-configuratiebestand.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="0e2a4-195">Daar kunt u een hash-tabel (eventueel geneste) die gebruikmaakt van bieden 'En' en 'Of' sleutels u uw regels samenstelt.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="0e2a4-196">Hier volgen enkele voorbeelden van hoe u dit veld:</span><span class="sxs-lookup"><span data-stu-id="0e2a4-196">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="0e2a4-197">Regels voor voorwaardelijke toegang zijn alleen beschikbaar in Windows PowerShell 5.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="0e2a4-198">Andere eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0e2a4-198">Other properties</span></span>
<span data-ttu-id="0e2a4-199">Sessie-configuratiebestanden kunnen alles die een rol mogelijkheid bestand uitvoeren kunt, maar wel zonder de mogelijkheid om te verbinden gebruikerstoegang geven tot andere opdrachten ook doen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="0e2a4-200">Als u dat alle gebruikers toegang tot bepaalde cmdlets, functies of providers wilt, kunt u doen rechts in het configuratiebestand van de sessie.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="0e2a4-201">Voer voor een volledige lijst met ondersteunde eigenschappen in het configuratiebestand van de sessie `Get-Help New-PSSessionConfigurationFile -Full`.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="0e2a4-202">Een configuratiebestand sessie testen</span><span class="sxs-lookup"><span data-stu-id="0e2a4-202">Testing a session configuration file</span></span>

<span data-ttu-id="0e2a4-203">U kunt testen met een sessie configuratie met de [Test PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="0e2a4-204">Het is raadzaam dat u uw configuratiebestand sessie testen als u de voor-bestand handmatig met een teksteditor om te controleren of dat de syntaxis is juist hebt bewerkt.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="0e2a4-205">Als een sessie-configuratiebestand deze test niet slaagt, is het niet mogelijk is op het systeem worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="0e2a4-206">Voorbeeldconfiguratiebestand sessie</span><span class="sxs-lookup"><span data-stu-id="0e2a4-206">Sample session configuration file</span></span>

<span data-ttu-id="0e2a4-207">Hieronder volgt een voorbeeld van een volledige waarin wordt getoond hoe maakt en valideert de sessieconfiguratie van een voor JEA.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="0e2a4-208">Houd er rekening mee dat de definities van gebruikersrollen worden gemaakt en opgeslagen in de `$roles` variabele voor uw gemak en de leesbaarheid.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="0e2a4-209">Het is niet vereist om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="0e2a4-210">Sessie-configuratiebestanden bijwerken</span><span class="sxs-lookup"><span data-stu-id="0e2a4-210">Updating session configuration files</span></span>

<span data-ttu-id="0e2a4-211">Als u wijzigen van de eigenschappen van een sessieconfiguratie JEA wilt, met inbegrip van de toewijzing van gebruikers aan rollen, moet u [registratie](register-jea.md#unregistering-jea-configurations) en [opnieuw registreren](register-jea.md) de sessieconfiguratie JEA.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="0e2a4-212">Wanneer u de configuratie van de sessie JEA opnieuw registreren, gebruikt u een bijgewerkte PowerShell-sessie configuratiebestand met de gewenste wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="0e2a4-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0e2a4-213">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="0e2a4-213">Next steps</span></span>

- [<span data-ttu-id="0e2a4-214">De configuratie van een JEA registreren</span><span class="sxs-lookup"><span data-stu-id="0e2a4-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="0e2a4-215">Auteur JEA rollen</span><span class="sxs-lookup"><span data-stu-id="0e2a4-215">Author JEA roles</span></span>](role-capabilities.md)