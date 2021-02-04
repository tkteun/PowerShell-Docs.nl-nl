---
description: Hierin wordt beschreven hoe u klassen kunt gebruiken om uw eigen aangepaste typen te maken.
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: 7974ec49ebf27338da461cd57fb43cc0229b7323
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/21/2021
ms.locfileid: "98620044"
---
# <a name="about-classes"></a>Over klassen

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u klassen kunt gebruiken om uw eigen aangepaste typen te maken.

## <a name="long-description"></a>Lange beschrijving

Power shell 5,0 voegt een formele syntaxis toe om klassen en andere door de gebruiker gedefinieerde typen te definiëren. Dankzij de toevoeging van klassen kunnen ontwikkel aars en IT-professionals Power shell gebruiken voor een groter aantal use cases. Het vereenvoudigt de ontwikkeling van Power shell-artefacten en versnelt de dekking van beheer oppervlakken.

Een klassen declaratie is een blauw druk die wordt gebruikt om exemplaren van objecten te maken tijdens de uitvoering. Wanneer u een klasse definieert, is de naam van de klasse de naam van het type. Als u bijvoorbeeld een klasse met de naam **apparaat** declareert en een variabele initialiseert `$dev` naar een nieuw exemplaar van **apparaat**, `$dev` is een object of een exemplaar van het type **apparaat**. Elk exemplaar van het **apparaat** kan verschillende waarden in de eigenschappen hebben.

## <a name="supported-scenarios"></a>Ondersteunde scenario's

- Definieer aangepaste typen in Power shell met behulp van bekende object georiënteerde programmeer semantiek zoals klassen, eigenschappen, methoden, overname, enzovoort.
- Typen fout opsporing met behulp van de Power shell-taal.
- Met formele mechanismen uitzonde ringen genereren en verwerken.
- DSC-resources en de bijbehorende typen definiëren met behulp van de Power shell-taal.

## <a name="syntax"></a>Syntax

Klassen worden gedeclareerd met de volgende syntaxis:

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

Klassen worden geïnstantieerd met een van de volgende syntaxis:

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> Wanneer u de `[<class-name>]::new()` syntaxis gebruikt, zijn haakjes rond de naam van de klasse verplicht. De vier Kante haken geven een type definitie voor Power shell.

### <a name="example-syntax-and-usage"></a>Voorbeeld syntaxis en-gebruik

In dit voor beeld ziet u de minimale syntaxis die nodig is om een bruikbare klasse te maken.

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a>Klasse-eigenschappen

Eigenschappen zijn variabelen die worden gedeclareerd bij een klasse-bereik. Een eigenschap kan van een ingebouwd type of een exemplaar van een andere klasse zijn. Klassen hebben geen beperkingen voor het aantal eigenschappen dat ze hebben.

### <a name="example-class-with-simple-properties"></a>Voorbeeld klasse met eenvoudige eigenschappen

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a>Voor beelden van complexe typen in klasse-eigenschappen

In dit voor beeld wordt een lege **rack** klasse gedefinieerd met behulp **van de apparaatklasse** . Hieronder ziet u hoe u apparaten aan het rek kunt toevoegen en hoe u begint met een vooraf geladen rek.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a>Klasse-methoden

Met methoden worden de acties gedefinieerd die een klasse kan uitvoeren. Methoden kunnen para meters hebben die invoer gegevens opgeven. De methoden kunnen uitvoer retour neren. Gegevens die door een methode worden geretourneerd, kunnen elk gedefinieerd gegevens type zijn.

Wanneer u een methode voor een klasse definieert, verwijst u naar het huidige klassen object met behulp van de `$this` Automatische variabele. Hiermee krijgt u toegang tot eigenschappen en andere methoden die in de huidige klasse zijn gedefinieerd.

### <a name="example-simple-class-with-properties-and-methods"></a>Voor beeld van een eenvoudige klasse met eigenschappen en methoden

De **rack** klasse uitbreiden om apparaten toe te voegen aan of te verwijderen.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a>Uitvoer in klasse-methoden

Voor methoden moet een retour type zijn gedefinieerd. Als een methode geen uitvoer retourneert, moet het uitvoer type zijn `[void]` .

Bij klassen methoden worden er geen objecten verzonden naar de pijp lijn, behalve die in de `return` instructie vermeld. Er is geen onbedoelde uitvoer van de code naar de pijp lijn.

> [!NOTE]
> Dit wijkt fundamenteel af van de manier waarop Power shell-functies uitvoer afhandelen, waarbij alles naar de pijp lijn gaat.

Niet-afsluit fouten die naar de fout stroom zijn geschreven vanuit een klassen methode, worden niet door gegeven. U moet gebruiken `throw` om een afsluitende fout op te halen.
Met de `Write-*` cmdlets kunt u nog steeds vanuit een klassen methode naar de uitvoer stromen van Power shell schrijven. Dit moet echter worden vermeden, zodat de methode objecten alleen verzendt met behulp van de- `return` instructie.

### <a name="method-output"></a>Methode-uitvoer

