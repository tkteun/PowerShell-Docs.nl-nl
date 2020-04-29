---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-WindowsFeature-resource
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942417"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="52ad8-103">DSC-WindowsFeature-resource</span><span class="sxs-lookup"><span data-stu-id="52ad8-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="52ad8-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="52ad8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="52ad8-105">De resource **WindowsFeature** in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat rollen en functies worden toegevoegd aan of verwijderd uit een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="52ad8-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="52ad8-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="52ad8-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="52ad8-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="52ad8-107">Properties</span></span>

|<span data-ttu-id="52ad8-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="52ad8-108">Property</span></span> |<span data-ttu-id="52ad8-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="52ad8-109">Description</span></span> |
|---|---|
|<span data-ttu-id="52ad8-110">Naam</span><span class="sxs-lookup"><span data-stu-id="52ad8-110">Name</span></span> |<span data-ttu-id="52ad8-111">Hiermee wordt de naam aangegeven van de functie of het onderdeel dat u wilt garanderen, wordt toegevoegd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="52ad8-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="52ad8-112">Dit is hetzelfde als de **naam** eigenschap van de cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) en niet de weergave naam van de functie of het onderdeel.</span><span class="sxs-lookup"><span data-stu-id="52ad8-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="52ad8-113">Referentie</span><span class="sxs-lookup"><span data-stu-id="52ad8-113">Credential</span></span> |<span data-ttu-id="52ad8-114">Hiermee geeft u de referenties op die moeten worden gebruikt om de functie of het onderdeel toe te voegen of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="52ad8-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="52ad8-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="52ad8-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="52ad8-116">Stel deze eigenschap in `$true` op om de status van alle vereiste subonderdelen met de status van de functie die u opgeeft met de eigenschap **name** te controleren.</span><span class="sxs-lookup"><span data-stu-id="52ad8-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="52ad8-117">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="52ad8-117">LogPath</span></span> |<span data-ttu-id="52ad8-118">Hiermee geeft u het pad naar een logboek bestand op waar de resource provider de bewerking moet registreren.</span><span class="sxs-lookup"><span data-stu-id="52ad8-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |
|<span data-ttu-id="52ad8-119">Bron</span><span class="sxs-lookup"><span data-stu-id="52ad8-119">Source</span></span> |<span data-ttu-id="52ad8-120">Hiermee wordt de locatie aangegeven van het bron bestand dat moet worden gebruikt voor installatie, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="52ad8-120">Indicates the location of the source file to use for installation, if necessary.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="52ad8-121">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="52ad8-121">Common properties</span></span>

|<span data-ttu-id="52ad8-122">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="52ad8-122">Property</span></span> |<span data-ttu-id="52ad8-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="52ad8-123">Description</span></span> |
|---|---|
|<span data-ttu-id="52ad8-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="52ad8-124">DependsOn</span></span> |<span data-ttu-id="52ad8-125">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="52ad8-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="52ad8-126">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="52ad8-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="52ad8-127">Zo</span><span class="sxs-lookup"><span data-stu-id="52ad8-127">Ensure</span></span> |<span data-ttu-id="52ad8-128">Hiermee wordt aangegeven of de functie of het onderdeel is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="52ad8-128">Indicates if the role or feature is added.</span></span> <span data-ttu-id="52ad8-129">Stel deze eigenschap in op **aanwezig**om te controleren of de functie of het onderdeel is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="52ad8-129">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="52ad8-130">Om ervoor te zorgen dat de functie of het onderdeel wordt verwijderd, stelt u de eigenschap in op **afwezig**.</span><span class="sxs-lookup"><span data-stu-id="52ad8-130">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="52ad8-131">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="52ad8-131">The default value is **Present**.</span></span> |
|<span data-ttu-id="52ad8-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="52ad8-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="52ad8-133">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="52ad8-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="52ad8-134">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="52ad8-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="52ad8-135">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="52ad8-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="52ad8-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="52ad8-136">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```