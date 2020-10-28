---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsFeatureSet-resource
description: DSC WindowsFeatureSet-resource
ms.openlocfilehash: f7706679e3dfe85a8cf5a6795bc100657b018678
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656640"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="7ff34-103">DSC WindowsFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="7ff34-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="7ff34-104">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="7ff34-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="7ff34-105">De **WindowsFeatureSet** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat rollen en functies worden toegevoegd aan of verwijderd uit een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="7ff34-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="7ff34-106">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [resource WindowsFeature](windowsfeatureResource.md) aanroept voor elk onderdeel dat is opgegeven in de eigenschap **name** .</span><span class="sxs-lookup"><span data-stu-id="7ff34-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="7ff34-107">Gebruik deze resource als u een aantal Windows-onderdelen wilt configureren met dezelfde status.</span><span class="sxs-lookup"><span data-stu-id="7ff34-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ff34-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ff34-108">Syntax</span></span>

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7ff34-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="7ff34-109">Properties</span></span>

|  <span data-ttu-id="7ff34-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7ff34-110">Property</span></span>  |  <span data-ttu-id="7ff34-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7ff34-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="7ff34-112">Naam</span><span class="sxs-lookup"><span data-stu-id="7ff34-112">Name</span></span> |<span data-ttu-id="7ff34-113">De namen van de functies of onderdelen die u wilt controleren, worden toegevoegd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7ff34-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="7ff34-114">Dit is hetzelfde als de **naam** eigenschap van de cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) en niet de weergave naam van de functies of onderdelen.</span><span class="sxs-lookup"><span data-stu-id="7ff34-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="7ff34-115">Bron</span><span class="sxs-lookup"><span data-stu-id="7ff34-115">Source</span></span> |<span data-ttu-id="7ff34-116">Hiermee wordt de locatie aangegeven van het bron bestand dat moet worden gebruikt voor installatie, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="7ff34-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="7ff34-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="7ff34-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="7ff34-118">Stel deze eigenschap in op `$true` om alle vereiste subonderdelen toe te voegen met de functies die u opgeeft met de eigenschap **naam** .</span><span class="sxs-lookup"><span data-stu-id="7ff34-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="7ff34-119">Referentie</span><span class="sxs-lookup"><span data-stu-id="7ff34-119">Credential</span></span> |<span data-ttu-id="7ff34-120">De referenties die moeten worden gebruikt om de functies of onderdelen toe te voegen of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7ff34-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="7ff34-121">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="7ff34-121">LogPath</span></span> |<span data-ttu-id="7ff34-122">Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren.</span><span class="sxs-lookup"><span data-stu-id="7ff34-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7ff34-123">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="7ff34-123">Common properties</span></span>

|<span data-ttu-id="7ff34-124">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7ff34-124">Property</span></span> |<span data-ttu-id="7ff34-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7ff34-125">Description</span></span> |
|---|---|
|<span data-ttu-id="7ff34-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7ff34-126">DependsOn</span></span> |<span data-ttu-id="7ff34-127">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="7ff34-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7ff34-128">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="7ff34-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7ff34-129">Zo</span><span class="sxs-lookup"><span data-stu-id="7ff34-129">Ensure</span></span> |<span data-ttu-id="7ff34-130">Hiermee wordt aangegeven of de functies of onderdelen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="7ff34-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="7ff34-131">Stel deze eigenschap in op **presen teren** om ervoor te zorgen dat de functies of onderdelen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="7ff34-131">To ensure that the roles or features are added, set this property to **Present** .</span></span> <span data-ttu-id="7ff34-132">Om ervoor te zorgen dat de functies of onderdelen worden verwijderd, stelt u de eigenschap in op **afwezig** .</span><span class="sxs-lookup"><span data-stu-id="7ff34-132">To ensure that the roles or features are removed, set the property to **Absent** .</span></span> <span data-ttu-id="7ff34-133">De standaard waarde is **aanwezig** .</span><span class="sxs-lookup"><span data-stu-id="7ff34-133">The default value is **Present** .</span></span> |
|<span data-ttu-id="7ff34-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7ff34-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="7ff34-135">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="7ff34-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7ff34-136">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="7ff34-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7ff34-137">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7ff34-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="7ff34-138">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7ff34-138">Example</span></span>

<span data-ttu-id="7ff34-139">De volgende configuratie zorgt ervoor dat de functies van de **webserver** (IIS) en de **SMTP-server** , en alle subonderdelen van elke, worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7ff34-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
