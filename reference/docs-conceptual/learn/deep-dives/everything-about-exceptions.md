---
title: Alles wat u wilt weten over uitzonde ringen
description: Het afhandelen van fouten is slechts een deel van de levens duur van het schrijven van code.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fd3ddacbf14d1faeee98682697161f86c6ff0c72
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149878"
---
# <a name="everything-you-wanted-to-know-about-exceptions"></a>Alles wat u wilt weten over uitzonde ringen

Het afhandelen van fouten is slechts een deel van de levens duur van het schrijven van code. We kunnen de voor waarden voor het verwachte gedrag vaak controleren en valideren. Wanneer het onverwachte gebeurt, gaan we uitzonde ringen verwerken. U kunt uitzonde ringen die zijn gegenereerd door de code van andere gebruikers eenvoudig afhandelen of u kunt uw eigen uitzonde ringen genereren zodat anderen deze kunnen verwerken.

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] . Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [PowerShellExplained.com][].

## <a name="basic-terminology"></a>Basis terminologie

We moeten enkele basis termen best rijken voordat we naar deze functie gaan.

### <a name="exception"></a>Uitzondering

Een uitzonde ring is een gebeurtenis die wordt gemaakt wanneer het probleem niet kan worden opgelost met de normale fout afhandeling.
Als u een getal wilt delen door nul of als er onvoldoende geheugen beschikbaar is, zijn er voor beelden van iets dat een uitzonde ring veroorzaakt. Soms maakt de auteur van de code die u gebruikt uitzonde ringen voor bepaalde problemen wanneer deze zich voordoen.

### <a name="throw-and-catch"></a>Genereren en Catchiseren

Wanneer er een uitzonde ring optreedt, zeggen we dat er een uitzonde ring wordt gegenereerd. Als u een gegenereerde uitzonde ring wilt verwerken, moet u deze opvangen. Als er een uitzonde ring wordt gegenereerd en deze niet wordt onderschept door iets, stopt het uitvoeren van het script.

### <a name="the-call-stack"></a>De aanroep stack

De aanroep stack is de lijst met functies die elkaar hebben aangeroepen. Wanneer een functie wordt aangeroepen, wordt deze toegevoegd aan de stack of aan de bovenkant van de lijst. Wanneer de functie wordt afgesloten of geretourneerd, wordt deze uit de stack verwijderd.

Wanneer er een uitzonde ring wordt gegenereerd, wordt de aanroep stack gecontroleerd om een uitzonderings-handler te ondervangen.

### <a name="terminating-and-non-terminating-errors"></a>Afsluitende en niet-afsluit fouten

Een uitzonde ring is doorgaans een afsluit fout. Een gegenereerde uitzonde ring wordt onderschept of de huidige uitvoering wordt beëindigd. Standaard wordt een niet-afsluit fout gegenereerd door en wordt er `Write-Error` een fout aan de uitvoer stroom toegevoegd zonder een uitzonde ring te genereren.

`Write-Error`U moet dit doen omdat en andere niet-afsluit fouten de niet activeren `catch` .

### <a name="swallowing-an-exception"></a>Een uitzonde ring inslikken

Dit is het geval wanneer u een fout ondervangt die alleen wordt onderdrukt. Doe dit met een waarschuwing omdat het zeer lastig is om problemen met het oplossen van problemen op te lossen.

## <a name="basic-command-syntax"></a>Basis syntaxis van opdracht

Hier volgt een kort overzicht van de standaard syntaxis voor het afhandelen van uitzonde ringen in Power shell.

### <a name="throw"></a>Sprong

We hebben een uitzonde ring gegenereerd met het tref woord om onze eigen uitzonderings gebeurtenis te maken `throw` .

```powershell
function Do-Something
{
    throw "Bad thing happened"
}
```

Hiermee maakt u een runtime-uitzonde ring die een afsluit fout vormt. Het wordt verwerkt door een `catch` in een aanroepende functie of sluit het script af met een bericht als dit.

