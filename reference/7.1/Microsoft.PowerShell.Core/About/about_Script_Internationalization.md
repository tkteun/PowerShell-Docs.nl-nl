---
description: Hierin worden de functies voor script intertalen beschreven waarmee scripts eenvoudig berichten en instructies voor gebruikers worden weer gegeven in de taal van de gebruikers interface (UI).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 9506500c8e689933a5826504c344a949eb24a53b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252903"
---
# <a name="about-script-internationalization"></a>Over script intertalen

## <a name="short-description"></a>Korte beschrijving
Hierin worden de functies voor script intertalen beschreven waarmee scripts eenvoudig berichten en instructies voor gebruikers worden weer gegeven in de taal van de gebruikers interface (UI).

## <a name="long-description"></a>Lange beschrijving

Met de functies voor intertalen in Power shell-script kunt u gebruikers in de hele wereld beter van dienst zijn door Help-en gebruikers berichten in de taal van de gebruiker weer te geven.

De functies voor script intertalen voeren een query uit op de UI-cultuur van het besturings systeem tijdens de uitvoering, importeer de juiste vertaalde teken reeksen en geef deze weer in de gebruiker. Met de sectie gegevens kunt u tekst reeksen gescheiden van code opslaan, zodat ze gemakkelijk kunnen worden geïdentificeerd en geëxtraheerd. Een nieuwe cmdlet, `ConvertFrom-StringData` , converteert teken reeksen naar woordenboek achtige hash-tabellen om de vertaling te vergemakkelijken.

Power shell bevat de volgende functies ter ondersteuning van internationale Help-tekst:

- Een gegevens sectie waarmee tekst reeksen worden gescheiden van code-instructies. Zie [about_Data_Sections](about_Data_Sections.md)voor meer informatie over de sectie gegevens.

- Nieuwe automatische variabelen `$PSCulture` en `$PSUICulture` . `$PSCulture` slaat de naam op van de taal van de gebruikers interface die op het systeem wordt gebruikt voor elementen zoals de datum, tijd en valuta. De `$PSUICulture` variabele bevat de naam van de taal van de gebruikers interface die op het systeem wordt gebruikt voor elementen van gebruikers interfaces, zoals menu's en tekst teken reeksen.

- Een cmdlet, `ConvertFrom-StringData` , waarmee tekst reeksen worden geconverteerd naar woordenboek achtige hash-tabellen om de vertaling te vergemakkelijken. Zie [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)voor meer informatie.

- Een nieuw bestands type, `.psd1` dat vertaalde teken reeksen opslaat. De `.psd1` bestanden worden opgeslagen in taalspecifieke submappen van de script Directory.

- Een cmdlet, `Import-LocalizedData` , waarmee de vertaalde teken reeksen voor een opgegeven taal worden geïmporteerd in een script tijdens runtime. Met deze cmdlet worden teken reeksen in een door Windows ondersteunde taal herkend en geïmporteerd. Zie [import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)voor meer informatie.

### <a name="the-data-section-storing-default-strings"></a>De sectie gegevens: standaard reeksen opslaan

Gebruik een gegevens sectie in het script om de teken reeksen in de standaard taal op te slaan. Rang Schik de teken reeksen in sleutel-waardeparen in een hier-teken reeks. Elke sleutel/waarde-paar moet op een afzonderlijke regel staan. Als u opmerkingen toevoegt, moeten de opmerkingen op afzonderlijke regels staan.

Met de `ConvertFrom-StringData` cmdlet worden de sleutel-waardeparen in de hier-teken reeks geconverteerd naar een woordenboek achtige hash-tabel die is opgeslagen in de waarde van de variabele gegevens sectie.

In het volgende voor beeld bevat de sectie gegevens van het `World.ps1` script de English-United Staten (en-US) die zijn ingesteld op prompt berichten voor een script. `ConvertFrom-StringData`Met de cmdlet worden de teken reeksen omgezet in een hash-tabel en opgeslagen in de `$msgtable` variabele.

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.

### <a name="psd1-files-storing-translated-strings"></a>PSD1-bestanden: vertaalde teken reeksen opslaan

Sla de script berichten voor elke taal van de gebruikers interface op in afzonderlijke tekst bestanden met dezelfde naam als het script en de `.psd1` bestandsnaam extensie. Sla de bestanden in submappen van de script Directory op met namen van cultures in de volgende indeling:

