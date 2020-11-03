---
description: Hierin wordt beschreven hoe u aangepaste standaard waarden instelt voor cmdlet-para meters en geavanceerde functies.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: 0e19241549b53bac9a57de183f2896985f94d116
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252280"
---
# <a name="about-parameters-default-values"></a>Over de standaard waarden van para meters

## <a name="short-description"></a>Korte beschrijving

Hierin wordt beschreven hoe u aangepaste standaard waarden instelt voor cmdlet-para meters en geavanceerde functies.

## <a name="long-description"></a>Lange beschrijving

Met de `$PSDefaultParameterValues` Voorkeurs variabele kunt u aangepaste standaard waarden opgeven voor een cmdlet of een geavanceerde functie. Cmdlets en geavanceerde functies gebruiken de aangepaste standaard waarde tenzij u een andere waarde in de opdracht opgeeft.

De auteurs van cmdlets en geavanceerde functies stellen standaard waarden in voor de para meters. Normaal gesp roken zijn de standaard waarden handig, maar ze zijn mogelijk niet geschikt voor alle omgevingen.

Deze functie is vooral nuttig wanneer u dezelfde alternatieve parameter waarde moet opgeven bijna elke keer dat u de opdracht gebruikt of wanneer een bepaalde parameter waarde moeilijk te onthouden is, zoals de naam van een e-mail server of project-GUID.

Als de gewenste standaard waarde zoals verwacht varieert, kunt u een script blok opgeven dat verschillende standaard waarden voor een para meter onder verschillende omstandigheden levert.

`$PSDefaultParameterValues` is geïntroduceerd in Power Shell 3,0.

## <a name="syntax"></a>Syntax

De `$PSDefaultParameterValues` variabele is een hash-tabel die de indeling van sleutels valideert als object type **System. Management. Automation. DefaultParameterDictionary**. De hash-tabel bevat **sleutel-** waardeparen. Een **sleutel** heeft de indeling `CmdletName:ParameterName` . Een **waarde** is de **DefaultValue** of **script Block** die is toegewezen aan de sleutel.

De syntaxis van de `$PSDefaultParameterValues` Voorkeurs variabele is als volgt:

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

Joker tekens zijn toegestaan in de waarden van de **cmdlet** -en **para meter** .

Als u een specifieke **sleutel/waarde-** paar wilt instellen, wijzigen, toevoegen of verwijderen `$PSDefaultParameterValues` , gebruikt u de methoden om een standaard-hash-tabel te bewerken. Bijvoorbeeld de methoden **toevoegen** en **verwijderen** . Met deze methoden worden andere waarden in de hash-tabel niet overschreven.

Er is een andere syntaxis die geen bestaande hash-tabel overschrijft `$PSDefaultParameterValues` . Als u een specifieke **sleutel/waarde-** paar wilt toevoegen of wijzigen, gebruikt u de volgende syntaxis:

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

De **cmdletnaam** moet de naam zijn van een cmdlet of de naam van een geavanceerde functie die gebruikmaakt van het kenmerk **CmdletBinding** . U kunt niet gebruiken `$PSDefaultParameterValues` om standaard waarden voor scripts of eenvoudige functies op te geven.

De **DefaultValue** kan een object of een script blok zijn. Als de waarde een script blok is, wordt het script blok door Power shell geëvalueerd en wordt het resultaat gebruikt als waarde voor de para meter. Wanneer de opgegeven para meter een script blok waarde accepteert, plaatst u de script blok waarde in een tweede set accolades, zoals:

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

Raadpleeg de volgende documenten voor meer informatie:

- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Preference_Variables](about_Preference_Variables.md)

## <a name="examples"></a>Voorbeelden

### <a name="how-to-set-psdefaultparametervalues"></a>\$PSDefaultParameterValues instellen

`$PSDefaultParameterValues` is een voorkeurs variabele, zodat deze alleen bestaat in de sessie waarin deze is ingesteld. Er is geen standaard waarde.

