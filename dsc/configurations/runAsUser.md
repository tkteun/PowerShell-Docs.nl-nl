---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Referenties gebruiken met DSC-resources
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470768"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="a9e63-103">Referenties gebruiken met DSC-resources</span><span class="sxs-lookup"><span data-stu-id="a9e63-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="a9e63-104">Van toepassing op: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="a9e63-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="a9e63-105">U kunt een DSC-resource onder een opgegeven set referenties uitvoeren met behulp van de automatische **PsDscRunAsCredential** eigenschap in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="a9e63-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="a9e63-106">DSC wordt standaard elke resource uitgevoerd als het systeem-account.</span><span class="sxs-lookup"><span data-stu-id="a9e63-106">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="a9e63-107">Er zijn tijden wanneer uitgevoerd als een gebruiker is nodig, zoals het installeren van MSI-pakketten in de context van een specifieke gebruiker, instellen van een gebruiker-registersleutels, toegang tot specifieke lokale directory van een gebruiker of toegang krijgen tot een netwerk share.</span><span class="sxs-lookup"><span data-stu-id="a9e63-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="a9e63-108">De **SeInteractiveLogonRight** is vereist, voor de doel-VM voor een account dat u opgeeft op **PSDSCRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="a9e63-108">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential**.</span></span> <span data-ttu-id="a9e63-109">Zie voor meer informatie, [Account rechten constanten](/windows/desktop/secauthz/account-rights-constants).</span><span class="sxs-lookup"><span data-stu-id="a9e63-109">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="a9e63-110">Elke DSC-resource heeft een **PsDscRunAsCredential** eigenschap die kan worden ingesteld op de referenties van een gebruiker (een [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span><span class="sxs-lookup"><span data-stu-id="a9e63-110">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="a9e63-111">De referentie op die kan worden vastgelegd als de waarde van de eigenschap in de configuratie, of u kunt de waarde instellen op [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), die wordt de gebruiker gevraagd om een referentie wanneer de configuratie wordt gecompileerd (voor meer informatie over -configuraties compileren, Zie [configuraties](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a9e63-111">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a9e63-112">In PowerShell 5.0, met behulp van de **PsDscRunAsCredential** eigenschap in configuraties aanroepen van samengestelde resources wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a9e63-112">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="a9e63-113">In PowerShell 5.1, de **PsDscRunAsCredential** eigenschap wordt ondersteund in configuraties aanroepen van samengestelde resources.</span><span class="sxs-lookup"><span data-stu-id="a9e63-113">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="a9e63-114">De **PsDscRunAsCredential** eigenschap is niet beschikbaar in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="a9e63-114">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="a9e63-115">In het volgende voorbeeld `Get-Credential` wordt gebruikt voor de gebruiker gevraagd om referenties.</span><span class="sxs-lookup"><span data-stu-id="a9e63-115">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="a9e63-116">De **register** bron wordt gebruikt om de registersleutel die Hiermee geeft u de achtergrondkleur voor het Windows-opdrachtpromptvenster wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a9e63-116">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
> <span data-ttu-id="a9e63-117">In dit voorbeeld wordt ervan uitgegaan dat u hebt een geldig certificaat op `C:\publicKeys\targetNode.cer`, en dat de vingerafdruk van certificaat de waarde die wordt weergegeven is.</span><span class="sxs-lookup"><span data-stu-id="a9e63-117">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="a9e63-118">Zie voor meer informatie over het versleutelen van de referenties in MOF-bestanden voor DSC-configuratie [beveiligen van het MOF-bestand](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="a9e63-118">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
