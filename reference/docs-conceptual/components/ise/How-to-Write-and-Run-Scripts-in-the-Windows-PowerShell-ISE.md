---
ms.date: 08/14/2018
keywords: Power shell, cmdlet
title: Scripts schrijven en uitvoeren in Windows PowerShell ISE
ms.openlocfilehash: be54e26965a6d2f1472059820080a6a06c47dd26
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117568"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Scripts schrijven en uitvoeren in Windows PowerShell ISE

In dit artikel wordt beschreven hoe u scripts maakt, bewerkt, uitvoert en opslaat in het Script-venster.

## <a name="how-to-create-and-run-scripts"></a>Scripts maken en uitvoeren

U kunt Windows Power Shell-bestanden openen en bewerken in het Script-venster. Specifieke bestands typen die van belang zijn in Windows Power shell zijn script bestanden (. ps1), script gegevensbestand (. psd1) en script module bestanden (. psm1). Deze bestands typen zijn syntaxis gekleurd in de Script-Editor. Andere algemene bestands typen die u kunt openen in het deel venster script zijn configuratie bestanden (. ps1xml), XML-bestanden en tekst bestanden.

> [!NOTE]
> Het Windows Power shell-uitvoerings beleid bepaalt of u scripts kunt uitvoeren en Windows Power shell-profielen en-configuratie bestanden kan laden. Het standaard uitvoerings beleid, beperkt, voor komt dat alle scripts worden uitgevoerd en voor komt het laden van profielen. Zie [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) en [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)om het uitvoerings beleid te wijzigen zodat de profielen kunnen worden geladen en gebruikt.

### <a name="to-create-a-new-script-file"></a>Een nieuw script bestand maken

Klik op de werk balk op **Nieuw**of Klik in het menu **bestand** op **Nieuw**. Het gemaakte bestand wordt weer gegeven op het tabblad nieuw bestand onder het huidige Power shell-tabblad. Houd er rekening mee dat de Power shell-tabbladen alleen zichtbaar zijn wanneer er meer dan één. Standaard wordt een bestand van het type script (. ps1) gemaakt, maar het kan worden opgeslagen met een nieuwe naam en extensie. Meerdere script bestanden kunnen worden gemaakt op hetzelfde Power shell-tabblad.

### <a name="to-open-an-existing-script"></a>Een bestaand script openen

Klik op de werk balk op **openen**of Klik in het menu **bestand** op **openen**. Selecteer in het dialoog venster **openen** het bestand dat u wilt openen. Het geopende bestand wordt weer gegeven op een nieuw tabblad.

### <a name="to-close-a-script-tab"></a>Het tabblad Script sluiten

Klik op het pictogram **sluiten** (X) van het tabblad bestand dat u wilt sluiten of selecteer het menu **bestand** en klik op **sluiten**.

Als het bestand sinds de laatste keer dat het is opgeslagen, is gewijzigd, wordt u gevraagd dit op te slaan of te negeren.

### <a name="to-display-the-file-path"></a>Het bestandspad weer geven

Wijs op het tabblad bestand de naam van het bestand aan. Het volledig gekwalificeerde pad naar het script bestand wordt weer gegeven in de knop info.

### <a name="to-run-a-script"></a>Een script uitvoeren

Klik op de werk balk op **script uitvoeren**of Klik in het menu **bestand** op **uitvoeren**.

### <a name="to-run-a-portion-of-a-script"></a>Een gedeelte van een script uitvoeren

1. Selecteer een gedeelte van een script in het Script-venster.
2. Klik in het menu **bestand** op **selectie uitvoeren**of klik op de werk balk op **selectie uitvoeren**.

### <a name="to-stop-a-running-script"></a>Een actief script stoppen

Er zijn verschillende manieren om een actief script te stoppen.

- Klik op **Stop bewerking** op de werk balk
- Druk op CTRL + onderbreken
- Selecteer het menu **bestand** en klik op **bewerking stoppen**.

Als u op **CTRL + c** drukt, werkt ook, tenzij er een tekst is geselecteerd. in dat geval wordt **CTRL + c** toegewezen aan de kopieer functie voor de geselecteerde tekst.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Tekst schrijven en bewerken in het Script-venster

U kunt tekst kopiëren, knippen, plakken, zoeken en vervangen in het Script-venster. U kunt ook de laatste actie die u zojuist hebt uitgevoerd, ongedaan maken en opnieuw uitvoeren. De sneltoetsen voor deze acties zijn dezelfde snelkoppelingen die worden gebruikt voor alle Windows-toepassingen.

### <a name="to-enter-text-in-the-script-pane"></a>Tekst in het Script-venster invoeren

