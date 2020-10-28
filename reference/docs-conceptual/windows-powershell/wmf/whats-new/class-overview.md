---
ms.date: 07/29/2020
title: Nieuwe taalfuncties in PowerShell 5.0
description: Power shell 5,0 heeft de mogelijkheid om klassen en andere door de gebruiker gedefinieerde typen te definiëren met behulp van formele syntaxis en semantiek, zoals andere objectgeoriënteerd programmeer talen.
ms.openlocfilehash: 31ff54ba6f2800a0680c1a2db3832ca97246973d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663298"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="4897e-103">Nieuwe taalfuncties in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4897e-103">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="4897e-104">Power shell 5,0 heeft de mogelijkheid om klassen en andere door de gebruiker gedefinieerde typen te definiëren met behulp van formele syntaxis en semantiek, zoals andere objectgeoriënteerd programmeer talen.</span><span class="sxs-lookup"><span data-stu-id="4897e-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="4897e-105">Het doel is om ontwikkel aars en IT-professionals in staat te stellen Power shell te gebruiken voor een breder scala aan gebruiks voorbeelden, het ontwikkelen van Power shell-artefacten (zoals DSC-resources) te vereenvoudigen en de dekking van management-Opper vlakken te versnellen.</span><span class="sxs-lookup"><span data-stu-id="4897e-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

<span data-ttu-id="4897e-106">Power shell 5,0 introduceert de volgende nieuwe taal elementen in Power shell:</span><span class="sxs-lookup"><span data-stu-id="4897e-106">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="4897e-107">Tref woord klasse</span><span class="sxs-lookup"><span data-stu-id="4897e-107">Class keyword</span></span>

<span data-ttu-id="4897e-108">Het `class` sleutel woord definieert een nieuwe klasse.</span><span class="sxs-lookup"><span data-stu-id="4897e-108">The `class` keyword defines a new class.</span></span> <span data-ttu-id="4897e-109">Dit is een True .NET Framework type.</span><span class="sxs-lookup"><span data-stu-id="4897e-109">This is a true .NET Framework type.</span></span> <span data-ttu-id="4897e-110">Klasse-leden zijn openbaar, maar alleen openbaar binnen het module bereik.</span><span class="sxs-lookup"><span data-stu-id="4897e-110">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="4897e-111">U kunt niet naar de type naam verwijzen als een teken reeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u geen letterlijke type waarde (bijvoorbeeld) gebruiken `[MyClass]` buiten het script of module bestand waarin de klasse is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="4897e-111">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="4897e-112">Tref woord en opsommingen inventariseren</span><span class="sxs-lookup"><span data-stu-id="4897e-112">Enum keyword and enumerations</span></span>

<span data-ttu-id="4897e-113">Ondersteuning voor het `enum` tref woord is toegevoegd. Dit maakt gebruik van een nieuwe regel als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="4897e-113">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="4897e-114">Op dit moment kunt u geen enumerator definiëren in termen van zichzelf.</span><span class="sxs-lookup"><span data-stu-id="4897e-114">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="4897e-115">U kunt echter een Enum initialiseren in termen van een andere Enum, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="4897e-115">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="4897e-116">Het basis type kan ook niet worden opgegeven. het is altijd `[int]` .</span><span class="sxs-lookup"><span data-stu-id="4897e-116">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="4897e-117">Een enumerator-waarde moet een geparseerd tijd constante zijn.</span><span class="sxs-lookup"><span data-stu-id="4897e-117">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="4897e-118">U kunt deze niet instellen op het resultaat van een aangeroepen opdracht.</span><span class="sxs-lookup"><span data-stu-id="4897e-118">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="4897e-119">Opsommingen bieden ondersteuning voor reken kundige bewerkingen, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="4897e-119">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="4897e-120">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="4897e-120">Import-DscResource</span></span>

<span data-ttu-id="4897e-121">`Import-DscResource` is nu een echt dynamisch sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="4897e-121">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="4897e-122">Power shell parseert de hoofd module van de opgegeven module. er wordt gezocht naar klassen die het kenmerk **dscresource bieden** bevatten.</span><span class="sxs-lookup"><span data-stu-id="4897e-122">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="4897e-123">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="4897e-123">ImplementingAssembly</span></span>

<span data-ttu-id="4897e-124">Er is een nieuw veld, **ImplementingAssembly** , toegevoegd aan **ModuleInfo** .</span><span class="sxs-lookup"><span data-stu-id="4897e-124">A new field, **ImplementingAssembly** , has been added to **ModuleInfo** .</span></span> <span data-ttu-id="4897e-125">Deze wordt ingesteld op de dynamische assembly die is gemaakt voor een script module als het script klassen definieert, of de geladen assembly voor binaire modules.</span><span class="sxs-lookup"><span data-stu-id="4897e-125">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="4897e-126">Het is niet ingesteld wanneer **module type** is **manifest** .</span><span class="sxs-lookup"><span data-stu-id="4897e-126">It is not set when **ModuleType** is **Manifest** .</span></span>

<span data-ttu-id="4897e-127">Reflectie in het veld **ImplementingAssembly** detecteert bronnen in een module.</span><span class="sxs-lookup"><span data-stu-id="4897e-127">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="4897e-128">Dit betekent dat u resources kunt detecteren die in Power shell of andere beheerde talen zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="4897e-128">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

## <a name="further-reading"></a><span data-ttu-id="4897e-129">Meer lezen</span><span class="sxs-lookup"><span data-stu-id="4897e-129">Further reading</span></span>

- [<span data-ttu-id="4897e-130">about_Classes</span><span class="sxs-lookup"><span data-stu-id="4897e-130">about_Classes</span></span>](/powershell/module/microsoft.powershell.core/about/about_classes)
- [<span data-ttu-id="4897e-131">about_Enum</span><span class="sxs-lookup"><span data-stu-id="4897e-131">about_Enum</span></span>](/powershell/module/microsoft.powershell.core/about/about_enum)
- [<span data-ttu-id="4897e-132">about_Classes_and_DSC</span><span class="sxs-lookup"><span data-stu-id="4897e-132">about_Classes_and_DSC</span></span>](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)
