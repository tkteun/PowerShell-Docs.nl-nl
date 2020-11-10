---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: 7e3d02dedb9f7809a8f8e1c657987fef8ec38fa9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387988"
---
# Select-Xml

## SAMENVATTING
Zoekt tekst in een XML-teken reeks of-document.

## SYNTAXIS

### XML (standaard)

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### Pad

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### LiteralPath

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### Inhoud

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Select-XML** kunt u XPath-query's gebruiken om te zoeken naar tekst in XML-teken reeksen en documenten.
Voer een XPath-query in en gebruik de para meter *Content* , *Path* of *XML* om op te geven welke XML moet worden doorzocht.

## VOORBEELDEN

### Voor beeld 1: AliasProperty-knoop punten selecteren

```
PS C:\> $Path = "$Pshome\Types.ps1xml"
PS C:\> $XPath = "/Types/Type/Members/AliasProperty"
PS C:\> Select-Xml -Path $Path -XPath $Xpath | Select-Object -ExpandProperty Node
Name                 ReferencedMemberName
----                 --------------------
Count                Length
Name                 Key
Name                 ServiceName
RequiredServices     ServicesDependedOn
ProcessName          Name
Handles              Handlecount
VM                   VirtualSize
WS                   WorkingSetSize
Name                 ProcessName
Handles              Handlecount
VM                   VirtualMemorySize
WS                   WorkingSet
PM                   PagedMemorySize
NPM                  NonpagedSystemMemorySize
Name                 __Class
Namespace            ModuleName
```

