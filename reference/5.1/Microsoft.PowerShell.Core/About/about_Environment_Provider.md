---
description: Omgeving
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Omgevings provider
ms.openlocfilehash: afa9f17333e09f31b130e24d9ede289f9621faf8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252809"
---
# <a name="environment-provider"></a>Omgevings provider

## <a name="provider-name"></a>Provider naam

Omgeving

## <a name="drives"></a>Aandrijfeenheden

`Env:`

## <a name="capabilities"></a>Functies

**ShouldProcess**

## <a name="short-description"></a>Korte beschrijving

Biedt toegang tot de Windows-omgevings variabelen.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met de Power shell- **omgevings** provider kunt u omgevings variabelen en-waarden in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.

**Omgevings** variabelen zijn dynamische variabelen met een naam die de omgeving beschrijven waarin uw Program ma's worden uitgevoerd. Windows en Power shell gebruiken omgevings variabelen om permanente gegevens op te slaan die van invloed zijn op de uitvoering van systemen en processen. In tegens telling tot Power shell-variabelen vallen omgevings variabelen geen bereik beperkingen op.

Het **omgevings** station is een platte naam ruimte met de omgevings variabelen die specifiek zijn voor de sessie van de huidige gebruiker. De omgevings variabelen hebben geen onderliggende items.

De **omgevings** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Wissen-item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>Typen die door deze provider worden weer gegeven

Elke omgevings variabele is een instantie van de klasse [System. Collections. Dictionary entry](/dotnet/api/system.collections.dictionaryentry) . De naam van de variabele is de woordenlijst sleutel. De waarde van de omgevings variabele is de waarde van de woorden lijst.

## <a name="navigating-the-environment-drive"></a>Navigeren door het omgevings station

De **omgevings** provider geeft de gegevens opslag in het `Env:` station. Als u met omgevings variabelen wilt werken, wijzigt u uw locatie in het `Env:` station ( `Set-Location Env:` ) of werkt u vanaf een ander Power Shell-station. Als u wilt verwijzen naar een omgevings variabele vanaf een andere locatie, gebruikt u de `Env:` naam van het station in het pad.

```powershell
Set-Location Env:
```

Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station. Typ bijvoorbeeld:

```powershell
Set-Location C:
```

U kunt ook met de **omgevings** provider werken vanuit elk ander Power Shell-station. Als u wilt verwijzen naar een omgevings variabele vanaf een andere locatie, gebruikt u de naam van het station `Env:` in het pad.

De **omgevings** provider stelt ook omgevings variabelen beschikbaar met behulp van een variabele prefix van `$env:` .  Met de volgende opdracht wordt de inhoud van de omgevings variabele **Program Files** weer gegeven. Het `$env:` variabele prefix kan vanuit elk Power Shell-station worden gebruikt.

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

U kunt ook de waarde van een omgevings variabele wijzigen met behulp van het `$env:` voor voegsel van de variabele.  Alle wijzigingen die zijn aangebracht, hebben alleen betrekking op de huidige Power shell-sessie zolang deze actief is.

> [!NOTE]
> In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken. Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location). en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-environment-variables"></a>Omgevings variabelen ophalen

Met deze opdracht worden alle omgevings variabelen in de huidige sessie weer gegeven.

```powershell
Get-Item -Path Env:
```

U kunt deze opdracht vanuit elk Power Shell-station gebruiken.

De omgevings provider heeft geen containers, dus de bovenstaande opdracht heeft hetzelfde effect als het gebruikt in combi natie met `Get-ChildItem` .

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a>Een geselecteerde omgevings variabele ophalen

Met deze opdracht wordt de `WINDIR` omgevings variabele opgehaald.

```powershell
Get-ChildItem -Path Env:windir
```

U kunt ook de notatie van het variabele voor voegsel gebruiken.

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a>Een omgevingsvariabele maken

Met deze opdracht maakt u de `USERMODE` omgevings variabele met de waarde ' niet-beheerder '. De `-Path` parameter waarde maakt het nieuwe item in het `Env:` station. De nieuwe omgevings variabele kan alleen worden gebruikt in de huidige Power shell-sessie zolang deze actief is.

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a>Een omgevings variabele wijzigen

### <a name="rename-an-environment-variable"></a>De naam van een omgevings variabele wijzigen

Met deze opdracht wordt de- `Rename-Item` cmdlet gebruikt om de naam van de `USERMODE` omgevings variabele die u hebt gemaakt, te wijzigen `USERROLE` . Wijzig niet de naam van een omgevings variabele die door het systeem wordt gebruikt. Hoewel deze wijzigingen alleen van invloed zijn op de huidige sessie, kunnen ze ervoor zorgen dat het systeem of een programma onjuist werkt.

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a>Een omgevings variabele wijzigen

Met deze opdracht wordt de- `Set-Item` cmdlet gebruikt om de waarde van de `USERROLE` omgevings variabele te wijzigen in ' Administrator '.

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a>Een omgevings variabele kopiëren

Met deze opdracht wordt de waarde van de `USERROLE` omgevings variabele gekopieerd naar de `USERROLE2` omgevings variabele.

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a>Een omgevings variabele verwijderen

Met deze opdracht wordt de `USERROLE2` omgevings variabele uit de huidige sessie verwijderd.

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a>Een omgevings variabele met Clear-Item verwijderen

Met deze opdracht wordt de `USERROLE` omgevings variabele verwijderd door de waarde ervan te wissen.

```powershell
Clear-Item -Path Env:USERROLE
```

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
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a>Zie ook

[about_Providers](../About/about_Providers.md)
