---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: 4c45267113ff7b8a870d5a05bf3e4ab922f7e9c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705851"
---
# Set-ExecutionPolicy

## SAMENVATTING
Hiermee stelt u het Power shell-uitvoerings beleid voor Windows-computers.

## SYNTAXIS

### Alles

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Set-ExecutionPolicy` cmdlet wijzigt het Power shell-uitvoerings beleid voor Windows-computers. Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)voor meer informatie.

Vanaf Power shell 6,0 voor niet-Windows-computers is het standaard uitvoerings beleid **onbeperkt** en kan het niet worden gewijzigd. De `Set-ExecutionPolicy` cmdlet is beschikbaar, maar in Power shell wordt een console bericht weer gegeven dat niet wordt ondersteund.

Een uitvoerings beleid maakt deel uit van de Power shell-beveiligings strategie. Uitvoerings beleid bepaalt of u configuratie bestanden kunt laden, zoals uw Power shell-profiel, of scripts moet uitvoeren. En, of scripts digitaal moeten worden ondertekend voordat ze worden uitgevoerd.

Het `Set-ExecutionPolicy` standaard bereik van de cmdlet is **LocalMachine**, wat van invloed is op iedereen die de computer gebruikt. Als u het uitvoerings beleid voor **LocalMachine** wilt wijzigen, start u Power shell met **als administrator uitvoeren**.

Gebruik om het uitvoerings beleid voor elk bereik weer te geven in de volg orde van prioriteit `Get-ExecutionPolicy -List` . Om het effectief uitvoerings beleid voor uw Power shell-sessie gebruik `Get-ExecutionPolicy` zonder para meters te bekijken.

## VOORBEELDEN

### Voor beeld 1: een uitvoerings beleid instellen

In dit voor beeld ziet u hoe u het uitvoerings beleid voor de lokale computer instelt.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

De `Set-ExecutionPolicy` cmdlet gebruikt de para meter **ExecutionPolicy** om het **RemoteSigned** -beleid op te geven. De **bereik** parameter geeft de standaard waarde voor het bereik **LocalMachine**. Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.

### Voor beeld 2: een uitvoerings beleid instellen dat in conflict is met een groepsbeleid

Met deze opdracht wordt geprobeerd het uitvoerings beleid van het **LocalMachine** -bereik in te stellen op **beperkt**.
**LocalMachine** is beperkter, maar is niet het effectief beleid omdat het een conflict veroorzaakt met een Groepsbeleid. Het **beperkte** beleid wordt geschreven naar de register component **HKEY_LOCAL_MACHINE**.

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

De `Set-ExecutionPolicy` cmdlet gebruikt de para meter **ExecutionPolicy** om het **beperkte** beleid op te geven. De **bereik** parameter geeft de standaard waarde voor het bereik **LocalMachine**.
De `Get-ChildItem` cmdlet gebruikt de para meter **Path** met de **HKLM** -provider om de register locatie op te geven.

### Voor beeld 3: het uitvoerings beleid van een externe computer Toep assen op een lokale computer

Met deze opdracht wordt het uitvoerings beleid-object opgehaald van een externe computer en wordt het beleid ingesteld op de lokale computer. `Get-ExecutionPolicy` Hiermee verzendt u een **Microsoft.PowerShell.ExecutionPolicy** -object omlaag in de pijp lijn. `Set-ExecutionPolicy` de invoer van de pijp lijn wordt geaccepteerd en de para meter **ExecutionPolicy** is niet vereist.

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

De `Invoke-Command` cmdlet wordt uitgevoerd op de lokale computer en verzendt de **script Block** naar de externe computer. De para meter **ComputerName** specificeert de externe computer, **Server01**. De para meter **script Block** wordt uitgevoerd `Get-ExecutionPolicy` op de externe computer. Het `Get-ExecutionPolicy` object wordt naar beneden verzonden in de pijp lijn `Set-ExecutionPolicy` .
`Set-ExecutionPolicy` Hiermee wordt het uitvoerings beleid toegepast op het standaard bereik van de lokale computer, **LocalMachine**.

### Voor beeld 4: het bereik instellen voor een uitvoerings beleid

In dit voor beeld ziet u hoe u een uitvoerings beleid instelt voor een opgegeven bereik, **CurrentUser**. Het bereik van **CurrentUser** is alleen van invloed op de gebruiker die dit bereik instelt.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy` maakt gebruik van de para meter **ExecutionPolicy** om het **Alles ondertekend** -beleid op te geven.
De para meter **Scope** geeft de eigenschap **CurrentUser**. Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.

