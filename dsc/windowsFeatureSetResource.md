---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsFeatureSet Resource
ms.openlocfilehash: a6fecba0397b88ce39f6f1a1be6cc366c8a983a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="069d9-103">DSC-WindowsFeatureSet Resource</span><span class="sxs-lookup"><span data-stu-id="069d9-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="069d9-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="069d9-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="069d9-105">De **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat functies en onderdelen worden toegevoegd of verwijderd in een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="069d9-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="069d9-106">Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [WindowsFeature resource](windowsfeatureResource.md) voor elke functie die is opgegeven in de `Name` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="069d9-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="069d9-107">Gebruik deze bron als u wilt configureren, een aantal functies van Windows naar dezelfde toestand.</span><span class="sxs-lookup"><span data-stu-id="069d9-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="069d9-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="069d9-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="069d9-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="069d9-109">Properties</span></span>

|  <span data-ttu-id="069d9-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="069d9-110">Property</span></span>  |  <span data-ttu-id="069d9-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="069d9-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="069d9-112">Naam</span><span class="sxs-lookup"><span data-stu-id="069d9-112">Name</span></span>| <span data-ttu-id="069d9-113">De namen van de functies of onderdelen die u wilt zorgen worden toegevoegd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="069d9-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="069d9-114">Dit is hetzelfde als de **naam** eigenschap van de [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, en niet de weergavenaam van de functies of onderdelen.</span><span class="sxs-lookup"><span data-stu-id="069d9-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="069d9-115">referentie</span><span class="sxs-lookup"><span data-stu-id="069d9-115">Credential</span></span>| <span data-ttu-id="069d9-116">De referenties toevoegen of verwijderen van de functies of onderdelen.</span><span class="sxs-lookup"><span data-stu-id="069d9-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="069d9-117">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="069d9-117">Ensure</span></span>| <span data-ttu-id="069d9-118">Hiermee wordt aangegeven of de functies of onderdelen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="069d9-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="069d9-119">Om ervoor te zorgen dat de functies of onderdelen zijn toegevoegd, stel deze eigenschap in op 'Aanwezig' om ervoor te zorgen dat de functies of onderdelen zijn verwijderd, de eigenschap instellen op 'Afwezig'.</span><span class="sxs-lookup"><span data-stu-id="069d9-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="069d9-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="069d9-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="069d9-121">Deze eigenschap instellen op **$true** om op te nemen van alle vereiste subonderdelen met van de functies die u met opgeeft de **naam** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="069d9-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="069d9-122">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="069d9-122">LogPath</span></span>| <span data-ttu-id="069d9-123">Het pad naar een logboekbestand waar u de resourceprovider aan te melden van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="069d9-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="069d9-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="069d9-124">DependsOn</span></span>| <span data-ttu-id="069d9-125">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="069d9-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="069d9-126">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="069d9-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="069d9-127">Bron</span><span class="sxs-lookup"><span data-stu-id="069d9-127">Source</span></span>| <span data-ttu-id="069d9-128">Geeft de locatie van het bronbestand moet worden gebruikt voor de installatie, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="069d9-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="069d9-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="069d9-129">Example</span></span>

<span data-ttu-id="069d9-130">De volgende configuratie zorgt ervoor dat de **webserver** (IIS) en **SMTP-Server** functies en alle subfuncties van elke, worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="069d9-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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