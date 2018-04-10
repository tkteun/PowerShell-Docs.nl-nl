---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell Integrated Scripting Environment ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: d116ec107c2d07e9fd55ee974008b3636b4ab049
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell ISE (Integrated Scripting Environment)

De Windows PowerShell Integrated Scripting Environment (ISE) is een van twee hosts voor de Windows PowerShell-engine en taal. Met hockeyapp die kunt u uitvoeren en scripts te testen op een manier die niet beschikbaar in de Windows PowerShell-Console zijn. De ISE voegt de syntaxis van de kleuren, tab-Aanvulling IntelliSense, visuele foutopsporing en contextgevoelige Help.

De ISE kunt u opdrachten uitvoeren in een consolevenster, maar ondersteunt ook deelvensters die u gebruiken kunt om de broncode van uw script en andere hulpprogramma's die in de ISE kunnen aansluiten tegelijkertijd weer te geven. U kunt zelfs meerdere script Windows openen op hetzelfde moment, dit vooral nuttig is wanneer u een script dat gebruikmaakt van functies die zijn gedefinieerd in andere scripts of modules foutopsporing.

## <a name="whats-new"></a>What's New in System Center 2012 - Data Protection Manager (Wat is nieuw in System Center 2012 - Data Protection Manager)

Hier zijn enkele van de functies die zijn toegevoegd aan de ISE in de meest recente versies van PowerShell.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Toegevoegd in PowerShell 3.0 (WindowsServer 2012, Windows 8)

**IntelliSense** automatisch ingevuld uw opdrachten door de menu's van de overeenkomende cmdlets, parameters, parameterwaarden bestanden of mappen worden weergegeven terwijl u typt.

**Codefragmenten** korte gedeelten van code die u eenvoudig in de scripts uw schrijven invoegen kunt. Een verzameling van nuttig codefragmenten is opgenomen in het vak en kunt u meer met behulp van de **nieuw codefragment** cmdlet.

**Invoegtoepassingen** die toevoegen de ISE-functies kunnen worden gemaakt door schrijven van code die met communiceert [de Windows PowerShell ISE Scripting Object Model](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Deze hulpprogramma's kunnen besturingselementen in een deelvenster met tabbladen worden weergegeven of REF werken op de achtergrond. De **opdrachten** invoegtoepassing is een goed voorbeeld en is opgenomen in versie 3.0 en hoger die een lijst van de beschikbare opdrachten en hun Help weergegeven.

**Opnieuw opstarten van de Manager en automatisch opslaan** automatisch elke twee minuten opslaan uw scripts om te voorkomen dat het verlies van uw werk in het geval van een computer vastloopt of onverwacht opnieuw opgestart.

**Lijst van de meeste laatstgebruikte** maakt nu deel uit van het menu bestand openen om het gemakkelijker om te krijgen tot de bestanden die u vaak gebruikt.

**Samengevoegde consolevenster**. In eerdere versies van de ISE zijn er afzonderlijke opdracht en uitvoer deelvensters. Ze nu gecombineerd tot één of meer rechtstreeks lijkt op wat u ziet in de Windows Powershell-Console.

**Opdrachtregelopties**. Verschillende nieuwe opdrachtregelopties bieden u meer controle over de werking van de ISE. De ISE - NoProfile gestart zonder dat een script profiel uitvoeren. -Een help-venster met de ISE help wordt geopend. -mta begint de ISE in 'met meerdere threads apartment-modus'. De standaardwaarde is één thread.

**Nieuwe functies van de editor** gemakkelijker te maken en uw code te lezen:

- **XML-syntaxiskleuren**. De ISE-editor nu de kleuren van XML-syntaxis op dezelfde manier als het Windows PowerShell-codesyntaxis kleuren.

- **Overeenkomende accolade**. De ISEWindows PowerShell ISE licht overeenkomende accolades waarmee u Zorg ervoor dat u hebt het juiste aantal haakje sluiten zodat deze overeenkomen met uw openen toepassingsgroepen. Gebruik CTRL -\[ vinden de accolade sluiten die overeenkomt met de openingsaccolade die de cursor zich bevindt.

- **Overzichtsweergave**. U kunt samenvouwen of secties van uw code uitbreiden door te klikken op het plusteken en minteken zijn in de linkermarge. Dit vergemakkelijkt het vinden van de code die u in een lange script zoekt.

- **Slepen en neerzetten tekstbewerking**. U kunt een blok tekst selecteren en sleep deze naar een andere locatie om deze te verplaatsen. Als u Houd de Ctrl-toets ingedrukt terwijl u de geselecteerde tekst die u in plaats van kopiëren sleept verplaatsen.

- **Parseren van de weergave van fouten**. Windows PowerShell onderzoekt uw script terwijl u typt. Als er een fout wordt gedetecteerd, wordt een rode kronkeltje onder de strijdige code. Wanneer u de muisaanwijzer op de aangegeven fout, ziet u een tooltip het probleem dat is gevonden.

- **Zoom**. U kunt inzoomen op uw tekst gemakkelijker te lezen of uitzoomen om te zien van de grotere afbeelding met behulp van de schuifregelaar in de rechterbenedenhoek van de ISE-venster.

- **Rich text kopiëren en plakken**. Wanneer u kopiëren van de ISE naar het Klembord, het lettertype, grootte en kleurinformatie van de geselecteerde tekst is opgenomen.

- **Blok selecteren**. U kunt een segment blok vorm van tekst selecteren door de ALT-toets ingedrukt te houden bij het selecteren van tekst in het deelvenster script met de muis of door op **Alt + Shift + pijl**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Toegevoegd in PowerShell 2.0 (Windows Server 2008 R2, Windows 7)

De ISE is geïntroduceerd in PowerShell versie 2.0.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Vereisten voor het uitvoeren van de Windows PowerShell ISE

De ISE is beschikbaar op elke Windows-computer met Windows PowerShell versie 2.0 of hoger. Elke versie van Windows en Windows Server bevat een versie van Windows PowerShell en de ISE, maar u kunt upgraden naar de meest recente beschikbare door de Windows Management Framework (WMF) installeren. Zie de [WMF](/powershell/wmf/readme) documentatie voor meer informatie.

> [!NOTE]
> Windows PowerShell ISE vereist een grafische gebruikersinterface, kan niet worden uitgevoerd op de optie Server Core van Windows Server.

## <a name="see-also"></a>Zie ook

[Doel van de windows power shell ise-objectmodel scripting](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)