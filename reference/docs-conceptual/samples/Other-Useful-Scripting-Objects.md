---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Andere nuttige scriptobjecten
description: In dit artikel worden objecten beschreven die extra script functionaliteit bieden in de Windows PowerShell ISE.
ms.openlocfilehash: c20daa0045bc07b1f21aafa42a80ce7c47ee7331
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500263"
---
# <a name="other-useful-scripting-objects"></a>Andere nuttige scriptobjecten

De volgende objecten bieden extra script functionaliteit in Windows PowerShell ISE. Ze maken geen deel uit van de **$psISE** hiërarchie.

## <a name="useful-scripting-objects"></a>Nuttige script objecten

### <a name="psunsupportedconsoleapplications"></a>$psUnsupportedConsoleApplications

Er zijn enkele beperkingen ten aanzien van de interactie van Windows PowerShell ISE met console toepassingen. Een opdracht of een automatiserings script waarvoor tussen komst van de gebruiker is vereist, werkt mogelijk niet zoals in de Windows Power shell-console. U kunt voor komen dat deze opdrachten of scripts worden uitgevoerd in het opdracht venster Windows PowerShell ISE. Het **$psUnsupportedConsoleApplications** -object houdt een lijst bij van deze opdrachten. Als u de opdrachten in deze lijst probeert uit te voeren, wordt er een bericht weer gegeven dat niet wordt ondersteund. Met het volgende script wordt een item toegevoegd aan de lijst.

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a>$psLocalHelp

Dit is een woordenlijst object dat een context gevoelige toewijzing onderhoudt tussen Help-onderwerpen en de bijbehorende koppelingen in het lokale gecompileerde HTML Help-bestand. Het wordt gebruikt om de lokale Help voor een bepaald onderwerp te vinden. U kunt onderwerpen uit deze lijst toevoegen of verwijderen. In het volgende code voorbeeld ziet u enkele voor beelden van sleutel-waardeparen die zijn opgenomen in `$psLocalHelp` .

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```Output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

Met het volgende script wordt een item toegevoegd aan de lijst.

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a>$psOnlineHelp

Dit is een woordenlijst object dat een context gevoelige toewijzing onderhoudt tussen de titels van de Help-onderwerpen en de bijbehorende externe Url's. Het wordt gebruikt om de Help voor een bepaald onderwerp op het web te vinden. U kunt onderwerpen uit deze lijst toevoegen of verwijderen.

```powershell
$psOnlineHelp | Format-List
```

```Output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

Met het volgende script wordt een item toegevoegd aan de lijst.

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a>Zie ook

[Doel van het scriptobjectmodel van Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
