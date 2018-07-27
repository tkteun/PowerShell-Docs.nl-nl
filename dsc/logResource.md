---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Logboekresource
ms.openlocfilehash: 50fd6cd31ba426108830fcf124a767318060a95d
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268429"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="3764b-103">DSC-Logboekresource</span><span class="sxs-lookup"><span data-stu-id="3764b-103">DSC Log Resource</span></span>

<span data-ttu-id="3764b-104">_Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="3764b-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="3764b-105">De __Log__ resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het schrijven van berichten naar het gebeurtenislogboek van de Microsoft-Windows-Desired State Configuration / analysen.</span><span class="sxs-lookup"><span data-stu-id="3764b-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="3764b-106">Alleen de operationele logboeken voor DSC zijn standaard ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3764b-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="3764b-107">Voordat de analytische logboek beschikbaar of zichtbaar is, moet zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3764b-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="3764b-108">Zie voor meer informatie, [waar zich de gebeurtenislogboeken DSC?](troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="3764b-108">For more information, see [Where are DSC Event Logs?](troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="3764b-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="3764b-109">Properties</span></span>

| <span data-ttu-id="3764b-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="3764b-110">Property</span></span> | <span data-ttu-id="3764b-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3764b-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3764b-112">Bericht</span><span class="sxs-lookup"><span data-stu-id="3764b-112">Message</span></span>| <span data-ttu-id="3764b-113">Geeft aan dat het bericht dat u wilt schrijven naar het gebeurtenislogboek Microsoft-Windows-Desired staat configuratie/analysen.</span><span class="sxs-lookup"><span data-stu-id="3764b-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="3764b-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3764b-114">DependsOn</span></span> | <span data-ttu-id="3764b-115">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze logboekbericht wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="3764b-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="3764b-116">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="3764b-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="3764b-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3764b-117">Example</span></span>

<span data-ttu-id="3764b-118">Het volgende voorbeeld ziet hoe u een bericht opnemen in het gebeurtenislogboek Microsoft-Windows-Desired staat configuratie/analysen.</span><span class="sxs-lookup"><span data-stu-id="3764b-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="3764b-119">Als u [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) met deze resource geconfigureerd, wordt altijd geretourneerd **$false**.</span><span class="sxs-lookup"><span data-stu-id="3764b-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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