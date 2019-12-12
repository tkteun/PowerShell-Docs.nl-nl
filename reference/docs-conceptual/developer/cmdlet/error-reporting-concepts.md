---
title: Concepten voor fouten rapportage | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355655"
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

[Windows Power Shell-fout records](./windows-powershell-error-records.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
