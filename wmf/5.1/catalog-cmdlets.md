---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
title: Catalogus-cmdlets
ms.openlocfilehash: f0869e8c174ab127996866775ad20d056f877345
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="catalog-cmdlets"></a>Catalogus-Cmdlets  

We hebben twee nieuwe cmdlets in toegevoegd [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) module die u wilt genereren en bestanden voor windows-catalogus te valideren.  

## <a name="new-filecatalog"></a>Nieuwe FileCatalog 
--------------------------------

`New-FileCatalog`maakt een windows-catalogusbestand voor mappen en bestanden. Een catalogusbestand bevat hashes voor alle bestanden in de opgegeven paden. De set mappen samen met het catalogusbestand die deze mappen vertegenwoordigt overeenkomt, kunnen gebruikers distribueren. Een catalogusbestand kan worden gebruikt door de ontvanger van inhoud wilt controleren of er wijzigingen zijn aangebracht in de mappen nadat de catalogus is gemaakt.    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Wij ondersteunen maken catalogusversie 1 en 2. Versie 1 maakt gebruik van SHA1-hash-algoritme voor het maken van bestands-hashes en versie 2 SHA256 gebruikt. Catalogusversie 2 van de wordt niet ondersteund op *Windows Server 2008 R2* en *Windows 7*. Het is raadzaam om catalogusversie 2 van de gebruiken als platforms *Windows 8*, *Windows Server 2012* en hoger.  

Geef de CatalogFilePath en het pad variabelen zodat deze overeenkomen met de locatie van de module-manifest voor het gebruik van deze opdracht op een bestaande module. In het onderstaande voorbeeld is de module-manifest in C:\Program Files\Windows PowerShell\Modules\Pester. 

![](../images/NewFileCatalog.jpg)

Hiermee maakt u het catalogusbestand. 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

Om te controleren of de integriteit van een catalogusbestand (Pester.cat in bovenstaande voorbeeld) moet het worden ondertekend met behulp van de [Set AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.   


## <a name="test-filecatalog"></a>Test FileCatalog 
--------------------------------

`Test-FileCatalog`valideert de catalogus die vertegenwoordigt een reeks mappen. 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Deze cmdlet vergelijkt de hashes van alle bestanden en hun relatieve paden gevonden in het catalogusbestand met zijn opgeslagen op schijf. Als er een discrepantie tussen het bestands-hashes en paden gedetecteerd wordt de status van `ValidationFailed`. Gebruikers kunnen ophalen met alle deze informatie met behulp van de `Detailed` overschakelen. De status van de ondertekening van de catalogus wordt weergegeven als de `Signature` veld hetzelfde als het aanroepen is de [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) cmdlet uit op het catalogusbestand. Gebruikers kunnen ook een bestand tijdens de validatie overslaan met behulp van de `FilesToSkip` parameter. 

