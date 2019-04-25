---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
contributor: ryanpu
title: Verbeteringen in Just Enough Administration (JEA)
ms.openlocfilehash: 66cbacb78f8a365e9c8556c7c56b3c3525de7395
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055629"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="5aa8d-103">Verbeteringen in Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="5aa8d-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="5aa8d-104">Beperkte bestanden kopiëren naar JEA-eindpunten</span><span class="sxs-lookup"><span data-stu-id="5aa8d-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="5aa8d-105">Kunt u nu op afstand bestanden te kopiëren/in een JEA-eindpunt en rest kan worden gegarandeerd dat de gebruiker die de verbinding alleen kan niet kopiëren *eventuele* bestand op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="5aa8d-106">Dit is mogelijk door het configureren van uw voor-bestand voor het koppelen van een schijf van de gebruiker om verbinding te maken van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="5aa8d-107">De schijf van de gebruiker is een nieuwe PSDrive die uniek is voor elke gebruiker die verbinding maakt en clusterverbinding blijven behouden tussen sessies.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="5aa8d-108">Wanneer `Copy-Item` wordt gebruikt om bestanden te kopiëren naar of van een JEA-sessie, is deze beperkt tot alleen toegang tot de schijf van de gebruiker toestaan.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-108">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="5aa8d-109">Pogingen om bestanden te kopiëren naar een andere PSDrive mislukken.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="5aa8d-110">Om in te stellen de schijf van de gebruiker in uw configuratiebestand van de JEA-sessie, gebruikt u de volgende nieuwe velden:</span><span class="sxs-lookup"><span data-stu-id="5aa8d-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="5aa8d-111">De map die de schijf van de gebruiker een back-up wordt gemaakt op `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="5aa8d-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="5aa8d-112">Als u wilt gebruikmaken van de schijf van de gebruiker en kopiëren van bestanden naar/van een JEA-eindpunt dat is geconfigureerd als de schijf van de gebruiker beschikbaar wilt maken, gebruikt u de `-ToSession` en `-FromSession` parameters op `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="5aa8d-113">U kunt vervolgens aangepaste functies voor het verwerken van de gegevens die zijn opgeslagen in de schijf van de gebruiker en die beschikbaar maken voor gebruikers in uw rol mogelijkheid-bestand schrijven.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="5aa8d-114">Ondersteuning voor Group Managed Service Accounts</span><span class="sxs-lookup"><span data-stu-id="5aa8d-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="5aa8d-115">In sommige gevallen kan een taak die een gebruiker nodig heeft om uit te voeren in een JEA-sessie moet toegang tot bronnen voorbij de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="5aa8d-116">Wanneer een JEA-sessie is geconfigureerd voor het gebruik van een virtueel account, wordt elke poging tot deze bronnen afkomstig zijn van de identiteit van de lokale computer, niet de virtuele-account of verbonden gebruiker weergegeven.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="5aa8d-117">TP5, is voorzien van ondersteuning voor het uitvoeren van JEA in de context van een [groep beheerd serviceaccount](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), waardoor het veel eenvoudiger toegang krijgen tot netwerkbronnen met behulp van de identiteit van een domein.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="5aa8d-118">Voor het configureren van een JEA-sessie moet worden uitgevoerd in een gMSA-account, gebruikt u de volgende sleutel in het bestand voor:</span><span class="sxs-lookup"><span data-stu-id="5aa8d-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="5aa8d-119">Groep beheerde serviceaccounts doen niet zomaar de isolatie- of beperkte mogelijkheden van virtuele accounts.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-119">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="5aa8d-120">Elke gebruiker die verbinding maakt, wordt de hetzelfde gMSA-id, die mogelijk machtigingen in uw gehele organisatie delen.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="5aa8d-121">Wees voorzichtig bij het selecteren van een gMSA gebruiken en altijd de voorkeur geeft aan virtuele accounts die zijn beperkt tot de lokale computer, indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="5aa8d-122">Beleid voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="5aa8d-122">Conditional access policies</span></span>

<span data-ttu-id="5aa8d-123">JEA is erg handig bij het beperken van iemand kunt doen wanneer ze hebt verbonden met een systeem te beheren, maar wat als u ook wilt beperken *wanneer* iemand kunt JEA gebruiken?</span><span class="sxs-lookup"><span data-stu-id="5aa8d-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="5aa8d-124">Configuratie-opties in de sessie-configuratiebestanden (.pssc) waarin u kunt opgeven-beveiligingsgroepen waartoe een gebruiker behoren moet om een JEA-sessie tot stand brengen, hebben we toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="5aa8d-125">Dit kan vooral nuttig zijn als u een systeem alleen In tijd (JIT) in uw omgeving hebt en maken van uw gebruikers wilt voordat u toegang tot een JEA-eindpunt voor veel bevoegdheden verhogen.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="5aa8d-126">De nieuwe *RequiredGroups* veld in het bestand voor kunt u de logica om na te gaan als een gebruiker verbinding met JEA maken kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="5aa8d-127">Er bestaat voor het opgeven van een hash-tabel (eventueel geneste) die gebruikmaakt van de 'En' en 'Of' sleutels te maken van uw regels.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="5aa8d-128">Hier volgen enkele voorbeelden van hoe u dit veld:</span><span class="sxs-lookup"><span data-stu-id="5aa8d-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="5aa8d-129">Opgelost: Virtuele accounts worden nu ondersteund op Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5aa8d-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="5aa8d-130">In WMF 5.1 bent u nu te kunnen gebruikmaken van virtuele accounts in Windows Server 2008 R2, waardoor consistente configuraties en functiepariteit voor Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="5aa8d-131">Virtuele accounts blijven wordt niet ondersteund bij het gebruik van JEA op Windows 7.</span><span class="sxs-lookup"><span data-stu-id="5aa8d-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>