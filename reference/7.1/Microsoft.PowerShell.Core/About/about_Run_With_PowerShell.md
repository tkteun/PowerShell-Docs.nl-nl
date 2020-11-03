---
description: Hierin wordt uitgelegd hoe u de functie uitvoeren met Power shell gebruikt om een script uit te voeren vanuit een bestandssysteem station.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 83931fcfcc89340b1d4958e41cb182642a554737
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252858"
---
# <a name="about-run-with-powershell"></a>Over uitvoeren met Power shell

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt uitgelegd hoe u de functie uitvoeren met Power shell gebruikt om een script uit te voeren vanuit een bestandssysteem station.

## <a name="long-description"></a>LANGE BESCHRIJVING

Vanaf Windows Power Shell 3,0 kunt u de functie uitvoeren met Power shell gebruiken om scripts uit te voeren vanuit Verkenner in Windows 8 en Windows Server 2012 en Windows Verkenner in eerdere versies van Windows.

De functie ' uitvoeren met Power shell ' is ontworpen voor het uitvoeren van scripts waarvoor geen vereiste para meters zijn en die geen uitvoer retour neren naar de opdracht prompt.

Wanneer u de functie ' uitvoeren met Power shell ' gebruikt, wordt het Power shell-console venster alleen kort weer gegeven. U kunt er niet mee communiceren.

De functie ' uitvoeren met Power shell ' gebruiken:

Klik in Verkenner (of Windows Verkenner) met de rechter muisknop op de naam van het script bestand en selecteer vervolgens uitvoeren met Power shell.

De functie uitvoeren met Power shell start een Power shell-sessie met een uitvoerings beleid voor overs Laan, voert het script uit en sluit de sessie.

Er wordt een opdracht uitgevoerd met de volgende indeling:

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

Met ' uitvoeren met Power shell ' stelt u het uitvoerings beleid overs Laan alleen in voor de sessie (het huidige exemplaar van het Power Shell-proces) waarin het script wordt uitgevoerd.
Deze functie wijzigt het uitvoerings beleid voor de computer of de gebruiker niet.

De functie ' uitvoeren met Power shell ' is alleen van invloed op het uitvoerings beleid voor alles ondertekend. Als het alles ondertekend-uitvoerings beleid van kracht is voor de computer of de gebruiker, voert ' uitvoeren met Power shell ' alleen ondertekende scripts uit. ' Uitvoeren met Power shell ' wordt niet beïnvloed door andere uitvoerings beleid. Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie.

Opmerking voor probleem oplossing: met de Power shell-opdracht wordt u mogelijk gevraagd de wijziging van het uitvoerings beleid te bevestigen.

## <a name="see-also"></a>ZIE OOK

[about_Execution_Policies](about_Execution_Policies.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Scripts](about_Scripts.md)

