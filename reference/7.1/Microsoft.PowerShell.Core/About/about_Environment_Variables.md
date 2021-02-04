---
description: Hierin wordt beschreven hoe u toegang krijgt tot Windows-omgevings variabelen in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 4b5894822f4436f127ed4789fd8008a0e7f2f2df
ms.sourcegitcommit: f5986121386c81acddcf324eb0526d7d092bcc8f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584640"
---
# <a name="about-environment-variables"></a>Omgevings variabelen

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe u toegang krijgt tot Windows-omgevings variabelen in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

Omgevings variabelen bevatten informatie over de besturingssysteem omgeving. Deze informatie bevat details zoals het pad van het besturings systeem, het aantal processors dat wordt gebruikt door het besturings systeem en de locatie van tijdelijke mappen.

De omgevings variabelen slaan gegevens op die worden gebruikt door het besturings systeem en andere Program ma's. De `WINDIR` omgevings variabele bevat bijvoorbeeld de locatie van de installatiemap van Windows. Program ma's kunnen een query uitvoeren op de waarde van deze variabele om te bepalen waar de bestanden van het Windows-besturings systeem zich bevinden.

Power shell kan omgevings variabelen openen en beheren in elk van de ondersteunde besturingssysteem platforms. De provider van de Power shell-omgeving vereenvoudigt dit proces door het weer geven en wijzigen van omgevings variabelen te vergemakkelijken.

Omgevings variabelen, in tegens telling tot andere typen variabelen in Power shell, worden overgenomen door onderliggende processen, zoals lokale achtergrond taken en de sessies waarin module leden worden uitgevoerd. Dit zorgt ervoor dat omgevings variabelen goed zijn geschikt voor het opslaan van waarden die nodig zijn voor zowel het bovenliggende als het onderliggende proces.

## <a name="using-and-changing-environment-variables"></a>Omgevings variabelen gebruiken en wijzigen

In Windows kunnen omgevings variabelen in drie bereiken worden gedefinieerd:

- Machine-(of systeem) bereik
- Gebruikers bereik
- Proces bereik

Het _proces_ bereik bevat de omgevings variabelen die beschikbaar zijn in het huidige proces of Power shell-sessie. Deze lijst met variabelen wordt overgenomen van het bovenliggende proces en wordt samengesteld op basis van de variabelen in de _computer_ -en _gebruikers_ bereik. Op UNIX gebaseerde platforms hebben alleen het _proces_ bereik.

U kunt de waarden van omgevings variabelen weer geven en wijzigen zonder een cmdlet te gebruiken met behulp van een variabele syntaxis met de omgevings provider. Als u de waarde van een omgevings variabele wilt weer geven, gebruikt u de volgende syntaxis:

```
$Env:<variable-name>
```

Als u bijvoorbeeld de waarde van de `WINDIR` omgevings variabele wilt weer geven, typt u de volgende opdracht achter de Power shell-opdracht prompt:

```powershell
$Env:windir
```

In deze syntaxis duidt het dollar teken ( `$` ) aan een variabele en geeft de stationsnaam ( `Env:` ) een omgevings variabele aan, gevolgd door de naam van de variabele ( `windir` ).

Wanneer u omgevings variabelen in Power shell wijzigt, is de wijziging alleen van invloed op de huidige sessie. Dit gedrag lijkt op het gedrag van de `Set` opdracht in de Windows-opdracht shell en de `Setenv` opdracht in op UNIX gebaseerde omgevingen. Als u waarden in het bereik van de computer of de gebruiker wilt wijzigen, moet u de methoden van de klasse **System. Environment** gebruiken.

Als u wijzigingen wilt aanbrengen in de variabelen van de computer bereik, moet ook over machtigingen beschikken. Als u probeert een waarde te wijzigen zonder voldoende machtiging, mislukt de opdracht en wordt een fout weer gegeven in Power shell.

U kunt de waarden van variabelen wijzigen zonder gebruik te maken van een cmdlet met de volgende syntaxis:

```powershell
$Env:<variable-name> = "<new-value>"
```

Als u bijvoorbeeld wilt toevoegen `;c:\temp` aan de waarde van de `Path` omgevings variabele, gebruikt u de volgende syntaxis:

```powershell
$Env:Path += ";c:\temp"
```

In Linux of macOS scheidt de dubbele punt ( `:` ) in de opdracht het nieuwe pad van het pad dat voorafgaat aan de voor waarde in de lijst.

```powershell
$Env:PATH += ":/usr/local/temp"
```

U kunt ook de item-cmdlets gebruiken, zoals `Set-Item` , `Remove-Item` , en `Copy-Item` de waarden van omgevings variabelen wijzigen. Als u bijvoorbeeld de cmdlet wilt gebruiken `Set-Item` om toe `;c:\temp` te voegen aan de waarde van de `Path` omgevings variabele, gebruikt u de volgende syntaxis:

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

In deze opdracht wordt de waarde tussen haakjes geplaatst, zodat deze wordt geïnterpreteerd als een eenheid.

