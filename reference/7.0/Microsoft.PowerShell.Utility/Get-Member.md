---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-member?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Member
ms.openlocfilehash: e85d8d315600d81297a85f09f55a023fd02afe09
ms.sourcegitcommit: d95a7255f6775b2973aa9473611185a5583881ff
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106555216"
---
# Get-Member

## Samen vatting
Hiermee worden de eigenschappen en methoden van objecten opgehaald.

## Syntax

```
Get-Member [-InputObject <PSObject>] [[-Name] <String[]>] [-MemberType <PSMemberTypes>]
 [-View <PSMemberViewTypes>] [-Static] [-Force] [<CommonParameters>]
```

## Beschrijving

Met de `Get-Member` cmdlet worden de leden, eigenschappen en methoden van objecten opgehaald.

Als u het object wilt opgeven, gebruikt u de para meter **input object** of pipet u een object naar `Get-Member` . Als u informatie wilt ophalen over statische leden, de leden van de klasse, niet van het exemplaar, gebruikt u de **statische** para meter. Als u alleen bepaalde typen leden wilt ophalen, bijvoorbeeld **NoteProperties**, gebruikt u de para meter **member type** .

## Voorbeelden

### Voor beeld 1: leden van proces objecten ophalen

Met deze opdracht worden de eigenschappen en methoden van de service objecten weer gegeven die door de cmdlet worden gegenereerd `Get-Service` .

Omdat het `Get-Member` onderdeel van de opdracht geen para meters heeft, worden standaard waarden voor de para meters gebruikt. Standaard `Get-Member` krijgt geen statische of ingebouwde leden.

```powershell
Get-Service | Get-Member
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, System.EventArgs)
Close                     Method        void Close()
Continue                  Method        void Continue()
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.ServiceControllerSt...
BinaryPathName            Property      System.String {get;set;}
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DelayedAutoStart          Property      System.Boolean {get;set;}
DependentServices         Property      System.ServiceProcess.ServiceController[] DependentServices {get;}
Description               Property      System.String {get;set;}
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle ServiceHandle {get;}
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] ServicesDependedOn {get;}
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType {get;}
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartType {get;}
StartupType               Property      Microsoft.PowerShell.Commands.ServiceStartupType {get;set;}
Status                    Property      System.ServiceProcess.ServiceControllerStatus Status {get;}
UserName                  Property      System.String {get;set;}
ToString                  ScriptMethod  System.Object ToString();
```

### Voor beeld 2: leden van service objecten ophalen

In dit voor beeld worden alle leden (eigenschappen en methoden) opgehaald van de service objecten die zijn opgehaald door de `Get-Service` cmdlet, met inbegrip van de intrinsieke leden, zoals **PSBase**, **PSObject** en de methoden **get_** en **set_** .

```powershell
Get-Service | Get-Member -Force
(Get-Service Schedule).PSBase
```

De `Get-Member` opdracht gebruikt de para meter **Force** om de ingebouwde leden en door het compileren gegenereerde leden van de objecten toe te voegen aan de weer gave. U kunt deze eigenschappen en methoden op dezelfde manier gebruiken als een aangepaste methode van het object. Met de tweede opdracht wordt aangegeven hoe de waarde van de eigenschap PSBase van de Schedule-service wordt weer gegeven.

### Voor beeld 3: uitgebreide leden van service objecten ophalen

In dit voor beeld worden de methoden en eigenschappen van service objecten opgehaald die zijn uitgebreid met behulp van een `Types.ps1xml` bestand of de `Add-Member` cmdlet.

```powershell
Get-Service | Get-Member -View Extended
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name             MemberType    Definition
----             ----------    ----------
Name             AliasProperty Name = ServiceName
RequiredServices AliasProperty RequiredServices = ServicesDependedOn
ToString         ScriptMethod  System.Object ToString();
```

De `Get-Member` opdracht gebruikt de para meter **weer geven** om alleen de uitgebreide leden van de service objecten op te halen. In dit geval is het uitgebreide lid de **naam** eigenschap, een alias eigenschap van de eigenschap **ServiceName** .

