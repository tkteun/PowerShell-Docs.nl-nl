---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Welke s die nieuw is in de 50 van de PowerShell ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 35b825cfa6ea720d0af3537c5d1b16c5ececb701
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>Wat&#39;s die nieuw is in de Windows PowerShell ISE
Dit onderwerp worden de nieuwe en bijgewerkte functies die zijn geïntroduceerd in versies van Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="feature-description"></a>Functiebeschrijving
De Windows PowerShell ISE is een hosttoepassing waarmee u kunt schrijven, uitvoeren en scripts en modules in een grafische en intuïtieve omgeving testen. Belangrijkste functies zoals syntaxis-kleuren, tabblad voltooiing, visuele foutopsporing, Unicode-compatibiliteit en Help-onderwerpen bieden een rijke ervaring voor het uitvoeren van scripts.

Zie voor een overzicht van Windows PowerShell ISE [overzicht van Windows PowerShell Integrated Scripting Environment](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Nieuwe en gewijzigde functionaliteit in Windows PowerShell ISE
De volgende tabel bevat de nieuwe en gewijzigde functies voor deze versie van Windows PowerShell ISE in Windows PowerShell.

|Onderdeel/functionaliteit|Windows PowerShell ISE 4.0|Windows PowerShell ISE 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Codefragmenten](#snippets)**|X|X||
|**[Extra hulpprogramma 's](#add-on-tools)**|X|X||
|**[Opnieuw opstarten van de Manager en automatisch moeten worden opgeslagen](#restart-manager-and-auto-save)**|X|X||
|**[Recent gebruikte](#most-recently-used-list)**|X|X||
|**[Consolevenster](#console-pane)**|X|X||
|**[Opdrachtregelopties](#command-line-switches)**|X|X||
|**[Nieuwe functies van de editor](#new-editor-features)**|X|X||
|**[Nieuwe Help-venster](#new-help-viewer-window)**|X|X||
|**[De cmdlet opdracht weergeven](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**In de ISE 3.0 toegevoegd**

IntelliSense is een automatische voltooiing hulp-functie die deel uitmaakt van Windows PowerShell ISE. IntelliSense geeft klikbaar menu's met overeenkomende mogelijk cmdlets, parameters, parameterwaarden, bestanden of mappen terwijl u typt.

**Welke toegevoegde waarde van deze wijziging?**

Met de toevoeging van IntelliSense is het eenvoudiger voor het detecteren van de cmdlet en syntaxis als u Windows PowerShell ISE gebruiken om scripts te maken. U kunt ook Windows PowerShell ISE voor meer informatie over Windows PowerShell bij het maken van nieuwe scripts gebruiken.

**Wat werkt er anders?**

Wanneer u cmdlets in Windows PowerShell ISE 3.0 of hoger typt, een schuifbare en klikbaar menu wordt weergegeven, zodat u kunt bladeren en selecteer de juiste opdrachten.

### <a name="snippets"></a>Codefragmenten
**In de ISE 3.0 toegevoegd**

*Codefragmenten* korte gedeelten van Windows PowerShell-code die u in de scripts die u in Windows PowerShell ISE maakt kunt invoegen. Windows PowerShell ISE wordt geleverd met een standaardset codefragmenten. U kunt codefragmenten toevoegen met behulp van de **nieuw codefragment** cmdlet terwijl u werkt in Windows PowerShell ISE.

**Welke toegevoegde waarde van deze wijziging?**

U kunt snel samenstellen en maken van scripts voor uw omgeving te automatiseren met behulp van codefragmenten.

**Wat werkt er anders?**

Codefragmenten op in Windows PowerShell 3.0 of hoger, gebruiken de **bewerken** menu, klikt u op **Start codefragmenten**, of druk op **Ctrl J**.

### <a name="add-on-tools"></a>Extra hulpprogramma 's
**Toegevoegd in PowerShell 3.0**

Windows PowerShell ISE ondersteunt nu de invoegtoepassingen die Windows Presentation Foundation (WPF)-besturingselementen die worden toegevoegd met behulp van het objectmodel zijn. Extra hulpprogramma's kunnen worden weergegeven als een verticale of horizontale venster in de console. Meerdere invoegtoepassingen in een deelvenster worden weergegeven als een besturingselement met tabbladen. U kunt ook toevoegen of verwijderen van de invoegtoepassing-hulpprogramma's die worden geproduceerd door niet-Microsoft partijen. Zie voor meer informatie over het importeren of te verwijderen van de invoegtoepassing extra [bewerkingen in het Windows PowerShell ISE](http://technet.microsoft.com/library/cc732148.aspx).

**Welke toegevoegde waarde van deze wijziging?**

Invoegtoepassingen toestaan u uitbreiden en aanpassen van Windows PowerShell ISE met hulpprogramma's die u kunnen uw scripting ervaring te verbeteren of functionaliteit toevoegen aan Windows PowerShell ISE.

**Wat werkt er anders?**

Windows PowerShell ISE 3.0 en hoger worden geleverd met de **opdrachten** invoegtoepassing. De **opdrachten** invoegtoepassing kunt u bladeren cmdlets en help-informatie over de cmdlets side-by-side met toegang tot de **Script** en **Console** deelvensters.

Extra invoegtoepassingen kunnen worden gevonden met behulp van de **Open-invoegtoepassing voor extra Website** opdracht op de **invoegtoepassingen** menu.

### <a name="restart-manager-and-auto-save"></a>Opnieuw opstarten van de manager en automatisch moeten worden opgeslagen
**Toegevoegd in PowerShell 3.0**

Windows PowerShell ISE nu automatisch opgeslagen open scripts elke twee minuten op een andere locatie.  Als Windows PowerShell ISE werkt niet, of als het besturingssysteem opnieuw wordt opgestart, nadat Windows PowerShell ISE opnieuw is opgestart, herstelt openen scripts die zijn in de laatste sessie, zelfs als de scripts zijn niet opgeslagen.

De automatische opslaan als interval wilt wijzigen, kunt u de volgende opdracht uitvoeren in het consolevenster: **$psise. Options.AutoSaveMinuteInterval**.

**Welke toegevoegde waarde van deze wijziging?**

U kunt nu werken in Windows PowerShell ISE weten dat uw open scripts automatisch worden opgeslagen in het geval van een onverwacht opnieuw opgestart.

**Wat werkt er anders?**

De scripts automatisch opnieuw opstarten in geval van een Windows PowerShell ISE 2.0 niet opgeslagen.

### <a name="most-recently-used-list"></a>Recent gebruikte
**Toegevoegd in PowerShell 3.0**

Windows PowerShell ISE heeft nu een lijst met recent zijn gebruikt voor bestanden. Wanneer u een bestand in Windows PowerShell ISE opent, het bestand wordt toegevoegd aan de lijst met recent zijn gebruikt op de **bestand** menu.

Als u wilt wijzigen van het aantal bestanden in de lijst met recent zijn gebruikt, kunt u de volgende opdracht uitvoeren in het consolevenster: **$psise. Options.MruCount**.

**Welke toegevoegde waarde van deze wijziging?**

U kunt nu de meest recentelijk gebruikte lijst eenvoudig toegang tot uw bestanden vaak gebruikt.

**Wat werkt er anders?**

Windows PowerShell ISE 2.0 beschikt niet over een lijst met recent zijn gebruikt.

### <a name="console-pane"></a>Consolevenster
**Toegevoegd in PowerShell 3.0**

De afzonderlijke opdracht en de uitvoer deelvensters die beschikbaar in de eerste versie van Windows PowerShell ISE waren zijn gecombineerd in één Console deelvenster. Het consolevenster lijkt in functie en het uiterlijk aan een typische Windows PowerShell-console, maar deze bevat de volgende verbeteringen (de meeste worden beschreven in dit onderwerp).

- Kleur van de syntaxis voor de ingevoerde tekst (geen uitvoertekst), met inbegrip van XML-syntaxis

- IntelliSense

- Overeenkomende accolade

- Fout-vermelding

- Volledige ondersteuning voor Unicode

- **F1** contextgevoelige help

- **CTRL + F1** opdracht contextgevoelige weergeven

- Complexe script en ondersteuning van rechts naar links

- Lettertype-ondersteuning

- Uitzoomen

- Modi van regel selecteren en blok selecteren

- Behoud van getypeerde inhoud op de opdrachtregel als u op de **Up** pijl geschiedenis weergeven in de console

**Welke toegevoegde waarde van deze wijziging?**

Het toevoegen van deze wijzigingen consolevenster biedt een scripting-ervaring die consistenter met de console-interface.

**Wat werkt er anders?**

Windows PowerShell ISE 2.0 heeft afzonderlijke opdracht en uitvoer deelvensters.

### <a name="command-line-switches"></a>Opdrachtregelopties
**Toegevoegd in PowerShell 3.0**

Als u Windows PowerShell ISE vanaf de opdrachtregel starten (door te typen **powershell_ise.exe**), kunt u de volgende nieuwe schakelopties toevoegen.

- *-NoProfile*: Start Windows PowerShell ISE zonder uitgevoerd **$profile**

- *-Help*: een Help-venster wordt weergegeven

- *-mta*: Start Windows PowerShell ISE in meerdere threads apartment-modus. De standaardmodus voor de bewerking voor Windows PowerShell ISE is single thread apartment-modus, of *- sta*.

**Welke toegevoegde waarde van deze wijziging?**

Het toevoegen van deze opdrachtregelopties kunt u bepalen van de omgeving waarin de Windows PowerShell ISE wordt uitgevoerd.

**Wat werkt er anders?**

Deze opdrachtregelparameters worden niet herkend door Windows PowerShell ISE 2.0.

### <a name="new-editor-features"></a>Nieuwe functies van de editor
**Toegevoegd in PowerShell 3.0**

Andere functies van Windows PowerShell ISE-bewerken:

- **XML-syntaxiskleuren**XML-syntaxis Windows PowerShell ISE nu kleuren op dezelfde manier als het Windows PowerShell-syntaxis kleuren.

- **Overeenkomende accolade** Windows PowerShell ISE omvat overeenkomende accolade en is gemarkeerd en kan worden gebruikt in de volgende manieren: (bijvoorbeeld met behulp van de **gaat u naar de overeenkomst** opdracht of **Ctrl +]** zoekt de haakje sluiten, hebt u een openingsaccolade geselecteerd).

- **Overzichtsweergave** het scriptvenster ondersteunt overzicht, waarmee samenvouwen of stukjes code door te klikken op plus of min uitvouwen in de linkermarge zich aanmeldt. U kunt de accolades gebruiken of de **#region** en **#endregion** labels markeert het begin of einde van een samenvouwbare sectie. Als u wilt uitvouwen of samenvouwen alle regio's, drukt u op **Ctrl + M**.

- **Slepen en neerzetten tekstbewerking**Windows PowerShell ISE nu ondersteunt slepen en neerzetten van tekst bewerken. U kunt elk blok tekst selecteren en sleept u deze tekst naar een andere locatie in de editor of de console om de tekst te verplaatsen. Als u Houd Ctrl ingedrukt terwijl u de geselecteerde tekst sleept, wanneer u de muisknop loslaat wordt de tekst wordt gekopieerd naar de nieuwe locatie. In deze versie van Windows PowerShell ISE, evenals de vorige versie van Windows PowerShell ISE, als u slepen en neerzetten van bestanden naar de Windows PowerShell ISE Windows PowerShell ISE opent u het bestand.

- **Parseren van de weergave van fouten** Parse fouten worden aangegeven met een rode onderstreping. Wanneer u de muisaanwijzer op een fout aangegeven, wordt het probleem dat is gevonden in de code weergegeven in knopinfo.

- **Zoomen** het zoompercentage van de console'™ s inhoud kan worden ingesteld met behulp van de schuifregelaar Inzoomen (in de rechterbenedenhoek van Windows PowerShell ISE-venster) of met de opdracht **$psise.options.Zoom** in het consolevenster.

- **Rich text kopiëren en plakken** kopiëren naar het Klembord in Windows PowerShell ISE gehandhaafd het lettertype, grootte en kleurinformatie van de oorspronkelijke selectie.

- **Blok selecteren** kunt u een blok tekst door de ALT-toets ingedrukt te houden bij het selecteren van tekst in het deelvenster Script met de muis of door op **Alt + Shift + pijl**.

**Welke toegevoegde waarde van deze wijziging?**

De aanvullende functies bieden een consistentere en krachtige omgeving voor het bewerken.

**Wat werkt er anders?**

Deze bewerking uitbreidingen zijn niet aanwezig in Windows PowerShell ISE 2.0.

### <a name="new-help-viewer-window"></a>Nieuwe Help-venster
**Toegevoegd in PowerShell 3.0**

Als u op **F1** wanneer de cursor zich in een cmdlet of deel uitmaken van een cmdlet gemarkeerd hebt, de nieuwe Help-viewer Help-onderwerpen over de gemarkeerde cmdlet geopend. Typ het volgende Windows PowerShell over Help-informatie **operators** in het consolevenster, en druk **F1**.

Voordat u deze functie gebruiken, moet u de meest recente versie van Windows PowerShell Help-onderwerpen downloaden van de website van Microsoft. De eenvoudigste methode voor het downloaden van de Help-onderwerpen is om uit te voeren de **Update-Help** cmdlet in het consolevenster bij het uitvoeren van Windows PowerShell ISE als beheerder.

U kunt wijzigen waar de **F1** sleutel wordt gezocht naar Help. In de **extra**/**opties** menu op de **algemene instellingen** tabblad onder **overige instellingen**, kunt u instellen of schakel de selectievakje **lokale help-inhoud gebruiken in plaats van online inhoud**. Als dit selectievakje inschakelt, zoekt vervolgens naar de client de cmdlet Help in de gedownloade Help gevonden in de map modules.  Als het selectievakje is uitgeschakeld, klikt u vervolgens zoekt de client op de TechNet-bibliotheek voor de help van cmdlet.

**Welke toegevoegde waarde van deze wijziging?**

Contextgevoelige Help zonder uw huidige cmdlet of script biedt een naadloze learning-ervaring.

**Wat werkt er anders?**

Het help-bestand op de lokale computer op F1 drukt in eerdere versies van Windows PowerShell ISE worden geopend. In Windows PowerShell ISE 3.0 en hoger, wordt er een venster geopend waarin de help voor de cmdlet die doorzoekbaar en kunnen worden geconfigureerd. Deze Help-ervaring is er nieuw voor Windows PowerShell ISE 3.0 en bij te werken Help is er nieuw voor Windows PowerShell 3.0.

### <a name="show-command-cmdlet"></a>De cmdlet opdracht weergeven
**Toegevoegd in PowerShell 3.0**

De **opdracht weergeven** cmdlet kunt u samenstellen of een cmdlet of functie uitvoeren door een grafische formulier invullen. Het formulier kan gebruikers die werken met Windows PowerShell in een grafische omgeving. **Opdracht weergeven** ook schakelt geavanceerde scripttalen voor het maken van een snelle GUI op basis van Windows PowerShell.

**Welke toegevoegde waarde van deze wijziging?**

Met behulp van **opdracht weergeven** in uw Windows PowerShell-scripts, kunt u uw gebruikers opgeven met de grafische omgeving waaraan die bekend zijn. **Opdracht weergeven** kunt inleidende gebruikers meer informatie over Windows PowerShell.

**Wat werkt er anders?**

Opdracht weergeven is een nieuwe Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Zie ook
Zie de volgende koppelingen voor meer informatie over het gebruik van Windows PowerShell ISE in Windows PowerShell.

- [De Windows PowerShell Integrated Scripting Environment verkennen](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [ISE op de TechNet-Wiki](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Script Center](http://technet.microsoft.com/scriptcenter/default)