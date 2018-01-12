# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="e2099-101">WS-Management (WSMan) voor externe toegang in PowerShell-kern</span><span class="sxs-lookup"><span data-stu-id="e2099-101">WS-Management (WSMan) Remoting in PowerShell Core</span></span> 

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="e2099-102">Instructies voor het maken van een eindpunt voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="e2099-102">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="e2099-103">Het PowerShell-kern-pakket voor Windows bevat een WinRM-invoegtoepassing (`pwrshplugin.dll`) en een script voor installatie (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="e2099-103">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="e2099-104">Deze bestanden inschakelen PowerShell te accepteren van binnenkomende PowerShell externe verbindingen wanneer het eindpunt is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e2099-104">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="e2099-105">Doel</span><span class="sxs-lookup"><span data-stu-id="e2099-105">Motivation</span></span>

<span data-ttu-id="e2099-106">Een installatie van PowerShell kan verbinding maken met PowerShell-sessies met externe computers met behulp van `New-PSSession` en `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="e2099-106">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="e2099-107">De gebruiker moet een WinRM-eindpunt voor externe toegang maken zodat het accepteren van binnenkomende PowerShell externe verbindingen.</span><span class="sxs-lookup"><span data-stu-id="e2099-107">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="e2099-108">Dit is een expliciete opt-in-scenario waarin de gebruiker wordt uitgevoerd met Install-PowerShellRemoting.ps1 om de WinRM-eindpunt te maken.</span><span class="sxs-lookup"><span data-stu-id="e2099-108">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="e2099-109">Het script voor installatie is een oplossing op korte termijn totdat we toevoegen van aanvullende functionaliteit voor `Enable-PSRemoting` de dezelfde actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e2099-109">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="e2099-110">Zie voor meer informatie probleem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="e2099-110">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="e2099-111">Scriptacties</span><span class="sxs-lookup"><span data-stu-id="e2099-111">Script Actions</span></span>

<span data-ttu-id="e2099-112">Het script</span><span class="sxs-lookup"><span data-stu-id="e2099-112">The script</span></span>

1. <span data-ttu-id="e2099-113">Hiermee maakt u een map voor de invoegtoepassing binnen %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2099-113">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="e2099-114">Pwrshplugin.dll naar die locatie opgehaald</span><span class="sxs-lookup"><span data-stu-id="e2099-114">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="e2099-115">Genereert een configuratiebestand</span><span class="sxs-lookup"><span data-stu-id="e2099-115">Generates a configuration file</span></span>
1. <span data-ttu-id="e2099-116">Registers dat invoegtoepassing met WinRM</span><span class="sxs-lookup"><span data-stu-id="e2099-116">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="e2099-117">Registratie</span><span class="sxs-lookup"><span data-stu-id="e2099-117">Registration</span></span>

<span data-ttu-id="e2099-118">Het script moet worden uitgevoerd binnen een beheerdersniveau PowerShell-sessie en wordt uitgevoerd in twee modi.</span><span class="sxs-lookup"><span data-stu-id="e2099-118">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="e2099-119">Uitgevoerd door het exemplaar van PowerShell die wordt geregistreerd</span><span class="sxs-lookup"><span data-stu-id="e2099-119">Executed by the instance of PowerShell that it will register</span></span>

``` powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="e2099-120">Uitgevoerd door een ander exemplaar van PowerShell namens het exemplaar dat wordt geregistreerd</span><span class="sxs-lookup"><span data-stu-id="e2099-120">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

``` powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>" -PowerShellVersion "<the powershell version tag>"
```

<span data-ttu-id="e2099-121">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e2099-121">For Example:</span></span>

``` powershell
C:\Program Files\PowerShell\6.0.0.9\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0.9\" -PowerShellVersion "6.0.0-alpha.9"
```

<span data-ttu-id="e2099-122">**Opmerking:** wordt het script voor de registratie voor externe toegang opnieuw starten van WinRM, zodat alle bestaande PSRP-sessies wordt beëindigd onmiddellijk nadat het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e2099-122">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="e2099-123">Als tijdens een externe sessie worden uitgevoerd, wordt deze de verbinding verbreken.</span><span class="sxs-lookup"><span data-stu-id="e2099-123">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="e2099-124">Verbinding maken met het nieuwe eindpunt</span><span class="sxs-lookup"><span data-stu-id="e2099-124">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="e2099-125">Een PowerShell-sessie met het nieuwe PowerShell-eindpunt maken door te geven `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="e2099-125">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="e2099-126">Maak verbinding met de PowerShell-exemplaar van het bovenstaande voorbeeld door een te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="e2099-126">To connect to the PowerShell instance from the example above, use either:</span></span>

``` powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0-alpha.9"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0-alpha.9"
```

<span data-ttu-id="e2099-127">Houd er rekening mee dat `New-PSSession` en `Enter-PSSession` aanroepen die geen opgeeft `-ConfigurationName` heeft betrekking op het standaardeindpunt PowerShell `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="e2099-127">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>
