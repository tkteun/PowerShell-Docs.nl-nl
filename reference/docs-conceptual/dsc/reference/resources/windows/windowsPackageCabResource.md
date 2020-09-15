---
ms.date: 07/16/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsPackageCab-resource
ms.openlocfilehash: 7205a454d100bb369fd6cf0c5ac419585c8bbe86
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464142"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="21592-103">DSC WindowsPackageCab-resource</span><span class="sxs-lookup"><span data-stu-id="21592-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="21592-104">Van toepassing op: Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="21592-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="21592-105">De **WindowsPackageCab** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het installeren of verwijderen van Windows CAB-pakketten (CAB) op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="21592-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="21592-106">Op het doel knooppunt moet de Power shell-module DISM zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="21592-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="21592-107">Zie [DISM gebruiken in Windows Power shell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="21592-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

## <a name="syntax"></a><span data-ttu-id="21592-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="21592-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="21592-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="21592-109">Properties</span></span>

|<span data-ttu-id="21592-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="21592-110">Property</span></span> |<span data-ttu-id="21592-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="21592-111">Description</span></span> |
|---|---|
|<span data-ttu-id="21592-112">Naam</span><span class="sxs-lookup"><span data-stu-id="21592-112">Name</span></span> |<span data-ttu-id="21592-113">Hiermee wordt de naam van het pakket aangegeven dat u een specifieke status wilt bieden.</span><span class="sxs-lookup"><span data-stu-id="21592-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="21592-114">Bronpad</span><span class="sxs-lookup"><span data-stu-id="21592-114">SourcePath</span></span> |<span data-ttu-id="21592-115">Hiermee wordt het pad aangegeven waar het pakket zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="21592-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="21592-116">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="21592-116">LogPath</span></span> |<span data-ttu-id="21592-117">Hiermee wordt het volledige pad aangegeven waar u wilt dat de provider een logboek bestand opslaat om het pakket te installeren of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="21592-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="21592-118">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="21592-118">Common properties</span></span>

|<span data-ttu-id="21592-119">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="21592-119">Property</span></span> |<span data-ttu-id="21592-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="21592-120">Description</span></span> |
|---|---|
|<span data-ttu-id="21592-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="21592-121">DependsOn</span></span> |<span data-ttu-id="21592-122">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="21592-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="21592-123">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="21592-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="21592-124">Zo</span><span class="sxs-lookup"><span data-stu-id="21592-124">Ensure</span></span> |<span data-ttu-id="21592-125">Hiermee wordt aangegeven of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="21592-125">Indicates if the package is installed.</span></span> <span data-ttu-id="21592-126">Stel deze eigenschap in op **afwezig** om te controleren of het pakket niet is geïnstalleerd (of verwijder het pakket als dit is geïnstalleerd).</span><span class="sxs-lookup"><span data-stu-id="21592-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="21592-127">Stel deze in op **aanwezig** om te controleren of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="21592-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="21592-128">**Zorg ervoor dat** de eigenschap vereist is voor de **WindowsPackageCab** -resource.</span><span class="sxs-lookup"><span data-stu-id="21592-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="21592-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="21592-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="21592-130">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="21592-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="21592-131">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="21592-131">Example</span></span>

<span data-ttu-id="21592-132">De volgende voorbeeld configuratie haalt invoer parameters op en zorgt ervoor dat het CAB-bestand dat is opgegeven met de `$Name` para meter, wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="21592-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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
