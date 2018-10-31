---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxEnvironment-Resource
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225978"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="f8e30-103">DSC voor Linux nxEnvironment-Resource</span><span class="sxs-lookup"><span data-stu-id="f8e30-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="f8e30-104">De **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van omgevingsvariabelen op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="f8e30-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8e30-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f8e30-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="f8e30-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="f8e30-106">Properties</span></span>

|  <span data-ttu-id="f8e30-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="f8e30-107">Property</span></span> |  <span data-ttu-id="f8e30-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f8e30-108">Description</span></span> |
|---|---|
| <span data-ttu-id="f8e30-109">Naam</span><span class="sxs-lookup"><span data-stu-id="f8e30-109">Name</span></span>| <span data-ttu-id="f8e30-110">Geeft de naam van de omgevingsvariabele waarvoor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="f8e30-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="f8e30-111">Value</span><span class="sxs-lookup"><span data-stu-id="f8e30-111">Value</span></span>| <span data-ttu-id="f8e30-112">De waarde om toe te wijzen aan de omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="f8e30-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="f8e30-113">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="f8e30-113">Ensure</span></span>| <span data-ttu-id="f8e30-114">Hiermee bepaalt u of om te controleren of de variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="f8e30-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="f8e30-115">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="f8e30-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="f8e30-116">Stel deze in op 'Ontbreekt' om te controleren of dat de variabele niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="f8e30-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="f8e30-117">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="f8e30-117">The default value is "Present".</span></span>|
| <span data-ttu-id="f8e30-118">Pad</span><span class="sxs-lookup"><span data-stu-id="f8e30-118">Path</span></span>| <span data-ttu-id="f8e30-119">Hiermee definieert u de omgevingsvariabele die wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="f8e30-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="f8e30-120">Deze eigenschap instellen op **$true** als de variabele de **pad** variabele, anders wordt deze ingesteld op **$false**.</span><span class="sxs-lookup"><span data-stu-id="f8e30-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="f8e30-121">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="f8e30-121">The default is **$false**.</span></span> <span data-ttu-id="f8e30-122">Als de variabele die wordt geconfigureerd is de **pad** variabele, de waarde wordt opgegeven via de **waarde** eigenschap toegevoegd aan de bestaande waarde.</span><span class="sxs-lookup"><span data-stu-id="f8e30-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="f8e30-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f8e30-123">DependsOn</span></span> | <span data-ttu-id="f8e30-124">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="f8e30-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f8e30-125">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f8e30-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="f8e30-126">Als u meer informatie</span><span class="sxs-lookup"><span data-stu-id="f8e30-126">Additional Information</span></span>

* <span data-ttu-id="f8e30-127">Als **pad** ontbreekt of is ingesteld op **$false**, omgevingsvariabelen worden beheerd in `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="f8e30-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="f8e30-128">Uw programma's of scripts mogelijk configuratie vereist voor bron de `/etc/environment` bestand voor toegang tot de beheerde omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="f8e30-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="f8e30-129">Als **pad** is ingesteld op **$true**, de omgevingsvariabele wordt beheerd in het bestand `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="f8e30-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="f8e30-130">Als deze niet bestaat, wordt dit bestand worden aangemaakt.</span><span class="sxs-lookup"><span data-stu-id="f8e30-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="f8e30-131">Als **Zorg ervoor dat** is ingesteld op 'Ontbreekt' en **pad** is ingesteld op **$true**, een bestaande omgevingsvariabele wordt alleen verwijderd uit `/etc/profile.d/DSCenvironment.sh` en niet vanuit andere bestanden.</span><span class="sxs-lookup"><span data-stu-id="f8e30-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="f8e30-132">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f8e30-132">Example</span></span>

<span data-ttu-id="f8e30-133">Het volgende voorbeeld ziet u hoe u de **nxEnvironment** resource om ervoor te zorgen dat **TestEnvironmentVariable** aanwezig is en de waarde 'Test-waarde'.</span><span class="sxs-lookup"><span data-stu-id="f8e30-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="f8e30-134">Als **TestEnvironmentVariable** is niet aanwezig is, wordt deze gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f8e30-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```