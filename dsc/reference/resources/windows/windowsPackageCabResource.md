---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WindowsPackageCab-Resource
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076936"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="1a7db-103">DSC WindowsPackageCab-Resource</span><span class="sxs-lookup"><span data-stu-id="1a7db-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="1a7db-104">Van toepassing op: Windows PowerShell 5.1 of hoger</span><span class="sxs-lookup"><span data-stu-id="1a7db-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="1a7db-105">De **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om te installeren of verwijderen van Windows CAB-pakketten op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="1a7db-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="1a7db-106">Het doelknooppunt moet de DISM-PowerShell-module geïnstalleerd hebben.</span><span class="sxs-lookup"><span data-stu-id="1a7db-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="1a7db-107">Zie voor meer informatie, [DISM gebruiken in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="1a7db-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="1a7db-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1a7db-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="1a7db-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="1a7db-109">Properties</span></span>

|  <span data-ttu-id="1a7db-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="1a7db-110">Property</span></span>  |  <span data-ttu-id="1a7db-111">Description</span><span class="sxs-lookup"><span data-stu-id="1a7db-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="1a7db-112">Naam</span><span class="sxs-lookup"><span data-stu-id="1a7db-112">Name</span></span>| <span data-ttu-id="1a7db-113">Geeft de naam van het pakket voor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="1a7db-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="1a7db-114">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="1a7db-114">Ensure</span></span>| <span data-ttu-id="1a7db-115">Geeft aan of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a7db-115">Indicates if the package is installed.</span></span> <span data-ttu-id="1a7db-116">Deze eigenschap instellen op 'Afwezig"Controleer of dat het pakket niet is geïnstalleerd (of het pakket verwijderen als deze is geïnstalleerd).</span><span class="sxs-lookup"><span data-stu-id="1a7db-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="1a7db-117">Instellen om "" (de standaardwaarde) om te controleren of dat het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a7db-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="1a7db-118">Pad</span><span class="sxs-lookup"><span data-stu-id="1a7db-118">Path</span></span>| <span data-ttu-id="1a7db-119">Geeft het pad waar het pakket zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="1a7db-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="1a7db-120">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="1a7db-120">LogPath</span></span>| <span data-ttu-id="1a7db-121">Geeft het volledige pad waar u wilt dat de provider een logboekbestand om te installeren of verwijderen van het pakket op te slaan.</span><span class="sxs-lookup"><span data-stu-id="1a7db-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="1a7db-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1a7db-122">DependsOn</span></span> | <span data-ttu-id="1a7db-123">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="1a7db-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1a7db-124">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="1a7db-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="1a7db-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1a7db-125">Example</span></span>

<span data-ttu-id="1a7db-126">De volgende voorbeeldconfiguratie parameters nodig heeft, en zorgt ervoor dat het CAB-bestand opgegeven door de `$Name` parameter is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a7db-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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