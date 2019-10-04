---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Referenties gebruiken met DSC-resources
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941962"
---
# <a name="use-credentials-with-dsc-resources"></a>Referenties gebruiken met DSC-resources

> Van toepassing op: Windows Power shell 5,0, Windows Power shell 5,1

U kunt een DSC-resource uitvoeren onder een opgegeven set referenties met behulp van de automatische eigenschap **PsDscRunAsCredential** in de configuratie. DSC voert standaard elke bron uit als het systeem account. Het uitvoeren van een gebruiker is vaak nodig, zoals het installeren van MSI-pakketten in een specifieke gebruikers context, het instellen van de register sleutels van een gebruiker, het openen van de specifieke lokale map van een gebruiker of het verkrijgen van toegang tot een netwerk share. De **SeInteractiveLogonRight** is vereist voor de doel computer, voor elk account dat u opgeeft voor **PSDSCRunAsCredential**. Zie voor meer informatie [constanten voor account rechten](/windows/desktop/secauthz/account-rights-constants).

Elke DSC-resource heeft een **PsDscRunAsCredential** -eigenschap die kan worden ingesteld op alle gebruikers referenties (een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object). De referentie kan worden vastgelegd als de waarde van de eigenschap in de configuratie, of u kunt de waarde instellen op [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), waarmee de gebruiker wordt gevraagd om een referentie wanneer de configuratie wordt gecompileerd (voor informatie over het compileren van configuraties, Zie [configuraties](configurations.md).

> [!NOTE]
> In Power shell 5,0 wordt het gebruik van de eigenschap **PsDscRunAsCredential** in configuraties waarmee samengestelde resources worden aangeroepen, niet ondersteund. In Power shell 5,1 wordt de eigenschap **PsDscRunAsCredential** ondersteund in configuraties waarmee samengestelde resources worden aangeroepen. De eigenschap **PsDscRunAsCredential** is niet beschikbaar in power Shell 4,0.

In het volgende voor beeld wordt `Get-Credential` gebruikt om de gebruiker om referenties te vragen. De **register** bron wordt gebruikt om de register sleutel te wijzigen waarmee de achtergrond kleur voor het Windows-opdracht prompt venster wordt opgegeven.

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
> In dit voor beeld wordt ervan uitgegaan dat u een geldig certificaat op `C:\publicKeys\targetNode.cer` hebt en dat de vinger afdruk van het certificaat de weer gegeven waarde is. Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)voor meer informatie over het versleutelen van referenties in MOF-bestanden van de DSC-configuratie.
