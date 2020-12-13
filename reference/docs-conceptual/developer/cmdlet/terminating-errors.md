---
ms.date: 09/13/2016
ms.topic: reference
title: Fouten waarbij de functie of bewerking wordt beëindigd
description: Fouten waarbij de functie of bewerking wordt beëindigd
ms.openlocfilehash: b7c9b949a654f10a0421ea69dfe955c8dfb5627e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652549"
---
# <a name="terminating-errors"></a>Fouten waarbij de functie of bewerking wordt beëindigd

In dit onderwerp wordt de methode beschreven die wordt gebruikt voor het rapporteren van afsluit fouten. Ook wordt beschreven hoe u de methode aanroept vanuit de cmdlet en worden de uitzonde ringen beschreven die kunnen worden geretourneerd door de Windows Power shell-runtime wanneer de methode wordt aangeroepen.

Als er een afsluit fout optreedt, moet de cmdlet de fout rapporteren door de methode [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) aan te roepen. Met deze methode kan de cmdlet een fout record verzenden waarin de voor waarde wordt beschreven die de afsluit fout heeft veroorzaakt. Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout records.

Bij het aanroepen van de methode [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) wordt de uitvoering van de pijp lijn permanent gestopt en wordt een [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) -uitzonde ring gegenereerd. Eventuele daaropvolgende pogingen om [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System. Management. Automation](/dotnet/api/System.Management.Automation.Cmdlet.WriteError). cmdlet. WriteError of verschillende andere api's aan te roepen, veroorzaken deze aanroepen om een uitzonde ring [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) uit te voeren.

De uitzonde ring [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) kan ook optreden als een andere cmdlet in de pijp lijn een afsluit fout rapporteert, als de gebruiker heeft gevraagd de pijp lijn te stoppen of als de pijp lijn om een of andere reden is gestopt. De cmdlet hoeft de uitzonde ring [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) niet te ondervangen, tenzij open bronnen of de interne status ervan moeten worden opgeruimd.

Met cmdlets kunt u elk wille keurig aantal uitvoer objecten of niet-afsluit fouten schrijven voordat u een afsluit fout rapporteert. De afsluit fout stopt echter permanent de pijp lijn en er kunnen geen verdere uitvoer, afsluit fouten of niet-afsluit fouten worden gerapporteerd.

Met cmdlets kan [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) alleen worden aangeroepen vanuit de thread met de naam [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Automation. cmdlet. ProcessRecord of [System. Management.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Automation. cmdlet. EndProcessing-invoer methode. Probeer [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) of [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) niet aan te roepen vanuit een andere thread. In plaats daarvan moeten fouten worden teruggestuurd naar de hoofd thread.

Het is mogelijk dat een cmdlet een uitzonde ring genereert in de implementatie van [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management.](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)Automation. cmdlet. ProcessRecord of [System. Management.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Automation. cmdlet. EndProcessing. Een uitzonde ring die is gegenereerd op basis van deze methoden (met uitzonde ring van enkele ernstige fout situaties die de Windows Power shell-host stoppen) wordt geïnterpreteerd als een afsluit fout waardoor de pijp lijn wordt gestopt, maar niet Windows Power shell als geheel. (Dit geldt alleen voor de hoofd-cmdlet-thread. Niet-onderschepte uitzonde ringen in threads die worden geïnitieerd door de cmdlet, in het algemeen, stopt u de Windows Power shell-host.) U wordt aangeraden [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) te gebruiken in plaats van een uitzonde ring uit te voeren, omdat de fout record aanvullende informatie bevat over de fout voorwaarde, die nuttig is voor de eind gebruiker. Cmdlets moeten voldoen aan de richt lijnen voor beheerde code voor het uitvoeren en afhandelen van alle uitzonde ringen ( `catch (Exception e)` ). Converteer alleen uitzonde ringen van bekende en verwachte typen naar fout records.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-foutrecords](./windows-powershell-error-records.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
