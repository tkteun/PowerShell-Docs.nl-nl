---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Het ISESnippet-object
ms.openlocfilehash: f810e6b26f0ded04be15bdc37f336d7890e29dad
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810930"
---
# <a name="the-isesnippetobject"></a>Het ISESnippet-object

Een **ISESnippet** -object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISESnippet. De leden van de `$psISE.CurrentPowerShellTab.Snippets` verzameling zijn alle voor beelden van **ISESnippet** -objecten. De eenvoudigste manier om een fragment te maken, is door de cmdlet [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) te gebruiken.

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
- [Doel van het scriptobjectmodel van Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [De ISE-object model hiërarchie](The-ISE-Object-Model-Hierarchy.md)
