---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Logboek van de DSC-Resource
ms.openlocfilehash: c7e1957540da2fd85a30f739e0f69bdb6975a4d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219382"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="cc925-103">Logboek van de DSC-Resource</span><span class="sxs-lookup"><span data-stu-id="cc925-103">DSC Log Resource</span></span>

> <span data-ttu-id="cc925-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cc925-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="cc925-105">De __logboek__ in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor berichten schrijven naar het gebeurtenislogboek van de Microsoft-Windows-gewenst status Configuration/analysen.</span><span class="sxs-lookup"><span data-stu-id="cc925-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="cc925-106">Opmerking: Standaard alleen de operationele logboeken voor DSC zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="cc925-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="cc925-107">Voordat het analytische logboek beschikbaar of zichtbaar is, moet zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="cc925-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="cc925-108">Zie het volgende artikel.</span><span class="sxs-lookup"><span data-stu-id="cc925-108">See the following article.</span></span>

[<span data-ttu-id="cc925-109">Waar zijn de gebeurtenislogboeken DSC?</span><span class="sxs-lookup"><span data-stu-id="cc925-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="cc925-110">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="cc925-110">Properties</span></span>
|  <span data-ttu-id="cc925-111">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="cc925-111">Property</span></span>  |  <span data-ttu-id="cc925-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cc925-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="cc925-113">Bericht</span><span class="sxs-lookup"><span data-stu-id="cc925-113">Message</span></span>| <span data-ttu-id="cc925-114">Hiermee geeft u het bericht dat u wilt schrijven naar het gebeurtenislogboek Microsoft-Windows-Desired status Configuration/analysen.</span><span class="sxs-lookup"><span data-stu-id="cc925-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="cc925-115">dependsOn</span><span class="sxs-lookup"><span data-stu-id="cc925-115">DependsOn</span></span> | <span data-ttu-id="cc925-116">Geeft aan dat de configuratie van een andere resource moet worden uitgevoerd voordat dit logboekbericht wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="cc925-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="cc925-117">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="cc925-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="cc925-118">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="cc925-118">Example</span></span>

<span data-ttu-id="cc925-119">Het volgende voorbeeld laat zien hoe een bericht in het gebeurtenislogboek Microsoft-Windows-Desired status Configuration/analysen opnemen.</span><span class="sxs-lookup"><span data-stu-id="cc925-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="cc925-120">**Opmerking**: als u [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) aan deze resource is geconfigureerd, wordt altijd geretourneerd **$false**.</span><span class="sxs-lookup"><span data-stu-id="cc925-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```