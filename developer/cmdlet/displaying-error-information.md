---
title: Weergeven van informatie over de fout | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848403"
---
# <a name="displaying-error-information"></a>Foutgegevens weergeven

In dit onderwerp worden de manieren waarop gebruikers informatie over de fout kunnen weergeven.

Wanneer de cmdlet een fout optreedt, de presentatie van gegevens van de fout ziet, standaard eruit als in de volgende foutuitvoer.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Echter gebruikers fouten kunnen weergeven op categorie door in te stellen de `$ErrorView` variabele `"CategoryView"`. Categorieweergave bevat specifieke gegevens uit de foutrecord in plaats van een vrije tekst beschrijving van de fout. In deze weergave is handig als u hebt een lange lijst met fouten om te scannen. In de Categorieweergave, wordt als volgt het vorige foutbericht weergegeven.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Zie voor meer informatie over foutcategorieën [Windows PowerShell-foutrecords](./windows-powershell-error-records.md).

## <a name="see-also"></a>Zie ook

[Windows PowerShell-foutrecords](./windows-powershell-error-records.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
