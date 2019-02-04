---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISESnippetCollection-object
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684610"
---
# <a name="the-isesnippetcollection-object"></a>Het ISESnippetCollection-object

De **ISESnippetCollection** object is een verzameling van **ISESnippet** objecten. De verzameling bestanden dat is gekoppeld aan een **PowerShellTab** object is lid van deze klasse. Een voorbeeld is de **$psISE.CurrentPowerShellTab.Files** verzameling.

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Belasting een. snippets.ps1xml-bestand met de gebruiker gedefinieerde codefragmenten. Er is de eenvoudigste manier om codefragmenten maken met de cmdlet New-IseSnippet, die automatisch in de profielmap van uw opgeslagen zodat ze geladen elke keer worden dat u start Windows PowerShell ISE.

**FilePathName** - tekenreeks van het pad en bestandsnaam naar een. snippets.ps1xml-bestand dat fragment definities bevat.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Zie ook

- [The ISESnippetObject](The-ISESnippetObject.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)