1. Verplaats de cursor naar het deel venster script door ergens in het Script venster te klikken of door te klikken op **naar script deel venster** in het menu **beeld** .
2. Een script maken. Syntaxis kleuren en tabblad voltooiing bieden een uitgebreidere bewerkings ervaring in Windows PowerShell ISE.
3. Zie [Tab-aanvulling gebruiken in het Script venster en console venster](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) voor meer informatie over het gebruik van de functie voor het volt ooien van tabs om te helpen bij het typen van.

### <a name="to-find-text-in-the-script-pane"></a>Tekst in het Script-venster zoeken

1. Als u tekst overal wilt zoeken, drukt u op **CTRL + F** of klikt u in het menu **bewerken** op **Zoeken in script**.
2. Als u tekst na de cursor wilt zoeken, drukt u op **F3** of klikt u in het menu **bewerken** op **Volgende zoeken in script**.
3. Als u tekst wilt zoeken vóór de cursor, drukt u op **SHIFT + F3** of klikt u in het menu **bewerken** op **Vorige zoeken in script**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Tekst in het Script-venster zoeken en vervangen

Druk op **CTRL + H** of Klik in het menu **bewerken** op **vervangen in script**. Voer de tekst in die u wilt zoeken en de vervangende tekst en druk vervolgens op **Enter**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Naar een bepaalde tekst regel in het Script-venster gaan

1. Druk in het deel venster script op **CTRL + G** of Klik in het menu **bewerken** op **Ga naar regel**.

2. Voer een regel nummer in.

### <a name="to-copy-text-in-the-script-pane"></a>Tekst in het Script venster kopiëren

1. Selecteer in het deel venster script de tekst die u wilt kopiëren.

2. Druk op **CTRL + C** of Klik in de werk balk op het pictogram **kopiëren** of Klik in het menu **bewerken** op **kopiëren**.

### <a name="to-cut-text-in-the-script-pane"></a>Tekst in het Script-venster knippen

1. Selecteer in het deel venster script de tekst die u wilt knippen.
2. Druk op **CTRL + X** of Klik in de werk balk op het pictogram voor **knippen** of Klik in het menu **bewerken** op **knippen**.

### <a name="to-paste-text-into-the-script-pane"></a>Tekst in het Script-venster plakken

Druk op **CTRL + V** of Klik in de werk balk op het pictogram **Plakken** of Klik in het menu **bewerken** op **Plakken**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Een actie in het Script venster ongedaan maken

Druk op **CTRL + Z** of klik op de werk balk op het pictogram **ongedaan maken** of Klik in het menu **bewerken** op **ongedaan maken**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Een actie opnieuw uitvoeren in het deel venster script

Druk op **CTRL + Y** of Klik in de werk balk op het pictogram **opnieuw** , of Klik in het menu **bewerken** op **opnieuw**.

## <a name="how-to-save-a-script"></a>Een script opslaan

Er wordt een sterretje naast de naam van het script weer gegeven om een bestand te markeren dat niet is opgeslagen sinds het is gewijzigd. Het sterretje verdwijnt wanneer het bestand wordt opgeslagen.

### <a name="to-save-a-script"></a>Een script opslaan

Druk op **CTRL + S** of klik op de werk balk op het pictogram **Opslaan** of Klik in het menu **bestand** op **Opslaan**.

### <a name="to-save-and-name-a-script"></a>Een script opslaan en een naam schrijven

1. Klik in het menu **bestand** op **Opslaan als**. Het dialoog venster **Opslaan als** wordt weer gegeven.
2. Voer in het vak **Bestands naam** een naam in voor het bestand.
3. Selecteer een bestands type in het vak **Opslaan als type** . Selecteer bijvoorbeeld Power shell-scripts (\*. ps1) in het vak **Opslaan als** .
4. Klik op **Opslaan**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Een script in ASCII-code ring opslaan

Windows PowerShell ISE worden standaard nieuwe script bestanden (. ps1), script gegevensbestand (. psd1) en script module bestanden (. psm1) standaard opgeslagen als Unicode (BigEndianUnicode). Â Als u een script in een andere code ring wilt opslaan, zoals ASCII (ANSI), gebruikt u de methoden **Save** of **SaveAs** in het object [$psISE. CurrentFile](object-model/the-ise-object-model-hierarchy.md) .

Met de volgende opdracht wordt een nieuw script opgeslagen als MyScript. ps1 met ASCII-code ring.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

Met de volgende opdracht wordt het huidige script bestand vervangen door een bestand met dezelfde naam, maar met ASCII-code ring.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

Met de volgende opdracht wordt de code ring van het huidige bestand opgehaald.

```powershell
$psISE.CurrentFile.encoding
```

Windows PowerShell ISE ondersteunt de volgende coderings opties: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 en default. De waarde van de standaard optie is afhankelijk van het systeem.

Windows PowerShell ISE wijzigt de code ring van script bestanden niet wanneer u de opdrachten opslaan of opslaan als gebruikt.

## <a name="see-also"></a>Zie ook

- [Kennismaking met Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
