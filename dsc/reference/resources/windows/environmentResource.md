---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Omgevingsresource
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077531"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="38817-103">DSC-Omgevingsresource</span><span class="sxs-lookup"><span data-stu-id="38817-103">DSC Environment Resource</span></span>

> <span data-ttu-id="38817-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="38817-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="38817-105">De __omgeving__ resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="38817-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="38817-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="38817-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="38817-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="38817-107">Properties</span></span>

|  <span data-ttu-id="38817-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="38817-108">Property</span></span>  |  <span data-ttu-id="38817-109">Description</span><span class="sxs-lookup"><span data-stu-id="38817-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="38817-110">Naam</span><span class="sxs-lookup"><span data-stu-id="38817-110">Name</span></span>| <span data-ttu-id="38817-111">Geeft de naam van de omgevingsvariabele waarvoor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="38817-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="38817-112">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="38817-112">Ensure</span></span>| <span data-ttu-id="38817-113">Geeft aan dat er een variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="38817-113">Indicates if a variable exists.</span></span> <span data-ttu-id="38817-114">Deze eigenschap instellen op __aanwezig__ te maken van de omgevingsvariabele als deze niet bestaat of om ervoor te zorgen dat de waarde ervan overeenkomt met wat wordt geboden via de __waarde__ eigenschap als de variabele al bestaat.</span><span class="sxs-lookup"><span data-stu-id="38817-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="38817-115">Stel deze in op __afwezig__ verwijderen van de variabele als deze bestaat.</span><span class="sxs-lookup"><span data-stu-id="38817-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="38817-116">Pad</span><span class="sxs-lookup"><span data-stu-id="38817-116">Path</span></span>| <span data-ttu-id="38817-117">Hiermee definieert u de omgevingsvariabele die wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="38817-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="38817-118">Deze eigenschap instellen op __$true__ als de variabele de __pad__ variabele, anders wordt deze ingesteld op __$false__.</span><span class="sxs-lookup"><span data-stu-id="38817-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="38817-119">De standaardwaarde is __$false__.</span><span class="sxs-lookup"><span data-stu-id="38817-119">The default is __$false__.</span></span> <span data-ttu-id="38817-120">Als de variabele die wordt geconfigureerd is de __pad__ variabele, de waarde wordt opgegeven via de __waarde__ eigenschap toegevoegd aan de bestaande waarde.</span><span class="sxs-lookup"><span data-stu-id="38817-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="38817-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="38817-121">DependsOn</span></span> | <span data-ttu-id="38817-122">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="38817-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="38817-123">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="38817-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="38817-124">Waarde</span><span class="sxs-lookup"><span data-stu-id="38817-124">Value</span></span>| <span data-ttu-id="38817-125">De waarde om toe te wijzen aan de omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="38817-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="38817-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="38817-126">Example</span></span>

<span data-ttu-id="38817-127">Het volgende voorbeeld zorgt ervoor dat __TestEnvironmentVariable__ aanwezig is en heeft de waarde __testwaarde__.</span><span class="sxs-lookup"><span data-stu-id="38817-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="38817-128">Als dit niet aanwezig is, maakt deze.</span><span class="sxs-lookup"><span data-stu-id="38817-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```