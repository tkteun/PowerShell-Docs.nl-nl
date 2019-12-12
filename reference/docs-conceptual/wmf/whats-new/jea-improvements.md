---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen van Just Enough Administration (JEA)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145031"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="e2a16-103">Verbeteringen van Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="e2a16-103">Improvements to Just Enough Administration (JEA)</span></span>

<span data-ttu-id="e2a16-104">Net genoeg beheer is een nieuwe functie in WMF 5,0 waarmee beheer op basis van rollen via Power shell Remoting kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e2a16-104">Just Enough Administration is a new feature in WMF 5.0 that enables role-based administration through PowerShell remoting.</span></span> <span data-ttu-id="e2a16-105">Hiermee wordt de bestaande beperkte eindpunt infrastructuur uitgebreid, omdat niet-beheerders specifieke opdrachten, scripts en uitvoer bare bestanden kunnen uitvoeren als beheerder.</span><span class="sxs-lookup"><span data-stu-id="e2a16-105">It extends the existing constrained endpoint infrastructure by allowing non-administrators to run specific commands, scripts, and executables as an administrator.</span></span> <span data-ttu-id="e2a16-106">Zo kunt u het aantal volledige beheerders in uw omgeving verminderen en de beveiliging verbeteren.</span><span class="sxs-lookup"><span data-stu-id="e2a16-106">This enables you to reduce the number of full administrators in your environment and improve security.</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="e2a16-107">Beperkte bestands kopie naar/van JEA-eind punten</span><span class="sxs-lookup"><span data-stu-id="e2a16-107">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="e2a16-108">U kunt bestanden nu extern kopiëren naar/van een JEA-eind punt en er zeker van zijn dat de gebruiker die de verbinding maakt, alleen *een* bestand op uw systeem kan kopiëren.</span><span class="sxs-lookup"><span data-stu-id="e2a16-108">You can now remotely copy files to/from a JEA endpoint and be assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="e2a16-109">Dit is mogelijk door uw PSSC-bestand te configureren om een gebruikers station te koppelen voor het verbinden van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="e2a16-109">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="e2a16-110">Het gebruikers station is een nieuwe PSDrive die uniek is voor elke gebruiker die verbinding maakt en die zich in verschillende sessies bevindt.</span><span class="sxs-lookup"><span data-stu-id="e2a16-110">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="e2a16-111">Als `Copy-Item` wordt gebruikt om bestanden te kopiëren naar of van een JEA-sessie, is deze beperkt tot alleen toegang tot het gebruikers station toestaan.</span><span class="sxs-lookup"><span data-stu-id="e2a16-111">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="e2a16-112">Pogingen om bestanden naar andere PSDrive te kopiëren, mislukken.</span><span class="sxs-lookup"><span data-stu-id="e2a16-112">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="e2a16-113">Als u het gebruikers station in het configuratie bestand van uw JEA-sessie wilt instellen, gebruikt u de volgende nieuwe velden:</span><span class="sxs-lookup"><span data-stu-id="e2a16-113">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="e2a16-114">De map die een back-up maakt van het gebruikers station wordt gemaakt op `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="e2a16-114">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="e2a16-115">Als u het gebruikers station wilt gebruiken en bestanden wilt kopiëren naar/van een JEA-eind punt dat is geconfigureerd om het gebruikers station zichtbaar te maken, gebruikt u de para meters `-ToSession` en `-FromSession` in `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="e2a16-115">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

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

