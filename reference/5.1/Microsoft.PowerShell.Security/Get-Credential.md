---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 26c4f8c8dcc1fbd56e29f55a6a8c2e6aa37a2842
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "93253230"
---
# Get-Credential

## SAMENVATTING
Hiermee wordt een referentie object opgehaald op basis van een gebruikers naam en wacht woord.

## SYNTAXIS

### Referentieset (standaard)

```
Get-Credential [-Credential] <PSCredential> [<CommonParameters>]
```

### Berichtenset

```
Get-Credential -Message <String> [[-UserName] <String>] [<CommonParameters>]
```

## BESCHRIJVING

`Get-Credential`Met de cmdlet wordt een referentie object gemaakt voor een opgegeven gebruikers naam en wacht woord. U kunt het referentie object in beveiligings bewerkingen gebruiken.

Vanaf Power Shell 3,0 kunt u de para meter **bericht** gebruiken om een aangepast bericht op te geven in het dialoog venster waarin de gebruiker wordt gevraagd om de naam en het wacht woord.

De `Get-Credential` cmdlet vraagt de gebruiker om een wacht woord of een gebruikers naam en wacht woord. Standaard wordt er een verificatie dialoogvenster weer gegeven waarin de gebruiker wordt gevraagd. In sommige host-Program ma's, zoals de Power shell-console, kunt u echter de gebruiker vragen op de opdracht regel door een register vermelding te wijzigen. Raadpleeg de opmerkingen en voor beelden voor meer informatie over deze register vermelding.

## VOORBEELDEN

### Voorbeeld 1

```powershell
$c = Get-Credential
```

Met deze opdracht wordt een referentie object opgehaald en opgeslagen in de `$c` variabele.

Wanneer u de opdracht invoert, wordt een dialoog venster weer gegeven met een aanvraag voor een gebruikers naam en wacht woord. Wanneer u de aangevraagde informatie invoert, maakt de cmdlet een **PSCredential** -object dat de referenties van de gebruiker vertegenwoordigt en opslaat in de `$c` variabele.

U kunt het object gebruiken als invoer voor cmdlets die gebruikers verificatie aanvragen, zoals de para meters met een **referentie** parameter. Sommige providers die zijn geïnstalleerd met Power shell bieden echter geen ondersteuning voor de para meter **Credential** .

### Voorbeeld 2

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

Deze opdrachten gebruiken een referentie object dat door de `Get-Credential` cmdlet wordt geretourneerd om een gebruiker te verifiëren op een externe computer zodat deze Windows Management Instrumentation (WMI) kan gebruiken om de computer te beheren.

Met de eerste opdracht wordt een referentie object opgehaald en opgeslagen in de `$c` variabele. Met de tweede opdracht wordt het referentie object in een `Get-CimInstance` opdracht gebruikt. Met deze opdracht wordt informatie opgehaald over de schijf stations op de Server01-computer.

### Voorbeeld 3

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

Met deze opdracht wordt aangegeven hoe u een `Get-Credential` opdracht in een opdracht opneemt  `Get-CimInstance` .

Met deze opdracht wordt de `Get-CimInstance` cmdlet gebruikt om informatie over het BIOS op de Server01-computer op te halen. De para meter **Credential** wordt gebruikt voor het verifiëren van de gebruiker, Domain01\User01 en een `Get-Credential` opdracht als de waarde van de para meter **Credential** .

### Voorbeeld 4

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

In dit voor beeld wordt een referentie gemaakt die een gebruikers naam zonder domein naam bevat.

Met de eerste opdracht wordt een referentie opgehaald met de gebruikers naam gebruiker01 en opgeslagen in de `$c` variabele.
Met de tweede opdracht wordt de waarde van de eigenschap **username** van het resulterende referentie object weer gegeven.

### Voorbeeld 5

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

Met deze opdracht wordt de methode **PromptForCredential** gebruikt om de gebruiker te vragen naar de gebruikers naam en het wacht woord. Met de opdracht worden de resulterende referenties in de `$Credential` variabele opgeslagen.

De methode **PromptForCredential** is een alternatief voor het gebruik van de `Get-Credential` cmdlet. Wanneer u **PromptForCredential** gebruikt, kunt u de bijschriften, berichten en gebruikers namen opgeven die worden weer gegeven in het bericht venster.

Zie de [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) -documentatie in de SDK voor meer informatie.

### Voorbeeld 6

```powershell
Set-ItemProperty "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds" -Name ConsolePrompting -Value $true
```

In dit voor beeld ziet u hoe u het REGI ster wijzigt, zodat de gebruiker op de opdracht regel wordt gevraagd, in plaats van via een dialoog venster.

Met de opdracht wordt de register vermelding **ConsolePrompting** gemaakt en wordt de waarde ingesteld op True. Als u deze opdracht wilt uitvoeren, start u Power shell met de optie als administrator uitvoeren.

