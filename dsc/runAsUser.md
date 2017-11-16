---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC uitgevoerd met de referenties van gebruiker
ms.openlocfilehash: f15b2e4bfb888e2f3646a33cc0191e33a7ebb8ab
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="165ca-103">DSC uitgevoerd met de referenties van gebruiker</span><span class="sxs-lookup"><span data-stu-id="165ca-103">Running DSC with user credentials</span></span> 

> <span data-ttu-id="165ca-104">Van toepassing op: Windows PowerShell 5.0, 5.1 van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="165ca-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="165ca-105">U kunt een DSC-resource onder een opgegeven set referenties uitvoeren met behulp van de automatische **PsDscRunAsCredential** eigenschap in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="165ca-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="165ca-106">Standaard wordt elke resource DSC uitgevoerd als het systeem-account.</span><span class="sxs-lookup"><span data-stu-id="165ca-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="165ca-107">Er zijn momenten wanneer uitgevoerd, zoals een gebruiker is nodig, zoals een MSI-pakketten installeren in de context van een specifieke gebruiker, instellen van een gebruiker registersleutels, toegang tot specifieke lokale directory van een gebruiker of toegang tot een netwerk share.</span><span class="sxs-lookup"><span data-stu-id="165ca-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="165ca-108">Elke DSC-resource heeft een **PsDscRunAsCredential** eigenschap die kan worden ingesteld op de referenties van een gebruiker (een [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) object).</span><span class="sxs-lookup"><span data-stu-id="165ca-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="165ca-109">De referentie kan worden vastgelegd als de waarde van de eigenschap in de configuratie of u kunt de waarde instellen op [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), die wordt de gebruiker gevraagd om een referentie wanneer de configuratie wordt gecompileerd (voor meer informatie over compileren van configuraties, Zie [configuraties](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="165ca-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="165ca-110">**Opmerking:** In PowerShell 5.0, met behulp van de **PsDscRunAsCredential** eigenschap in de configuraties voor het aanroepen van samengestelde bronnen wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="165ca-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> 
><span data-ttu-id="165ca-111">In PowerShell 5.1, de **PsDscRunAsCredential** eigenschap wordt ondersteund in de configuraties voor het aanroepen van samengestelde bronnen.</span><span class="sxs-lookup"><span data-stu-id="165ca-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="165ca-112">**Opmerking:** de **PsDscRunAsCredential** eigenschap is niet beschikbaar in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="165ca-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="165ca-113">In het volgende voorbeeld **Get-Credential** wordt gebruikt voor de gebruiker gevraagd om referenties.</span><span class="sxs-lookup"><span data-stu-id="165ca-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span> <span data-ttu-id="165ca-114">De [register](registryResource.md) bron wordt gebruikt om te wijzigen van de registersleutel die de achtergrondkleur voor het Windows-opdrachtpromptvenster geeft.</span><span class="sxs-lookup"><span data-stu-id="165ca-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
><span data-ttu-id="165ca-115">**Opmerking:** in dit voorbeeld wordt ervan uitgegaan dat u hebt een geldig certificaat op `C:\publicKeys\targetNode.cer`, en dat de vingerafdruk van certificaat de waarde die wordt weergegeven is.</span><span class="sxs-lookup"><span data-stu-id="165ca-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="165ca-116">Zie voor meer informatie over het coderen van referenties in het MOF-bestanden van DSC-configuratie [beveiligen van het MOF-bestand](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="165ca-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>

