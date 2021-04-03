---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: 3696073b2135438c3645d855e09932b44d199963
ms.sourcegitcommit: c91f79576bc54e162bcc7adf78026417b2776687
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274099"
---
# Add-Type

## SAMENVATTING
Hiermee wordt een Microsoft .NET klasse toegevoegd aan een Power shell-sessie.

## SYNTAXIS

### FromSource (standaard)

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromMember

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromPath

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromLiteralPath

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromAssemblyName

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## BESCHRIJVING

`Add-Type`Met de cmdlet kunt u een Microsoft .net kern klasse definiëren in uw Power shell-sessie. U kunt vervolgens objecten instantiëren met behulp van de `New-Object` -cmdlet en de objecten gebruiken op dezelfde manier als u een .net core-object zou gebruiken. Als u een `Add-Type` opdracht aan uw Power shell-profiel toevoegt, is de klasse beschikbaar in alle Power shell-sessies.

U kunt het type opgeven door een bestaande assembly-of broncode bestand op te geven, of u kunt de bron code inline opgeven of in een variabele opslaan. U kunt zelfs een methode opgeven en `Add-Type` de klasse definiëren en genereren. In Windows kunt u deze functie gebruiken om aanroepen van platform Invoke (P/Invoke) aan onbeheerde functies in Power shell te maken. Als u de bron code opgeeft, `Add-Type` compileert de opgegeven bron code en genereert een assembly in het geheugen die de nieuwe .net-kern typen bevat.

U kunt de para meters van gebruiken `Add-Type` om een alternatieve taal en een andere compiler op te geven, C# is de standaard opties voor compiler, assembly-afhankelijkheden, de klasse-naam ruimte, de namen van het type en de resulterende assembly.

Vanaf Power shell 7 `Add-Type` compileert niet een type als er al een type met dezelfde naam bestaat. Zoekt ook `Add-Type` naar assembly's in een `ref` map in de map met `pwsh.dll` .

## VOORBEELDEN

### Voor beeld 1: een .NET-type toevoegen aan een sessie

In dit voor beeld wordt de klasse **BasicTest** toegevoegd aan de sessie door de bron code op te geven die is opgeslagen in een variabele. De klasse **BasicTest** wordt gebruikt om gehele getallen toe te voegen, een object te maken en gehele getallen te vermenigvuldigen.

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

De `$Source` variabele slaat de bron code voor de klasse op. Het type heeft een statische methode met de naam `Add` en een niet-statische methode met de naam `Multiply` .

De- `Add-Type` cmdlet voegt de klasse toe aan de sessie. Omdat de inline-bron code wordt gebruikt, gebruikt de opdracht de para meter **TypeDefinition** om de code in de variabele op te geven `$Source` .

De `Add` statische methode van de klasse **BasicTest** gebruikt de tekens met dubbele punt komma's ( `::` ) om een statisch lid van de klasse op te geven. De gehele getallen worden toegevoegd en de som wordt weer gegeven.

`New-Object`Met de cmdlet wordt een instantie van de klasse **BasicTest** geïnstantieerd. Het nieuwe object wordt opgeslagen in de `$BasicTestObject` variabele.

`$BasicTestObject` maakt gebruik van de- `Multiply` methode. De gehele getallen worden vermenigvuldigd en het product wordt weer gegeven.

### Voor beeld 2: een toegevoegd type onderzoeken

In dit voor beeld wordt de `Get-Member` cmdlet gebruikt om de objecten te onderzoeken die de `Add-Type` `New-Object` cmdlets en zijn gemaakt in **voor beeld 1**.

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

Met de `Get-Member` cmdlet worden het type en de leden van de klasse **BasicTest** opgehaald die `Add-Type` aan de sessie zijn toegevoegd. De `Get-Member` opdracht toont aan dat het een **System. RuntimeType** -object is, dat is afgeleid van de klasse **System. object** .

Met de `Get-Member` **statische** para meter worden de statische eigenschappen en methoden van de klasse **BasicTest** opgehaald. In de uitvoer ziet u dat de- `Add` methode is opgenomen.

