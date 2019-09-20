---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Bekende problemen in WMF 5.1
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145276"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="66847-103">Bekende problemen in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="66847-103">Known Issues in WMF 5.1</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="66847-104">Power shell-snelkoppeling starten als beheerder</span><span class="sxs-lookup"><span data-stu-id="66847-104">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="66847-105">Als u na de installatie van WMF probeert Power shell als Administrator te starten vanuit de snelkoppeling, wordt mogelijk het bericht ' niet nader omschreven fout ' weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="66847-105">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span> <span data-ttu-id="66847-106">Open de snelkoppeling opnieuw als niet-beheerder. de snelkoppeling werkt nu ook als beheerder.</span><span class="sxs-lookup"><span data-stu-id="66847-106">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="66847-107">Pester</span><span class="sxs-lookup"><span data-stu-id="66847-107">Pester</span></span>

<span data-ttu-id="66847-108">In deze release zijn er twee problemen waarvan u rekening moet houden bij het gebruik van een ziekte met behulp van een plaag op nano server:</span><span class="sxs-lookup"><span data-stu-id="66847-108">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="66847-109">Het uitvoeren van tests tegen een aanval zelf kan leiden tot enkele fouten vanwege verschillen tussen de volledige CLR en CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="66847-109">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="66847-110">Met name de methode **Validate** is niet beschikbaar voor het type **XMLDocument** .</span><span class="sxs-lookup"><span data-stu-id="66847-110">In particular, the **Validate** method is not available on the **XmlDocument** type.</span></span> <span data-ttu-id="66847-111">Zes tests die proberen het schema van de NUnit-uitvoer logboeken te valideren, zijn bekend als mislukken.</span><span class="sxs-lookup"><span data-stu-id="66847-111">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="66847-112">**Het testen** van de code dekking mislukt, omdat de resource voor de DSC-opdracht bestaat niet in nano server.</span><span class="sxs-lookup"><span data-stu-id="66847-112">One code coverage test fails because the **WindowsFeature** DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="66847-113">Deze fouten zijn echter in het algemeen goed aardig en kunnen veilig worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="66847-113">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="66847-114">Bewerkings validatie</span><span class="sxs-lookup"><span data-stu-id="66847-114">Operation Validation</span></span>

- <span data-ttu-id="66847-115">`Update-Help`mislukt voor de module micro soft. Power shell. Operation. validatie vanwege een niet-werkende Help-URI</span><span class="sxs-lookup"><span data-stu-id="66847-115">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="66847-116">DSC na verwijderen van WMF</span><span class="sxs-lookup"><span data-stu-id="66847-116">DSC after uninstall WMF</span></span>

- <span data-ttu-id="66847-117">Als u WMF verwijdert, worden de DSC-MOF-documenten uit de configuratiemap niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="66847-117">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="66847-118">DSC werkt niet goed als de MOF-documenten nieuwere eigenschappen bevatten die niet beschikbaar zijn op de oudere systemen.</span><span class="sxs-lookup"><span data-stu-id="66847-118">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="66847-119">In dit geval voert u het volgende script uit vanuit de Power shell-console met verhoogde bevoegdheid om de DSC-statussen op te schonen.</span><span class="sxs-lookup"><span data-stu-id="66847-119">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="66847-120">Virtuele JEA-accounts</span><span class="sxs-lookup"><span data-stu-id="66847-120">JEA Virtual Accounts</span></span>

<span data-ttu-id="66847-121">JEA-eind punten en-sessie configuraties die zijn geconfigureerd voor het gebruik van virtuele accounts in WMF 5,0, worden niet geconfigureerd voor het gebruik van een virtueel account na een upgrade naar WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="66847-121">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span> <span data-ttu-id="66847-122">Dit betekent dat de opdrachten die worden uitgevoerd in JEA-sessies worden uitgevoerd onder de identiteit van de gebruiker in plaats van een tijdelijk beheerders account, waardoor de gebruiker geen opdrachten kan uitvoeren waarvoor verhoogde bevoegdheden zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="66847-122">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span> <span data-ttu-id="66847-123">Als u de virtuele accounts wilt herstellen, moet u de registratie ongedaan maken en alle sessie configuraties die gebruikmaken van virtuele accounts, opnieuw registreren.</span><span class="sxs-lookup"><span data-stu-id="66847-123">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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