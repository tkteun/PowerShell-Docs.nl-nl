---
description: De `Format.ps1xml` bestanden in Power shell definiëren de standaard weergave van objecten in de Power shell-console. U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1XML
ms.openlocfilehash: be88007d23ab98b9c2f707b77f9c43578ba9887b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252619"
---
# <a name="about-formatps1xml"></a>Over Format.ps1XML

## <a name="short-description"></a>Korte beschrijving

De `Format.ps1xml` bestanden in Power shell definiëren de standaard weergave van objecten in de Power shell-console. U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.

## <a name="long-description"></a>Lange beschrijving

De `Format.ps1xml` bestanden in Power shell definiëren de standaard weergave van objecten in Power shell. U kunt uw eigen `Format.ps1xml` bestanden maken om de weer gave van objecten te wijzigen of om standaard weer gaven te definiëren voor nieuwe object typen die u in Power Shell maakt.

Wanneer Power shell een object weergeeft, worden de gegevens in gestructureerde indelings bestanden gebruikt om de standaard weergave van het object te bepalen. De gegevens in de indelings bestanden bepalen of het object wordt weer gegeven in een tabel of in een lijst en bepaalt welke eigenschappen standaard worden weer gegeven.

De opmaak is alleen van invloed op de weer gave. Dit heeft geen invloed op welke object eigenschappen worden door gegeven aan de pijp lijn of hoe ze worden door gegeven. `Format.ps1xml` bestanden kunnen niet worden gebruikt om de uitvoer indeling voor hash-tabellen aan te passen.

Power shell bevat zeven indelings bestanden. Deze bestanden bevinden zich in de installatiemap ( `$PSHOME` ). Elk bestand definieert de weer gave van een groep Microsoft .NET Framework-objecten:

1. `Certificate.Format.ps1xml`

   Objecten in het certificaat archief, zoals X. 509-certificaten en certificaat archieven.

1. `DotNetTypes.Format.ps1xml`

   Andere .NET Framework typen, zoals Culture info-, FileVersionInfo-en EventLogEntry-objecten.

1. `FileSystem.Format.ps1xml`

   Bestandssysteem objecten, zoals bestanden en mappen.

1. `Help.Format.ps1xml`

   Help-weer gaven, zoals gedetailleerde en volledige weer gaven, para meters en voor beelden.

1. `PowerShellCore.Format.ps1xml`

   Objecten die worden gegenereerd door Power shell core-cmdlets, zoals `Get-Member` en `Get-History` .

1. `PowerShellTrace.Format.ps1xml`

   Traceer objecten, zoals die worden gegenereerd door de `Trace-Command` cmdlet.

1. `Registry.Format.ps1xml`

   Register objecten, zoals sleutels en vermeldingen.

Een opmaak bestand kan vier verschillende weer gaven van elk object definiëren:

- Tabel
- Lijst
- Organisatiebreed
- Aangepast

Als bijvoorbeeld de uitvoer van een `Get-ChildItem` opdracht wordt gepiped naar een `Format-List` opdracht, `Format-List` wordt de weer gave in het `FileSystem.Format.ps1xml` bestand gebruikt om te bepalen hoe het bestand en de objecten van de map als een lijst moeten worden weer gegeven.

Wanneer een opmaak bestand meer dan één weer gave van een object bevat, past Power shell de eerste weer gave toe die wordt gevonden.

In een `Format.ps1xml` bestand wordt een weer gave gedefinieerd met behulp van een set XML-tags die de naam van de weer gave beschrijven, het type object waarop deze kan worden toegepast, de kolom koppen en de eigenschappen die worden weer gegeven in de hoofd tekst van de weer gave. De indeling in `Format.ps1xml` bestanden wordt alleen toegepast voordat de gegevens aan de gebruiker worden gepresenteerd.

## <a name="creating-new-formatps1xml-files"></a>Nieuwe Format.ps1XML-bestanden maken

