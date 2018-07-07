---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Andere nuttige scriptobjecten
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 2ae9bc1864daedbcb0070c5f3862a6c98f8db2d4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893277"
---
# <a name="other-useful-scripting-objects"></a>Andere nuttige scriptobjecten

De volgende objecten bieden extra scripts functionaliteit in Windows PowerShell ISE. Ze zijn niet deel uitmaakt van de **$psISE** hiërarchie.

## <a name="useful-scripting-objects"></a>Nuttige Scripting-objecten

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Er zijn enkele beperkingen met betrekking tot de interactie van Windows PowerShell ISE met consoletoepassingen. Een opdracht of een automatiseringsscript dat vereist dat tussenkomst van de gebruiker mogelijk niet werken voor de werking van de Windows PowerShell-console. Het is raadzaam om te blokkeren van deze opdrachten of scripts niet kunnen worden uitgevoerd in het deelvenster met Windows PowerShell ISE-opdracht. De **$psUnsupportedConsoleApplications** object houdt een lijst van deze opdrachten. Als u probeert uit te voeren van de opdrachten in deze lijst, krijgt u een bericht weergegeven dat ze niet worden ondersteund. Het volgende script voegt een vermelding toe aan de lijst.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Dit is een dictionary-object die wordt onderhouden door een contextgevoelige toewijzing tussen het Help-onderwerpen en hun bijbehorende koppelingen in het lokale gecompileerde HTML Help-bestand. Deze wordt gebruikt om de lokale Help voor een bepaald onderwerp zoekt. U kunt toevoegen of verwijderen van onderwerpen in deze lijst. Het volgende codevoorbeeld toont een voorbeeld sleutel / waarde-paren die zijn opgenomen in `$psLocalHelp`.

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="pslocalhelp-sample-output"></a>Voorbeeld van uitvoer $psLocalHelp

|||
|-|-|
|Sleutel: Computer toevoegen|Waarde: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Sleutel:-Inhoud|Waarde: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

Het volgende script voegt een vermelding toe aan de lijst.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Dit is een dictionary-object die wordt onderhouden door een contextgevoelige toewijzing tussen de titels van Help-onderwerpen en de bijbehorende externe URL's. Deze wordt gebruikt om de Help voor een bepaald onderwerp vinden op het web. U kunt toevoegen of verwijderen van onderwerpen in deze lijst.

```powershell
$psOnlineHelp | Format-List
```

## <a name="psonilnehelp-sample-output"></a>Voorbeeld van uitvoer $psOnilneHelp

|||
|-|-|
|Sleutel: Computer toevoegen|Waarde: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Sleutel:-Inhoud|Waarde: http://go.microsoft.com/fwlink/p/?LinkID=113278|

Het volgende script voegt een vermelding toe aan de lijst.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Zie ook

[Doel van de Scriptobjectmodel van Windows PowerShell ISE](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)