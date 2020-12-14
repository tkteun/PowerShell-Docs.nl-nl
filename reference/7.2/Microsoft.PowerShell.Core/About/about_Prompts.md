---
description: Hierin wordt de `Prompt` functie beschreven en wordt gedemonstreerd hoe u een aangepaste `Prompt` functie maakt.
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 3887df636c3ad486a4dbe72fffdc8acd92d2b3e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705332"
---
# <a name="about-prompts"></a>Over prompts

## <a name="short-description"></a>Korte beschrijving
Hierin wordt de `Prompt` functie beschreven en wordt gedemonstreerd hoe u een aangepaste `Prompt` functie maakt.

## <a name="long-description"></a>Lange beschrijving

De Power shell-opdracht prompt geeft aan dat Power shell gereed is om een opdracht uit te voeren:

```
PS C:\>
```

De Power shell-prompt wordt bepaald door de ingebouwde `Prompt` functie. U kunt de prompt aanpassen door uw eigen functie te maken `Prompt` en deze op te slaan in uw Power shell-profiel.

## <a name="about-the-prompt-function"></a>Over de functie vragen

De `Prompt` functie bepaalt het uiterlijk van de Power shell-prompt.
Power shell wordt geleverd met een ingebouwde `Prompt` functie, maar u kunt deze vervangen door uw eigen functie te definiëren `Prompt` .

De `Prompt` functie heeft de volgende syntaxis:

```powershell
function Prompt { <function-body> }
```

De `Prompt` functie moet een object retour neren. Als best practice retourneert een teken reeks of een object dat is opgemaakt als een teken reeks. De maximale aanbevolen lengte is 80 tekens.

De volgende `Prompt` functie retourneert bijvoorbeeld een teken reeks ' Hallo, wereld ', gevolgd door een punt haak rechts ( `>` ).

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a>De functie voor vragen ophalen

Als u de `Prompt` functie wilt ophalen, gebruikt u de `Get-Command` cmdlet of gebruikt u de `Get-Item` cmdlet in het functie station.

Bijvoorbeeld:

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

Als u het script wilt ophalen waarmee de waarde van de prompt wordt ingesteld, gebruikt u de punt methode om de eigenschap **script Block** van de functie op te halen `Prompt` .

Bijvoorbeeld:

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

Net als alle functies `Prompt` wordt de functie in het `Function:` station opgeslagen.
Als u het script wilt weer geven waarmee de huidige functie wordt gemaakt `Prompt` , typt u:

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a>De standaard prompt

De standaard prompt wordt alleen weer gegeven als de `Prompt` functie een fout genereert of geen object retourneert.

De standaard Power shell-prompt is:

```
PS>
```

Met de volgende opdracht wordt bijvoorbeeld de `Prompt` functie ingesteld op `$null` , die ongeldig is. Als gevolg hiervan wordt de standaard prompt weer gegeven.

```powershell
PS C:\> function prompt {$null}
PS>
```

Omdat Power shell wordt geleverd met een ingebouwde prompt, wordt de standaard prompt doorgaans niet weer gegeven.

### <a name="built-in-prompt"></a>Ingebouwde prompt

Power shell bevat een ingebouwde `Prompt` functie.

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

De functie gebruikt de `Test-Path` cmdlet om te bepalen of de `$PSDebugContext` Automatische variabele is gevuld. Als deze `$PSDebugContext` is ingevuld, bevindt u zich in de foutopsporingsmodus en `[DBG]:` wordt u als volgt aan de prompt toegevoegd:

```Output
[DBG]: PS C:\ps-test>
```

Als `$PSDebugContext` niet is ingevuld, wordt de functie toegevoegd `PS` aan de prompt.
En de functie gebruikt de `Get-Location` cmdlet om de huidige locatie van de bestandssysteem Directory op te halen. Vervolgens wordt er een rechte haak () toegevoegd `>` .

Bijvoorbeeld:

```Output
PS C:\ps-test>
```

Als u zich in een geneste prompt bevindt, voegt de functie twee punt haken ( `>>` ) toe aan de prompt. (U bevindt zich in een geneste prompt als de waarde van de `$NestedPromptLevel` Automatische variabele groter is dan 1.)

Wanneer u bijvoorbeeld fouten opspoort in een geneste prompt, ziet u het volgende bericht:

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a>Wijzigingen in de prompt

De `Enter-PSSession` cmdlet voegt de naam van de externe computer toe aan de huidige `Prompt` functie. Wanneer u de `Enter-PSSession` cmdlet gebruikt om een sessie met een externe computer te starten, wordt de opdracht prompt gewijzigd in de naam van de externe computer. Bijvoorbeeld:

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

Andere Power shell-hosttoepassingen en alternatieve shells hebben mogelijk hun eigen opdracht prompts.

Zie about_Automatic_Variables voor meer informatie over de `$PSDebugContext` en `$NestedPromptLevel` automatische variabelen [](about_Automatic_Variables.md).

### <a name="how-to-customize-the-prompt"></a>De prompt aanpassen

Als u de prompt wilt aanpassen, schrijft u een nieuwe `Prompt` functie. De functie is niet beveiligd, dus u kunt deze overschrijven.

Als u een `Prompt` functie wilt schrijven, typt u het volgende:

```powershell
function prompt { }
```

Voer vervolgens tussen de accolades de opdrachten in of de teken reeks waarmee u wordt gevraagd.

De volgende prompt bevat bijvoorbeeld de naam van uw computer:

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

Op de Server01-computer ziet u het volgende bericht:

```Output
PS [Server01] >
```

De volgende `Prompt` functie bevat de huidige datum en tijd:

```powershell
function prompt {"$(Get-Date)> "}
```

De prompt ziet er ongeveer als volgt uit:

```Output
03/15/2012 17:49:47>
```

U kunt ook de standaard `Prompt` functie wijzigen:

De volgende gewijzigde `Prompt` functie voegt bijvoorbeeld `[ADMIN]:` toe aan de ingebouwde Power shell-prompt wanneer Power shell wordt geopend met de optie **als administrator uitvoeren** :

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

Wanneer u Power shell start met behulp van de optie **als administrator uitvoeren** , wordt een prompt weer gegeven die er ongeveer als volgt uitziet:

```Output
[ADMIN]: PS C:\ps-test>
```

Met de volgende `Prompt` functie wordt de geschiedenis-id van de volgende opdracht weer gegeven. Als u de opdracht geschiedenis wilt weer geven, gebruikt u de- `Get-History` cmdlet.

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

In de volgende prompt worden de- `Write-Host` en- `Get-Random` cmdlets gebruikt om een prompt te maken die wille keurige kleur wijzigt. Omdat `Write-Host` Er wordt geschreven naar de huidige hosttoepassing, maar geen object retourneert, bevat deze functie een `Return` instructie. Zonder IT maakt Power shell gebruik van de standaard prompt `PS>` .

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a>De functie vragen opslaan

Net als elke functie `Prompt` bestaat de functie alleen in de huidige sessie. Als u de `Prompt` functie voor toekomstige sessies wilt opslaan, voegt u deze toe aan uw Power shell-profielen. Zie [about_Profiles](about_Profiles.md)voor meer informatie over profielen.

## <a name="see-also"></a>Zie ook

[Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Get-geschiedenis](xref:Microsoft.PowerShell.Core.Get-History)

[Ophalen-wille keurig](xref:Microsoft.PowerShell.Utility.Get-Random)

[Write-host](xref:Microsoft.PowerShell.Utility.Write-Host)

[about_Profiles](about_Profiles.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Debuggers](about_Debuggers.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

