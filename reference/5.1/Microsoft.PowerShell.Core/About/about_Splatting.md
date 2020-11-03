---
description: Hierin wordt beschreven hoe u splatting gebruikt om para meters door te geven aan opdrachten in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: 0cf9702adcc7d19a19d9aaa9673fb42e3af715fa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252739"
---
# <a name="about-splatting"></a>Over splatting

## <a name="short-description"></a>Korte beschrijving

Hierin wordt beschreven hoe u splatting gebruikt om para meters door te geven aan opdrachten in Power shell.

## <a name="long-description"></a>Lange beschrijving

Splatting is een methode voor het door geven van een verzameling parameter waarden aan een opdracht als een eenheid. Power shell koppelt elke waarde in de verzameling met een opdracht parameter. Splatted parameter waarden worden opgeslagen in benoemde splatting-variabelen, die eruitzien als standaard variabelen, maar beginnen met een at `@` -symbool () in plaats van een dollar teken ( `$` ). Het at-symbool vertelt Power shell dat u een verzameling waarden, in plaats van één waarde, door gegeven.

Splatting maakt uw opdrachten korter en eenvoudiger te lezen. U kunt de splatting-waarden in verschillende opdracht aanroepen opnieuw gebruiken en splatting gebruiken om parameter waarden van de `$PSBoundParameters` Automatische variabele door te geven aan andere scripts en functies.

Vanaf Windows Power Shell 3,0 kunt u ook splatting gebruiken om alle para meters van een opdracht weer te geven.

## <a name="syntax"></a>Syntax

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

Gebruik de matrix syntaxis om parameter waarden op te geven voor positionele para meters, waarbij geen parameter namen zijn vereist. Als u parameter naam-en-waardeparen wilt opgeven, gebruikt u de syntaxis van de hash-tabel. De splatted-waarde kan ergens in de parameter lijst worden weer gegeven.

Wanneer splatting, hoeft u geen hash-tabel of matrix te gebruiken om alle para meters door te geven. U kunt bepaalde para meters door geven door splatting te gebruiken en anderen door te geven op positie of op parameter naam. U kunt ook meerdere objecten in één opdracht splat, zodat u niet meer dan één waarde voor elke para meter hoeft door te geven.

## <a name="splatting-with-hash-tables"></a>Splatting met hash-tabellen

Gebruik een hash-tabel om parameter naam-en-waardeparen te splat. U kunt deze indeling gebruiken voor alle parameter typen, waaronder positionele para meters en switch parameters.
Positionele para meters moeten worden toegewezen op naam.

In de volgende voor beelden `Copy-Item` worden twee opdrachten vergeleken waarmee het Test.txt-bestand wordt gekopieerd naar het Test2.txt-bestand in dezelfde map.

In het eerste voor beeld wordt gebruikgemaakt van de traditionele notatie waarin parameter namen worden opgenomen.

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

In het tweede voor beeld wordt gebruikgemaakt van hash-tabel splatting. Met de eerste opdracht maakt u een hash-tabel met de para meter-naam en parameter-waardeparen en slaat u deze op in de `$HashArguments` variabele. Met de tweede opdracht wordt de `$HashArguments` variabele gebruikt in een opdracht met splatting. Het symbool at ( `@HashArguments` ) vervangt het dollar teken ( `$HashArguments` ) in de opdracht.

Als u een waarde wilt opgeven voor de switch parameter **WhatIf** , gebruikt u `$True` of `$False` .

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> In de eerste opdracht geeft het at-symbool ( `@` ) een hash-tabel aan, geen splatted-waarde. De syntaxis voor hash-tabellen in Power shell is: `@{<name>=<value>; <name>=<value>; ...}`

## <a name="splatting-with-arrays"></a>Splatting met matrices

Gebruik een matrix om waarden te splat voor positionele para meters, waarvoor geen parameter namen zijn vereist. De waarden moeten op positie nummer in de matrix staan.

In de volgende voor beelden `Copy-Item` worden twee opdrachten vergeleken waarmee het Test.txt-bestand wordt gekopieerd naar het Test2.txt-bestand in dezelfde map.

In het eerste voor beeld wordt gebruikgemaakt van de traditionele notatie waarin parameter namen worden wegge laten. De parameter waarden worden weer gegeven in positie volgorde in de opdracht.

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

In het tweede voor beeld wordt gebruikgemaakt van matrix splatting. Met de eerste opdracht maakt u een matrix van de parameter waarden en slaat u deze op in de `$ArrayArguments` variabele. De waarden bevinden zich in positie volgorde in de matrix. Met de tweede opdracht wordt de `$ArrayArguments` variabele gebruikt in een opdracht in splatting. Het symbool at ( `@ArrayArguments` ) vervangt het dollar teken ( `$ArrayArguments` ) in de opdracht.

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a>De para meter argument list gebruiken

