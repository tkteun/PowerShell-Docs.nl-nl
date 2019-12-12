---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISESnippetCollection-object
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030512"
---
# <a name="the-isesnippetcollection-object"></a>Het ISESnippetCollection-object

Het **ISESnippetCollection** -object is een verzameling **ISESnippet** -objecten. De verzameling bestanden die is gekoppeld aan een **PowerShellTab** -object, is een lid van deze klasse. Een voor beeld is de verzameling **$psISE. CurrentPowerShellTab. files** .

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>\( bestandspad laden \)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee wordt een. fragmenten. ps1xml-bestand geladen dat door de gebruiker gedefinieerde fragmenten bevat. De eenvoudigste manier om fragmenten te maken, is met behulp van de cmdlet New-IseSnippet, die deze automatisch opslaat in de profielmap, zodat ze elke keer dat u begint Windows PowerShell ISE worden geladen.

**Filepath** -teken reeks het pad en de bestands naam naar een. fragmenten. ps1xml-bestand dat fragment definities bevat.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Zie ook

- [De ISESnippetObject](The-ISESnippetObject.md)
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
