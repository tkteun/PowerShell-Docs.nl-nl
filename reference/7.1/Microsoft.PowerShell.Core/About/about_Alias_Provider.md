---
description: Alias
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Alias provider
ms.openlocfilehash: 8edd1a406862e6bf1dcbc5e8215b60c93ac7b13f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252668"
---
# <a name="alias-provider"></a>Alias provider

## <a name="provider-name"></a>Provider naam
Alias

## <a name="drives"></a>Aandrijfeenheden

`Alias:`

## <a name="capabilities"></a>Functies

**ShouldProcess**

## <a name="short-description"></a>Korte beschrijving

Geeft toegang tot de Power shell-aliassen en de waarden die ze vertegenwoordigen.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met de Power shell- **alias** provider kunt u aliassen ophalen, toevoegen, wijzigen, wissen en verwijderen in Power shell.

Een alias is een alternatieve naam voor een cmdlet, functie, uitvoerbaar bestand, met inbegrip van scripts. Power shell bevat een reeks ingebouwde aliassen. U kunt uw eigen aliassen toevoegen aan de huidige sessie en aan uw Power shell-profiel.

Het **alias** station is een platte naam ruimte die alleen de alias-objecten bevat.
De aliassen hebben geen onderliggende items.

De **alias** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Wissen-item](xref:Microsoft.PowerShell.Management.Clear-Item)

Power shell bevat een set cmdlets die zijn ontworpen om aliassen weer te geven en te wijzigen. Wanneer u **alias** -cmdlets gebruikt, hoeft u het `Alias:` station niet in de naam op te geven. Dit artikel is niet van belang voor het werken met **alias** -cmdlets.