## <a name="environment-variables-that-store-preferences"></a>Omgevings variabelen waarin voor keuren worden opgeslagen

Met de Power shell-functies kunt u omgevings variabelen gebruiken om gebruikers voorkeuren op te slaan.
Deze variabelen werken als voorkeurs variabelen, maar ze worden overgenomen door onderliggende sessies van de sessies waarin ze zijn gemaakt. Zie [about_preference_variables](about_Preference_Variables.md)voor meer informatie over voorkeurs variabelen.

De omgevings variabelen waarin de voor keuren zijn opgeslagen, zijn:

- PSExecutionPolicyPreference

  Slaat de uitvoerings beleidset voor de huidige sessie op. Deze omgevings variabele bestaat alleen wanneer u een uitvoerings beleid voor één sessie instelt.
  U kunt dit op twee verschillende manieren doen.

  - Start een sessie vanaf de opdracht regel met behulp van de para meter **ExecutionPolicy** om het uitvoerings beleid voor de sessie in te stellen.

  - Gebruik de `Set-ExecutionPolicy` cmdlet. Gebruik de bereik parameter met de waarde ' process '.

    Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie.

- PSModuleAnalysisCachePath

  Power shell biedt controle over het bestand dat wordt gebruikt voor het opslaan van gegevens over modules en de bijbehorende cmdlets. De cache wordt tijdens het opstarten gelezen tijdens het zoeken naar een opdracht en wordt ergens op een achtergrond thread geschreven nadat een module is geïmporteerd.

  De standaard locatie van de cache is:

  - Windows Power shell 5,1: `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`
  - Power shell 6,0 en hoger: `$env:LOCALAPPDATA\Microsoft\PowerShell`
  - Niet-Windows-standaard: `~/.cache/powershell`

  De standaard bestandsnaam voor de cache is `ModuleAnalysisCache` . Wanneer er meerdere instanties van Power shell zijn geïnstalleerd, bevat de bestands naam een hexadecimaal achtervoegsel, zodat er een unieke bestands naam per installatie is.

  > [!NOTE]
  > Als de opdracht detectie niet correct werkt, bijvoorbeeld IntelliSense opdrachten bevat die niet bestaan, kunt u het cache bestand verwijderen. De cache wordt opnieuw gemaakt wanneer u Power shell de volgende keer start.

  Als u de standaard locatie van de cache wilt wijzigen, stelt u de omgevings variabele in voordat u Power shell start. Wijzigingen in deze omgevings variabele zijn alleen van invloed op onderliggende processen. De waarde moet een volledig pad (inclusief bestands naam) zijn dat Power shell toestemming heeft om bestanden te maken en te schrijven.

  Als u de bestands cache wilt uitschakelen, stelt u deze waarde in op een ongeldige locatie, bijvoorbeeld:

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to,
  # on non-Windows you would use `/dev/null`
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  Hiermee stelt u het pad naar het **nul** -apparaat in. Power shell kan niet naar het pad schrijven, maar er is geen fout geretourneerd. U kunt de fouten zien die zijn gerapporteerd met behulp van een tracering:

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- PSDisableModuleAnalysisCacheCleanup

  Wanneer u de module analyse cache afschrijft, controleert Power shell op modules die niet meer bestaan om een onnodig grote cache te voor komen. Soms zijn deze controles niet gewenst, in welk geval u deze kunt uitschakelen door deze omgevings variabele in te stellen op `1` .

  Het instellen van deze omgevings variabele wordt direct van kracht in het huidige proces.

- PSModulePath

  De `$env:PSModulePath` omgevings variabele bevat een lijst met maplocaties die worden doorzocht om modules en resources te zoeken.

  De doel locaties die worden toegewezen aan, `$env:PSModulePath` zijn standaard:

  - Locaties voor het hele systeem: deze mappen bevatten modules die worden geleverd met Power shell. De modules worden opgeslagen op de `$PSHOME\Modules` locatie. Dit is ook de locatie waar de Windows-beheer modules worden geïnstalleerd.

  - Door de gebruiker geïnstalleerde modules: Dit zijn de modules die door de gebruiker zijn geïnstalleerd.
    `Install-Module` heeft een **bereik** parameter waarmee u kunt opgeven of de module is geïnstalleerd voor de huidige gebruiker of voor alle gebruikers. Zie [install-module](xref:PowerShellGet.Install-Module)voor meer informatie.

    - In Windows is de locatie van **het gebruikersspecifieke Windows-bereik de** `$HOME\Documents\PowerShell\Modules` map. De locatie van het **ALLUSERS** bereik is `$env:ProgramFiles\PowerShell\Modules` .
    - Op niet-Windows-systemen is de locatie van **het gebruikersspecifieke Windows-bereik de** `$HOME/.local/share/powershell/Modules` map. De locatie van het **ALLUSERS** bereik is `/usr/local/share/powershell/Modules` .

  Daarnaast kunnen installatie Programma's waarmee modules in andere directory's worden geïnstalleerd, zoals de map Program Files, hun locaties toevoegen aan de waarde van `$env:PSModulePath` .

  Zie [about_PSModulePath](about_PSModulePath.md)voor meer informatie.

