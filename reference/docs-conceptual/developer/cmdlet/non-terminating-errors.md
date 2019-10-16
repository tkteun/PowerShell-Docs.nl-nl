---
title: Niet-afsluit fouten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359270"
---
# <a name="non-terminating-errors"></a>Fouten waarbij de functie of bewerking niet wordt beëindigd

In dit onderwerp wordt de methode beschreven die wordt gebruikt om niet-afsluit fouten te rapporteren. Ook wordt beschreven hoe u de methode aanroept vanuit de cmdlet.

Als er een fout optreedt die niet wordt afgesloten, moet de cmdlet deze fout rapporteren door de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aan te roepen. Wanneer de cmdlet een niet-afsluit fout rapporteert, kan de cmdlet blijven werken op dit invoer object en op verdere inkomende pijplijn objecten. Als de cmdlet de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroept, kan de cmdlet een fout record schrijven met een beschrijving van de voor waarde die de niet-afsluit bare fout heeft veroorzaakt. Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout records.

Cmdlets kunnen [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroepen vanuit hun invoer methoden. Met-cmdlets kan [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) echter alleen worden aangeroepen vanuit de thread met de naam [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. ~. ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)of [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) -invoer methode. Roep [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) niet aan vanuit een andere thread. Communiceert in plaats daarvan fouten terug naar de hoofd thread.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows Power Shell-fout records](./windows-powershell-error-records.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
