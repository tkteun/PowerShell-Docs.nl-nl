---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-Resource voor register
ms.openlocfilehash: 649cb60578c053c04a7fcc7446881fb76daee26a
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="651b3-103">DSC-Resource voor register</span><span class="sxs-lookup"><span data-stu-id="651b3-103">DSC Registry Resource</span></span>

> <span data-ttu-id="651b3-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="651b3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="651b3-105">De **register** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van registersleutels en -waarden in een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="651b3-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="651b3-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="651b3-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="651b3-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="651b3-107">Properties</span></span>
|  <span data-ttu-id="651b3-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="651b3-108">Property</span></span>  |  <span data-ttu-id="651b3-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="651b3-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="651b3-110">Toets</span><span class="sxs-lookup"><span data-stu-id="651b3-110">Key</span></span>| <span data-ttu-id="651b3-111">Geeft het pad van de registersleutel waarvoor u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="651b3-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="651b3-112">Dit pad moet de component bevatten.</span><span class="sxs-lookup"><span data-stu-id="651b3-112">This path must include the hive.</span></span>| 
| <span data-ttu-id="651b3-113">Waardenaam</span><span class="sxs-lookup"><span data-stu-id="651b3-113">ValueName</span></span>| <span data-ttu-id="651b3-114">Geeft de naam van de registerwaarde.</span><span class="sxs-lookup"><span data-stu-id="651b3-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="651b3-115">Als u wilt toevoegen of verwijderen van een registersleutel, moet u deze eigenschap opgeven als een lege tekenreeks zonder ValueType of Waardegegevens te geven.</span><span class="sxs-lookup"><span data-stu-id="651b3-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="651b3-116">Als u wilt wijzigen of verwijderen van de standaardwaarde van een registersleutel, moet u deze eigenschap opgeven als een lege tekenreeks ook specificeren ValueType of Waardegegevens.</span><span class="sxs-lookup"><span data-stu-id="651b3-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>| 
| <span data-ttu-id="651b3-117">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="651b3-117">Ensure</span></span>| <span data-ttu-id="651b3-118">Hiermee wordt aangegeven als de sleutel en waarde bestaan.</span><span class="sxs-lookup"><span data-stu-id="651b3-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="651b3-119">Om ervoor te zorgen dat ze doen, stel deze eigenschap in op 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="651b3-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="651b3-120">Om ervoor te zorgen dat ze niet bestaat, de eigenschap instellen op 'Afwezig'.</span><span class="sxs-lookup"><span data-stu-id="651b3-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="651b3-121">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="651b3-121">The default value is "Present".</span></span>| 
| <span data-ttu-id="651b3-122">Force</span><span class="sxs-lookup"><span data-stu-id="651b3-122">Force</span></span>| <span data-ttu-id="651b3-123">Als de opgegeven registersleutel aanwezig is, __Force__ overschreven met de nieuwe waarde.</span><span class="sxs-lookup"><span data-stu-id="651b3-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="651b3-124">Als een registersleutel met subsleutels verwijdert, moet dit __$true__</span><span class="sxs-lookup"><span data-stu-id="651b3-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>| 
| <span data-ttu-id="651b3-125">Hex</span><span class="sxs-lookup"><span data-stu-id="651b3-125">Hex</span></span>| <span data-ttu-id="651b3-126">Hiermee wordt aangegeven als gegevens zullen worden uitgedrukt in hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="651b3-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="651b3-127">Als u opgeeft, wordt de waardegegevens DWORD/QWORD is opgenomen in hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="651b3-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="651b3-128">Niet geldig voor andere typen.</span><span class="sxs-lookup"><span data-stu-id="651b3-128">Not valid for other types.</span></span> <span data-ttu-id="651b3-129">De standaardwaarde is __$false__.</span><span class="sxs-lookup"><span data-stu-id="651b3-129">The default value is __$false__.</span></span>| 
| <span data-ttu-id="651b3-130">dependsOn</span><span class="sxs-lookup"><span data-stu-id="651b3-130">DependsOn</span></span>| <span data-ttu-id="651b3-131">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="651b3-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="651b3-132">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="651b3-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="651b3-133">Waardegegevens</span><span class="sxs-lookup"><span data-stu-id="651b3-133">ValueData</span></span>| <span data-ttu-id="651b3-134">De gegevens voor de registerwaarde.</span><span class="sxs-lookup"><span data-stu-id="651b3-134">The data for the registry value.</span></span>| 
| <span data-ttu-id="651b3-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="651b3-135">ValueType</span></span>| <span data-ttu-id="651b3-136">Geeft het type van de waarde.</span><span class="sxs-lookup"><span data-stu-id="651b3-136">Indicates the type of the value.</span></span> <span data-ttu-id="651b3-137">De ondersteunde typen zijn:</span><span class="sxs-lookup"><span data-stu-id="651b3-137">The supported types are:</span></span> 
<ul><li><span data-ttu-id="651b3-138">Tekenreeks (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="651b3-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="651b3-139">Binair (REG-BINARY)</span><span class="sxs-lookup"><span data-stu-id="651b3-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="651b3-140">DWORD 32-bits (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="651b3-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="651b3-141">Qword 64-bits (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="651b3-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="651b3-142">Met meerdere tekenreeksen (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="651b3-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="651b3-143">Uit te breiden tekenreeks (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="651b3-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="651b3-144">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="651b3-144">Example</span></span>
<span data-ttu-id="651b3-145">In dit voorbeeld zorgt ervoor dat een sleutel met de naam 'ExampleKey' aanwezig is in de **HKEY\_lokale\_MACHINE** hive.</span><span class="sxs-lookup"><span data-stu-id="651b3-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
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

><span data-ttu-id="651b3-146">**Opmerking:** aanbrengen in een registerinstelling in de **HKEY\_huidige\_gebruiker** hive vereist dat de configuratie wordt uitgevoerd met gebruikersgegevens, in plaats van als het systeem.</span><span class="sxs-lookup"><span data-stu-id="651b3-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="651b3-147">U kunt de **PsDscRunAsCredential** eigenschap gebruikersreferenties voor de configuratie opgeven.</span><span class="sxs-lookup"><span data-stu-id="651b3-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="651b3-148">Zie voor een voorbeeld [DSC uitgevoerd met gebruikersgegevens](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="651b3-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>



