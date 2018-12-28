---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Methoden voor het rechtstreeks aanroepen van DSC-resources
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403913"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="d4a22-103">Methoden voor het rechtstreeks aanroepen van DSC-resources</span><span class="sxs-lookup"><span data-stu-id="d4a22-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="d4a22-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d4a22-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d4a22-105">U kunt de [sleutelwoorden Invoke-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet voor het rechtstreeks aanroepen van de functies of methoden van een DSC-resource (de **Get-TargetResource**, **Set TargetResource**, en  **Test-TargetResource** functies van een resource op basis van MOF of de **ophalen**, **ingesteld**, en **Test** methoden van een resource op basis van een klasse).</span><span class="sxs-lookup"><span data-stu-id="d4a22-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="d4a22-106">Dit kan worden gebruikt door derden die DSC-resources wilt gebruiken, of als een handig hulpmiddel tijdens het ontwikkelen van resources.</span><span class="sxs-lookup"><span data-stu-id="d4a22-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="d4a22-107">Deze cmdlet wordt doorgaans gebruikt in combinatie met een eigenschap metaconfiguration `refreshMode = 'Disabled'`, maar deze kan worden gebruikt, ongeacht wat **refreshMode** is ingesteld op.</span><span class="sxs-lookup"><span data-stu-id="d4a22-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="d4a22-108">Bij het aanroepen van de **sleutelwoorden Invoke-dscresource bieden** cmdlet, u opgeven welke methode of functie aan te roepen met behulp van de **methode** parameter.</span><span class="sxs-lookup"><span data-stu-id="d4a22-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="d4a22-109">U de eigenschappen van de resource opgeven door een hash-tabel als de waarde van de **eigenschap** parameter.</span><span class="sxs-lookup"><span data-stu-id="d4a22-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="d4a22-110">Hier volgen enkele voorbeelden van het rechtstreeks aanroepen van resourcemethoden:</span><span class="sxs-lookup"><span data-stu-id="d4a22-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="d4a22-111">Zorg ervoor dat een bestand aanwezig is</span><span class="sxs-lookup"><span data-stu-id="d4a22-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="d4a22-112">Test of een bestand aanwezig is</span><span class="sxs-lookup"><span data-stu-id="d4a22-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="d4a22-113">De inhoud van bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="d4a22-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="d4a22-114">**Opmerking:** Samengestelde resourcemethoden direct aan te roepen wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d4a22-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="d4a22-115">In plaats daarvan de methoden van de onderliggende resources die gezamenlijk de samengestelde resource aanroept.</span><span class="sxs-lookup"><span data-stu-id="d4a22-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4a22-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d4a22-116">See Also</span></span>
- [<span data-ttu-id="d4a22-117">Een aangepaste DSC-resource met MOF schrijven</span><span class="sxs-lookup"><span data-stu-id="d4a22-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="d4a22-118">Schrijven van een aangepaste DSC-resource met de PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="d4a22-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="d4a22-119">Foutopsporing voor DSC-resources</span><span class="sxs-lookup"><span data-stu-id="d4a22-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)