---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
contributor: ryanpu
title: Verbeteringen in Just Enough Administration (JEA)
ms.openlocfilehash: 47a58a6fae9f3a41ec527ec1f77ac1c196336669
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="47447-103">Verbeteringen in Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="47447-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="47447-104">Beperkte bestandskopie uit JEA-eindpunten</span><span class="sxs-lookup"><span data-stu-id="47447-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="47447-105">U kunt nu bestanden op afstand kopiëren/van een JEA eindpunt en rest gegarandeerd dat de gebruiker verbinding maakt alleen kan niet kopiëren *eventuele* bestand op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="47447-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span>
<span data-ttu-id="47447-106">Dit is mogelijk door het configureren van uw bestand voor om te koppelen van een station van de gebruiker voor de verbinding van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="47447-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span>
<span data-ttu-id="47447-107">De schijf van de gebruiker is een nieuwe PSDrive die uniek is voor elke gebruiker die verbinding maakt en blijft bestaan tussen sessies.</span><span class="sxs-lookup"><span data-stu-id="47447-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span>
<span data-ttu-id="47447-108">Wanneer het Item kopiëren wordt gebruikt om bestanden te kopiëren naar of van een sessie JEA, is deze beperkt tot alleen toegang tot de schijf van de gebruiker toestaan.</span><span class="sxs-lookup"><span data-stu-id="47447-108">When Copy-Item is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span>
<span data-ttu-id="47447-109">Pogingen om bestanden te kopiëren naar een andere PSDrive mislukken.</span><span class="sxs-lookup"><span data-stu-id="47447-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="47447-110">Gebruik de volgende nieuwe velden voordat u de schijf van de gebruiker in uw configuratiebestand JEA-sessie kunt instellen:</span><span class="sxs-lookup"><span data-stu-id="47447-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="47447-111">De map back-ups maken van de schijf van de gebruiker wordt gemaakt op `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="47447-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="47447-112">Als u wilt gebruikmaken van de schijf van de gebruiker en kopieer de bestanden naar/van een eindpunt JEA is geconfigureerd om de schijf van de gebruiker weer te geven, gebruikt u de `-ToSession` en `-FromSession` parameters op Copy-Item.</span><span class="sxs-lookup"><span data-stu-id="47447-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on Copy-Item.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="47447-113">U kunt vervolgens aangepaste functies om te verwerken van de gegevens die zijn opgeslagen in het station van de gebruiker en deze beschikbaar te maken voor gebruikers in uw bestand rol mogelijkheid schrijven.</span><span class="sxs-lookup"><span data-stu-id="47447-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="47447-114">Ondersteuning voor de groep Managed Service Accounts</span><span class="sxs-lookup"><span data-stu-id="47447-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="47447-115">In sommige gevallen moet een taak die een gebruiker moet uitvoeren in een sessie JEA mogelijk toegang tot bronnen voorbij de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="47447-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span>
<span data-ttu-id="47447-116">Wanneer een sessie JEA is geconfigureerd voor gebruik van een virtueel account, wordt elke poging tot deze bronnen afkomstig zijn van de identiteit van de lokale computer, niet de virtueel account of verbonden gebruiker weergegeven.</span><span class="sxs-lookup"><span data-stu-id="47447-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span>
<span data-ttu-id="47447-117">In TP5, hebben we ondersteuning voor het uitvoeren van JEA onder de context van een [groep beheerd serviceaccount](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx) ingeschakeld, waardoor het veel eenvoudiger toegang tot netwerkbronnen met behulp van de identiteit van een domein.</span><span class="sxs-lookup"><span data-stu-id="47447-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="47447-118">Gebruik voor het configureren van een sessie JEA worden uitgevoerd onder een beheerd serviceaccount voor de volgende sleutel in uw bestand voor:</span><span class="sxs-lookup"><span data-stu-id="47447-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> <span data-ttu-id="47447-119">**Opmerking:** isolatie of beperkte mogelijkheden van virtuele accounts komen niet toestaan van beheerde serviceaccounts voor groepen.</span><span class="sxs-lookup"><span data-stu-id="47447-119">**Note:** Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="47447-120">Elke gebruiker die verbinding maakt, wordt de hetzelfde gMSA-identiteit die mogelijk machtigingen van het gehele bedrijf delen.</span><span class="sxs-lookup"><span data-stu-id="47447-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span>
> <span data-ttu-id="47447-121">Wees voorzichtig bij het selecteren van een gMSA te gebruiken en altijd liever virtuele accounts die zijn beperkt tot de lokale machine indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="47447-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="47447-122">Beleid voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="47447-122">Conditional access policies</span></span>

<span data-ttu-id="47447-123">JEA is een goede beperkt wat iemand kunt doen wanneer ze hebt aangesloten op een systeem voor het beheren, maar wat als u ook wilt beperken *wanneer* iemand JEA kunt gebruiken?</span><span class="sxs-lookup"><span data-stu-id="47447-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span>
<span data-ttu-id="47447-124">Configuratie-opties in de configuratiebestanden sessie (.pssc) waarin u kunt opgeven beveiligingsgroepen waartoe een gebruiker behoren moet om een sessie JEA stand te brengen, hebben we toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="47447-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span>
<span data-ttu-id="47447-125">Dit is vooral handig als u een systeem net In tijd (Just in time) in uw omgeving hebt en maken van uw gebruikers hun bevoegdheden wilt voor de toegang tot een hoge bevoegdheden JEA-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="47447-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="47447-126">De nieuwe *RequiredGroups* veld in het bestand voor kunt u de logica om na te gaan als een gebruiker verbinding met JEA maken kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="47447-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span>
<span data-ttu-id="47447-127">Bestaat uit het opgeven van een hashtabel (eventueel geneste) die gebruikmaakt van de 'En' en 'Of' sleutels u uw regels samenstelt.</span><span class="sxs-lookup"><span data-stu-id="47447-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="47447-128">Hier volgen enkele voorbeelden van hoe u dit veld:</span><span class="sxs-lookup"><span data-stu-id="47447-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="47447-129">Vaste: Virtuele accounts worden nu ondersteund op Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="47447-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>
<span data-ttu-id="47447-130">WMF 5.1 bent u nu virtuele accounts gebruiken op Windows Server 2008 R2 inschakelen consistente configuraties en functie pariteit via Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="47447-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span>
<span data-ttu-id="47447-131">Virtuele accounts blijven wordt niet ondersteund wanneer u JEA op Windows 7.</span><span class="sxs-lookup"><span data-stu-id="47447-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>