De `Get-Member` cmdlet haalt de leden van het object op dat is opgeslagen in de `$BasicTestObject` variabele.
`$BasicTestObject` is gemaakt met behulp van de `New-Object` cmdlet met de **BasicTest** -klasse. De uitvoer laat zien dat de waarde van de `$BasicTestObject` variabele een exemplaar van de klasse **BasicTest** is en dat het een lid bevat met de naam `Multiply` .

### Voor beeld 3: typen uit een assembly toevoegen

In dit voor beeld worden de klassen van de `NJsonSchema.dll` Assembly toegevoegd aan de huidige sessie.

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

`Set-Location` maakt gebruik van de para meter **Path** om de variabele op te geven `$PSHOME` . De variabele verwijst naar de Power shell-installatie directory waar het DLL-bestand zich bevindt.

De `$AccType` variabele slaat een object op dat is gemaakt met de `Add-Type` cmdlet. `Add-Type` de **assemblyname** -para meter wordt gebruikt om de naam van de assembly op te geven. `*`Met het Joker teken sterretje () kunt u de juiste assembly ophalen, zelfs wanneer u niet zeker bent van de naam of de spelling. De para meter **PassThru** genereert objecten die de klassen vertegenwoordigen die aan de sessie worden toegevoegd.

### Voor beeld 4: systeem eigen Windows-Api's aanroepen

In dit voor beeld ziet u hoe u systeem eigen Windows-Api's aanroept in Power shell. `Add-Type` maakt gebruik van het mechanisme voor het aanroepen van het platform (P/Invoke) om een functie in `User32.dll` vanuit Power shell aan te roepen. Dit voor beeld werkt alleen op computers met het Windows-besturings systeem.

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

De `$Signature` variabele slaat de C#-hand tekening van de `ShowWindowAsync` functie op. Om ervoor te zorgen dat de resulterende methode zichtbaar is in een Power shell-sessie, `public` is het sleutel woord toegevoegd aan de standaard handtekening. Zie de [functie ShowWindowAsync](/windows/win32/api/winuser/nf-winuser-showwindowasync)voor meer informatie.

De `$ShowWindowAsync` variabele slaat het object op dat door de `Add-Type` para meter **PassThru** is gemaakt.
De `Add-Type` cmdlet voegt de `ShowWindowAsync` functie als een statische methode toe aan de Power shell-sessie. De opdracht gebruikt de para meter **MemberDefinition** om de definitie van de methode op te geven die is opgeslagen in de `$Signature` variabele. De opdracht maakt gebruik van de para meters **naam** en naam **ruimte** om een naam en naam ruimte voor de klasse op te geven. De para meter **PassThru** genereert een object dat de typen vertegenwoordigt.

De nieuwe `ShowWindowAsync` statische methode wordt gebruikt in de opdrachten om de Power shell-console te minimaliseren en te herstellen. De methode heeft twee para meters: de venster ingang en een geheel getal dat aangeeft hoe het venster wordt weer gegeven.

Om de Power shell-console te minimaliseren, `ShowWindowAsync` gebruikt de `Get-Process` cmdlet met de `$PID` Automatische variabele om het proces op te halen dat als host fungeert voor de huidige Power shell-sessie. Vervolgens wordt de eigenschap **MainWindowHandle** van het huidige proces en een waarde van gebruikt `2` die de waarde vertegenwoordigt `SW_MINIMIZE` .

Als u het venster wilt herstellen, `ShowWindowAsync` gebruikt u een waarde van `4` voor de venster positie, waarmee de waarde wordt aangeduid `SW_RESTORE` .

Gebruik de waarde van dat vertegenwoordigt om het venster te maximaliseren `3` `SW_MAXIMIZE` .

## PARAMETERS

### -Assemblyname

Hiermee geeft u de naam op van een assembly die de typen bevat. `Add-Type` neemt de typen van de opgegeven assembly op. Deze para meter is vereist wanneer u typen maakt op basis van de naam van een assembly.

