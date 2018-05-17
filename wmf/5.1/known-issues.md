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
# <a name="known-issues-in-wmf-51"></a>Bekende problemen in WMF 5.1 #

> Opmerking: Deze informatie kan worden gewijzigd.

## <a name="starting-powershell-shortcut-as-administrator"></a>Snelkoppeling PowerShell als beheerder vanaf
Bij het installeren van WMF als u probeert te start PowerShell als beheerder van de snelkoppeling mogelijk dat u een bericht 'Onbekende fout'.
Open de snelkoppeling als niet-beheerders en de snelkoppeling werkt nu zelfs als administrator.

## <a name="pester"></a>Lastige
In deze release zijn er twee problemen die u houden moet rekening wanneer u Pester op Nano Server:

* Tests uitgevoerd tegen Pester zelf kan vanwege verschillen tussen volledige CLR en CORE CLR leiden tot een aantal fouten. In het bijzonder is de methode Validate niet beschikbaar op het type XmlDocument. Zes tests die proberen te valideren van het schema van de logboeken van de uitvoer NUnit bekend is mislukt.
* Een Code dekking test momenteel mislukt, omdat de *WindowsFeature* DSC-Resource bestaat niet in de Nano Server. Deze fouten worden echter in het algemeen onschadelijk zijn en kunnen worden genegeerd.

## <a name="operation-validation"></a>Bewerking valideren

* Help bijwerken is mislukt voor module Microsoft.PowerShell.Operation.Validation vanwege niet-werkende help-URI

## <a name="dsc-after-uninstall-wmf"></a>DSC nadat WMF verwijderen
* Verwijderen van WMF verwijdert niet DSC MOF documenten uit de configuratiemap. DSC werkt niet correct als de MOF-documenten bevatten nieuwere eigenschappen die niet beschikbaar op de oudere systemen. Voer het volgende script in dit geval van PowerShell-console met verhoogde bevoegdheid voor opschonen van de DSC-statussen.
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a>JEA virtuele Accounts
JEA eindpunten en sessieconfiguraties geconfigureerd voor het gebruik van virtuele accounts in WMF 5.0 niet geconfigureerd voor gebruik van een virtueel account na de upgrade naar WMF 5.1.
Dit betekent dat de opdrachten uitvoert in JEA-sessies wordt uitgevoerd onder de identiteit van de gebruiker verbinding maakt in plaats van een tijdelijke administrator-account mogelijk zo wordt voorkomen dat de gebruiker met opdrachten waarvoor verhoogde bevoegdheden vereist.
Voor het herstellen van de virtuele accounts, moet u de registratie ongedaan maken en alle sessieconfiguraties die gebruikmaken van virtuele accounts opnieuw te registreren.

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