### Voor beeld 4: script eigenschappen van gebeurtenis logboek objecten ophalen

In dit voor beeld worden de script eigenschappen van gebeurtenis logboek objecten in het systeem logboek in Logboeken opgehaald.

```powershell
Get-WinEvent -LogName System -MaxEvents 1 | Get-Member -MemberType NoteProperty
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.EventLogRecord

Name    MemberType   Definition
----    ----------   ----------
Message NoteProperty string Message=The machine-default permission settings do not grant Local ...
```

De para meter **member type** haalt alleen objecten op met de waarde `NoteProperty` voor de eigenschap **member type** .

De opdracht retourneert de eigenschap **bericht** van het object **EventLogRecord** .

### Voor beeld 5: objecten ophalen met een opgegeven eigenschap

In dit voor beeld worden objecten opgehaald die de eigenschap **MachineName** hebben in de uitvoer van een lijst met cmdlets.

De `$list` variabele bevat een lijst met cmdlets die moeten worden geëvalueerd. De instructie **foreach** roept elke opdracht aan en stuurt de resultaten naar `Get-Member` . De para meter **name** beperkt de resultaten van `Get-Member` aan leden met de naam **MachineName**.

```powershell
$list = "Get-Process", "Get-Service", "Get-Culture", "Get-PSDrive", "Get-ExecutionPolicy"
foreach ($cmdlet in $list) {& $cmdlet | Get-Member -Name MachineName}
```

```Output
   TypeName: System.Diagnostics.Process

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;}

   TypeName: System.Service.ServiceController#StartupType

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;set;}
```

De resultaten geven aan dat alleen objecten en service objecten verwerken een **MachineName** -eigenschap hebben.

### Voor beeld 6: leden voor een matrix ophalen

In dit voor beeld ziet u hoe u de leden van een matrix met objecten kunt vinden. Wanneer u een pipe en een matrix van objecten naar `Get-Member` , retourneert de cmdlet een leden lijst voor elk uniek object type in de matrix.
Als u de matrix doorgeeft met behulp van de para meter **input object** , wordt de matrix beschouwd als één object.

```powershell
$array = @(1,'hello')
$array | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType Definition
----        ---------- ----------
CompareTo   Method     int CompareTo(System.Object value), int CompareTo(int value), int ICompar...
Equals      Method     bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int...
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
GetTypeCode Method     System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method     bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method     byte IConvertible.ToByte(System.IFormatProvider provider)
...

   TypeName: System.String

Name                 MemberType            Definition
----                 ----------            ----------
Clone                Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo            Method                int CompareTo(System.Object value), int CompareTo(str...
Contains             Method                bool Contains(string value), bool Contains(string val...
CopyTo               Method                void CopyTo(int sourceIndex, char[] destination, int ...
EndsWith             Method                bool EndsWith(string value), bool EndsWith(string val...
EnumerateRunes       Method                System.Text.StringRuneEnumerator EnumerateRunes()
Equals               Method                bool Equals(System.Object obj), bool Equals(string va...
GetEnumerator        Method                System.CharEnumerator GetEnumerator(), System.Collect...
GetHashCode          Method                int GetHashCode(), int GetHashCode(System.StringCompa...
...
```

```powershell
Get-Member -InputObject $array
```

```Output
   TypeName: System.Object[]

Name           MemberType            Definition
----           ----------            ----------
Add            Method                int IList.Add(System.Object value)
Address        Method                System.Object&, System.Private.CoreLib, Version=4.0.0.0, Cu...
Clear          Method                void IList.Clear()
Clone          Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo      Method                int IStructuralComparable.CompareTo(System.Object other, Sy...
...
```

De `$array` variabele bevat een **Int32** -object en een **teken reeks** object, zoals gezien wanneer de matrix wordt gesluisd `Get-Member` . Wanneer `$array` wordt door gegeven met behulp van de para meter **input object** , worden `Get-Member` de leden van het type **object []** geretourneerd.

