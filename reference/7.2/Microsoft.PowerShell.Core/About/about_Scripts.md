---
description: Hierin wordt beschreven hoe u scripts in Power shell uitvoert en schrijft.
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: 2fc81d1d43b8cdddaacb917deaa5d58536a541cb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706081"
---
# <a name="about-scripts"></a>Over scripts

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u scripts in Power shell uitvoert en schrijft.

## <a name="long-description"></a>Lange beschrijving

Een script is een bestand met tekst zonder opmaak dat een of meer Power shell-opdrachten bevat.
Power shell-scripts hebben een `.ps1` bestands extensie.

Het uitvoeren van een script is veel hetzelfde als het uitvoeren van een cmdlet. U typt het pad en de bestands naam van het script en gebruikt para meters om gegevens in te dienen en opties in te stellen. U kunt scripts uitvoeren op uw computer of in een externe sessie op een andere computer.

Als u een script schrijft, wordt een opdracht voor later gebruik opgeslagen en kunt u eenvoudig delen met anderen. Het belangrijkste is dat u de opdrachten kunt uitvoeren door simpelweg het pad naar het script en de bestands naam op te geven. Scripts kunnen zo eenvoudig zijn als één opdracht in een bestand of zo uitgebreid als een complex programma.

Scripts hebben extra functies, zoals de `#Requires` speciale opmerking, het gebruik van para meters, ondersteuning voor gegevens secties en digitale hand tekeningen voor beveiliging.
U kunt ook Help-onderwerpen voor scripts en voor alle functies in het script schrijven.

## <a name="how-to-run-a-script"></a>Een script uitvoeren

Voordat u een script kunt uitvoeren in Windows, moet u het standaard beleid voor Power shell-uitvoering wijzigen. Uitvoerings beleid is niet van toepassing op Power shell die wordt uitgevoerd op niet-Windows-platforms.

Het standaard uitvoerings beleid, `Restricted` , voor komt dat alle scripts worden uitgevoerd, met inbegrip van scripts die u op de lokale computer schrijft. Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie.

Het uitvoerings beleid wordt opgeslagen in het REGI ster, dus u hoeft dit slechts één keer op elke computer te wijzigen.

Gebruik de volgende procedure om het uitvoerings beleid te wijzigen.

Typ in de opdrachtprompt:

```powershell
Set-ExecutionPolicy AllSigned
```

of

```powershell
Set-ExecutionPolicy RemoteSigned
```

De wijziging is direct van kracht.

Als u een script wilt uitvoeren, typt u de volledige naam en het volledige pad naar het script bestand.

Als u bijvoorbeeld het Get-ServiceLog.ps1 script wilt uitvoeren in de map C:\Scripts, typt u:

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

