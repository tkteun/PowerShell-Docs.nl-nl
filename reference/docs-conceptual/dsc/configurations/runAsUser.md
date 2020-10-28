---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Referenties gebruiken met DSC-resources
description: Met DSC kunt u referenties opgeven voor een configuratie zodat de configuratie-instellingen kunnen worden toegepast in de context van een specifiek gebruikers account in plaats van het lokale systeem account.
ms.openlocfilehash: e4ca39e099afacd7cb06c4d9ef889f94deb73cee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645090"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="ca195-104">Referenties gebruiken met DSC-resources</span><span class="sxs-lookup"><span data-stu-id="ca195-104">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="ca195-105">Van toepassing op: Windows Power shell 5,0, Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="ca195-105">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="ca195-106">U kunt een DSC-resource uitvoeren onder een opgegeven set referenties met behulp van de automatische eigenschap **PsDscRunAsCredential** in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="ca195-106">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="ca195-107">DSC voert standaard elke bron uit als het systeem account.</span><span class="sxs-lookup"><span data-stu-id="ca195-107">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="ca195-108">Het uitvoeren van een gebruiker is vaak nodig, zoals het installeren van MSI-pakketten in een specifieke gebruikers context, het instellen van de register sleutels van een gebruiker, het openen van de specifieke lokale map van een gebruiker of het verkrijgen van toegang tot een netwerk share.</span><span class="sxs-lookup"><span data-stu-id="ca195-108">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="ca195-109">De **SeInteractiveLogonRight** is vereist voor de doel computer, voor elk account dat u opgeeft voor **PSDSCRunAsCredential** .</span><span class="sxs-lookup"><span data-stu-id="ca195-109">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential** .</span></span> <span data-ttu-id="ca195-110">Zie voor meer informatie [constanten voor account rechten](/windows/desktop/secauthz/account-rights-constants).</span><span class="sxs-lookup"><span data-stu-id="ca195-110">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="ca195-111">Elke DSC-resource heeft een **PsDscRunAsCredential** -eigenschap die kan worden ingesteld op alle gebruikers referenties (een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object).</span><span class="sxs-lookup"><span data-stu-id="ca195-111">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="ca195-112">De referentie kan worden vastgelegd als de waarde van de eigenschap in de configuratie, of u kunt de waarde instellen op [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), waarmee de gebruiker wordt gevraagd om een referentie wanneer de configuratie wordt gecompileerd (Zie [configuraties](configurations.md)voor meer informatie over het compileren van configuraties.</span><span class="sxs-lookup"><span data-stu-id="ca195-112">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ca195-113">In Power shell 5,0 wordt het gebruik van de eigenschap **PsDscRunAsCredential** in configuraties waarmee samengestelde resources worden aangeroepen, niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ca195-113">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="ca195-114">In Power shell 5,1 wordt de eigenschap **PsDscRunAsCredential** ondersteund in configuraties waarmee samengestelde resources worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="ca195-114">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="ca195-115">De eigenschap **PsDscRunAsCredential** is niet beschikbaar in power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="ca195-115">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="ca195-116">In het volgende voor beeld `Get-Credential` wordt gebruikt om de gebruiker om referenties te vragen.</span><span class="sxs-lookup"><span data-stu-id="ca195-116">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="ca195-117">De **register** bron wordt gebruikt om de register sleutel te wijzigen waarmee de achtergrond kleur voor het Windows-opdracht prompt venster wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ca195-117">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
> <span data-ttu-id="ca195-118">In dit voor beeld wordt ervan uitgegaan dat u een geldig certificaat hebt op `C:\publicKeys\targetNode.cer` en dat de vinger afdruk van het certificaat de weer gegeven waarde is.</span><span class="sxs-lookup"><span data-stu-id="ca195-118">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="ca195-119">Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)voor meer informatie over het versleutelen van referenties in MOF-bestanden van de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="ca195-119">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
