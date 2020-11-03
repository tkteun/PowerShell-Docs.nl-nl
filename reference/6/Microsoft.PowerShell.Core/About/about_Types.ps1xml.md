---
description: Hierin wordt uitgelegd hoe u bestanden kunt gebruiken `Types.ps1xml` om de typen objecten die worden gebruikt in Power shell uit te breiden.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1XML
ms.openlocfilehash: 6b150626f41b61d4e91f20e7d5e93af04298369c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252200"
---
# <a name="about-typesps1xml"></a>Over Types.ps1XML

## <a name="short-description"></a>Korte beschrijving
Hierin wordt uitgelegd hoe u bestanden kunt gebruiken `Types.ps1xml` om de typen objecten die worden gebruikt in Power shell uit te breiden.

## <a name="long-description"></a>Lange beschrijving

Uitgebreide type gegevens worden extra eigenschappen en methoden (' leden ') van object typen in Power shell gedefinieerd. Er zijn twee technieken voor het toevoegen van uitgebreide type gegevens aan een Power shell-sessie.

- `Types.ps1xml` bestand: een XML-bestand waarin uitgebreide type gegevens worden gedefinieerd.
- `Update-TypeData`: Een cmdlet waarmee bestanden opnieuw worden geladen `Types.ps1xml` en uitgebreide gegevens worden gedefinieerd voor typen in de huidige sessie.

In dit onderwerp worden `Types.ps1xml` bestanden beschreven. Zie update-TypeData voor meer informatie over het gebruik van de `Update-TypeData` cmdlet om dynamische uitgebreide type gegevens [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData)toe te voegen aan de huidige sessie.

## <a name="about-extended-type-data"></a>Informatie over uitgebreide-type gegevens

Uitgebreide type gegevens worden extra eigenschappen en methoden (' leden ') van object typen in Power shell gedefinieerd. U kunt elk type dat door Power shell wordt ondersteund, uitbreiden en de toegevoegde eigenschappen en methoden op dezelfde manier gebruiken als de eigenschappen die voor de object typen zijn gedefinieerd.

Power shell voegt bijvoorbeeld een eigenschap **DateTime** toe aan alle `System.DateTime` objecten, zoals de waarde die door de `Get-Date` cmdlet wordt geretourneerd.

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

U kunt de eigenschap **DateTime** niet vinden in de beschrijving van de structuur [System. datetime](/dotnet/api/system.datetime) , omdat Power shell de eigenschap toevoegt en alleen zichtbaar is in Power shell.

Power shell definieert intern een standaardset uitgebreide typen. Dit type informatie wordt tijdens het opstarten in elke Power shell-sessie geladen. De eigenschap **DateTime** maakt deel uit van deze standaardset. Vóór Power shell 6 werden de type definities het `Types.ps1xml` bestand in de Power shell-installatiemap ( `$PSHOME` ) opgeslagen.

## <a name="adding-extended-type-data-to-powershell"></a>Uitgebreide type gegevens toevoegen aan Power shell

Er zijn drie bronnen van uitgebreide-type gegevens in Power shell-sessies.

- De gedefinieerde door Power shell en wordt automatisch in elke Power shell-sessie geladen. Vanaf Power shell 6 wordt deze informatie gecompileerd in Power shell en wordt deze niet meer in een `Types.ps1xml` bestand verzonden.

- De `Types.ps1xml` bestanden die modules exporteren, worden geladen wanneer de module in de huidige sessie wordt geïmporteerd.

- Uitgebreide-type gegevens die zijn gedefinieerd met behulp van de- `Update-TypeData` cmdlet, worden alleen toegevoegd aan de huidige sessie. Het wordt niet opgeslagen in een bestand.

In de-sessie worden de uitgebreide type gegevens van de drie bronnen toegepast op objecten op dezelfde manier en zijn deze beschikbaar voor alle objecten van de opgegeven typen.

## <a name="the-typedata-cmdlets"></a>De TypeData-cmdlets

De volgende cmdlets zijn opgenomen in de module **micro soft. Power shell. Utility** in power Shell 3,0 en hoger.

- `Get-TypeData`: Hiermee worden uitgebreide type gegevens in de huidige sessie opgehaald.
- `Update-TypeData`: Bestanden opnieuw laden `Types.ps1xml` . Voegt uitgebreide type gegevens toe aan de huidige sessie.
- `Remove-TypeData`: Verwijdert uitgebreide-type gegevens uit de huidige sessie.

Zie het Help-onderwerp voor elke cmdlet voor meer informatie over deze cmdlets.

## <a name="built-in-typesps1xml-files"></a>Ingebouwde Types.ps1XML-bestanden

