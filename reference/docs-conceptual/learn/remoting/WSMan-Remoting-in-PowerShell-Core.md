---
title: Externe communicatie van WS-Management (WSMan) in PowerShell Core
description: Externe communicatie in Power shell core met behulp van WSMan
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "62058876"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="5a49a-103">Externe communicatie van WS-Management (WSMan) in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5a49a-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="5a49a-104">Instructies voor het maken van een extern eind punt</span><span class="sxs-lookup"><span data-stu-id="5a49a-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="5a49a-105">Het Power shell core-pakket voor Windows bevat een WinRM-invoeg`pwrshplugin.dll`toepassing () en een installatie`Install-PowerShellRemoting.ps1`script ( `$PSHome`) in.</span><span class="sxs-lookup"><span data-stu-id="5a49a-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="5a49a-106">Met deze bestanden kunnen Power shell binnenkomende Power shell-externe verbindingen accepteren wanneer het eind punt is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5a49a-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="5a49a-107">Motivatie</span><span class="sxs-lookup"><span data-stu-id="5a49a-107">Motivation</span></span>

<span data-ttu-id="5a49a-108">Een installatie van Power shell kan Power shell-sessies tot stand `New-PSSession` brengen `Enter-PSSession`met externe computers met behulp van en.</span><span class="sxs-lookup"><span data-stu-id="5a49a-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="5a49a-109">Voor het accepteren van binnenkomende Power shell-externe verbindingen, moet de gebruiker een extern eind punt voor WinRM maken.</span><span class="sxs-lookup"><span data-stu-id="5a49a-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="5a49a-110">Dit is een expliciet opt-in-scenario waarbij de gebruiker Install-PowerShellRemoting. ps1 uitvoert om het WinRM-eind punt te maken.</span><span class="sxs-lookup"><span data-stu-id="5a49a-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="5a49a-111">Het installatie script is een oplossing voor de korte termijn totdat we extra functionaliteit toevoegen `Enable-PSRemoting` om dezelfde actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5a49a-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="5a49a-112">Zie issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a49a-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="5a49a-113">Script acties</span><span class="sxs-lookup"><span data-stu-id="5a49a-113">Script Actions</span></span>

<span data-ttu-id="5a49a-114">Het script</span><span class="sxs-lookup"><span data-stu-id="5a49a-114">The script</span></span>

1. <span data-ttu-id="5a49a-115">Hiermee maakt u een map voor de invoeg toepassing in`$env:windir\System32\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="5a49a-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="5a49a-116">Kopieert pwrshplugin. dll naar die locatie</span><span class="sxs-lookup"><span data-stu-id="5a49a-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="5a49a-117">Hiermee genereert u een configuratie bestand</span><span class="sxs-lookup"><span data-stu-id="5a49a-117">Generates a configuration file</span></span>
1. <span data-ttu-id="5a49a-118">Registreert deze invoeg toepassing met WinRM</span><span class="sxs-lookup"><span data-stu-id="5a49a-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="5a49a-119">Registratie</span><span class="sxs-lookup"><span data-stu-id="5a49a-119">Registration</span></span>

<span data-ttu-id="5a49a-120">Het script moet worden uitgevoerd binnen een Power shell-sessie op beheerders niveau en kan in twee modi worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5a49a-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="5a49a-121">Uitgevoerd door het instantie van Power shell dat wordt geregistreerd</span><span class="sxs-lookup"><span data-stu-id="5a49a-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="5a49a-122">Uitgevoerd door een ander exemplaar van Power shell namens het exemplaar dat wordt geregistreerd</span><span class="sxs-lookup"><span data-stu-id="5a49a-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="5a49a-123">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5a49a-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="5a49a-124">**Opmerking:** Het externe registratie script zal WinRM opnieuw opstarten, zodat alle bestaande PSRP-sessies onmiddellijk worden beëindigd nadat het script is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5a49a-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="5a49a-125">Als deze wordt uitgevoerd tijdens een externe sessie, wordt de verbinding verbroken.</span><span class="sxs-lookup"><span data-stu-id="5a49a-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="5a49a-126">Verbinding maken met het nieuwe eind punt</span><span class="sxs-lookup"><span data-stu-id="5a49a-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="5a49a-127">Maak een Power shell-sessie met het nieuwe Power shell `-ConfigurationName "some endpoint name"`-eind punt door op te geven.</span><span class="sxs-lookup"><span data-stu-id="5a49a-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="5a49a-128">Als u vanuit bovenstaand voor beeld verbinding wilt maken met het Power shell-exemplaar, gebruikt u een van de volgende opties:</span><span class="sxs-lookup"><span data-stu-id="5a49a-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="5a49a-129">Houd er `New-PSSession` rekening `Enter-PSSession` mee dat en aanroepen die niet `-ConfigurationName` worden opgegeven, het standaard-Power `microsoft.powershell`shell-eind punt zijn.</span><span class="sxs-lookup"><span data-stu-id="5a49a-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>