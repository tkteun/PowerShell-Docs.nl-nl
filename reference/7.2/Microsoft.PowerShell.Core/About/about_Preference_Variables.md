---
description: Variabelen waarmee het gedrag van Power shell wordt aangepast.
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: d8eadf88d486de4758b56738089f27e8adc3bc91
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705349"
---
# <a name="about-preference-variables"></a>Over voorkeurs variabelen

## <a name="short-description"></a>Korte beschrijving

Variabelen waarmee het gedrag van Power shell wordt aangepast.

## <a name="long-description"></a>Lange beschrijving

Power shell bevat een set variabelen waarmee u het gedrag ervan kunt aanpassen. Deze voorkeurs variabelen werken zoals de opties in op GUI gebaseerde systemen.

De voorkeurs variabelen zijn van invloed op de Power shell-besturings omgeving en alle opdrachten die in de omgeving worden uitgevoerd. In veel gevallen hebben de-cmdlets para meters die u kunt gebruiken om het voorkeurs gedrag voor een specifieke opdracht te onderdrukken.

De volgende tabel bevat de voorkeurs variabelen en hun standaard waarden.

|             Variabele             |       Standaardwaarde       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | Hoog                      |
| `$DebugPreference`               | SilentlyContinue          |
| `$ErrorActionPreference`         | Doorgaan                  |
| `$ErrorView`                     | ConciseView               |
| `$FormatEnumerationLimit`        | 4                         |
| `$InformationPreference`         | SilentlyContinue          |
| `$LogCommandHealthEvent`         | ONWAAR (niet geregistreerd)        |
| `$LogCommandLifecycleEvent`      | ONWAAR (niet geregistreerd)        |
| `$LogEngineHealthEvent`          | Waar (geregistreerd)             |
| `$LogEngineLifecycleEvent`       | Waar (geregistreerd)             |
| `$LogProviderLifecycleEvent`     | Waar (geregistreerd)             |
| `$LogProviderHealthEvent`        | Waar (geregistreerd)             |
| `$MaximumHistoryCount`           | 4096                      |
| `$OFS`                           | (Spatie teken ( `" "` )) |
| `$OutputEncoding`                | UTF8Encoding-object       |
| `$ProgressPreference`            | Doorgaan                  |
| `$PSDefaultParameterValues`      | (Geen-lege hash-tabel) |
| `$PSEmailServer`                 | (Geen)                    |
| `$PSModuleAutoLoadingPreference` | Alles                       |
| `$PSSessionApplicationName`      | wsman                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | Zie [$PSSessionOption](#pssessionoption) |
| `$Transcript`                    | (geen)                    |
| `$VerbosePreference`             | SilentlyContinue          |
| `$WarningPreference`             | Doorgaan                  |
| `$WhatIfPreference`              | Niet waar                     |

Power shell bevat de volgende omgevings variabelen waarmee gebruikers voorkeuren worden opgeslagen. Zie [about_Environment_Variables](about_Environment_Variables.md)voor meer informatie over deze omgevings variabelen.

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> Wijzigingen in de voorkeurs variabele worden alleen doorgevoerd in scripts en functies als deze scripts of functies in hetzelfde bereik zijn gedefinieerd als het bereik waarin de voor keur is gebruikt. Zie [about_Scopes](about_Scopes.md)voor meer informatie.

## <a name="working-with-preference-variables"></a>Werken met voorkeurs variabelen

In dit document worden alle voorkeurs variabelen beschreven.

Als u de huidige waarde van een specifieke voorkeurs variabele wilt weer geven, typt u de naam van de variabele. Met de volgende opdracht wordt bijvoorbeeld de `$ConfirmPreference` waarde van de variabele weer gegeven.

```powershell
 $ConfirmPreference
```

```Output
High
```

Gebruik een toewijzings instructie om de waarde van een variabele te wijzigen. De volgende instructie wijzigt bijvoorbeeld de `$ConfirmPreference` waarde van de para meter in **gemiddeld**.

```powershell
$ConfirmPreference = "Medium"
```

De waarden die u instelt, zijn specifiek voor de huidige Power shell-sessie. Als u variabelen effectief wilt maken in alle Power shell-sessies, voegt u deze toe aan uw Power shell-profiel. Zie [about_Profiles](about_Profiles.md)voor meer informatie.

## <a name="working-remotely"></a>Op afstand werken

Wanneer u opdrachten uitvoert op een externe computer, worden de externe opdrachten alleen onderhevig aan de voor keuren die zijn ingesteld in de Power shell-client van de externe computer. Wanneer u bijvoorbeeld een externe opdracht uitvoert, bepaalt de waarde van de variabele van de externe computer `$DebugPreference` hoe Power shell reageert op fout opsporing van berichten.

Zie [about_Remote](about_Remote.md)voor meer informatie over externe opdrachten.

### <a name="confirmpreference"></a>\$ConfirmPreference

Hiermee wordt bepaald of Power shell automatisch om bevestiging wordt gevraagd voordat een cmdlet of functie wordt uitgevoerd.

De `$ConfirmPreference` geldige waarden voor de variabele zijn **hoog**, **gemiddeld** of **laag**. Cmdlets en functions krijgen een risico van **hoog**, **gemiddeld** of **laag**. Wanneer de waarde van de `$ConfirmPreference` variabele kleiner is dan of gelijk is aan het risico dat is toegewezen aan een cmdlet of functie, wordt u door Power shell automatisch gevraagd om bevestiging voordat de cmdlet of functie wordt uitgevoerd.

Als de waarde van de `$ConfirmPreference` variabele **geen** is, wordt u door Power Shell nooit automatisch gevraagd voordat een cmdlet of functie wordt uitgevoerd.

Als u het bevestigings gedrag voor alle cmdlets en functies in de sessie wilt wijzigen, wijzigt u de `$ConfirmPreference` waarde van de variabele.

Als u de `$ConfirmPreference` voor één opdracht wilt overschrijven, gebruikt u de para meter **confirm** van de cmdlet of functie. Als u een bevestiging wilt aanvragen, gebruikt u `-Confirm` . Gebruik om de bevestiging te onderdrukken `-Confirm:$false` .

Geldige waarden voor `$ConfirmPreference` :

- **Geen**: er wordt niet automatisch om Power shell gevraagd. Als u een bevestiging van een bepaalde opdracht wilt aanvragen, gebruikt u de para meter **confirm** van de cmdlet of functie.
- **Laag**: Power shell vraagt om bevestiging voordat cmdlets of functies met een laag, gemiddeld of hoog risico worden uitgevoerd.
- **Gemiddeld**: Power shell vraagt om bevestiging voordat cmdlets of functies met een gemiddeld of hoog risico worden uitgevoerd.
- **Hoog**: Power shell vraagt om bevestiging voordat cmdlets of functions met een hoog risico worden uitgevoerd.

#### <a name="detailed-explanation"></a>Gedetailleerde uitleg

Power shell kan u automatisch om bevestiging vragen voordat een actie wordt uitgevoerd. Als cmdlet of function bijvoorbeeld aanzienlijk van invloed is op het systeem om gegevens te verwijderen of een aanzienlijke hoeveelheid systeem bronnen te gebruiken.

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

De schatting van het risico is een kenmerk van de cmdlet of functie die de **ConfirmImpact** heet. Gebruikers kunnen dit niet wijzigen.

Cmdlets en functies die mogelijk een risico vormen voor het systeem, hebben een **bevestigings** parameter die u kunt gebruiken om de bevestiging van één opdracht aan te vragen of te onderdrukken.

Omdat de meeste cmdlets en functies gebruikmaken van de standaard risico waarde, **ConfirmImpact**, van **medium** en de standaard waarde van `$ConfirmPreference` is **hoog**, wordt er zelden een automatische bevestiging weer gegeven. U kunt de automatische bevestiging echter activeren door de waarde te wijzigen van `$ConfirmPreference` op **gemiddeld** of **laag**.

#### <a name="examples"></a>Voorbeelden

In dit voor beeld ziet u het effect van de `$ConfirmPreference` standaard waarde van de variabele, **hoog**. Met de **hoge** waarde worden alleen cmdlets en functies met een hoog risico bevestigd. Aangezien de meeste cmdlets en functies gemiddeld risico lopen, worden ze niet automatisch bevestigd en wordt `Remove-Item` het bestand verwijderd. `-Confirm`Als u toevoegt aan de opdracht, wordt de gebruiker gevraagd om bevestiging.

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

Gebruiken `-Confirm` om een bevestiging aan te vragen.

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

In het volgende voor beeld ziet u het effect van het wijzigen van de waarde van `$ConfirmPreference` op **gemiddeld**. Omdat de meeste cmdlets en functies gemiddeld risico lopen, worden ze automatisch bevestigd. Als u de bevestigings prompt voor één opdracht wilt onderdrukken, gebruikt u de para meter **confirm** met de waarde `$false` .

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a>\$DebugPreference

Bepaalt hoe Power shell reageert op fout opsporing van berichten die zijn gegenereerd door een script, cmdlet of provider, of door een `Write-Debug` opdracht op de opdracht regel.

Sommige cmdlets tonen fout opsporingsgegevens, meestal technische berichten die zijn bedoeld voor programmeurs en technische ondersteunings medewerkers. Standaard worden fout opsporings berichten niet weer gegeven, maar u kunt fout opsporingsgegevens weer geven door de waarde van te wijzigen `$DebugPreference` .

U kunt de para meter common **debug** van een cmdlet gebruiken om de fout opsporingsgegevens voor een specifieke opdracht weer te geven of te verbergen. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.

De geldige waarden zijn als volgt:

- **Stop**: geeft het debug-bericht weer en stopt de uitvoering. Hiermee schrijft u een fout naar de-console.
- **Query**: Hiermee wordt het fout bericht over fouten weer gegeven en wordt u gevraagd of u wilt door gaan. Het toevoegen van de para meter common **debug** voor een opdracht, als de opdracht is geconfigureerd voor het genereren van een fout opsporingsgegevens, wijzigt u de waarde van de `$DebugPreference` variabele om op te **vragen**.
- **Door gaan**: Hiermee geeft u het fout bericht bij de uitvoering weer en gaat u verder met uitvoeren.
- **SilentlyContinue**: (standaard) geen effect. Het bericht fout opsporing wordt niet weer gegeven en de uitvoering wordt zonder onderbreking voortgezet.

#### <a name="examples"></a>Voorbeelden

In de volgende voor beelden ziet u het effect van het wijzigen van de waarden van `$DebugPreference` Wanneer een `Write-Debug` opdracht wordt ingevoerd op de opdracht regel.
De wijziging is van invloed op alle fout opsporingsgegevens, met inbegrip van berichten die worden gegenereerd door cmdlets en scripts. In de voor beelden wordt de para meter **debug** weer gegeven, waarin de fout opsporingsgegevens die betrekking hebben op één opdracht, worden weer geven of verborgen.

In dit voor beeld ziet u het effect van de `$DebugPreference` standaard waarde van de variabele **SilentlyContinue**. Standaard wordt het `Write-Debug` debug-bericht van de cmdlet niet weer gegeven en wordt de verwerking voortgezet. Wanneer de **debug** -para meter wordt gebruikt, wordt de voor keur voor één opdracht overschreven. Het bericht fout opsporing wordt weer gegeven.

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

In dit voor beeld ziet u het effect van `$DebugPreference` met de waarde **continue** . Het bericht fout opsporing wordt weer gegeven en de opdracht blijft verwerken.

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

In dit voor beeld wordt de para meter **debug** gebruikt met de waarde `$false` om het bericht voor één opdracht te onderdrukken. Het bericht fout opsporing wordt niet weer gegeven.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

Dit voor beeld laat zien hoe het effect is van `$DebugPreference` het instellen op de waarde **Stop** . Het bericht fout opsporing wordt weer gegeven en de opdracht is gestopt.

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

In dit voor beeld wordt de para meter **debug** gebruikt met de waarde `$false` om het bericht voor één opdracht te onderdrukken. Het bericht fout opsporing wordt niet weer gegeven en de verwerking is niet gestopt.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

Dit voor beeld laat zien hoe het effect is van `$DebugPreference` het instellen op de **query** waarde. Het bericht fout opsporing wordt weer gegeven en de gebruiker wordt om bevestiging gevraagd.

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

In dit voor beeld wordt de para meter **debug** gebruikt met de waarde `$false` om het bericht voor één opdracht te onderdrukken. Het bericht fout opsporing wordt niet weer gegeven en de verwerking wordt voortgezet.

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a>\$ErrorActionPreference

Bepaalt hoe Power shell reageert op een niet-afsluit fout, een fout die de verwerking van de cmdlet niet stopt. Bijvoorbeeld op de opdracht regel of in een script, cmdlet of provider, zoals de fouten die zijn gegenereerd door de `Write-Error` cmdlet.

U kunt de gemeen schappelijke para meter **Error Action** van de cmdlet gebruiken om de voor keur voor een specifieke opdracht te onderdrukken.

De geldige waarden zijn als volgt:

- **Onderbreken** : Voer het fout opsporingsprogramma in als er een fout optreedt of wanneer er een uitzonde ring wordt gegenereerd.
- **Door gaan**: (standaard) Hiermee wordt het fout bericht weer gegeven en wordt de uitvoering voortgezet.
- **Negeren**: onderdrukt het fout bericht en gaat verder met het uitvoeren van de opdracht. De waarde voor **negeren** is bedoeld voor gebruik per opdracht, niet voor gebruik als opgeslagen voor keur. **Ignore** is geen geldige waarde voor de `$ErrorActionPreference` variabele.
- **Query**: Hiermee wordt het fout bericht weer gegeven en wordt u gevraagd of u wilt door gaan.
- **SilentlyContinue**: geen effect. Het fout bericht wordt niet weer gegeven en de uitvoering wordt zonder onderbreking voortgezet.
- **Stop**: geeft het fout bericht weer en stopt de uitvoering. Naast de fout die wordt gegenereerd, genereert de **Stop** waarde een ActionPreferenceStopException-object in de fout stroom.
  gegevensstroom
- **Suspend**: Hiermee wordt een werk stroom taak automatisch opgeschort zodat deze verder kan worden onderzocht. Na onderzoek kan de werk stroom worden hervat. De **suspend** -waarde is bedoeld voor gebruik per opdracht en niet voor gebruik als opgeslagen voor keur. **Suspend** is geen geldige waarde voor de `$ErrorActionPreference` variabele.

`$ErrorActionPreference` en de para meter **Error Action** hebben geen invloed op de manier waarop Power shell reageert op beëindigings fouten die de verwerking van de cmdlet stoppen. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over de algemene para meter **Error Action** .

#### <a name="examples"></a>Voorbeelden

In deze voor beelden ziet u het effect van de verschillende waarden van de `$ErrorActionPreference` variabele. De para meter **Error Action** wordt gebruikt om de `$ErrorActionPreference` waarde te overschrijven.

In dit voor beeld wordt de `$ErrorActionPreference` standaard waarde weer gegeven, **door gaan**. Er wordt een niet-afsluit fout gegenereerd. Het bericht wordt weer gegeven en de verwerking wordt voortgezet.

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error: Test Error
Hello World
```

In dit voor beeld ziet u de `$ErrorActionPreference` standaard waarde, **query's**. Er wordt een fout gegenereerd en er wordt een prompt voor de actie weer gegeven.

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

In dit voor beeld wordt de `$ErrorActionPreference` ingesteld op **SilentlyContinue**.
Het fout bericht wordt onderdrukt.

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

In dit voor beeld ziet `$ErrorActionPreference` u de set die moet worden **gestopt**. Ook wordt het extra object weer gegeven dat is gegenereerd voor de `$Error` variabele.

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error: Test Error

ErrorRecord                 : Test Error
WasThrownFromThrowStatement : False
TargetSite                  : System.Collections.ObjectModel.Collection`1[System.Management.Automation.PSObject]
                              Invoke(System.Collections.IEnumerable)
StackTrace                  :    at System.Management.Automation.Runspaces.PipelineBase.Invoke(IEnumerable input)
                                 at Microsoft.PowerShell.Executor.ExecuteCommandHelper(Pipeline tempPipeline,
                              Exception& exceptionThrown, ExecutionOptions options)
Message                     : The running command stopped because the preference variable "ErrorActionPreference" or
                              common parameter is set to Stop: Test Error
Data                        : {System.Management.Automation.Interpreter.InterpretedFrameInfo}
InnerException              :
HelpLink                    :
Source                      : System.Management.Automation
HResult                     : -2146233087

Write-Error: Test Error
```

### <a name="errorview"></a>\$ErrorView

Bepaalt de weergave notatie van fout berichten in Power shell.

De geldige waarden zijn als volgt:

- **ConciseView**: (standaard) biedt een beknopt fout bericht en een refactorische weer gave voor geavanceerde module bouwers. Als de fout wordt weer gegeven vanaf de opdracht regel, is er een fout bericht met één regel. Anders wordt er een fout bericht over meerdere regels weer gegeven met de fout en een verwijzing naar de fout die aangeeft waar deze zich op die regel voordoet. Als de Terminal virtuele terminal ondersteunt, worden ANSI-kleur codes gebruikt om kleur accenten te bieden. De accent kleur kan worden gewijzigd op `$Host.PrivateData.ErrorAccentColor` . Gebruik `Get-Error` cmdlet voor een uitgebreide gedetailleerde weer gave van de volledig gekwalificeerde fout, inclusief interne uitzonde ringen.

  **ConciseView** is toegevoegd aan Power shell 7.

- **NormalView**: een gedetailleerde weer gave die is ontworpen voor de meeste gebruikers. Bevat een beschrijving van de fout en de naam van het object dat bij de fout betrokken is.

- **CategoryView**: een beknopte, gestructureerde weer gave die is ontworpen voor productie omgevingen. De indeling is als volgt:

  {Category}: ({TargetName}: {target type}): [{Activity}], {Reason}

Zie [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) -klasse voor meer informatie over de velden in **CategoryView**.

#### <a name="examples"></a>Voorbeelden

In dit voor beeld ziet u hoe een fout wordt weer gegeven wanneer de waarde `$ErrorView` is ingesteld op de standaard **ConciseView**. `Get-ChildItem` wordt gebruikt om een niet-bestaande map te zoeken.

```powershell
Get-ChildItem -path 'C:\NoRealDirectory'
```

```Output
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.
```

In dit voor beeld ziet u hoe een fout wordt weer gegeven wanneer de waarde `$ErrorView` is ingesteld op de standaard **ConciseView**. `Script.ps1` wordt uitgevoerd en genereert een fout van de `Get-Item` instructie.

```powershell
./Script.ps1
```

```Output
Get-Item: C:\Script.ps1
Line |
  11 | Get-Item -Path .\stuff
     | ^ Cannot find path 'C:\demo\stuff' because it does not exist.
```

In dit voor beeld ziet u hoe een fout wordt weer gegeven wanneer de waarde van `$ErrorView` wordt gewijzigd in **NormalView**. `Get-ChildItem` wordt gebruikt om een niet-bestaand bestand te zoeken.

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

In dit voor beeld ziet u hoe dezelfde fout optreedt wanneer de waarde van `$ErrorView` wordt gewijzigd in **CategoryView**.

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

In dit voor beeld wordt gedemonstreerd dat de waarde van `$ErrorView` alleen invloed heeft op de fout weergave. De structuur van het fout object dat is opgeslagen in de automatische variabele wordt niet gewijzigd `$Error` . Zie about_automatic_variables voor meer informatie over de `$Error` automatische [](about_Automatic_Variables.md)variabele.

Met de volgende opdracht wordt het **ErrorRecord** -object dat is gekoppeld aan de meest recente fout in de fout matrix, **element 0**, gebruikt en worden alle eigenschappen van het object Error in een lijst opgemaakt.

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a>\$FormatEnumerationLimit

Hiermee wordt bepaald hoeveel opgesomde items in een weer gave worden opgenomen. Deze variabele heeft geen invloed op de onderliggende objecten, alleen de weer gave. Wanneer de waarde van `$FormatEnumerationLimit` kleiner is dan het aantal opgesomde items, voegt Power shell een weglatings teken ( `...` ) toe om items aan te geven die niet worden weer gegeven.

**Geldige waarden**: integers ( `Int32` )

**Standaard waarde**: 4

#### <a name="examples"></a>Voorbeelden

In dit voor beeld ziet u hoe u de `$FormatEnumerationLimit` variabele gebruikt om de weer gave van opgesomde items te verbeteren.

Met de opdracht in dit voor beeld wordt een tabel gegenereerd met een lijst met alle services die worden uitgevoerd op de computer in twee groepen: één voor het **uitvoeren** van services en één voor **gestopt** Services. Er wordt een `Get-Service` opdracht gebruikt om alle services op te halen en vervolgens worden de resultaten via de pijp lijn naar de `Group-Object` cmdlet verzonden, waarmee de resultaten worden gegroepeerd op basis van de status van de service.

Het resultaat is een tabel met een lijst met de status in de kolom **naam** en de processen in de kolom **groep** . Als u de kolomlabels wilt wijzigen, gebruikt u een hash-tabel, Zie [about_Hash_Tables](about_Hash_Tables.md). Zie de voor beelden in de [indelings tabel](xref:Microsoft.PowerShell.Utility.Format-Table)voor meer informatie.

Zoek de huidige waarde van `$FormatEnumerationLimit` .

```powershell
$FormatEnumerationLimit
```

```Output
4
```

Alle services gegroepeerd op **status** weer geven. Er zijn Maxi maal vier services die worden vermeld in de kolom **groep** voor elke status, omdat de `$FormatEnumerationLimit` waarde **4** heeft.

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

Verhoog het aantal items in de lijst door de waarde te verhogen `$FormatEnumerationLimit` van **1000**. Gebruik `Get-Service` en `Group-Object` om de services weer te geven.

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

Gebruik `Format-Table` met de para meter **wrap** om de lijst met services weer te geven.

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a>\$InformationPreference

Met de `$InformationPreference` variabele kunt u voor keuren voor de informatie stroom instellen die u wilt weer geven voor gebruikers. Met name informatie berichten die u hebt toegevoegd aan opdrachten of scripts door de cmdlet [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) toe te voegen. Als de para meter **Information Action** wordt gebruikt, overschrijft de waarde de waarde van de `$InformationPreference` variabele. `Write-Information` is geïntroduceerd in Power shell 5,0.

De geldige waarden zijn als volgt:

- **Stoppen**: Hiermee stopt u een opdracht of script bij een exemplaar van de `Write-Information` opdracht.
- **Query**: geeft het informatieve bericht weer dat u in een opdracht opgeeft `Write-Information` . vervolgens wordt u gevraagd of u wilt door gaan.
- **Door gaan**: geeft het informatieve bericht weer en blijft actief.
- **Suspend** is alleen beschikbaar voor werk stromen die niet worden ondersteund in Power shell 6 en hoger.
- **SilentlyContinue**: (standaard) geen effect. De informatieve berichten worden niet weer gegeven en het script wordt zonder onderbreking voortgezet.

### <a name="logevent"></a>\$Logboek * gebeurtenis

Het **logboek * gebeurtenis** voorkeurs variabelen bepalen welke typen gebeurtenissen worden geschreven naar het Power shell-gebeurtenis logboek in Logboeken. Standaard worden alleen engine-en provider gebeurtenissen vastgelegd. Maar u kunt het logboek *** gebeurtenis** voorkeurs variabelen gebruiken om uw logboek aan te passen, zoals logboek gebeurtenissen over opdrachten.

Het **logboek * gebeurtenis** voorkeurs variabelen zijn als volgt:

- `$LogCommandHealthEvent`: Registreert fouten en uitzonde ringen in de opdracht initialisatie en-verwerking. De standaard instelling is `$false` (niet geregistreerd).
- `$LogCommandLifecycleEvent`: Registreert het starten en stoppen van opdrachten en opdracht pijplijnen en beveiligings uitzonderingen in opdracht detectie. De standaard instelling is `$false` (niet geregistreerd).
- `$LogEngineHealthEvent`: Registreert fouten en fouten van sessies. De standaard instelling is `$true` (geregistreerd).
- `$LogEngineLifecycleEvent`: Hiermee wordt het openen en sluiten van sessies geregistreerd. De standaard instelling is `$true` (geregistreerd).
- `$LogProviderHealthEvent`: Registreert provider fouten, zoals lees-en schrijf fouten, zoek fouten en aanroep fouten. De standaard instelling is `$true` (geregistreerd).
- `$LogProviderLifecycleEvent`: Logboeken voor het toevoegen en verwijderen van Power shell-providers. De standaard instelling is `$true` (geregistreerd). Zie [about_Providers](about_Providers.md)voor meer informatie over Power shell-providers.

Als u een **logboek * gebeurtenis** wilt inschakelen, typt u de variabele met een waarde van `$true` , bijvoorbeeld:

```powershell
$LogCommandLifeCycleEvent = $true
```

Als u een gebeurtenis type wilt uitschakelen, typt u de variabele met een waarde van `$false` , bijvoorbeeld:

```powershell
$LogCommandLifeCycleEvent = $false
```

De gebeurtenissen die u inschakelt, zijn alleen geldig voor de huidige Power shell-console. Sla de instellingen van de variabele op in uw Power shell-profiel om de configuratie toe te passen op alle-consoles. Zie [about_Profiles](about_Profiles.md)voor meer informatie.

### <a name="maximumhistorycount"></a>\$MaximumHistoryCount

Hiermee wordt bepaald hoeveel opdrachten worden opgeslagen in de opdracht geschiedenis van de huidige sessie.

**Geldige waarden**: 1-32768 ( `Int32` )

**Standaard**: 4096

Om het aantal opdrachten te bepalen dat op het moment van de opdracht geschiedenis is opgeslagen, typt u:

```powershell
(Get-History).Count
```

Voor een overzicht van de opdrachten die zijn opgeslagen in de sessie geschiedenis, gebruikt u de `Get-History` cmdlet. Zie [about_History](about_History.md)voor meer informatie.

### <a name="ofs"></a>\$OFS

Het OFS (output field separator) geeft het teken aan waarmee de elementen van een matrix worden gescheiden die naar een teken reeks worden geconverteerd.

**Geldige waarden**: een wille keurige teken reeks.

**Standaard**: ruimte

De `$OFS` variabele bestaat standaard niet en het scheidings teken van het uitvoer bestand is een spatie, maar u kunt deze variabele toevoegen en instellen op een wille keurige teken reeks. U kunt de waarde van `$OFS` in uw sessie wijzigen door te typen `$OFS="<value>"` .

> [!NOTE]
> Als u de standaard waarde van een spatie ( `" "` ) in uw script, module of configuratie-uitvoer verwacht, moet u ervoor zorgen dat de `$OFS` standaard waarde niet elders in de code is gewijzigd.

#### <a name="examples"></a>Voorbeelden

In dit voor beeld ziet u dat er een spatie wordt gebruikt om de waarden te scheiden wanneer een matrix wordt geconverteerd naar een teken reeks. In dit geval wordt een matrix met gehele getallen in een variabele opgeslagen en vervolgens wordt de variabele als een teken reeks gecast.

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

Als u het scheidings teken wilt wijzigen, voegt `$OFS` u de variabele toe door er een waarde aan toe te wijzen.
De variabele moet een naam hebben `$OFS` .

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

Als u het standaard gedrag wilt herstellen, kunt u een spatie ( `" "` ) toewijzen aan de waarde van `$OFS` of de variabele verwijderen. Met de volgende opdrachten verwijdert u de variabele en controleert u of het scheidings teken een spatie is.

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a>\$OutputEncoding

Bepaalt de teken coderings methode die Power shell gebruikt bij het verzenden van tekst naar andere toepassingen.

Als een toepassing bijvoorbeeld Unicode-teken reeksen retourneert naar Power shell, moet u de waarde mogelijk wijzigen in **UnicodeEncoding** om de tekens correct te verzenden.

De geldige waarden zijn als volgt: objecten die zijn afgeleid van een coderings klasse, zoals **ASCIIEncoding**, **SBCSCodePageEncoding**, **UTF7Encoding**, **UTF8Encoding**, **UTF32Encoding** en **UnicodeEncoding**.

**Standaard**: UTF8Encoding-object (System. Text. UTF8Encoding)

#### <a name="examples"></a>Voorbeelden

In dit voor beeld ziet u hoe u de Windows **findstr.exe** -opdracht in Power shell kunt gebruiken op een computer die is gelokaliseerd voor een taal die gebruikmaakt van Unicode-tekens, zoals Chinees.

De eerste opdracht zoekt de waarde van `$OutputEncoding` . Omdat de waarde een encoding-object is, wordt alleen de eigenschap **Encoding** naam weer gegeven.

```powershell
$OutputEncoding.EncodingName
```

In dit voor beeld wordt een **findstr.exe** -opdracht gebruikt om te zoeken naar twee Chinese tekens die aanwezig zijn in het `Test.txt` bestand. Wanneer deze **findstr.exe** opdracht wordt uitgevoerd in de Windows-opdracht Prompt (**cmd.exe**), wordt in **findstr.exe** de tekens in het tekst bestand gevonden. Wanneer u echter dezelfde **findstr.exe** -opdracht uitvoert in Power shell, worden de tekens niet gevonden omdat de Power shell deze verzendt naar **findstr.exe** in ASCII-tekst, in plaats van in Unicode-tekst.

```powershell
findstr <Unicode-characters>
```

Als u de opdracht in Power shell wilt gebruiken, stelt u de waarde van `$OutputEncoding` in op de waarde van de eigenschap **OutputEncoding** van de-console, die is gebaseerd op de land instelling die voor Windows is geselecteerd. Omdat **OutputEncoding** een statische eigenschap van de console is, gebruikt u dubbele punten ( `::` ) in de opdracht.

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

Nadat de code ring is gewijzigd, vindt de **findstr.exe** opdracht de Unicode-tekens.

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a>\$ProgressPreference

Bepaalt hoe Power shell reageert op de voortgangs updates die zijn gegenereerd door een script, cmdlet of provider, zoals de voortgangs balken die worden gegenereerd door de cmdlet [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) .
`Write-Progress`Met de cmdlet worden voortgangs balken gemaakt waarin de status van een opdracht wordt weer gegeven.

De geldige waarden zijn als volgt:

- **Stop**: de voortgangs balk wordt niet weer gegeven. In plaats daarvan wordt er een fout bericht weer gegeven en wordt de uitvoering gestopt.
- **Query**: de voortgangs balk wordt niet weer gegeven. Vraagt om toestemming om door te gaan. Als u met `Y` of beantwoordt `A` , wordt de voortgangs balk weer gegeven.
- **Door gaan**: (standaard) Hiermee wordt de voortgangs balk weer gegeven en wordt de uitvoering voortgezet.
- **SilentlyContinue**: de opdracht wordt uitgevoerd, maar de voortgangs balk wordt niet weer gegeven.

### <a name="psemailserver"></a>\$PSEmailServer

Hiermee geeft u de standaard-e-mail server op die wordt gebruikt voor het verzenden van e-mail berichten. Deze voorkeurs variabele wordt gebruikt door cmdlets die e-mail verzenden, zoals de cmdlet [Send-mail Message](xref:Microsoft.PowerShell.Utility.Send-MailMessage) .

### <a name="psdefaultparametervalues"></a>\$PSDefaultParameterValues

Hiermee geeft u de standaard waarden voor de para meters van cmdlets en geavanceerde functies.
De waarde van `$PSDefaultParameterValues` is een hash-tabel waarbij de sleutel bestaat uit de naam van de cmdlet en de naam van de para meter, gescheiden door een dubbele punt ( `:` ). De waarde is een aangepaste standaard waarde die u opgeeft.

`$PSDefaultParameterValues` is geïntroduceerd in Power Shell 3,0.

Zie [about_Parameters_Default_Values](about_Parameters_Default_Values.md)voor meer informatie over deze voorkeurs variabele.

### <a name="psmoduleautoloadingpreference"></a>\$PSModuleAutoloadingPreference

Hiermee wordt het automatisch importeren van modules in de sessie in-en uitgeschakeld. Dit **is de** standaard instelling. Ongeacht de waarde van de variabele kunt u [import-module](xref:Microsoft.PowerShell.Core.Import-Module) gebruiken om een module te importeren.

Geldige waarden zijn:

- **Alle**: modules worden automatisch geïmporteerd bij het eerste gebruik. Als u een module wilt importeren, kunt u elke opdracht in de module ophalen of gebruiken. Gebruik bijvoorbeeld `Get-Command`.
- **ModuleQualified**: modules worden alleen automatisch geïmporteerd wanneer een gebruiker de module-gekwalificeerde naam van een opdracht in de module gebruikt. Als de gebruiker bijvoorbeeld typt, wordt `MyModule\MyCommand` de **MyModule** -module door Power shell geïmporteerd.
- **Geen**: het automatisch importeren van modules is uitgeschakeld in de sessie. Als u een module wilt importeren, gebruikt u de `Import-Module` cmdlet.

Zie [about_Modules](about_Modules.md)voor meer informatie over het automatisch importeren van modules.

### <a name="pssessionapplicationname"></a>\$PSSessionApplicationName

Hiermee geeft u de standaard toepassings naam voor een externe opdracht die gebruikmaakt van webservices voor beheer (WS-Management)-technologie. Zie [about Windows Remote Management](/windows/win32/winrm/about-windows-remote-management)(Engelstalig) voor meer informatie.

De standaard naam van de systeem toepassing is `WSMAN` , maar u kunt deze voorkeurs variabele gebruiken om de standaard waarde te wijzigen.

De naam van de toepassing is het laatste knoop punt in een verbindings-URI. Bijvoorbeeld, de naam van de toepassing in de volgende voor beeld-URI is `WSMAN` .

`http://Server01:8080/WSMAN`

De standaard naam van de toepassing wordt gebruikt wanneer met de externe opdracht geen verbindings-URI of een toepassings naam wordt opgegeven.

De **WinRM** -service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden. De waarde van de para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.

Als u de standaard waarden van het systeem en de waarde van deze variabele wilt negeren en een andere toepassings naam voor een bepaalde sessie wilt selecteren, gebruikt u de para meters **ConnectionURI** of **ApplicationName** van de cmdlets [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)of [invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .

De `$PSSessionApplicationName` Voorkeurs variabele is ingesteld op de lokale computer, maar Hiermee wordt een listener op de externe computer opgegeven. Als de naam van de toepassing die u opgeeft niet bestaat op de externe computer, mislukt de opdracht voor het instellen van de sessie.

### <a name="pssessionconfigurationname"></a>\$PSSessionConfigurationName

Hiermee geeft u de standaard sessie configuratie op die wordt gebruikt voor **PSSessions** die zijn gemaakt in de huidige sessie.

Deze voorkeurs variabele is ingesteld op de lokale computer, maar Hiermee geeft u een sessie configuratie op die zich op de externe computer bevindt.

De waarde van de `$PSSessionConfigurationName` variabele is een volledig gekwalificeerde resource-URI.

De standaard waarde `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` geeft de configuratie van de **micro soft. Power shell** -sessie op de externe computer aan.

Als u alleen een configuratie naam opgeeft, wordt de volgende schema-URI voor het voor voegsel geplaatst:

`http://schemas.microsoft.com/PowerShell/`

U kunt de standaard instelling onderdrukken en een andere sessie configuratie voor een bepaalde sessie selecteren met behulp van de para meter **configuratiepad** van de `New-PSSession` `Enter-PSSession` `Invoke-Command` cmdlets, of.

U kunt de waarde van deze variabele op elk gewenst moment wijzigen. Houd er rekening mee dat de door u geselecteerde sessie configuratie op de externe computer moet bestaan. Als dat niet het geval is, mislukt de opdracht voor het maken van een sessie die gebruikmaakt van de sessie configuratie.

Met deze voorkeurs variabele kunt u niet bepalen welke lokale sessie configuraties worden gebruikt wanneer externe gebruikers een sessie maken die verbinding maakt met deze computer.
U kunt echter de machtigingen voor de lokale sessie configuraties gebruiken om te bepalen welke gebruikers ze mogen gebruiken.

### <a name="pssessionoption"></a>\$PSSessionOption

Hiermee worden de standaard waarden voor geavanceerde gebruikers opties ingesteld in een externe sessie.
Met deze optie Voorkeuren worden de standaard waarden van het systeem voor sessie opties genegeerd.

De `$PSSessionOption` variabele bevat een **PSSessionOption** -object. Zie [System. Management. Automation. Remoting. PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption)voor meer informatie.
Elke eigenschap van het object vertegenwoordigt een sessie optie. De eigenschap ' niet **comprimeren** ' wordt bijvoorbeeld tijdens de sessie van gegevens compressie ingeschakeld.

De `$PSSessionOption` variabele bevat standaard een **PSSessionOption** -object met de standaard waarden voor alle opties, zoals hieronder wordt weer gegeven.

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor een beschrijving van deze opties en meer informatie. Zie [about_Remote](about_Remote.md) en [about_PSSessions](about_PSSessions.md)voor meer informatie over externe opdrachten en sessies.

Als u de waarde van de `$PSSessionOption` Voorkeurs variabele wilt wijzigen, gebruikt `New-PSSessionOption` u de cmdlet om een **PSSessionOption** -object te maken met de optie waarden die u wilt gebruiken. Sla de uitvoer op in een variabele met de naam `$PSSessionOption` .

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

Als u de `$PSSessionOption` Voorkeurs variabele in elke Power shell-sessie wilt gebruiken, voegt u een `New-PSSessionOption` opdracht toe waarmee de variabele wordt gemaakt in `$PSSessionOption` uw Power shell-profiel. Zie [about_Profiles](about_Profiles.md)voor meer informatie.

U kunt aangepaste opties instellen voor een bepaalde externe sessie. De opties die u instelt, hebben voor rang op de standaard waarden van het systeem en de waarde van de `$PSSessionOption` Voorkeurs variabele.

Als u aangepaste sessie opties wilt instellen, gebruikt u de `New-PSSessionOption` cmdlet om een **PSSessionOption** -object te maken. Gebruik vervolgens het object **PSSessionOption** als de waarde van de para meter **SessionOption** in cmdlets die een sessie maken, zoals `New-PSSession` , `Enter-PSSession` , en `Invoke-Command` .

### <a name="transcript"></a>$Transcript

Wordt gebruikt door `Start-Transcript` om de naam en locatie van het transcript-bestand op te geven. Als u geen waarde opgeeft voor de para meter **Path** , `Start-Transcript` wordt het pad gebruikt in de waarde van de `$Transcript` globale variabele. Als u deze variabele niet hebt gemaakt, `Start-Transcript` slaat de transcripten in de `$Home\My Documents` map op als `\PowerShell_transcript.<time-stamp>.txt` bestanden.

### <a name="verbosepreference"></a>\$VerbosePreference

Bepaalt hoe Power shell reageert op uitgebreide berichten die zijn gegenereerd door een script, cmdlet of provider, zoals de berichten die door de cmdlet [Write-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) worden gegenereerd.
Uitgebreide berichten beschrijven de acties die worden uitgevoerd om een opdracht uit te voeren.

Standaard worden uitgebreide berichten niet weer gegeven, maar u kunt dit gedrag wijzigen door de waarde van te wijzigen `$VerbosePreference` .

U kunt de **uitgebreide** algemene para meter van een cmdlet gebruiken om de uitgebreide berichten voor een specifieke opdracht weer te geven of te verbergen. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.

De geldige waarden zijn als volgt:

- **Stoppen**: Hiermee wordt het uitgebreide bericht en een fout bericht weer gegeven en wordt de uitvoering gestopt.
- **Query**: Hiermee wordt het uitgebreide bericht weer gegeven en wordt er een prompt weer gegeven waarin u wordt gevraagd of u wilt door gaan.
- **Door gaan**: Hiermee wordt het uitgebreide bericht weer gegeven en wordt de uitvoering voortgezet.
- **SilentlyContinue**: (standaard) geeft het uitgebreide bericht niet weer. Gaat verder met uitvoeren.

#### <a name="examples"></a>Voorbeelden

In deze voor beelden ziet u het effect van de verschillende waarden van `$VerbosePreference` en de **uitgebreide** para meter om de voorkeurs waarde te overschrijven.

In dit voor beeld ziet u het effect van de **SilentlyContinue** -waarde. Dit is de standaard instelling. De opdracht gebruikt de para meter **bericht** , maar schrijft geen bericht naar de Power shell-console.

```powershell
Write-Verbose -Message "Verbose message test."
```

Wanneer de **uitgebreide** para meter wordt gebruikt, wordt het bericht geschreven.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

In dit voor beeld ziet u het effect van de waarde **continue** . De `$VerbosePreference` variabele is ingesteld om **door te gaan** en het bericht wordt weer gegeven.

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

In dit voor beeld wordt de **uitgebreide** para meter met de waarde van `$false` vervangen door de waarde **continue** . Het bericht wordt niet weer gegeven.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

In dit voor beeld wordt het effect van de waarde **Stop** weer gegeven. De `$VerbosePreference` variabele wordt ingesteld op **stoppen** en het bericht wordt weer gegeven. De opdracht is gestopt.

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

In dit voor beeld wordt de para meter **uitgebreid** gebruikt met de waarde `$false` die de **Stop** waarde overschrijft. Het bericht wordt niet weer gegeven.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

In dit voor beeld ziet u het effect van de waarde van de **query** . De `$VerbosePreference` variabele is ingesteld op **query's**. Het bericht wordt weer gegeven en de gebruiker wordt om bevestiging gevraagd.

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

In dit voor beeld wordt de **uitgebreide** para meter met de waarde van `$false` vervangen door de waarde van de **query** . De gebruiker wordt niet gevraagd en het bericht wordt niet weer gegeven.

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a>\$WarningPreference

Bepaalt hoe Power shell reageert op waarschuwings berichten die worden gegenereerd door een script, cmdlet of provider, zoals de berichten die worden gegenereerd door de cmdlet [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) .

Standaard worden waarschuwings berichten weer gegeven en de uitvoering wordt voortgezet, maar u kunt dit gedrag wijzigen door de waarde van te wijzigen `$WarningPreference` .

U kunt de algemene para meter **WarningAction** van een cmdlet gebruiken om te bepalen hoe Power shell reageert op waarschuwingen van een bepaalde opdracht. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie.

De geldige waarden zijn als volgt:

- **Stoppen**: Hiermee wordt het waarschuwings bericht en een fout bericht weer gegeven en wordt de uitvoering gestopt.
- **Query**: geeft het waarschuwings bericht weer en vraagt om toestemming om door te gaan.
- **Door gaan**: (standaard) Hiermee wordt het waarschuwings bericht weer gegeven en wordt de uitvoering voortgezet.
- **SilentlyContinue**: het waarschuwings bericht wordt niet weer gegeven. Gaat verder met uitvoeren.

#### <a name="examples"></a>Voorbeelden

In deze voor beelden ziet u het effect van de verschillende waarden van `$WarningPreference` .
De para meter **WarningAction** overschrijft de voorkeurs waarde.

In dit voor **beeld wordt het** effect van de standaard waarde weer gegeven.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

In dit voor beeld wordt de para meter **WarningAction** gebruikt met de waarde **SilentlyContinue** om de waarschuwing te onderdrukken. Het bericht wordt niet weer gegeven.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

In dit voor beeld wordt de `$WarningPreference` variabele gewijzigd in de waarde **SilentlyContinue** . Het bericht wordt niet weer gegeven.

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

In dit voor beeld wordt de para meter **WarningAction** gebruikt om te stoppen wanneer een waarschuwing wordt gegenereerd.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

In dit voor beeld wordt de `$WarningPreference` variabele gewijzigd in de **query** waarde. De gebruiker wordt gevraagd om bevestiging.

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

In dit voor beeld wordt de para meter **WarningAction** gebruikt met de waarde **SilentlyContinue**. De opdracht blijft uitvoeren en er wordt geen bericht weer gegeven.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

In dit voor beeld wordt de `$WarningPreference` te **stoppen** waarde gewijzigd.

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

In dit voor beeld wordt de **WarningAction** gebruikt met de **query** waarde. De gebruiker wordt gevraagd wanneer een waarschuwing wordt weer gegeven.

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a>\$WhatIfPreference

Hiermee wordt bepaald of **WhatIf** automatisch wordt ingeschakeld voor elke opdracht die het ondersteunt. Wanneer **WhatIf** is ingeschakeld, rapporteert de cmdlet het verwachte effect van de opdracht, maar voert de-opdracht niet uit.

De geldige waarden zijn als volgt:

- **False** (**0**, niet ingeschakeld): (standaard) **WhatIf** is niet automatisch ingeschakeld. Als u deze hand matig wilt inschakelen, gebruikt u de para meter **WhatIf** van de cmdlet.
- **True** (**1**, ingeschakeld): **WhatIf** wordt automatisch ingeschakeld voor alle opdrachten die dit ondersteunen. Gebruikers kunnen de para meter **WhatIf** gebruiken met de waarde **False** om deze hand matig uit te scha kelen, zoals `-WhatIf:$false` .

#### <a name="examples"></a>Voorbeelden

In deze voor beelden ziet u het effect van de verschillende waarden van `$WhatIfPreference` .
Ze laten zien hoe u de para meter **WhatIf** kunt gebruiken om de voorkeurs waarde voor een specifieke opdracht te overschrijven.

In dit voor beeld wordt het effect van de `$WhatIfPreference` variabele ingesteld op de standaard waarde, **Onwaar**. Gebruiken `Get-ChildItem` om te controleren of het bestand bestaat.
`Remove-Item` Hiermee verwijdert u het bestand. Nadat het bestand is verwijderd, kunt u de verwijdering controleren met `Get-ChildItem` .

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

In dit voor beeld ziet u het effect van het gebruik van de para meter **WhatIf** wanneer de waarde van is ingesteld op `$WhatIfPreference` **False**.

Controleer of het bestand bestaat.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

Gebruik de para meter **WhatIf** om het resultaat van de poging om het bestand te verwijderen te bepalen.

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

Controleer of het bestand niet is verwijderd.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

In dit voor beeld ziet u het effect van de `$WhatIfPreference` variabele die is ingesteld op de waarde **True**. Wanneer u gebruikt `Remove-Item` om een bestand te verwijderen, wordt het pad van het bestand weer gegeven, maar wordt het bestand niet verwijderd.

Poging een bestand te verwijderen. Er wordt een bericht weer gegeven over wat er zou gebeuren als `Remove-Item` het programma werd uitgevoerd, maar het bestand wordt niet verwijderd.

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

Gebruiken `Get-ChildItem` om te controleren of het bestand niet is verwijderd.

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

In dit voor beeld ziet u hoe u een bestand verwijdert wanneer de waarde van is ingesteld op `$WhatIfPreference` **True**. De para meter **WhatIf** wordt gebruikt met de waarde `$false` . Gebruiken `Get-ChildItem` om te controleren of het bestand is verwijderd.

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

Hier volgen enkele voor beelden van de `Get-Process` cmdlet die geen ondersteuning biedt voor **WhatIf** en `Stop-Process` die **WhatIf** ondersteunt. De `$WhatIfPreference` waarde van de variabele is **waar**.

`Get-Process` biedt geen ondersteuning voor **WhatIf**. Wanneer de opdracht wordt uitgevoerd, wordt het **Winword** -proces weer gegeven.

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

`Stop-Process` biedt ondersteuning voor **WhatIf**. Het **Winword** -proces is niet gestopt.

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

U kunt het `Stop-Process` gedrag van de **WhatIf** negeren door de para meter **WhatIf** te gebruiken met de waarde `$false` . Het **Winword** -proces is gestopt.

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

Gebruik om te controleren of het proces **Winword** is gestopt `Get-Process` .

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a>Zie ook

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_CommonParameters](about_CommonParameters.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Variables](about_Variables.md)

