---
description: Register
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register provider
ms.openlocfilehash: a45513ca0ab4816793d52771ea1cfa56b239ecbf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252759"
---
# <a name="registry-provider"></a>Register provider

## <a name="provider-name"></a>Provider naam

Register

## <a name="drives"></a>Aandrijfeenheden

`HKLM:`, `HKCU:`

## <a name="capabilities"></a>Functies

**ShouldProcess** , **UseTransactions**

## <a name="short-description"></a>Korte beschrijving

Biedt toegang tot de register sleutels, vermeldingen en waarden in Power shell.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met de Power shell- **register** provider kunt u register sleutels, vermeldingen en waarden in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.

De **register** stations zijn een hiërarchische naam ruimte met de register sleutels en subsleutels op uw computer. Register vermeldingen en-waarden zijn geen onderdelen van die hiërarchie. In plaats daarvan zijn ze eigenschappen van elk van de sleutels.

De **register** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.

- [Get-locatie](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Item verplaatsen](xref:Microsoft.PowerShell.Management.Move-Item)
- [Nieuw-item](xref:Microsoft.PowerShell.Management.New-Item)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-item Property](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Verwijderen-item Property](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Wissen-item Property](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Get-ACL](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-ACL](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a>Typen die door deze provider worden weer gegeven

Register sleutels worden weer gegeven als exemplaren van de klasse [micro soft. Win32. RegistryKey](/dotnet/api/microsoft.win32.registrykey) . Register vermeldingen worden weer gegeven als exemplaren van de klasse [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) .

## <a name="navigating-the-registry-drives"></a>Navigeren door de register stations

De gegevens opslag van de **register** provider is beschikbaar als twee standaard stations. De register locatie HKEY_LOCAL_MACHINE wordt toegewezen aan het `HKLM:` station en HKEY_CURRENT_USER wordt toegewezen aan het `HKCU:` station. Als u wilt werken met het REGI ster, kunt u uw locatie wijzigen in het `HKLM:` station met behulp van de volgende opdracht.

```powershell
Set-Location HKLM:
```

Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station. Typ bijvoorbeeld:

```powershell
Set-Location C:
```

U kunt ook met de **register** provider werken vanuit elk ander Power Shell-station. Als u wilt verwijzen naar een register sleutel van een andere locatie, gebruikt u de naam van het station ( `HKLM:` , `HKCU:` ) in het pad. Gebruik een back slash ( \\ ) of een slash (/) om een niveau van het **register** station aan te geven.

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken. Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

Dit laatste voor beeld toont een andere pad-syntaxis die u kunt gebruiken om te navigeren door de **register** provider. Deze syntaxis maakt gebruik van de provider naam, gevolgd door twee dubbele punten `::` . Met deze syntaxis kunt u de volledige HIVE-naam gebruiken in plaats van de naam van het toegewezen station `HKLM` .

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a>De inhoud van register sleutels weer geven

Het REGI ster is onderverdeeld in sleutels, subsleutels en vermeldingen. Zie [structuur van het REGI ster](/windows/desktop/sysinfo/structure-of-the-registry)voor meer informatie over de Register structuur.

In een **register** station is elke sleutel een container. Een sleutel kan een wille keurig aantal sleutels bevatten. Een register sleutel met een bovenliggende sleutel wordt een subsleutel genoemd. U kunt gebruiken `Get-ChildItem` om register sleutels weer te geven en naar `Set-Location` een sleutelpad te navigeren.

Register waarden zijn kenmerken van een register sleutel. In het **register** station worden deze **item eigenschappen** genoemd. Een register sleutel kan zowel onderliggende sleutels als item eigenschappen hebben.

In dit voor beeld wordt het verschil tussen `Get-Item` en `Get-ChildItem` weer gegeven. Wanneer u `Get-Item` op de register sleutel ' spooler ' gebruikt, kunt u de eigenschappen ervan weer geven.

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

Elke register sleutel kan ook subsleutels hebben. Wanneer u `Get-Item` een register sleutel gebruikt, worden de subsleutels niet weer gegeven. `Get-ChildItem`Met de cmdlet worden de onderliggende items van de ' spooler-sleutel ' weer gegeven, inclusief de eigenschappen van elke subsleutel. De eigenschappen van de bovenliggende sleutels worden niet weer gegeven wanneer u gebruikt `Get-ChildItem` .

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

De `Get-Item` cmdlet kan ook worden gebruikt op de huidige locatie. In het volgende voor beeld wordt naar de register sleutel ' spooler ' genavigeerd en worden de item eigenschappen opgehaald.
De punt `.` wordt gebruikt om de huidige locatie aan te geven.

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden besproken.

-[Get-item](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem)

## <a name="viewing-registry-key-values"></a>Register sleutel waarden weer geven

Register sleutel waarden worden opgeslagen als eigenschappen van elke register sleutel. De `Get-ItemProperty` cmdlet bekijkt de register sleutel eigenschappen met de naam die u opgeeft. Het resultaat is een **PSCustomObject** die de door u opgegeven eigenschappen bevat.

In het volgende voor beeld wordt de `Get-ItemProperty` cmdlet gebruikt om alle eigenschappen weer te geven. Als u het resulterende object opslaat in een variabele, kunt u toegang krijgen tot de gewenste eigenschaps waarde.

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

Door een waarde voor de `-Name` para meter op te geven, selecteert u de eigenschappen die u opgeeft en retourneert de **PSCustomObject**.  In het volgende voor beeld wordt het verschil in uitvoer weer gegeven wanneer u de `-Name` para meter gebruikt.

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

Vanaf Power shell 5,0 retourneert de `Get-ItemPropertyValue` cmdlet alleen de waarde van de eigenschap die u opgeeft.

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.

- [Get-item Property](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Get-ItemPropertyValue](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a>Register sleutel waarden wijzigen

Met de `Set-ItemProperty` cmdlet worden kenmerken voor register sleutels ingesteld. In het volgende voor beeld wordt `Set-ItemProperty` het start type van de Spooler-service gewijzigd in hand matig. In het voor beeld wordt de **starttype** weer gewijzigd in *automatisch* met behulp van de `Set-Service` cmdlet.

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

Elke register sleutel heeft een *standaard* waarde. U kunt de *standaard* waarde voor een register sleutel wijzigen met ofwel `Set-Item` of `Set-ItemProperty` .

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.

- [Set-item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a>Register sleutels en-waarden maken

`New-Item`Met de cmdlet worden register sleutels gemaakt met een naam die u opgeeft.
U kunt ook de `mkdir` functie gebruiken, die de `New-Item` cmdlet intern aanroept.

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

U kunt de `New-ItemProperty` cmdlet gebruiken om waarden te maken in een register sleutel die u opgeeft. In het volgende voor beeld wordt een nieuwe DWORD-waarde gemaakt voor de register sleutel ContosoCompany.

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> Raadpleeg de sectie dynamische para meters in dit artikel voor andere toegestane type waarden.

Zie [New-item Property](xref:Microsoft.PowerShell.Management.New-ItemProperty)voor gedetailleerd gebruik van de cmdlet.

## <a name="copying-registry-keys-and-values"></a>Register sleutels en-waarden kopiëren

Gebruik in de **register** provider de- `Copy-Item` cmdlet om register sleutels en-waarden te kopiëren. Gebruik de `Copy-ItemProperty` cmdlet alleen om register waarden te kopiëren.
Met de volgende opdracht worden de register sleutel ' Contoso ' en de bijbehorende eigenschappen gekopieerd naar de opgegeven locatie ' HKLM: \ Software\Fabrikam '.

`Copy-Item` maakt de doel sleutel als deze niet bestaat. Als de doel sleutel bestaat, `Copy-Item` wordt er een duplicaat van de bron sleutel gemaakt als een onderliggend item (subsleutel) van de doel sleutel.

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

De volgende opdracht maakt gebruik `Copy-ItemProperty` van de-cmdlet om de waarde ' server ' van de sleutel ' Contoso ' naar de sleutel ' fabrikam ' te kopiëren.

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.

- [Kopie-item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Kopiëren-item Property](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a>Register sleutels en-waarden verplaatsen

De `Move-Item` `Move-ItemProperty` cmdlets en gedragen zich als hun "kopie"-equivalenten. Als het doel bestaat, `Move-Item` verplaatst de bron sleutel onder de doel sleutel. Als de doel sleutel niet bestaat, wordt de bron sleutel verplaatst naar het doelpad.

Met de volgende opdracht wordt de sleutel ' Contoso ' verplaatst naar het pad ' HKLM: \ SOFTWARE\Fabrikam '.

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

Met deze opdracht worden alle eigenschappen van ' HKLM: \ SOFTWARE\ContosoCompany ' naar ' HKLM: \ SOFTWARE\Fabrikam ' verplaatst.

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

Raadpleeg de volgende artikelen voor meer informatie over de cmdlets die in deze sectie worden gebruikt.

- [Item verplaatsen](xref:Microsoft.PowerShell.Management.Move-Item)
- [Verplaatsen-item Property](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a>De naam van register sleutels en-waarden wijzigen

U kunt de naam van register sleutels en-waarden wijzigen, net zoals u bestanden en mappen zou doen.
`Rename-Item` de naam van register sleutels wijzigen terwijl de naam van de `Rename-ItemProperty` register waarden wordt gewijzigd.

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a>Security descriptors wijzigen

U kunt de toegang tot register sleutels beperken met behulp van de- `Get-Acl` en- `Set-Acl` cmdlets. In het volgende voor beeld wordt een nieuwe gebruiker met volledig beheer toegevoegd aan de register sleutel HKLM: \ SOFTWARE\Contoso.

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

Raadpleeg de volgende artikelen voor meer voor beelden en Details over het gebruik van de cmdlet.

- [Get-ACL](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-ACL](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a>Register sleutels en-waarden verwijderen en wissen

U kunt opgenomen items verwijderen met behulp van **Remove-item** , maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat. In het volgende voor beeld wordt geprobeerd een sleutel ' HKLM: \ SOFTWARE\Contoso ' te verwijderen.

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Als u opgenomen items zonder vragen wilt verwijderen, geeft u de `-Recurse` para meter op.

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

Als u alle items in ' HKLM: \ SOFTWARE\Contoso ' wilt verwijderen, maar niet ' HKLM: \ SOFTWARE\Contoso ' zelf, gebruikt u een afsluitende back slash `\` gevolgd door een Joker teken.

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

Met deze opdracht wordt de register waarde ' ContosoTest ' verwijderd uit de register sleutel ' HKLM: \ SOFTWARE\Contoso '.

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

`Clear-Item` Hiermee wist u alle register waarden voor een sleutel. In het volgende voor beeld worden alle waarden uit de register sleutel HKLM: \ SOFTWARE\Contoso gewist. Als u alleen een bepaalde eigenschap wilt wissen, gebruikt u `Clear-ItemProperty` .

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

Raadpleeg de volgende artikelen voor meer voor beelden en Details over het gebruik van de cmdlet.

- [Wissen-item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Wissen-item Property](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Verwijderen-item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Verwijderen-item Property](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a>Dynamische parameters

Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.

### <a name="type-microsoftwin32registryvaluekind"></a>Typ <Microsoft. Win32. RegistryValueKind>

Hiermee wordt het gegevens type van een register waarde gemaakt of gewijzigd. De standaard waarde is `String` (REG_SZ).

Deze para meter werkt zoals ontworpen op de cmdlet [set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty) . Het is ook beschikbaar voor de cmdlet [set-item](xref:Microsoft.PowerShell.Management.Set-Item) in de register stations, maar heeft geen effect.

|Waarde | Beschrijving |
| ---- | ----------- |
| `String` | Hiermee geeft u een teken reeks met een null-waarde op. Gelijk aan REG_SZ. |
| `ExpandString` | Hiermee wordt een teken reeks met een null-waarde beëindigd die niet is uitgevouwen |
|                | verwijzingen naar omgevings variabelen die worden uitgebreid wanneer |
|                | de waarde wordt opgehaald. Gelijk aan REG_EXPAND_SZ. |
| `Binary` | Hiermee worden binaire gegevens in een formulier opgegeven. Gelijk aan REG_BINARY. |
| `DWord` | Hiermee geeft u een 32-bits binair getal op. Gelijk aan REG_DWORD. |
| `MultiString` | Hiermee geeft u een matrix van op null eindigende teken reeksen die zijn beëindigd door |
|               | twee null-tekens. Gelijk aan REG_MULTI_SZ. |
| `QWord` | Hiermee geeft u een 64-bits binair getal op. Gelijk aan REG_QWORD. |
| `Unknown` | Hiermee wordt een niet-ondersteund gegevens type van het REGI ster aangegeven, zoals |
|           | REG_RESOURCE_LIST. |

#### <a name="cmdlets-supported"></a>Ondersteunde cmdlets

- [Set-item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-item Property](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a>De pijp lijn gebruiken

Provider-cmdlets accepteren de invoer van de pijp lijn. U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden. Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.

## <a name="getting-help"></a>Ondersteuning vragen

Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.

Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u een `Get-Help` opdracht uit in een bestandssysteem station of gebruikt u de para meter **Path** om een bestandssysteem station op te geven.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a>Zie ook

 [about_Providers](../About/about_Providers.md)
