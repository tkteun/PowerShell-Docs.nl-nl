---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: De ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a>De ISESnippetObject
  Een **ISESnippet** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISESnippet. De leden van de **$psISE.CurrentPowerShellTab.Snippets** verzameling zijn alle voorbeelden van **ISESnippet** objecten. De eenvoudigste manier om een codefragment maken is met de [nieuw IseSnippet &#91; PSITPro5_ISE &#93; ](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.

## <a name="properties"></a>Eigenschappen

### <a name="author"></a>auteur
  Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies. 

 De alleen-lezen eigenschap die de naam van de auteur van het fragment opgehaald.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a>CodeFragment
  Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies. 

 De alleen-lezen eigenschap die het codefragment moet worden ingevoegd in de editor opgehaald.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a>Snelkoppeling
  Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies. 

 De alleen-lezen eigenschap die opgehaald van de Windows-sneltoets voor de menuopdracht.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Zie ook
- [Het Object ISESnippetCollection](The-ISESnippetCollection-Object.md) 
- [De Windows PowerShell ISE-objectmodel Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Naslaginformatie voor Windows PowerShell ISE-objectmodel](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [De hiërarchie ISE](The-ISE-Object-Model-Hierarchy.md)

  