### Voor beeld 7: bepalen welke object eigenschappen u kunt instellen

In dit voor beeld ziet u hoe u kunt bepalen welke eigenschappen van een object kunnen worden gewijzigd.

```powershell
$File = Get-Item c:\test\textFile.txt
$File.PSObject.Properties | Where-Object isSettable | Select-Object -Property Name
```

```Output
Name
----
PSPath
PSParentPath
PSChildName
PSDrive
PSProvider
PSIsContainer
IsReadOnly
CreationTime
CreationTimeUtc
LastAccessTime
LastAccessTimeUtc
LastWriteTime
LastWriteTimeUtc
Attributes
```

## Parameters

### -Force

Voegt de intrinsieke leden en de **get_** van het door de compiler gegenereerde en **set_** -methoden toe aan de weer gave.
In de volgende lijst worden de eigenschappen beschreven die worden toegevoegd wanneer u de para meter **Force** gebruikt:

- `PSBase`: De oorspronkelijke eigenschappen van het .NET-object zonder extensie of aanpassing. Dit zijn de eigenschappen die voor de object klasse zijn gedefinieerd.
- `PSAdapted`: De eigenschappen en methoden die zijn gedefinieerd in het type systeem Power shell Extended.
- `PSExtended`: De eigenschappen en methoden die zijn toegevoegd aan de `Types.ps1xml` bestanden of door gebruik te maken van de `Add-Member` cmdlet.
- `PSObject`: De adapter die het basis object converteert naar een Power shell **PSObject** -object.
- `PSTypeNames`: Een lijst met object typen die het object beschrijven, in volg orde van specificiteit. Bij het format teren van het object zoekt Power shell naar de typen in de `Format.ps1xml` bestanden in de installatie directory van Power shell ( `$PSHOME` ). De opmaak definitie wordt gebruikt voor het eerste type dat wordt gevonden.

`Get-Member`Deze eigenschappen worden standaard in alle weer gaven opgehaald, behalve **basis** en **aangepast**, maar ze worden niet weer gegeven.

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

### -Input object

Hiermee geeft u het object op waarvan de leden worden opgehaald.

Het gebruik van de para meter **input object** is niet hetzelfde als het door sluizen van een object `Get-Member` . De verschillen zijn als volgt:

- Wanneer u een verzameling objecten naar een pipet `Get-Member` , worden `Get-Member` de leden van de afzonderlijke objecten in de verzameling opgehaald, zoals de eigenschappen van elke teken reeks in een matrix met teken reeksen.
- Wanneer u **input object** gebruikt om een verzameling objecten te verzenden, worden `Get-Member` de leden van de verzameling opgehaald, zoals de eigenschappen van de matrix in een matrix met teken reeksen.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Member type

Hiermee geeft u het lidtype-type op dat met deze cmdlet wordt opgehaald. De standaardwaarde is `All`.

De aanvaardbare waarden voor deze parameter zijn:

- `AliasProperty`
- `CodeProperty`
- `Property`
- `NoteProperty`
- `ScriptProperty`
- `Properties`
- `PropertySet`
- `Method`
- `CodeMethod`
- `ScriptMethod`
- `Methods`
- `ParameterizedProperty`
- `MemberSet`
- `Event`
- `Dynamic`
- `All`

Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag. U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter. De waarden kunnen worden door gegeven aan de **member type** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden. Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking. Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.

Zie [PSMemberTypes Enumeration (Engelstalig)](/dotnet/api/system.management.automation.psmembertypes)voor meer informatie over deze waarden.

Niet alle objecten hebben elk type lid. Als u een lidtype opgeeft dat het object niet heeft, retourneert Power shell een null-waarde. Als u verwante typen leden wilt ophalen, bijvoorbeeld alle uitgebreide leden, gebruikt u de **weer gave** -para meter. Als u de para meter **member type** met de para meters **static** of **View** gebruikt, `Get-Member` worden de leden opgehaald die deel uitmaken van beide sets.

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen van een of meer eigenschappen of methoden van het object op. `Get-Member` Hiermee worden alleen de opgegeven eigenschappen en methoden opgehaald.