Als u wilt instellen `$PSDefaultParameterValues` , typt u de naam van de variabele en een of meer **sleutel-** waardeparen. Als u een andere `$PSDefaultParameterValues` opdracht uitvoert, wordt de bestaande hash-tabel overschreven.

Zie [waarden toevoegen aan \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) of informatie over het [wijzigen van waarden in \$ PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues)voor voor beelden van het wijzigen van **sleutel/waarde** -paren zonder bestaande waarden van hash-tabellen te overschrijven.

Als u wilt opslaan `$PSDefaultParameterValues` voor toekomstige sessies, voegt `$PSDefaultParameterValues` u een opdracht toe aan uw Power shell-profiel. Zie [about_Profiles](about_Profiles.md)voor meer informatie.

#### <a name="set-a-custom-default-value"></a>Een aangepaste standaard waarde instellen

Met het **sleutel/waarde-** paar wordt de `Send-MailMessage:SmtpServer` sleutel ingesteld op een aangepaste standaard waarde van **Server123**.

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a>Standaard waarden voor meerdere para meters instellen

Als u standaard waarden wilt instellen voor meerdere para meters, scheidt u elk **sleutel/waarde** -paar met een punt komma ( `;` ). De `Send-MailMessage:SmtpServer` `Get-WinEvent:LogName` sleutels en worden ingesteld op aangepaste standaard waarden.

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a>Joker tekens en switch parameters gebruiken

De cmdlet-en parameter namen mogen joker tekens bevatten. Gebruik `$True` en `$False` om waarden in te stellen voor switch parameters, zoals **uitgebreid**. De para meter **uitgebreid** van de algemene para meter is ingesteld op `$True` voor alle opdrachten.

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a>Een matrix gebruiken voor de standaard waarde

Als een para meter meerdere waarden kan accepteren, een matrix, kunt u meerdere waarden instellen als de standaard waarden. De standaard waarde van de `Invoke-Command:ComputerName` sleutel wordt ingesteld op een matrix waarde van **Server01** en **Server02**.

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a>Een script blok gebruiken

U kunt een script blok gebruiken om verschillende standaard waarden op te geven voor een para meter onder verschillende omstandigheden. Power shell evalueert het script blok en gebruikt het resultaat als de standaard parameter waarde.

De `Format-Table:AutoSize` sleutel stelt die para meter in op de standaard waarde **waar**. De `If` instructie bevat een voor waarde die de `$host.Name` moet de Power shell-console, **ConsoleHost**.

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

Als een para meter een script blok waarde accepteert, plaatst u het script blok in een extra verzameling accolades. Wanneer Power shell het buitenste script blok evalueert, is het resultaat het interne script blok en dat is ingesteld als de standaard parameter waarde.

De `Invoke-Command:ScriptBlock` sleutel is ingesteld op de standaard waarde van het **logboek voor systeem gebeurtenissen** , omdat het script blok is inge sloten in een tweede set accolades. Het resultaat van het script blok wordt door gegeven aan de `Invoke-Command` cmdlet.

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a>\$PSDefaultParameterValues ophalen

De waarden van de hash-tabel worden weer gegeven door `$PSDefaultParameterValues` de Power shell-prompt in te voeren.

Een `$PSDefaultParameterValues` hash-tabel is ingesteld met drie **sleutel-** waardeparen.
Deze hash-tabel wordt gebruikt in de volgende voor beelden die beschrijven hoe waarden moeten worden toegevoegd, gewijzigd of verwijderd `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

Als u de waarde van een specifieke `CmdletName:ParameterName` sleutel wilt ophalen, gebruikt u de volgende syntaxis:

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

Als u bijvoorbeeld de waarde voor de sleutel wilt ophalen `Send-MailMessage:SmtpServer` .

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a>Waarden toevoegen aan \$ PSDefaultParameterValues

Als u een waarde wilt toevoegen aan `$PSDefaultParameterValues` , gebruikt u de methode **add** . Het toevoegen van een waarde heeft geen invloed op de bestaande waarden van de hash-tabel.

Gebruik een komma ( `,` ) om de **sleutel** te scheiden van de **waarde**. De volgende syntaxis laat zien hoe u de methode **add** gebruikt voor `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

