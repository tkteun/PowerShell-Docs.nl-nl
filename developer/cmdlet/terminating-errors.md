---
title: Fouten wordt beëindigd | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: c593da1f7bdb6ddf09ba8d5de92af730687dbc8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849075"
---
# <a name="terminating-errors"></a>Fouten waarbij de functie of bewerking wordt beëindigd

In dit onderwerp worden de methode die wordt gebruikt voor het rapport wordt beëindigd fouten. Hierin worden ook over het aanroepen van de methode van de cmdlet en hierin worden de uitzonderingen die door de Windows PowerShell-runtime kunnen worden geretourneerd wanneer de methode wordt aangeroepen.

Wanneer een afsluitende fout optreedt, de cmdlet de fout te melden door het aanroepen van de [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) methode. Deze methode kunt de cmdlet voor het verzenden van een foutrecord die beschrijft de voorwaarde dat de afsluitende fout heeft veroorzaakt. Zie voor meer informatie over foutrecords [Windows PowerShell-foutrecords](./windows-powershell-error-records.md).

Wanneer de [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) methode wordt aangeroepen, de Windows PowerShell-runtime permanent stopt de uitvoering van de pijplijn en genereert een [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) uitzondering. Alle daaropvolgende pogingen om aan te roepen [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), of verschillende andere API's zorgt ervoor dat deze aanroepen om een [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) uitzondering.

De [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) uitzondering kan ook optreden als een andere cmdlet in de pijplijn een afsluitfout gerapporteerd als de gebruiker heeft gevraagd om te stoppen van de pijplijn, of als de pijplijn is gestopt voordat de voltooid voor een bepaalde reden. De cmdlet hoeft niet te vangen de [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) uitzondering, tenzij deze opschoning van resources of de interne status moet openen.

Cmdlets kunt u een willekeurig aantal objecten uitvoer of niet-afsluitfouten schrijven voordat wordt een afsluitende fout gemeld. Echter de afsluitfout permanent de pijplijn en geen verdere uitvoer, wordt beëindigd fouten, gestopt of niet-afsluitfouten worden gerapporteerd.

Cmdlets kan aanroepen [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) alleen vanaf de thread die met de naam de [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), of [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) invoermethode voor verwerking. Probeer niet om aan te roepen [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) of [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) via een andere thread. In plaats daarvan moeten fouten worden gecommuniceerd terug naar de hoofdthread.

Het is mogelijk voor een cmdlet om een uitzondering in de implementatie van de [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), of [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode. Een uitzondering van deze methoden (met uitzondering van een aantal ernstige fouten die stoppen van de Windows PowerShell-host) wordt geïnterpreteerd als een afsluitfout wat voorkomt dat de pijplijn, maar geen Windows PowerShell als geheel. (Dit geldt alleen voor de belangrijkste cmdlet-thread. Niet-onderschepte uitzonderingen in threads geïnitieerd door de cmdlet, in het algemeen, dat de Windows PowerShell-host.) Het is raadzaam dat u [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) in plaats van die een uitzondering veroorzaakt omdat de foutrecord aanvullende informatie over de fout biedt, dit is handig om de eindgebruiker. Cmdlets moet voldoen aan de richtlijn voor de beheerde code tegen worden vastgelegd en verwerken van alle uitzonderingen (`catch (Exception e)`). Bekende en de verwachte typen uitzonderingen converteren naar foutrecords.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-foutrecords](./windows-powershell-error-records.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
