---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISESnippetCollection-object
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736042"
---
# <a name="the-isesnippetcollection-object"></a>Het ISESnippetCollection-object

Het **ISESnippetCollection** -object is een verzameling **ISESnippet** -objecten. De verzameling bestanden die is gekoppeld aan een **PowerShellTab** -object, is een lid van deze klasse. Een voor beeld is de verzameling `$psISE.CurrentPowerShellTab.Files`.

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>\( bestandspad laden \)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee wordt een `.snippets.ps1xml`-bestand geladen dat door de gebruiker gedefinieerde fragmenten bevat. De eenvoudigste manier om fragmenten te maken, is met behulp van de cmdlet `New-IseSnippet`, die deze automatisch opslaat in de profielmap, zodat deze elke keer dat u begint Windows PowerShell ISE wordt geladen.

**Filepath** -teken reeks het pad en de bestands naam naar een. fragmenten. ps1xml-bestand dat fragment definities bevat.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Zie ook

- [De ISESnippetObject](The-ISESnippetObject.md)
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