`<language>-<region>`

Voor beelden: de-DE, AR-SA en zh-Hans

Als het `World.ps1` script bijvoorbeeld wordt opgeslagen in de `C:\Scripts` map, maakt u een mapstructuur die er ongeveer als volgt uitziet:

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

Het `World.psd1` bestand in de subdirectory van de script Directory bevat mogelijk de volgende instructie:

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

Het `World.psd1` bestand in de subdirectory AR-SA van de script Directory kan er ook als volgt uitzien:

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a>Import-LocalizedData: dynamische ophalen van vertaalde teken reeksen

Als u de teken reeksen wilt ophalen in de taal van de gebruikers interface van de huidige gebruiker, gebruikt u de `Import-LocalizedData` cmdlet.

`Import-LocalizedData` Hiermee wordt de waarde van de `$PSUICulture` Automatische variabele opgehaald en wordt de inhoud van de `<script-name>.psd1` bestanden in de submap die overeenkomt met de `$PSUICulture` waarde geïmporteerd. Vervolgens wordt de geïmporteerde inhoud opgeslagen in de variabele die is opgegeven door de waarde van de para meter **BindingVariable** .

```powershell
Import-LocalizedData -BindingVariable msgTable
```

Als de `Import-LocalizedData` opdracht bijvoorbeeld wordt weer gegeven in het `C:\Scripts\World.ps1` script en de waarde van `$PSUICulture` is ' AR-SA ', `Import-LocalizedData` zoekt het volgende bestand:

`C:\Scripts\ar-SA\World.psd1`

Vervolgens worden de Arabische teken reeksen uit het bestand in de variabele geïmporteerd `$msgTable` , waarbij alle standaard reeksen worden vervangen die kunnen worden gedefinieerd in de sectie gegevens van het `World.ps1` script.

Als gevolg hiervan `$msgTable` worden de berichten in het Arabisch weer gegeven wanneer het script de variabele gebruikt om gebruikers berichten weer te geven.

Het volgende script geeft bijvoorbeeld het bericht ' Geef uw gebruikers naam op ' in het Arabisch op:

```powershell
if (!($username)) { $msgTable.promptMsg }
```

Als `Import-LocalizedData` er geen bestand kan worden gevonden `.psd1` dat overeenkomt met de waarde van `$PSUIculture` , wordt de waarde van `$msgTable` niet vervangen en wordt de aanroep om `$msgTable.promptMsg` de terugval-en-US-teken reeksen weer te geven.

## <a name="examples"></a>Voorbeelden

In dit voor beeld ziet u hoe de script functies voor meerdere talen worden gebruikt in een script om een dag van de week weer te geven voor gebruikers in de taal die op de computer is ingesteld.

Hier volgt een volledige lijst van het Sample1.ps1-script bestand.

Het script begint met een gegevens sectie met de naam Day ($Day) die een `ConvertFrom-StringData` opdracht bevat. De expressie `ConvertFrom-StringData` die wordt verzonden naar is een hier-teken reeks die de namen van de dagen in de standaard gebruikersinterface cultuur, en-us, in sleutel/waarde-paren bevat. Met de `ConvertFrom-StringData` cmdlet worden de sleutel-waardeparen in de hier-teken reeks geconverteerd naar een hash-tabel en vervolgens opgeslagen in de waarde van de `$Day` variabele.

De `Import-LocalizedData` opdracht importeert de inhoud van het `.psd1` bestand in de map die overeenkomt met de waarde van de `$PSUICulture` Automatische variabele en slaat deze vervolgens op in de `$Day` variabele. vervolgens worden de waarden van `$Day` die zijn gedefinieerd in de sectie gegevens vervangen.

Met de overige opdrachten worden de teken reeksen in een matrix geladen en weer gegeven.

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

De `.psd1` bestanden die het script ondersteunen, worden opgeslagen in submappen van de script Directory met namen die overeenkomen met de `$PSUICulture` waarden.

Hieronder vindt u een volledige lijst met `.\de-DE\sample1.psd1` :

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

Als u Sample.ps1 uitvoert op een systeem waarop de waarde van `$PSUICulture` is, is de uitvoer van het script:

```Output
Heute ist Freitag
```

## <a name="see-also"></a>Zie ook

- [about_Data_Sections](about_Data_Sections.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