Als u de para meter **name** gebruikt met de para meter **member type**, **View** of **static** , worden `Get-Member` alleen de leden opgehaald die voldoen aan de criteria van alle para meters.

Als u een statisch lid wilt ophalen op naam, gebruikt u de **statische** para meter met de **naam** parameter.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Static

Geeft aan dat met deze cmdlet alleen de statische eigenschappen en methoden van het object worden opgehaald. Statische eigenschappen en methoden worden gedefinieerd voor de object klasse, niet op een bepaalde instantie van de klasse.

Als u de **statische** para meter met de **weer gave** -para meter gebruikt, wordt de **weer gave** -para meter genegeerd.
Als u de **statische** para meter gebruikt met de para meter **member type** , worden `Get-Member` alleen de leden opgehaald die deel uitmaken van beide sets.

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

### -Weer geven

Hiermee geeft u op dat met deze cmdlet alleen bepaalde typen eigenschappen en-methoden worden opgehaald. Geef een of meer van de waarden op. De standaard waarde is **aangepast**, **uitgebreid**.

De aanvaardbare waarden voor deze parameter zijn:

- Baseer. Hiermee worden alleen de oorspronkelijke eigenschappen en methoden van het .NET-object (zonder extensie of aanpassing) opgehaald.
- Gebaseerd. Hiermee worden alleen de eigenschappen en methoden opgehaald die in het systeem eigen Power shell Extended type zijn gedefinieerd.
- Diakritische. Haalt alleen de eigenschappen en methoden op die zijn toegevoegd aan een `Types.ps1xml` bestand of met behulp van de- `Add-Member` cmdlet.
- Hele. Hiermee worden de leden in de basis-, aangepaste en uitgebreide weer gaven opgehaald.

De **weer gave** -para meter bepaalt welke leden worden opgehaald, niet alleen de weer gave van deze leden.

Gebruik de para meter **member type** om bepaalde leden typen, zoals script eigenschappen, op te halen. Als u de para meters **member type** en **View** in dezelfde opdracht gebruikt, worden `Get-Member` de leden die deel uitmaken van beide sets opgehaald. Als u de para meters **static** en **weer geven** in dezelfde opdracht gebruikt, wordt de **weer gave** -para meter genegeerd.

```yaml
Type: System.Management.Automation.PSMemberViewTypes
Parameter Sets: (All)
Aliases:
Accepted values: Extended, Adapted, Base, All

Required: False
Position: Named
Default value: Adapted, Extended
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### System. Management. Automation. PSObject

U kunt elk object door sluizen naar `Get-Member` .

## Uitvoerwaarden

### Micro soft. Power shell. commands. MemberDefinition

`Get-Member` retourneert een object voor elke eigenschap of methode die wordt opgehaald.

## Notities

U kunt informatie over een verzamelings object ophalen met behulp van de para meter **input object** of door het object, voorafgegaan door een komma, te gebruiken in `Get-Member` .

U kunt de `$This` Automatische variabele gebruiken in script blokken waarmee de waarden van nieuwe eigenschappen en methoden worden gedefinieerd. De `$This` variabele verwijst naar het exemplaar van het object waarnaar de eigenschappen en methoden worden toegevoegd. Zie about_Automatic_Variables voor meer informatie over de `$This` variabele [](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

Als u een object door geven dat een _type_ vertegenwoordigt, zoals een letterlijke type, bijvoorbeeld `[int]` , geeft u `Get-Member` informatie over het `[System.RuntimeType]` type. Wanneer u echter de **statische** para meter gebruikt, `Get-Member` retourneert de statische leden van het specifieke type dat door het `System.RuntimeType` exemplaar wordt vertegenwoordigd.

## Verwante koppelingen

[Lid toevoegen](Add-Member.md)