De `.ps1xml` bestanden die worden geïnstalleerd met Power shell, zijn digitaal ondertekend om knoeien te voor komen, omdat de opmaak script blokken kan bevatten. Als u de weergave opmaak van een bestaande object weergave wilt wijzigen of als u weer gaven wilt toevoegen voor nieuwe objecten, maakt u uw eigen `Format.ps1xml` bestanden en voegt u deze toe aan uw Power shell-sessie.

Als u een nieuw bestand wilt maken, kopieert u een bestaand `Format.ps1xml` bestand. Het nieuwe bestand kan een wille keurige naam hebben, maar moet een `.ps1xml` bestandsnaam extensie hebben. U kunt het nieuwe bestand in elke map plaatsen die toegankelijk is voor Power shell, maar het is handig om de bestanden in de Power shell-installatiemap ( `$PSHOME` ) of in een submap van de installatiemap te plaatsen.

Als u de opmaak van een huidige weer gave wilt wijzigen, gaat u naar de weer gave in het opmaak bestand en gebruikt u vervolgens de labels om de weer gave te wijzigen. Als u een weer gave voor een nieuw object type wilt maken, maakt u een nieuwe weer gave of gebruikt u een bestaande weer gave als een model. De tags worden in de volgende sectie beschreven. U kunt vervolgens alle andere weer gaven in het bestand verwijderen, zodat de wijzigingen duidelijk zijn voor iedereen die het bestand bekijkt.

Nadat u de wijzigingen hebt opgeslagen, gebruikt u de `Update-FormatData` cmdlet om het nieuwe bestand aan uw Power shell-sessie toe te voegen. Als u wilt dat de weer gave voor rang krijgt boven een weer gave die is gedefinieerd in de ingebouwde bestanden, gebruikt u de para meter **PrependPath** .
`Update-FormatData` alleen van invloed op de huidige sessie. Als u de wijziging wilt aanbrengen in alle toekomstige sessies, voegt u de `Update-FormatData` opdracht toe aan uw Power shell-profiel.

### <a name="example-adding-calendar-data-to-culture-objects"></a>Voor beeld: agenda gegevens toevoegen aan cultuur objecten

In dit voor beeld ziet u hoe u de indeling wijzigt van de cultuur-objecten **System. Globalization. Culture info** die zijn gegenereerd door de `Get-Culture` cmdlet in de huidige Power shell-sessie. Met de opdrachten in het voor beeld wordt de eigenschap **Calendar** toegevoegd aan de standaard tabel weergave weer gave van cultuur-objecten.

De eerste stap is het zoeken naar het `Format.ps1xml` bestand dat de huidige weer gave van de cultuur-objecten bevat. Met de volgende `Select-String` opdracht wordt het bestand gevonden:

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.Globalization.CultureInfo"
}

Select-String @Parms
```

```Output
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:113:
     <Name>System.Globalization.CultureInfo</Name>
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:115:
<TypeName>System.Globalization.CultureInfo</TypeName>
```

Met deze opdracht wordt de definitie in het bestand verstaan `DotNetTypes.Format.ps1xml` .

Met de volgende opdracht wordt de bestands inhoud naar een nieuw bestand gekopieerd `MyDotNetTypes.Format.ps1xml` .

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

Open het `MyDotNetTypes.Format.ps1xml` bestand in een XML-of tekst editor, zoals Visual Studio code. Zoek de sectie **System. Globalization. Culture info** -object. De volgende XML definieert de weer gaven van het **Culture info** -object. Het object heeft alleen een **TableControl** -weer gave.

```xml
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
    <TypeName>System.Globalization.CultureInfo</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
            <PropertyName>LCID</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

De rest van het bestand verwijderen, met uitzonde ring van de `<?xml>` Tags openen, `<Configuration>` ,, en `<ViewDefinitions>` Sluiten `<ViewDefinitions>` en `<Configuration>` Tags. Als er een digitale hand tekening is, verwijdert u deze uit uw aangepaste `Format.ps1xml` bestand.

