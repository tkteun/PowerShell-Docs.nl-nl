---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Logboekresource
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048282"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="6b461-103">DSC-Logboekresource</span><span class="sxs-lookup"><span data-stu-id="6b461-103">DSC Log Resource</span></span>

> <span data-ttu-id="6b461-104">_Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="6b461-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="6b461-105">De __Log__ resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het schrijven van berichten naar het gebeurtenislogboek van de Microsoft-Windows-Desired State Configuration / analysen.</span><span class="sxs-lookup"><span data-stu-id="6b461-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="6b461-106">Alleen de operationele logboeken voor DSC zijn standaard ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="6b461-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="6b461-107">Voordat de analytische logboek beschikbaar of zichtbaar is, moet zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="6b461-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="6b461-108">Zie voor meer informatie, [waar zich de gebeurtenislogboeken DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="6b461-108">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="6b461-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="6b461-109">Properties</span></span>

| <span data-ttu-id="6b461-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6b461-110">Property</span></span> | <span data-ttu-id="6b461-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6b461-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="6b461-112">Bericht</span><span class="sxs-lookup"><span data-stu-id="6b461-112">Message</span></span>| <span data-ttu-id="6b461-113">Geeft aan dat het bericht dat u wilt schrijven naar het gebeurtenislogboek Microsoft-Windows-Desired staat configuratie/analysen.</span><span class="sxs-lookup"><span data-stu-id="6b461-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="6b461-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6b461-114">DependsOn</span></span> | <span data-ttu-id="6b461-115">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze logboekbericht wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="6b461-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="6b461-116">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="6b461-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="6b461-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6b461-117">Example</span></span>

<span data-ttu-id="6b461-118">Het volgende voorbeeld ziet hoe u een bericht opnemen in het gebeurtenislogboek Microsoft-Windows-Desired staat configuratie/analysen.</span><span class="sxs-lookup"><span data-stu-id="6b461-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="6b461-119">Als u [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) met deze resource geconfigureerd, wordt altijd geretourneerd **$false**.</span><span class="sxs-lookup"><span data-stu-id="6b461-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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
