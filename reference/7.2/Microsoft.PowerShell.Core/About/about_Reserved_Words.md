---
description: Een lijst met gereserveerde woorden die niet als id's kunnen worden gebruikt, omdat ze een speciale betekenis hebben in Power shell.
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: 95911e328a50c173235f47a7610393124781555d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705793"
---
# <a name="about-reserved-words"></a>Over gereserveerde woorden

## <a name="short-description"></a>KORTE BESCHRIJVING
Een lijst met gereserveerde woorden die niet als id's kunnen worden gebruikt, omdat ze een speciale betekenis hebben in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

Er zijn bepaalde woorden met een speciale betekenis in Power shell. Wanneer deze woorden zonder aanhalings tekens worden weer gegeven, probeert Power shell hun speciale betekenis toe te passen in plaats van deze als teken reeksen te behandelen. Als u deze woorden wilt gebruiken als parameter argumenten in een opdracht of script zonder hun speciale betekenis aan te roepen, plaatst u de gereserveerde woorden tussen aanhalings tekens.

De volgende gereserveerde woorden zijn opgenomen in Power shell:

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

Verschillende taal trefwoorden, waaronder `Foreach` , `If` , `For` en `While` , hebben hun eigen Help-artikelen. Als u deze wilt weer geven, typt `Get-Help about_` en voegt u het tref woord toe. Als u bijvoorbeeld informatie wilt ophalen over de `Foreach` -instructie, typt u:

```powershell
Get-Help about_ForEach
```

Voor informatie over het `Filter` overzicht of de `Return` syntaxis van de instructie typt u:

```powershell
Get-Help about_Functions
```

Voor informatie over andere gereserveerde woorden, typt u:

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> Niet elk gereserveerd woord heeft zijn eigen Help-artikel. Als geen `Get-Help` artikel retourneert, kunt u zoeken naar artikelen over het gereserveerde woord met behulp van de volgende opdracht:
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a>ZIE OOK

- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Language_Keywords](about_Language_Keywords.md)
- [about_Parsing](about_Parsing.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Special_Characters](about_Special_Characters.md)
