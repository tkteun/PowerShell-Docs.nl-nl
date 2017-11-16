---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a>Het Object ISESnippetCollection
  De **ISESnippetCollection** object is een verzameling **ISESnippet** objecten. De verzameling bestanden dat is gekoppeld aan een **PowerShellTab** object is lid van deze klasse. Een voorbeeld is de **$psISE.CurrentPowerShellTab.Files** verzameling.

## <a name="methods"></a>Methoden

### <a name="load-filepathname-"></a>Load\( FilePathName\)
  Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies. 

 Laadt een. snippets.ps1xml-bestand waarin de gebruiker gedefinieerde codefragmenten. De eenvoudigste manier om fragmenten te maken is met de cmdlet New-IseSnippet, waarmee automatisch in de profielmap van uw opgeslagen zodat ze worden geladen telkens wanneer u Windows PowerShell ISE start.

 **FilePathName** - tekenreeks van het pad en bestandsnaam naar een. snippets.ps1xml-bestand dat codefragment definities bevat.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a>Zie ook
- [De ISESnippetObject](The-ISESnippetObject.md) 
- [De Windows PowerShell ISE-objectmodel Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Naslaginformatie voor Windows PowerShell ISE-objectmodel](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [De hiërarchie ISE](The-ISE-Object-Model-Hierarchy.md)

  
