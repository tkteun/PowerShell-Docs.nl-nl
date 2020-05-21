---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Methoden voor het rechtstreeks aanroepen van DSC-resources
ms.openlocfilehash: 9955de4f284c182a724b004c17080a8b8e19808d
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692414"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="498a5-103">Methoden voor het rechtstreeks aanroepen van DSC-resources</span><span class="sxs-lookup"><span data-stu-id="498a5-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="498a5-104">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="498a5-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="498a5-105">U kunt de cmdlet [invoke-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) gebruiken om de functies of methoden van een DSC-resource rechtstreeks aan te roepen (de functies **Get-TargetResource**, **set-TargetResource**en **test-TargetResource** van een op een MOF gebaseerde resource, of de methoden **Get**, **set**en **test** van een op een klasse gebaseerde bron).</span><span class="sxs-lookup"><span data-stu-id="498a5-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="498a5-106">Dit kan worden gebruikt door derden die DSC-resources willen gebruiken of als handig hulp middel bij het ontwikkelen van resources.</span><span class="sxs-lookup"><span data-stu-id="498a5-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="498a5-107">Deze cmdlet wordt doorgaans gebruikt in combi natie met een eigenschap `refreshMode = 'Disabled'` **refreshMode** , maar kan ook worden gebruikt, ongeacht de waarde die is ingesteld op.</span><span class="sxs-lookup"><span data-stu-id="498a5-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="498a5-108">Wanneer u de cmdlet **invoke-dscresource bieden** aanroept, geeft u op welke methode of functie u wilt aanroepen met behulp van de **methode** parameter.</span><span class="sxs-lookup"><span data-stu-id="498a5-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="498a5-109">U geeft de eigenschappen van de resource op door een hashtabel door te geven als de waarde van de **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="498a5-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="498a5-110">Hier volgen enkele voor beelden van het rechtstreeks aanroepen van resource methoden:</span><span class="sxs-lookup"><span data-stu-id="498a5-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="498a5-111">Controleren of een bestand aanwezig is</span><span class="sxs-lookup"><span data-stu-id="498a5-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="498a5-112">Testen of een bestand aanwezig is</span><span class="sxs-lookup"><span data-stu-id="498a5-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="498a5-113">De inhoud van het bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="498a5-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="498a5-114">**Opmerking:** Het rechtstreeks aanroepen van samengestelde resource methoden wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="498a5-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="498a5-115">In plaats daarvan roept u de methoden van de onderliggende resources aan waaruit de samengestelde resource is samengesteld.</span><span class="sxs-lookup"><span data-stu-id="498a5-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="498a5-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="498a5-116">See Also</span></span>

- [<span data-ttu-id="498a5-117">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="498a5-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="498a5-118">Een aangepaste DSC-resource schrijven met Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="498a5-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="498a5-119">Foutopsporing voor DSC-resources</span><span class="sxs-lookup"><span data-stu-id="498a5-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
