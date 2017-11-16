---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Andere nuttige Scripting objecten
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a>Andere nuttige Scripting objecten
  De volgende objecten bieden extra scripting functionaliteit in Windows PowerShell ISE. Ze maken geen deel uit van de **$psISE** hiërarchie.

## <a name="useful-scripting-objects"></a>Nuttige Scripting-objecten

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications
 Er zijn enkele beperkingen op de interactie van Windows PowerShell ISE met consoletoepassingen. Een opdracht of een automatiseringsscript dat vereist dat tussenkomst van de gebruiker werken de werking van de Windows PowerShell-console niet. Het is raadzaam om deze opdrachten of scripts worden uitgevoerd in het deelvenster met Windows PowerShell ISE-opdracht te blokkeren. De **$psUnsupportedConsoleApplications** object houdt een lijst van deze opdrachten. Als u probeert de opdrachten uitvoeren in deze lijst, krijgt u een bericht dat ze niet worden ondersteund. Het volgende script voegt een vermelding toe aan de lijst.

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a>$psLocalHelp
 Dit is een dictionary-object dat wordt de contextgevoelige toewijzing tussen het Help-onderwerpen en hun bijbehorende koppelingen in het lokale gecompileerde HTML Help-bestand. Deze wordt gebruikt voor het vinden van de lokale Help voor een bepaald onderwerp. U kunt toevoegen of verwijderen van onderwerpen uit deze lijst. Het volgende codevoorbeeld toont een aantal voorbeelden van sleutel-waardeparen die zijn opgenomen in **$psLocalHelp**.

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a>Voorbeelduitvoer

|||
|-|-|
|Sleutel:-Computer|Waarde: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm|
|Sleutel:-Inhoud|Waarde: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm|

 Het volgende script voegt een vermelding toe aan de lijst.

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp
 Dit is een dictionary-object dat wordt de contextgevoelige toewijzing tussen de titels van Help-onderwerpen en de bijbehorende externe URL's. Wordt gebruikt voor het vinden van de Help voor een bepaald onderwerp op het web. U kunt toevoegen of verwijderen van onderwerpen uit deze lijst.

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a>Voorbeelduitvoer

|||
|-|-|
|Sleutel:-Computer|Waarde: http://go.microsoft.com/fwlink/p/?LinkID=135194|
|Sleutel:-Inhoud|Waarde: http://go.microsoft.com/fwlink/p/?LinkID=113278|

 Het volgende script voegt een vermelding toe aan de lijst.

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Zie ook
- [De Windows PowerShell ISE-objectmodel Scripting](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
