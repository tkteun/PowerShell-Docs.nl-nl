---
description: Hierin worden de syntaxis diagrammen beschreven die worden gebruikt in Power shell.
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: 8182cc856de0813f0828400bcef7170a6e165c51
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705533"
---
# <a name="about-command-syntax"></a>Over opdracht syntaxis

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de syntaxis diagrammen beschreven die worden gebruikt in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

Met de cmdlets [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) en [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) worden syntaxis diagrammen weer gegeven om u te helpen opdrachten op de juiste manier te bouwen. In dit onderwerp wordt uitgelegd hoe u de syntaxis diagrammen kunt interpreteren.

## <a name="syntax-diagrams"></a>SYNTAXIS DIAGRAMMEN

Elke alinea in een opdracht syntaxis diagram vertegenwoordigt een geldige vorm van de opdracht.

Als u een opdracht wilt maken, volgt u het syntaxis diagram van links naar rechts. Selecteer een van de optionele para meters en geef waarden op voor de tijdelijke aanduidingen.

Power shell gebruikt de volgende notatie voor syntaxis diagrammen.

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

Hier volgt de syntaxis van de cmdlet [New-alias](xref:Microsoft.PowerShell.Utility.New-Alias) .

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

De syntaxis is in grote zin voor lees baarheid, maar Power shell is niet hoofdletter gevoelig.

Het syntaxis diagram bevat de volgende elementen.

## <a name="command-name"></a>Opdracht naam

Opdrachten beginnen altijd met een opdracht naam, zoals `New-Alias` . Typ de naam van de opdracht of de alias, bijvoorbeeld ' GCM ' voor `Get-Command` .

## <a name="parameters"></a>Parameters

De para meters van een opdracht zijn opties die bepalen wat de opdracht doet.
Sommige para meters hebben een ' waarde ' die gebruikers invoer heeft naar de opdracht.

De `Get-Help` opdracht heeft bijvoorbeeld een para meter **name** waarmee u de naam van het onderwerp kunt opgeven waarvoor Help wordt weer gegeven. De naam van het onderwerp is de waarde van de para meter **name** .

In een Power shell-opdracht beginnen parameter namen altijd met een koppel teken.
Het afbreek streepje vertelt Power shell dat het item in de opdracht een parameter naam is.

Als u bijvoorbeeld de para meter name van wilt gebruiken `New-Alias` , typt u het volgende:

```powershell
-Name
```

Para meters kunnen verplicht of optioneel zijn. In een syntaxis diagram bevinden optionele items zich tussen vier Kante haken `[ ]` .

Zie [about_Parameters](about_Parameters.md)voor meer informatie over para meters.

## <a name="parameter-values"></a>Parameterwaarden

Een parameter waarde is de invoer die door de para meter wordt gebruikt. Omdat Windows Power shell is gebaseerd op het Microsoft .NET Framework, worden parameter waarden weer gegeven in het syntaxis diagram op basis van hun .NET-type.

De para meter name van neemt bijvoorbeeld een `Get-Help` teken reeks waarde, een teken reeks, zoals een enkel woord of meerdere woorden tussen aanhalings tekens.

```powershell
[-Name] <string>
```

Het .NET-type van een parameter waarde bevindt zich tussen punt haken `< >` om aan te geven dat het een tijdelijke aanduiding voor een waarde is en niet een letterlijke teken reeks die u in een opdracht typt.

Als u de para meter wilt gebruiken, vervangt u de tijdelijke aanduiding .NET-type door een object dat het opgegeven .NET-type heeft.

Als u bijvoorbeeld de para meter **name** wilt gebruiken, typt u '-name ', gevolgd door een teken reeks, zoals in het volgende voor beeld:

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a>Para meters zonder waarden

Sommige para meters accepteren geen invoer, dus ze hebben geen parameter waarde.
Para meters zonder waarden worden "switch parameters" genoemd, omdat ze werken als aan/uit-switches. U neemt ze op (aan) of u kunt deze weglaten (uit) van een opdracht.

Als u een para meter switch wilt gebruiken, typt u de parameter naam, voorafgegaan door een koppel teken.

Als u bijvoorbeeld de para meter **WhatIf** van de cmdlet wilt gebruiken `New-Alias` , typt u het volgende:

```powershell
-WhatIf
```

## <a name="parameter-sets"></a>Parametersets

De para meters van een opdracht worden weer gegeven in de parameter sets. Parameter sets zien eruit als de alinea's van een syntaxis diagram.

De `New-Alias` cmdlet heeft één set para meters, maar veel cmdlets hebben meerdere parametersets. Sommige cmdlet-para meters zijn uniek voor een parameterset en andere worden weer gegeven in meerdere parameter sets. Elke parameterset vertegenwoordigt de indeling van een geldige opdracht. Een parameterset bevat alleen para meters die samen in een opdracht kunnen worden gebruikt. Als para meters niet kunnen worden gebruikt in dezelfde opdracht, worden ze weer gegeven in afzonderlijke parameter sets.

