---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-logboek resource
description: DSC-logboek resource
ms.openlocfilehash: 281d1f8aeeb4d075f073419ac02a0f81888ed2b5
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142460"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="8c4bf-103">DSC-logboek resource</span><span class="sxs-lookup"><span data-stu-id="8c4bf-103">DSC Log Resource</span></span>

> <span data-ttu-id="8c4bf-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="8c4bf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="8c4bf-105">De **logboek** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het schrijven van berichten naar het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="8c4bf-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8c4bf-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="8c4bf-107">Standaard zijn alleen de operationele logboeken voor DSC ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="8c4bf-108">Voordat het analytische logboek beschikbaar of zichtbaar is, moet het worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="8c4bf-109">Zie voor meer informatie [waar zijn DSC-gebeurtenis logboeken?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="8c4bf-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="8c4bf-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8c4bf-110">Properties</span></span>

| <span data-ttu-id="8c4bf-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8c4bf-111">Property</span></span> |                                                   <span data-ttu-id="8c4bf-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8c4bf-112">Description</span></span>                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="8c4bf-113">Bericht</span><span class="sxs-lookup"><span data-stu-id="8c4bf-113">Message</span></span>  | <span data-ttu-id="8c4bf-114">Hiermee wordt het bericht aangegeven dat u wilt schrijven naar het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="8c4bf-115">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8c4bf-115">Common properties</span></span>

|       <span data-ttu-id="8c4bf-116">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8c4bf-116">Property</span></span>       |                                                                                                                                                          <span data-ttu-id="8c4bf-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8c4bf-117">Description</span></span>                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="8c4bf-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8c4bf-118">DependsOn</span></span>            | <span data-ttu-id="8c4bf-119">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8c4bf-120">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="8c4bf-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
| <span data-ttu-id="8c4bf-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="8c4bf-121">PsDscRunAsCredential</span></span> | <span data-ttu-id="8c4bf-122">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-122">Sets the credential for running the entire resource as.</span></span>                                                                                                                                                                                                                                                                        |

> [!NOTE]
> <span data-ttu-id="8c4bf-123">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="8c4bf-124">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="8c4bf-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8c4bf-125">Example</span></span>

<span data-ttu-id="8c4bf-126">In het volgende voor beeld ziet u hoe u een bericht opneemt in het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="8c4bf-127">Als u [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration) uitvoert met deze bron geconfigureerd, wordt er altijd **$False** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8c4bf-127">If you run [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration) with this resource configured, it will always return **$false** .</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
