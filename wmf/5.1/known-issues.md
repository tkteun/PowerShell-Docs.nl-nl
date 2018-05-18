---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Bekende problemen in WMF 5.1
ms.openlocfilehash: d53031bea978087c68fcb22989c7cd2e2cf2d9fa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="90ae9-103">Bekende problemen in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="90ae9-103">Known Issues in WMF 5.1</span></span> #

> <span data-ttu-id="90ae9-104">Opmerking: Deze informatie kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="90ae9-104">Note: This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="90ae9-105">Snelkoppeling PowerShell als beheerder vanaf</span><span class="sxs-lookup"><span data-stu-id="90ae9-105">Starting PowerShell shortcut as Administrator</span></span>
<span data-ttu-id="90ae9-106">Bij het installeren van WMF als u probeert te start PowerShell als beheerder van de snelkoppeling mogelijk dat u een bericht 'Onbekende fout'.</span><span class="sxs-lookup"><span data-stu-id="90ae9-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="90ae9-107">Open de snelkoppeling als niet-beheerders en de snelkoppeling werkt nu zelfs als administrator.</span><span class="sxs-lookup"><span data-stu-id="90ae9-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="90ae9-108">Lastige</span><span class="sxs-lookup"><span data-stu-id="90ae9-108">Pester</span></span>
<span data-ttu-id="90ae9-109">In deze release zijn er twee problemen die u houden moet rekening wanneer u Pester op Nano Server:</span><span class="sxs-lookup"><span data-stu-id="90ae9-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

* <span data-ttu-id="90ae9-110">Tests uitgevoerd tegen Pester zelf kan vanwege verschillen tussen volledige CLR en CORE CLR leiden tot een aantal fouten.</span><span class="sxs-lookup"><span data-stu-id="90ae9-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="90ae9-111">In het bijzonder is de methode Validate niet beschikbaar op het type XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="90ae9-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="90ae9-112">Zes tests die proberen te valideren van het schema van de logboeken van de uitvoer NUnit bekend is mislukt.</span><span class="sxs-lookup"><span data-stu-id="90ae9-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
* <span data-ttu-id="90ae9-113">Een Code dekking test momenteel mislukt, omdat de *WindowsFeature* DSC-Resource bestaat niet in de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="90ae9-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="90ae9-114">Deze fouten worden echter in het algemeen onschadelijk zijn en kunnen worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="90ae9-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="90ae9-115">Bewerking valideren</span><span class="sxs-lookup"><span data-stu-id="90ae9-115">Operation Validation</span></span>

* <span data-ttu-id="90ae9-116">Help bijwerken is mislukt voor module Microsoft.PowerShell.Operation.Validation vanwege niet-werkende help-URI</span><span class="sxs-lookup"><span data-stu-id="90ae9-116">Update-Help fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="90ae9-117">DSC nadat WMF verwijderen</span><span class="sxs-lookup"><span data-stu-id="90ae9-117">DSC after uninstall WMF</span></span>
* <span data-ttu-id="90ae9-118">Verwijderen van WMF verwijdert niet DSC MOF documenten uit de configuratiemap.</span><span class="sxs-lookup"><span data-stu-id="90ae9-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="90ae9-119">DSC werkt niet correct als de MOF-documenten bevatten nieuwere eigenschappen die niet beschikbaar op de oudere systemen.</span><span class="sxs-lookup"><span data-stu-id="90ae9-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="90ae9-120">Voer het volgende script in dit geval van PowerShell-console met verhoogde bevoegdheid voor opschonen van de DSC-statussen.</span><span class="sxs-lookup"><span data-stu-id="90ae9-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="90ae9-121">JEA virtuele Accounts</span><span class="sxs-lookup"><span data-stu-id="90ae9-121">JEA Virtual Accounts</span></span>
<span data-ttu-id="90ae9-122">JEA eindpunten en sessieconfiguraties geconfigureerd voor het gebruik van virtuele accounts in WMF 5.0 niet geconfigureerd voor gebruik van een virtueel account na de upgrade naar WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="90ae9-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="90ae9-123">Dit betekent dat de opdrachten uitvoert in JEA-sessies wordt uitgevoerd onder de identiteit van de gebruiker verbinding maakt in plaats van een tijdelijke administrator-account mogelijk zo wordt voorkomen dat de gebruiker met opdrachten waarvoor verhoogde bevoegdheden vereist.</span><span class="sxs-lookup"><span data-stu-id="90ae9-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="90ae9-124">Voor het herstellen van de virtuele accounts, moet u de registratie ongedaan maken en alle sessieconfiguraties die gebruikmaken van virtuele accounts opnieuw te registreren.</span><span class="sxs-lookup"><span data-stu-id="90ae9-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```