```powershell
PS> Do-Something

Bad thing happened
At line:1 char:1
+ throw "Bad thing happened"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Bad thing happened:String) [], RuntimeException
    + FullyQualifiedErrorId : Bad thing happened
```

#### <a name="write-error--erroraction-stop"></a>Schrijf fout-Error Action stoppen

Ik heb genoteerd dat `Write-Error` standaard geen afsluit fout wordt gegenereerd. Als u opgeeft `-ErrorAction Stop` , wordt er `Write-Error` een afsluit fout gegenereerd die kan worden verwerkt met een `catch` .

```powershell
Write-Error -Message "Houston, we have a problem." -ErrorAction Stop
```

Hartelijk dank dat u dagelijks Lee hebt om u te herinneren over het gebruik van `-ErrorAction Stop` deze methode.

#### <a name="cmdlet--erroraction-stop"></a>Cmdlet-error Action stoppen

Als u `-ErrorAction Stop` een geavanceerde functie of cmdlet opgeeft, worden alle- `Write-Error` instructies omgezet in afsluit fouten die de uitvoering stoppen of die kunnen worden verwerkt door een `catch` .

```powershell
Do-Something -ErrorAction Stop
```

### <a name="trycatch"></a>Try/catch

De manier waarop uitzonde ringen worden verwerkt in Power shell (en veel andere talen) is dat u eerst `try` een gedeelte van de code maakt en als er een fout optreedt, kunt u dat `catch` doen. Hier volgt een kort voor beeld.

```powershell
try
{
    Do-Something
}
catch
{
    Write-Output "Something threw an exception"
}

try
{
    Do-Something -ErrorAction Stop
}
catch
{
    Write-Output "Something threw an exception or used Write-Error"
}
```

Het `catch` script wordt alleen uitgevoerd als er een afsluit fout is opgetreden. Als de `try` uitvoering op de juiste wijze wordt uitgevoerd, wordt het overgeslagen `catch` .

### <a name="tryfinally"></a>Try/finally

Soms is het niet nodig om een fout af te handelen, maar moet u nog steeds code uitvoeren als er een uitzonde ring optreedt of niet. Een `finally` script heeft precies dat.

Bekijk dit voor beeld:

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
$command.Connection.Open()
$command.ExecuteNonQuery()
$command.Connection.Close()
```

Wanneer u een resource opent of er verbinding mee maakt, moet u deze sluiten. Als `ExecuteNonQuery()` er een uitzonde ring optreedt, wordt de verbinding niet gesloten. Dit is dezelfde code in een `try/finally` blok.

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
try
{
    $command.Connection.Open()
    $command.ExecuteNonQuery()
}
finally
{
    $command.Connection.Close()
}
```

In dit voor beeld wordt de verbinding gesloten als er een fout optreedt. Het wordt ook gesloten als er geen fout is opgetreden. Het `finally` script wordt elke keer uitgevoerd.

Omdat u de uitzonde ring niet ondervangt, wordt de aanroep stack nog steeds door gegeven.

### <a name="trycatchfinally"></a>Try/catch/finally

Het is volledig geldig om te gebruiken `catch` en samen te werken `finally` . In de meeste gevallen kunt u een of meer gebruiken, maar u kunt ook scenario's vinden waarin u beide gebruikt.

## <a name="psitem"></a>$PSItem

Nu we de basis principes van de weg hebben ontvangen, kunnen we een beetje dieper vinden.

Binnen het `catch` blok is er een automatische variabele ( `$PSItem` of `$_` ) van het type `ErrorRecord` met de details over de uitzonde ring. Hier volgt een kort overzicht van een aantal van de belangrijkste eigenschappen.

In deze voor beelden hebt u een ongeldig pad gebruikt in `ReadAllText` om deze uitzonde ring te genereren.

```powershell
[System.IO.File]::ReadAllText( '\\test\no\filefound.log')
```

### <a name="psitemtostring"></a>PSItem. ToString ()

Dit geeft u het schone bericht dat u kunt gebruiken in logboek registratie en algemene uitvoer. `ToString()`wordt automatisch aangeroepen als `$PSItem` binnen een teken reeks wordt geplaatst.

