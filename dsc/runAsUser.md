---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC uitgevoerd met de referenties van gebruiker
ms.openlocfilehash: 7b57732679e4fb29112a3ca7fe64cba2bda67207
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="running-dsc-with-user-credentials"></a>DSC uitgevoerd met de referenties van gebruiker 

> Van toepassing op: Windows PowerShell 5.0, 5.1 van Windows PowerShell

U kunt een DSC-resource onder een opgegeven set referenties uitvoeren met behulp van de automatische **PsDscRunAsCredential** eigenschap in de configuratie. Standaard wordt elke resource DSC uitgevoerd als het systeem-account.
Er zijn momenten wanneer uitgevoerd, zoals een gebruiker is nodig, zoals een MSI-pakketten installeren in de context van een specifieke gebruiker, instellen van een gebruiker registersleutels, toegang tot specifieke lokale directory van een gebruiker of toegang tot een netwerk share.

Elke DSC-resource heeft een **PsDscRunAsCredential** eigenschap die kan worden ingesteld op de referenties van een gebruiker (een [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) object).
De referentie kan worden vastgelegd als de waarde van de eigenschap in de configuratie of u kunt de waarde instellen op [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), die wordt de gebruiker gevraagd om een referentie wanneer de configuratie wordt gecompileerd (voor meer informatie over compileren van configuraties, Zie [configuraties](configurations.md).

>**Opmerking:** In PowerShell 5.0, met behulp van de **PsDscRunAsCredential** eigenschap in de configuraties voor het aanroepen van samengestelde bronnen wordt niet ondersteund. 
>In PowerShell 5.1, de **PsDscRunAsCredential** eigenschap wordt ondersteund in de configuraties voor het aanroepen van samengestelde bronnen.

>**Opmerking:** de **PsDscRunAsCredential** eigenschap is niet beschikbaar in PowerShell 4.0.

In het volgende voorbeeld **Get-Credential** wordt gebruikt voor de gebruiker gevraagd om referenties. De [register](registryResource.md) bron wordt gebruikt om te wijzigen van de registersleutel die de achtergrondkleur voor het Windows-opdrachtpromptvenster geeft.

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
>**Opmerking:** in dit voorbeeld wordt ervan uitgegaan dat u hebt een geldig certificaat op `C:\publicKeys\targetNode.cer`, en dat de vingerafdruk van certificaat de waarde die wordt weergegeven is.
>Zie voor meer informatie over het coderen van referenties in het MOF-bestanden van DSC-configuratie [beveiligen van het MOF-bestand](secureMOF.md).

