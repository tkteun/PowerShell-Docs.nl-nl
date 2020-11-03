---
description: Hierin worden de functies en systeem vereisten beschreven van Windows Power shell Integrated Scripting Environment (ISE).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_ISE
ms.openlocfilehash: ec99dec9ea5012b41c10a56a688b23a6fa2c9dd8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252721"
---
# <a name="about-windows-powershell-ise"></a>Over Windows PowerShell ISE

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin worden de functies en systeem vereisten beschreven van Windows Power shell Integrated Scripting Environment (ISE).

## <a name="long-description"></a>LANGE BESCHRIJVING

Windows PowerShell ISE is een grafische hosttoepassing voor Windows Power shell.
In Windows PowerShell ISE kunt u in één op Windows gebaseerde Graphical User Interface opdrachten uitvoeren en scripts schrijven, testen en fouten opsporen. De functies omvatten IntelliSense, het bewerken van meerdere regels, het volt ooien van tabbladen, automatisch opslaan, syntaxis kleuren, selectief uitvoeren, context gevoelige Help, opdracht weer geven (opdrachten in een venster opstellen) en ondersteuning voor dubbel-byte teken sets en talen van rechts naar links.

Windows PowerShell ISE is een uitstekend hulp programma voor beginners. Op het tabblad Opdrachtvenster en nieuw externe Power shell kunt u taken door lopen, zodat u met de eerste try-out op de juiste manier zou kunnen slagen. Fragmenten en fout indicatoren helpen u bij het leren van de Windows Power shell-taal terwijl u werkt.

Ervaren gebruikers kunnen profiteren van de geavanceerde functies voor fout opsporing, invoeg toepassingen en het Windows PowerShell ISE-object model.

Wat is er nieuw in Windows PowerShell ISE in Windows Power Shell 4,0

Windows PowerShell ISE introduceert twee nieuwe functies in Windows Power Shell 4,0.

- Windows PowerShell ISE ondersteunt nu zowel Windows Power shell-werk stroom fout opsporing als externe script fout opsporing. Zie about_Debuggers voor meer informatie.

- IntelliSense-ondersteuning is toegevoegd voor de gewenste status configuratie providers en configuraties van Windows Power shell.

## <a name="starting-windows-powershell-ise"></a>Windows PowerShell ISE starten

Windows PowerShell ISE is geïnstalleerd, ingeschakeld en klaar voor gebruik in alle ondersteunde versies van Windows.

- In Windows 8,1, Windows 8, Windows Server 2012 R2 en Windows Server 2012 typt u PowerShell_ISE in het scherm Start en klikt u vervolgens op PowerShell_ISE of Windows PowerShell ISE.

- Klik in Windows Server 2012 R2 en Windows Server 2012, in Serverbeheer, in het menu Extra op Windows PowerShell ISE.

- In eerdere versies van Windows, klikt u op Start, alle Program Ma's, accessoires en Windows Power shell, en klikt u vervolgens op Windows PowerShell ISE.

- In een Windows Power shell-console, Cmd.exe of het vak uitvoeren of zoeken in Windows typt u ' PowerShell_ise.exe '. U kunt ook de opdracht regel parameters gebruiken, met inbegrip van de schakel optie geen profiel. Zie de [ Help vanPowerShell_ISE.exe-console](about_powershell_ise_exe.md)voor meer informatie.

## <a name="running-interactive-commands"></a>Interactieve opdrachten uitvoeren

U kunt een Windows Power shell-expressie of-opdracht uitvoeren in Windows PowerShell ISE. U kunt met behulp van cmdlets, providers, modules en modules werken zoals u deze in de Windows Power shell-console zou gebruiken.

U kunt interactieve opdrachten in het console venster typen of plakken. Als u de opdrachten wilt uitvoeren, kunt u knoppen, menu opdrachten en sneltoetsen gebruiken.

U kunt de functie voor het bewerken van meerdere regels gebruiken om verschillende regel code in het console venster tegelijk te typen of te plakken. Wanneer u op de pijl-omhoog drukt om de vorige opdracht te halen, worden alle regels in de opdracht ingetrokken. Wanneer u opdrachten typt, drukt u op SHIFT + ENTER om een nieuwe lege regel weer te geven onder de huidige regel.

