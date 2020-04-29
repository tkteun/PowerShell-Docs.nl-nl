---
ms.date: 08/15/2019
keywords: DSC, Power shell, configuratie, installatie
title: Aan de slag met de desired state Configuration (DSC) voor Windows
ms.openlocfilehash: 2add2c936e60c0c9446bf4b398fbf7b4bd6407f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75416168"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Aan de slag met de desired state Configuration (DSC) voor Windows

In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Windows.
Zie [aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)(Engelstalig) voor algemene informatie over DSC.

## <a name="supported-windows-operation-system-versions"></a>Ondersteunde versies van Windows-besturings systeem

De volgende versies worden ondersteund:

- Windows Server 2019
- Windows Server 2016
- Windows Server-2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

De zelfstandige product-SKU van [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) bevat geen implementatie van de desired state configuratie zodat deze niet kan worden beheerd door Power shell DSC of Azure Automation status configuratie.

## <a name="installing-dsc"></a>DSC installeren

De gewenste status configuratie van Power shell is opgenomen in Windows en bijgewerkt via Windows Management Framework. De nieuwste versie is [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

> [!NOTE]
> U hoeft de Windows Server-functie DSC-service niet in te scha kelen om een machine te beheren met behulp van DSC.
> Deze functie is alleen nodig bij het bouwen van een Windows pull-Server exemplaar.

## <a name="using-dsc-for-windows"></a>DSC voor Windows gebruiken

In de volgende secties wordt uitgelegd hoe u DSC-configuraties maakt en uitvoert op Windows-computers.

### <a name="creating-a-configuration-mof-document"></a>Een configuratie-MOF-document maken

Het sleutel woord `Configuration` Windows Power shell wordt gebruikt om een configuratie te maken.
De volgende stappen beschrijven het maken van een configuratie document met behulp van Windows Power shell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Definieer een configuratie en Genereer het configuratie document:

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a>Een module met DSC-resources installeren

Windows Power shell desired state Configuration bevat ingebouwde modules met DSC-resources.
U kunt ook modules laden vanuit externe bronnen, zoals de PowerShell Gallery, met behulp van de PowerShellGet-cmdlets.

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a>De configuratie Toep assen op de computer

> [!NOTE]
> Om DSC te kunnen uitvoeren, moet Windows worden geconfigureerd om externe Power shell-opdrachten te ontvangen, zelfs wanneer u `localhost` een configuratie uitvoert. Als u uw omgeving eenvoudig op de juiste wijze `Set-WsManQuickConfig -Force` wilt configureren, voert u de opdracht uit in een Power shell-terminal met verhoogde bevoegdheden.

Configuratie documenten (MOF-bestanden) kunnen worden toegepast op de machineusing van de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a>De huidige status van de configuratie ophalen

De cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) voert een query uit op de huidige status van de machine en retourneert de huidige waarden voor de configuratie.

```powershell
Get-DscConfiguration
```

De cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) retourneert de huidige meta-configuratie die is toegepast op de computer.

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a>De huidige configuratie van een machine verwijderen

De [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a>Instellingen in lokale Configuration Manager configureren

Pas een MOF-bestand met de meta configuratie toe met de cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .
Vereist het pad naar de meta configuratie-MOF.

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Windows Power shell desired state Configuration-logboek bestanden

Logboeken voor DSC worden in het pad `Microsoft-Windows-Dsc/Operational`naar het Windows-gebeurtenis logboek geschreven.
Aanvullende logboeken voor fout opsporing kunnen worden ingeschakeld Volg de stappen in [waar vindt u de logboeken van DSC-gebeurtenissen](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).
