---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISESnippet-object
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028883"
---
# <a name="the-isesnippetobject"></a>Het ISESnippet-object

Een **ISESnippet** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISESnippet. De leden van de **$psISE.CurrentPowerShellTab.Snippets** verzameling zijn alle voorbeelden van **ISESnippet** objecten. De eenvoudigste manier om het maken van een codefragment is met de [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Properties

### <a name="author"></a>Auteur

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De alleen-lezen eigenschap die haalt u de naam van de auteur van het codefragment.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De alleen-lezen eigenschap waarmee het codefragment moet worden ingevoegd in de editor worden opgehaald.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Snelkoppeling

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De alleen-lezen eigenschap die opgehaald van de Windows sneltoets voor de menuopdracht.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Zie ook

- [Het ISESnippetCollection-Object](The-ISESnippetCollection-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