In dit voor beeld worden de alias eigenschappen in de Types.ps1XML opgehaald.
(Zie about_Types.ps1XML (Engelstalig) voor meer informatie over dit bestand.

Met de eerste opdracht wordt het pad naar het Types.ps1XML-bestand in de $Path variabele opgeslagen.

Met de tweede opdracht slaat u het XML-pad op naar het AliasProperty-knoop punt in de variabele $XPath.

De derde opdracht maakt gebruik van de **Select-XML-** cmdlet om de AliasProperty-knoop punten op te halen die worden geïdentificeerd door de XPath-instructie van het Types.ps1XML-bestand.
De opdracht maakt gebruik van een pijplijn operator om de AliasProperty-knoop punten te verzenden naar de cmdlet Select-Object.
De para meter *ExpandProperty* breidt het **knooppunt** object uit en retourneert de eigenschappen name en ReferencedMemberName.

Het resultaat toont de naam en ReferencedMemberName van elke alias eigenschap in het XML-bestand Types.ps1.
Er is bijvoorbeeld een eigenschap **Count** die een alias is van de eigenschap **Length** .

### Voor beeld 2: een XML-document invoeren

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

In dit voor beeld ziet u hoe u de *XML-* para meter gebruikt om een XML-document te voorzien van de cmdlet **Select-XML** .

De eerste opdracht gebruikt de cmdlet Get-Content om de inhoud van het Types.ps1XML-bestand op te halen en op te slaan in de $Types variabele.
Het \[ XML \] cast de variabele als een XML-object.

De tweede opdracht maakt gebruik van de **Select-XML-** cmdlet voor het ophalen van de methodName-knoop punten in het Types.ps1XML-bestand.
De opdracht gebruikt de *XML-* para meter om de XML-inhoud in de variabele $types en de para meter *XPath* op te geven het pad naar het knoop punt van de methode.

### Voor beeld 3: Help-bestanden voor Power shell zoeken

```
PS C:\> $Namespace = @{command = "http://schemas.microsoft.com/maml/dev/command/2004/10"; maml = "http://schemas.microsoft.com/maml/2004/10"; dev = "http://schemas.microsoft.com/maml/dev/2004/10"}

The second command saves the path to the help files in the $Path variable.If there are no help files in this path on your computer, use the Update-Help cmdlet to download the help files. For more information about Updatable Help, see about_Updatable_Help (https://go.microsoft.com/fwlink/?LinkId=235801).
PS C:\> $Path = "$Pshome\en-us\*dll-Help.xml"

The third command uses the **Select-Xml** cmdlet to search the XML for cmdlet names by finding Command:Name element anywhere in the files. It saves the results in the $Xml variable.**Select-Xml** returns a **SelectXmlInfo** object that has a Node property, which is a **System.Xml.XmlElement** object. The Node property has an InnerXML property, which contains the actual XML that is retrieved.
PS C:\> $Xml = Select-Xml -Path $Path -Namespace $Namespace -XPath "//command:name"

The fourth command sends the XML in the $Xml variable to the Format-Table cmdlet. The **Format-Table** command uses a calculated property to get the Node.InnerXML property of each object in the $Xml variable, trim the white space before and after the text, and display it in the table, along with the path to the source file.
PS C:\> $Xml | Format-Table @{Label="Name"; Expression= {($_.node.innerxml).trim()}}, Path -AutoSize

Name                    Path
----                    ----
Export-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-Counter             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-WinEvent            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Import-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Add-Computer            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Add-Content             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Checkpoint-Computer     C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
...
```

In dit voor beeld ziet u hoe u met de cmdlet **Select-XML** de Help-bestanden op basis van de Power shell-cmdlet doorzoekt.
In dit voor beeld wordt gezocht naar de naam van de cmdlet die fungeert als titel voor elk Help-bestand en het pad naar het Help-bestand.

Met de eerste opdracht maakt u een hash-tabel die de XML-naam ruimte vertegenwoordigt die wordt gebruikt voor de Help-bestanden en slaat u deze op in de variabele $Namespace.

### Voor beeld 4: verschillende manieren voor het invoeren van XML

```
PS C:\> $Xml = @"
<?xml version="1.0" encoding="utf-8"?>
<Book>
  <projects>
    <project name="Book1" date="2009-01-20">
      <editions>
        <edition language="English">En.Book1.com</edition>
        <edition language="German">Ge.Book1.Com</edition>
        <edition language="French">Fr.Book1.com</edition>
        <edition language="Polish">Pl.Book1.com</edition>
      </editions>
    </project>
  </projects>
</Book>
"@

The second command uses the *Content* parameter of **Select-Xml** to specify the XML in the $Xml variable.
PS C:\> Select-Xml -Content $Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com

The third command is equivalent to the second. It uses a pipeline operator (|) to send the XML in the $Xml variable to the **Select-Xml** cmdlet.
PS C:\> $Xml | Select-Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com
```

In dit voor beeld ziet u twee verschillende manieren voor het verzenden van XML naar de cmdlet **Select-XML** .

Met de eerste opdracht slaat u een hier-teken reeks op die XML bevat in de variabele $Xml.
(Zie about_Quoting_Rules voor meer informatie over hier teken reeksen.)

### Voor beeld 5: de standaard xmlns-naam ruimte gebruiken

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

In dit voor beeld ziet u hoe u de cmdlet **Select-XML** gebruikt met XML-documenten die de standaard xmlns-naam ruimte gebruiken.
In het voor beeld worden de titels van Windows PowerShell ISE door de gebruiker gemaakte fragment bestanden opgehaald.
Zie New-IseSnippet voor meer informatie over fragmenten.

Met de eerste opdracht maakt u een hash-tabel voor de standaard naam ruimte die XML-bestanden van het fragment gebruikt en wijst u deze toe aan de $SnippetNamespace variabele.
De waarde van de hash-tabel is de XMLNS-schema-URI in het XML-code fragment.
De sleutel naam van de hash-tabel, knipsel, is wille keurig.
U kunt een naam gebruiken die niet is gereserveerd, maar u kunt geen xmlns gebruiken.

## PARAMETERS

### -Inhoud

Hiermee geeft u een teken reeks op die de XML bevat waarnaar moet worden gezocht.
U kunt ook teken reeksen door sluizen naar **Select-XML**.

```yaml
Type: System.String[]
Parameter Sets: Content
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u de paden en bestands namen op van de XML-bestanden die u wilt zoeken.
In tegens telling tot *Path* wordt de waarde van de para meter *LiteralPath* exact gebruikt wanneer deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Naam ruimte

Hiermee geeft u een hash-tabel op van de naam ruimten die worden gebruikt in de XML.
Gebruik de indeling @ { \<namespaceName\>  =  \<namespaceValue\> }.

Wanneer de XML de standaard naam ruimte gebruikt, die begint met xmlns, gebruikt u een wille keurige sleutel voor de naam van de naam ruimte.
U kunt xmlns niet gebruiken.
In de XPath-instructie, voor voegsel van elke knooppunt naam met de naam van de naam ruimte en een dubbele punt, zoals//namespaceName: node.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad en de bestands namen op van de XML-bestanden die u wilt zoeken.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -XML

Hiermee geeft u een of meer XML-knoop punten op.

Een XML-document wordt verwerkt als een verzameling van XML-knoop punten.
Als u een XML-document pipet naar **Select-XML** , wordt elk document knooppunt afzonderlijk doorzocht, zoals het door de pijp lijn wordt geleverd.

```yaml
Type: System.Xml.XmlNode[]
Parameter Sets: Xml
Aliases: Node

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -XPath

Hiermee geeft u een XPath-Zoek query op.
De query taal is hoofdletter gevoelig.
Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Knoop punt System. String of System.Xml.Xml

U kunt een pad of XML-knoop punt door sluizen naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. commands. SelectXmlInfo

## OPMERKINGEN

XPath is een standaard taal die is ontworpen om delen van een XML-document te identificeren. Zie [XPath-verwijzing](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) en het gedeelte selectie filters van de [gebeurtenis selectie](/previous-versions//aa385231(v=vs.85))voor meer informatie over de XPath-taal.

## GERELATEERDE KOPPELINGEN

[ConvertTo-Xml](ConvertTo-Xml.md)
