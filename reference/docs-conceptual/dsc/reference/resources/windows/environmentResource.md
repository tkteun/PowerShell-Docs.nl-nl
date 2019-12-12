---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-omgevings resource
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942480"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="8ee16-103">DSC-omgevings resource</span><span class="sxs-lookup"><span data-stu-id="8ee16-103">DSC Environment Resource</span></span>

> <span data-ttu-id="8ee16-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="8ee16-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="8ee16-105">De **omgevings** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van systeem omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="8ee16-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="8ee16-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8ee16-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="8ee16-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8ee16-107">Properties</span></span>

|<span data-ttu-id="8ee16-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8ee16-108">Property</span></span> |<span data-ttu-id="8ee16-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8ee16-109">Description</span></span> |
|---|---|
|<span data-ttu-id="8ee16-110">Naam</span><span class="sxs-lookup"><span data-stu-id="8ee16-110">Name</span></span> |<span data-ttu-id="8ee16-111">Hiermee wordt de naam van de omgevings variabele opgegeven waarvoor u een specifieke status wilt waarborgen.</span><span class="sxs-lookup"><span data-stu-id="8ee16-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="8ee16-112">Pad</span><span class="sxs-lookup"><span data-stu-id="8ee16-112">Path</span></span> |<span data-ttu-id="8ee16-113">Hiermee definieert u de omgevings variabele die wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="8ee16-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="8ee16-114">Stel deze eigenschap in op `$true` **als de variabele een padvariabele** is; Stel deze in andere gevallen in op `$false`.</span><span class="sxs-lookup"><span data-stu-id="8ee16-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="8ee16-115">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="8ee16-115">The default is `$false`.</span></span> <span data-ttu-id="8ee16-116">Als **de variabele die wordt geconfigureerd de padvariabele** is, wordt de waarde die is opgegeven via de eigenschap **Value** , aan de bestaande waarde toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="8ee16-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="8ee16-117">Value</span><span class="sxs-lookup"><span data-stu-id="8ee16-117">Value</span></span> |<span data-ttu-id="8ee16-118">De waarde die moet worden toegewezen aan de omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="8ee16-118">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="8ee16-119">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8ee16-119">Common properties</span></span>

|<span data-ttu-id="8ee16-120">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8ee16-120">Property</span></span> |<span data-ttu-id="8ee16-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8ee16-121">Description</span></span> |
|---|---|
|<span data-ttu-id="8ee16-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8ee16-122">DependsOn</span></span> |<span data-ttu-id="8ee16-123">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="8ee16-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8ee16-124">Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8ee16-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="8ee16-125">Zo</span><span class="sxs-lookup"><span data-stu-id="8ee16-125">Ensure</span></span> |<span data-ttu-id="8ee16-126">Hiermee wordt aangegeven of een variabele bestaat.</span><span class="sxs-lookup"><span data-stu-id="8ee16-126">Indicates if a variable exists.</span></span> <span data-ttu-id="8ee16-127">Stel deze eigenschap in op **presen teren** om de omgevings variabele te maken als deze niet bestaat of om ervoor te zorgen dat de waarde overeenkomt met wat is opgegeven via de eigenschap **Value** als de variabele al bestaat.</span><span class="sxs-lookup"><span data-stu-id="8ee16-127">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="8ee16-128">Stel deze in op **afwezig** om de variabele te verwijderen als deze bestaat.</span><span class="sxs-lookup"><span data-stu-id="8ee16-128">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="8ee16-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="8ee16-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="8ee16-130">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="8ee16-130">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="8ee16-131">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="8ee16-131">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="8ee16-132">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ee16-132">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="8ee16-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8ee16-133">Example</span></span>

<span data-ttu-id="8ee16-134">In het volgende voor beeld wordt ervoor gezorgd dat TestEnvironmentVariable aanwezig is en de waarde _TestValue_heeft.</span><span class="sxs-lookup"><span data-stu-id="8ee16-134">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="8ee16-135">Als deze niet aanwezig is, wordt deze gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8ee16-135">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```