---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Referenties gebruiken met DSC-resources
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080047"
---
# <a name="use-credentials-with-dsc-resources"></a>Referenties gebruiken met DSC-resources

> Van toepassing op: Windows PowerShell 5.0, Windows PowerShell 5.1

U kunt een DSC-resource onder een opgegeven set referenties uitvoeren met behulp van de automatische **PsDscRunAsCredential** eigenschap in de configuratie.
DSC wordt standaard elke resource uitgevoerd als het systeem-account.
Er zijn tijden wanneer uitgevoerd als een gebruiker is nodig, zoals het installeren van MSI-pakketten in de context van een specifieke gebruiker, instellen van een gebruiker-registersleutels, toegang tot specifieke lokale directory van een gebruiker of toegang krijgen tot een netwerk share.

Elke DSC-resource heeft een **PsDscRunAsCredential** eigenschap die kan worden ingesteld op de referenties van een gebruiker (een [PSCredential](/dotnet/api/system.management.automation.pscredential) object).
De referentie op die kan worden vastgelegd als de waarde van de eigenschap in de configuratie, of u kunt de waarde instellen op [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), die wordt de gebruiker gevraagd om een referentie wanneer de configuratie wordt gecompileerd (voor meer informatie over -configuraties compileren, Zie [configuraties](configurations.md).

> [!NOTE]
> In PowerShell 5.0, met behulp van de **PsDscRunAsCredential** eigenschap in configuraties aanroepen van samengestelde resources wordt niet ondersteund.
> In PowerShell 5.1, de **PsDscRunAsCredential** eigenschap wordt ondersteund in configuraties aanroepen van samengestelde resources.
> De **PsDscRunAsCredential** eigenschap is niet beschikbaar in PowerShell 4.0.

In het volgende voorbeeld `Get-Credential` wordt gebruikt voor de gebruiker gevraagd om referenties.
De **register** bron wordt gebruikt om de registersleutel die Hiermee geeft u de achtergrondkleur voor het Windows-opdrachtpromptvenster wijzigen.

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> In dit voorbeeld wordt ervan uitgegaan dat u hebt een geldig certificaat op `C:\publicKeys\targetNode.cer`, en dat de vingerafdruk van certificaat de waarde die wordt weergegeven is.
> Zie voor meer informatie over het versleutelen van de referenties in MOF-bestanden voor DSC-configuratie [beveiligen van het MOF-bestand](../pull-server/secureMOF.md).
