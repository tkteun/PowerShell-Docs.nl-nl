---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: a5f65a70ccb97db5338456cca50309b593b900c1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249689"
---
# ConvertFrom-StringData

## SAMENVATTING
Hiermee wordt een teken reeks met een of meer sleutel-en waardeparen geconverteerd naar een hash-tabel.

## SYNTAXIS

### Alles

```
ConvertFrom-StringData [-StringData] <String> [[-Delimiter] <Char>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `ConvertFrom-StringData` cmdlet wordt een teken reeks met een of meer sleutel-en waardeparen geconverteerd naar een hash-tabel. Omdat elke sleutel/waarde-paar op een afzonderlijke regel moet staan, worden hier vaak de invoer gegevens gebruikt. Standaard moet de **sleutel** worden gescheiden van de **waarde** met een teken () van het gelijkteken ( `=` ).

De `ConvertFrom-StringData` cmdlet wordt beschouwd als een veilige cmdlet die kan worden gebruikt in de `DATA` sectie van een script of functie. Bij gebruik in een `DATA` sectie moet de inhoud van de teken reeks voldoen aan de regels voor een gegevens sectie. Zie [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md)voor meer informatie.

`ConvertFrom-StringData` ondersteunt escape-teken reeksen die zijn toegestaan door conventionele hulpprogram ma's voor machine vertalingen. Dat wil zeggen dat de cmdlet backslashes () kan interpreteren `\` als escape tekens in de teken reeks gegevens met behulp van de [methode regex. unesc](/dotnet/api/system.text.regularexpressions.regex.unescape), in plaats van het Power shell apostroffen-teken ( \` ) dat normaal gesp roken het einde van een regel in een script zou Signa leren. In de teken reeks die hier is, werkt het apostroffen-teken niet. U kunt ook een letterlijke back slash in uw resultaten behouden door deze te escapen met een voor gaande back slash, bijvoorbeeld: `\\` . Back slash-tekens, zoals die vaak worden gebruikt in bestands paden, kunnen worden weer gegeven als ongeldige escape reeksen in uw resultaten.

Power shell 7 voegt de para meter **scheidings teken** toe.

## VOORBEELDEN

### Voor beeld 1: een enkel aanhalings teken naar een hash-tabel converteren

In dit voor beeld wordt een teken reeks met enkele aanhalings tekens van gebruikers berichten geconverteerd naar een hash-tabel. In een teken reeks met enkele aanhalings tekens worden waarden niet vervangen door variabelen en expressies worden niet geëvalueerd.
`ConvertFrom-StringData`Met de cmdlet wordt de waarde in de `$Here` variabele geconverteerd naar een hash-tabel.

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### Voor beeld 2: teken reeks gegevens converteren met een ander scheidings teken

In dit voor beeld ziet u hoe u teken reeks gegevens converteert die gebruikmaken van een ander teken als scheidings tekens. In dit voor beeld wordt de teken reeks gegevens gebruikt als het `|` scheidings teken ().

```powershell
$StringData = @'
color|red
model|coupe
year|1965
condition|mint
'@
$carData = ConvertFrom-StringData -StringData $StringData -Delimiter '|'
$carData
```

```Output
Name                           Value
----                           -----
condition                      mint
model                          coupe
color                          red
year                           1965
```

### Voor beeld 3: een hier een teken reeks converteren met een opmerking

In dit voor beeld wordt een hier-teken reeks geconverteerd die een opmerking en meerdere sleutel-waardeparen in een hash-tabel bevat.

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

De waarde van de para meter **StringData** is een hier-teken reeks, in plaats van een variabele die een hier-teken reeks bevat. Beide indelingen zijn geldig. De volgende teken reeks bevat een opmerking over een van de teken reeksen.
`ConvertFrom-StringData` opmerkingen met één regel worden genegeerd, maar het `#` teken moet het eerste niet-spatie teken op de regel zijn. Alle tekens op de regel na de `#` worden genegeerd.

### Voor beeld 4: een teken reeks converteren naar een hash-tabel

In dit voor beeld wordt een reguliere teken reeks met dubbele aanhalings tekens (geen hier een teken reeks) geconverteerd naar een hash-tabel en opgeslagen in de `$A` variabele.

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

