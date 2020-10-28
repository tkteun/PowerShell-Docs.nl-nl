---
ms.date: 09/13/2016
ms.topic: reference
title: Foutgegevens weergeven
description: Foutgegevens weergeven
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653061"
---
# <a name="displaying-error-information"></a>Foutgegevens weergeven

In dit onderwerp worden de manieren beschreven waarop gebruikers fout gegevens kunnen weer geven.

Wanneer de cmdlet een fout tegen komt, is de presentatie van de fout informatie standaard vergelijkbaar met de volgende fout uitvoer.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Gebruikers kunnen echter fouten op categorie bekijken door de `$ErrorView` variabele in te stellen `"CategoryView"` op. In de categorie weergave worden specifieke gegevens uit de fout record weer gegeven in plaats van een vrije-tekst beschrijving van de fout. Deze weer gave kan nuttig zijn als u een lange lijst met fouten wilt scannen. In de categorie weergave wordt het vorige fout bericht als volgt weer gegeven.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout categorieën.

## <a name="see-also"></a>Zie ook

[Windows PowerShell-foutrecords](./windows-powershell-error-records.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