Het `MyDotNetTypes.Format.ps1xml` bestand moet er nu uitzien als in het volgende voor beeld:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
<ViewDefinitions>
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
    <TypeName>System.Globalization.CultureInfo</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader/>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
            <PropertyName>LCID</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
</ViewDefinitions>
</Configuration>
```

Maak een nieuwe kolom voor de eigenschap **Calendar** door een nieuwe set tags toe te voegen `<TableColumnHeader>` . De waarde van de eigenschap **Calendar** kan lang zijn. Geef dus een waarde van 45 tekens op als de `<Width>` .

```xml
<TableHeaders>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>45</Width>
  </TableColumnHeader>
  <TableColumnHeader/>
</TableHeaders>
```

Voeg een nieuw kolom item toe voor **kalenders** in de tabel rijen met behulp van de `<TableColumnItem>` `<PropertyName` Tags en:

```xml
<TableRowEntries>
  <TableRowEntry>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName>LCID</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Name</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Calendar</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>DisplayName</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>
```

Sla het bestand op en sluit het. Gebruik `Update-FormatData` om het nieuwe indelings bestand aan de huidige Power shell-sessie toe te voegen.

In dit voor beeld wordt de para meter **PrependPath** gebruikt om het nieuwe bestand in een hogere volg orde dan het oorspronkelijke bestand te plaatsen. Zie [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)voor meer informatie.

```powershell
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

Als u de wijziging wilt testen, typt `Get-Culture` en controleert u de uitvoer die de eigenschap **Calendar** bevat.

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a>De XML in Format.ps1XML-bestanden