In dit voor beeld ziet u geen onbedoelde uitvoer naar de pijp lijn vanuit klassen methoden, behalve op de- `return` instructie.

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a>Constructor

Met constructors kunt u standaard waarden instellen en object logica valideren op het moment dat u het exemplaar van de klasse maakt. Constructors hebben dezelfde naam als de klasse. Constructors kunnen argumenten hebben om de gegevens leden van het nieuwe object te initialiseren.

Er kunnen geen of meer constructors zijn gedefinieerd voor de klasse. Als er geen constructor is gedefinieerd, krijgt de klasse een standaard parameterloze constructor. Deze constructor initialiseert alle leden op hun standaard waarden. Object typen en teken reeksen krijgen Null-waarden. Wanneer u een constructor definieert, wordt er geen standaard parameterloze constructor gemaakt. Maak een parameterloze constructor als deze nodig is.

### <a name="constructor-basic-syntax"></a>Basis syntaxis van constructor

In dit voor beeld wordt de apparaatklasse gedefinieerd met eigenschappen en een constructor.
Als u deze klasse wilt gebruiken, moet de gebruiker waarden opgeven voor de para meters die worden weer gegeven in de constructor.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a>Voor beeld met meerdere Constructors

In dit voor beeld wordt **de apparaatklasse** gedefinieerd met eigenschappen, een standaardconstructor en een constructor om het exemplaar te initialiseren.

De standaardconstructor stelt het **merk** in op **ongedefinieerd** en verlaat het **model** en de **leverancier-SKU** met Null-waarden.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a>Verborgen kenmerk

Het `hidden` kenmerk verbergt een eigenschap of methode. De eigenschap of methode is nog steeds toegankelijk voor de gebruiker en is beschikbaar in alle bereiken waarin het object beschikbaar is. Verborgen leden worden verborgen in de `Get-Member` cmdlet en kunnen niet worden weer gegeven met Tab-aanvulling of IntelliSense buiten de klassedefinitie.

Zie [About_hidden](About_hidden.md)voor meer informatie.

### <a name="example-using-hidden-attributes"></a>Voor beeld met verborgen kenmerken

Wanneer een **rek** -object wordt gemaakt, is het aantal sleuven voor apparaten een vaste waarde die op geen enkel moment mag worden gewijzigd. Deze waarde is bekend tijdens het maken.

Met behulp van het kenmerk Hidden kan de ontwikkelaar het aantal sleuven verbergen en wordt voor komen dat onbedoeld de grootte van het rek wijzigt.

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

De eigenschap voor de **sleuf** wordt niet weer gegeven in de `$r1` uitvoer. De grootte is echter gewijzigd door de constructor.

## <a name="static-attribute"></a>Statisch kenmerk

Het `static` kenmerk definieert een eigenschap of een methode die voor komt in de klasse en waarvoor geen exemplaar is vereist.

Een statische eigenschap is altijd beschikbaar, onafhankelijk van klasse-instantiëring. Een statische eigenschap wordt gedeeld in alle instanties van de klasse. Een statische methode is altijd beschikbaar. Alle statische eigenschappen Live voor de hele sessie duur.

### <a name="example-using-static-attributes-and-methods"></a>Voor beeld van het gebruik van statische kenmerken en methoden

Ga ervan uit dat de racks die hier worden geïnstantieerd, zich in uw Data Center bevinden. Daarom wilt u de rekken in uw code bijhouden.

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a>Statische eigenschap en methode voor testen bestaan

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

U ziet dat het aantal racks telkens wordt verhoogd wanneer u dit voor beeld uitvoert.

## <a name="property-validation-attributes"></a>Kenmerken van eigenschappen validatie

Met validatie kenmerken kunt u testen of waarden die zijn gegeven aan eigenschappen voldoen aan gedefinieerde vereisten. Validatie wordt geactiveerd zodra de waarde is toegewezen. Zie [about_functions_advanced_parameters](about_functions_advanced_parameters.md).

### <a name="example-using-validation-attributes"></a>Voor beeld met validatie kenmerken

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a>Overname in Power shell-klassen

U kunt een klasse uitbreiden door een nieuwe klasse te maken die van een bestaande klasse is afgeleid. De afgeleide klasse neemt de eigenschappen van de basis klasse over. U kunt methoden en eigenschappen indien nodig toevoegen of onderdrukken.

Power shell biedt geen ondersteuning voor meerdere overname. Klassen kunnen niet overnemen van meer dan een klasse. U kunt echter wel interfaces voor dat doel gebruiken.

Overname-implementatie wordt gedefinieerd door de `:` operator; wat betekent dat deze klasse moet worden uitgebreid of dat deze interfaces worden geïmplementeerd. De afgeleide klasse moet altijd links in de klassen declaratie staan.

### <a name="example-using-simple-inheritance-syntax"></a>Voor beeld van eenvoudige overname syntaxis

In dit voor beeld ziet u de eenvoudige syntaxis van Power shell-klassen overname.

```powershell
Class Derived : Base {...}
```

In dit voor beeld ziet u overname met een interface declaratie die afkomstig is van de basis klasse.

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a>Voor beeld van eenvoudige overname in Power shell-klassen

