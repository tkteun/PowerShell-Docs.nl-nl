---
ms.date: 12/31/2019
title: Het ISESnippetCollection-object
description: Het ISESnippetCollection-object is een verzameling ISESnippet-objecten. De verzameling bestanden die is gekoppeld aan een PowerShellTab-object, is een lid van deze klasse.
ms.openlocfilehash: e6170ddf72d5ead840aa3015d4de1dcb21dbfeff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655969"
---
# <a name="the-isesnippetcollection-object"></a>Het ISESnippetCollection-object

Het **ISESnippetCollection** -object is een verzameling **ISESnippet** -objecten. De verzameling bestanden die is gekoppeld aan een **PowerShellTab** -object, is een lid van deze klasse. Een voor beeld is de `$psISE.CurrentPowerShellTab.Files` verzameling.

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>Load \( filepath \)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee wordt een `.snippets.ps1xml` bestand geladen dat door de gebruiker gedefinieerde fragmenten bevat. De eenvoudigste manier om fragmenten te maken, is door de `New-IseSnippet` cmdlet te gebruiken, die deze automatisch opslaat in de profielmap, zodat ze elke keer dat u begint Windows PowerShell ISE worden geladen.

**Filepath** -teken reeks het pad en de bestands naam naar een .snippets.ps1XML-bestand dat fragment definities bevat.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Zie ook

- [Het ISESnippet-object](The-ISESnippetObject.md)
- [Doel van het scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De ISE-object model hiërarchie](The-ISE-Object-Model-Hierarchy.md)
