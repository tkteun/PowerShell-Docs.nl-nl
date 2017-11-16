---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het schrijven en uitvoeren van Scripts in de Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: dd3055df8c84195f0145b1a058f1d17c9c382f33
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Het schrijven en uitvoeren van Scripts in de Windows PowerShell ISE
In dit onderwerp wordt beschreven hoe maken, bewerken, uitvoeren en scripts in het deelvenster Script opslaat.

## <a name="how-to-create-and-run-scripts"></a>Het maken en scripts uitvoeren
U kunt openen en bewerken van Windows PowerShell-bestanden in het scriptvenster. Specifieke bestandstypen van belang zijn in Windows PowerShell zijn scriptbestanden (.ps1), gegevens scriptbestanden (.psd1) en module scriptbestanden (.psm1). Deze bestandstypen zijn syntaxis in de editor scriptvenster gekleurd. Andere veelvoorkomende bestandstypen die u in het scriptvenster openen kunt zijn configuratiebestanden (.ps1xml), XML-bestanden en tekstbestanden.

> [!NOTE]
> De Windows PowerShell-uitvoeringsbeleid bepaalt of u kunt scripts uitvoeren en Windows PowerShell-profielen en configuratiebestanden laden. Het standaarduitvoeringsbeleid beperkt, wordt voorkomen dat alle scripts uitgevoerd en voorkomt u dat bij het laden profielen. Als u wilt wijzigen van het uitvoeringsbeleid zodat profielen worden geladen en worden gebruikt, Zie [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) en [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### <a name="to-create-a-new-script-file"></a>Voor het maken van een script
Klik op de werkbalk op **nieuw** , of op de **bestand** menu, klikt u op **nieuw**. Het bestand wordt weergegeven in een nieuw tabblad bestand onder het huidige PowerShell-tabblad. Vergeet niet de tabbladen PowerShell zijn alleen zichtbaar als er meer dan één. Standaard wordt een bestand van het type script (.ps1) gemaakt, maar deze kan worden opgeslagen met een nieuwe naam en extensie. Meerdere scriptbestanden kunnen worden gemaakt op hetzelfde tabblad PowerShell.

### <a name="to-open-an-existing-script"></a>Een bestaand script openen
Klik op de werkbalk op **Open**, of op de **bestand** menu, klikt u op **Open**. In de **openen** dialoogvenster Selecteer het bestand dat u wilt openen. Het geopende bestand wordt weergegeven in een nieuw tabblad.

### <a name="to-close-a-script-tab"></a>Een script tabblad sluiten
Klik op het tabblad script van het script dat u wilt sluiten en voer vervolgens een van de volgende handelingen uit:

1. Klik op de **sluiten** pictogram (X) op het tabblad script.

2. Op de **bestand** menu, klikt u op **sluiten**.

Als het bestand is gewijzigd sinds het laatst is opgeslagen, wordt u gevraagd op te slaan of te verwijderen.

### <a name="to-display-the-file-path"></a>Het bestandspad weergeven
Wijs de bestandsnaam op het tabblad bestand. Het volledig gekwalificeerde pad naar het scriptbestand wordt weergegeven in knopinfo.

### <a name="to-run-a-script"></a>Een script uitvoeren
Klik op de werkbalk op **-Script uitvoeren**, of op de **bestand** menu, klikt u op **uitvoeren**.

### <a name="to-run-a-portion-of-a-script"></a>Een gedeelte van een script uitvoeren

1. Selecteer in het scriptvenster een deel van een script.

2. Op de **bestand** menu, klikt u op **selectie uitvoeren**, of klik op de werkbalk op **selectie uitvoeren**.

### <a name="to-stop-a-running-script"></a>Stoppen van een script wordt uitgevoerd
Klik op de werkbalk op **bewerking stoppen**, druk op CTRL + BREAK of op de **bestand** menu, klikt u op **bewerking stoppen**. Drukken **CTRL + C** werkt ook tenzij tekst momenteel is geselecteerd, in welk geval **CTRL + C** wordt toegewezen aan de functie kopiëren voor de geselecteerde tekst.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Het schrijven en tekst in het scriptvenster bewerken
Gebruik de volgende stappen uit om tekst in het scriptvenster te bewerken. U kunt kopiëren, knippen, plakken, zoeken en vervangen tekst. U kunt ook ongedaan maken en herstellen van de laatste actie die u zojuist hebt uitgevoerd. De sneltoetsen voor het uitvoeren van deze acties zijn hetzelfde als die worden gebruikt voor alle Windows-toepassingen.

### <a name="to-enter-text-in-the-script-pane"></a>Tekst invoeren in het scriptvenster

1. De cursor naar het scriptvenster verplaatsen door te klikken op in het scriptvenster of door te klikken op **gaat u naar scriptvenster** in de **weergave** menu.

2. Een script maken. Van de syntaxiskleuren en tab-Aanvulling Maak hiervan een rijkere ervaring in Windows PowerShell ISE.

3. Zie [hoe gebruik Tab-aanvulling in het scriptvenster en consolevenster](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) voor meer informatie over het gebruik van de functie van de voltooiing tabblad te helpen bij het te typen.

### <a name="to-find-text-in-the-script-pane"></a>Tekst zoeken in het scriptvenster

1. Druk overal tekst zoeken op **CTRL + F** of Ga naar de **bewerken** menu, klikt u op **niet vinden in het Script**.

2. Druk tekst zoeken na de cursor op **F3** of Ga naar de **bewerken** menu, klikt u op **volgende zoeken in Script**.

3. Tekst wilt vinden voordat de cursor, drukt u op **SHIFT + F3** of Ga naar de **bewerken** menu, klikt u op **vorige in Script**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Voor tekst in het scriptvenster zoeken en vervangen
Druk op **CTRL + H** of Ga naar de **bewerken** menu, klikt u op **vervangen in Script**. Geef zowel de tekst die u wilt zoeken en de tekst die u wilt vervangen, en druk vervolgens op **ENTER**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Naar een bepaalde regel tekst in het scriptvenster

1. Druk in het scriptvenster op **CTRL + G** of Ga naar de **bewerken** menu, klikt u op **gaat u naar regel**.

2. Voer een getal van de regel.

### <a name="to-copy-text-in-the-script-pane"></a>Tekst in het scriptvenster kopiëren

1. Selecteer in het scriptvenster de tekst die u wilt kopiëren.

2. Druk op **CTRL + C** of klik op de werkbalk op de **kopie** pictogram, of op de **bewerken** menu, klikt u op **kopie**.

### <a name="to-cut-text-in-the-script-pane"></a>Tekst in het scriptvenster knippen

1. Selecteer in het scriptvenster de tekst die u wilt knippen.

2. Druk op **CTRL + X** of klik op de werkbalk op de **Knippen** pictogram, of op de **bewerken** menu, klikt u op **Knippen**.

### <a name="to-paste-text-into-the-script-pane"></a>Tekst in het scriptvenster plakken
Druk op **CTRL + V** of klik op de werkbalk op de **plakken** pictogram, of op de **bewerken** menu, klikt u op **plakken**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Een bewerking in het scriptvenster ongedaan maken
Druk op **CTRL + Z** of klik op de werkbalk op de **ongedaan** pictogram, of op de **bewerken** menu, klikt u op **ongedaan maken**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Een bewerking in het scriptvenster opnieuw uitvoeren
Druk op **CTRL + Y** of klik op de werkbalk op de **opnieuw** pictogram, of op de **bewerken** menu, klikt u op **opnieuw**.

## <a name="how-to-save-a-script"></a>Het opslaan van een script
Gebruik de volgende stappen uit om te slaan en de naam van een script. Een asterisk weergegeven naast de naam van de scriptopdracht markeren van een bestand dat niet opgeslagen is omdat dit werd gewijzigd. Het sterretje verdwijnt wanneer het bestand wordt opgeslagen.

### <a name="to-save-a-script"></a>Opslaan van een script
Druk op **CTRL + S** of klik op de werkbalk op de **opslaan** pictogram, of op de **bestand** menu, klikt u op **opslaan**.

### <a name="to-save-and-name-a-script"></a>Voor opslaan en de naam van een script

1. Op de **bestand** menu, klikt u op **OpslaanAls**. De **OpslaanAls** dialoogvenster wordt weergegeven.

2. In de **bestandsnaam** Voer een naam voor het bestand.

3. In de **opslaan als type** Selecteer een bestandstype. Bijvoorbeeld, in de **opslaan als type** de optie ' œPowerShell Scripts (\* .ps1)'.

4. Klik op **Opslaan**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Voor het opslaan van een script in ASCII-codering
Standaard slaat Windows PowerShell ISE nieuwe scriptbestanden (.ps1), gegevens scriptbestanden (.psd1) en module scriptbestanden (.psm1) als Unicode (BigEndianUnicode) standaard. Â Sla een script in een andere codering, zoals ASCII (ANSI), gebruikt u de **opslaan** of **SaveAs** methoden op de [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.

De volgende opdracht slaat een nieuw script als Mijnscript.ps1 ASCII-codering.

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

De volgende opdracht uit vervangen het huidige scriptbestand door een bestand met dezelfde naam, maar met ASCII-codering.

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

De volgende opdracht haalt de codering van het huidige bestand.

```
$psise.CurrentFile.encoding
```

Windows PowerShell ISE ondersteunt de volgende opties voor codering: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 en standaard. De waarde van de standaardoptie verschillen afhankelijk van het systeem.

Windows PowerShell ISE niet verandert de codering van scripts die zijn gemaakt door in een andere editor, zelfs wanneer u gebruikt de opslaan of OpslaanAls opdrachten in Windows PowerShell ISE.

## <a name="see-also"></a>Zie ook
- [Met behulp van de Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)

