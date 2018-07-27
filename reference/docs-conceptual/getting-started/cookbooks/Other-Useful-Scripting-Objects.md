---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Andere nuttige scriptobjecten
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 04e94f858b568928b3910dd0ee85a912a6afc264
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268497"
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

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

Het volgende script voegt een vermelding toe aan de lijst.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Dit is een dictionary-object die wordt onderhouden door een contextgevoelige toewijzing tussen de titels van Help-onderwerpen en de bijbehorende externe URL's. Deze wordt gebruikt om de Help voor een bepaald onderwerp vinden op het web. U kunt toevoegen of verwijderen van onderwerpen in deze lijst.

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

Het volgende script voegt een vermelding toe aan de lijst.

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Zie ook

[Doel van de Scriptobjectmodel van Windows PowerShell ISE](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)