De volledige schema definitie vindt u in [Format. XSD](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in de Power shell-bron code opslagplaats op github.

De sectie **ViewDefinitions** van elk `Format.ps1xml` bestand bevat de `<View>` Tags waarmee elke weer gave wordt gedefinieerd. Een typische `<View>` tag bevat de volgende Tags:

- `<Name>` Hiermee wordt de naam van de weer gave aangeduid.
- `<ViewSelectedBy>` Hiermee geeft u het object type of de typen waarop de weer gave van toepassing is.
- `<GroupBy>` Hiermee wordt aangegeven hoe items in de weer gave in groepen worden gecombineerd.
- `<TableControl>`, `<ListControl>` , `<WideControl>` en `<CustomControl>` bevatten de tags die aangeven hoe elk item wordt weer gegeven.

### <a name="viewselectedby-tag"></a>ViewSelectedBy-tag

De `<ViewSelectedBy>` tag kan een `<TypeName>` tag bevatten voor elk object type waarop de weer gave van toepassing is. Het kan ook een tag bevatten `<SelectionSetName>` die verwijst naar een selectieset die elders is gedefinieerd met behulp van een `<SelectionSet>` tag.

### <a name="groupby-tag"></a>GroupBy-tag

Het `<GroupBy>` label bevat een `<PropertyName>` tag die de object eigenschap specificeert op basis waarvan items moeten worden gegroepeerd. Het bevat ook een `<Label>` label dat een teken reeks opgeeft die moet worden gebruikt als label voor elke groep of een `<CustomControlName>` label dat verwijst naar een aangepast besturings element dat elders is gedefinieerd met behulp van een `<Control>` tag. Het `<Control>` label bevat een `<Name>` tag en een `<CustomControl>` tag.

### <a name="tablecontroltag"></a>TableControlTag

De `<TableControl>` tag bevat normaal gesp roken `<TableHeaders>` `<TableRowEntries>` labels en tags waarmee de opmaak van de koppen en rijen van de tabel worden gedefinieerd. Het `<TableHeaders>` label bevat doorgaans `<TableColumnHeader>` Tags die de `<Label>` `<Width>` Tags, en bevatten `<Alignment>` . Het `<TableRowEntries>` label bevat `<TableRowEntry>` labels voor elke rij in de tabel. Het `<TableRowEntry>` label bevat een `<TableColumnItems>` label dat een `<TableColumnItem>` tag bevat voor elke kolom in de rij. Normaal gesp roken `<TableColumnItem>` bevat de tag een `<PropertyName>` tag die de object eigenschap identificeert die moet worden weer gegeven op de gedefinieerde locatie of een label met een `<ScriptBlock>` script code die een resultaat berekent dat op de locatie moet worden weer gegeven.

> [!NOTE]
> Script blokken kunnen ook elders worden gebruikt in locaties waar berekende resultaten nuttig kunnen zijn.

De `<TableColumnItem>` tag kan ook een `<FormatString>` tag bevatten die aangeeft hoe de eigenschap of de berekende resultaten worden weer gegeven.

### <a name="listcontrol-tag"></a>ListControl-tag

De `<ListControl>` tag bevat meestal een `<ListEntries>` tag. Het `<ListEntries>` label bevat een `<ListEntry>` tag. Het `<ListEntry>` label bevat een `<ListItems>` tag. Het `<ListItems>` label bevat `<ListItem>` Tags die labels bevatten `<PropertyName>` . De `<PropertyName>` labels geven de object eigenschap op die moet worden weer gegeven op de opgegeven locatie in de lijst. Als de weergave selectie is gedefinieerd met behulp van een selectieset, `<ListControl>` `<ListEntry>` kunnen de tags en ook een tag bevatten `<EntrySelectedBy>` die een of meer `<TypeName>` labels bevat. Deze `<TypeName>` Tags geven het object type op waarvan de `<ListControl>` tag is bedoeld om weer te geven.

### <a name="widecontrol-tag"></a>WideControl-tag

De `<WideControl>` tag bevat meestal een `<WideEntries>` tag. Het `<WideEntries>` label bevat een of meer `<WideEntry>` Tags. Een `<WideEntry>` tag bevat meestal een `<PropertyName>` tag waarmee de eigenschap wordt opgegeven die op de opgegeven locatie in de weer gave moet worden weer gegeven. De `<PropertyName>` tag kan een `<FormatString>` tag bevatten die aangeeft hoe de eigenschap moet worden weer gegeven.

### <a name="customcontrol-tag"></a>CustomControl-tag

`<CustomControl>`Met de tag kunt u een script blok gebruiken om een indeling te definiëren. Een `<CustomControl>` tag bevat doorgaans een `<CustomEntries>` tag die meerdere `<CustomEntry>` labels bevat. Elke `<CustomEntry>` tag bevat een `<CustomItem>` tag die diverse Tags kan bevatten waarin de inhoud en opmaak van de opgegeven locatie in de weer gave, inclusief `<Text>` ,, `<Indentation>` `<ExpressionBinding>` , en de `<NewLine>` Tags, worden opgegeven.

## <a name="default-displays-in-typesps1xml"></a>Standaard wordt weer gegeven in Types.ps1XML

De standaard weer gaven van sommige basis object typen worden gedefinieerd in het `Types.ps1xml` bestand in de `$PSHOME` map. De knoop punten hebben de naam **PsStandardMembers** en de subknooppunten gebruiken een van de volgende Tags:

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

Zie [about_Types.ps1XML](about_Types.ps1xml.md)voor meer informatie.

## <a name="tracing-formatps1xml-file-use"></a>Het gebruik van Format.ps1XML-bestand traceren

Als u fouten wilt detecteren tijdens het laden of Toep assen van `Format.ps1xml` bestanden, gebruikt u de `Trace-Command` cmdlet met een van de volgende indelings onderdelen als de waarde van de para meter **name** :

- FormatFileLoading
- FormatViewBinding

Zie [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) en [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)voor meer informatie.

## <a name="signing-a-formatps1xml-file"></a>Een Format.ps1XML-bestand ondertekenen

Als u de gebruikers van uw bestand wilt beveiligen, moet u `Format.ps1xml` het bestand ondertekenen met een digitale hand tekening. Zie [about_Signing](about_Signing.md)voor meer informatie.

## <a name="sample-xml-for-a-format-table-custom-view"></a>Voor beeld-XML voor een aangepaste weer gave Format-Table

In het volgende voor beeld wordt een `Format-Table` aangepaste weer gave gemaakt voor de objecten **System. io. DirectoryInfo** en **System. io. file info.** `Get-ChildItem` De aangepaste weer gave heet **mygciview** en voegt de kolom **CreationTime** toe aan de tabel.

De aangepaste weer gave wordt gemaakt op basis van een bewerkte versie van het `FileSystem.Format.ps1xml` bestand dat is opgeslagen in `$PSHOME` power shell 5,1.

Nadat het aangepaste `.ps1xml` bestand is opgeslagen, gebruikt `Update-FormatData` u om de weer gave in een Power shell-sessie op te slaan. In dit voor beeld moet de aangepaste weer gave de tabel indeling gebruiken, anders `Format-Table` mislukt.

Gebruik `Format-Table` met de **weer gave** -para meter om de naam van de aangepaste weer gave op te geven en de uitvoer van de tabel op te maken. Zie [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)voor een voor beeld van hoe de opdracht wordt uitgevoerd.

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.IO.DirectoryInfo"
}
Select-String @Parms
Copy-Item $PSHome\FileSystem.format.ps1xml .\MyFileSystem.Format.ps1xml
Update-FormatData -PrependPath $PSHOME\Format\MyFileSystem.Format.ps1xml
```

> [!NOTE]
> Als u het XML-voor beeld wilt aanpassen aan de beperkingen van de regel breedte, was het nood zakelijk om een bepaalde inspringing te comprimeren en regel einden in de code te gebruiken.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
    <SelectionSets>
        <SelectionSet>
            <Name>FileSystemTypes</Name>
            <Types>
                <TypeName>System.IO.DirectoryInfo</TypeName>
                <TypeName>System.IO.FileInfo</TypeName>
            </Types>
        </SelectionSet>
    </SelectionSets>
<Controls>
<Control>
<Name>FileSystemTypes-GroupingFormat</Name>
<CustomControl>
 <CustomEntries>
  <CustomEntry>
    <CustomItem>
    <Frame>
    <LeftIndent>4</LeftIndent>
    <CustomItem>
    <Text AssemblyName="System.Management.Automation"
    BaseName="FileSystemProviderStrings"
    ResourceId="DirectoryDisplayGrouping"/>
    <ExpressionBinding>
     <ScriptBlock>
      $_.PSParentPath.Replace("Microsoft.PowerShell.Core\FileSystem::", "")
     </ScriptBlock>
    </ExpressionBinding>
    <NewLine/>
    </CustomItem>
    </Frame>
    </CustomItem>
    </CustomEntry>
 </CustomEntries>
</CustomControl>
</Control>
</Controls>
<ViewDefinitions>
    <View>
    <Name>mygciview</Name>
    <ViewSelectedBy>
        <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <GroupBy>
      <PropertyName>PSParentPath</PropertyName>
      <CustomControlName>FileSystemTypes-GroupingFormat</CustomControlName>
    </GroupBy>
        <TableControl>
            <TableHeaders>
                <TableColumnHeader>
                    <Label>Mode</Label>
                    <Width>7</Width>
                    <Alignment>left</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>LastWriteTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>CreationTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>Length</Label>
                    <Width>14</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader/>
            </TableHeaders>
            <TableRowEntries>
                <TableRowEntry>
                    <Wrap/>
                    <TableColumnItems>
                        <TableColumnItem>
                            <PropertyName>Mode</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.LastWriteTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.CreationTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                        <PropertyName>Length</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <PropertyName>Name</PropertyName>
                        </TableColumnItem>
                    </TableColumnItems>
                </TableRowEntry>
            </TableRowEntries>
        </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Zie ook

[Exporteren-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[Naslaginformatie over XML voor opmaakschema](/powershell/scripting/developer/format/format-schema-xml-reference)

[Tracering-opdracht](xref:Microsoft.PowerShell.Utility.Trace-Command)

[Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[Een PowerShell-opmaakbestand schrijven](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
