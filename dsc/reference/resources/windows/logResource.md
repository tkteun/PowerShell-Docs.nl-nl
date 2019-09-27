---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-logboek resource
ms.openlocfilehash: a1b7bf44fbaf36a3adaf0666e9f0a754fa3f6ee1
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324355"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="6a2ec-103">DSC-logboek resource</span><span class="sxs-lookup"><span data-stu-id="6a2ec-103">DSC Log Resource</span></span>

> <span data-ttu-id="6a2ec-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="6a2ec-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="6a2ec-105">De **logboek** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het schrijven van berichten naar het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a2ec-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6a2ec-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="6a2ec-107">Standaard zijn alleen de operationele logboeken voor DSC ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="6a2ec-108">Voordat het analytische logboek beschikbaar of zichtbaar is, moet het worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="6a2ec-109">Zie voor meer informatie [waar zijn DSC-gebeurtenis logboeken?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="6a2ec-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="6a2ec-110">properties</span><span class="sxs-lookup"><span data-stu-id="6a2ec-110">Properties</span></span>

|<span data-ttu-id="6a2ec-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6a2ec-111">Property</span></span> |<span data-ttu-id="6a2ec-112">Description</span><span class="sxs-lookup"><span data-stu-id="6a2ec-112">Description</span></span> |
|---|---|
|<span data-ttu-id="6a2ec-113">Message</span><span class="sxs-lookup"><span data-stu-id="6a2ec-113">Message</span></span> |<span data-ttu-id="6a2ec-114">Hiermee wordt het bericht aangegeven dat u wilt schrijven naar het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6a2ec-115">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="6a2ec-115">Common properties</span></span>

|<span data-ttu-id="6a2ec-116">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6a2ec-116">Property</span></span> |<span data-ttu-id="6a2ec-117">Description</span><span class="sxs-lookup"><span data-stu-id="6a2ec-117">Description</span></span> |
|---|---|
|<span data-ttu-id="6a2ec-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6a2ec-118">DependsOn</span></span> |<span data-ttu-id="6a2ec-119">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6a2ec-120">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6a2ec-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6a2ec-121">PsDscRunAsCredential</span></span> |<span data-ttu-id="6a2ec-122">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-122">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="6a2ec-123">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="6a2ec-124">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a2ec-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6a2ec-125">Example</span></span>

<span data-ttu-id="6a2ec-126">In het volgende voor beeld ziet u hoe u een bericht opneemt in het gebeurtenis logboek micro soft-Windows-desired state Configuration/analytic.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="6a2ec-127">Als u [test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) uitvoert met deze bron geconfigureerd, wordt er altijd **$False**geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="6a2ec-127">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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