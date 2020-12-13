---
ms.date: 09/13/2016
ms.topic: reference
title: Fouten waarbij de functie of bewerking niet wordt beëindigd
description: Fouten waarbij de functie of bewerking niet wordt beëindigd
ms.openlocfilehash: d23642103e005c6d3a6168b317b11f40001b6bbe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655737"
---
# <a name="non-terminating-errors"></a>Fouten waarbij de functie of bewerking niet wordt beëindigd

In dit onderwerp wordt de methode beschreven die wordt gebruikt om niet-afsluit fouten te rapporteren. Ook wordt beschreven hoe u de methode aanroept vanuit de cmdlet.

Als er een fout optreedt die niet wordt afgesloten, moet de cmdlet deze fout rapporteren door de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aan te roepen. Wanneer de cmdlet een niet-afsluit fout rapporteert, kan de cmdlet blijven werken op dit invoer object en op verdere inkomende pijplijn objecten. Als de cmdlet de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroept, kan de cmdlet een fout record schrijven met een beschrijving van de voor waarde die de niet-afsluit bare fout heeft veroorzaakt. Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout records.

Cmdlets kunnen [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroepen vanuit hun invoer methoden. Met cmdlets kan [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) echter alleen worden aangeroepen vanuit de thread met de naam [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Automation. cmdlet. ProcessRecord of [System. Management.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Automation. cmdlet. EndProcessing-invoer methode. Roep [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) niet aan vanuit een andere thread. Communiceert in plaats daarvan fouten terug naar de hoofd thread.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell-foutrecords](./windows-powershell-error-records.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
