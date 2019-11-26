---
title: Fouten beëindigen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359205"
---
# <a name="terminating-errors"></a>Fouten waarbij de functie of bewerking wordt beëindigd

In dit onderwerp wordt de methode beschreven die wordt gebruikt voor het rapporteren van afsluit fouten. Ook wordt beschreven hoe u de methode aanroept vanuit de cmdlet en worden de uitzonde ringen beschreven die kunnen worden geretourneerd door de Windows Power shell-runtime wanneer de methode wordt aangeroepen.

Als er een afsluit fout optreedt, moet de cmdlet de fout rapporteren door de methode [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) aan te roepen. Met deze methode kan de cmdlet een fout record verzenden waarin de voor waarde wordt beschreven die de afsluit fout heeft veroorzaakt. Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout records.

Bij het aanroepen van de methode [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) wordt de uitvoering van de pijp lijn permanent gestopt door Windows Power shell runtime en wordt een [System. Management. Automation. Pipelinestoppedexception gegenereerd. ](/dotnet/api/System.Management.Automation.PipelineStoppedException)uitzonde ring. Alle daaropvolgende pogingen om [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System. Management. Automation](/dotnet/api/System.Management.Automation.Cmdlet.WriteError). cmdlet. WriteError of verschillende andere api's aan te roepen, veroorzaken een [ System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) -uitzonde ring.

De uitzonde ring [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) kan ook optreden als een andere cmdlet in de pijp lijn een afsluit fout rapporteert, als de gebruiker heeft gevraagd de pijp lijn te stoppen of als de pijp lijn is onderbroken voordat een gemotiveerd. De cmdlet hoeft de uitzonde ring [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) niet te ondervangen, tenzij open bronnen of de interne status ervan moeten worden opgeruimd.

Met cmdlets kunt u elk wille keurig aantal uitvoer objecten of niet-afsluit fouten schrijven voordat u een afsluit fout rapporteert. De afsluit fout stopt echter permanent de pijp lijn en er kunnen geen verdere uitvoer, afsluit fouten of niet-afsluit fouten worden gerapporteerd.

Met cmdlets kan [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) alleen worden aangeroepen vanuit de thread met de naam [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. ~. ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)of [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -invoer methode. Probeer [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) of [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) niet aan te roepen vanuit een andere thread. In plaats daarvan moeten fouten worden teruggestuurd naar de hoofd thread.

Het is mogelijk dat een cmdlet een uitzonde ring genereert in de implementatie van [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). cmdlet. ProcessRecord of [ Methode System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Een uitzonde ring die is gegenereerd op basis van deze methoden (met uitzonde ring van enkele ernstige fout situaties die de Windows Power shell-host stoppen) wordt geïnterpreteerd als een afsluit fout waardoor de pijp lijn wordt gestopt, maar niet Windows Power shell als geheel. (Dit geldt alleen voor de hoofd-cmdlet-thread. Niet-onderschepte uitzonde ringen in threads die worden geïnitieerd door de cmdlet, in het algemeen, stopt u de Windows Power shell-host.) U wordt aangeraden [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) te gebruiken in plaats van een uitzonde ring uit te voeren, omdat de fout record aanvullende informatie bevat over de fout voorwaarde, die nuttig is voor de eind gebruiker. Cmdlets moeten voldoen aan de richt lijnen voor beheerde code voor het afhandelen en verwerken van alle uitzonde ringen (`catch (Exception e)`). Converteer alleen uitzonde ringen van bekende en verwachte typen naar fout records.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows Power Shell-fout records](./windows-powershell-error-records.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)