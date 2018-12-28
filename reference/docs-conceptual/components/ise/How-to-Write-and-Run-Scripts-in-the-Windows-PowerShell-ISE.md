---
ms.date: 08/14/2018
keywords: PowerShell-cmdlet
title: Scripts schrijven en uitvoeren in Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403990"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Scripts schrijven en uitvoeren in Windows PowerShell ISE

Dit artikel wordt beschreven hoe u kunt maken, bewerken, uitvoeren en opslaan van scripts in het scriptvenster.

## <a name="how-to-create-and-run-scripts"></a>Over het maken en uitvoeren van scripts

U kunt openen en bewerken van Windows PowerShell-bestanden in het scriptvenster. Bepaalde bestandstypen van belang zijn in Windows PowerShell zijn scriptbestanden (.ps1), data-scriptbestanden (.psd1) en module scriptbestanden (.psm1). Deze bestandstypen zijn gekleurd in de editor scriptvenster syntaxis. Andere algemene bestandstypen die u in het scriptvenster openen kunt zijn configuratiebestanden (.ps1xml), XML-bestanden en tekstbestanden.

> [!NOTE]
> De Windows PowerShell-uitvoeringsbeleid bepaalt of u kunt uitvoeren van scripts en Windows PowerShell-profielen en -configuratiebestanden worden geladen. Het standaardbeleid worden uitgevoerd met beperkte toegang, voorkomt u dat alle scripts die worden uitgevoerd en wordt voorkomen dat het laden van profielen. Als u wilt wijzigen van het uitvoeringsbeleid om toe te staan profielen die moeten worden geladen en worden gebruikt, Zie [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) en [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

### <a name="to-create-a-new-script-file"></a>Een nieuwe scriptbestand maken

Klik op de werkbalk op **nieuw**, of op de **bestand** menu, klikt u op **nieuw**. Het bestand wordt weergegeven in een nieuw tabblad van het bestand onder de huidige PowerShell-tabblad. Houd er rekening mee dat de PowerShell-tabbladen alleen zichtbaar zijn als er meer dan één. Standaard wordt een bestand van het type script (.ps1) gemaakt, maar deze kan worden opgeslagen met een nieuwe naam en extensie. Meerdere scriptbestanden kunnen worden gemaakt in de dezelfde PowerShell-tabblad.

### <a name="to-open-an-existing-script"></a>Een bestaand script openen

Klik op de werkbalk op **Open**, of op de **bestand** menu, klikt u op **Open**. In de **Open** dialoogvenster vak, selecteert u het bestand dat u wilt openen. Het geopende bestand wordt weergegeven in een nieuw tabblad.

### <a name="to-close-a-script-tab"></a>Om een script tabblad te sluiten

Klik op de **sluiten** pictogram (X) van het tabblad bestand dat u wilt sluiten of Selecteer de **bestand** en klik op **sluiten**.

Als het bestand is gewijzigd sinds het laatst is opgeslagen, wordt u gevraagd op te slaan of te verwijderen.

### <a name="to-display-the-file-path"></a>Om weer te geven van het bestandspad

Op het tabblad bestand, wijst u de bestandsnaam. De volledig gekwalificeerde pad naar het scriptbestand wordt weergegeven in de knopinfo.

### <a name="to-run-a-script"></a>Een script uitvoeren

Klik op de werkbalk op **-Script uitvoeren**, of op de **bestand** menu, klikt u op **uitvoeren**.

### <a name="to-run-a-portion-of-a-script"></a>Een gedeelte van een script uitvoeren

1. Selecteer in het scriptvenster een gedeelte van een script.
2. Op de **bestand** menu, klikt u op **selectie uitvoeren**, of klik op de werkbalk op **selectie uitvoeren**.

### <a name="to-stop-a-running-script"></a>Stoppen van een script uit te voeren

Er zijn verschillende manieren om te stoppen van een script uit te voeren.

- Klik op **stoppen bewerking** op de werkbalk
- Druk op CTRL + BREAK
- Selecteer de **bestand** en klik op **stoppen bewerking**.

Drukken **CTRL + C** werkt ook, tenzij de tekst is geselecteerd, in welk geval **CTRL + C** wordt toegewezen aan de functie kopiëren voor de geselecteerde tekst.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Het schrijven en tekst in het scriptvenster bewerken

U kunt kopiëren, knippen, plakken, zoeken en vervangen tekst in het scriptvenster. U kunt ook ongedaan maken en herstellen van de laatste actie die u zojuist hebt uitgevoerd. De sneltoetsen voor deze acties zijn dezelfde snelkoppelingen die wordt gebruikt voor alle Windows-toepassingen.

### <a name="to-enter-text-in-the-script-pane"></a>Tekst invoeren in het scriptvenster

1. De cursor naar het scriptvenster verplaatsen door te klikken op een willekeurige plaats in het scriptvenster of door te klikken op **gaat u naar scriptvenster** in de **weergave** menu.
2. Een script maken. Syntaxiskleuren en tab-Aanvulling bieden een rijkere bewerken in Windows PowerShell ISE.
3. Zie [hoe u de Tab-aanvulling gebruiken in het scriptvenster en consolevenster](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) voor meer informatie over het gebruik van het tabblad voltooiing-functie om te helpen bij het typen.

### <a name="to-find-text-in-the-script-pane"></a>Tekst zoeken in het scriptvenster

1. Als u wilt zoeken overal tekst, drukt u op **CTRL + F** of Ga naar de **bewerken** menu, klikt u op **niet vinden in het Script**.
2. Om te zoeken tekst na de cursor, drukt u op **F3** of Ga naar de **bewerken** menu, klikt u op **volgende zoeken in Script**.
3. Om te zoeken tekst vóór de cursor, drukt u op **SHIFT + F3** of Ga naar de **bewerken** menu, klikt u op **vorige in Script**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Om te zoeken en vervangen tekst in het scriptvenster

Druk op **CTRL + H** of Ga naar de **bewerken** menu, klikt u op **vervangen in Script**. Voer de tekst die u wilt zoeken en de nieuwe tekst, drukt u vervolgens op **ENTER**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Naar een bepaalde regel tekst in het scriptvenster

1. Druk in het scriptvenster op **CTRL + G** of Ga naar de **bewerken** menu, klikt u op **gaat u naar de regel**.

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

Er verschijnt een sterretje naast de naam van het script naar een bestand dat niet is opgeslagen, omdat deze is gewijzigd. Het sterretje verdwijnt wanneer het bestand wordt opgeslagen.

### <a name="to-save-a-script"></a>Een script opslaan

Druk op **CTRL + S** of klik op de werkbalk op de **opslaan** pictogram, of op de **bestand** menu, klikt u op **opslaan**.

### <a name="to-save-and-name-a-script"></a>Opslaan en de naam van een script

1. Op de **bestand** menu, klikt u op **OpslaanAls**. De **OpslaanAls** in het dialoogvenster wordt weergegeven.
2. In de **bestandsnaam** voert u een naam voor het bestand.
3. In de **opslaan als** vak, selecteert u een bestandstype. Bijvoorbeeld, in de **opslaan als** Schakel ' PowerShell-Scripts (\*.ps1)'.
4. Klik op **Opslaan**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Voor het opslaan van een script in ASCII-codering

Standaard Windows PowerShell ISE Hiermee slaat u nieuwe scriptbestanden (.ps1), data-scriptbestanden (.psd1) en module scriptbestanden (.psm1) als Unicode (BigEndianUnicode) standaard. (C) als u wilt opslaan een script in een andere codering, zoals ASCII (ANSI), gebruiken de **opslaan** of **opslaan** methoden op de [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.

De volgende opdracht wordt een nieuw script opgeslagen als Mijnscript.ps1 met ASCII-codering.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

De volgende opdracht vervangt het huidige scriptbestand met een bestand met dezelfde naam maar met de ASCII-codering.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

De volgende opdracht wordt de codering van het huidige bestand.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE ondersteunt de volgende opties voor encoding: ASCII-, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 en standaard. De waarde van de standaardoptie is afhankelijk van het systeem.

Windows PowerShell ISE verandert niet met de codering van scriptbestanden wanneer u de opslaan of OpslaanAls opdrachten.

## <a name="see-also"></a>Zie ook

- [Kennismaking met Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
