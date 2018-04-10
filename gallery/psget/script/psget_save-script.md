---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a>Save-Script

Opslaan Script cmdlet kunt u het scriptbestand bekijken door op een opgegeven locatie op te slaan.

## <a name="description"></a>Beschrijving

Het opgegeven script Hiermee slaat u de cmdlet opslaan-Script.

## <a name="cmdlet-syntax"></a>De syntaxis van cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Verwijzing naar het online help van cmdlet

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Voorbeeldopdrachten

### <a name="example-1-save-a-script-from-a-repository"></a>Voorbeeld 1: Een script uit een bibliotheek opslaan
Deze opdracht slaat u de nieuwste versie van het script Fabrikam-ClientScript vanuit GalleryINT opslagplaats naar de lokale map C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Voorbeeld 2: Een versie van een script opslaan door piping van de cmdlet Find-Script

De eerste opdracht Zoeken naar versie 1.5 van Fabrikam-ClientScript vanuit de opslagplaats GalleryINT en opgeslagen in de map C:\ScriptSharingDemo

De tweede opdracht valideert de metagegevens van de opgeslagen script.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a>Voorbeeld 3: Een voorlopige versie van een script uit een bibliotheek opslaan
Deze opdracht slaat u de nieuwste versie van het script Fabrikam-ClientScript vanuit GalleryINT opslagplaats naar de lokale map C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```