Het effectief uitvoerings beleid voor de gebruiker wordt **Alles ondertekend**.

### Voor beeld 5: het uitvoerings beleid voor de huidige gebruiker verwijderen

Dit voor beeld laat zien hoe u het niet- **gedefinieerde** uitvoerings beleid gebruikt voor het verwijderen van een uitvoerings beleid voor een opgegeven bereik.

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

`Set-ExecutionPolicy` maakt gebruik van de para meter **ExecutionPolicy** om het niet- **gedefinieerde** beleid op te geven.
De para meter **Scope** geeft de eigenschap **CurrentUser**. Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.

### Voor beeld 6: het uitvoerings beleid voor de huidige Power shell-sessie instellen

Het **proces** bereik is alleen van invloed op de huidige Power shell-sessie. Het uitvoerings beleid wordt opgeslagen in de omgevings variabele `$env:PSExecutionPolicyPreference` en wordt verwijderd wanneer de sessie wordt gesloten.

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

De `Set-ExecutionPolicy` para meter **ExecutionPolicy** wordt gebruikt om het **Alles ondertekend** -beleid op te geven. De **bereik** parameter geeft u het **waardeproces** op. Als u de instellingen voor het uitvoerings beleid wilt weer geven, gebruikt u de `Get-ExecutionPolicy` cmdlet met de **lijst** parameter.

### Voor beeld 7: een script blok keren om het uit te voeren zonder het uitvoerings beleid te wijzigen

Dit voor beeld laat zien hoe u met het beleid voor het uitvoeren van **RemoteSigned** geen niet-ondertekende scripts kunt uitvoeren.

Een best practice is de code van het script te lezen en te controleren of het veilig is **voordat** u de `Unblock-File` cmdlet gebruikt. De `Unblock-File` cmdlet verwijdert scripts zodat ze kunnen worden uitgevoerd, maar het uitvoerings beleid wordt niet gewijzigd.

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

De `Set-ExecutionPolicy` para meter **ExecutionPolicy** wordt gebruikt om het **RemoteSigned** -beleid op te geven. Het beleid wordt ingesteld voor het standaard bereik **LocalMachine**.

De `Get-ExecutionPolicy` cmdlet geeft aan dat **RemoteSigned** het effectief uitvoerings beleid voor de huidige Power shell-sessie is.

Het **Start-ActivityTracker.ps1** script wordt uitgevoerd vanuit de huidige map. Het script wordt geblokkeerd door **RemoteSigned** omdat het script geen digitale hand tekening heeft.

Voor dit voor beeld is de code van het script beoordeeld en geverifieerd als veilig om uit te voeren. De `Unblock-File` cmdlet gebruikt de para meter **Path** om het script uit te blok keren.

Als u wilt controleren of `Unblock-File` het uitvoerings beleid niet is gewijzigd, `Get-ExecutionPolicy` wordt het effectief uitvoerings beleid, **RemoteSigned**, weer gegeven.

Het script **Start-ActivityTracker.ps1** wordt uitgevoerd vanuit de huidige map. Het script wordt uitgevoerd, omdat het is gedeblokkeerd door de `Unblock-File` cmdlet.

## PARAMETERS

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExecutionPolicy

Hiermee geeft u het uitvoerings beleid op. Als er geen groeps beleid is en het uitvoerings beleid van elke scope is ingesteld op niet **gedefinieerd**, wordt het **beperkte** beleid voor alle gebruikers.

De acceptabele waarden voor het uitvoerings beleid zijn als volgt:

- **Alles ondertekend**. Vereist dat alle scripts en configuratie bestanden zijn ondertekend door een vertrouwde uitgever, met inbegrip van scripts die op de lokale computer zijn geschreven.
- **Overs Laan**. Er is niets geblokkeerd en er zijn geen waarschuwingen of prompts.
- **Standaard instelling**. Hiermee stelt u het standaard uitvoerings beleid in. **Beperkt** voor Windows-clients of **RemoteSigned** voor Windows-servers.
- **RemoteSigned**. Vereist dat alle scripts en configuratie bestanden van het Internet worden ondertekend door een vertrouwde uitgever. Het standaard uitvoerings beleid voor Windows Server-computers.
- **Beperkt**. Laadt geen configuratie bestanden of voert scripts uit. Het standaard beleid voor het uitvoeren van Windows-client computers.
- Niet **gedefinieerd**. Er is geen uitvoerings beleid ingesteld voor het bereik. Hiermee wordt een toegewezen uitvoerings beleid verwijderd uit een bereik dat niet is ingesteld door een groepsbeleid. Als het uitvoerings beleid in alle bereiken niet is **gedefinieerd**, wordt het effectief uitvoerings beleid **beperkt**.
- **Onbeperkt**. Vanaf Power shell 6,0 is dit het standaard uitvoerings beleid voor niet-Windows-computers en kan het niet worden gewijzigd. Laadt alle configuratie bestanden en voert alle scripts uit. Als u een niet-ondertekend script uitvoert dat van Internet is gedownload, wordt u gevraagd om toestemming voordat het wordt uitgevoerd.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Force

Onderdrukt alle bevestigings prompts. Wees voorzichtig met deze para meter om onverwachte resultaten te voor komen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bereik

Hiermee geeft u het bereik op dat wordt beïnvloed door een uitvoerings beleid. Het standaard bereik is **LocalMachine**.

Het effectief uitvoerings beleid wordt als volgt bepaald door de volg orde van prioriteit:

- **MachinePolicy**. Ingesteld door een groepsbeleid voor alle gebruikers van de computer.
- **User Policy**. Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.
- **Proces**. Alleen van invloed op de huidige Power shell-sessie.
- **CurrentUser**. Alleen van invloed op de huidige gebruiker.
- **LocalMachine**. Het standaard bereik dat van invloed is op alle gebruikers van de computer.

Het **proces** bereik is alleen van invloed op de huidige Power shell-sessie. Het uitvoerings beleid wordt opgeslagen in de omgevings variabele in `$env:PSExecutionPolicyPreference` plaats van het REGI ster. Wanneer de Power shell-sessie wordt gesloten, worden de variabele en de waarde verwijderd.

Uitvoerings beleid voor het bereik van **CurrentUser** wordt geschreven naar de register component **HKEY_LOCAL_USER**.

Uitvoerings beleid voor het **LocalMachine** -bereik wordt geschreven naar de register component **HKEY_LOCAL_MACHINE**.

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Microsoft.PowerShell.ExecutionPolicy, System. String

U kunt een uitvoerings beleid of een teken reeks die de naam van een uitvoerings beleid bevat, door sluizen naar `Set-ExecutionPolicy` .

## UITVOER

### Geen

`Set-ExecutionPolicy` retourneert geen uitvoer.

## OPMERKINGEN

`Set-ExecutionPolicy` de **MachinePolicy** -en **User Policy** -scopes worden niet gewijzigd, omdat deze zijn ingesteld door groeps beleid.

`Set-ExecutionPolicy` overschrijft een groepsbeleid, zelfs niet als de gebruikers voorkeur meer beperkend is dan het beleid.

Als de groepsbeleid **script uitvoering inschakelen** is ingeschakeld voor de computer of gebruiker, wordt de gebruikers voorkeur opgeslagen, maar dit is niet effectief. In Power shell wordt een bericht weer gegeven waarin het conflict wordt uitgelegd.

## GERELATEERDE KOPPELINGEN

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Group_Policy_Settings](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Get-Child item](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Invoke-opdracht](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Blok kering van bestand opheffen](../Microsoft.PowerShell.Utility/Unblock-File.md)

