---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: b6147b35a8818cf448b1e23f5458550d1c6e5c50
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2020
ms.locfileid: "93251697"
---
# Start-Process

## SAMENVATTING
Start een of meer processen op de lokale computer.

## SYNTAXIS

### Standaard (standaard instelling)

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [<CommonParameters>]
```

### Useshellexecute worden

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [<CommonParameters>]
```

## BESCHRIJVING

De `Start-Process` cmdlet start een of meer processen op de lokale computer. `Start-Process`Maakt standaard een nieuw proces dat alle omgevings variabelen overneemt die in het huidige proces zijn gedefinieerd.

Als u het programma wilt opgeven dat in het proces wordt uitgevoerd, voert u een uitvoerbaar bestand of script bestand in of een bestand dat kan worden geopend met behulp van een programma op de computer. Als u een niet-uitvoerbaar bestand opgeeft, `Start-Process` wordt het programma gestart dat is gekoppeld aan het bestand, vergelijkbaar met de `Invoke-Item` cmdlet.

U kunt de para meters van gebruiken `Start-Process` om opties op te geven, zoals het laden van een gebruikers profiel, het starten van het proces in een nieuw venster of het gebruik van alternatieve referenties.

## VOORBEELDEN

### Voor beeld 1: een proces starten dat gebruikmaakt van standaard waarden

In dit voor beeld wordt een proces gestart dat gebruikmaakt `Sort.exe` van het bestand in de huidige map. De opdracht gebruikt alle standaard waarden, met inbegrip van de standaard venster stijl, werkmap en referenties.

```powershell
Start-Process -FilePath "sort.exe"
```

### Voor beeld 2: een tekst bestand afdrukken

In dit voor beeld wordt een proces gestart waarmee het bestand wordt afgedrukt `C:\PS-Test\MyFile.txt` .

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### Voor beeld 3: een proces starten om items naar een nieuw bestand te sorteren

In dit voor beeld wordt een proces gestart waarmee items in het bestand worden gesorteerd `Testsort.txt` en de gesorteerde items in de bestanden worden geretourneerd `Sorted.txt` . Eventuele fouten worden naar het `SortError.txt` bestand geschreven.

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

De para meter **UseNewEnvironment** geeft aan dat het proces wordt uitgevoerd met de eigen omgevings variabelen.

### Voor beeld 4: een proces in een gemaximaliseerd venster starten

In dit voor beeld wordt het `Notepad.exe` proces gestart. Het maximaliseert het venster en behoudt het venster totdat het proces is voltooid.

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### Voor beeld 5: Power shell starten als beheerder

In dit voor beeld wordt Power shell gestart met de optie **als administrator uitvoeren** .

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### Voor beeld 6: verschillende woorden gebruiken om een proces te starten

In dit voor beeld ziet u hoe u de termen vindt die kunnen worden gebruikt bij het starten van een proces. De beschik bare termen worden bepaald door de bestandsnaam extensie van het bestand dat in het proces wordt uitgevoerd.

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

In het voor beeld wordt gebruikt `New-Object` om een **System. Diagnostics. ProcessStartInfo** -object te maken voor **PowerShell.exe** , het bestand dat in het Power Shell-proces wordt uitgevoerd. De eigenschap **verbs** van het object **ProcessStartInfo** laat zien dat u de werk woorden **Open** en **runas** kunt gebruiken met `PowerShell.exe` , of met elk proces waarmee een bestand wordt uitgevoerd `.exe` .

### Voor beeld 7: argumenten opgeven voor het proces

Met beide opdrachten start u de Windows-opdracht-interpreter, waarbij een opdracht wordt uitgegeven `dir` in de `Program Files` map. Omdat deze mapnaam een spatie bevat, moet de waarde tussen dubbele aanhalings tekens worden geplaatst.
Houd er rekening mee dat met de eerste opdracht een teken reeks wordt opgegeven als **argument List**. De tweede opdracht is een teken reeks matrix.

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## PARAMETERS

### -Argument List

Hiermee geeft u para meters of parameter waarden op die moeten worden gebruikt wanneer deze cmdlet het proces start. Argumenten kunnen worden geaccepteerd als één teken reeks met de argumenten gescheiden door spaties, of als een matrix met teken reeksen gescheiden door komma's.