Voer de volledige of eenvoudige naam in, ook wel bekend als de gedeeltelijke naam, van een assembly. Joker tekens zijn toegestaan in de naam van de assembly. Als u een eenvoudige of gedeeltelijke naam opgeeft, wordt `Add-Type` deze omgezet in de volledige naam, waarna de volledige naam wordt gebruikt om de assembly te laden.

Deze para meter accepteert geen pad of bestands naam. Als u het pad naar het bestand van de assembly-Dynamic-Link Library (DLL) wilt invoeren, gebruikt u de para meter **Path** .

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -CompilerOptions

Hiermee geeft u de opties voor de bron code compiler op. Deze opties worden zonder revisie naar de compiler verzonden.

Met deze para meter kunt u de compiler omleiden om een uitvoerbaar bestand te genereren, resources in te sluiten of opdracht regel opties in te stellen, zoals de `/unsafe` optie.

U kunt de para meters **CompilerOptions** en **ReferencedAssemblies** niet in dezelfde opdracht gebruiken.

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWarnings

Waarschuwingen voor compileren worden genegeerd. Gebruik deze para meter om te voor komen dat `Add-Type` waarschuwingen van het Compileer programma worden verwerkt als fouten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Taal

Hiermee geeft u de taal op die wordt gebruikt in de bron code. De acceptabele waarde voor deze para meter is **csharp**.

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad op naar broncode bestanden of assembly-DLL-bestanden die de typen bevatten. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt zoals deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberDefinition

Hiermee geeft u nieuwe eigenschappen of methoden voor de klasse op. `Add-Type` genereert de sjabloon code die nodig is om de eigenschappen of methoden te ondersteunen.

In Windows kunt u deze functie gebruiken om aanroepen van platform Invoke (P/Invoke) aan onbeheerde functies in Power shell te maken.

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam op van de klasse die u wilt maken. Deze para meter is vereist voor het genereren van een type uit een definitie van een lid.

De type naam en naam ruimte moeten uniek zijn binnen een sessie. U kunt een type niet verwijderen of wijzigen.
Als u de code voor een type wilt wijzigen, moet u de naam wijzigen of een nieuwe Power shell-sessie starten.
Anders mislukt de opdracht.

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Naam ruimte

Hiermee geeft u een naam ruimte voor het type op.

Als deze para meter niet is opgenomen in de opdracht, wordt het type gemaakt in de naam ruimte **micro soft. Power shell. commands. AddType. AutoGeneratedTypes** . Als de para meter in de opdracht wordt opgenomen met een lege teken reeks waarde of een waarde van `$Null` , wordt het type gegenereerd in de globale naam ruimte.

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputAssembly

Hiermee wordt een DLL-bestand voor de assembly gegenereerd met de opgegeven naam op de locatie. Voer een optioneel pad en een bestands naam in. Joker tekens zijn toegestaan. `Add-Type`De assembly wordt standaard alleen in het geheugen gegenereerd.

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Output type

Hiermee geeft u het uitvoer type van de uitvoer-assembly op. Standaard is geen uitvoer type opgegeven. Deze para meter is alleen geldig wanneer een uitvoer-assembly is opgegeven in de opdracht. Zie [OutputAssemblyType Enumeration (Engelstalig)](/dotnet/api/microsoft.powershell.commands.outputassemblytype)voor meer informatie over de waarden.

De acceptabele waarden voor deze para meter zijn als volgt:

- ConsoleApplication
- Bibliotheek
- WindowsApplication

> [!IMPORTANT]
> Vanaf Power shell 7,1 `ConsoleApplication` en `WindowsApplication` worden niet ondersteund en Power shell genereert een afsluit fout als deze zijn opgegeven als waarden voor de **output** type-para meter.

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een **System. runtime** -object dat de typen vertegenwoordigt die zijn toegevoegd. Deze cmdlet genereert standaard geen uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar broncode bestanden of assembly-DLL-bestanden die de typen bevatten.

Als u bron code bestanden verzendt, `Add-Type` compileert de code in de bestanden en maakt een assembly in het geheugen van de typen. De bestands extensie die in de waarde van het **pad** is opgegeven, bepaalt de compiler die `Add-Type` gebruikt.

