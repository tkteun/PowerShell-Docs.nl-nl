---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-register resource
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941332"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="aec47-103">DSC-register resource</span><span class="sxs-lookup"><span data-stu-id="aec47-103">DSC Registry Resource</span></span>

> <span data-ttu-id="aec47-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="aec47-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="aec47-105">De **register** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van register sleutels en-waarden op een doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="aec47-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="aec47-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="aec47-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="aec47-107">properties</span><span class="sxs-lookup"><span data-stu-id="aec47-107">Properties</span></span>

|<span data-ttu-id="aec47-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="aec47-108">Property</span></span> |<span data-ttu-id="aec47-109">Description</span><span class="sxs-lookup"><span data-stu-id="aec47-109">Description</span></span> |
|---|---|
|<span data-ttu-id="aec47-110">Sleutel</span><span class="sxs-lookup"><span data-stu-id="aec47-110">Key</span></span> |<span data-ttu-id="aec47-111">Hiermee geeft u het pad van de register sleutel op waarvan u een specifieke status wilt waarborgen.</span><span class="sxs-lookup"><span data-stu-id="aec47-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="aec47-112">Dit pad moet de Hive bevatten.</span><span class="sxs-lookup"><span data-stu-id="aec47-112">This path must include the hive.</span></span> |
|<span data-ttu-id="aec47-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="aec47-113">ValueName</span></span> |<span data-ttu-id="aec47-114">Hiermee wordt de naam van de register waarde aangegeven.</span><span class="sxs-lookup"><span data-stu-id="aec47-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="aec47-115">Als u een register sleutel wilt toevoegen of verwijderen, geeft u deze eigenschap op als een lege teken reeks zonder **Value type** of **ValueData**op te geven.</span><span class="sxs-lookup"><span data-stu-id="aec47-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData**.</span></span> <span data-ttu-id="aec47-116">Als u de standaard waarde van een register sleutel wilt wijzigen of verwijderen, geeft u deze eigenschap op als een lege teken reeks terwijl u ook **Value type** of **ValueData**opgeeft.</span><span class="sxs-lookup"><span data-stu-id="aec47-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData**.</span></span> |
|<span data-ttu-id="aec47-117">Force</span><span class="sxs-lookup"><span data-stu-id="aec47-117">Force</span></span> |<span data-ttu-id="aec47-118">Als de opgegeven register sleutel aanwezig is, wordt deze door **geforceerd** overschreven met de nieuwe waarde.</span><span class="sxs-lookup"><span data-stu-id="aec47-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="aec47-119">Als u een register sleutel met subsleutels verwijdert, moet dit `$true`zijn.</span><span class="sxs-lookup"><span data-stu-id="aec47-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="aec47-120">Bovenaanzicht</span><span class="sxs-lookup"><span data-stu-id="aec47-120">Hex</span></span> |<span data-ttu-id="aec47-121">Hiermee wordt aangegeven of gegevens in hexadecimale indeling worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aec47-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="aec47-122">Indien opgegeven, worden de DWORD/QWORD-waardegegevens weer gegeven in hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="aec47-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="aec47-123">Niet geldig voor andere typen.</span><span class="sxs-lookup"><span data-stu-id="aec47-123">Not valid for other types.</span></span> <span data-ttu-id="aec47-124">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="aec47-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="aec47-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="aec47-125">ValueData</span></span> |<span data-ttu-id="aec47-126">De gegevens voor de register waarde.</span><span class="sxs-lookup"><span data-stu-id="aec47-126">The data for the registry value.</span></span> |
|<span data-ttu-id="aec47-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="aec47-127">ValueType</span></span> |<span data-ttu-id="aec47-128">Hiermee wordt het type van de waarde aangegeven.</span><span class="sxs-lookup"><span data-stu-id="aec47-128">Indicates the type of the value.</span></span> <span data-ttu-id="aec47-129">De ondersteunde typen zijn: **Teken reeks** (REG_SZ), **binair** (REG-BINARY), **DWORD** (32-bits REG_DWORD), **Qword** (64-bits REG_QWORD), **multistring** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span><span class="sxs-lookup"><span data-stu-id="aec47-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="aec47-130">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="aec47-130">Common properties</span></span>

|<span data-ttu-id="aec47-131">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="aec47-131">Property</span></span> |<span data-ttu-id="aec47-132">Description</span><span class="sxs-lookup"><span data-stu-id="aec47-132">Description</span></span> |
|---|---|
|<span data-ttu-id="aec47-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aec47-133">DependsOn</span></span> |<span data-ttu-id="aec47-134">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="aec47-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aec47-135">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="aec47-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="aec47-136">Zo</span><span class="sxs-lookup"><span data-stu-id="aec47-136">Ensure</span></span> |<span data-ttu-id="aec47-137">Hiermee wordt aangegeven of de sleutel en de waarde bestaan.</span><span class="sxs-lookup"><span data-stu-id="aec47-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="aec47-138">Stel deze eigenschap in op **presen teren**om ervoor te zorgen dat ze wel aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="aec47-138">To ensure that they do, set this property to **Present**.</span></span> <span data-ttu-id="aec47-139">Om ervoor te zorgen dat ze niet bestaan, stelt u de eigenschap in op **afwezig**.</span><span class="sxs-lookup"><span data-stu-id="aec47-139">To ensure that they do not exist, set the property to **Absent**.</span></span> <span data-ttu-id="aec47-140">De standaard waarde is **aanwezig**.</span><span class="sxs-lookup"><span data-stu-id="aec47-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="aec47-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="aec47-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="aec47-142">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="aec47-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="aec47-143">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="aec47-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="aec47-144">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aec47-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="aec47-145">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="aec47-145">Example</span></span>

<span data-ttu-id="aec47-146">In dit voor beeld wordt ervoor gezorgd dat een sleutel met de naam ' ExampleKey ' aanwezig is in de **lokale\_\_machine** -component HKEY.</span><span class="sxs-lookup"><span data-stu-id="aec47-146">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="aec47-147">Als u een register instelling in `HKEY_CURRENT_USER` het onderdeel wilt wijzigen, moet de configuratie worden uitgevoerd met gebruikers referenties in plaats van als het systeem.</span><span class="sxs-lookup"><span data-stu-id="aec47-147">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="aec47-148">U kunt de eigenschap **PsDscRunAsCredential** gebruiken om gebruikers referenties op te geven voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="aec47-148">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="aec47-149">Zie [DSC uitvoeren met gebruikers referenties](../../../configurations/runAsUser.md)voor een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="aec47-149">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>