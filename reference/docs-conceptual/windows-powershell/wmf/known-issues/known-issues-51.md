---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Bekende problemen in WMF 5.1
ms.openlocfilehash: 4f4c85e1f4984d9e91ea74ba65fdbf7188c5c7ab
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810209"
---
# <a name="known-issues-in-wmf-51"></a>Bekende problemen in WMF 5.1

## <a name="starting-powershell-shortcut-as-administrator"></a>Power shell-snelkoppeling starten als beheerder

Als u na de installatie van WMF probeert Power shell als Administrator te starten vanuit de snelkoppeling, wordt mogelijk het bericht ' niet nader omschreven fout ' weer gegeven. Open de snelkoppeling opnieuw als niet-beheerder. de snelkoppeling werkt nu ook als beheerder.

## <a name="pester"></a>Pester

In deze release zijn er twee problemen waarvan u rekening moet houden bij het gebruik van een ziekte met behulp van een plaag op nano server:

- Het uitvoeren van tests tegen een aanval zelf kan leiden tot enkele fouten vanwege verschillen tussen de volledige CLR en CORE CLR. Met name de methode **Validate** is niet beschikbaar voor het type **XMLDocument** . Zes tests die proberen het schema van de NUnit-uitvoer logboeken te valideren, zijn bekend als mislukken.
- **Het testen** van de code dekking mislukt, omdat de resource voor de DSC-opdracht bestaat niet in nano server. Deze fouten zijn echter in het algemeen goed aardig en kunnen veilig worden genegeerd.

## <a name="operation-validation"></a>Bewerkings validatie

- `Update-Help`mislukt voor de module micro soft. Power shell. Operation. validatie vanwege een niet-werkende Help-URI

## <a name="dsc-after-uninstall-wmf"></a>DSC na verwijderen van WMF

- Als u WMF verwijdert, worden de DSC-MOF-documenten uit de configuratiemap niet verwijderd. DSC werkt niet goed als de MOF-documenten nieuwere eigenschappen bevatten die niet beschikbaar zijn op de oudere systemen. In dit geval voert u het volgende script uit vanuit de Power shell-console met verhoogde bevoegdheid om de DSC-statussen op te schonen.

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>Virtuele JEA-accounts

JEA-eind punten en-sessie configuraties die zijn geconfigureerd voor het gebruik van virtuele accounts in WMF 5,0, worden niet geconfigureerd voor het gebruik van een virtueel account na een upgrade naar WMF 5,1. Dit betekent dat de opdrachten die worden uitgevoerd in JEA-sessies worden uitgevoerd onder de identiteit van de gebruiker in plaats van een tijdelijk beheerders account, waardoor de gebruiker geen opdrachten kan uitvoeren waarvoor verhoogde bevoegdheden zijn vereist. Als u de virtuele accounts wilt herstellen, moet u de registratie ongedaan maken en alle sessie configuraties die gebruikmaken van virtuele accounts, opnieuw registreren.

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
