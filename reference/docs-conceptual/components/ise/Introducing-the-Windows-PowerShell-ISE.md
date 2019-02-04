---
ms.date: 08/14/2018
keywords: PowerShell-cmdlet
title: Kennismaking met Windows PowerShell ISE
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685100"
---
# <a name="the-windows-powershell-ise"></a>De Windows PowerShell ISE

De Windows PowerShell Integrated Scripting Environment (ISE) is een hosttoepassing voor Windows PowerShell. U kunt in de ISE uitvoeren van opdrachten en schrijven, testen en fouten opsporen in scripts in een enkel Windows-gebruikersinterface op basis van afbeeldingen. Het ISE biedt met meerdere regels bewerken tab-aanvulling, syntaxiskleuren, selectief worden uitgevoerd, contextgevoelige help en ondersteuning voor talen van rechts naar links. Sneltoetsen en menu-items worden toegewezen aan veel van dezelfde taken die u in de Windows PowerShell-console doen zou. Bijvoorbeeld, wanneer u fouten opsporen in een script in de ISE, u kunt met de rechtermuisknop op een regel met code in het bewerkingsvenster een onderbrekingspunt instellen.

## <a name="support"></a>Ondersteuning

Het ISE eerst werd geïntroduceerd in Windows PowerShell V2 en is opnieuw ontworpen met PowerShell V3. Het ISE wordt ondersteund in alle ondersteunde versies van Windows PowerShell tot en met Windows PowerShell V5.1. De ISE is echter in de onderhoudsmodus bevindt en geen nieuwe functies zijn waarschijnlijk moet worden toegevoegd.
Daarnaast is er geen ondersteuning voor ISE met PowerShell v6 en daarbuiten. Gebruikers die een grafisch hulpprogramma voor het beheren van PowerShell-scripts, enzovoort, waarmee rekening moeten houden [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Belangrijkste functies

Belangrijke functies in Windows PowerShell ISE omvatten:

- Met meerdere regels bewerken: Voor het invoegen van een lege regel onder de huidige regel in het opdrachtvenster, drukt u op SHIFT + ENTER.
- Selectief worden uitgevoerd: Voor het onderdeel van een script uitvoeren, selecteert u de tekst die u wilt uitvoeren, en klik vervolgens op de **-Script uitvoeren** knop. Of druk op F5.
- Contextgevoelige help: Type **Invoke-Item**, en druk op F1 drukt. Het Help-bestand wordt geopend op het artikel voor de **Invoke-Item** cmdlet.

De Windows PowerShell ISE kunt u bepaalde aspecten van de weergave aanpassen. Het bevat ook een eigen Windows PowerShell-script voor profiel.

## <a name="to-start-the-windows-powershell-ise"></a>De Windows PowerShell ISE starten

Klik op **Start**, selecteer **Windows PowerShell**, en klik vervolgens op **Windows PowerShell ISE**.
U kunt ook typen `powershell_ise.exe` in elke opdrachtshell of in het vak uitvoeren.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Om hulp te krijgen in de Windows PowerShell ISE

Op de **Help** menu, klikt u op **Windows PowerShell Help**. Of op F1 drukt. Het bestand dat geopend wordt Windows PowerShell ISE- en Windows PowerShell, met inbegrip van alle van de Help-informatie van de cmdlet Get-Help beschreven.