Als para meters of parameter waarden een spatie bevatten, moeten deze tussen dubbele aanhalings tekens worden geplaatst. Zie [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. De cmdlet maakt standaard gebruik van de referenties van de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u het pad en de bestands naam op van het programma dat in het proces wordt uitgevoerd. Voer de naam in van een uitvoerbaar bestand of van een document, zoals een `.txt` of `.doc` -bestand, dat is gekoppeld aan een programma op de computer. Deze parameter is vereist.

Als u alleen een bestands naam opgeeft, gebruikt u de para meter **variabele workingdirectory** om het pad op te geven.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LoadUserProfile

Geeft aan dat met deze cmdlet het Windows-gebruikers profiel wordt geladen dat is opgeslagen in de `HKEY_USERS` register sleutel voor de huidige gebruiker.

Deze para meter heeft geen invloed op de Power shell-profielen. Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Outnewwindow

Start het nieuwe proces in het huidige console venster. Standaard wordt in Power shell een nieuw venster geopend.

U kunt de para meters voor niet- **NewWindow** en **WindowStyle** niet gebruiken in dezelfde opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een proces object voor elk proces dat door de cmdlet is gestart. Deze cmdlet genereert standaard geen uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardError

Hiermee geeft u een bestand. Met deze cmdlet worden fouten verzonden die door het proces worden gegenereerd naar een bestand dat u opgeeft.
Voer het pad en de bestands naam in. De fouten worden standaard weer gegeven in de-console.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardInput

Hiermee geeft u een bestand. Met deze cmdlet wordt de invoer van het opgegeven bestand gelezen. Voer het pad en de bestands naam van het invoer bestand in. Het proces krijgt standaard de invoer van het toetsen bord.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardOutput

Hiermee geeft u een bestand. Met deze cmdlet wordt de uitvoer die door het proces is gegenereerd, verzonden naar een bestand dat u opgeeft.
Voer het pad en de bestands naam in. Standaard wordt de uitvoer in de-console weer gegeven.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseNewEnvironment

Geeft aan dat deze cmdlet nieuwe omgevings variabelen gebruikt die zijn opgegeven voor het proces. Standaard wordt het gestarte proces uitgevoerd met de omgevings variabelen die zijn overgenomen van het bovenliggende proces.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verb

Hiermee geeft u een term op die moet worden gebruikt wanneer deze cmdlet het proces start. De beschik bare termen worden bepaald door de bestandsnaam extensie van het bestand dat in het proces wordt uitgevoerd.

In de volgende tabel ziet u de bewerkingen voor een aantal algemene proces bestands typen.

| Bestands type |                Termen                |
| --------- | ----------------------------------- |
| cmd      | Bewerken, openen, afdrukken, runas, RunAsUser |
| .exe      | Open, runas, RunAsUser              |
| .txt      | Openen, afdrukken, PrintTo                |
| .wav      | Openen, afspelen                          |

Als u de woorden wilt vinden die kunnen worden gebruikt in combi natie met het bestand dat in een proces wordt uitgevoerd, gebruikt u de `New-Object` cmdlet om een **System. Diagnostics. ProcessStartInfo** -object voor het bestand te maken. De beschik bare termen bevinden zich in de eigenschap **verbs** van het object **ProcessStartInfo** . Zie de voor beelden voor meer informatie.

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wachten

Hiermee wordt aangegeven dat met deze cmdlet wordt gewacht op het opgegeven proces en de descendanten die moeten worden voltooid voordat meer invoer wordt geaccepteerd. Met deze para meter wordt de opdracht prompt onderdrukt of wordt het venster bewaard totdat de processen zijn voltooid.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WindowStyle

Hiermee geeft u de status van het venster dat voor het nieuwe proces wordt gebruikt. De acceptabele waarden voor deze para meter zijn: **normaal** , **verborgen** , **geminimaliseerd** en **gemaximaliseerd**. De standaard waarde is **Normal**.

U kunt de para meters **WindowStyle** en **NewWindow** niet gebruiken in dezelfde opdracht.

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variabele workingdirectory

Hiermee geeft u de locatie op waar het nieuwe proces moet worden gestart. De standaard waarde is de locatie van het uitvoer bare bestand of het document dat wordt gestart. Jokertekens worden niet ondersteund. De naam van het pad mag geen tekens bevatten die als Joker teken worden geïnterpreteerd.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen, System. Diagnostics. process

Met deze cmdlet wordt een **System. Diagnostics. process** -object gegenereerd als u de para meter **PassThru** opgeeft. Anders retourneert deze cmdlet geen uitvoer.

## OPMERKINGEN

- Deze cmdlet wordt geïmplementeerd met behulp van de methode **Start** van de klasse **System. Diagnostics. process** . Zie [process. Start-methode](/dotnet/api/system.diagnostics.process.start#overloads)voor meer informatie over deze methode.

- Wanneer u **UseNewEnvironment** gebruikt in Windows, begint het nieuwe proces alleen met de standaard omgevings variabelen die voor het **computer** bereik zijn gedefinieerd. Dit is de zijde die van invloed is op de `$env:USERNAME` is ingesteld op **System**. Geen van de variabelen uit het **gebruikers** bereik is opgenomen.

## GERELATEERDE KOPPELINGEN

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Debug-proces](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Service](Start-Service.md)

[Stoppen-proces](Stop-Process.md)

[Wacht proces](Wait-Process.md)
