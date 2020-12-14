---
description: Hierin worden de beschik baarheid en het doel van uitvoer stromen in Power shell uitgelegd.
Locale: en-US
ms.date: 10/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_output_streams?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Output_Streams
ms.openlocfilehash: 1dd6424ea14aa241b084a0a2c97a7e9bf6927518
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706090"
---
# <a name="about-output-streams"></a>Over uitvoer stromen

## <a name="short-description"></a>Korte beschrijving
Hierin worden de beschik baarheid en het doel van uitvoer stromen in Power shell uitgelegd.

## <a name="long-description"></a>Lange beschrijving

Power shell biedt meerdere uitvoer stromen. De streams bieden kanalen voor verschillende typen berichten. U kunt schrijven naar deze streams met behulp van de bijbehorende cmdlet of omleiding. Zie [about_Redirection](about_Redirection.md)voor meer informatie.

Power shell ondersteunt de volgende uitvoer stromen.

| Bitsnelheid # |      Description       | Geïntroduceerd in  |    Cmdlet schrijven     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **Geslaagde** stroom     | Power Shell 2,0 | `Write-Output`      |
| 2        | **Fout** stroom       | Power Shell 2,0 | `Write-Error`       |
| 3        | **Waarschuwings** stroom     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **Uitgebreide** stroom     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **Fout opsporing** stroom       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **Informatie** stroom | PowerShell 5.0 | `Write-Information` |
| n.v.t.      | **Voortgangs** stroom    | PowerShell 3.0 | `Write-Progress`    |

> [!NOTE]
> Omleiding wordt niet ondersteund door de **voortgangs** stroom.

## <a name="success-stream"></a>Geslaagde stroom

De **geslaagde** stroom is de standaard stroom voor normale, geslaagde resultaten.
Gebruik de `Write-Output` cmdlet om objecten expliciet naar deze stroom te schrijven. Deze stroom wordt gebruikt voor het door geven van objecten via de Power shell-pijp lijn. De stroom voor **successen** is verbonden met de **stdout** -stroom voor systeem eigen toepassingen.

## <a name="error-stream"></a>Fout stroom

De **fout** stroom is de standaard stroom voor fout resultaten. Gebruik de `Write-Error` cmdlet om expliciet naar deze stroom te schrijven. De **fout** stroom is verbonden met de **stderr** -stroom voor systeem eigen toepassingen. Onder de meeste omstandigheden kan deze fout de uitvoerings pijplijn beëindigen. Fouten die naar deze stroom worden geschreven, worden ook toegevoegd de `$Error` Automatische variabele. Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.

## <a name="warning-stream"></a>Waarschuwings stroom

De **waarschuwing** stroom is bedoeld voor fout voorwaarden die minder ernstig zijn dan fouten die worden geschreven naar de **fout** stroom. Onder normale omstandigheden wordt de uitvoering van deze waarschuwingen niet beëindigd. Waarschuwingen worden niet naar de `$Error` Automatische variabele geschreven. Gebruik de `Write-Warning` cmdlet om expliciet naar deze stroom te schrijven.

## <a name="verbose-stream"></a>Uitgebreide stroom

De **uitgebreide** stroom is bedoeld voor berichten die gebruikers helpen bij het oplossen van opdrachten die interactief of vanuit een script worden uitgevoerd. Gebruik de `Write-Verbose` cmdlet om berichten in deze stroom expliciet te schrijven. Veel cmdlets bieden uitgebreide uitvoer die nuttig is voor het leren van de interne werking van de cmdlet. De uitgebreide berichten worden alleen uitgevoerd wanneer u de `-Verbose` para meter common gebruikt. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.

## <a name="debug-stream"></a>Fout opsporing stroom

De stroom voor **fout opsporing** wordt gebruikt voor berichten die scripters begrijpen waarom de code mislukt. Gebruik de `Write-Debug` cmdlet om expliciet naar deze stroom te schrijven. De fout opsporingsgegevens worden alleen uitgevoerd wanneer u de `-Debug` para meter common gebruikt. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.

Debug-berichten zijn bedoeld voor script-en cmdlet-ontwikkel aars meer dan eind gebruikers. Deze fout berichten kunnen interne gegevens bevatten die nodig zijn voor uitgebreide probleem oplossing.

## <a name="information-stream"></a>Informatie stroom

De **informatie** stroom is bedoeld om berichten te leveren die een gebruiker helpen begrijpen wat een script doet. Het kan ook worden gebruikt door ontwikkel aars als een extra stream die wordt gebruikt om gegevens door te geven via Power shell. De ontwikkelaar kan stroom gegevens labelen en specifieke verwerking voor die stroom hebben. Gebruik de `Write-Information` cmdlet om expliciet naar deze stroom te schrijven.

## <a name="progress-stream"></a>Voortgangs stroom

De **voortgangs** stroom wordt gebruikt voor berichten waarmee de voortgang wordt gecommuniceerd met meer opdrachten en scripts. Gebruik de `Write-Progress` cmdlet om berichten in deze stroom expliciet te schrijven. Omleiding wordt niet ondersteund door de **voortgangs** stroom.

## <a name="see-also"></a>Zie ook

- [Schrijf fouten opsporen](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Schrijf fout](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Schrijf voortgang](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Waarschuwing voor schrijven](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_CommonParameters](about_CommonParameters.md)
- [about_Redirection](about_Redirection.md)
