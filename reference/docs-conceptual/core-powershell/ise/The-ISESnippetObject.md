---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISESnippet-object
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isesnippetobject"></a>Het ISESnippet-object

Een **ISESnippet** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISESnippet. De leden van de **$psISE.CurrentPowerShellTab.Snippets** verzameling zijn alle voorbeelden van **ISESnippet** objecten. De eenvoudigste manier om een codefragment maken is met de [nieuw IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Eigenschappen

### <a name="author"></a>auteur

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap die de naam van de auteur van het fragment opgehaald.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap die het codefragment moet worden ingevoegd in de editor opgehaald.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Snelkoppeling

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap die opgehaald van de Windows-sneltoets voor de menuopdracht.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Zie ook

- [Het Object ISESnippetCollection](The-ISESnippetCollection-Object.md)
- [Doel van de Windows PowerShell ISE-objectmodel Scripting](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)