De hash-tabel die in het vorige voor beeld is gemaakt, wordt bijgewerkt met een nieuwe **sleutel/waarde-** paar. Met de methode **add** wordt de `Get-Process:Name` sleutel ingesteld op de waarde **Power shell**.

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

Met de volgende syntaxis wordt hetzelfde resultaat bereikt.

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

Met de `$PSDefaultParameterValues` variabele wordt de bijgewerkte hash-tabel weer gegeven. De `Get-Process:Name` sleutel is toegevoegd.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a>Waarden verwijderen uit \$ PSDefaultParameterValues

Als u een waarde uit wilt verwijderen `$PSDefaultParameterValues` , gebruikt u de methode **verwijderen** van hash-tabellen. Het verwijderen van een waarde heeft geen invloed op de bestaande waarden van de hash-tabel.

De volgende syntaxis laat zien hoe u de methode **Remove** gebruikt op `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

In dit voor beeld wordt de in het vorige voor beeld gemaakte hashtabel bijgewerkt om een **sleutel/waarde-** paar te verwijderen. Met de methode **Remove** wordt de `Get-Process:Name` sleutel verwijderd.

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

Met de `$PSDefaultParameterValues` variabele wordt de bijgewerkte hash-tabel weer gegeven. De `Get-Process:Name` sleutel is verwijderd.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a>Waarden in \$ PSDefaultParameterValues wijzigen

Wijzigingen in een specifieke waarde zijn niet van invloed op bestaande waarden van hash-tabellen. Als u een specifiek **sleutel/waardepaar** wilt wijzigen in `$PSDefaultParameterValues` , gebruikt u de volgende syntaxis:

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

In dit voor beeld wordt de in het vorige voor beeld gemaakte hash-tabel bijgewerkt om een **sleutel/waarde-** paar te wijzigen. Met de volgende opdracht wordt de `Send-MailMessage:SmtpServer` sleutel gewijzigd in een nieuwe waarde van **ServerXYZ**.

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

Met de `$PSDefaultParameterValues` variabele wordt de bijgewerkte hash-tabel weer gegeven. De `Send-MailMessage:SmtpServer` sleutel is gewijzigd in een nieuwe waarde.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a>PSDefaultParameterValues uitschakelen en opnieuw inschakelen \$

U kunt tijdelijk uitschakelen en vervolgens weer inschakelen `$PSDefaultParameterValues` .
Uitschakelen `$PSDefaultParameterValues` is handig als u scripts uitvoert waarvoor verschillende standaard parameter waarden nodig zijn.

Als u wilt uitschakelen `$PSDefaultParameterValues` , voegt u een sleutel toe `Disabled` met de waarde **True**. De waarden in blijven `$PSDefaultParameterValues` behouden, maar zijn niet effectief.

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

Met de volgende syntaxis wordt hetzelfde resultaat bereikt.

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

De `$PSDefaultParameterValues` variabele geeft de bijgewerkte hash-tabel weer met de waarde voor de `Disabled` sleutel.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

Als u het opnieuw wilt inschakelen `$PSDefaultParameterValues` , verwijdert u de **Uitgeschakelde** sleutel of wijzigt u de waarde van de **Uitgeschakelde** sleutel in `$False` . De vorige waarde van `$PSDefaultParameterValues` is opnieuw effectief.

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

Met de volgende syntaxis wordt hetzelfde resultaat bereikt.

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

Met de `$PSDefaultParameterValues` variabele wordt de bijgewerkte hash-tabel weer gegeven. Wanneer de methode **Remove** wordt gebruikt, `Disabled` wordt de sleutel uit de uitvoer verwijderd.
Als de alternatieve syntaxis is gebruikt om opnieuw in te scha kelen `$PSDefaultParameterValues` , `Disabled` wordt de sleutel weer gegeven als **Onwaar**.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a>Zie ook

[about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Script_Blocks](about_Script_Blocks.md)
