---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WindowsOptionalFeatureSet-Resource
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683945"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="1efbb-103">DSC WindowsOptionalFeatureSet-Resource</span><span class="sxs-lookup"><span data-stu-id="1efbb-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="1efbb-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1efbb-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1efbb-105">De **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat de optionele functies zijn ingeschakeld op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="1efbb-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="1efbb-106">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die roept de [WindowsOptionalFeature-resource](windowsOptionalFeatureResource.md) voor elke functie die is opgegeven in de `Name` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1efbb-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="1efbb-107">Gebruik deze resource als u wilt configureren van een aantal optionele functies van Windows naar dezelfde toestand.</span><span class="sxs-lookup"><span data-stu-id="1efbb-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="1efbb-108">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1efbb-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="1efbb-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="1efbb-109">Properties</span></span>

|  <span data-ttu-id="1efbb-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="1efbb-110">Property</span></span>  |  <span data-ttu-id="1efbb-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1efbb-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="1efbb-112">Naam</span><span class="sxs-lookup"><span data-stu-id="1efbb-112">Name</span></span>| <span data-ttu-id="1efbb-113">Geeft aan dat de naam van de functies die u wilt ervoor zorgen zijn ingeschakeld of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="1efbb-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="1efbb-114">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="1efbb-114">Ensure</span></span>| <span data-ttu-id="1efbb-115">Hiermee geeft u op of de functies zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="1efbb-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="1efbb-116">Om ervoor te zorgen dat de functies zijn ingeschakeld en stel deze eigenschap in op 'Inschakelen' om ervoor te zorgen dat de functies zijn uitgeschakeld, de eigenschap instellen op 'Uitschakelen'.</span><span class="sxs-lookup"><span data-stu-id="1efbb-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="1efbb-117">Bron</span><span class="sxs-lookup"><span data-stu-id="1efbb-117">Source</span></span>| <span data-ttu-id="1efbb-118">Niet geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="1efbb-118">Not implemented.</span></span>|
| <span data-ttu-id="1efbb-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="1efbb-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="1efbb-120">Hiermee geeft u op of DISM neemt contact op met Windows Update (WU) bij het zoeken naar de bronbestanden voor de functies inschakelen.</span><span class="sxs-lookup"><span data-stu-id="1efbb-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="1efbb-121">Als $true, DISM geen contact opnemen met WU.</span><span class="sxs-lookup"><span data-stu-id="1efbb-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="1efbb-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="1efbb-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="1efbb-123">Ingesteld op **$true** te verwijderen van alle bestanden die zijn gekoppeld aan de functies wanneer ze worden uitgeschakeld (dat wil zeggen, wanneer **Zorg ervoor dat** is ingesteld op 'Ontbreekt').</span><span class="sxs-lookup"><span data-stu-id="1efbb-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="1efbb-124">Logniveau</span><span class="sxs-lookup"><span data-stu-id="1efbb-124">LogLevel</span></span>| <span data-ttu-id="1efbb-125">Het maximale uitvoerniveau op dat wordt weergegeven in de logboeken.</span><span class="sxs-lookup"><span data-stu-id="1efbb-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="1efbb-126">De toegestane waarden zijn: "ErrorsOnly' (alleen fouten worden vastgelegd), 'ErrorsAndWarning' (fouten en waarschuwingen worden geregistreerd), en 'ErrorsAndWarningAndInformation' (fouten, waarschuwingen en gegevens voor foutopsporing worden geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="1efbb-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="1efbb-127">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="1efbb-127">LogPath</span></span>| <span data-ttu-id="1efbb-128">Het pad naar een logboekbestand waar u de resourceprovider voor aanmelding van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="1efbb-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="1efbb-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1efbb-129">DependsOn</span></span>| <span data-ttu-id="1efbb-130">Hiermee geeft u op dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="1efbb-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1efbb-131">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1efbb-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