Verschillende cmdlets hebben een **argument List** -para meter die wordt gebruikt om parameter waarden door te geven aan een script blok dat door de cmdlet wordt uitgevoerd. De para meter **argument List** gebruikt een matrix van waarden die worden door gegeven aan het script blok. Power Shell maakt effectief gebruik van matrix splatting om de waarden te binden aan de para meters van het-script blok. Wanneer u **argument List** gebruikt en u een matrix wilt door geven als één object dat aan één para meter is gebonden, moet u de matrix als het enige element van een andere matrix laten teruglopen.

Het volgende voor beeld heeft een script blok dat één para meter gebruikt die een matrix met teken reeksen is.

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```

In dit voor beeld wordt alleen het eerste item in `$array` door gegeven aan het script blok.
```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList (,$array)
```

In dit voor beeld `$array` wordt verpakt in een matrix, zodat de gehele matrix als één object wordt door gegeven aan het script blok.

```Output
Hello World!
```

## <a name="examples"></a>Voorbeelden

In dit voor beeld ziet u hoe u splatted waarden in verschillende opdrachten opnieuw kunt gebruiken. Met de opdrachten in dit voor beeld wordt de `Write-Host` cmdlet gebruikt voor het schrijven van berichten naar de console van de host. Splatting wordt gebruikt om de voorgrond-en achtergrond kleuren op te geven.

Als u de kleuren van alle opdrachten wilt wijzigen, wijzigt u alleen de waarde van de `$Colors` variabele.

Met de eerste opdracht maakt u een hash-tabel met parameter namen en-waarden en slaat u de hash-tabel op in de `$Colors` variabele.

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

De tweede en derde opdracht gebruiken de `$Colors` variabele voor splatting in een `Write-Host` opdracht. Als u de wilt gebruiken `$Colors variable` , vervangt u het dollar teken ( `$Colors` ) door een at-symbool ( `@Colors` ).

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

In dit voor beeld ziet u hoe u de para meters kunt door sturen naar andere opdrachten met behulp van splatting en de `$PSBoundParameters` Automatische variabele.

De `$PSBoundParameters` Automatische variabele is een Dictionary-object (System. Collections. generic. Dictionary) met daarin alle parameter namen en-waarden die worden gebruikt wanneer een script of functie wordt uitgevoerd.

In het volgende voor beeld gebruiken we de `$PSBoundParameters` variabele voor het door sturen van de parameter waarden die zijn door gegeven aan een script of functie van `Test2` de functie naar de `Test1` functie. Beide aanroepen naar de `Test1` functie vanuit het `Test2` gebruik van splatting.

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

## <a name="splatting-command-parameters"></a>Splatting-opdracht parameters

U kunt splatting gebruiken om de para meters van een opdracht weer te geven. Deze techniek is handig wanneer u een proxy functie maakt, dat wil zeggen een functie die een andere opdracht aanroept. Deze functie is geïntroduceerd in Windows Power Shell 3,0.

Als u de para meters van een opdracht wilt splat, gebruikt `@Args` u om de opdracht parameters weer te geven. Deze techniek is eenvoudiger dan het inventariseren van opdracht parameters en werkt zonder revisie, zelfs niet als de para meters van de aangeroepen opdracht veranderen.

De functie maakt gebruik van de `$Args` Automatische variabele, die alle niet-toegewezen parameter waarden bevat.

Met de volgende functie wordt bijvoorbeeld de `Get-Process` cmdlet aangeroepen. In deze functie `@Args` vertegenwoordigt alle para meters van de `Get-Process` cmdlet.

```powershell
function Get-MyProcess { Get-Process @Args }
```

Wanneer u de `Get-MyProcess` functie gebruikt, worden alle niet-toegewezen para meters en parameter waarden door gegeven aan `@Args` , zoals wordt weer gegeven in de volgende opdrachten.

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

U kunt `@Args` in een functie gebruiken die expliciet para meters heeft gedeclareerd. U kunt dit meer dan eens gebruiken in een functie, maar alle para meters die u invoert, worden door gegeven aan alle exemplaren van `@Args` , zoals wordt weer gegeven in het volgende voor beeld.

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a>Opmerkingen

Als u een functie in een geavanceerde functie maakt met behulp van de kenmerken **CmdletBinding** of **para meter** , `$args` is de automatische variabele niet meer beschikbaar in de functie. Voor geavanceerde functies is expliciete parameter definitie vereist.

Power shell desired state Configuration (DSC) is niet ontworpen voor gebruik van splatting.
U kunt splatting niet gebruiken om waarden door te geven aan een DSC-resource. Zie Gael Colas ' article [pseudo-SPLATTING DSC resources (](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)Engelstalig) voor meer informatie.

## <a name="see-also"></a>Zie ook

[about_Arrays](about_Arrays.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Parameters](about_Parameters.md)
