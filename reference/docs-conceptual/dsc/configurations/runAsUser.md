---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Referenties gebruiken met DSC-resources
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941962"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="3cc78-103">Referenties gebruiken met DSC-resources</span><span class="sxs-lookup"><span data-stu-id="3cc78-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="3cc78-104">Van toepassing op: Windows Power shell 5,0, Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="3cc78-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="3cc78-105">U kunt een DSC-resource uitvoeren onder een opgegeven set referenties met behulp van de automatische eigenschap **PsDscRunAsCredential** in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="3cc78-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="3cc78-106">DSC voert standaard elke bron uit als het systeem account.</span><span class="sxs-lookup"><span data-stu-id="3cc78-106">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="3cc78-107">Het uitvoeren van een gebruiker is vaak nodig, zoals het installeren van MSI-pakketten in een specifieke gebruikers context, het instellen van de register sleutels van een gebruiker, het openen van de specifieke lokale map van een gebruiker of het verkrijgen van toegang tot een netwerk share.</span><span class="sxs-lookup"><span data-stu-id="3cc78-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="3cc78-108">De **SeInteractiveLogonRight** is vereist voor de doel computer, voor elk account dat u opgeeft voor **PSDSCRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="3cc78-108">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential**.</span></span> <span data-ttu-id="3cc78-109">Zie voor meer informatie [constanten voor account rechten](/windows/desktop/secauthz/account-rights-constants).</span><span class="sxs-lookup"><span data-stu-id="3cc78-109">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="3cc78-110">Elke DSC-resource heeft een **PsDscRunAsCredential** -eigenschap die kan worden ingesteld op alle gebruikers referenties (een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object).</span><span class="sxs-lookup"><span data-stu-id="3cc78-110">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="3cc78-111">De referentie kan worden vastgelegd als de waarde van de eigenschap in de configuratie, of u kunt de waarde instellen op [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), waarmee de gebruiker wordt gevraagd om een referentie wanneer de configuratie wordt gecompileerd (Zie [configuraties](configurations.md)voor meer informatie over het compileren van configuraties.</span><span class="sxs-lookup"><span data-stu-id="3cc78-111">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3cc78-112">In Power shell 5,0 wordt het gebruik van de eigenschap **PsDscRunAsCredential** in configuraties waarmee samengestelde resources worden aangeroepen, niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3cc78-112">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="3cc78-113">In Power shell 5,1 wordt de eigenschap **PsDscRunAsCredential** ondersteund in configuraties waarmee samengestelde resources worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="3cc78-113">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="3cc78-114">De eigenschap **PsDscRunAsCredential** is niet beschikbaar in power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="3cc78-114">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="3cc78-115">In het volgende voor beeld `Get-Credential` wordt gebruikt om de gebruiker om referenties te vragen.</span><span class="sxs-lookup"><span data-stu-id="3cc78-115">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="3cc78-116">De **register** bron wordt gebruikt om de register sleutel te wijzigen waarmee de achtergrond kleur voor het Windows-opdracht prompt venster wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3cc78-116">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
> <span data-ttu-id="3cc78-117">In dit voor beeld wordt ervan uitgegaan dat u een `C:\publicKeys\targetNode.cer`geldig certificaat hebt op en dat de vinger afdruk van het certificaat de weer gegeven waarde is.</span><span class="sxs-lookup"><span data-stu-id="3cc78-117">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="3cc78-118">Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)voor meer informatie over het versleutelen van referenties in MOF-bestanden van de DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="3cc78-118">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