## <a name="viewing-output"></a>Uitvoer weer geven

De resultaten van opdrachten en scripts worden weer gegeven in het console venster. U kunt de resultaten vanuit het console venster verplaatsen of kopiëren met behulp van sneltoetsen of de knop kopiëren op de werk balk, en u kunt de resultaten plakken in het script-of console deel venster of andere Program ma's. Als u het console venster wilt wissen, klikt u op de knop uitvoer paneel wissen of typt u een van de volgende opdrachten:

```
Clear-Host
cls
```

## <a name="writing-scripts-and-functions"></a>Scripts en functies schrijven

In het deel venster script kunt u scripts openen, opstellen, bewerken en uitvoeren. In het deel venster script kunt u scripts bewerken met behulp van knoppen en sneltoetsen. U kunt ook tekst kopiëren, knippen en plakken tussen het Script venster en het console venster.

U kunt de functie selectief uitvoeren gebruiken om een script geheel of gedeeltelijk uit te voeren. Als u een deel van een script wilt uitvoeren, selecteert u de tekst die u wilt uitvoeren en klikt u vervolgens op de knop selectie uitvoeren of drukt u op F8. F8 voert standaard de huidige regel uit.

Geavanceerde bewerkings functies zijn onder meer accolades, verg Roten/verkleinen, regel nummers, fout indicatoren, blok bewerken en inspringen, uitgebreide kopie en hoofdletter conversie.

## <a name="getting-help"></a>Hulp krijgen

Windows PowerShell ISE bevat Help-onderwerpen waarin het gebruik wordt beschreven. Daarnaast zijn alle geïnstalleerde Help-bestanden toegankelijk vanuit het script en de opdracht deel Vensters.

Windows PowerShell ISE biedt ook ondersteuning voor context gevoelige Help. Als u hulp wilt krijgen over een bepaalde cmdlet, provider of tref woord, plaatst u de cursor in de naam van het item en drukt u op F1. Als u de Help-onderwerpen wilt doorzoeken, drukt u op F1 en typt u de zoek term.

Als u de Help-onderwerpen op de computer wilt bijwerken, gebruikt u het item Windows Power shell Help bijwerken in het menu Help. Dit item helpt bij het bijwerken van de hulp voor de modules in de huidige sessie in de huidige GEBRUIKERSINTERFACE cultuur. Het is gelijk aan het uitvoeren van de Update-Help cmdlet zonder para meters. Als u de Help wilt bijwerken voor de cmdlets die worden geleverd met Windows Power shell, start u Windows PowerShell ISE met de optie als administrator uitvoeren.

U kunt ook de cmdlets Get-Help, Save-Help en Update-Help gebruiken in Windows PowerShell ISE, net zoals u deze gebruikt in de Windows Power shell-console. In Windows PowerShell ISE geeft de Help-functie echter het volledige Help-onderwerp weer, niet één pagina tegelijk.

## <a name="debugging-scripts"></a>Scripts voor fout opsporing

U kunt het fout opsporingsprogramma Windows PowerShell ISE gebruiken om fouten op te sporen in een Windows Power shell-script of-functie. Wanneer u fouten opspoort in een script, kunt u menu-items en sneltoetsen gebruiken voor het uitvoeren van veel van de taken die u in de Windows Power shell-console zou uitvoeren. Als u bijvoorbeeld een onderbrekings punt in een script wilt instellen, klikt u met de rechter muisknop op de regel code en klikt u vervolgens op onderbrekings punt in-en uitschakelen.

Tijdens het door lopen van een script tijdens het opsporen van fouten, wordt in de Markeer functie voor fout opsporing nauw keurig weer gegeven welk deel van de opdracht wordt uitgevoerd en worden automatisch bestanden geopend met de naam functies en scripts.

Standaard stelt het menu-item wissel knop scha kelen een onderbrekings punt in voor een volledige regel in een script, maar u kunt een onderbrekings punt instellen voor een variabele of opdracht naam.
U kunt ook een onderbrekings punt op een opdracht op regel-en kolom nummer instellen, waardoor het eenvoudiger wordt om fouten in lange pijplijn opdrachten op te sporen.

