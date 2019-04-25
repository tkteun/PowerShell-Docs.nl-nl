---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Nieuw in PowerShell 50 ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 2d953bc4553de7720c590304d29750b84a1ef3b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058179"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>Wat&#39;nieuw in de Windows PowerShell ISE
In dit onderwerp wordt uitgelegd dat de nieuwe en bijgewerkte functies die zijn geïntroduceerd in versies van Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="feature-description"></a>Functiebeschrijving
De Windows PowerShell ISE is een hosttoepassing waarmee u te schrijven, uitvoeren en scripts en modules testen in een grafische en intuïtieve omgeving. Belangrijke functies zoals syntaxiskleuren, tabblad voltooiing, visuele foutopsporing, Unicode-naleving en contextgevoelige Help-onderwerpen bieden een rijke scripting ervaring.

Zie voor een overzicht van Windows PowerShell ISE, [overzicht van Windows PowerShell Integrated Scripting Environment](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Nieuwe en gewijzigde functionaliteit in Windows PowerShell ISE
De volgende tabel bevat de nieuwe en gewijzigde functies voor deze release van Windows PowerShell ISE in Windows PowerShell.

|Onderdeel/functionaliteit|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Codefragmenten](#snippets)**|X|X||
|**[Invoegtoepassing hulpprogramma 's](#add-on-tools)**|X|X||
|**[Opnieuw opstarten van de Manager en automatisch opslaan](#restart-manager-and-auto-save)**|X|X||
|**[Meest recent gebruikte](#most-recently-used-list)**|X|X||
|**[Consolevenster](#console-pane)**|X|X||
|**[Opdrachtregelopties](#command-line-switches)**|X|X||
|**[Nieuwe functies van de editor](#new-editor-features)**|X|X||
|**[Nieuwe Help-venster](#new-help-viewer-window)**|X|X||
|**[De cmdlet opdracht weergeven](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**Toegevoegd in ISE 3.0**

IntelliSense is een functie voor automatisch aanvullen hulp op die deel uitmaakt van Windows PowerShell ISE. IntelliSense geeft geklikt menu's met overeenkomende mogelijk cmdlets, parameters, parameterwaarden, bestanden of mappen terwijl u typt.

**Welke toegevoegde waarde van deze wijziging?**

Met de toevoeging van IntelliSense is het eenvoudiger cmdlet en syntaxis wordt gedetecteerd wanneer u Windows PowerShell ISE gebruiken om scripts te maken. U kunt ook Windows PowerShell ISE gebruiken voor meer informatie over Windows PowerShell bij het maken van nieuwe scripts.

**Wat werkt anders?**

Wanneer u cmdlets in Windows PowerShell ISE 3.0 of hoger, een overzicht en geklikt menu wordt weergegeven, zodat u kunt bladeren en selecteer de juiste opdrachten.

### <a name="snippets"></a>Codefragmenten
**Toegevoegd in ISE 3.0**

*Codefragmenten* korte secties van de Windows PowerShell-code die u kunt invoegen in de scripts die u in Windows PowerShell ISE maakt. Windows PowerShell ISE wordt geleverd met een standaardset aan fragmenten. U kunt codefragmenten toevoegen met behulp van de **New-fragment** cmdlet tijdens het werken in Windows PowerShell ISE.

**Welke toegevoegde waarde van deze wijziging?**

U kunt snel samen te stellen en scripts voor het automatiseren van uw omgeving maken met behulp van codefragmenten.

**Wat werkt anders?**

Voor het gebruik van codefragmenten in Windows PowerShell 3.0 of hoger, is het op de **bewerken** menu, klikt u op **Start codefragmenten**, of druk op **Ctrl-J**.

### <a name="add-on-tools"></a>Invoegtoepassing hulpprogramma 's
**Toegevoegd in PowerShell 3.0**

Windows PowerShell ISE biedt nu ondersteuning voor invoegtoepassingen, die Windows Presentation Foundation (WPF)-besturingselementen die worden toegevoegd met behulp van het objectmodel zijn. Invoegtoepassingen kunnen worden weergegeven als een verticale of horizontale deelvenster in de console. Meerdere invoegtoepassingen in een deelvenster worden weergegeven als een besturingselement met tabbladen. U kunt ook toevoegen of verwijderen van de invoegtoepassing-hulpprogramma's die worden geproduceerd door niet-Microsoft partijen. Zie voor meer informatie over het importeren of te verwijderen van de invoegtoepassing extra [Windows PowerShell ISE-bewerkingen](https://technet.microsoft.com/library/cc732148.aspx).

**Welke toegevoegde waarde van deze wijziging?**

Invoegtoepassingen kunnen u uitbreiden en aanpassen van Windows PowerShell ISE met hulpprogramma's die u kunnen uw scripting ervaring te verbeteren of functionaliteit toevoegen aan Windows PowerShell ISE.

**Wat werkt anders?**

Windows PowerShell ISE 3.0 en hoger worden geleverd met de **opdrachten** invoegtoepassing. De **opdrachten** invoegtoepassing kunt u bladeren cmdlets en help-informatie over de cmdlets side-by-side met toegang tot de **Script** en **Console** deelvensters.

Aanvullende invoegtoepassingen kunnen worden gevonden met behulp van de **Open invoegtoepassing extra Website** opdracht op de **invoegtoepassingen** menu.

### <a name="restart-manager-and-auto-save"></a>Opnieuw opstarten van de manager en automatisch opslaan
**Toegevoegd in PowerShell 3.0**

Windows PowerShell ISE nu automatisch opgeslagen uw open scripts elke twee minuten in een andere locatie.  Als Windows PowerShell ISE niet meer werkt, of als het besturingssysteem opnieuw wordt opgestart, nadat Windows PowerShell ISE opnieuw is opgestart, wordt hersteld scripts die zijn geopend in de vorige sessie, zelfs als de scripts zijn niet opgeslagen.

Als u wilt wijzigen van het interval voor automatisch opslaan, kunt u de volgende opdracht uitvoeren in het consolevenster: **$psise. Options.AutoSaveMinuteInterval**.

**Welke toegevoegde waarde van deze wijziging?**

U kunt nu werken in Windows PowerShell ISE wetenschap dat uw open-scripts worden automatisch opgeslagen in het geval van een onverwacht opnieuw opgestart.

**Wat werkt anders?**

Windows PowerShell ISE 2.0 wordt niet opgeslagen voor de scripts automatisch in het geval van een opnieuw opstarten.

### <a name="most-recently-used-list"></a>Meest recent gebruikte
**Toegevoegd in PowerShell 3.0**

Windows PowerShell ISE heeft nu een lijst met recent zijn gebruikt voor bestanden. Wanneer u een bestand in Windows PowerShell ISE opent, het bestand wordt toegevoegd aan de lijst met meest recent gebruikte op de **bestand** menu.

Als u wilt wijzigen van het aantal bestanden in de lijst met recent zijn gebruikt, kunt u de volgende opdracht uitvoeren in het consolevenster: **$psise. Options.MruCount**.

**Welke toegevoegde waarde van deze wijziging?**

U kunt nu de lijst met meest recent gebruikte eenvoudige toegang tot uw bestanden vaak gebruikt.

**Wat werkt anders?**

Windows PowerShell ISE 2.0 beschikt niet over een lijst met recent zijn gebruikt.

### <a name="console-pane"></a>Consolevenster
**Toegevoegd in PowerShell 3.0**

De afzonderlijke opdracht en de deelvensters van de uitvoer die beschikbaar in de eerste release van Windows PowerShell ISE waren zijn gecombineerd in één Console-venster. Het consolevenster lijkt in functie en het uiterlijk aan een typische Windows PowerShell-console, maar deze bevat de volgende verbeteringen (de meeste worden beschreven in dit onderwerp).

- Kleur van de syntaxis voor invoertekst (geen uitvoertekst), inclusief syntaxis en voorbeelden XML

- IntelliSense

- Accolade die overeenkomt met

- Vermelding van fout

- Volledige ondersteuning voor Unicode

- **F1** contextgevoelige help

- **CTRL + F1** opdracht contextgevoelige weergeven

- Complexe schrifttypen en ondersteuning van rechts naar links

- Ondersteuning voor lettertype

- Uitzoomen

- Regel selecteren en de blok-Selecteer-modi

- Behoud van getypeerde inhoud op de opdrachtregel als u op de **van** pijl geschiedenis weergeven in de console

**Welke toegevoegde waarde van deze wijziging?**

Het toevoegen van deze wijzigingen consolevenster biedt een scripting ervaring die consistenter wordt met de console-interface.

**Wat werkt anders?**

Windows PowerShell ISE 2.0 heeft afzonderlijke opdracht en deelvensters van de uitvoer.

### <a name="command-line-switches"></a>Opdrachtregelopties
**Toegevoegd in PowerShell 3.0**

Als u Windows PowerShell ISE vanaf de opdrachtregel starten (door te typen **powershell_ise.exe**), kunt u de volgende nieuwe schakelopties toevoegen.

- *-NoProfile*: Hiermee start u Windows PowerShell ISE zonder uitgevoerd **$profile**

- *-Help*: Een Help-venster wordt weergegeven

- *-mta*: Start Windows PowerShell ISE in de modus apartment meerdere threads. De standaardmodus voor de bewerking voor Windows PowerShell ISE is een single-threaded apartment-modus, of *- sta*.

**Welke toegevoegde waarde van deze wijziging?**

Het toevoegen van deze opdrachtregelopties kunt u voor het beheren van de omgeving waarin de Windows PowerShell ISE wordt uitgevoerd.

**Wat werkt anders?**

Windows PowerShell ISE 2.0 wordt niet herkend voor deze opdrachtregelopties.

### <a name="new-editor-features"></a>Nieuwe functies van de editor
**Toegevoegd in PowerShell 3.0**

Andere Windows PowerShell ISE-bewerkingsfuncties zijn onder andere:

- **XML-syntaxiskleuren**XML-syntaxis Windows PowerShell ISE nu kleuren op dezelfde manier als u deze Windows PowerShell-syntaxis kleuren.

- **Accolade die overeenkomt met** Windows PowerShell ISE bevat toe die overeenkomen met en te markeren en kan worden gebruikt in de volgende manieren: (bijvoorbeeld met behulp van de **gaat u naar overeenkomende reeks** opdracht of **Ctrl +]** wordt gezocht naar de haakje sluiten, hebt u een openingsaccolade geselecteerd).

- **Overzichtsweergave** het scriptvenster biedt ondersteuning voor een overzicht maken, waarmee samenvouwen of uitvouwen gedeelten van de code door te klikken op plus of min zich in de linkermarge. U kunt de accolades gebruiken of de **#region** en **#endregion** tags aan het begin of einde van een samenvouwbare sectie markeren. Als u wilt uitvouwen of samenvouwen van alle regio's, drukt u op **Ctrl + M**.

- **Slepen en neerzetten tekstbewerking**Windows PowerShell ISE nu ondersteunt slepen en tekst bewerken neerzetten. U kunt een blok tekst selecteert en sleept u deze tekst naar een andere locatie in de editor of in de console om de tekst te verplaatsen. Als u u de Ctrl-toets houdt terwijl u sleept u de geselecteerde tekst, wanneer u de muisknop loslaat wordt de tekst gekopieerd naar de nieuwe locatie. Wanneer u bestanden slepen en naar de Windows PowerShell ISE neerzetten, wordt Windows PowerShell ISE in deze versie van Windows PowerShell ISE, evenals de vorige versie van Windows PowerShell ISE, het bestand.

- **De weergave van fouten parseren** Parse-fouten worden aangegeven met rood onderstreept. Wanneer u de muisaanwijzer over een opgegeven fout, geeft de knopinfo die het probleem dat is gevonden in de code.

- **Zoomen** het zoompercentage van de inhoud van de console kan worden ingesteld met behulp van de zoomschuifregelaar (in de rechterbenedenhoek van de Windows PowerShell ISE-venster) of met de opdracht **$psise.options.Zoom** in het consolevenster.

- **Uitgebreide tekst kopiëren en plakken** kopiëren naar het Klembord in Windows PowerShell ISE behoudt van het lettertype, grootte en kleurinformatie van de oorspronkelijke selectie.

- **Selectie blokkeren** kunt u een blok tekst selecteren door de ALT-toets ingedrukt te houden bij het selecteren van tekst in het scriptvenster met de muis, of door te drukken **Alt + Shift + pijltoets**.

**Welke toegevoegde waarde van deze wijziging?**

De aanvullende functies bieden een consistente en krachtige bewerken omgeving.

**Wat werkt anders?**

Deze bewerking uitbreidingen zijn niet aanwezig zijn in Windows PowerShell ISE 2.0.

### <a name="new-help-viewer-window"></a>Nieuwe Help-venster
**Toegevoegd in PowerShell 3.0**

Als u druk op **F1** als de cursor zich in een cmdlet, of als onderdeel van een cmdlet die is gemarkeerd, voor de nieuwe Help-viewer contextgevoelige Help-informatie over de gemarkeerde cmdlet wordt geopend. Als Windows PowerShell over Help-informatie weergeven, typt **operators** in het consolevenster en druk vervolgens op **F1**.

Voordat u deze functie gebruiken, downloadt u de meest recente versie van Windows PowerShell Help-onderwerpen van de website van Microsoft. De eenvoudigste methode voor het downloaden van de Help-onderwerpen is om uit te voeren de **Update-Help** cmdlet in het consolevenster bij het uitvoeren van Windows PowerShell ISE als administrator.

U kunt wijzigen en waar u de **F1** sleutel ziet er uit voor hulp. In de **extra**/**opties** menu op de **algemene instellingen** tabblad onder **overige instellingen**, kunt u instellen of wissen de selectievakje **lokale help-inhoud gebruiken in plaats van online-inhoud**. Als dit selectievakje inschakelt, klikt u vervolgens zoekt de client de cmdlet Help-informatie in de gedownloade Help gevonden in de map modules.  Als het selectievakje is uitgeschakeld, klikt u vervolgens zoekt de client op de TechNet-bibliotheek voor de help van de cmdlet.

**Welke toegevoegde waarde van deze wijziging?**

Contextgevoelige Help zonder uw huidige cmdlet of script biedt een naadloze leerervaring.

**Wat werkt anders?**

Het help-bestand op de lokale computer op F1 drukt in eerdere versies van Windows PowerShell ISE worden geopend. In Windows PowerShell ISE 3.0 en hoger, wordt er een venster geopend met de help voor de cmdlet die is doorzoekbaar en kunnen worden geconfigureerd. In dit Help-ervaring is er nieuw voor Windows PowerShell ISE 3.0 en bij te werken Help is er nieuw voor Windows PowerShell 3.0.

### <a name="show-command-cmdlet"></a>De cmdlet opdracht weergeven
**Toegevoegd in PowerShell 3.0**

De **opdracht weergeven** cmdlet kunt u samenstellen of een cmdlet of de functie uitvoeren door in te vullen in een grafische vorm. Het formulier kan gebruikers werken met Windows PowerShell in een grafische omgeving. **Opdracht weergeven** ook kunnen geavanceerde scripttalen te maken van een snelle Windows PowerShell gebaseerde gebruikersinterface geopend.

**Welke toegevoegde waarde van deze wijziging?**

Met behulp van **opdracht weergeven** in uw Windows PowerShell-scripts, kunt u uw gebruikers opgeven met de grafische omgeving waarmee ze al bekend zijn. **Opdracht weergeven** kunt inleidende gebruikers meer informatie over Windows PowerShell.

**Wat werkt anders?**

Show-opdracht is een nieuwe Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Zie ook
Zie de volgende koppelingen voor meer informatie over het gebruik van Windows PowerShell ISE in Windows PowerShell.

- [De Windows PowerShell Integrated Scripting Environment verkennen](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [ISE op de TechNet-Wiki](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Script Center](https://technet.microsoft.com/scriptcenter/default)