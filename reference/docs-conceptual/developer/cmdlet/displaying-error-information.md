---
title: Fout informatie weer geven | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774572"
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