<span data-ttu-id="e2a16-116">U kunt vervolgens aangepaste functies schrijven om de gegevens te verwerken die zijn opgeslagen in het gebruikers station en deze beschikbaar te maken voor gebruikers in uw functie-functionaliteits bestand.</span><span class="sxs-lookup"><span data-stu-id="e2a16-116">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="e2a16-117">Ondersteuning voor door groepen beheerde service accounts</span><span class="sxs-lookup"><span data-stu-id="e2a16-117">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="e2a16-118">In sommige gevallen moet een taak die een gebruiker moet uitvoeren in een JEA-sessie mogelijk toegang hebben tot bronnen buiten de lokale machine.</span><span class="sxs-lookup"><span data-stu-id="e2a16-118">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="e2a16-119">Wanneer een JEA-sessie is geconfigureerd voor het gebruik van een virtueel account, zal elke poging om dergelijke bronnen te bereiken, afkomstig zijn van de identiteit van de lokale computer, niet van het virtuele account of de verbonden gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e2a16-119">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="e2a16-120">In TP5 hebben we ondersteuning ingeschakeld voor het uitvoeren van JEA in de context van een door een [groep beheerd service account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), waardoor het veel eenvoudiger is om toegang te krijgen tot netwerk bronnen met behulp van een domein identiteit.</span><span class="sxs-lookup"><span data-stu-id="e2a16-120">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="e2a16-121">Als u een JEA-sessie wilt configureren om te worden uitgevoerd onder een gMSA-account, gebruikt u de volgende nieuwe sleutel in uw PSSC-bestand:</span><span class="sxs-lookup"><span data-stu-id="e2a16-121">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="e2a16-122">Door groepen beheerde service accounts bieden geen isolatie of beperkt bereik van virtuele accounts.</span><span class="sxs-lookup"><span data-stu-id="e2a16-122">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="e2a16-123">Elke gebruiker die verbinding maakt, deelt dezelfde gMSA-identiteit, die mogelijk machtigingen heeft voor uw hele onderneming.</span><span class="sxs-lookup"><span data-stu-id="e2a16-123">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="e2a16-124">Wees voorzichtig bij het selecteren van een gMSA en gebruik altijd de voor keur aan virtuele accounts die worden beperkt tot de lokale machine wanneer dat mogelijk is.</span><span class="sxs-lookup"><span data-stu-id="e2a16-124">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="e2a16-125">Beleid voor voorwaardelijke toegang</span><span class="sxs-lookup"><span data-stu-id="e2a16-125">Conditional access policies</span></span>

<span data-ttu-id="e2a16-126">JEA is handig om te beperken wat iemand kan doen wanneer ze zijn verbonden met een systeem om het te beheren, maar wat als u ook wilt beperken *Wanneer* iemand JEA kan gebruiken?</span><span class="sxs-lookup"><span data-stu-id="e2a16-126">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="e2a16-127">Er zijn configuratie opties toegevoegd aan de sessie configuratie bestanden (. pssc) waarmee u beveiligings groepen kunt opgeven waarvoor een gebruiker moet behoren om een JEA-sessie tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="e2a16-127">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="e2a16-128">Dit is met name handig als u een just-in-time-systeem (JIT) in uw omgeving hebt en u wilt dat uw gebruikers hun bevoegdheden kunnen verhogen voordat ze toegang krijgen tot een JEA-eind punt met hoge privileges.</span><span class="sxs-lookup"><span data-stu-id="e2a16-128">This is especially helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="e2a16-129">In het nieuwe veld *RequiredGroups* in het PSSC-bestand kunt u de logica opgeven om te bepalen of een gebruiker verbinding kan maken met jea.</span><span class="sxs-lookup"><span data-stu-id="e2a16-129">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="e2a16-130">Het bestaat uit het opgeven van een hashtabel (optioneel genest) die gebruikmaakt van de-en-of-sleutels om uw regels te maken.</span><span class="sxs-lookup"><span data-stu-id="e2a16-130">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="e2a16-131">Hier volgen enkele voor beelden van het gebruik van dit veld:</span><span class="sxs-lookup"><span data-stu-id="e2a16-131">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="e2a16-132">Opgelost: virtuele accounts worden nu ondersteund op Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="e2a16-132">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="e2a16-133">In WMF 5,1 kunt u nu virtuele accounts gebruiken op Windows Server 2008 R2, waardoor consistente configuraties en functie pariteit in Windows Server 2008 R2-2016 wordt ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e2a16-133">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="e2a16-134">Virtuele accounts blijven niet-ondersteund wanneer JEA wordt gebruikt in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="e2a16-134">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>