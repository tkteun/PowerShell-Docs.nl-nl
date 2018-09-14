---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Catalogus-cmdlets
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522885"
---
# <a name="catalog-cmdlets"></a>Catalogus-Cmdlets

Hebben we twee nieuwe cmdlets in toegevoegd [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module te genereren en bestanden van windows-catalogus te valideren.

## <a name="new-filecatalog"></a>Nieuwe FileCatalog
--------------------------------

`New-FileCatalog` Hiermee maakt u een windows-catalogusbestand voor set van bestanden en mappen. Een catalogusbestand bevat-hashes voor alle bestanden in de opgegeven paden. Gebruikers kunnen de set van mappen, samen met de catalogusbestand met deze mappen overeenkomt distribueren. Een catalogusbestand kan worden gebruikt door de ontvanger van inhoud te valideren of eventuele wijzigingen zijn aangebracht in de mappen nadat de catalogus is gemaakt.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
We ondersteuning voor het maken van het catalogusversie 1 en 2. Versie 1 maakt gebruik van SHA1-hash-algoritme om bestands-hashes en versie 2 gebruikt SHA256 te maken. Catalogusversie 2 wordt niet ondersteund op *Windows Server 2008 R2* en *Windows 7*. Het verdient aanbeveling catalogusversie 2 gebruiken als platforms *Windows 8*, *Windows Server 2012* en hoger.

Geef de CatalogFilePath en het pad variabelen zodat deze overeenkomt met de locatie van de module-manifest voor het gebruik van deze opdracht op een bestaande module. In het onderstaande voorbeeld is de module-manifest in C:\Program Files\Windows PowerShell\Modules\Pester.

![](../images/NewFileCatalog.jpg)

Hiermee maakt u het catalogusbestand.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Om te controleren of de integriteit van een catalogusbestand (Pester.cat in bovenstaande voorbeeld) moet het worden ondertekend met behulp van de [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.


## <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

`Test-FileCatalog` Hiermee valideert u de catalogus voor een set van mappen.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Deze cmdlet vergelijkt de hashes van alle bestanden en hun relatieve paden gevonden in het catalogusbestand met resources op schijf opgeslagen. Als er overeenkomende bestands-hashes en paden gedetecteerd wordt de status van `ValidationFailed`.
Gebruikers kunnen ophalen van alle deze informatie met behulp van de `Detailed` overschakelen. De status van de ondertekening van de catalogus wordt weergegeven als de `Signature` veld, die hetzelfde is als het aanroepen de [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet uit op de catalog-bestand.
Gebruikers kunnen ook een bestand tijdens de validatie overslaan met behulp van de `FilesToSkip` parameter.
