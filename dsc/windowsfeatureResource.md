---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsFeature-Resource
ms.openlocfilehash: b4f50cb9ee172600b1811175e9cf67f6a7ed2d55
ms.sourcegitcommit: cd5a1f054cbf9eb95c5242a995f9741e031ddb24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/28/2017
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="f203e-103">DSC-WindowsFeature-Resource</span><span class="sxs-lookup"><span data-stu-id="f203e-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="f203e-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f203e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f203e-105">De **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat functies en onderdelen worden toegevoegd of verwijderd in een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="f203e-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f203e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f203e-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="f203e-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="f203e-107">Properties</span></span>

|  <span data-ttu-id="f203e-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="f203e-108">Property</span></span>  |  <span data-ttu-id="f203e-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f203e-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="f203e-110">Naam</span><span class="sxs-lookup"><span data-stu-id="f203e-110">Name</span></span>| <span data-ttu-id="f203e-111">Hiermee geeft u de naam van de rol of functie die u wilt zorgen toegevoegd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f203e-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="f203e-112">Dit is hetzelfde als de __naam__ eigenschap uit de [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, en niet de weergavenaam van de rol of functie.</span><span class="sxs-lookup"><span data-stu-id="f203e-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>| 
| <span data-ttu-id="f203e-113">referentie</span><span class="sxs-lookup"><span data-stu-id="f203e-113">Credential</span></span>| <span data-ttu-id="f203e-114">Hiermee geeft u de referenties toevoegen of verwijderen van de rol of functie.</span><span class="sxs-lookup"><span data-stu-id="f203e-114">Indicates the credentials to use to add or remove the role or feature.</span></span>| 
| <span data-ttu-id="f203e-115">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="f203e-115">Ensure</span></span>| <span data-ttu-id="f203e-116">Hiermee wordt aangegeven of de rol of functie is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f203e-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="f203e-117">Om ervoor te zorgen dat de rol of functie is toegevoegd, stel deze eigenschap in op 'Aanwezig' om ervoor te zorgen dat de rol of functie wordt verwijderd, de eigenschap instellen op 'Afwezig'.</span><span class="sxs-lookup"><span data-stu-id="f203e-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="f203e-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="f203e-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="f203e-119">Deze eigenschap instellen op __$true__ om te controleren of de status van alle vereiste subonderdelen met de status van de functie die u met opgeeft de __naam__ eigenschap.</span><span class="sxs-lookup"><span data-stu-id="f203e-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>| 
| <span data-ttu-id="f203e-120">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="f203e-120">LogPath</span></span>| <span data-ttu-id="f203e-121">Geeft het pad naar een logboekbestand waar u de resourceprovider aan te melden van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="f203e-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="f203e-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f203e-122">DependsOn</span></span>| <span data-ttu-id="f203e-123">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="f203e-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f203e-124">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f203e-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="f203e-125">Bron</span><span class="sxs-lookup"><span data-stu-id="f203e-125">Source</span></span>| <span data-ttu-id="f203e-126">Geeft de locatie van het bronbestand moet worden gebruikt voor de installatie, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="f203e-126">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="f203e-127">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f203e-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

