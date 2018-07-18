---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Registerresource
ms.openlocfilehash: b77710d7a6fc599949e78c17af309ad88a1a0872
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093582"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="01102-103">DSC-Registerresource</span><span class="sxs-lookup"><span data-stu-id="01102-103">DSC Registry Resource</span></span>

> <span data-ttu-id="01102-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="01102-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="01102-105">De **register** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van registersleutels en -waarden op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="01102-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="01102-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="01102-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="01102-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="01102-107">Properties</span></span>

|  <span data-ttu-id="01102-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="01102-108">Property</span></span>  |  <span data-ttu-id="01102-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="01102-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="01102-110">Toets</span><span class="sxs-lookup"><span data-stu-id="01102-110">Key</span></span>| <span data-ttu-id="01102-111">Geeft het pad van de registersleutel die u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="01102-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="01102-112">Dit pad moet de component bevatten.</span><span class="sxs-lookup"><span data-stu-id="01102-112">This path must include the hive.</span></span>|
| <span data-ttu-id="01102-113">Waardenaam</span><span class="sxs-lookup"><span data-stu-id="01102-113">ValueName</span></span>| <span data-ttu-id="01102-114">Geeft de naam van de registerwaarde.</span><span class="sxs-lookup"><span data-stu-id="01102-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="01102-115">Als u wilt toevoegen of verwijderen van een registersleutel, moet u deze eigenschap opgeven als een lege tekenreeks zonder ValueType of Waardegegevens op te geven.</span><span class="sxs-lookup"><span data-stu-id="01102-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="01102-116">Als u wilt wijzigen of verwijderen van de standaardwaarde van een registersleutel, moet u deze eigenschap opgeven als een lege tekenreeks tijdens het instellen van ook ValueType of Waardegegevens.</span><span class="sxs-lookup"><span data-stu-id="01102-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="01102-117">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="01102-117">Ensure</span></span>| <span data-ttu-id="01102-118">Geeft aan of de sleutel en waarde bestaan.</span><span class="sxs-lookup"><span data-stu-id="01102-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="01102-119">Om ervoor te zorgen dat ze doen, stelt u deze eigenschap in 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="01102-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="01102-120">Om ervoor te zorgen dat deze niet bestaan, de eigenschap instellen op 'Ontbreekt'.</span><span class="sxs-lookup"><span data-stu-id="01102-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="01102-121">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="01102-121">The default value is "Present".</span></span>|
| <span data-ttu-id="01102-122">Force</span><span class="sxs-lookup"><span data-stu-id="01102-122">Force</span></span>| <span data-ttu-id="01102-123">Als de opgegeven registersleutel aanwezig is, **Force** overschreven door de nieuwe waarde.</span><span class="sxs-lookup"><span data-stu-id="01102-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="01102-124">Als een registersleutel met subsleutels verwijdert, moet dit **$true**</span><span class="sxs-lookup"><span data-stu-id="01102-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="01102-125">Hexadecimaal</span><span class="sxs-lookup"><span data-stu-id="01102-125">Hex</span></span>| <span data-ttu-id="01102-126">Hiermee wordt aangegeven als gegevens zullen worden uitgedrukt in hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="01102-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="01102-127">Als u opgeeft, worden de gegevens van de DWORD-/ QWORD-waarde wordt weergegeven in hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="01102-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="01102-128">Niet geldig voor andere typen.</span><span class="sxs-lookup"><span data-stu-id="01102-128">Not valid for other types.</span></span> <span data-ttu-id="01102-129">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="01102-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="01102-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="01102-130">DependsOn</span></span>| <span data-ttu-id="01102-131">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="01102-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="01102-132">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="01102-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="01102-133">Waardegegevens</span><span class="sxs-lookup"><span data-stu-id="01102-133">ValueData</span></span>| <span data-ttu-id="01102-134">De gegevens voor de waarde van het register.</span><span class="sxs-lookup"><span data-stu-id="01102-134">The data for the registry value.</span></span>|
| <span data-ttu-id="01102-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="01102-135">ValueType</span></span>| <span data-ttu-id="01102-136">Geeft het type van de waarde.</span><span class="sxs-lookup"><span data-stu-id="01102-136">Indicates the type of the value.</span></span> <span data-ttu-id="01102-137">De ondersteunde typen zijn: tekenreeks (REG_SZ), binair (REG-BINARY), DWORD-32-bits (REG_DWORD), Qword 64-bits (REG_QWORD), met meerdere tekenreeksen (REG_MULTI_SZ), uitbreidbare tekenreeks (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="01102-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="01102-138">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="01102-138">Example</span></span>

<span data-ttu-id="01102-139">In dit voorbeeld zorgt ervoor dat een sleutel met de naam "ExampleKey" aanwezig zijn in de **HKEY\_lokale\_MACHINE** hive.</span><span class="sxs-lookup"><span data-stu-id="01102-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

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
> <span data-ttu-id="01102-140">Wijzigen van een instelling in het register in de **HKEY\_huidige\_gebruiker** hive vereist dat de configuratie wordt uitgevoerd met de referenties van gebruiker, in plaats van als het systeem.</span><span class="sxs-lookup"><span data-stu-id="01102-140">Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="01102-141">U kunt de **PsDscRunAsCredential** eigenschap om op te geven voor de configuratie van de gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="01102-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="01102-142">Zie voor een voorbeeld [DSC uitvoeren met gebruikersreferenties](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="01102-142">For an example, see [Running DSC with user credentials](runAsUser.md).</span></span>