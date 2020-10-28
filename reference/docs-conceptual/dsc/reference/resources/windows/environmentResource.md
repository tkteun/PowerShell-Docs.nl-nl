---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-omgevings resource
description: DSC-omgevings resource
ms.openlocfilehash: c114aef76ef8308fa2805c18ab885d67b44d2b2b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650543"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="b7340-103">DSC-omgevings resource</span><span class="sxs-lookup"><span data-stu-id="b7340-103">DSC Environment Resource</span></span>

> <span data-ttu-id="b7340-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="b7340-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="b7340-105">De **omgevings** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van systeem omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="b7340-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7340-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7340-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Target = [string] { Process | Machine } ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="b7340-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="b7340-107">Properties</span></span>

|<span data-ttu-id="b7340-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b7340-108">Property</span></span> |<span data-ttu-id="b7340-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b7340-109">Description</span></span> |
|---|---|
|<span data-ttu-id="b7340-110">Naam</span><span class="sxs-lookup"><span data-stu-id="b7340-110">Name</span></span> |<span data-ttu-id="b7340-111">Hiermee wordt de naam van de omgevings variabele opgegeven waarvoor u een specifieke status wilt waarborgen.</span><span class="sxs-lookup"><span data-stu-id="b7340-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="b7340-112">Pad</span><span class="sxs-lookup"><span data-stu-id="b7340-112">Path</span></span> |<span data-ttu-id="b7340-113">Hiermee definieert u de omgevings variabele die wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="b7340-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="b7340-114">Stel deze eigenschap in op `$true` als de variabele een **padvariabele** is. anders stelt u deze in op `$false` .</span><span class="sxs-lookup"><span data-stu-id="b7340-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="b7340-115">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="b7340-115">The default is `$false`.</span></span> <span data-ttu-id="b7340-116">Als **de variabele die wordt geconfigureerd de padvariabele** is, wordt de waarde die is opgegeven via de eigenschap **Value** , aan de bestaande waarde toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b7340-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="b7340-117">Doel</span><span class="sxs-lookup"><span data-stu-id="b7340-117">Target</span></span>| <span data-ttu-id="b7340-118">Hiermee wordt aangegeven waar de variabele moet worden opgehaald: de computer of het proces.</span><span class="sxs-lookup"><span data-stu-id="b7340-118">Indicates where to retrieve the variable: The machine or the process.</span></span> <span data-ttu-id="b7340-119">Als beide worden aangegeven, wordt alleen de waarde van de computer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b7340-119">If both are indicated then only the value from the machine is returned.</span></span> <span data-ttu-id="b7340-120">De standaard waarde is beide, omdat dit de standaard waarde is voor de rest van de resource.</span><span class="sxs-lookup"><span data-stu-id="b7340-120">The default is both since that is the default for the rest of the resource.</span></span> |
|<span data-ttu-id="b7340-121">Waarde</span><span class="sxs-lookup"><span data-stu-id="b7340-121">Value</span></span> |<span data-ttu-id="b7340-122">De waarde die moet worden toegewezen aan de omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="b7340-122">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b7340-123">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="b7340-123">Common properties</span></span>

|<span data-ttu-id="b7340-124">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b7340-124">Property</span></span> |<span data-ttu-id="b7340-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b7340-125">Description</span></span> |
|---|---|
|<span data-ttu-id="b7340-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b7340-126">DependsOn</span></span> |<span data-ttu-id="b7340-127">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="b7340-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b7340-128">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="b7340-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b7340-129">Zo</span><span class="sxs-lookup"><span data-stu-id="b7340-129">Ensure</span></span> |<span data-ttu-id="b7340-130">Hiermee wordt aangegeven of een variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="b7340-130">Indicates if a variable exists.</span></span> <span data-ttu-id="b7340-131">Stel deze eigenschap in op **presen teren** om de omgevings variabele te maken als deze niet bestaat of om ervoor te zorgen dat de waarde overeenkomt met wat is opgegeven via de eigenschap **Value** als de variabele al bestaat.</span><span class="sxs-lookup"><span data-stu-id="b7340-131">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="b7340-132">Stel deze in op **afwezig** om de variabele te verwijderen als deze bestaat.</span><span class="sxs-lookup"><span data-stu-id="b7340-132">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="b7340-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b7340-133">PsDscRunAsCredential</span></span> |<span data-ttu-id="b7340-134">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="b7340-134">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="b7340-135">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="b7340-135">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="b7340-136">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b7340-136">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="b7340-137">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b7340-137">Example</span></span>

<span data-ttu-id="b7340-138">In het volgende voor beeld wordt ervoor gezorgd dat TestEnvironmentVariable aanwezig is en de waarde _TestValue_ heeft.</span><span class="sxs-lookup"><span data-stu-id="b7340-138">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_ .</span></span> <span data-ttu-id="b7340-139">Als deze niet aanwezig is, wordt deze gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b7340-139">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