Als u een script wilt uitvoeren in de huidige map, typt u het pad naar de huidige map of gebruikt u een punt om de huidige map weer te geven, gevolgd door een pad naar een back slash ( `.\` ).

Als u bijvoorbeeld het ServicesLog.ps1 script wilt uitvoeren in de lokale map, typt u:

```powershell
.\Get-ServiceLog.ps1
```

Als het script para meters heeft, typt u de para meters en parameter waarden na de script bestandsnaam.

De volgende opdracht gebruikt bijvoorbeeld de para meter ServiceName van het Get-ServiceLog script om een logboek van de WinRM-service activiteit aan te vragen.

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

Als beveiligings functie voert Power shell geen scripts uit wanneer u dubbelklikt op het script pictogram in Verkenner of wanneer u de script naam typt zonder een volledig pad, zelfs wanneer het script zich in de huidige map bevindt. Zie [about_Command_Precedence](about_Command_Precedence.md)voor meer informatie over het uitvoeren van opdrachten en scripts in Power shell.

### <a name="run-with-powershell"></a>Uitvoeren met Power shell

Vanaf Power Shell 3,0 kunt u scripts uitvoeren vanuit Verkenner.

De functie ' uitvoeren met Power shell ' gebruiken:

Voer de Verkenner uit, klik met de rechter muisknop op het script bestands naam en selecteer uitvoeren met Power shell.

De functie ' uitvoeren met Power shell ' is ontworpen voor het uitvoeren van scripts waarvoor geen vereiste para meters zijn en die geen uitvoer retour neren naar de opdracht prompt.

Zie [about_Run_With_PowerShell](about_Run_With_PowerShell.md)voor meer informatie.

### <a name="running-scripts-on-other-computers"></a>Scripts uitvoeren op andere computers

Als u een script wilt uitvoeren op een of meer externe computers, gebruikt u de para meter **filepath** van de `Invoke-Command` cmdlet.

Voer het pad en de bestands naam van het script in als de waarde van de **filepath** -para meter. Het script moet zich bevinden op de lokale computer of in een map waartoe de lokale computer toegang heeft.

Met de volgende opdracht wordt het `Get-ServiceLog.ps1` script uitgevoerd op de externe computers met de naam Server01 en Server02.

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a>Hulp vragen voor scripts

Met de cmdlet Get-Help worden de Help-onderwerpen voor scripts en voor cmdlets en andere typen opdrachten opgehaald. Als u het Help-onderwerp voor een script wilt ophalen, typt u `Get-Help` gevolgd door het pad en de bestands naam van het script. Als het scriptpad zich in uw `Path` omgevings variabele bevindt, kunt u het pad weglaten.

Als u bijvoorbeeld hulp wilt krijgen voor het ServicesLog.ps1 script, typt u:

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a>Een script schrijven

Een script kan een wille keurige geldige Power shell-opdracht bevatten, waaronder afzonderlijke opdrachten, opdrachten die gebruikmaken van de pijp lijn, functies en besturings structuren zoals if-instructies en for-lussen.

Als u een script wilt schrijven, opent u een nieuw bestand in een tekst editor, typt u de opdrachten en slaat u deze op in een bestand met een geldige bestands naam met de `.ps1` bestands extensie.

Het volgende voor beeld is een eenvoudig script waarmee de services worden opgehaald die worden uitgevoerd op het huidige systeem en worden opgeslagen in een logboek bestand. De naam van het logboek bestand wordt gemaakt op basis van de huidige datum.

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

Als u dit script wilt maken, opent u een tekst editor of een script editor, typt u deze opdrachten en slaat u deze op in een bestand met de naam `ServiceLog.ps1` .

### <a name="parameters-in-scripts"></a>Para meters in scripts

Als u para meters wilt definiëren in een script, gebruikt u een parameter instructie. De `Param` instructie moet de eerste instructie in een script zijn, met uitzonde ring van opmerkingen en `#Require` instructies.

Script parameters werken als functie parameters. De parameter waarden zijn beschikbaar voor alle opdrachten in het script. Alle functies van functie parameters, met inbegrip van het parameter kenmerk en de benoemde argumenten, zijn ook geldig in scripts.

Wanneer het script wordt uitgevoerd, typen script gebruikers de para meters na de script naam.

In het volgende voor beeld ziet u een `Test-Remote.ps1` script met de para meter **ComputerName** . Beide script functies hebben toegang tot de waarde van de para meter **ComputerName** .

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

Als u dit script wilt uitvoeren, typt u de parameter naam achter de script naam. Bijvoorbeeld:

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

Zie [about_Functions](about_Functions.md) en [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie over de parameter instructie en de functie parameters.

### <a name="writing-help-for-scripts"></a>Help voor scripts schrijven

U kunt een Help-onderwerp voor een script schrijven met behulp van een van de volgende twee methoden:

- Help voor scripts Comment-Based

  Maak een Help-onderwerp met behulp van speciale tref woorden in de opmerkingen. Als u op opmerkingen gebaseerde hulp voor een script wilt maken, moeten de opmerkingen aan het begin of einde van het script bestand worden geplaatst. Zie [about_Comment_Based_Help](about_Comment_Based_Help.md)voor meer informatie over op opmerkingen gebaseerde Help.

- Help voor scripts XML-Based

  Maak een Help-onderwerp op basis van XML, zoals het type dat doorgaans voor cmdlets wordt gemaakt. Help op basis van XML is vereist als u Help-onderwerpen in meerdere talen vertaalt.

Als u het script wilt koppelen aan het Help-onderwerp op basis van XML, gebruikt u de. ExternalHelp Help opmerking over tref woord. Zie [about_Comment_Based_Help](about_Comment_Based_Help.md)voor meer informatie over het sleutel woord ExternalHelp. Zie [instructies voor het schrijven van cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)voor meer informatie over Help op basis van XML.

### <a name="returning-an-exit-value"></a>Een eind waarde Retour neren

Scripts retour neren standaard geen afsluit status wanneer het script eindigt. U moet de `exit` instructie gebruiken om een afsluit code uit een script te retour neren. De `exit` instructie retourneert standaard `0` . U kunt een numerieke waarde opgeven om een andere afsluit status te retour neren. Een afsluit code die niet gelijk is aan nul, geeft meestal een fout aan.

In Windows is een wille keurig getal tussen `[int]::MinValue` en `[int]::MaxValue` toegestaan.

Op UNIX zijn alleen positieve getallen tussen `[byte]::MinValue` (0) en `[byte]::MaxValue` (255) toegestaan. Een negatief getal in het bereik `-1` tot en met `-255` wordt automatisch omgezet in een positief getal door het toe te voegen
256. Bijvoorbeeld, `-2` wordt omgezet naar `254` .

In Power shell `exit` stelt de instructie de waarde van de `$LASTEXITCODE` variabele in. In de Windows-opdracht shell (cmd.exe) wordt met de instructie Exit de waarde van de `%ERRORLEVEL%` omgevings variabele ingesteld.

Elk argument dat niet-numeriek of buiten het platformspecifieke bereik valt, wordt vertaald naar de waarde van `0` .

## <a name="script-scope-and-dot-sourcing"></a>Script bereik en punt sourcing

Elk script wordt uitgevoerd in een eigen bereik. De functies, variabelen, aliassen en stations die in het script zijn gemaakt, bestaan alleen in het script bereik. U hebt geen toegang tot deze items of de waarden daarvan in het bereik waarin het script wordt uitgevoerd.

Als u een script wilt uitvoeren in een ander bereik, kunt u een bereik opgeven, zoals globaal of lokaal, of u kunt het script een punt bron geven.

Met de functie dot sourcing kunt u een script uitvoeren in het huidige bereik in plaats van in het script bereik. Wanneer u een script uitvoert dat een dot-bron heeft, worden de opdrachten in het script uitgevoerd alsof u deze hebt getypt bij de opdracht prompt. De functies, variabelen, aliassen en stations die het script maakt, worden gemaakt in het bereik waarin u werkt. Nadat het script is uitgevoerd, kunt u de gemaakte items gebruiken en toegang krijgen tot hun waarden in uw sessie.

Als u een script wilt maken van een punt, typt u een punt (.) en een spatie vóór het scriptpad.

Bijvoorbeeld:

```powershell
. C:\scripts\UtilityFunctions.ps1
```

of

```powershell
. .\UtilityFunctions.ps1
```

Nadat het `UtilityFunctions.ps1` script is uitgevoerd, worden de functies en variabelen die het script maakt, toegevoegd aan het huidige bereik.

Het `UtilityFunctions.ps1` script maakt bijvoorbeeld de `New-Profile` functie en de `$ProfileName` variabele.

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

Als u het `UtilityFunctions.ps1` script uitvoert in een eigen script bereik, `New-Profile` bestaan de functie en de `$ProfileName` variabele alleen tijdens het uitvoeren van het script. Wanneer het script wordt afgesloten, worden de functie en de variabele verwijderd, zoals in het volgende voor beeld wordt weer gegeven.

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

Wanneer u het script naar een punt bron en uitvoert, maakt het script de `New-Profile` functie en de `$ProfileName` variabele in uw sessie in uw bereik. Nadat het script is uitgevoerd, kunt u de `New-Profile` functie gebruiken in uw sessie, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

Zie about_Scopes voor meer informatie over het bereik.

## <a name="scripts-in-modules"></a>Scripts in modules

Een module is een set gerelateerde Power shell-resources die kunnen worden gedistribueerd als een eenheid. U kunt modules gebruiken om uw scripts, functies en andere resources te organiseren. U kunt ook modules gebruiken om uw code naar anderen te distribueren en om code op te halen uit betrouw bare bronnen.

U kunt scripts in uw modules insluiten of u kunt een script module maken. Dit is een module die geheel of voornamelijk uit een script en ondersteunende bronnen bestaat. Een script module is slechts een script met de bestands extensie. psm1.

Zie [about_Modules](about_Modules.md)voor meer informatie over modules.

## <a name="other-script-features"></a>Andere script functies

Power Shell heeft veel nuttige functies die u in scripts kunt gebruiken.

- `#Requires` -U kunt een `#Requires` instructie gebruiken om te voor komen dat een script wordt uitgevoerd zonder opgegeven modules of modules en een opgegeven versie van Power shell. Zie about_Requires voor meer informatie.

- `$PSCommandPath` -Bevat het volledige pad en de naam van het script dat wordt uitgevoerd. Deze para meter is geldig in alle scripts. Deze automatische variabele wordt geïntroduceerd in Power Shell 3,0.

- `$PSScriptRoot` -Bevat de map van waaruit een script wordt uitgevoerd. In Power Shell 2,0 is deze variabele alleen geldig in script modules ( `.psm1` ).
  Vanaf Power Shell 3,0 is deze in alle scripts geldig.

- `$MyInvocation` -De `$MyInvocation` Automatische variabele bevat informatie over het huidige script, met inbegrip van informatie over hoe het is gestart of geactiveerd. U kunt deze variabele en de bijbehorende eigenschappen gebruiken om informatie over het script op te halen terwijl deze wordt uitgevoerd. Bijvoorbeeld, de `$MyInvocation` . De variabele MyCommand. path bevat het pad en de bestands naam van het script. `$MyInvocation`. De regel bevat de opdracht waarmee het script is gestart, inclusief alle para meters en waarden.

  Vanaf Power Shell 3,0 `$MyInvocation` heeft twee nieuwe eigenschappen die informatie geven over het script dat het huidige script heeft aangeroepen of aangeroepen. De waarden van deze eigenschappen worden alleen ingevuld wanneer de aanroepende of aanroeper een script is.

  - **PSCommandPath** bevat het volledige pad en de naam van het script dat het huidige script heeft aangeroepen of aangeroepen.

  - **PSScriptRoot** bevat de map van het script dat het huidige script heeft aangeroepen of aangeroepen.

  In tegens telling tot de `$PSCommandPath` en `$PSScriptRoot` automatische variabelen, die informatie bevatten over het huidige script, bevatten de eigenschappen **PSCommandPath** en **PSScriptRoot** van de `$MyInvocation` variabele informatie over het script dat het huidige script aanroept.

- Gegevens secties: u kunt het `Data` sleutel woord gebruiken om gegevens te scheiden van logica in scripts. Gegevens secties kunnen de lokalisatie ook gemakkelijker maken. Zie [about_Data_Sections](about_Data_Sections.md) en [about_Script_Internationalization](about_Script_Internationalization.md)voor meer informatie.

- Script ondertekening: u kunt een digitale hand tekening aan een script toevoegen. Afhankelijk van het uitvoerings beleid kunt u digitale hand tekeningen gebruiken om de uitvoering van scripts te beperken die onveilige opdrachten kunnen bevatten. Zie [about_Execution_Policies](about_Execution_Policies.md) en [about_Signing](about_Signing.md)voor meer informatie.

## <a name="see-also"></a>Zie ook

[about_Command_Precedence](about_Command_Precedence.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Functions](about_Functions.md)

[about_Modules](about_Modules.md)

[about_Profiles](about_Profiles.md)

[about_Requires](about_Requires.md)

[about_Run_With_PowerShell](about_Run_With_PowerShell.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Signing](about_Signing.md)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)
