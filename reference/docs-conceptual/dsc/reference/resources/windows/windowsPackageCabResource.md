---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsPackageCab-resource
description: DSC WindowsPackageCab-resource
ms.openlocfilehash: 3ac10eb2a7da502b8cac23ab8bfee869a4e26fd3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143021"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="8bfb8-103">DSC WindowsPackageCab-resource</span><span class="sxs-lookup"><span data-stu-id="8bfb8-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="8bfb8-104">Van toepassing op: Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="8bfb8-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="8bfb8-105">De **WindowsPackageCab** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het installeren of verwijderen van Windows CAB-pakketten (CAB) op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="8bfb8-106">Op het doel knooppunt moet de Power shell-module DISM zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="8bfb8-107">Zie [DISM gebruiken in Windows Power shell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="8bfb8-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="8bfb8-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="8bfb8-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8bfb8-109">Properties</span></span>

|<span data-ttu-id="8bfb8-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8bfb8-110">Property</span></span> |<span data-ttu-id="8bfb8-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8bfb8-111">Description</span></span> |
|---|---|
|<span data-ttu-id="8bfb8-112">Naam</span><span class="sxs-lookup"><span data-stu-id="8bfb8-112">Name</span></span> |<span data-ttu-id="8bfb8-113">Hiermee wordt de naam van het pakket aangegeven dat u een specifieke status wilt bieden.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="8bfb8-114">Bronpad</span><span class="sxs-lookup"><span data-stu-id="8bfb8-114">SourcePath</span></span> |<span data-ttu-id="8bfb8-115">Hiermee wordt het pad aangegeven waar het pakket zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="8bfb8-116">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="8bfb8-116">LogPath</span></span> |<span data-ttu-id="8bfb8-117">Hiermee wordt het volledige pad aangegeven waar u wilt dat de provider een logboek bestand opslaat om het pakket te installeren of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="8bfb8-118">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8bfb8-118">Common properties</span></span>

|<span data-ttu-id="8bfb8-119">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8bfb8-119">Property</span></span> |<span data-ttu-id="8bfb8-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8bfb8-120">Description</span></span> |
|---|---|
|<span data-ttu-id="8bfb8-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8bfb8-121">DependsOn</span></span> |<span data-ttu-id="8bfb8-122">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8bfb8-123">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="8bfb8-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="8bfb8-124">Zo</span><span class="sxs-lookup"><span data-stu-id="8bfb8-124">Ensure</span></span> |<span data-ttu-id="8bfb8-125">Hiermee wordt aangegeven of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-125">Indicates if the package is installed.</span></span> <span data-ttu-id="8bfb8-126">Stel deze eigenschap in op **afwezig** om te controleren of het pakket niet is geïnstalleerd (of verwijder het pakket als dit is geïnstalleerd).</span><span class="sxs-lookup"><span data-stu-id="8bfb8-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="8bfb8-127">Stel deze in op **aanwezig** om te controleren of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="8bfb8-128">**Zorg ervoor dat** de eigenschap vereist is voor de **WindowsPackageCab** -resource.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="8bfb8-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="8bfb8-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="8bfb8-130">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="8bfb8-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8bfb8-131">Example</span></span>

<span data-ttu-id="8bfb8-132">De volgende voorbeeld configuratie haalt invoer parameters op en zorgt ervoor dat het CAB-bestand dat is opgegeven met de `$Name` para meter, wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8bfb8-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```
