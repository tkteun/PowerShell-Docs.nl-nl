---
title: Niet-afsluitfouten fouten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067651"
---
# <a name="non-terminating-errors"></a>Fouten waarbij de functie of bewerking niet wordt beëindigd

In dit onderwerp worden de methode die wordt gebruikt voor het rapporteren van niet-afsluitfouten. Hierin worden ook over het aanroepen van de methode van de cmdlet.

Wanneer er een niet-afsluitfout optreedt, de cmdlet moet Meld deze fout door het aanroepen van de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode. Wanneer de cmdlet een niet-afsluitfout meldt, de cmdlet kan door blijven werken op dit invoerobject en verdere inkomende pipeline-objecten. Als de cmdlet roept de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode, de cmdlet kunt schrijven een foutrecord die beschrijft de voorwaarde dat de niet-afsluitfouten fout heeft veroorzaakt. Zie voor meer informatie over foutrecords [Windows PowerShell-foutrecords](./windows-powershell-error-records.md).

Cmdlets kan aanroepen [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) zo nodig uit binnen hun invoer verwerkingsmethoden. Echter cmdlets kan aanroepen [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) alleen vanaf de thread die met de naam de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), of [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) invoermethode voor verwerking. Roep niet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) via een andere thread. In plaats daarvan communiceren fouten terug naar de hoofdthread.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell-foutrecords](./windows-powershell-error-records.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
