---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Het ISESnippetCollection-object
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810055"
---
# <a name="the-isesnippetcollection-object"></a>Het ISESnippetCollection-object

Het **ISESnippetCollection** -object is een verzameling **ISESnippet** -objecten. De verzameling bestanden die is gekoppeld aan een **PowerShellTab** -object, is een lid van deze klasse. Een voor beeld is de `$psISE.CurrentPowerShellTab.Files` verzameling.

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>Load \( filepath\)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee wordt een `.snippets.ps1xml` bestand geladen dat door de gebruiker gedefinieerde fragmenten bevat. De eenvoudigste manier om fragmenten te maken, is door de `New-IseSnippet` cmdlet te gebruiken, die deze automatisch opslaat in de profielmap, zodat ze elke keer dat u begint Windows PowerShell ISE worden geladen.

**Filepath** -teken reeks het pad en de bestands naam naar een. fragmenten. ps1xml-bestand dat fragment definities bevat.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Zie ook

- [Het ISESnippet-object](The-ISESnippetObject.md)
- [Doel van het scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De ISE-object model hiërarchie](The-ISE-Object-Model-Hierarchy.md)
