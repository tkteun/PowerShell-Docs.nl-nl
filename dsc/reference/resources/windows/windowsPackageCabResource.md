---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WindowsPackageCab-Resource
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048257"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="3ae2f-103">DSC WindowsPackageCab-Resource</span><span class="sxs-lookup"><span data-stu-id="3ae2f-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="3ae2f-104">Van toepassing op: Windows PowerShell 5.1 of hoger</span><span class="sxs-lookup"><span data-stu-id="3ae2f-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="3ae2f-105">De **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om te installeren of verwijderen van Windows CAB-pakketten op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="3ae2f-106">Het doelknooppunt moet de DISM-PowerShell-module geïnstalleerd hebben.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="3ae2f-107">Zie voor meer informatie, [DISM gebruiken in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="3ae2f-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="3ae2f-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3ae2f-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="3ae2f-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="3ae2f-109">Properties</span></span>

|  <span data-ttu-id="3ae2f-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="3ae2f-110">Property</span></span>  |  <span data-ttu-id="3ae2f-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3ae2f-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="3ae2f-112">Naam</span><span class="sxs-lookup"><span data-stu-id="3ae2f-112">Name</span></span>| <span data-ttu-id="3ae2f-113">Geeft de naam van het pakket voor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="3ae2f-114">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="3ae2f-114">Ensure</span></span>| <span data-ttu-id="3ae2f-115">Geeft aan of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-115">Indicates if the package is installed.</span></span> <span data-ttu-id="3ae2f-116">Deze eigenschap instellen op 'Afwezig"Controleer of dat het pakket niet is geïnstalleerd (of het pakket verwijderen als deze is geïnstalleerd).</span><span class="sxs-lookup"><span data-stu-id="3ae2f-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="3ae2f-117">Instellen om "" (de standaardwaarde) om te controleren of dat het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="3ae2f-118">Pad</span><span class="sxs-lookup"><span data-stu-id="3ae2f-118">Path</span></span>| <span data-ttu-id="3ae2f-119">Geeft het pad waar het pakket zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="3ae2f-120">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="3ae2f-120">LogPath</span></span>| <span data-ttu-id="3ae2f-121">Geeft het volledige pad waar u wilt dat de provider een logboekbestand om te installeren of verwijderen van het pakket op te slaan.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="3ae2f-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3ae2f-122">DependsOn</span></span> | <span data-ttu-id="3ae2f-123">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3ae2f-124">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="3ae2f-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3ae2f-125">Example</span></span>

<span data-ttu-id="3ae2f-126">De volgende voorbeeldconfiguratie parameters nodig heeft, en zorgt ervoor dat het CAB-bestand opgegeven door de `$Name` parameter is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3ae2f-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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