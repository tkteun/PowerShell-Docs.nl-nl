---
description: Hierin wordt een taal opdracht beschreven die u kunt gebruiken om overzichts lijsten uit te voeren op basis van de resultaten van een of meer voorwaardelijke tests.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 33c0050cb5f8c3dfa623213b288ef3a84d10099d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252148"
---
# <a name="about-if"></a>Over als

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt een taal opdracht beschreven die u kunt gebruiken om overzichts lijsten uit te voeren op basis van de resultaten van een of meer voorwaardelijke tests.

## <a name="long-description"></a>LANGE BESCHRIJVING

U kunt de- `If` instructie gebruiken om code blokken uit te voeren als een opgegeven voorwaardelijke test resulteert in waar. U kunt ook een of meer aanvullende voorwaardelijke tests opgeven die moeten worden uitgevoerd als alle voor gaande tests resulteren in ONWAAR. Ten slotte kunt u een extra code blok opgeven dat wordt uitgevoerd als er geen andere eerdere voorwaardelijke test wordt geëvalueerd als waar.

### <a name="syntax"></a>Syntax

In het volgende voor beeld ziet u de syntaxis van de `If` instructie:

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

Wanneer u een `If` -instructie uitvoert, evalueert Power shell de `<test1>` voorwaardelijke expressie als waar of onwaar. Als `<test1>` de waarde True is, `<statement list 1>` wordt uitgevoerd en Power shell de `If` instructie verlaat. Als `<test1>` is ingesteld op False, wordt de voor waarde die is opgegeven door de voorwaardelijke instructie door Power shell geëvalueerd `<test2>` .

Als `<test2>` de waarde True is, `<statement list 2>` wordt uitgevoerd en Power shell de `If` instructie verlaat. Als zowel `<test1>` als `<test2>` wordt geëvalueerd als onwaar, `<statement list 3` wordt het> code blok uitgevoerd en wordt de if-instructie door Power shell afgesloten.

U kunt meerdere elseif-instructies gebruiken om een reeks voorwaardelijke tests te koppelen. Dit betekent dat elke test alleen wordt uitgevoerd als alle vorige tests onwaar zijn.
Als u een instructie moet maken `If` die veel elseif-instructies bevat, kunt u in plaats daarvan een switch instructie gebruiken.

Voorbeelden:

De eenvoudigste `If` instructie bevat één opdracht en bevat geen elseif-instructies of enige else-instructies. In het volgende voor beeld ziet u de meest eenvoudige vorm van de `If` instructie:

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

Als in dit voor beeld de variabele $a groter is dan 2, wordt de voor waarde geëvalueerd als waar en wordt de instructie lijst uitgevoerd. Als $a echter kleiner is dan of gelijk is aan 2 of niet een bestaande variabele is, `If` wordt er geen bericht weer gegeven in de instructie.

Door een else-instructie toe te voegen, wordt een bericht weer gegeven wanneer $a kleiner is dan of gelijk is aan 2. Zoals in het volgende voor beeld wordt weer gegeven:

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

Als u dit voor beeld verder wilt verfijnen, kunt u de instructie elseif gebruiken om een bericht weer te geven wanneer de waarde van $a gelijk is aan 2. Zoals in het volgende voor beeld wordt weer gegeven:

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

### <a name="using-the-ternary-operator-syntax"></a>De syntaxis van de ternaire operator gebruiken

Power shell 7,0 heeft een nieuwe syntaxis geïntroduceerd met behulp van de ternaire operator. Het volgt de syntaxis van C# ternaire Opera tors:

```Syntax
<condition> ? <if-true> : <if-false>
```

De ternaire operator gedraagt zich als de vereenvoudigde `if-else` instructie. De `<condition>` expressie wordt geëvalueerd en het resultaat wordt geconverteerd naar een Booleaanse waarde om te bepalen welke vertakking vervolgens moet worden geëvalueerd:

- De `<if-true>` expressie wordt uitgevoerd als de `<condition>` expressie True is
- De `<if-false>` expressie wordt uitgevoerd als de `<condition>` expressie onwaar is

Bijvoorbeeld:

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

In dit voor beeld is de waarde van `$message` ' Path exists ' bij het `Test-Path` retour neren `$true` . Wanneer `Test-Path` retourneert `$false` , is de waarde van `$message` is "pad niet gevonden".

```powershell
$service = Get-Service BITS
$service.Status -eq 'Running' ? (Stop-Service $service) : (Start-Service $service)
```

Als in dit voor beeld de service wordt uitgevoerd, wordt deze gestopt en als de status niet wordt **uitgevoerd** , wordt deze gestart.

## <a name="see-also"></a>ZIE OOK

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Switch](about_Switch.md)