- [Exporteren-alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Import-alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [Nieuwe alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Set-alias](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a>Typen die door deze provider worden weer gegeven

Elke alias is een instantie van de klasse [System. Management. Automation. AliasInfo](/dotnet/api/system.management.automation.aliasinfo) .

## <a name="navigating-the-alias-drive"></a>Navigeren door het alias station

De **alias** provider toont het gegevens archief van het `Alias:` station. Als u met aliassen wilt werken, kunt u uw locatie wijzigen in het `Alias:` station met behulp van de volgende opdracht:

```powershell
Set-Location Alias:
```

Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station. Typ bijvoorbeeld:

```powershell
Set-Location C:
```

U kunt ook met de alias provider werken vanuit elk ander Power Shell-station. Als u wilt verwijzen naar een alias vanuit een andere locatie, gebruikt u de `Alias:` naam van het station in het pad.

> [!NOTE]
> In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken. Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location). en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

### <a name="displaying-the-contents-of-the-alias-drive"></a>De inhoud van de alias wordt weer gegeven: station

Met deze opdracht wordt de lijst met alle aliassen opgehaald wanneer de huidige locatie het `Alias:` station is. Er wordt een Joker teken gebruikt `*` om alle inhoud van de huidige locatie aan te geven.

```powershell
PS Alias:\> Get-Item -Path *
```

In het `Alias:` station, een punt `.` , dat de huidige locatie vertegenwoordigt en een Joker teken `*` , waarmee alle items op de huidige locatie worden aangeduid, hebben hetzelfde effect. U kunt bijvoorbeeld `Get-Item -Path .` `Get-Item \*` hetzelfde resultaat opleveren.

De alias provider heeft geen containers, dus de bovenstaande opdracht heeft hetzelfde effect als het wordt gebruikt in combi natie met `Get-ChildItem` .

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a>Een geselecteerde alias ophalen

Met deze opdracht wordt de `ls` alias opgehaald.
Omdat deze het pad bevat, kunt u het gebruiken in een Power Shell-station.

```powershell
Get-Item -Path Alias:ls
```

Als u zich in het station bevindt `Alias:` , kunt u de naam van het station weglaten uit het pad.

U kunt ook de definitie voor een alias ophalen door het pad naar de provider te voorzien van het dollar teken ( `$` ).

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a>Alle aliassen voor een specifieke cmdlet ophalen

Met deze opdracht wordt een lijst opgehaald met de aliassen die zijn gekoppeld aan de `Get-ChildItem` cmdlet. De eigenschap **definitie** wordt gebruikt om de naam van de cmdlet op te slaan.

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a>Aliassen maken

### <a name="create-an-alias-from-the-alias-drive"></a>Een alias maken op basis van de alias: station

Met deze opdracht wordt de `serv` alias voor de `Get-Service` cmdlet gemaakt. Omdat de huidige locatie zich in het station bevindt `Alias:` , `-Path` is de para meter niet nodig.

Met deze opdracht wordt ook de `-Options` dynamische para meter gebruikt om de **AllScope** -optie in te stellen voor de alias. De `-Options` para meter is alleen beschikbaar in de `New-Item` cmdlet als u zich in het station bevindt `Alias:` . De punt ( `.` ) geeft de huidige map aan. Dit is het alias station.

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a>Een alias met een absoluut pad maken

U kunt een alias maken voor elk item dat een opdracht aanroept.
Met deze opdracht maakt u de `np` alias voor `Notepad.exe` .

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a>Een alias maken voor een nieuwe functie

U kunt voor elke functie een alias maken. U kunt deze functie gebruiken om een alias te maken die zowel een cmdlet als de bijbehorende para meters bevat.

Met de eerste opdracht wordt de `CD32` functie gemaakt, waarmee de huidige map wordt gewijzigd in de `System32` map. Met de tweede opdracht wordt de `go` alias voor de `CD32` functie gemaakt.

Wanneer de opdracht is voltooid, kunt u ofwel `CD32` of gebruiken `go` om de functie aan te roepen.

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a>Aliassen wijzigen

### <a name="change-the-options-of-an-alias"></a>De opties van een alias wijzigen

U kunt de `Set-Item` cmdlet met de `-Options` para meter Dynamic gebruiken om de waarde van de `-Options` eigenschap van een alias te wijzigen.

Met deze opdracht worden de opties **AllScope** en **ReadOnly** ingesteld voor de `dir` alias. De opdracht maakt gebruik `-Options` van de dynamische para meter van de `Set-Item` cmdlet. De `-Options` para meter is beschikbaar in `Set-Item` Wanneer u deze gebruikt met de **alias** of **functie** provider.

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a>Een alias waarnaar wordt verwezen, wijzigen

Met deze opdracht wordt de- `Set-Item` cmdlet gebruikt om de alias te wijzigen `gp` zodat deze de `Get-Process` cmdlet vertegenwoordigt in plaats van de `Get-ItemProperty` cmdlet.
De `-Force` para meter is vereist omdat de waarde van de eigenschap **Options** van de `gp` alias is ingesteld op `ReadOnly` . Omdat de opdracht vanuit het station wordt verzonden `Alias:` , is het station niet opgegeven in het pad.

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

De wijziging is van invloed op de vier eigenschappen die de koppeling tussen de alias en de opdracht definiëren. Als u het effect van de wijziging wilt weer geven, typt u de volgende opdracht:

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a>Naam wijzigen van een alias

Met deze opdracht wordt de- `Rename-Item` cmdlet gebruikt om de `popd` alias te wijzigen in `pop` .

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a>Een alias kopiëren

Met deze opdracht `pushd` wordt de alias gekopieerd zodat er een nieuwe `push` alias voor de `Push-Location` cmdlet wordt gemaakt.

Wanneer de nieuwe alias wordt gemaakt, heeft de eigenschap **Description** een null-waarde.
En de **optie** eigenschap heeft de waarde `None` . Als de opdracht wordt verleend vanuit het `Alias:` station, kunt u de naam van het station weglaten uit de waarde van de `-Path` para meter.

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a>Een alias verwijderen

Met deze opdracht wordt de `serv` alias van de huidige sessie verwijderd.
U kunt deze opdracht in elk Power Shell-station gebruiken.

```powershell
Remove-Item -Path Alias:serv
```

Met deze opdracht worden aliassen verwijderd die beginnen met s.
Er worden geen alleen-lezen-aliassen verwijderd.

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a>Alleen-lezen aliassen verwijderen

Met deze opdracht worden alle aliassen verwijderd uit de huidige sessie, met uitzonde ring van die met de `Constant` eigenschap **Options** van de waarde voor. `-Force`Met de para meter kan de opdracht aliassen verwijderen waarvan de eigenschap **Options** de waarde `ReadOnly` .

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a>Dynamische parameters

Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.

### <a name="options-systemmanagementautomationscopeditemoptions"></a>Opties [System. Management. Automation. ScopedItemOptions]

Bepaalt de waarde van de eigenschap **Options** van een alias.

- **Geen** : geen opties. Dit is de standaardwaarde.
- **Constante** : de alias kan niet worden verwijderd en de eigenschappen kunnen niet worden gewijzigd.
  **Constante** is alleen beschikbaar wanneer u een alias maakt. U kunt de optie van een bestaande alias niet wijzigen in een **constante**.
- **Privé** : de alias is alleen zichtbaar in het huidige bereik, niet in de onderliggende bereiken.
- **ReadOnly** : de eigenschappen van de alias kunnen niet worden gewijzigd, behalve door gebruik te maken van de `-Force` para meter. U kunt gebruiken `Remove-Item` om de alias te verwijderen.
- **AllScope** : de alias wordt gekopieerd naar een nieuwe scope die wordt gemaakt.

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Set-item](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a>De pijp lijn gebruiken

Provider-cmdlets accepteren de invoer van de pijp lijn. U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.
Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.

## <a name="getting-help"></a>Ondersteuning vragen

Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.

Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a>Zie ook

[about_Aliases](../About/about_Aliases.md)

[about_Providers](../About/about_Providers.md)