```powershell
catch
{
    Write-Output "Ran into an issue: $($PSItem.ToString())"
}

catch
{
    Write-Output "Ran into an issue: $PSItem"
}
```

### <a name="psiteminvocationinfo"></a>$PSItem. InvocationInfo

Deze eigenschap bevat aanvullende informatie die door Power shell wordt verzameld over de functie of het script waarin de uitzonde ring is opgetreden. Hier volgt een `InvocationInfo` van de voor beeld-uitzonde ringen die ik heb gemaakt.

```powershell
PS> $PSItem.InvocationInfo | Format-List *

MyCommand             : Get-Resource
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 5
OffsetInLine          : 5
ScriptName            : C:\blog\throwerror.ps1
Line                  :     Get-Resource
PositionMessage       : At C:\blog\throwerror.ps1:5 char:5
                        +     Get-Resource
                        +     ~~~~~~~~~~~~
PSScriptRoot          : C:\blog
PSCommandPath         : C:\blog\throwerror.ps1
InvocationName        : Get-Resource
```

In de belang rijke informatie ziet u de `ScriptName` , de `Line` code en de `ScriptLineNumber` locatie van de aanroep gestart.

### <a name="psitemscriptstacktrace"></a>$PSItem. ScriptStackTrace

Met deze eigenschap wordt de volg orde van functie aanroepen weer gegeven waarmee u naar de code wordt gemeldd waarin de uitzonde ring is gegenereerd.

```powershell
PS> $PSItem.ScriptStackTrace
at Get-Resource, C:\blog\throwerror.ps1: line 13
at Do-Something, C:\blog\throwerror.ps1: line 5
at <ScriptBlock>, C:\blog\throwerror.ps1: line 18
```

Ik maak alleen aanroepen voor functies in hetzelfde script, maar dit kan de aanroepen volgen als er meerdere scripts zijn betrokken.

### <a name="psitemexception"></a>$PSItem. Exception

Dit is de werkelijke uitzonde ring die is opgetreden.

#### <a name="psitemexceptionmessage"></a>$PSItem. Exception. Message

Dit is het algemene bericht met een beschrijving van de uitzonde ring en is een goed uitgangs punt bij het oplossen van problemen. De meeste uitzonde ringen hebben een standaard bericht, maar kunnen ook worden ingesteld op iets aangepast wanneer de uitzonde ring wordt gegenereerd.

```powershell
PS> $PSItem.Exception.Message

Exception calling "ReadAllText" with "1" argument(s): "The network path was not found."
```

Dit is ook het bericht dat wordt geretourneerd wanneer `$PSItem.ToString()` wordt gebeld als er niet één is ingesteld op de `ErrorRecord` .

#### <a name="psitemexceptioninnerexception"></a>$PSItem. Exception. InnerException

Uitzonde ringen kunnen binnenste uitzonde ringen bevatten. Dit is vaak het geval wanneer de code die u aanroept een uitzonde ring ophaalt en een andere uitzonde ring genereert. De oorspronkelijke uitzonde ring vindt plaats in de nieuwe uitzonde ring.

```powershell
PS> $PSItem.Exception.InnerExceptionMessage
The network path was not found.
```

Ik ga dit later opnieuw door te praten over het opnieuw genereren van uitzonde ringen.

#### <a name="psitemexceptionstacktrace"></a>$PSItem. Exception. StackTrace

Dit is de `StackTrace` voor de uitzonde ring. Ik heb hierboven een item weer gegeven `ScriptStackTrace` , maar dit is voor de aanroepen naar beheerde code.

