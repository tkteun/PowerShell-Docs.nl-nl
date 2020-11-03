---
description: Hierin wordt een taal opdracht beschreven die u kunt gebruiken om-instructies uit te voeren op basis van een voorwaardelijke test.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 5f4fc025ee36e99de7d2ad7a00b1c1dca9c5ce3f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252338"
---
# <a name="about-for"></a>Over voor

## <a name="short-description"></a>Korte beschrijving
Hierin wordt een taal opdracht beschreven die u kunt gebruiken om-instructies uit te voeren op basis van een voorwaardelijke test.

## <a name="long-description"></a>Lange beschrijving

De `For` instructie (ook wel een `For` lus genoemd) is een taal constructie die u kunt gebruiken om een lus te maken waarmee opdrachten in een opdracht blok worden uitgevoerd terwijl een opgegeven voor waarde wordt geëvalueerd `$true` .

Een typisch gebruik van de `For` lus is het herhalen van een matrix met waarden en voor het uitvoeren van een subset van deze waarden. In de meeste gevallen kunt u een instructie gebruiken als u alle waarden in een matrix wilt herhalen `Foreach` .

### <a name="syntax"></a>Syntax

Hieronder ziet u de `For` syntaxis van de instructie.

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

De tijdelijke aanduiding **init** vertegenwoordigt een of meer opdrachten die worden uitgevoerd voordat de lus begint. Normaal gesp roken gebruikt u het **init** -gedeelte van de-instructie om een variabele met een begin waarde te maken en initialiseren.

Deze variabele wordt vervolgens de basis voor de voor waarde die in het volgende gedeelte van de instructie moet worden getest `For` .

De tijdelijke aanduiding **voor de voor waarde** vertegenwoordigt het gedeelte van de `For` instructie dat wordt omgezet in een `$true` of `$false` **Booleaanse** waarde. Power shell evalueert de voor waarde telkens wanneer de `For` lus wordt uitgevoerd. Als de instructie is `$true` , worden de opdrachten in het opdracht blok uitgevoerd en wordt de instructie opnieuw geëvalueerd. Als de voor waarde nog steeds is `$true` , worden de opdrachten in de **instructie lijst** opnieuw uitgevoerd. De lus wordt herhaald totdat de voor waarde wordt gewijzigd `$false` .

De tijdelijke aanduiding voor **herhalingen** bevat een of meer opdrachten, gescheiden door komma's, die worden uitgevoerd telkens wanneer de lus wordt herhaald. Dit wordt meestal gebruikt voor het wijzigen van een variabele die wordt getest in het onderdeel **voor waarde** van de-instructie.

De tijdelijke aanduiding **lijst** bevat een verzameling van een of meer opdrachten die elke keer dat de lus wordt ingevoerd of herhaald wordt uitgevoerd. De inhoud van de **instructie lijst** wordt omgeven door accolades.

### <a name="support-for-multiple-operations"></a>Ondersteuning voor meerdere bewerkingen

De volgende syntaxis worden ondersteund voor bewerkingen met meerdere toewijzingen in de instructie **init** :

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

De volgende syntaxis worden ondersteund voor bewerkingen met meerdere toewijzingen in de instructie **repeat** :

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> Andere bewerkingen dan vóór of na het uitvoeren van een incrementeel werken mogelijk niet met alle-syntaxis.

Voor meerdere **voor waarden** worden logische Opera tors gebruikt, zoals wordt getoond in het volgende voor beeld.

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

Zie [about_Logical_Operators](about_Logical_Operators.md)voor meer informatie.

### <a name="examples"></a>Voorbeelden

Een instructie vereist mini maal `For` het haakje rond het **init** , de **voor waarde** en het **herhaalde** gedeelte van de instructie en een opdracht omgeven door accolades in het **overzichts** deel van de instructie.

Houd er rekening mee dat de komende voor beelden opzettelijk code weer geven buiten de- `For` instructie. In latere voor beelden is code geïntegreerd in de- `For` instructie.

Met de volgende `For` instructie wordt de waarde van de variabele bijvoorbeeld continu weer gegeven `$i` totdat u de opdracht hand matig uitbreekt door op CTRL + C te drukken.

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

U kunt extra opdrachten toevoegen aan de lijst met overzichten, zodat de waarde van `$i` wordt verhoogd met 1 telkens wanneer de lus wordt uitgevoerd, zoals in het volgende voor beeld wordt getoond.

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

Totdat u de opdracht opbreekt door op CTRL + C te drukken, wordt door deze instructie voortdurend de waarde van de variabele weer gegeven `$i` wanneer deze wordt verhoogd met 1 telkens wanneer de lus wordt uitgevoerd.

In plaats van de waarde van de variabele te wijzigen in het overzichts deel van het `For` overzicht, kunt u het **herhalings** gedeelte van de `For` instructie als volgt gebruiken.

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

Deze instructie wordt pas voor onbepaalde tijd herhaald als u de opdracht uitbreekt door op CTRL + C te drukken.

U kunt de `For` lus beëindigen met een *voor waarde*. U kunt een voor waarde plaatsen met behulp van het **voor waarde** -gedeelte van de `For` instructie. De `For` lus wordt beëindigd wanneer de voor waarde wordt geëvalueerd `$false` .

In het volgende voor beeld `For` wordt de lus uitgevoerd terwijl de waarde van `$i` kleiner dan of gelijk aan 10 is.

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

In plaats van het maken en initialiseren van de variabele buiten de `For` -instructie kunt u deze taak in de `For` lus uitvoeren met behulp van het gedeelte **init** van de- `For` instructie.

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

U kunt regel terugloop gebruiken in plaats van punt komma's om de **initialisatie** , **voor waarde** en **herhaling** delen van de instructie te beperken `For` . In het volgende voor beeld ziet `For` u een die gebruikmaakt van deze alternatieve syntaxis.

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

Deze alternatieve vorm van de `For` instructie werkt in Power shell-script bestanden en de Power shell-opdracht prompt. Het is echter gemakkelijker om de `For` syntaxis van de instructie te gebruiken met punt komma's wanneer u interactieve opdrachten invoert bij de opdracht prompt.

De `For` lus is flexibeler dan de `Foreach` lus, omdat u hiermee waarden in een matrix of verzameling kunt verhogen met behulp van patronen. In het volgende voor beeld `$i` wordt de variabele verhoogd met 2 in het **herhalings** gedeelte van de- `For` instructie.

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

De `For` lus kan ook op één regel worden geschreven, zoals in het volgende voor beeld.

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a>ZIE OOK

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Foreach](about_Foreach.md)