Om te voldoen aan de voor waarde dat elke sleutel waarde-paar op een afzonderlijke regel moet staan, gebruikt de teken reeks het Power shell-teken voor nieuwe regels ( \` n) om de paren van elkaar te scheiden.

### Voor beeld 5: ConvertFrom-StringData gebruiken in de sectie gegevens van een script

In dit voor beeld ziet u een `ConvertFrom-StringData` opdracht die wordt gebruikt in de sectie data van een script.
De instructies onder de sectie gegevens geven de tekst weer voor de gebruiker.

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

Omdat de tekst namen van variabelen bevat, moet deze worden inge sloten in een teken reeks met enkele aanhalings tekens, zodat de variabelen letterlijk worden geïnterpreteerd en niet worden uitgevouwen. Variabelen zijn niet toegestaan in de sectie **gegevens** .

### Voor beeld 6: de pijplijn operator gebruiken om een teken reeks door te geven

Dit voor beeld laat zien dat u een pijplijn operator () kunt gebruiken `|` voor het verzenden van een teken reeks naar `ConvertFrom-StringData` . De waarde van de `$Here` variabele wordt naar het `ConvertFrom-StringData` resultaat in de `$Hash` variabele geleid.

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### Voor beeld 7: Escape tekens gebruiken om nieuwe lijnen en retour tekens toe te voegen

In dit voor beeld ziet u het gebruik van escape tekens voor het maken van nieuwe regels en het retour neren van tekens in de bron gegevens. De escape-teken reeks `\n` wordt gebruikt voor het maken van nieuwe regels in een tekst blok dat is gekoppeld aan een naam of item in de resulterende hash-tabel.

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### Voor beeld 8: back slash-escape teken gebruiken om een bestandspad correct weer te geven

In dit voor beeld ziet u hoe u het escape-teken van back slash in de teken reeks gegevens kunt gebruiken om te zorgen dat een bestandspad correct kan worden weer gegeven in de resulterende `ConvertFrom-StringData` hash-tabel. De dubbele back slash zorgt ervoor dat de letterlijke back slash-tekens correct worden weer gegeven in de hash-tabel uitvoer.

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## PARAMETERS

### -StringData

Geeft de teken reeks die moet worden geconverteerd. U kunt deze para meter of pipe een teken reeks gebruiken voor `ConvertFrom-StringData` . De parameter naam is optioneel.

De waarde van deze para meter moet een teken reeks zijn die een of meer sleutel-waardeparen bevat. Elk sleutel-waardepaar moet zich op een afzonderlijke regel behoren of elk paar moet worden gescheiden door een nieuwe teken reeks ( \` n).

U kunt opmerkingen toevoegen aan de teken reeks, maar de opmerkingen mogen zich niet op dezelfde regel bevindt als een sleutel/waarde-paar. `ConvertFrom-StringData` opmerkingen over één regel worden genegeerd. Het `#` teken moet het eerste niet-spatie teken op de regel zijn. Alle tekens op de regel na de `#` worden genegeerd. De opmerkingen worden niet opgenomen in de hash-tabel.

Een hier-teken reeks is een teken reeks die bestaat uit een of meer regels. Aanhalings tekens in de teken reeks worden letterlijk geïnterpreteerd als onderdeel van de teken reeks gegevens. Zie [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Scheidings teken

Het teken dat wordt gebruikt om de **sleutel** te scheiden van de **waarde** gegevens in de teken reeks die wordt geconverteerd.
Het standaard scheidings teken is het gelijkteken ( `=` ). Deze para meter is toegevoegd in Power shell 7.

```yaml
Type: System.Char
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: '='
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een sleutel/waarde-paar door sluizen naar `ConvertFrom-StringData` .

## UITVOER

### System. Collections. hashtabel

Met deze cmdlet wordt een hash-tabel geretourneerd die wordt gemaakt op basis van de sleutel-waardeparen.

## OPMERKINGEN

Een hier-teken reeks is een teken reeks die bestaat uit een of meer regels waarin de aanhalings tekens letterlijk worden geïnterpreteerd.

Deze cmdlet kan nuttig zijn in scripts waarmee gebruikers berichten in meerdere gesp roken talen worden weer gegeven. U kunt de hash-tabellen voor het woordenlijst type gebruiken om teken reeksen uit code te isoleren, zoals in bron bestanden, en om de tekst teken reeksen op te maken voor gebruik in Vertaal hulpprogramma's.

## GERELATEERDE KOPPELINGEN