```Output
at System.IO.FileStream.Init(String path, FileMode mode, FileAccess access, Int32 rights, Boolean
 useRights, FileShare share, Int32 bufferSize, FileOptions options, SECURITY_ATTRIBUTES secAttrs,
 String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean checkHost)
at System.IO.FileStream..ctor(String path, FileMode mode, FileAccess access, FileShare share, Int32
 bufferSize, FileOptions options, String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean
 checkHost)
at System.IO.StreamReader..ctor(String path, Encoding encoding, Boolean detectEncodingFromByteOrderMarks,
 Int32 bufferSize, Boolean checkHost)
at System.IO.File.InternalReadAllText(String path, Encoding encoding, Boolean checkHost)
at CallSite.Target(Closure , CallSite , Type , String )
```

U krijgt deze Stack tracering alleen wanneer de gebeurtenis wordt gegenereerd op basis van beheerde code. Ik bel een .NET Framework-functie rechtstreeks zodat deze allemaal in dit voor beeld kan worden weer geven. Over het algemeen wanneer u een stack tracering bekijkt, zoekt u naar waar de code wordt gestopt en begint de systeem aanroepen.

## <a name="working-with-exceptions"></a>Werken met uitzonde ringen

Er zijn meer uitzonde ringen dan de eigenschappen basis syntaxis en uitzonde ring.

### <a name="catching-typed-exceptions"></a>Opgegeven uitzonde ringen voor inspringen

U kunt selectief selecteren met de uitzonde ringen die u ondervangt. Uitzonde ringen hebben een type en u kunt het type uitzonde ring opgeven dat u wilt opvangen.

```powershell
try
{
    Do-Something -Path $path
}
catch [System.IO.FileNotFoundException]
{
    Write-Output "Could not find $path"
}
catch [System.IO.IOException]
{
        Write-Output "IO error with the file: $path"
}
```

Het uitzonderings type wordt voor elk `catch` blok gecontroleerd totdat er een wordt gevonden dat overeenkomt met uw uitzonde ring.
Het is belang rijk om te realiseren dat uitzonde ringen kunnen overnemen van andere uitzonde ringen. In het bovenstaande voor beeld `FileNotFoundException` neemt overgenomen van `IOException` . Als het `IOException` eerst was, wordt deze in plaats daarvan aangeroepen. Er wordt slechts één catch-blok aangeroepen, zelfs als er meerdere overeenkomsten zijn.

Als we er een hebben `System.IO.PathTooLongException` `IOException` gevonden, zouden ze wel overeenkomen, maar als we er een zouden hebben gehad, zouden we de stack zouden kunnen `InsufficientMemoryException` opvangen.

### <a name="catch-multiple-types-at-once"></a>Meerdere typen tegelijk catchiseren

Het is mogelijk meerdere uitzonderings typen met dezelfde instructie te ondervangen `catch` .

```powershell
try
{
    Do-Something -Path $path -ErrorAction Stop
}
catch [System.IO.DirectoryNotFoundException],[System.IO.FileNotFoundException]
{
    Write-Output "The path or file was not found: [$path]"
}
catch [System.IO.IOException]
{
    Write-Output "IO error with the file: [$path]"
}
```

Hartelijk dank dat u `/u/Sheppard_Ra` deze toevoeging hebt Voorst Ellen.

### <a name="throwing-typed-exceptions"></a>Getypte uitzonde ringen

U kunt getypte uitzonde ringen in Power shell genereren. In plaats van `throw` aan te roepen met een teken reeks:

```powershell
throw "Could not find: $path"
```

Een uitzonderings versnelling als volgt gebruiken:

```powershell
throw [System.IO.FileNotFoundException] "Could not find: $path"
```

Maar u moet een bericht opgeven wanneer u het op deze manier doet.

U kunt ook een nieuw exemplaar van een uitzonde ring maken dat moet worden gegenereerd. Het bericht is optioneel wanneer u dit doet, omdat het systeem standaard berichten bevat voor alle ingebouwde uitzonde ringen.

```powershell
throw [System.IO.FileNotFoundException]::new()
throw [System.IO.FileNotFoundException]::new("Could not find path: $path")
```

Als u geen gebruik wilt maken van Power shell 5,0 of hoger, moet u de oudere `New-Object` benadering gebruiken.

