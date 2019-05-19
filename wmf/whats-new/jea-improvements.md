---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in Just Enough Administration (JEA)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856201"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="b2d30-103">Verbeteringen in Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="b2d30-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="b2d30-104">Just Enough Administration is een nieuwe functie in WMF 5.0 waarmee Rolgebaseerd beheer via externe communicatie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b2d30-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="b2d30-105">Deze uitbreiding van de bestaande infrastructuur van beperkte eindpunt doordat niet-beheerders kunnen specifieke opdrachten, scripts en uitvoerbare bestanden uitvoeren als beheerder.</span><span class="sxs-lookup"><span data-stu-id="b2d30-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="b2d30-106">Hiermee kunt u Verminder het aantal volledige beheerders in uw omgeving en beveiliging te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="b2d30-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="b2d30-107">Beperkte bestanden kopiëren naar JEA-eindpunten</span><span class="sxs-lookup"><span data-stu-id="b2d30-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="b2d30-108">U kunt nu op afstand bestanden kopiëren naar/van een JEA-eindpunt en er zeker van zijn dat de gebruiker die de verbinding alleen kan niet kopiëren *eventuele* bestand op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="b2d30-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="b2d30-109">Dit is mogelijk door het configureren van uw voor-bestand voor het koppelen van een schijf van de gebruiker om verbinding te maken van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="b2d30-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="b2d30-110">De schijf van de gebruiker is een nieuwe PSDrive die uniek is voor elke gebruiker die verbinding maakt en clusterverbinding blijven behouden tussen sessies.</span><span class="sxs-lookup"><span data-stu-id="b2d30-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="b2d30-111">Wanneer `Copy-Item` wordt gebruikt om bestanden te kopiëren naar of van een JEA-sessie, is deze beperkt tot alleen toegang tot de schijf van de gebruiker toestaan.</span><span class="sxs-lookup"><span data-stu-id="b2d30-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="b2d30-112">Pogingen om bestanden te kopiëren naar een andere PSDrive mislukken.</span><span class="sxs-lookup"><span data-stu-id="b2d30-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="b2d30-113">Om in te stellen de schijf van de gebruiker in uw configuratiebestand van de JEA-sessie, gebruikt u de volgende nieuwe velden:</span><span class="sxs-lookup"><span data-stu-id="b2d30-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="b2d30-114">De map die de schijf van de gebruiker een back-up wordt gemaakt op `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="b2d30-114">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="b2d30-115">Als u wilt gebruikmaken van de schijf van de gebruiker en kopiëren van bestanden naar/van een JEA-eindpunt dat is geconfigureerd als de schijf van de gebruiker beschikbaar wilt maken, gebruikt u de `-ToSession` en `-FromSession` parameters op `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="b2d30-115">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

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

<span data-ttu-id="b2d30-116">U kunt vervolgens aangepaste functies voor het verwerken van de gegevens die zijn opgeslagen in de schijf van de gebruiker en die beschikbaar maken voor gebruikers in uw rol mogelijkheid-bestand schrijven.</span><span class="sxs-lookup"><span data-stu-id="b2d30-116">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="b2d30-117">Ondersteuning voor Group Managed Service Accounts</span><span class="sxs-lookup"><span data-stu-id="b2d30-117">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="b2d30-118">In sommige gevallen kan een taak die een gebruiker nodig heeft om uit te voeren in een JEA-sessie moet toegang tot bronnen voorbij de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b2d30-118">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="b2d30-119">Wanneer een JEA-sessie is geconfigureerd voor het gebruik van een virtueel account, wordt elke poging tot deze bronnen afkomstig zijn van de identiteit van de lokale computer, niet de virtuele-account of verbonden gebruiker weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b2d30-119">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="b2d30-120">TP5, is voorzien van ondersteuning voor het uitvoeren van JEA in de context van een [groep beheerd serviceaccount](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), waardoor het veel eenvoudiger toegang krijgen tot netwerkbronnen met behulp van de identiteit van een domein.</span><span class="sxs-lookup"><span data-stu-id="b2d30-120">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="b2d30-121">Voor het configureren van een JEA-sessie moet worden uitgevoerd in een gMSA-account, gebruikt u de volgende sleutel in het bestand voor:</span><span class="sxs-lookup"><span data-stu-id="b2d30-121">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="b2d30-122">Groep beheerde serviceaccounts doen niet zomaar de isolatie- of beperkte mogelijkheden van virtuele accounts.</span><span class="sxs-lookup"><span data-stu-id="b2d30-122">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="b2d30-123">Elke gebruiker die verbinding maakt, wordt de hetzelfde gMSA-id, die mogelijk machtigingen in uw gehele organisatie delen.</span><span class="sxs-lookup"><span data-stu-id="b2d30-123">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="b2d30-124">Wees voorzichtig bij het selecteren van een gMSA gebruiken en altijd de voorkeur geeft aan virtuele accounts die zijn beperkt tot de lokale computer, indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="b2d30-124">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="b2d30-125">Beleid voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="b2d30-125">Conditional access policies</span></span>

<span data-ttu-id="b2d30-126">JEA is erg handig bij het beperken van iemand kunt doen wanneer ze hebt verbonden met een systeem te beheren, maar wat als u ook wilt beperken *wanneer* iemand kunt JEA gebruiken?</span><span class="sxs-lookup"><span data-stu-id="b2d30-126">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="b2d30-127">Configuratie-opties in de sessie-configuratiebestanden (.pssc) waarin u kunt opgeven-beveiligingsgroepen waartoe een gebruiker behoren moet om een JEA-sessie tot stand brengen, hebben we toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b2d30-127">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="b2d30-128">Dit is vooral handig als u een systeem alleen In tijd (JIT) in uw omgeving hebt en maken van uw gebruikers wilt voordat u toegang tot een JEA-eindpunt voor veel bevoegdheden verhogen.</span><span class="sxs-lookup"><span data-stu-id="b2d30-128">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="b2d30-129">De nieuwe *RequiredGroups* veld in het bestand voor kunt u de logica om na te gaan als een gebruiker verbinding met JEA maken kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="b2d30-129">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="b2d30-130">Er bestaat voor het opgeven van een hash-tabel (eventueel geneste) die gebruikmaakt van de 'En' en 'Of' sleutels te maken van uw regels.</span><span class="sxs-lookup"><span data-stu-id="b2d30-130">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="b2d30-131">Hier volgen enkele voorbeelden van hoe u dit veld:</span><span class="sxs-lookup"><span data-stu-id="b2d30-131">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="b2d30-132">Opgelost: Virtuele accounts worden nu ondersteund op Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b2d30-132">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="b2d30-133">In WMF 5.1 bent u nu te kunnen gebruikmaken van virtuele accounts in Windows Server 2008 R2, waardoor consistente configuraties en functiepariteit voor Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="b2d30-133">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="b2d30-134">Virtuele accounts blijven wordt niet ondersteund bij het gebruik van JEA op Windows 7.</span><span class="sxs-lookup"><span data-stu-id="b2d30-134">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>