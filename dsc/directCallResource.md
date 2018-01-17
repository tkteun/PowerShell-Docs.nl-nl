---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Rechtstreeks aanroepen van methoden van DSC-resource
ms.openlocfilehash: 3e83984fbf31dfcfec76fa15cdd9b83d92501aa0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="87dbb-103">Rechtstreeks aanroepen van methoden van DSC-resource</span><span class="sxs-lookup"><span data-stu-id="87dbb-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="87dbb-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="87dbb-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="87dbb-105">U kunt de [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) cmdlet rechtstreeks aanroepen van de functies of methoden van een DSC-resource (de **Get-TargetResource**, **Set TargetResource**, en  **Test-TargetResource** functies van een bron op basis van MOF of de **ophalen**, **ingesteld**, en **Test** methoden van een bron op basis van een klasse).</span><span class="sxs-lookup"><span data-stu-id="87dbb-105">You can use the [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="87dbb-106">Dit kan worden gebruikt door derden die DSC-resources wilt gebruiken of als een nuttig hulpmiddel bij het ontwikkelen van resources.</span><span class="sxs-lookup"><span data-stu-id="87dbb-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span> 

<span data-ttu-id="87dbb-107">Deze cmdlet wordt doorgaans gebruikt in combinatie met een eigenschap metaconfiguratie `refreshMode = 'Disabled'`, maar deze kan worden gebruikt, wat er ook **refreshMode** is ingesteld op.</span><span class="sxs-lookup"><span data-stu-id="87dbb-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="87dbb-108">Bij het aanroepen van de **Invoke-DscResource** cmdlet u opgeven welke methode of functie aan te roepen met behulp van de **methode** parameter.</span><span class="sxs-lookup"><span data-stu-id="87dbb-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="87dbb-109">U de eigenschappen van de resource opgeven door een hashtabel wordt doorgegeven als de waarde van de **eigenschap** parameter.</span><span class="sxs-lookup"><span data-stu-id="87dbb-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="87dbb-110">Hier volgen enkele voorbeelden van methoden van de resource direct aan te roepen:</span><span class="sxs-lookup"><span data-stu-id="87dbb-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="87dbb-111">Zorg ervoor dat een bestand aanwezig is</span><span class="sxs-lookup"><span data-stu-id="87dbb-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="87dbb-112">Testen of een bestand aanwezig is</span><span class="sxs-lookup"><span data-stu-id="87dbb-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="87dbb-113">De inhoud van bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="87dbb-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="87dbb-114">**Opmerking:** rechtstreeks aanroepen van methoden van de samengestelde bron wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="87dbb-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="87dbb-115">Roep in plaats daarvan de methoden van de onderliggende resources die gezamenlijk de samengestelde bron.</span><span class="sxs-lookup"><span data-stu-id="87dbb-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="87dbb-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="87dbb-116">See Also</span></span>
- [<span data-ttu-id="87dbb-117">Schrijven van een aangepaste DSC-resource met MOF</span><span class="sxs-lookup"><span data-stu-id="87dbb-117">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md) 
- [<span data-ttu-id="87dbb-118">Schrijven van een aangepaste DSC-resource met PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="87dbb-118">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="87dbb-119">Foutopsporing voor DSC-resources</span><span class="sxs-lookup"><span data-stu-id="87dbb-119">Debugging DSC resources</span></span>](debugResource.md)

