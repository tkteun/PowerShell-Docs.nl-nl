---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell Integrated Scripting Environment (ISE)
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 3002c2cb7213b1c2d7201dddf5ff3c0651fad767
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057482"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell ISE (Integrated Scripting Environment)

De Windows PowerShell Integrated Scripting Environment (ISE) is een van twee hosts voor de Windows PowerShell-engine en taal. U kunt schrijven, uitvoeren en scripts testen op een manier die niet beschikbaar in de Windows PowerShell-Console zijn. Het ISE wordt toegevoegd, syntaxis kleur, tab-aanvulling, IntelliSense, visuele foutopsporing en contextgevoelige Help.

Het ISE kunt u opdrachten uitvoeren in een consolevenster, maar ondersteunt ook deelvensters die u gebruiken kunt om de broncode van uw script en andere hulpprogramma's die in de ISE kunnen aansluiten tegelijkertijd weer te geven. U kunt zelfs meerdere script Windows openen op hetzelfde moment, dit met name handig is wanneer u fouten wilt opsporen met een script dat gebruikmaakt van functies die zijn gedefinieerd in andere scripts of modules.

## <a name="whats-new"></a>What's New in System Center 2012 - Data Protection Manager (Wat is nieuw in System Center 2012 - Data Protection Manager)

Hier volgen enkele van de functies die zijn toegevoegd aan de ISE in de meest recente versies van PowerShell.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Toegevoegd in PowerShell 3.0 (WindowsServer 2012, Windows 8)

**IntelliSense** is uw opdrachten automatisch voltooid door het weergeven van menu's van de overeenkomende cmdlets, parameters, parameterwaarden, bestanden of mappen terwijl u typt.

**Codefragmenten** korte gedeelten van de code die u eenvoudig in de scripts uw schrijven invoegen kunt zijn. Een verzameling van codefragmenten nuttig is opgenomen in het vak en kunt u meer met behulp van de **New-fragment** cmdlet.

**Invoegtoepassingen** die toevoegen functies naar de ISE kunnen worden gemaakt met het schrijven van code die met communiceert [de Windows PowerShell ISE Scripting-Object Model](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Deze hulpprogramma's kunnen besturingselementen in een deelvenster met tabbladen voor weergave of onzichtbaar werken op de achtergrond. De **opdrachten** invoegtoepassing is een goed voorbeeld en is opgenomen in versie 3.0 en hoger die een lijst van de beschikbare opdrachten en Help-informatie wordt weergegeven.

**Opnieuw opstarten van de Manager en automatisch opslaan** automatisch opslaan uw scripts elke twee minuten om te voorkomen dat het verlies van gegevens van uw werk in het geval van een crash of onverwacht opnieuw opgestart.

**De meeste lijst van de laatstgebruikte** maakt nu deel uit van het menu bestand openen zodat u gemakkelijk om te gaan naar de bestanden die u vaak gebruikt.

**Samengevoegde consolevenster**. In eerdere versies van de ISE zijn er afzonderlijke deelvensters van de opdracht en het resultaat. Ze zijn nu met de gecombineerd tot één deelvenster dat meer rechtstreeks lijkt op wat u ziet in de Windows PowerShell-Console.

**Opdrachtregelopties**. Verschillende nieuwe opdrachtregelopties geven u meer controle over de werking van de ISE. Het ISE - NoProfile gestart zonder dat een profiel-script is uitgevoerd. -Een help-venster met de ISE help wordt geopend. -mta begint de ISE in 'modus apartment meerdere threads'. De standaardwaarde is één thread.

**Nieuwe functies van de editor** eenvoudiger te maken en lezen van uw code:

- **XML-syntaxiskleuren**. XML-syntaxis kleuren de ISE-editor nu op dezelfde manier als deze syntaxis voor Windows PowerShell-code kleuren.

- **Accolade die overeenkomt met**. De ISEWindows PowerShell ISE markeert overeenkomende accolades om te helpen u te controleren of het juiste aantal accolades zodat deze overeenkomt met uw openen wordt gesloten zijn. Gebruik de CTRL -\[ te vinden van de accolade sluiten die overeenkomt met de openingsaccolade die de cursor zich bevindt.

- **Overzichtsweergave**. U kunt samenvouwen of uitvouwen secties van uw code door te klikken op het plusteken en minteken zijn in de linkermarge. Dit maakt het gemakkelijker te vinden van de code die u in een lange script zoekt.

- **Slepen en neerzetten tekstbewerking**. U kunt een blok tekst selecteren en sleep deze naar een andere locatie te verplaatsen. Als u u de Ctrl-toets houdt terwijl u sleept u de geselecteerde tekst die u in plaats van verplaatsen.

- **De weergave van fouten parseren**. Windows PowerShell onderzoekt uw script terwijl u typt. Als er een fout wordt gedetecteerd, wordt een rode golflijn onder de strijdige code weergegeven. Wanneer u de muisaanwijzer over de fout aangegeven, ziet u een knopinfo het probleem dat is gevonden.

- **Zoom**. U kunt inzoomen op uw tekst gemakkelijker te lezen of uitzoomen om te zien van het grote geheel met behulp van de schuifregelaar in de rechterbenedenhoek van de ISE-venster.

- **Uitgebreide tekst kopiëren en plakken**. Wanneer u kopiëren van de ISE naar het Klembord, het lettertype, grootte en kleurinformatie van de geselecteerde tekst wordt opgenomen.

- **Selectie blokkeren**. U kunt een vorm van blok-segment van de tekst selecteren door de ALT-toets ingedrukt te houden bij het selecteren van tekst in het scriptvenster met de muis, of door te drukken **Alt + Shift + pijltoets**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Toegevoegd in PowerShell 2.0 (Windows Server 2008 R2, Windows 7)

Het ISE is met PowerShell versie 2.0 geïntroduceerd.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Vereisten voor het uitvoeren van de Windows PowerShell ISE

Het ISE is beschikbaar op elke Windows-computer met Windows PowerShell versie 2.0 of hoger. Elke versie van Windows en Windows Server bevat een versie van Windows PowerShell en de ISE, maar u kunt upgraden naar de meest recente beschikbare door het installeren van de Windows Management Framework (WMF). Zie de [WMF](/powershell/wmf) documentatie voor meer informatie.

> [!NOTE]
> Omdat Windows PowerShell ISE een grafische gebruikersinterface vereist, kunt u deze niet uitvoeren op de optie Server Core van Windows Server.

## <a name="see-also"></a>Zie ook

[Doel van de windows power shell ise Scriptobjectmodel](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)