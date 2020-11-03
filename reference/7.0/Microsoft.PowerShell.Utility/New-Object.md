---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: baaff5a02cc583394019d2fe79a1b4d6210473af
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249387"
---
# New-Object

## SAMENVATTING
Hiermee maakt u een exemplaar van een Microsoft .NET Framework of COM-object.

## SYNTAXIS

### Net (standaard)

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### Com

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## BESCHRIJVING

`New-Object`Met de cmdlet maakt u een exemplaar van een .NET Framework of COM-object.

U kunt het type van een .NET Framework-klasse of een ProgID van een COM-object opgeven. Standaard typt u de volledig gekwalificeerde naam van een .NET Framework klasse en de cmdlet retourneert een verwijzing naar een exemplaar van die klasse. Als u een exemplaar van een COM-object wilt maken, gebruikt u de para meter **ComObject** en geeft u de ProgID van het object op als waarde.

## VOORBEELDEN

### Voor beeld 1: een System. Version-object maken

In dit voor beeld wordt een **System. version** -object gemaakt met de teken reeks "1.2.3.4" als constructor.

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### Voor beeld 2: een Internet Explorer COM-object maken

In dit voor beeld worden twee exemplaren gemaakt van het COM-object dat de toepassing Internet Explorer vertegenwoordigt. De eerste instantie gebruikt de hash-tabel **Property** para meter om de methode **Navigate2** aan te roepen en de eigenschap **Visible** van het object in te stellen om `$True` de toepassing zichtbaar te maken.
Het tweede exemplaar krijgt dezelfde resultaten als de afzonderlijke opdrachten.

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### Voor beeld 3: de strikte para meter gebruiken om een niet-afsluit fout te genereren

In dit voor beeld wordt gedemonstreerd dat het toevoegen van de **strikte** para meter zorgt ervoor dat de `New-Object` cmdlet een niet-afsluit fout genereert wanneer het COM-object gebruikmaakt van een interop-assembly.

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### Voor beeld 4: een COM-object maken voor het beheren van Windows Desktop

In dit voor beeld ziet u hoe u een COM-object maakt en gebruikt voor het beheren van uw Windows-bureau blad.

De eerste opdracht maakt gebruik van de para meter **ComObject** van de `New-Object` cmdlet om een COM-object te maken met de **shell. Application** ProgID. Het resulterende object wordt opgeslagen in de `$ObjShell` variabele. Met de tweede opdracht `$ObjShell` wordt de variabele door sluizen naar de `Get-Member` cmdlet, waarin de eigenschappen en methoden van het COM-object worden weer gegeven. De methoden zijn onder andere de methode **ToggleDesktop** . Met de derde opdracht wordt de methode **ToggleDesktop** van het object aangeroepen om de geopende vensters op het bureau blad te minimaliseren.

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### Voor beeld 5: meerdere argumenten door geven aan een constructor

In dit voor beeld ziet u hoe u een object maakt met een constructor waarvoor meerdere para meters worden gebruikt. De para meters moeten in een matrix worden geplaatst wanneer de para meter **argument List** wordt gebruikt.

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

Power shell verbindt elk lid van de matrix met een para meter van de constructor.

> [!NOTE]
> In dit voor beeld wordt de para meter splatting gebruikt voor de Lees baarheid. Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.

### Voor beeld 6: een constructor aanroepen die een matrix als één para meter gebruikt

In dit voor beeld ziet u hoe u een object maakt met een constructor die een para meter gebruikt die een matrix of verzameling is. De matrix parameter moet in een andere matrix worden geplaatst.

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

De eerste poging om het object in dit voor beeld te maken, mislukt. Power Shell heeft geprobeerd de drie leden van `$array` te binden aan de para meters van de constructor, maar de constructor heeft geen drie para meter. `$array`Door in een andere matrix in te pakken, wordt voor komen dat Power shell de drie leden van `$array` de para meters van de constructor bindt.

## PARAMETERS

### -Argument List

Hiermee geeft u een matrix op met argumenten die moeten worden door gegeven aan de constructor van de .NET Framework klasse. Als de constructor één para meter gebruikt die een matrix is, moet u die para meter in een andere matrix afronden. Bijvoorbeeld:

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

De alias voor **argument List** is **args**.

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComObject

Hiermee geeft u de programmatische id (ProgID) van het COM-object op.

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

Stelt eigenschaps waarden in en roept methoden van het nieuwe object aan.

Voer een hash-tabel in waarin de sleutels de namen van eigenschappen of methoden zijn en de waarden zijn eigenschaps waarden of methode argumenten. `New-Object` maakt het object en stelt elke eigenschaps waarde in en roept elke methode aan in de volg orde waarin ze worden weer gegeven in de hash-tabel.

Als het nieuwe object is afgeleid van de klasse **PSObject** en u een eigenschap opgeeft die niet voor komt in het object, `New-Object` voegt de opgegeven eigenschap toe aan het object als een NoteProperty. Als het object geen **PSObject** is, wordt door de opdracht een niet-afsluit fout gegenereerd.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strikte

Geeft aan dat de cmdlet een niet-afsluit fout genereert wanneer een COM-object dat u probeert te maken, gebruikmaakt van een interop-assembly. Deze functie onderscheidt de werkelijke COM-objecten van .NET Framework objecten met COM-aanroep bare wrappers.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Hiermee geeft u de volledig gekwalificeerde naam van de .NET Framework klasse op. U kunt niet zowel de para meter **TypeName** als de para meter **ComObject** opgeven.

```yaml
Type: System.String
Parameter Sets: Net
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

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Object

`New-Object` retourneert het object dat wordt gemaakt.

## OPMERKINGEN

- `New-Object` biedt de meest gebruikte functionaliteit van de functie voor VBScript CreateObject. Een instructie zoals `Set objShell = CreateObject("Shell.Application")` in VBScript kan worden vertaald `$objShell = New-Object -COMObject "Shell.Application"` in Power shell.
- `New-Object` uitbrei ding van de functionaliteit die beschikbaar is in de Windows Script Host-omgeving door eenvoudig te werken met .NET Framework objecten vanaf de opdracht regel en in scripts.

## GERELATEERDE KOPPELINGEN

[about_Object_Creation](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[Compare-object](Compare-Object.md)

[Groep-object](Group-Object.md)

[Meting object](Measure-Object.md)

[Select-Object](Select-Object.md)

[Sorteer object](Sort-Object.md)

[T-object](Tee-Object.md)
