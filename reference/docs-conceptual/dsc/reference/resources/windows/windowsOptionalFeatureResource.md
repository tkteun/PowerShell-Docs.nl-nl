---
ms.date: 08/28/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsOptionalFeature-resource
ms.openlocfilehash: f24173c1a9ed605bac43767a9da2d4dbded78883
ms.sourcegitcommit: 06b6f4012e4eca71d414733cdba23ef75535223c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/29/2020
ms.locfileid: "89093247"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="99de6-103">DSC WindowsOptionalFeature-resource</span><span class="sxs-lookup"><span data-stu-id="99de6-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="99de6-104">Van toepassing op: Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="99de6-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="99de6-105">De **WindowsOptionalFeature** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat optionele functies zijn ingeschakeld op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="99de6-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

> [!NOTE]
> <span data-ttu-id="99de6-106">**WindowsOptionalFeature** werkt alleen op Windows-client computers zoals Windows 10.</span><span class="sxs-lookup"><span data-stu-id="99de6-106">**WindowsOptionalFeature** only works on Windows client machines like Windows 10.</span></span>

## <a name="syntax"></a><span data-ttu-id="99de6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="99de6-107">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="99de6-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="99de6-108">Properties</span></span>

|<span data-ttu-id="99de6-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="99de6-109">Property</span></span> |<span data-ttu-id="99de6-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="99de6-110">Description</span></span> |
|---|---|
|<span data-ttu-id="99de6-111">Naam</span><span class="sxs-lookup"><span data-stu-id="99de6-111">Name</span></span> |<span data-ttu-id="99de6-112">Hiermee wordt de naam aangegeven van de functie die u wilt inschakelen, is ingeschakeld of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="99de6-112">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="99de6-113">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="99de6-113">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="99de6-114">Hiermee geeft u op of DISM-contact personen Windows Update (WU) bij het zoeken naar de bron bestanden om een functie in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="99de6-114">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="99de6-115">Als `$true` kan DISM geen contact opnemen met Wu.</span><span class="sxs-lookup"><span data-stu-id="99de6-115">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="99de6-116">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="99de6-116">RemoveFilesOnDisable</span></span> |<span data-ttu-id="99de6-117">Stel deze `$true` optie in om alle bestanden te verwijderen die zijn gekoppeld aan de functie als u **zeker weet dat** deze is ingesteld op **afwezig**.</span><span class="sxs-lookup"><span data-stu-id="99de6-117">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="99de6-118">Logniveau</span><span class="sxs-lookup"><span data-stu-id="99de6-118">LogLevel</span></span> |<span data-ttu-id="99de6-119">Het maximale uitvoer niveau dat wordt weer gegeven in de logboeken.</span><span class="sxs-lookup"><span data-stu-id="99de6-119">The maximum output level shown in the logs.</span></span> <span data-ttu-id="99de6-120">De geaccepteerde waarden zijn: **ErrorsOnly**, **ErrorsAndWarning**en **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="99de6-120">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="99de6-121">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="99de6-121">LogPath</span></span> |<span data-ttu-id="99de6-122">Het pad naar een logboek bestand waar de resource provider de bewerking moet registreren.</span><span class="sxs-lookup"><span data-stu-id="99de6-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="99de6-123">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="99de6-123">Common properties</span></span>

|<span data-ttu-id="99de6-124">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="99de6-124">Property</span></span> |<span data-ttu-id="99de6-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="99de6-125">Description</span></span> |
|---|---|
|<span data-ttu-id="99de6-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="99de6-126">DependsOn</span></span> |<span data-ttu-id="99de6-127">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="99de6-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="99de6-128">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="99de6-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="99de6-129">Zo</span><span class="sxs-lookup"><span data-stu-id="99de6-129">Ensure</span></span> |<span data-ttu-id="99de6-130">Hiermee wordt aangegeven of de functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="99de6-130">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="99de6-131">Stel deze eigenschap in op _inschakelen_om ervoor te zorgen dat de functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="99de6-131">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="99de6-132">Om ervoor te zorgen dat de functie is uitgeschakeld, stelt u de eigenschap in op _uitschakelen_.</span><span class="sxs-lookup"><span data-stu-id="99de6-132">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="99de6-133">De standaard waarde is _ingeschakeld_.</span><span class="sxs-lookup"><span data-stu-id="99de6-133">The default value is _Enable_.</span></span> |
|<span data-ttu-id="99de6-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="99de6-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="99de6-135">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="99de6-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="99de6-136">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="99de6-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="99de6-137">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="99de6-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