De `Types.ps1xml` bestanden in de `$PSHOME` map worden automatisch aan elke sessie toegevoegd.

Het `Types.ps1xml` bestand in de Power shell-installatie directory ( `$PSHOME` ) is een XML-tekst bestand waarmee u eigenschappen en methoden kunt toevoegen aan de objecten die worden gebruikt in Power shell. Power Shell heeft ingebouwde `Types.ps1xml` bestanden die verschillende elementen toevoegen aan de .net-typen, maar u kunt extra `Types.ps1xml` bestanden maken om de typen verder uit te breiden.

Bijvoorbeeld: Matrix objecten ( `System.Array` ) hebben een eigenschap **Length** die het aantal objecten in de matrix vermeldt. Omdat de naam **lengte** echter niet duidelijk de eigenschap beschrijft, voegt Power shell een alias eigenschap benoemde **Count** toe waarin dezelfde waarde wordt weer gegeven. De eigenschap **Count** van het volgende XML-bestand wordt toegevoegd aan het `System.Array` type.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

Als u de nieuwe **AliasProperty** wilt ophalen, gebruikt u een `Get-Member` opdracht op een wille keurige matrix, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
Get-Member -InputObject (1,2,3,4)
```

De opdracht retourneert de volgende resultaten.

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

Als gevolg hiervan kunt u de eigenschap **Count** of de eigenschap **Length** van matrices in Power shell gebruiken. Bijvoorbeeld:

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a>Nieuwe Types.ps1XML-bestanden maken

De `.ps1xml` bestanden die worden geïnstalleerd met Power shell, zijn digitaal ondertekend om knoeien te voor komen, omdat de opmaak script blokken kan bevatten. Daarom kunt u een eigenschap of methode toevoegen aan een .NET-type door uw eigen `Types.ps1xml` bestanden te maken en deze vervolgens toe te voegen aan uw Power shell-sessie.

Als u een nieuw bestand wilt maken, begint u met het kopiëren van een bestaand `Types.ps1xml` bestand. Het nieuwe bestand kan een wille keurige naam hebben, maar moet een `.ps1xml` bestandsnaam extensie hebben. U kunt het nieuwe bestand in elke map die toegankelijk is voor Power shell plaatsen, maar het is handig om de bestanden in de installatie directory van Power shell ( `$PSHOME` ) of in een submap van de installatiemap te plaatsen.

Wanneer u het nieuwe bestand hebt opgeslagen, gebruikt u de `Update-TypeData` cmdlet om het nieuwe bestand aan uw Power shell-sessie toe te voegen. Als u wilt dat uw typen voor rang hebben boven de ingebouwde typen die zijn gedefinieerd, gebruikt u de para meter **PrependData** van de `Update-TypeData` cmdlet. `Update-TypeData` alleen van invloed op de huidige sessie. Als u de wijziging wilt aanbrengen in alle toekomstige sessies, exporteert u de console of voegt `Update-TypeData` u de opdracht toe aan uw Power shell-profiel.

## <a name="typesps1xml-and-add-member"></a>Types.ps1XML en Add-Member

De `Types.ps1xml` bestanden voegen eigenschappen en methoden toe aan alle exemplaren van de objecten van het opgegeven .net-type in de desbetreffende Power shell-sessie. Als u echter eigenschappen of methoden wilt toevoegen aan één exemplaar van een object, gebruikt u de `Add-Member` cmdlet.

Zie [add-member](xref:Microsoft.PowerShell.Utility.Add-Member)voor meer informatie.

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a>Voor beeld: een lid van de leeftijd toevoegen aan file info-objecten

In dit voor beeld ziet u hoe u een eigenschap **leeftijd** kunt toevoegen aan **System. io. file info** -objecten. De leeftijd van een bestand is het verschil tussen de aanmaak tijd en de huidige tijd in dagen.

Omdat de eigenschap **leeftijd** wordt berekend met behulp van een script blok, zoekt `<ScriptProperty>` u een label om te gebruiken als model voor de nieuwe eigenschap **leeftijd** .

Sla de volgende XML-code op in het bestand `$PSHOME\MyTypes.ps1xml` .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

Voer uit `Update-TypeData` om het nieuwe `Types.ps1xml` bestand toe te voegen aan de huidige sessie. De opdracht gebruikt de para meter **PrependData** om het nieuwe bestand te plaatsen in een volg orde die hoger is dan de oorspronkelijke definities.

`Update-TypeData`Zie [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData)voor meer informatie over.

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

Als u de wijziging wilt testen, voert u een `Get-ChildItem` opdracht uit om het PowerShell.exe-bestand in de map op te halen `$PSHOME` en vervolgens het bestand naar de cmdlet te pipeen `Format-List` om alle eigenschappen van het bestand weer te geven. Als gevolg van de wijziging wordt de eigenschap **leeftijd** weer gegeven in de lijst.

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a>De XML in Types.ps1XML-bestanden

De volledige schema definitie vindt u in de [types. XSD](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) in de Power shell-bron code opslagplaats op github.

De `<Types>` tag omsluit alle typen die in het bestand zijn gedefinieerd. Er mag slechts één `<Types>` tag zijn.

Elk .NET-type dat in het bestand wordt vermeld, moet worden aangeduid met een `<Type>` tag.

De type Tags moeten de volgende tags bevatten:

`<Name>`: Omsluit de naam van het betrokken .NET-type.

`<Members>`: Omsluit de labels voor de nieuwe eigenschappen en methoden die zijn gedefinieerd voor het .NET-type.

Een van de volgende leden codes kan zich in de tag bevindt `<Members>` .

`<AliasProperty>`: Hiermee definieert u een nieuwe naam voor een bestaande eigenschap.

Het `<AliasProperty>` label moet een `<Name>` tag hebben die de naam van de nieuwe eigenschap en een `<ReferencedMemberName>` tag opgeeft waarmee de bestaande eigenschap wordt opgegeven.

De eigenschap **Count** alias is bijvoorbeeld een alias voor de eigenschap **Length** van Matrix objecten.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

`<CodeMethod>`: Verwijst naar een statische methode van een .NET-klasse.

Het `<CodeMethod>` label moet een `<Name>` tag hebben die de naam van de nieuwe methode opgeeft en een `<GetCodeReference>` tag die de code specificeert waarin de methode is gedefinieerd.

De eigenschap **mode** van `System.IO.DirectoryInfo` objecten is bijvoorbeeld een code-eigenschap die is gedefinieerd in de Power shell-bestandssysteem provider.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<CodeProperty>`: Verwijst naar een statische methode van een .NET-klasse.