De [Get-wille](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet heeft bijvoorbeeld de volgende parameter sets:

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

De eerste parameterset, die een wille keurig getal retourneert, heeft de **minimum** -en **maximum** waarden. De tweede parameterset, die een wille keurig geselecteerd object uit een set objecten retourneert, omvat de para meters **input object** en **Count** . Beide parameter sets hebben de para meter **SetSeed** en de algemene para meters.

Deze parameter sets geven aan dat u de para meters **input object** en **Count** kunt gebruiken in dezelfde opdracht, maar u kunt de para meters voor **maximum** en **aantal** niet gebruiken in dezelfde opdracht.

U geeft aan welke para meter die u wilt gebruiken met behulp van de para meters in die para meter zijn ingesteld.

Voor elke cmdlet is echter ook een standaard parameterset ingesteld. De standaard parameterset wordt gebruikt wanneer u geen para meters opgeeft die uniek zijn voor een parameterset. Als u bijvoorbeeld `Get-Random` zonder para meters gebruikt, veronderstelt Windows Power shell dat u de para  meter set gebruikt en retourneert deze een wille keurig getal.

In elke parameterset worden de para meters in positie volgorde weer gegeven. De volg orde van de para meters in een opdracht is alleen van belang wanneer u de optionele parameter namen weglaat. Wanneer parameter namen worden wegge laten, wijst Power shell waarden toe aan para meters op positie en type. Zie voor meer informatie over de positie van de para meter `about_Parameters` .

## <a name="symbols-in-syntax-diagrams"></a>Symbolen in syntaxis diagrammen

Het syntaxis diagram bevat een lijst met de naam van de opdracht, de opdracht parameters en de parameter waarden. Er worden ook symbolen gebruikt om te laten zien hoe u een geldige opdracht kunt maken.

De syntaxis diagrammen gebruiken de volgende symbolen:

- Een koppel teken `-` geeft de naam van een para meter aan. Typ in een opdracht het afbreek streepje direct vóór de parameter naam zonder tussenliggende spaties, zoals wordt weer gegeven in het syntaxis diagram.

  Als u bijvoorbeeld de para meter **name** van wilt gebruiken `New-Alias` , typt u:

  ```powershell
  -Name
  ```

- Met punt haken wordt de `<>` tijdelijke aanduiding voor tekst aangeduid. U typt geen punt haken of de tekst van de tijdelijke aanduiding in een opdracht. In plaats daarvan vervangt u deze door het item dat hierin wordt beschreven.

  Punt haken worden gebruikt voor het identificeren van het .NET-type van de waarde die een para meter gebruikt. Als u bijvoorbeeld de para meter **name** van de cmdlet wilt gebruiken `New-Alias` , vervangt u de `<string>` door een teken reeks, een enkel woord of een groep woorden die tussen aanhalings tekens staan.

- Optionele items worden aangegeven door accolades `[ ]` . Een para meter en de waarde ervan kunnen optioneel zijn, of de naam van een vereiste para meter kan optioneel zijn.

  De para meter **Description** van `New-Alias` en de waarde ervan bevindt zich bijvoorbeeld tussen vier Kante haken, omdat deze beide optioneel zijn.

  ```powershell
  [-Description <string>]
  ```

  De haakjes geven ook aan dat de waarde van de para meter name `<string>` vereist is, maar de parameter naam ' naam ' is optioneel.

  ```powershell
  [-Name] <string>
  ```

- Een recht en haakje links `[]` toegevoegd aan een .net-type geeft aan dat de para meter een of meer waarden van dat type kan accepteren. Voer de waarden in een door komma's gescheiden lijst in.

  De para meter **name** van de `New-Alias` cmdlet gebruikt bijvoorbeeld slechts één teken reeks, maar de para meter **name** van [Get-process](xref:Microsoft.PowerShell.Management.Get-Process) kan een of meer teken reeksen aannemen.

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- Accolades `{}` geven een ' opsomming ' aan. Dit is een set geldige waarden voor een para meter.

  De waarden in de accolades worden gescheiden door verticale balken `|` . Deze balken geven een ' exclusieve of ' keuze aan, wat betekent dat u slechts één waarde kunt kiezen uit de set waarden die worden weer gegeven binnen de accolades.

  De syntaxis voor de `New-Alias` cmdlet bevat bijvoorbeeld de volgende waarde-inventarisatie voor de para meter **Option** :

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  De accolades en verticale balken geven aan dat u een van de vermelde waarden voor de para meter **Option** kunt kiezen, zoals "readonly" of "AllScope".

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a>Optionele items

Vier Kante haken `[]` rond optionele items. In de beschrijving van de `New-Alias` syntaxis van de cmdlet is de **bereik** parameter bijvoorbeeld optioneel. Dit wordt aangegeven in de syntaxis door de haken rond de naam van de para meter en het volgende type:

```powershell
[-Scope <string>]
```

In zowel de volgende voor beelden zijn het juiste gebruik van de `New-Alias` cmdlet:

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

Een parameter naam kan optioneel zijn, zelfs als de waarde voor die para meter is vereist. Dit wordt aangegeven in de syntaxis van de haken rond de parameter naam, maar niet van het parameter type, zoals in dit voor beeld van de `New-Alias` cmdlet:

```powershell
[-Name] <string> [-Value] <string>
```

Met de volgende opdrachten wordt de cmdlet op de juiste wijze gebruikt `New-Alias` . De opdrachten leveren hetzelfde resultaat op.

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

Als de parameter naam niet is opgenomen in de instructie als getypeerd, probeert Windows Power shell de positie van de argumenten te gebruiken om de waarden aan para meters toe te wijzen.

Het volgende voor beeld is niet voltooid:

```powershell
New-Alias utd
```

Voor deze cmdlet zijn waarden vereist voor de para meters **name** en **Value** .

In syntaxis voorbeelden worden haakjes ook gebruikt bij het benoemen en casten naar .NET Framework typen. In deze context duiden haakjes niet aan dat een element optioneel is.

## <a name="see-also"></a>ZIE OOK

- [about_Parameters](about_Parameters.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