```powershell
throw (New-Object -TypeName System.IO.FileNotFoundException )
throw (New-Object -TypeName System.IO.FileNotFoundException -ArgumentList "Could not find path: $path")
```

Door een getypte uitzonde ring te gebruiken, kunnen u (of anderen) de uitzonde ring ondervangen door het type zoals vermeld in de vorige sectie.

#### <a name="write-error--exception"></a>Schrijf fout-uitzonde ring

We kunnen deze getypte uitzonde ringen toevoegen aan `Write-Error` en we kunnen nog steeds `catch` fouten opleveren op uitzonderings type. Gebruiken `Write-Error` als in de volgende voor beelden:

```powershell
# with normal message
Write-Error -Message "Could not find path: $path" -Exception ([System.IO.FileNotFoundException]::new()) -ErrorAction Stop

# With message inside new exception
Write-Error -Exception ([System.IO.FileNotFoundException]::new("Could not find path: $path")) -ErrorAction Stop

# Pre PS 5.0
Write-Error -Exception ([System.IO.FileNotFoundException]"Could not find path: $path") -ErrorAction Stop

Write-Error -Message "Could not find path: $path" -Exception ( New-Object -TypeName System.IO.FileNotFoundException ) -ErrorAction Stop
```

Vervolgens kunnen we deze als volgt ondervangen:

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Log $PSItem.ToString()
}
```

#### <a name="the-big-list-of-net-exceptions"></a>De grote lijst met .NET-uitzonde ringen

Ik heb een hoofd lijst gecompileerd met de hulp van de [Reddit/r/Power shell-Community][] die honderden .net-uitzonde ringen bevat om dit bericht aan te vullen.

- [De grote lijst met .NET-uitzonde ringen][]

Zoek vervolgens naar de lijst met uitzonde ringen die vergelijkbaar zijn met die van mijn situatie. Probeer uitzonde ringen in de basis `System` naam ruimte te gebruiken.

### <a name="exceptions-are-objects"></a>Uitzonde ringen zijn objecten

Als u veel typen uitzonde ringen gaat gebruiken, moet u er rekening mee houden dat ze objecten zijn. Verschillende uitzonde ringen hebben verschillende constructors en eigenschappen. Als we de [FileNotFoundException][] -documentatie voor zien `System.IO.FileNotFoundException` , zien we dat we een bericht en een bestandspad kunnen door geven.

```powershell
[System.IO.FileNotFoundException]::new("Could not find file", $path)
```

En het heeft een `FileName` eigenschap waarmee het bestandspad wordt weer gegeven.

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Output $PSItem.Exception.FileName
}
```

Raadpleeg de .net- [documentatie][] voor andere constructors en object eigenschappen.

### <a name="re-throwing-an-exception"></a>Een uitzonde ring opnieuw genereren

Als alles wat u in uw blok wilt doen `catch` `throw` , dezelfde uitzonde ring is, is `catch` dat niet het geval. U moet alleen `catch` een uitzonde ring hebben die u van plan bent te verwerken of een actie uit te voeren wanneer dit gebeurt.

Er zijn momenten waarop u een actie wilt uitvoeren op een uitzonde ring, maar de uitzonde ring opnieuw wilt genereren, zodat er iets kan worden gedaan met de uitvoering. We kunnen een bericht schrijven of het probleem in het logboek registreren op het punt waar we het vinden, maar verwerken het probleem verder op de stack.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw $PSItem
}
```

Interessant genoeg, we kunnen aanroepen `throw` vanuit de `catch` en de huidige uitzonde ring opnieuw genereren.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw
}
```

We willen de uitzonde ring opnieuw genereren om de oorspronkelijke uitvoerings informatie, zoals het bron script en het regel nummer, te bewaren. Als we op dit moment een nieuwe uitzonde ring genereren, wordt de uitzonde ring gestart.

#### <a name="re-throwing-a-new-exception"></a>Nieuwe uitzonde ring opnieuw activeren

Als u een uitzonde ring ondervangt, maar u een ander wilt doen, moet u de oorspronkelijke uitzonde ring in het nieuwe item nesten. Hierdoor kan iemand de stack benaderen als `$PSItem.Exception.InnerException` .