## <a name="managing-environment-variables"></a>Omgevings variabelen beheren

Power shell biedt verschillende methoden voor het beheren van omgevings variabelen.

- Het omgevings provider station
- De item-cmdlets
- De klasse .NET **System. Environment**
- In Windows, het configuratie scherm van het systeem

### <a name="using-the-environment-provider"></a>De omgevings provider gebruiken

Elke omgevings variabele wordt vertegenwoordigd door een instantie van de klasse **System. Collections. Dictionary entry** . In elk **Dictionary entry** -object is de naam van de omgevings variabele de woorden lijst sleutel. De waarde van de variabele is de woordenlijst waarde.

Gebruik de cmdlet om de eigenschappen en methoden van het object weer te geven die een omgevings variabele in Power shell vertegenwoordigen `Get-Member` . Als u bijvoorbeeld de methoden en eigenschappen van alle objecten in het station wilt weer geven `Env:` , typt u:

```powershell
Get-Item -Path Env:* | Get-Member
```

De provider van de Power shell-omgeving biedt toegang tot omgevings variabelen in een Power Shell-station (het `Env:` station). Dit station ziet er ongeveer uit als een bestandssysteem station. Als u naar het `Env:` station wilt gaan, typt u:

```powershell
Set-Location Env:
```

Gebruik de cmdlets voor inhoud om de waarden van een omgevings variabele op te halen of in te stellen.

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

U kunt de omgevings variabelen in het `Env:` station weer geven vanuit elk ander Power Shell-station en u kunt naar het `Env:` station gaan om de omgevings variabelen weer te geven en te wijzigen.

### <a name="using-item-cmdlets"></a>Item-cmdlets gebruiken

Wanneer u verwijst naar een omgevings variabele, typt u de `Env:` naam van het station gevolgd door de naam van de variabele. Als u bijvoorbeeld de waarde van de `COMPUTERNAME` omgevings variabele wilt weer geven, typt u:

```powershell
Get-ChildItem Env:Computername
```

Als u de waarden van alle omgevings variabelen wilt weer geven, typt u:

```powershell
Get-ChildItem Env:
```

Omdat omgevings variabelen geen onderliggende items hebben, is de uitvoer van `Get-Item` en `Get-ChildItem` is dezelfde.

Standaard worden de omgevings variabelen in Power shell weer gegeven in de volg orde waarin ze worden opgehaald. Als u de lijst met omgevings variabelen wilt sorteren op naam van variabele, pipet u de uitvoer van een `Get-ChildItem` opdracht naar de `Sort-Object` cmdlet. Typ bijvoorbeeld van elk Power Shell-station:

```powershell
Get-ChildItem Env: | Sort Name
```

U kunt ook naar het `Env:` station gaan met behulp van de `Set-Location` cmdlet:

```powershell
Set-Location Env:
```

Wanneer u zich in het station bevindt `Env:` , kunt u de `Env:` naam van het station weglaten uit het pad. Als u bijvoorbeeld alle omgevings variabelen wilt weer geven, typt u:

```powershell
PS Env:\> Get-ChildItem
```

Als u de waarde van de variabele wilt weer geven in `COMPUTERNAME` het `Env:` station, typt u:

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a>Wijzigingen in omgevings variabelen opslaan

Als u een permanente wijziging wilt aanbrengen in een omgevings variabele in Windows, gebruikt u het configuratie scherm van het systeem. Selecteer **geavanceerde systeem instellingen**. Klik op het tabblad **Geavanceerd** op **omgevings variabele...**. U kunt bestaande omgevings variabelen toevoegen of bewerken in de scopes van de **gebruiker** en het **systeem** (machine). Windows schrijft deze waarden naar het REGI ster, zodat ze behouden blijven in sessies en het opnieuw opstarten van het systeem.

U kunt ook omgevings variabelen toevoegen of wijzigen in uw Power shell-profiel. Deze methode werkt voor elke versie van Power shell op elk ondersteund platform.

### <a name="using-systemenvironment-methods"></a>Methoden van System. Environment gebruiken

De klasse **System. Environment** biedt **GetEnvironmentVariable** -en **SetEnvironmentVariable** -methoden waarmee u het bereik van de variabele kunt opgeven.

In het volgende voor beeld wordt de methode **GetEnvironmentVariable** gebruikt om de instelling van de computer `PSModulePath` en de methode **SetEnvironmentVariable** toe te voegen aan de `C:\Program Files\Fabrikam\Modules` waarde.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

Zie [omgevings methoden](/dotnet/api/system.environment)voor meer informatie over de methoden van de klasse **System. Environment** .

## <a name="see-also"></a>ZIE OOK

- [Omgeving (provider)](../About/about_Environment_Provider.md)
- [about_Modules](about_Modules.md)

