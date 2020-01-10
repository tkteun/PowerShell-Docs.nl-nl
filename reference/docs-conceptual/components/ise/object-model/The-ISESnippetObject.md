---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISESnippet-object
ms.openlocfilehash: 60456ec90f56753fa96f141b8b8299ef3f7e41c9
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736961"
---
# <a name="the-isesnippetobject"></a>Het ISESnippet-object

Een **ISESnippet** -object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISESnippet. De leden van de `$psISE.CurrentPowerShellTab.Snippets` verzameling zijn alle voor beelden van **ISESnippet** -objecten. De eenvoudigste manier om een fragment te maken, is door de cmdlet [New-IseSnippet](/reference/5.1/ISE/New-IseSnippet.md) te gebruiken.

## <a name="properties"></a>Eigenschappen

### <a name="author"></a>Auteur

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap waarmee de naam van de auteur van het fragment wordt opgehaald.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>Cofragmentatie

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap waarmee het code fragment wordt opgehaald dat in de editor moet worden ingevoegd.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Shortcutdimensie

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap waarmee de Windows-sneltoets wordt opgehaald voor de menu opdracht.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Zie ook

- [Het ISESnippetCollection-object](The-ISESnippetCollection-Object.md)
- [Doel van het Windows PowerShell ISE scripting object model](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