In dit voor beeld zijn de **rack** -en **apparaatklassen** die in de voor gaande voor beelden worden gebruikt, beter gedefinieerd voor: Vermijd het gebruik van herhalingen van eigenschappen, het beter uitlijnen van algemene eigenschappen en het opnieuw gebruiken van algemene bedrijfs logica.

De meeste objecten in het Data Center zijn bedrijfs middelen, wat zinvol is om ze te volgen als activa. Apparaattypen worden gedefinieerd door de `DeviceType` opsomming. zie [about_Enum](about_Enum.md) voor meer informatie over inventarisaties.

In ons voor beeld worden alleen `Rack` `ComputeServer` de uitbrei dingen voor de klasse gedefinieerd `Device` .

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a>Opbouw functie voor basis klassen aanroepen

Als u een basis klasse-constructor wilt aanroepen vanuit een subklasse, voegt u het `base` tref woord toe.

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a>Methoden van basis klasse aanroepen

Als u bestaande methoden in subklassen wilt overschrijven, declareert u methoden met dezelfde naam en hand tekening.

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

Als u basis klassen methoden wilt aanroepen vanuit overschreven implementaties, moet u een cast-conversie uitvoeren naar de basis klasse ([baseclass] $this) bij het aanroepen.

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a>Overnemen van interfaces

Power shell-klassen kunnen een interface implementeren met dezelfde overname syntaxis die wordt gebruikt om basis klassen uit te breiden. Omdat interfaces meerdere overname toestaan, kan een Power shell-klasse die een interface implementeert, overnemen van meerdere typen door de type namen na de dubbele punt () te scheiden door `:` komma's ( `,` ). Een Power shell-klasse die een interface implementeert, moet alle leden van die interface implementeren. Als u de implementatie-interface leden weglaat, treedt er een parseringsfout op in het script.

> [!NOTE]
> Power shell biedt momenteel geen ondersteuning voor het declareren van nieuwe interfaces in het Power shell-script.

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a>Klassen importeren uit een Power shell-module

`Import-Module` en de `#requires` instructie importeren alleen de module functies, aliassen en variabelen, zoals gedefinieerd door de module. Klassen zijn niet geïmporteerd. `using module`Met de instructie worden de klassen geïmporteerd die in de module zijn gedefinieerd. Als de module niet in de huidige sessie is geladen, `using` mislukt de instructie. Zie about_Using voor meer informatie over de `using` - [](about_Using.md)instructie.

`using module`Met de instructie worden klassen uit de hoofd module ( `ModuleToProcess` ) van een script module of binaire module geïmporteerd. Er worden niet consistent klassen geïmporteerd die zijn gedefinieerd in geneste modules of klassen die zijn gedefinieerd in scripts die met een punt zijn gebrond in de module. Klassen die u beschikbaar wilt maken voor gebruikers buiten de module, moeten worden gedefinieerd in de hoofd module.

## <a name="loading-newly-changed-code-during-development"></a>Nieuwe code laden tijdens de ontwikkeling

Tijdens de ontwikkeling van een script module is het gebruikelijk om wijzigingen aan te brengen in de code en vervolgens de nieuwe versie van de module te laden met behulp van `Import-Module` de para meter **Force** . Dit werkt alleen voor wijzigingen in functies in de hoofd module. `Import-Module` herlaadt geen geneste modules. Het is ook niet mogelijk om bijgewerkte klassen te laden.

Om ervoor te zorgen dat u de meest recente versie gebruikt, moet u de module uit het geheugen verwijderen met de `Remove-Module` cmdlet. `Remove-Module` Hiermee verwijdert u de hoofd module, alle geneste modules en klassen die in de modules zijn gedefinieerd. Daarna kunt u de module en de klassen opnieuw laden met behulp van `Import-Module` en de- `using module` instructie.

Een andere algemene ontwikkelings praktijk is het scheiden van uw code in verschillende bestanden. Als u werkt met een bestand dat gebruikmaakt van klassen die in een andere module zijn gedefinieerd, moet u de- `using module` instructie gebruiken om ervoor te zorgen dat de functies de klassen definities hebben die nodig zijn.

## <a name="the-psreference-type-is-not-supported-with-class-members"></a>Het PSReference-type wordt niet ondersteund voor klasse-leden

Het gebruik `[ref]` van het type cast met een klassetype is op de achtergrond mislukt. Api's die gebruikmaken `[ref]` van para meters kunnen niet worden gebruikt met klassen leden. De **PSReference** -klasse is ontworpen ter ondersteuning van COM-objecten. COM-objecten bevatten gevallen waarin u een waarde in moet door geven.

`[ref]`Zie [PSReference-klasse](/dotnet/api/system.management.automation.psreference)voor meer informatie over het type.

## <a name="see-also"></a>Zie ook

- [About_hidden](About_hidden.md)
- [about_Enum](about_Enum.md)
- [about_Language_Keywords](about_language_keywords.md)
- [about_Methods](about_methods.md)
- [about_Using](about_using.md)