Als u een assembly-bestand verzendt, `Add-Type` neemt de typen van de assembly toe. Als u een assembly in het geheugen of de Global Assembly Cache wilt opgeven, gebruikt u de **assemblyname** -para meter.

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferencedAssemblies

Hiermee geeft u de assembly's op waarvan het type afhankelijk is. `Add-Type`Verwijzingen en zijn standaard `System.dll` `System.Management.Automation.dll` . In de assembly's die u opgeeft met behulp van deze para meter wordt een aanvulling op de standaard-assembly's verwezen.

Vanaf Power shell 6 bevat **ReferencedAssemblies** niet de standaard-.net-assembly's. U moet in de waarde die wordt door gegeven aan deze para meter een specifieke verwijzing naar deze bevatten.

U kunt de para meters **CompilerOptions** en **ReferencedAssemblies** niet in dezelfde opdracht gebruiken.

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeDefinition

Hiermee geeft u de bron code die de type definities bevat. Voer de bron code in een teken reeks of hier in, of voer een variabele in die de bron code bevat. Zie [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.

Neem een naam ruimte declaratie op in uw type definitie. Als u de naam ruimte declaratie weglaat, kan uw type dezelfde naam hebben als een ander type of de snelkoppeling voor een ander type, waardoor een onbedoelde overschrijving wordt veroorzaakt. Als u bijvoorbeeld een type met de naam **Exception** definieert, zullen scripts die **uitzonde ring** gebruiken als de snelkoppeling voor **System. Exception** , mislukken.

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UsingNamespace

Hiermee geeft u andere naam ruimten op die voor de klasse zijn vereist. Dit is vergelijkbaar met het sleutel woord C# `Using` .

Maakt standaard `Add-Type` een verwijzing naar de **systeem** naam ruimte. Wanneer de para meter **MemberDefinition** wordt gebruikt, wordt `Add-Type` standaard ook naar de **System. runtime. InteropServices** -naam ruimte verwezen. Er wordt verwezen naar de naam ruimten die u toevoegt met behulp van de para meter **UsingNamespace** , naast de standaard naam ruimten.

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar beneden verplaatsen in de pijp lijn `Add-Type` .

## UITVOER

### Geen of System. type

Wanneer u de para meter **PassThru** gebruikt, `Add-Type` retourneert een **System. type** -object dat het nieuwe type vertegenwoordigt. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

De typen die u toevoegt, zijn alleen aanwezig in de huidige sessie. Als u de typen in alle sessies wilt gebruiken, voegt u deze toe aan uw Power shell-profiel. Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie over het profiel.

Type namen en naam ruimten moeten uniek zijn binnen een sessie. U kunt een type niet verwijderen of wijzigen. Als u de code voor een type moet wijzigen, moet u de naam wijzigen of een nieuwe Power shell-sessie starten.
Anders mislukt de opdracht.

In Windows Power shell (versie 5,1 en lager) moet u gebruiken `Add-Type` voor alles wat nog niet is geladen. Dit geldt meestal voor assembly's die zijn gevonden in de GAC (Global assembly cache).
In Power shell 6 en hoger is er geen GAC, waardoor Power shell zijn eigen assembly's installeert in `$PSHome` .
Deze assembly's worden automatisch op aanvraag geladen, dus u hoeft ze niet te gebruiken `Add-Type` om ze te laden. Het gebruik van `Add-Type` is echter nog steeds toegestaan om scripts impliciet compatibel te maken met elke versie van Power shell.

Assembly's in de GAC kunnen worden geladen op type naam, in plaats van op pad. Voor het laden van assembly's vanuit een wille keurig pad is vereist `Add-Type` , omdat deze assembly's niet automatisch kunnen worden geladen.

## GERELATEERDE KOPPELINGEN

[about_Profiles](../Microsoft.PowerShell.Core/About/about_profiles.md)

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Lid toevoegen](Add-Member.md)

[New-Object](New-Object.md)

[OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[Platform aanroepen (P/Invoke)](/dotnet/standard/native-interop/pinvoke)

[Where-object](../Microsoft.PowerShell.Core/Where-Object.md)
