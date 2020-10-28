---
ms.date: 08/11/2020
keywords: DSC, Power shell, configuratie, installatie
title: Methoden voor het rechtstreeks aanroepen van DSC-resources
description: De cmdlet Invoke-DscResource kan worden gebruikt om de functies of methoden van een DSC-resource aan te roepen. Dit kan worden gebruikt door derden die DSC-resources willen gebruiken of als handig hulp middel bij het ontwikkelen van resources.
ms.openlocfilehash: 5ccf0f589b60cef4ec197d1e0a583af9ed60d5e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651006"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="b10a1-105">Methoden voor het rechtstreeks aanroepen van DSC-resources</span><span class="sxs-lookup"><span data-stu-id="b10a1-105">Calling DSC resource methods directly</span></span>

> <span data-ttu-id="b10a1-106">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="b10a1-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b10a1-107">U kunt de cmdlet [invoke-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) gebruiken om de functies of methoden van een DSC-resource rechtstreeks aan te roepen (de `Get-TargetResource` `Set-TargetResource` functies,, en `Test-TargetResource` van een op MOF gebaseerde resource, of de methoden **Get** , **set** en **test** van een bron op basis van een klasse).</span><span class="sxs-lookup"><span data-stu-id="b10a1-107">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions of a MOF-based resource, or the **Get** , **Set** , and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="b10a1-108">Dit kan worden gebruikt door derden die DSC-resources willen gebruiken of als handig hulp middel bij het ontwikkelen van resources.</span><span class="sxs-lookup"><span data-stu-id="b10a1-108">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

> [!NOTE]
> <span data-ttu-id="b10a1-109">In Power shell 7.0 + `Invoke-DscResource` biedt geen ondersteuning meer voor het aanroepen van WMI DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="b10a1-109">In PowerShell 7.0+, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="b10a1-110">Dit omvat de **Bestands** -en **logboek** bronnen in **PSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="b10a1-110">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration** .</span></span>

<span data-ttu-id="b10a1-111">Deze cmdlet wordt doorgaans gebruikt in combi natie met een eigenschap `refreshMode = 'Disabled'` **refreshMode** , maar kan ook worden gebruikt, ongeacht de waarde die is ingesteld op.</span><span class="sxs-lookup"><span data-stu-id="b10a1-111">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="b10a1-112">Wanneer u de `Invoke-DscResource` cmdlet aanroept, geeft u op welke methode of functie u wilt aanroepen met behulp van de **methode** parameter.</span><span class="sxs-lookup"><span data-stu-id="b10a1-112">When calling the `Invoke-DscResource` cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="b10a1-113">U geeft de eigenschappen van de resource op door een hashtabel door te geven als de waarde van de **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="b10a1-113">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="b10a1-114">Hier volgen enkele voor beelden van het rechtstreeks aanroepen van resource methoden:</span><span class="sxs-lookup"><span data-stu-id="b10a1-114">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="b10a1-115">Controleren of een bestand aanwezig is</span><span class="sxs-lookup"><span data-stu-id="b10a1-115">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="b10a1-116">Testen of een bestand aanwezig is</span><span class="sxs-lookup"><span data-stu-id="b10a1-116">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="b10a1-117">De inhoud van het bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="b10a1-117">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

> [!NOTE]
> <span data-ttu-id="b10a1-118">Het rechtstreeks aanroepen van samengestelde resource methoden wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b10a1-118">Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="b10a1-119">In plaats daarvan roept u de methoden van de onderliggende resources aan waaruit de samengestelde resource is samengesteld.</span><span class="sxs-lookup"><span data-stu-id="b10a1-119">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="b10a1-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b10a1-120">See Also</span></span>

- [<span data-ttu-id="b10a1-121">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="b10a1-121">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="b10a1-122">Een aangepaste DSC-resource schrijven met Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="b10a1-122">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="b10a1-123">Foutopsporing voor DSC-resources</span><span class="sxs-lookup"><span data-stu-id="b10a1-123">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