```powershell
catch
{
    throw [System.MissingFieldException]::new('Could not access field',$PSItem.Exception)
}
```

#### <a name="pscmdletthrowterminatingerror"></a>$PSCmdlet. ThrowTerminatingError ()

Het enige wat ik niet bevalt met het gebruik `throw` van onbewerkte uitzonde ringen is dat het fout bericht verwijst naar de `throw` instructie en geeft aan dat de regel het probleem is.

```Output
Unable to find the specified file.
At line:31 char:9
+         throw [System.IO.FileNotFoundException]::new()
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], FileNotFoundException
    + FullyQualifiedErrorId : Unable to find the specified file.
```


Wanneer het fout bericht wordt weer gegeven dat mijn script is beschadigd omdat ik `throw` op regel 31 werd aangeroepen, is er een onjuist bericht voor gebruikers van uw script. Er zijn geen nuttige informatie.

Met Dexter Dhami is aangegeven dat ik dit kan `ThrowTerminatingError()` oplossen.

```powershell
$PSCmdlet.ThrowTerminatingError(
    [System.Management.Automation.ErrorRecord]::new(
        ([System.IO.FileNotFoundException]"Could not find $Path"),
        'My.ID',
        [System.Management.Automation.ErrorCategory]::OpenError,
        $MyObject
    )
)
```

Als we ervan uitgaan dat `ThrowTerminatingError()` in een functie met de naam wordt aangeroepen `Get-Resource` , is dit de fout die wordt weer geven.

```Output
Get-Resource : Could not find C:\Program Files (x86)\Reference
Assemblies\Microsoft\Framework\.NETPortable\v4.6\System.IO.xml
At line:6 char:5
+     Get-Resource -Path $Path
+     ~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (:) [Get-Resource], FileNotFoundException
    + FullyQualifiedErrorId : My.ID,Get-Resource
```

Ziet u hoe de `Get-Resource` functie als de bron van het probleem wijst? Dit geeft aan dat de gebruiker iets handig is.

Omdat `$PSItem` dit een is `ErrorRecord` , kunnen we `ThrowTerminatingError` deze manier ook gebruiken om opnieuw te genereren.

```powershell
catch
{
    $PSCmdlet.ThrowTerminatingError($PSItem)
}
```

Hiermee wijzigt u de bron van de fout in de cmdlet en verbergt u de interne functies van de functie van de gebruikers van uw cmdlet.

## <a name="try-can-create-terminating-errors"></a>Probeer afsluit fouten te maken

Kirk Munro wijst op dat sommige uitzonde ringen alleen afsluit fouten bevatten wanneer ze in een blok worden uitgevoerd `try/catch` . Hier ziet u dat er een deling door een runtime-uitzonde ring door nul wordt gegenereerd.

```powershell
function Do-Something { 1/(1-1) }
```

Vervolgens roept u dit als volgt aan om te zien hoe de fout wordt gegenereerd en wordt het bericht nog steeds uitgevoerd.

```powershell
&{ Do-Something; Write-Output "We did it. Send Email" }
```

Maar door dezelfde code te plaatsen in een `try/catch` , zien we iets anders.

```powershell
try
{
    &{ Do-Something; Write-Output "We did it. Send Email" }
}
catch
{
    Write-Output "Notify Admin to fix error and send email"
}
```


Er wordt een fout melding weer gegeven dat er een afsluit fout optreedt en het eerste bericht niet wordt uitgevoerd. Wat ik niet bevalt, is dat u deze code kunt gebruiken in een functie en anders reageert als iemand een `try/catch` .

Ik heb geen problemen met deze mezelf ondertreden, maar het is een belang rijk deel van het geval te weten.

### <a name="pscmdletthrowterminatingerror-inside-trycatch"></a>$PSCmdlet. ThrowTerminatingError () binnen try/catch

