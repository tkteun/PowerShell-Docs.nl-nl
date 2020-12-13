---
ms.date: 09/13/2016
ms.topic: reference
title: Concepten voor foutrapportage
description: Concepten voor foutrapportage
ms.openlocfilehash: 353e628c63667a2db010556b2ed9169809b742f4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653045"
---
# <a name="error-reporting-concepts"></a>Concepten voor foutrapportage

Windows Power shell biedt twee mechanismen voor het rapporteren van fouten: één mechanisme voor het *beëindigen van fouten* en een ander mechanisme voor *niet-afsluit fouten*. Het is belang rijk om ervoor te zorgen dat uw cmdlet fouten correct rapporteert, zodat de hosttoepassing waarop uw cmdlets worden uitgevoerd, op de juiste manier kan reageren.

De cmdlet moet de methode [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) aanroepen als er een fout optreedt waarbij de cmdlet de invoer objecten niet kan blijven verwerken. De cmdlet moet de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroepen om niet-afsluit fouten te rapporteren wanneer de cmdlet de verwerking van de invoer objecten kan voortzetten. Beide methoden bieden een fout record die de hosttoepassing kan gebruiken om de oorzaak van de fout te onderzoeken.

Gebruik de volgende richt lijnen om te bepalen of een fout een afsluitende of niet-afsluit fout is.

- Een fout is een afsluit fout als wordt voor komen dat de cmdlet doorgaat met het verwerken van het huidige object of door het verwerken van andere invoer objecten, ongeacht de inhoud.

- Een fout wordt beëindigd als u niet wilt dat de cmdlet het huidige object of andere invoer objecten verwerkt, ongeacht de inhoud.

- Een fout is een afsluit fout als deze optreedt in een cmdlet die geen object accepteert of retourneert, of als het probleem optreedt in een cmdlet die slechts één object accepteert of retourneert.

- Een fout is een niet-afsluit fout als u wilt dat uw cmdlet doorgaat met de verwerking van het huidige object en andere invoer objecten.

- Een fout is een niet-afsluit fout als deze is gerelateerd aan een specifiek invoer object of subset van invoer objecten.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-foutrecords](./windows-powershell-error-records.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
