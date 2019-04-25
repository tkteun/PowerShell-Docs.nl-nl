---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Bekende problemen in WMF 5.1
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084960"
---
# <a name="known-issues-in-wmf-51"></a>Bekende problemen in WMF 5.1

> [!Note]
> Deze informatie kan worden gewijzigd.

## <a name="starting-powershell-shortcut-as-administrator"></a>PowerShell-snelkoppeling starten als beheerder

Bij de installatie van WMF, als u probeert te start PowerShell als beheerder van de snelkoppeling, krijgt u mogelijk een bericht 'Onbekende fout'.
Opent u de snelkoppeling als niet-beheerder en de snelkoppeling werkt nu ook als administrator.

## <a name="pester"></a>Pester

In deze release zijn er twee problemen die u houden moet rekening bij het gebruik van Pester op Nano Server:

- Met het uitvoeren van tests in Pester zelf kan resulteren in fouten opgetreden vanwege verschillen tussen volledige CLR en CORE CLR. In het bijzonder is de methode valideren niet beschikbaar op het type XmlDocument. Zes tests die probeert te valideren van het schema van de logboeken van de uitvoer NUnit bekend is mislukt.
- Een Code-dekking test op dit moment is mislukt omdat de *WindowsFeature* DSC-Resource bestaat niet in Nano Server. Deze fouten zijn echter in het algemeen goedaardige en kunnen veilig worden genegeerd.

## <a name="operation-validation"></a>Bewerking valideren

- `Update-Help` voor de module Microsoft.PowerShell.Operation.Validation vanwege niet-werkende help-URI is mislukt

## <a name="dsc-after-uninstall-wmf"></a>DSC nadat WMF verwijderen

- WMF verwijderen, worden DSC MOF documenten niet verwijderd uit de configuratiemap. DSC goed niet als de MOF-documenten bevatten nieuwere-eigenschappen die niet beschikbaar op de oudere systemen zijn. Voer het volgende script in dit geval van PowerShell-console met verhoogde bevoegdheid voor het opschonen van de DSC-statussen.

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>JEA virtuele Accounts

JEA-eindpunten en sessieconfiguraties geconfigureerd voor het gebruik van virtuele accounts in WMF 5.0 wordt niet geconfigureerd voor het gebruik van een virtueel account na de upgrade naar WMF 5.1.
Dit betekent dat opdrachten worden uitgevoerd in JEA-sessies worden uitgevoerd onder de identiteit van de gebruiker van de verbinding maakt in plaats van een tijdelijke administrator-account, mogelijk zo wordt voorkomen dat de gebruiker uitvoeren van opdrachten waarvoor verhoogde bevoegdheden.
Als u de virtuele accounts herstellen, moet u de registratie ongedaan maken en alle sessieconfiguraties die gebruikmaken van virtuele accounts opnieuw te registreren.

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