Het `<CodeProperty>` label moet een `<Name>` tag hebben die de naam van de nieuwe eigenschap en een `<GetCodeReference>` tag opgeeft die de code specificeert waarin de eigenschap is gedefinieerd.

De eigenschap **mode** van `System.IO.DirectoryInfo` objecten is bijvoorbeeld een code-eigenschap die is gedefinieerd in de Power shell-bestandssysteem provider.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<MemberSet>`: Definieert een verzameling van leden (eigenschappen en methoden).

De `<MemberSet>` labels worden weer gegeven in de primaire `<Members>` labels. De tags moeten een tag omsluiten `<Name>` rond de naam van de ledenset en een secundaire `<Members>` code die de leden (eigenschappen en methoden) in de set omsluit. Een van de tags waarmee een eigenschap (zoals `<NoteProperty>` of `<ScriptProperty>` ) of een methode (zoals `<Method>` of `<ScriptMethod>` ) wordt gemaakt, kan lid zijn van de set.

In `Types.ps1xml` bestanden wordt de `<MemberSet>` tag gebruikt voor het definiëren van de standaard weergaven van de .net-objecten in Power shell. In dit geval is de naam van de leden reeks (de waarde binnen de `<Name>` Tags) altijd **PsStandardMembers** en de namen van de eigenschappen (de waarde van de `<Name>` tag) zijn een van de volgende:

- `DefaultDisplayProperty`: Eén eigenschap van een object.

- `DefaultDisplayPropertySet`: Een of meer eigenschappen van een object.

- `DefaultKeyPropertySet`: Een of meer sleutel eigenschappen van een object. Een sleutel eigenschap identificeert exemplaren van eigenschaps waarden, zoals de ID van items in een sessie geschiedenis.

De volgende XML definieert bijvoorbeeld de standaard weergave van Services ( `System.ServiceProcess.ServiceController` objecten) die door de cmdlet worden geretourneerd `Get-Service` . Hiermee wordt een leden reeks gedefinieerd met de naam **PsStandardMembers** die bestaat uit een standaard eigenschap die is ingesteld op de eigenschappen **status** , **naam** en **DisplayName** .

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<Method>`: Verwijst naar een systeem eigen methode van het onderliggende object.

`<Methods>`: Een verzameling methoden van het object.

`<NoteProperty>`: Definieert een eigenschap met een statische waarde.

Het `<NoteProperty>` label moet een `<Name>` tag hebben die de naam van de nieuwe eigenschap en een `<Value>` tag opgeeft waarmee de waarde van de eigenschap wordt opgegeven.

De volgende XML-code maakt bijvoorbeeld een eigenschap **status** voor **System. io. DirectoryInfo** -objecten. De waarde van de eigenschap **status** is altijd **geslaagd**.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

