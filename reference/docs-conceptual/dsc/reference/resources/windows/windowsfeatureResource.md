---
ms.date: 07/16/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC-WindowsFeature-resource
ms.openlocfilehash: b15b267c6898697816b386a381e5a6d59acd492a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464108"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="84ff9-103">DSC-WindowsFeature-resource</span><span class="sxs-lookup"><span data-stu-id="84ff9-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="84ff9-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="84ff9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="84ff9-105">De resource **WindowsFeature** in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat rollen en functies worden toegevoegd aan of verwijderd uit een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="84ff9-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="84ff9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="84ff9-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="84ff9-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="84ff9-107">Properties</span></span>

|<span data-ttu-id="84ff9-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="84ff9-108">Property</span></span> |<span data-ttu-id="84ff9-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="84ff9-109">Description</span></span> |
|---|---|
|<span data-ttu-id="84ff9-110">Naam</span><span class="sxs-lookup"><span data-stu-id="84ff9-110">Name</span></span> |<span data-ttu-id="84ff9-111">Hiermee wordt de naam aangegeven van de functie of het onderdeel dat u wilt garanderen, wordt toegevoegd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="84ff9-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="84ff9-112">Dit is hetzelfde als de **naam** eigenschap van de cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) en niet de weergave naam van de functie of het onderdeel.</span><span class="sxs-lookup"><span data-stu-id="84ff9-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="84ff9-113">Referentie</span><span class="sxs-lookup"><span data-stu-id="84ff9-113">Credential</span></span> |<span data-ttu-id="84ff9-114">Hiermee geeft u de referenties op die moeten worden gebruikt om de functie of het onderdeel toe te voegen of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="84ff9-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="84ff9-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="84ff9-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="84ff9-116">Stel deze eigenschap in op `$true` om de status van alle vereiste subonderdelen met de status van de functie die u opgeeft met de eigenschap **name** te controleren.</span><span class="sxs-lookup"><span data-stu-id="84ff9-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="84ff9-117">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="84ff9-117">LogPath</span></span> |<span data-ttu-id="84ff9-118">Hiermee geeft u het pad naar een logboek bestand op waar de resource provider de bewerking moet registreren.</span><span class="sxs-lookup"><span data-stu-id="84ff9-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="84ff9-119">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="84ff9-119">Common properties</span></span>

|<span data-ttu-id="84ff9-120">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="84ff9-120">Property</span></span> |<span data-ttu-id="84ff9-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="84ff9-121">Description</span></span> |
|---|---|
|<span data-ttu-id="84ff9-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="84ff9-122">DependsOn</span></span> |<span data-ttu-id="84ff9-123">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="84ff9-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="84ff9-124">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="84ff9-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="84ff9-125">Zo</span><span class="sxs-lookup"><span data-stu-id="84ff9-125">Ensure</span></span> |<span data-ttu-id="84ff9-126">Hiermee wordt aangegeven of de functie of het onderdeel is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="84ff9-126">Indicates if the role or feature is added.</span></span> <span data-ttu-id="84ff9-127">Stel deze eigenschap in op **aanwezig**om te controleren of de functie of het onderdeel is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="84ff9-127">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="84ff9-128">Om ervoor te zorgen dat de functie of het onderdeel wordt verwijderd, stelt u de eigenschap in op **afwezig**.</span><span class="sxs-lookup"><span data-stu-id="84ff9-128">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="84ff9-129">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="84ff9-129">The default value is **Present**.</span></span> |
|<span data-ttu-id="84ff9-130">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="84ff9-130">PsDscRunAsCredential</span></span> |<span data-ttu-id="84ff9-131">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="84ff9-131">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="84ff9-132">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="84ff9-132">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="84ff9-133">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="84ff9-133">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="84ff9-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="84ff9-134">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