Als u een dialoog venster voor vragen wilt gebruiken, stelt u de waarde van de ConsolePrompting in op False ($false) of gebruikt `Remove-ItemProperty` u de cmdlet om deze te verwijderen.

De register vermelding ConsolePrompting werkt in sommige host-Program ma's, zoals de Power shell-console. Het werkt mogelijk niet in alle host-Program ma's.

### Voorbeeld 7

In dit voor beeld ziet u hoe u een referentie object maakt dat identiek is aan het object dat `Get-Credential` wordt geretourneerd zonder dat de gebruiker om toestemming wordt gevraagd. Voor deze methode is een wacht woord met tekst zonder opmaak vereist, wat in sommige ondernemingen de beveiligings normen kan schenden.

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

Met de eerste opdracht slaat u de naam van het gebruikers account op in de `$User` para meter. De waarde moet de indeling "Domein\gebruiker" of "ComputerName\User" hebben.

Met de tweede opdracht wordt de `ConvertTo-SecureString` cmdlet gebruikt om een veilige teken reeks te maken van een wacht woord voor onbewerkte tekst. De opdracht gebruikt de para meter **AsPlainText** om aan te geven dat de teken reeks tekst zonder opmaak is en de para meter **Force** om te bevestigen dat u de Risico's van het gebruik van onbewerkte tekst begrijpt.

De derde opdracht gebruikt de `New-Object` cmdlet om een **PSCredential** -object te maken op basis van de waarden in de `$User` `$PWord` variabelen en.

### Voorbeeld 8

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

Met deze opdracht worden de para meters **bericht** en **gebruikers naam** van de `Get-Credential` cmdlet gebruikt. Deze opdracht indeling is ontworpen voor gedeelde scripts en functies. In dit geval geeft het bericht aan de gebruiker door dat er referenties nodig zijn en zorgt u ervoor dat de aanvraag betrouwbaar is.

### Voorbeeld 9

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

Met deze opdracht wordt een referentie opgehaald van de externe computer Server01. De opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-Credential` op de externe computer. De uitvoer toont het externe beveiligings bericht dat is `Get-Credential` opgenomen in de verificatie prompt.

## PARAMETERS

### -Credential

Hiermee geeft u een gebruikers naam op voor de referentie, zoals **gebruiker01** of **Domain01\User01**. De parameter naam, `-Credential` , is optioneel.

Wanneer u de opdracht verzendt en een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven. Als u deze para meter weglaat, wordt u gevraagd om een gebruikers naam en wacht woord op te vragen.

Als u vanaf Power Shell 3,0 een gebruikers naam zonder domein opgeeft, wordt `Get-Credential` er niet langer een back slash voor de naam ingevoegd.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bericht

Hiermee geeft u een bericht dat wordt weer gegeven in de verificatie prompt. Deze para meter is ontworpen voor gebruik in een functie of script. U kunt het bericht gebruiken om uitleg te geven over de gebruiker waarom u referenties aanvraagt en hoe deze worden gebruikt.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GebruikersNaam

Hiermee geeft u een gebruikers naam op. De verificatie prompt vraagt een wacht woord op voor de gebruikers naam. De gebruikers naam is standaard leeg en de verificatie prompt vraagt om een gebruikers naam en wacht woord.

Wanneer de verificatie prompt wordt weer gegeven in een dialoog venster, kan de gebruiker de opgegeven gebruikers naam bewerken.
De gebruiker kan echter de gebruikers naam niet wijzigen wanneer de prompt wordt weer gegeven op de opdracht regel. Wanneer u deze para meter in een gedeelde functie of een script gebruikt, moet u rekening houden met alle mogelijke presentaties.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSCredential

`Get-Credential` retourneert een referentie object.

## OPMERKINGEN

U kunt het **PSCredential** -object gebruiken dat `Get-Credential` maakt in cmdlets die gebruikers verificatie aanvragen, zoals de para meters met een **referentie** parameter.

De verificatie prompt wordt standaard weer gegeven in een dialoog venster. Als u de verificatie prompt wilt weer geven op de opdracht regel, voegt u de register vermelding **ConsolePrompting** ( `HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting` ) toe en stelt u de waarde in op **True**.
Als de register vermelding **ConsolePrompting** niet bestaat of als de bijbehorende waarde False is, wordt de verificatie prompt weer gegeven in een dialoog venster. Zie de voor beelden voor instructies.

De register vermelding **ConsolePrompting** werkt in de Power shell-console, maar werkt niet in alle host-Program ma's.

Het heeft bijvoorbeeld geen effect in Power shell Integrated Scripting Environment (ISE). Voor informatie over het effect van de register vermelding **ConsolePrompting** raadpleegt u de Help-onderwerpen voor het gast programma.

De **referentie** parameter wordt niet ondersteund door alle providers die met Power shell zijn geïnstalleerd.
Vanaf Power Shell 3,0 wordt het ondersteund op Select-cmdlets, zoals de `Get-Content` `New-PSDrive` cmdlets en.

## GERELATEERDE KOPPELINGEN

[PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
