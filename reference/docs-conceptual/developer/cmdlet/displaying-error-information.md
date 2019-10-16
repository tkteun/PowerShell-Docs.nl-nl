---
title: Fout informatie weer geven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359367"
---
# <a name="displaying-error-information"></a>Foutgegevens weergeven

In dit onderwerp worden de manieren beschreven waarop gebruikers fout gegevens kunnen weer geven.

Wanneer de cmdlet een fout tegen komt, is de presentatie van de fout informatie standaard vergelijkbaar met de volgende fout uitvoer.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Gebruikers kunnen echter fouten op categorie bekijken door de variabele `$ErrorView` in te stellen op `"CategoryView"`. In de categorie weergave worden specifieke gegevens uit de fout record weer gegeven in plaats van een vrije-tekst beschrijving van de fout. Deze weer gave kan nuttig zijn als u een lange lijst met fouten wilt scannen. In de categorie weergave wordt het vorige fout bericht als volgt weer gegeven.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout categorieën.

## <a name="see-also"></a>Zie ook

[Windows Power Shell-fout records](./windows-powershell-error-records.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
