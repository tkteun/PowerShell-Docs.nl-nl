---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Bekende opdrachtnamen gebruiken
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 37fc6dfad5a2f1363254744141dcab1e13aa5066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952678"
---
# <a name="using-familiar-command-names"></a>Bekende opdrachtnamen gebruiken
Aangeroepen met een mechanisme *aliasing*, kunnen gebruikers om te verwijzen naar opdrachten met alternatieve namen van Windows PowerShell. Aliasing kan gebruikers met ervaring in andere houders hergebruiken algemene namen van opdrachten die ze al bekend vergelijkbare bewerkingen uitvoeren in Windows PowerShell. Hoewel er geen Windows PowerShell-aliassen in detail worden besproken, kunt u ze nog steeds gebruiken als u aan de slag met Windows PowerShell.

De naam van een opdracht die u typt koppelt aliasing aan een andere opdracht. Bijvoorbeeld, Windows PowerShell is een interne functie met de naam **wissen Host** die het uitvoervenster worden gewist. Als u de **cls** of **wissen** een opdrachtprompt, Windows PowerShell-opdracht wordt geïnterpreteerd dat dit is een alias voor de **wissen Host** functioneren en de wordtuitgevoerd **Schakel Host** functie.

Deze functie helpt gebruikers voor meer informatie over Windows PowerShell. Eerst de meeste Cmd.exe- en UNIX-gebruikers hebben een grote tekenreeks van opdrachten die gebruikers al bekend is met de naam en hoewel de Windows PowerShell-equivalenten niet identiek resultaten opleveren mogen, sluiten in de vorm die gebruikers gebruiken kunnen om te werken zonder te zijn onthouden eerst de namen van de Windows PowerShell. Ten tweede is de primaire bron van vervelend in het leren van een nieuwe shell wanneer de gebruiker al bekend bent met een andere shell is, de fouten die worden veroorzaakt door 'vinger geheugen'. Als u Cmd.exe hebt gebruikt voor het jaar, wanneer u een volledige van uitvoer scherm hebt en wilt opruimen deze, typt u reflexively de **cls** opdracht en druk op ENTER. Zonder de alias voor de **wissen Host** functie in Windows PowerShell, krijgt u gewoon het foutbericht '**'cls' wordt niet herkend als een cmdlet, een functie, een programma of een scriptbestand.**' en blijft niets van wat te doen om te wissen van de uitvoer.

Hier volgt een kort overzicht van de algemene Cmd.exe- en UNIX-opdrachten die u in Windows PowerShell kunt gebruiken:

|||||
|-|-|-|-|
|CAT|Dir|koppelen|rm|
|cd|echo|verplaatsen|rmdir|
|chdir|wissen|popd|slaapstand|
|wissen|h|ps|Sorteren|
|CLS|Geschiedenis|pushd|t|
|Kopiëren|kill|pwd|Type|
|del|LP|r|schrijven|
|diff|Ls|ren||

Als u merkt met behulp van een van deze opdrachten reflexively en meer informatie over de werkelijke naam van de systeemeigen Windows PowerShell-opdracht wilt, kunt u de **Get-Alias** opdracht:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Voorbeelden meer om leesbaar te maken, voorkomt de Windows PowerShell User's Guide doorgaans gebruik van aliassen. Echter kan meer weten over aliassen dit vroeg toch nuttig zijn als u met willekeurige codefragmenten van Windows PowerShell-code uit een andere bron werkt of wilt u uw eigen aliassen definiëren. De rest van deze sectie wordt uitgelegd hoe standaard aliassen en het definiëren van uw eigen aliassen.

### <a name="interpreting-standard-aliases"></a>Standaard-aliassen interpreteren
In tegenstelling tot de hierboven beschreven, aliassen zijn ontworpen voor compatibiliteit met andere interfaces naam, zijn de aliassen die is ingebouwd in Windows PowerShell in het algemeen ontworpen als beknopt alternatief bevat. Deze kortere namen snel kunnen worden getypt, maar zijn niet mogelijk om te lezen als u niet wat ze weet naar verwijzen.

Windows PowerShell probeert te manipuleren tussen duidelijkheid en beknopt alternatief bevat door te geven van een reeks standaard aliassen die zijn gebaseerd op steno namen voor algemene termen en woorden. Hierdoor kan een kernset aan aliassen voor algemene cmdlets die kunnen gelezen worden als u weet dat de namen steno. Bijvoorbeeld, in de standaard aliassen de term **ophalen** is afgekort tot **g**, de term **ingesteld** is afgekort tot **s**, het zelfstandig naamwoord **Item** is afgekort tot **ik**, het zelfstandig naamwoord **locatie** is afgekort tot **l**, en het zelfstandig naamwoord opdracht is afgekort tot **cm**.

Hier volgt een voorbeeld van een korte ter illustratie van hoe dit werkt. De standaard alias voor Get-Item is afkomstig uit combineren **g** voor Get en **ik** voor Item: **gi**. De standaard alias voor Set-Item is afkomstig uit combineren **s** voor Set en **ik** voor Item: **si**. De standaard alias voor de Get-locatie afkomstig is van combineren **g** voor Get en **l** voor locatie **GB**. De standaard alias voor de locatie van de Set afkomstig is van combineren **s** voor Set en **l** voor locatie **sl**. De standaard alias voor Get-Command afkomstig is van combineren **g** voor Get en **cm** voor opdracht **gcm**. Er is geen opdracht Set-cmdlet, maar als er waren, we zou kunnen te raden de standaard alias vandaan **s** voor Set en **cm** voor opdracht: **scm**. Bovendien mensen bekend zijn met Windows PowerShell-aliasing die optreden **scm** zou kunnen te raden dat de alias die naar Set-opdracht verwijst.

### <a name="creating-new-aliases"></a>Nieuwe aliassen maken
U kunt uw eigen aliassen die met de cmdlet Set-Alias maken. De volgende instructies wordt bijvoorbeeld de standaard-cmdlet-aliassen die wordt besproken in standaard aliassen interpreteren maken:

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Intern, Windows PowerShell maakt gebruik van opdrachten zoals deze tijdens het opstarten, maar deze aliassen zijn niet gewijzigd. Als u uit te voeren een van deze opdrachten probeert, krijgt u een foutbericht aangegeven dat de alias kan niet worden gewijzigd. Bijvoorbeeld:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```