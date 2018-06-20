---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISESnippetCollection-object
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950947"
---
# <a name="the-isesnippetcollection-object"></a>Het ISESnippetCollection-object

De **ISESnippetCollection** object is een verzameling **ISESnippet** objecten. De verzameling bestanden dat is gekoppeld aan een **PowerShellTab** object is lid van deze klasse. Een voorbeeld is de **$psISE.CurrentPowerShellTab.Files** verzameling.

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>Load\( FilePathName \)

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Laadt een. snippets.ps1xml-bestand waarin de gebruiker gedefinieerde codefragmenten. De eenvoudigste manier om fragmenten te maken is met de cmdlet New-IseSnippet, waarmee automatisch in de profielmap van uw opgeslagen zodat ze worden geladen telkens wanneer u Windows PowerShell ISE start.

**FilePathName** - tekenreeks van het pad en bestandsnaam naar een. snippets.ps1xml-bestand dat codefragment definities bevat.

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a>Zie ook

- [De ISESnippetObject](The-ISESnippetObject.md)
- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)