---
ms.date: 08/26/2019
ms.topic: reference
title: Ondersteuning voor jokertekens in de cmdlet-parameters
description: Ondersteuning voor jokertekens in de cmdlet-parameters
ms.openlocfilehash: 06693c62cd2613050bdeb9d6b12ad6e9597a9894
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646387"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Ondersteuning voor jokertekens in de cmdlet-parameters

Vaak moet u een cmdlet ontwerpen om uit te voeren op basis van een groep resources en niet op basis van één resource. Een cmdlet kan bijvoorbeeld alle bestanden in een gegevens archief met dezelfde naam of extensie moeten zoeken. U moet ondersteuning bieden voor joker tekens wanneer u een cmdlet ontwerpt die wordt uitgevoerd voor een groep resources.

> [!NOTE]
> Het gebruik van joker tekens wordt soms ook wel *globbing* genoemd.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Windows Power shell-cmdlets die gebruikmaken van joker tekens

 Veel Windows Power shell-cmdlets ondersteunen joker tekens voor hun parameter waarden. Bijna elke cmdlet met een `Name` or- `Path` para meter ondersteunt bijvoorbeeld joker tekens voor deze para meters. (Hoewel de meeste cmdlets die een `Path` para meter hebben ook een `LiteralPath` para meter hebben die geen joker tekens ondersteunt.) De volgende opdracht laat zien hoe een Joker teken wordt gebruikt om alle cmdlets in de huidige sessie te retour neren waarvan de naam de bewerking Get bevat.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Ondersteunde joker tekens

Windows Power shell ondersteunt de volgende joker tekens.

| Vervanging |                             Beschrijving                             |  Voorbeeld   |     Komt overeen met      | Komt niet overeen met |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Komt overeen met nul of meer tekens, beginnend bij de opgegeven positie | `a*`       | A, AG, Apple     |                |
| ?        | Komt overeen met een teken op de opgegeven positie                     | `?n`       | Een, in, op       | uitgevoerd            |
| [ ]      | Komt overeen met een reeks tekens                                       | `[a-l]ook` | Book, Cook, zoeken | Nook, geduurde     |
| [ ]      | Komt overeen met de opgegeven tekens                                    | `[bn]ook`  | Book, Nook       | Cook, zoeken     |

Wanneer u cmdlets ontwerpt die ondersteuning bieden voor joker tekens, toestaan combi Naties van joker tekens. De volgende opdracht gebruikt de `Get-ChildItem` cmdlet bijvoorbeeld om alle txt-bestanden op te halen die zich in de map c:\Techdocs bevinden en die beginnen met de letters ' a ' tot en met ' l '.

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

In de vorige opdracht wordt het bereik Joker teken gebruikt `[a-l]` om op te geven dat de bestands naam moet beginnen met de tekens ' a ' tot en met ' l ' en het `*` Joker teken als tijdelijke aanduiding gebruikt voor tekens tussen de eerste letter van de bestands naam en de extensie **. txt** .

In het volgende voor beeld wordt een Joker teken voor een bereik gebruikt dat de letter ' d ' uitsluit, maar alle andere letters van ' a ' tot en met ' f ' bevat.

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Letterlijke tekens afhandelen in Joker teken patronen

Als het Joker teken dat u opgeeft letterlijke tekens bevat die niet mogen worden interpretted als joker tekens, gebruikt u het apostroffen-teken ( `` ` `` ) als escape-teken. Wanneer u letterlijke tekens int de Power shell-API opgeeft, gebruikt u één apostroffen. Wanneer u letterlijke tekens opgeeft bij de Power shell-opdracht prompt, gebruikt u twee accents graves.

Het volgende patroon bevat bijvoorbeeld twee haken die letterlijk moeten worden uitgevoerd.

Bij gebruik in de API voor Power shell:

- "John Smith \` [* ']"

Bij gebruik van de Power shell-opdracht prompt:

- "John Smith \` \` [* \` ']"

Dit patroon komt overeen met ' John Smith [marketing] ' of ' John Smith [development] '. Bijvoorbeeld:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Uitvoer van de cmdlet en Joker tekens

Wanneer cmdlet-para meters ondersteuning bieden voor joker tekens, genereert de bewerking meestal een matrix uitvoer.
In sommige gevallen is het niet zinvol om een matrix uitvoer te ondersteunen, omdat de gebruiker slechts één item kan gebruiken. De `Set-Location` cmdlet biedt bijvoorbeeld geen ondersteuning voor matrix uitvoer omdat de gebruiker slechts één locatie instelt. In dit geval ondersteunt de cmdlet nog steeds joker tekens, maar worden oplossingen op één locatie afgedwongen.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Klasse WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
