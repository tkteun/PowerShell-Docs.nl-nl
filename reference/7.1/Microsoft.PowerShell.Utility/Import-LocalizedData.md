---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: d19279133a42e3aea17f02348e44aec161ba5a23
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2020
ms.locfileid: "93253298"
---
# Import-LocalizedData

## SAMENVATTING
Hiermee worden taalspecifieke gegevens in scripts en functies geïmporteerd op basis van de UI-cultuur die is geselecteerd voor het besturings systeem.

## SYNTAXIS

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Import-LocalizedData` cmdlet haalt op dynamische wijze teken reeksen op uit een submap waarvan de naam overeenkomt met de taal van de gebruikers interface die is ingesteld voor de huidige gebruiker van het besturings systeem. Het is ontworpen om scripts in te scha kelen voor het weer geven van gebruikers berichten in de taal van de gebruikers interface die door de huidige gebruiker is geselecteerd.

`Import-LocalizedData``.psd1`Hiermee worden gegevens uit bestanden in taalspecifieke submappen van de script Directory geïmporteerd en opgeslagen in een lokale variabele die in de opdracht is opgegeven. De cmdlet selecteert de submap en het bestand op basis van de waarde van de `$PSUICulture` Automatische variabele. Wanneer u de lokale variabele in het script gebruikt om een gebruikers bericht weer te geven, wordt het bericht weer gegeven in de gebruikers interface taal van de gebruiker.

U kunt de para meters van gebruiken `Import-LocalizedData` om een alternatieve UI-cultuur, pad en bestands naam op te geven om ondersteunde opdrachten toe te voegen en om het fout bericht te onderdrukken dat wordt weer gegeven als de `.psd1` bestanden niet worden gevonden.

De `Import-LocalizedData` cmdlet ondersteunt het script voor de intertalen van scripts dat is geïntroduceerd in Windows Power shell 2,0. Dit initiatief is erop gericht om gebruikers wereld wijd beter van dienst te zijn door scripts in staat te stellen gebruikers berichten te laten weer geven in de taal van de gebruikers interface van de huidige gebruiker. Zie about_Script_Internationalization voor meer informatie over deze en de indeling van de `.psd1` bestanden. [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)

## VOORBEELDEN

### Voor beeld 1: tekst reeksen importeren

In dit voor beeld worden tekst reeksen in de `$Messages` variabele geïmporteerd. De standaard waarden van alle andere cmdlet-para meters worden gebruikt.

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

Als de opdracht is opgenomen in het Archives.ps1 script in de `C:\Test` map en de waarde van de `$PsUICulture` Automatische variabele is zh-cn, `Import-LocalizedData` importeert het `Archives.psd1` bestand in de map in de- `C:\test\zh-CN` `$Messages` variabele.

### Voor beeld 2: gelokaliseerde gegevens reeksen importeren

Dit voor beeld wordt uitgevoerd op de opdracht regel, niet in een script. De gelokaliseerde gegevens reeksen worden opgehaald uit het bestand Test.psd1 en weer gegeven op de opdracht regel. Omdat de opdracht niet in een script wordt gebruikt, is de **filename** -para meter vereist. De opdracht gebruikt de para meter **uiCulture** om de-en-US-cultuur op te geven.

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

`Import-LocalizedData` retourneert een hash-tabel die de gelokaliseerde gegevens reeksen bevat.

### Voor beeld 3: UI-cultuur teken reeksen importeren

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

Met deze opdracht worden tekst teken reeksen in de `$MsgTbl` variabele van een script geïmporteerd.

De para meter **uiCulture** wordt gebruikt om de cmdlet te gebruiken voor het importeren van gegevens uit het `Simple.psd1` bestand in de `ar-SA` submap van `C:\Data\Localized` .

### Voor beeld 4: gelokaliseerde gegevens in een script importeren

In dit voor beeld ziet u hoe u gelokaliseerde gegevens in een eenvoudig script gebruikt.

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

In het eerste deel van het voor beeld ziet u de inhoud van het `Test.psd1` bestand. Het bevat een `ConvertFrom-StringData` opdracht die een reeks benoemde teken reeksen converteert naar een hash-tabel. Het `Test.psd1` bestand bevindt zich in de submap en-US van de `C:\Test` map die het script bevat.

In het tweede gedeelte van het voor beeld ziet u de inhoud van het `Test.ps1` script. Het bevat een `Import-LocalizedData` opdracht waarmee de gegevens uit het overeenkomende `.psd1` bestand worden geïmporteerd in de `$Messages` variabele en een `Write-Host` opdracht waarmee een van de berichten in de `$Messages` variabele naar het hostprogramma wordt geschreven.

In het laatste deel van het voor beeld wordt het script uitgevoerd. In de uitvoer ziet u dat het juiste gebruikers bericht wordt weer gegeven in de taalset van de gebruikers interface voor de huidige gebruiker van het besturings systeem.

### Voor beeld 5: standaard teken reeksen in een script vervangen

In dit voor beeld ziet u hoe u kunt gebruiken `Import-LocalizedData` om standaard teken reeksen te vervangen die zijn gedefinieerd in de sectie gegevens van een script.

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

In dit voor beeld bevat de sectie gegevens van het TestScript.ps1 script een `ConvertFrom-StringData` opdracht waarmee de inhoud van de sectie gegevens wordt geconverteerd naar een hash-tabel en die wordt opgeslagen in de waarde van de `$UserMessages` variabele.

Het script bevat ook een `Import-LocalizedData` opdracht, waarmee een hash-tabel met vertaalde tekst reeksen uit het TestScript.psd1-bestand in de submap die wordt opgegeven door de waarde van de variabele wordt geïmporteerd `$PsUICulture` . Als de opdracht het `.psd1` bestand vindt, worden de vertaalde teken reeksen uit het bestand opgeslagen in de waarde van dezelfde `$UserMessages` variabele, waarbij de hash-tabel wordt overschreven die is opgeslagen door de logica van de gegevens sectie.

Met de derde opdracht wordt het eerste bericht in de variabele weer gegeven `$UserMessages` .

Als de `Import-LocalizedData` opdracht een `.psd1` bestand voor de `$PsUICulture` taal vindt, bevat de waarde van de `$UserMessages` variabele de vertaalde teken reeksen. Als de opdracht om welke reden dan ook mislukt, geeft de opdracht de standaard teken reeksen weer die zijn gedefinieerd in de sectie gegevens van het script.

### Voor beeld 6: fout berichten onderdrukken als de GEBRUIKERSINTERFACE cultuur niet wordt gevonden

In dit voor beeld ziet u hoe u de fout berichten onderdrukt die worden weer gegeven wanneer u `Import-LocalizedData` de mappen die overeenkomen met de gebruikers interface-cultuur van de gebruiker niet kunt vinden of geen `.psd1` bestanden voor het script in deze mappen kunt vinden.

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

U kunt de gemeen schappelijke para meter **Error Action** met de waarde SilentlyContinue gebruiken om het fout bericht te onderdrukken. Dit is vooral handig wanneer u gebruikers berichten hebt gegeven in een standaard-of terugval taal en er geen fout berichten nodig zijn.

In dit voor beeld worden twee scripts vergeleken `Day1.ps1` en Day2.ps1, die een `Import-LocalizedData` opdracht bevatten. De scripts zijn identiek, behalve dat Day2 de gemeen schappelijke para meter **Error Action** gebruikt met een waarde van `SilentlyContinue` .

De voorbeeld uitvoer toont de resultaten van het uitvoeren van beide scripts wanneer de GEBRUIKERSINTERFACE cultuur is ingesteld op `fr-BE` en er zijn geen overeenkomende bestanden of mappen voor die gebruikersinterface cultuur. `Day1.ps1` Hiermee wordt een fout bericht en een Engelse uitvoer weer gegeven. `Day2.ps1` Hiermee wordt alleen de Engelse uitvoer weer gegeven.

## PARAMETERS

### -BaseDirectory

Hiermee geeft u de basis directory op waarin de `.psd1` bestanden zich bevinden. De standaard waarde is de map waarin het script zich bevindt. `Import-LocalizedData` zoekt naar het `.psd1` bestand voor het script in een taalspecifieke submap van de basis directory.

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

### -BindingVariable

Hiermee geeft u de variabele op waarnaar de tekst teken reeksen worden geïmporteerd. Voer een variabelenaam in zonder een dollar teken ( `$` ).

In Windows Power Shell 2,0 is deze para meter vereist. In Windows Power Shell 3,0 is deze para meter optioneel. Als u deze para meter weglaat, `Import-LocalizedData` wordt een hash-tabel van de tekst teken reeksen geretourneerd. De hash-tabel wordt door gegeven aan de pijp lijn of wordt weer gegeven op de opdracht regel.

Wanneer u gebruikt `Import-LocalizedData` om standaard teken reeksen te vervangen die zijn opgegeven in de sectie gegevens van een script, wijst u de sectie gegevens toe aan een variabele en voert u de naam van de gegevens sectie variabele in de waarde van de para meter **BindingVariable** . Wanneer `Import-LocalizedData` de geïmporteerde inhoud in de **BindingVariable** opslaat, worden de standaard teken reeksen vervangen door de geïmporteerde gegevens. Als u geen standaard teken reeksen opgeeft, kunt u elke naam van een variabele selecteren.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileName

Hiermee geeft u de naam op van het gegevens bestand ( `.psd1)` dat moet worden geïmporteerd. Voer een bestands naam in. U kunt een bestands naam opgeven die niet de `.psd1` bestandsnaam extensie bevat, of u kunt de bestands naam opgeven, inclusief de `.psd1` bestandsnaam extensie. Gegevens bestanden moeten worden opgeslagen als Unicode-of UTF-8.

De **filename** -para meter is vereist wanneer `Import-LocalizedData` niet wordt gebruikt in een script.
Anders is de para meter optioneel en de standaard waarde is de basis naam van het script. U kunt deze para meter gebruiken om rechtstreeks `Import-LocalizedData` naar een ander bestand te zoeken `.psd1` .

Als bijvoorbeeld de **Bestands** naam wordt wegge laten en de script naam is FindFiles.ps1, wordt `Import-LocalizedData` gezocht naar het FindFiles.psd1-gegevens bestand.

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

### -SupportedCommand

Hiermee geeft u cmdlets en functies op waarmee alleen gegevens worden gegenereerd.

Gebruik deze para meter als u cmdlets en functies wilt gebruiken die u hebt geschreven of getest. Zie [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

Hiermee geeft u een alternatieve GEBRUIKERSINTERFACE cultuur.
De standaard instelling is de waarde van de `$PsUICulture` Automatische variabele.
Voer een GEBRUIKERSINTERFACE cultuur in `<language>-<region>` indeling in, zoals `en-US` , `de-DE` of `ar-SA` .

De waarde van de para meter **uiCulture** bepaalt de taalspecifieke submap (binnen de basis directory) waaruit `Import-LocalizedData` het `.psd1` bestand voor het script wordt opgehaald.

De cmdlet zoekt naar een submap met dezelfde naam als de waarde van de para meter **uiCulture** of de `$PsUICulture` Automatische variabele, zoals `de-DE` of `ar-SA` . Als de Directory niet kan worden gevonden of als de map geen `.psd1` bestand voor het script bevat, wordt gezocht naar een submap met de naam van de taal code, zoals de of AR. Als de submap of het bestand niet kan worden gevonden `.psd1` , mislukt de opdracht en worden de gegevens weer gegeven in de standaard taal die is opgegeven in het script.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
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

### System. Collections. hashtabel

`Import-LocalizedData` Hiermee slaat u de hash-tabel op in de variabele die wordt opgegeven door de waarde van de para meter **BindingVariable** .

## OPMERKINGEN

- `Import-LocalizedData`Lokaliseer uw gebruikers berichten voordat u deze gebruikt. Format teer de berichten voor elke land instelling (UI-cultuur) in een hash-tabel met sleutel-waardeparen en sla de hash-tabel op in een bestand met dezelfde naam als het script en de `.psd1` bestandsnaam extensie. Maak een map onder de script Directory voor elke ondersteunde UI-cultuur en sla het `.psd1` bestand op voor elke UI-cultuur in de directory met de naam van de UI-cultuur.

  U kunt bijvoorbeeld uw gebruikers berichten lokaliseren voor de land instelling en Format teren in een hash-tabel.
  Sla de hash-tabel op in een `<ScriptName>.psd1` bestand. Maak vervolgens een `de-DE` submap onder de script Directory en sla het Duitse `<ScriptName\>.psd1` bestand op in de `de-DE` submap.
  Herhaal deze methode voor elke land instelling die u ondersteunt.

- `Import-LocalizedData` Hiermee voert u een gestructureerde zoek opdracht uit voor de gelokaliseerde gebruikers berichten voor een script.

  `Import-LocalizedData` Start de zoek opdracht in de directory waarin het script bestand zich bevindt (of de waarde van de para meter **BaseDirectory** ). Vervolgens wordt gezocht in de basis directory voor een submap met dezelfde naam als de waarde van de `$PsUICulture` variabele (of de waarde van de para meter **uiCulture** ), zoals `de-DE` of `ar-SA` . Vervolgens wordt in die submap gezocht naar een `.psd1` bestand met dezelfde naam als het script (of de waarde van de **filename** -para meter).

  Als `Import-LocalizedData` u een submap met de naam van de UI-cultuur niet kunt vinden of de submap bevat geen `.psd1` bestand voor het script, zoekt het naar een `.psd1` bestand voor het script in een submap met de naam van de taal code, zoals de of AR. Als de submap of het bestand niet kan worden gevonden `.psd1` , mislukt de opdracht, worden de gegevens weer gegeven in de standaard taal in het script en wordt er een fout bericht weer gegeven waarin wordt uitgelegd dat de gegevens niet kunnen worden geïmporteerd. Als u het bericht wilt onderdrukken en niet goed wilt werken, gebruikt u de gemeen schappelijke **Error Action** -para meter met de waarde SilentlyContinue.

  Als `Import-LocalizedData` de submap en het `.psd1` bestand worden gevonden, wordt de hash-tabel met gebruikers berichten geïmporteerd in de waarde van de para meter **BindingVariable** in de opdracht. Wanneer u vervolgens een bericht uit de hash-tabel weergeeft in de variabele, wordt het gelokaliseerde bericht weer gegeven.

  Zie [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Write-host](Write-Host.md)

[Import-PowerShellDataFile](Import-PowerShellDataFile.md)