Eén nuance van `$PSCmdlet.ThrowTerminatingError()` is dat er een afsluit fout binnen uw cmdlet wordt gemaakt, maar er wordt een niet-afsluit fout weer gegenereerd nadat de cmdlet is achtergelaten. Dit laat de belasting van de oproepende functie van de functies zien om te bepalen hoe de fout moet worden afgehandeld. Ze kunnen deze weer omzetten in een afsluit fout door deze te gebruiken `-ErrorAction Stop` of aan te roepen vanuit een `try{...}catch{...}` .

### <a name="public-function-templates"></a>Sjablonen voor open bare functies

Een van de laatste een manier waarop ik met Kirk Munro werd gecommuniceerd, was dat hij een `try{...}catch{...}` rond elke en `begin` `process` `end` blok keren in al zijn geavanceerde functies. In deze generieke vangst blokken wordt hij als één regel gebruikt `$PSCmdlet.ThrowTerminatingError($PSitem)` om alle uitzonde ringen te behandelen die zijn functies verlaten.

```powershell
function Do-Something
{
    [cmdletbinding()]
    param()

    process
    {
        try
        {
            ...
        }
        catch
        {
            $PSCmdlet.ThrowTerminatingError($PSitem)
        }
    }
}
```

Omdat alles zich in een `try` instructie binnen zijn functions bevindt, gebeurt alles consistent. Dit geeft ook schone fouten aan de eind gebruiker die de interne code van de gegenereerde fout verbergt.

## <a name="trap"></a>Overlapping

Ik heb gestreefd over het `try/catch` aspect van uitzonde ringen. Maar er is één verouderde functie die ik moet vermelden voordat we dit in de omloop zetten.

A `trap` wordt in een script of functie geplaatst om alle uitzonde ringen die in dat bereik plaatsvinden, te ondervangen. Wanneer er een uitzonde ring optreedt, wordt de code in de `trap` uitgevoerd en vervolgens wordt de code normaal voortgezet. Als er meerdere uitzonde ringen optreden, wordt de trap boven en boven genoemd.

```powershell
trap
{
    Write-Log $PSItem.ToString()
}

throw [System.Exception]::new('first')
throw [System.Exception]::new('second')
throw [System.Exception]::new('third')
```

Ik heb deze aanpak nooit goedgekeurd, maar ik zie de waarde in de beheerders-of controller scripts waarmee alle uitzonde ringen worden vastgelegd, en ga daarna nog verder met uitvoeren.

## <a name="closing-remarks"></a>Opmerkingen sluiten

Het toevoegen van de juiste uitzonderings afhandeling aan uw scripts is dat ze niet alleen stabieler maken, maar het is ook eenvoudiger om deze uitzonde ringen op te lossen.

Ik heb veel tijd besteed aan `throw` het praten omdat het een kern concept is voor het afhandelen van uitzonde ringen. Power Shell heeft ons ook `Write-Error` de omstandigheden afhandelen die u zou gebruiken `throw` . Het is dus niet belang rijk dat u deze moet gebruiken `throw` nadat u dit hebt gelezen.

Nu u de tijd hebt genomen voor het schrijven van uitzonde ringen in deze details, gaat ik overschakelen naar het gebruik van `Write-Error -Stop` om fouten in mijn code te genereren. Ook gaat u Kirk-advies nemen en de `ThrowTerminatingError` uitzonderings-handler van mijn goto maken voor elke functie.

<!-- link references -->
[powershellexplained.com]: https://powershellexplained.com/
[oorspronkelijke versie]: https://powershellexplained.com/2017-04-10-Powershell-exceptions-everything-you-ever-wanted-to-know/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Reddit/r/Power shell-Community]: https://www.reddit.com/r/PowerShell/comments/64866o/kevmar_all_net_46_exceptions_list_for_use_with/
[De grote lijst met .NET-uitzonde ringen]: https://powershellexplained.com/2017-04-07-all-dotnet-exception-list
[FileNotFoundException]: https://docs.microsoft.com/dotnet/api/System.IO.FileNotFoundException
[.NET-documentatie]: https://docs.microsoft.com/dotnet/api