Vaak kunt u syntaxis fouten in een script opsporen door gewoon het script bestand in Windows PowerShell ISE te openen. De fout indicatoren identificeren syntaxis fouten en met de overzichts functies kunt u delen van het script samen vouwen om te focussen op problemen met de moeite.

U kunt ook de Windows Power shell-cmdlets voor fout opsporing in het opdracht venster gebruiken, net zoals u ze in de-console zou gebruiken.

## <a name="running-remote-commands"></a>Externe opdrachten uitvoeren

Met de nieuwe functie externe Power shell-tabblad kunt u eenvoudig een permanente, door de gebruiker beheerde Windows Power shell-sessie (' PSSession ') naar de lokale computer of een externe computer maken. Met de opdracht opent u een pop-upvenster waarin u wordt gevraagd om een computer naam en voor het gebruikers account dat is gemachtigd om opdrachten uit te voeren op de externe computer.

## <a name="customizing-the-view"></a>De weer gave aanpassen

U kunt Windows PowerShell ISE functies gebruiken om het console venster en het script paneel te verplaatsen en het formaat ervan te wijzigen. U kunt een deel venster weer geven en verbergen en u kunt de tekst grootte in alle deel vensters wijzigen.

U kunt ook het venster Opties gebruiken om het uiterlijk en de werking van Windows PowerShell ISE aan te passen. Daarnaast heeft Windows PowerShell ISE een aangepaste host-variabele, $psISE, die u kunt gebruiken om Windows PowerShell ISE aan te passen, zoals het toevoegen van menu's en menu-items.

## <a name="windows-powershell-ise-profile"></a>Windows PowerShell ISE profiel

Windows PowerShell ISE heeft een eigen Windows Power shell-profiel Microsoft.PowerShellISE_profile.ps1. In dit profiel kunt u functies, aliassen, variabelen en opdrachten opslaan die u in Windows PowerShell ISE gebruikt.

Items in de Windows Power shell AllHosts-profielen (CurrentUser \\ AllHosts en ALLUSERS \\ AllHosts) zijn ook beschikbaar in Windows PowerShell ISE, net zoals ze zich in een Windows Power shell-hostprogramma bevinden. De items in uw Windows Power shell-console profielen zijn echter niet beschikbaar in Windows PowerShell ISE.

Instructies voor het verplaatsen en opnieuw configureren van uw profielen zijn beschikbaar in Windows PowerShell ISE Help en in about_Profiles.

## <a name="notes"></a>OPMERKINGEN

Windows PowerShell ISE is een optionele Windows-functie die standaard is ingeschakeld op client-en server versies van Windows. Gebruik Windows-onderdelen in-of uitschakelen in het configuratie scherm om Windows PowerShell ISE in te scha kelen en uit te scha kelen in client versies van Windows. Gebruik de wizard functies en onderdelen toevoegen in Serverbeheer om Windows PowerShell ISE in te scha kelen en uit te scha kelen in Server versies van Windows.

Omdat Windows PowerShell ISE een gebruikers interface vereist, werkt deze niet op Server Core-installaties van Windows Server. Als u echter de functie Windows PowerShell ISE toevoegt, wordt de installatie automatisch geconverteerd naar een server met een grafische gebruikers interface.

Windows PowerShell ISE is gebaseerd op de Windows Presentation Foundation (WPF).
Als de grafische elementen van Windows PowerShell ISE niet correct worden weer gegeven op uw systeem, kunt u het probleem oplossen door de instellingen voor het weer geven van afbeeldingen van WPF-hardwareversnelling uitschakelen op uw systeem toe te voegen of aan te passen. Zie de [register instellingen voor grafische rendering](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings) in de MSDN-bibliotheek voor meer informatie.

## <a name="see-also"></a>ZIE OOK

[about_Debuggers](about_Debuggers.md)

[about_Profiles](about_Profiles.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-IseSnippet](xref:ISE.Get-IseSnippet)

[Import-IseSnippet](xref:ISE.Import-IseSnippet)

[New-IseSnippet](xref:ISE.New-IseSnippet)

[Opslaan-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Weer geven-opdracht](xref:Microsoft.PowerShell.Utility.Show-Command)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
