---
title: Externe communicatie van WS-Management (WSMan) in PowerShell Core
description: Externe communicatie in PowerShell Core met behulp van WSMan
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404610"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="b3223-103">Externe communicatie van WS-Management (WSMan) in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b3223-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="b3223-104">Instructies voor het maken van een eindpunt voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="b3223-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="b3223-105">De PowerShell Core-pakket voor Windows bevat een WinRM-invoegtoepassing (`pwrshplugin.dll`) en een script voor installatie (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="b3223-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="b3223-106">Deze bestanden inschakelen PowerShell om te accepteren van binnenkomende PowerShell externe verbindingen wanneer het eindpunt is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b3223-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="b3223-107">Motivatie</span><span class="sxs-lookup"><span data-stu-id="b3223-107">Motivation</span></span>

<span data-ttu-id="b3223-108">Een installatie van PowerShell kan tot stand brengen met externe computers met behulp van PowerShell-sessies `New-PSSession` en `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="b3223-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="b3223-109">Als u wilt inschakelen om binnenkomende PowerShell externe verbindingen te accepteren, moet de gebruiker een WinRM voor externe toegang-eindpunt maken.</span><span class="sxs-lookup"><span data-stu-id="b3223-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="b3223-110">Dit is een expliciete opt-in-scenario waarin de gebruiker wordt uitgevoerd met Install-PowerShellRemoting.ps1 om de WinRM-eindpunt te maken.</span><span class="sxs-lookup"><span data-stu-id="b3223-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="b3223-111">Het script voor installatie is een oplossing op korte termijn vooralsnog kunt aanvullende functionaliteit voor `Enable-PSRemoting` de dezelfde actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b3223-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="b3223-112">Zie voor meer informatie, probleem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="b3223-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="b3223-113">Scriptacties</span><span class="sxs-lookup"><span data-stu-id="b3223-113">Script Actions</span></span>

<span data-ttu-id="b3223-114">Het script</span><span class="sxs-lookup"><span data-stu-id="b3223-114">The script</span></span>

1. <span data-ttu-id="b3223-115">Hiermee maakt u een map voor de invoegtoepassing binnen %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3223-115">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="b3223-116">Pwrshplugin.dll aan die locatie opgehaald</span><span class="sxs-lookup"><span data-stu-id="b3223-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="b3223-117">Genereert een configuratiebestand</span><span class="sxs-lookup"><span data-stu-id="b3223-117">Generates a configuration file</span></span>
1. <span data-ttu-id="b3223-118">Registers die invoegtoepassing met WinRM</span><span class="sxs-lookup"><span data-stu-id="b3223-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="b3223-119">Registratie</span><span class="sxs-lookup"><span data-stu-id="b3223-119">Registration</span></span>

<span data-ttu-id="b3223-120">Het script moet worden uitgevoerd binnen een beheerder op serverniveau PowerShell-sessie en wordt uitgevoerd in twee modi.</span><span class="sxs-lookup"><span data-stu-id="b3223-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="b3223-121">Uitgevoerd door het exemplaar van PowerShell die geregistreerd</span><span class="sxs-lookup"><span data-stu-id="b3223-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="b3223-122">Uitgevoerd door een ander exemplaar van PowerShell namens het exemplaar dat wordt geregistreerd</span><span class="sxs-lookup"><span data-stu-id="b3223-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="b3223-123">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b3223-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="b3223-124">**OPMERKING:** Het script voor de registratie voor externe toegang wordt opnieuw opgestart van WinRM, zodat alle bestaande PSRP-sessies wordt beëindigd zodra het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b3223-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="b3223-125">Als tijdens een sessie op afstand uitvoert, wordt deze beëindigd als de verbinding.</span><span class="sxs-lookup"><span data-stu-id="b3223-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="b3223-126">Verbinding maken met het nieuwe eindpunt</span><span class="sxs-lookup"><span data-stu-id="b3223-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="b3223-127">Een PowerShell-sessie naar de nieuwe PowerShell-eindpunt maken door op te geven `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="b3223-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="b3223-128">Voor verbinding met de PowerShell-sessie uit het bovenstaande voorbeeld, een te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="b3223-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="b3223-129">Houd er rekening mee dat `New-PSSession` en `Enter-PSSession` aanroepen die niet opgeeft `-ConfigurationName` heeft betrekking op het standaardeindpunt PowerShell `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="b3223-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>