`<ParameterizedProperty>`: Eigenschappen die argumenten aannemen en een waarde Retour neren.

`<Properties>`: Een verzameling eigenschappen van het object.

`<Property>`: Een eigenschap van het basis object.

`<PropertySet>`: Hiermee definieert u een verzameling eigenschappen van het object.

Het `<PropertySet>` label moet een `<Name>` tag hebben die de naam van de eigenschappenset opgeeft en een `<ReferencedProperty>` tag die de eigenschappen specificeert. De namen van de eigenschappen bevinden zich in een `<Name>` tag.

In `Types.ps1xml` `<PropertySet>` worden tags gebruikt voor het definiëren van sets eigenschappen voor de standaard weergave van een object. U kunt de standaard weer geven identificeren met de waarde **PsStandardMembers** in het `<Name>` label van een `<MemberSet>` tag.

De volgende XML-code maakt bijvoorbeeld een **status** eigenschap voor het `System.IO.DirectoryInfo` object. De waarde van de eigenschap **status** is altijd **geslaagd**.

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<ScriptMethod>`: Definieert een methode waarvan de waarde de uitvoer van een script is.

Het `<ScriptMethod>` label moet een `<Name>` tag hebben die de naam van de nieuwe methode en een `<Script>` tag bevat die het script blok omsluit dat het resultaat van de methode retourneert.

De `ConvertToDateTime` `ConvertFromDateTime` methoden en van Management Objects ( `System.System.Management.ManagementObject` ) zijn bijvoorbeeld script methoden die gebruikmaken van de `ToDateTime` `ToDmtfDateTime` statische methoden van de- `System.Management.ManagementDateTimeConverter` klasse.

```xml
<Type>
 <Name>System.Management.ManagementObject</Name>
 <Members>
 <ScriptMethod>
   <Name>ConvertToDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
   </Script>
 </ScriptMethod>
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

`<ScriptProperty>`: Definieert een eigenschap waarvan de waarde de uitvoer van een script is.

Het `<ScriptProperty>` label moet een `<Name>` tag hebben die de naam van de nieuwe eigenschap en een `<GetScriptBlock>` tag bevat die het script blok omsluit dat de waarde van de eigenschap retourneert.

De eigenschap **VersionInfo** van het object **System. io. file info** is bijvoorbeeld een script eigenschap die het resultaat is **van het gebruik** van de eigenschap **FullName** van de statische methode van **System. Diagnostics. FileVersionInfo** -objecten.

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
      [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

Zie de [Windows Power shell Software Development Kit (SDK) (Engelstalig)](/powershell/scripting/developer/windows-powershell)voor meer informatie.

## <a name="update-typedata"></a>Update-TypeData

`Types.ps1xml`Voer de cmdlet uit om uw bestanden te laden in een Power shell-sessie `Update-TypeData` . Als u wilt dat de typen in het bestand voor rang hebben op typen in het ingebouwde `Types.ps1xml` bestand, voegt u de para meter **PrependData** van toe `Update-TypeData` . `Update-TypeData` alleen van invloed op de huidige sessie. Als u de wijziging wilt door voeren voor alle toekomstige sessies, exporteert u de sessie of voegt `Update-TypeData` u de opdracht toe aan uw Power shell-profiel.

Uitzonde ringen die optreden in eigenschappen of van het toevoegen van eigenschappen aan een `Update-TypeData` opdracht, rapporteren geen fouten aan `StdErr` . Dit is om uitzonde ringen te onderdrukken die tijdens het format teren en uitvoeren in veel voorkomende typen zouden optreden. Als u .NET-eigenschappen krijgt, kunt u de onderdrukking van uitzonde ringen omzeilen door in plaats daarvan de syntaxis van de methode te gebruiken, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
"hello".get_Length()
```

Houd er rekening mee dat syntaxis van een methode alleen kan worden gebruikt met .NET-eigenschappen. Eigenschappen die worden toegevoegd door de cmdlet uit te voeren `Update-TypeData` , kunnen de syntaxis van de methode niet gebruiken.

## <a name="signing-a-typesps1xml-file"></a>Een Types.ps1XML-bestand ondertekenen

Als u gebruikers van uw `Types.ps1xml` bestand wilt beveiligen, kunt u het bestand ondertekenen met een digitale hand tekening. Zie [about_Signing](about_Signing.md)voor meer informatie.

## <a name="see-also"></a>Zie ook

[about_Signing](about_Signing.md)

[Kopie-item](xref:Microsoft.PowerShell.Management.Copy-Item)

[Kopiëren-item Property](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[Get-member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Get-TypeData](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[Remove-TypeData](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData)
