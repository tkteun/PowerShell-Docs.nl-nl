---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Bekende problemen in WMF 5.1
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856362"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="b87f9-103">Bekende problemen in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="b87f9-103">Known Issues in WMF 5.1</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="b87f9-104">PowerShell-snelkoppeling starten als beheerder</span><span class="sxs-lookup"><span data-stu-id="b87f9-104">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="b87f9-105">Bij de installatie van WMF, als u probeert te start PowerShell als beheerder van de snelkoppeling, krijgt u mogelijk een bericht 'Onbekende fout'.</span><span class="sxs-lookup"><span data-stu-id="b87f9-105">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span> <span data-ttu-id="b87f9-106">Opent u de snelkoppeling als niet-beheerder en de snelkoppeling werkt nu ook als administrator.</span><span class="sxs-lookup"><span data-stu-id="b87f9-106">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="b87f9-107">Pester</span><span class="sxs-lookup"><span data-stu-id="b87f9-107">Pester</span></span>

<span data-ttu-id="b87f9-108">In deze release zijn er twee problemen die u houden moet rekening bij het gebruik van Pester op Nano Server:</span><span class="sxs-lookup"><span data-stu-id="b87f9-108">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="b87f9-109">Met het uitvoeren van tests in Pester zelf kan resulteren in fouten opgetreden vanwege verschillen tussen volledige CLR en CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="b87f9-109">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="b87f9-110">In het bijzonder de **valideren** methode is niet beschikbaar op de **XmlDocument** type.</span><span class="sxs-lookup"><span data-stu-id="b87f9-110">In particular, the **Validate** method is not available on the **XmlDocument** type.</span></span> <span data-ttu-id="b87f9-111">Zes tests die probeert te valideren van het schema van de logboeken van de uitvoer NUnit bekend is mislukt.</span><span class="sxs-lookup"><span data-stu-id="b87f9-111">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="b87f9-112">Een code dekking test mislukt, omdat de **WindowsFeature** DSC-Resource bestaat niet in Nano Server.</span><span class="sxs-lookup"><span data-stu-id="b87f9-112">One code coverage test fails because the **WindowsFeature** DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="b87f9-113">Deze fouten zijn echter in het algemeen goedaardige en kunnen veilig worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="b87f9-113">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="b87f9-114">Bewerking valideren</span><span class="sxs-lookup"><span data-stu-id="b87f9-114">Operation Validation</span></span>

- <span data-ttu-id="b87f9-115">`Update-Help` voor de module Microsoft.PowerShell.Operation.Validation vanwege niet-werkende help-URI is mislukt</span><span class="sxs-lookup"><span data-stu-id="b87f9-115">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="b87f9-116">DSC nadat WMF verwijderen</span><span class="sxs-lookup"><span data-stu-id="b87f9-116">DSC after uninstall WMF</span></span>

- <span data-ttu-id="b87f9-117">WMF verwijderen, worden DSC MOF documenten niet verwijderd uit de configuratiemap.</span><span class="sxs-lookup"><span data-stu-id="b87f9-117">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="b87f9-118">DSC goed niet als de MOF-documenten bevatten nieuwere-eigenschappen die niet beschikbaar op de oudere systemen zijn.</span><span class="sxs-lookup"><span data-stu-id="b87f9-118">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="b87f9-119">Voer het volgende script in dit geval van PowerShell-console met verhoogde bevoegdheid voor het opschonen van de DSC-statussen.</span><span class="sxs-lookup"><span data-stu-id="b87f9-119">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="b87f9-120">JEA virtuele Accounts</span><span class="sxs-lookup"><span data-stu-id="b87f9-120">JEA Virtual Accounts</span></span>

<span data-ttu-id="b87f9-121">JEA-eindpunten en sessieconfiguraties geconfigureerd voor het gebruik van virtuele accounts in WMF 5.0 wordt niet geconfigureerd voor het gebruik van een virtueel account na de upgrade naar WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="b87f9-121">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span> <span data-ttu-id="b87f9-122">Dit betekent dat opdrachten worden uitgevoerd in JEA-sessies worden uitgevoerd onder de identiteit van de gebruiker van de verbinding maakt in plaats van een tijdelijke administrator-account, mogelijk zo wordt voorkomen dat de gebruiker uitvoeren van opdrachten waarvoor verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="b87f9-122">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span> <span data-ttu-id="b87f9-123">Als u de virtuele accounts herstellen, moet u de registratie ongedaan maken en alle sessieconfiguraties die gebruikmaken van virtuele accounts opnieuw te registreren.</span><span class="sxs-lookup"><span data-stu-id="b87f9-123">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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