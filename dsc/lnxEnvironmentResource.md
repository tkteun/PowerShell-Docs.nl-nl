---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxEnvironment Resource
ms.openlocfilehash: 3c9f39760e0fba7fac060f29f9e808a3a434401f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189479"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="6b656-103">DSC voor Linux nxEnvironment Resource</span><span class="sxs-lookup"><span data-stu-id="6b656-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="6b656-104">De **nxEnvironment** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme op voor het beheren van omgevingsvariabelen op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="6b656-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b656-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6b656-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="6b656-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="6b656-106">Properties</span></span>

|  <span data-ttu-id="6b656-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6b656-107">Property</span></span> |  <span data-ttu-id="6b656-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6b656-108">Description</span></span> |
|---|---|
| <span data-ttu-id="6b656-109">Naam</span><span class="sxs-lookup"><span data-stu-id="6b656-109">Name</span></span>| <span data-ttu-id="6b656-110">Geeft de naam van de omgevingsvariabele waarvoor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="6b656-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="6b656-111">Value</span><span class="sxs-lookup"><span data-stu-id="6b656-111">Value</span></span>| <span data-ttu-id="6b656-112">De waarde om toe te wijzen aan de omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="6b656-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="6b656-113">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="6b656-113">Ensure</span></span>| <span data-ttu-id="6b656-114">Bepaalt of Controleer of de variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="6b656-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="6b656-115">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="6b656-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="6b656-116">Stel deze in op 'Ontbreekt' om te controleren of dat de variabele bestaat niet.</span><span class="sxs-lookup"><span data-stu-id="6b656-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="6b656-117">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="6b656-117">The default value is "Present".</span></span>|
| <span data-ttu-id="6b656-118">Pad</span><span class="sxs-lookup"><span data-stu-id="6b656-118">Path</span></span>| <span data-ttu-id="6b656-119">Hiermee definieert u de variabele die wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="6b656-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="6b656-120">Deze eigenschap instellen op **$true** als de variabele de **pad** variabele, anders wordt ingesteld op **$false**.</span><span class="sxs-lookup"><span data-stu-id="6b656-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="6b656-121">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="6b656-121">The default is **$false**.</span></span> <span data-ttu-id="6b656-122">Als de variabele die wordt geconfigureerd de **pad** variabele, de waarde wordt opgegeven via de **waarde** eigenschap worden toegevoegd aan de bestaande waarde.</span><span class="sxs-lookup"><span data-stu-id="6b656-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="6b656-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="6b656-123">DependsOn</span></span> | <span data-ttu-id="6b656-124">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="6b656-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6b656-125">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6b656-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="6b656-126">Als u meer informatie</span><span class="sxs-lookup"><span data-stu-id="6b656-126">Additional Information</span></span>

* <span data-ttu-id="6b656-127">Als **pad** ontbreekt of is ingesteld op **$false**, omgevingsvariabelen worden beheerd in `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="6b656-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="6b656-128">Uw programma's of scripts mogelijk configuratie bron vereist de `/etc/environment` bestand voor toegang tot de beheerde omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="6b656-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="6b656-129">Als **pad** is ingesteld op **$true**, de omgevingsvariabele wordt beheerd in het bestand `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="6b656-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="6b656-130">Dit bestand wordt gemaakt als deze niet bestaat.</span><span class="sxs-lookup"><span data-stu-id="6b656-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="6b656-131">Als **Zorg ervoor dat** is ingesteld op 'Afwezig' en **pad** is ingesteld op **$true**, een bestaande omgevingsvariabele wordt alleen verwijderd uit `/etc/profile.d/DSCenvironment.sh` en niet vanuit andere bestanden.</span><span class="sxs-lookup"><span data-stu-id="6b656-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="6b656-132">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6b656-132">Example</span></span>

<span data-ttu-id="6b656-133">Het volgende voorbeeld ziet u hoe u de **nxEnvironment** resource ervoor te zorgen dat **TestEnvironmentVariable** aanwezig is en de waarde 'Test-waarde'.</span><span class="sxs-lookup"><span data-stu-id="6b656-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="6b656-134">Als **TestEnvironmentVariable** is niet aanwezig is, wordt deze gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6b656-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```