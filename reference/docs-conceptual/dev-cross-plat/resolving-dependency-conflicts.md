---
title: Conflicten met de assembly-afhankelijkheden van Power shell-modules oplossen
description: Bij het schrijven van een binaire Power shell-module in C# is het natuurlijk om afhankelijkheden te maken met andere pakketten of bibliotheken om functionaliteit te bieden.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 536bcfd1ced536faccde0d6c5bc483cdaf31ce68
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87775166"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a>Conflicten met de assembly-afhankelijkheden van Power shell-modules oplossen

Bij het schrijven van een binaire Power shell-module in C# is het natuurlijk om afhankelijkheden te maken met andere pakketten of bibliotheken om functionaliteit te bieden. Het nemen van afhankelijkheden op andere bibliotheken is wenselijk voor het hergebruik van code. Power shell laadt altijd assembly's in dezelfde context. Dit geeft problemen wanneer de afhankelijkheden van een module conflicteren met reeds geladen Dll's en kunnen verhinderen dat er twee anderszins niet-gerelateerde modules worden gebruikt in dezelfde Power shell-sessie.

Als u dit probleem hebt gehad, ziet u een fout bericht als volgt:

![Fout bericht bij conflict bij het laden van assembly](./media/resolving-dependency-conflicts/moduleconflict.png)

In dit artikel vindt u een aantal manieren waarop afhankelijkheids conflicten optreden in Power shell en manieren om problemen met afhankelijkheids conflicten te verhelpen. Zelfs als u geen module auteur bent, zijn er hier enkele trucs die u kunnen helpen bij het oplossen van afhankelijkheids conflicten in modules die u gebruikt.

## <a name="why-do-dependency-conflicts-occur"></a>Waarom vinden afhankelijkheids conflicten plaats?

In .NET treden afhankelijkheids conflicten op wanneer twee versies van dezelfde assembly worden geladen in dezelfde _Assembly-laad context_. Deze term betekent iets anders op verschillende .NET-platformen, die [later](#powershell-and-net)worden besproken. Dit conflict is een veelvoorkomend probleem dat zich voordoet in software waarvoor versie afhankelijke afhankelijkheden worden gebruikt. Omdat er geen eenvoudige oplossingen zijn, en omdat veel afhankelijkheids modellen het probleem op verschillende manieren proberen op te lossen, wordt deze situatie vaak ' afhankelijkheids Hell ' genoemd.

Conflict problemen worden samengesteld op basis van het feit dat een project bijna nooit opzettelijk of rechtstreeks afhankelijk is van twee versies van dezelfde afhankelijkheid. In plaats daarvan heeft het project twee of meer afhankelijkheden waarvoor elk een andere versie van dezelfde afhankelijkheid nodig is.

Stel bijvoorbeeld dat uw .NET-toepassing, `DuckBuilder` met twee afhankelijkheden, een deel van de functionaliteit kan uitvoeren en er als volgt uitziet:

![Twee afhankelijkheden van DuckBuilder zijn afhankelijk van verschillende versies van Newtonsoft.Jsop](./media/resolving-dependency-conflicts/dep-conflict.jpg)

Omdat `Contoso.ZipTools` en `Fabrikam.FileHelpers` beide afhankelijk zijn van verschillende versies van `Newtonsoft.Json` , is er mogelijk een afhankelijkheids conflict afhankelijk van hoe elke afhankelijkheid wordt geladen.

### <a name="conflicting-with-powershells-dependencies"></a>Conflicterende met de afhankelijkheden van Power shell

In Power shell wordt het conflict met afhankelijkheids conflicten verg root omdat Power shell-modules en eigen afhankelijkheden van Power shell in dezelfde gedeelde context worden geladen. Dit betekent dat de Power shell-engine en alle geladen Power shell-modules geen conflicterende afhankelijkheden hebben. Een klassiek voor beeld hiervan is `Newtonsoft.Json` :

![De FictionalTools-module is afhankelijk van de nieuwere versie van Newtonsoft.Jsvan Power shell](./media/resolving-dependency-conflicts/engine-conflict.jpg)

In dit voor beeld is de module `FictionalTools` afhankelijk van `Newtonsoft.Json` versie `12.0.3` , een nieuwere versie van `Newtonsoft.Json` `11.0.2` die in het voor beeld Power shell wordt geleverd.

> [!NOTE]
> Dit is een voor beeld en Power shell 7 wordt momenteel geleverd met `Newtonsoft.Json 12.0.3` .

Omdat de module afhankelijk is van een nieuwere versie van de assembly, wordt de versie die Power shell al heeft geladen, niet geaccepteerd. Maar omdat Power shell al een versie van de assembly heeft geladen, kan de module geen eigen versie laden met behulp van het conventionele laad mechanisme.

### <a name="conflicting-with-another-modules-dependencies"></a>Conflicterende met de afhankelijkheden van een andere module

Een ander algemeen scenario in Power shell is dat een module wordt geladen die afhankelijk is van één versie van een assembly. vervolgens wordt een andere module geladen die afhankelijk is van een andere versie van de assembly.

Dit ziet er ongeveer als volgt uit:

![Twee Power shell-modules vereisen verschillende versies van de micro soft. Extensions. logboek registratie afhankelijkheid](./media/resolving-dependency-conflicts/mod-conflict.jpg)

In dit geval vereist de `FictionalTools` module een nieuwere versie van `Microsoft.Extensions.Logging` de `FilesystemManager` module.

Stel dat deze modules hun afhankelijkheden laden door de afhankelijkheids-assembly's in dezelfde map als de assembly van de hoofd module te plaatsen. Hierdoor kan .NET deze impliciet op naam laden. Als Power shell 7 wordt uitgevoerd (boven op .NET Core 3,1), kunnen we laden en uitvoeren `FictionalTools` , vervolgens laden en uitvoeren `FilesystemManager` zonder problemen. Als we in een nieuwe sessie echter laden en uitvoeren en `FilesystemManager` vervolgens laden, `FictionalTools` krijgen we een `FileLoadException` van de `FictionalTools` opdracht omdat er een nieuwere versie van is vereist `Microsoft.Extensions.Logging` dan de geladen.
`FictionalTools` de benodigde versie kan niet worden geladen omdat er al een assembly met dezelfde naam is geladen.

## <a name="powershell-and-net"></a>Power shell en .NET

Power shell wordt uitgevoerd op het .NET-platform. NET is uiteindelijk verantwoordelijk voor het oplossen en laden van assembly-afhankelijkheden. Daarom moeten we weten hoe .NET hier wordt beschreven om afhankelijkheids conflicten te begrijpen.

We moeten ook het feit confront dat verschillende versies van Power shell worden uitgevoerd op verschillende .NET-implementaties. In het algemeen worden Power shell 5,1 en lager uitgevoerd op .NET Framework, terwijl Power shell 6 en hoger op .NET core worden uitgevoerd. Deze twee implementaties van .NET laden en verwerken assembly's verschillend.
Dit betekent dat het oplossen van afhankelijkheids conflicten kan variëren, afhankelijk van het onderliggende .NET-platform.

### <a name="assembly-load-contexts"></a>Contexten assembly laden

In .NET is dit een _Assembly-laad context_ (ALC) die een runtime-naam ruimte is waarin de assembly's worden geladen. De namen van de assembly's moeten uniek zijn. In dit concept kunnen assembly's uniek worden omgezet op naam in elke ALC.

### <a name="assembly-reference-loading-in-net"></a>Assembly-referentie laden in .NET

De semantiek van het laden van de assembly is afhankelijk van de .NET-implementatie (.NET Core versus .NET Framework) en de .NET API die wordt gebruikt om een bepaalde assembly te laden. In plaats van hier meer informatie te geven, zijn er koppelingen in de [verdere Lees](#further-reading) sectie die in het bijzonder worden uitgebreid over hoe .NET-assembly laden in elke .net-implementatie werkt.

In dit artikel wordt verwezen naar de volgende mechanismen:

- Impliciet assembly wordt geladen (effectief `Assembly.Load(AssemblyName)` ), wanneer .net impliciet probeert een assembly te laden op naam uit een statische assembly-verwijzing in .net-code.
- `Assembly.LoadFrom()`, een door de invoeg toepassing georiënteerde laad-API die handlers toevoegt voor het oplossen van afhankelijkheden van het geladen DLL-bestand. Deze methode kan mogelijk de afhankelijkheden niet op de gewenste manier oplossen.
- `Assembly.LoadFile()`, een Basic-laad-API die bedoeld is voor het laden van alleen de assembly die wordt gevraagd en geen afhankelijkheden afhandelt.

### <a name="differences-in-net-framework-vs-net-core"></a>Verschillen in .NET Framework vs .NET core

De manier waarop deze Api's werken, is gewijzigd op subtiele manieren tussen .NET core en .NET Framework, zodat het voor deel is dat u de opgenomen [koppelingen](#further-reading)kunt lezen. Het is belang rijk dat contexten voor assembly-belasting en andere mechanismen voor de oplossing van de assembly zijn gewijzigd tussen .NET Framework en .NET core.

Met name .NET Framework heeft de volgende functies:

- De globale assembly-cache, voor de oplossing van de assembly voor alle computers
- Toepassings domeinen, die in sandboxes in het proces worden gebruikt voor de isolatie van de assembly, maar die ook een serializion-laag aan concurreren geven met
- Een beperkt context model voor het laden van de assembly, waarin [hier](/dotnet/framework/deployment/best-practices-for-assembly-loading)dieper wordt uitgelegd, met een vaste verzameling van assembly-laad contexten, elk met hun eigen gedrag:
  - De standaard laad context, waar assembly's standaard worden geladen
  - De context van laden voor het hand matig laden van assembly's tijdens runtime
  - De alleen-reflectie context, voor het veilig laden van assembly's om de meta gegevens te lezen zonder ze uit te voeren
  - De verwarrende void dat assembly's zijn geladen met `Assembly.LoadFile(string path)` en `Assembly.Load(byte[] asmBytes)` Live in

.NET core (en .NET 5 +) heeft deze complexiteit vervangen door een eenvoudiger model:

- Geen globale assembly-cache. Toepassingen nemen al hun eigen afhankelijkheden. Hiermee verwijdert u een externe factor voor de oplossing van afhankelijkheden in toepassingen, waardoor het maken van afhankelijkheids oplossingen betrouwbaarder wordt.
  Met Power shell, als de host voor de invoeg toepassing, wordt dit enigszins door ingewik kelder voor modules. De afhankelijkheden in `$PSHOME` worden gedeeld met alle modules.
- Slechts één toepassings domein en geen mogelijkheid om nieuwe items te maken. Het toepassings domein concept wordt in .NET core onderhouden, louter als de algemene status van het .NET-proces.
- Een nieuw, uitbreidbaar verzamelings context model voor het laden van de assembly. De oplossing van de assembly kan worden voorzien van een naam ruimte door deze in een nieuwe ALC te zetten. .NET core-processen beginnen met één standaard ALC waarin alle assembly's worden geladen. (met uitzonde ring van de geladen met `Assembly.LoadFile(string)` en `Assembly.Load(byte[])` ), maar het proces kan een eigen aangepaste ALCs maken en definiëren met een eigen geladen logica. Wanneer een assembly wordt geladen, wordt de eerste ALC die wordt geladen in, verantwoordelijk voor het oplossen van de bijbehorende afhankelijkheden. Hiermee maakt u mogelijkheden voor het implementeren van krachtige .NET-invoeg toepassingen voor laden.

In beide implementaties worden assembly's geladen vertraagd. Dit betekent dat ze worden geladen wanneer een methode voor de eerste keer wordt uitgevoerd.

Dit zijn bijvoorbeeld twee versies van dezelfde code die een afhankelijkheid op verschillende tijdstippen laden.

Bij de eerste keer wordt de afhankelijkheid altijd geladen als `Program.GetRange()` deze wordt aangeroepen, omdat de afhankelijkheids verwijzing in de methode lexicalen is.

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

De tweede laadt de afhankelijkheid alleen als de `limit` para meter 20 of meer is, vanwege de interne Inleiding via een methode:

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

Dit is een goede gewoonte omdat het geheugen en bestandssysteem-I/O minimaliseert en de bronnen efficiënter worden gebruikt. De vervelend een neven effect hiervan is dat we niet weten dat de assembly niet kan worden geladen totdat we het codepad hebben bereikt dat probeert de assembly te laden.

Er kan ook een timing voorwaarde worden gemaakt voor conflicten bij het laden van de assembly. Als twee delen van hetzelfde programma proberen verschillende versies van dezelfde assembly te laden, is de versie die wordt geladen, afhankelijk van welk codepad het eerst wordt uitgevoerd.

Voor Power shell betekent dit dat de volgende factoren van invloed kunnen zijn op een assembly-belasting conflict:

- Welke module is het eerst geladen?
- Is het codepad dat gebruikmaakt van de afhankelijkheids bibliotheek run?
- Laadt Power shell een conflicterende afhankelijkheid bij het opstarten of alleen onder bepaalde code paden?

## <a name="quick-fixes-and-their-limitations"></a>Snelle oplossingen en hun beperkingen

In sommige gevallen is het mogelijk om kleine aanpassingen aan te brengen in uw module en om dingen te corrigeren met minimale inspanning. Maar deze oplossingen worden meestal geleverd met aanvullende opmerkingen. Hoewel ze kunnen worden toegepast op uw module, werken ze niet voor elke module.

### <a name="change-your-dependency-version"></a>De afhankelijkheids versie wijzigen

De eenvoudigste manier om afhankelijkheids conflicten te voor komen, is door akkoord te gaan met een afhankelijkheid. Dit kan de volgende oorzaken hebben:

- Uw conflict is met een directe afhankelijkheid van uw module en u beheert de versie.
- Uw conflict is met een indirecte afhankelijkheid, maar u kunt uw directe afhankelijkheden configureren voor het gebruik van een bemaalde, indirecte afhankelijkheids versie.
- U weet de conflicterende versie en kan erop vertrouwen dat deze niet verandert.

Het `Newtonsoft.Json` pakket is een goed voor beeld van dit laatste scenario. Dit is een afhankelijkheid van Power shell 6 en hoger, en wordt niet gebruikt in Windows Power shell. Een eenvoudige manier om versie conflicten op te lossen is het richten op de laagste versie van `Newtonsoft.Json` alle Power shell-versies die u wilt richten.

Bijvoorbeeld, Power shell 6.2.6 en Power shell 7.0.2 gebruiken momenteel `Newtonsoft.Json` versie 12.0.3. Als u een module wilt maken die is gericht op Windows Power shell, Power shell 6 en Power shell 7, zou u dus `Newtonsoft.Json 12.0.3` als een afhankelijkheid als doel hebben en deze in uw ingebouwde module toevoegen. Wanneer de module in Power shell 6 of 7 is geladen, is de eigen assembly van Power shell `Newtonsoft.Json` al geladen. Het is ook ten minste de versie die is vereist voor uw module, waardoor de oplossing slaagt. In Windows Power shell is de assembly niet al aanwezig in Power shell. In plaats daarvan wordt het geladen vanuit de map module.

Bij het richten op een concreet Power shell-pakket, zoals `Microsoft.PowerShell.Sdk` of `System.Management.Automation` , moet NuGet de juiste vereiste afhankelijkheids versies kunnen omzetten. Het doel van Windows Power shell en Power shell 6 + is moeilijker geworden omdat u moet kiezen tussen meerdere frameworks of het doel `PowerShellStandard.Library` .

Omstandigheden waarbij het vastmaken aan een algemene afhankelijkheids versie niet werkt:

- Het conflict is met een indirecte afhankelijkheid en geen van uw afhankelijkheden kunnen worden geconfigureerd voor het gebruik van een gemeen schappelijke versie.
- De andere versie van de afhankelijkheid is waarschijnlijk vaak gewijzigd, dus het afstellen van een algemene versie is alleen een oplossing op korte termijn.

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a>Een gebeurtenis-handler voor AssemblyResolve toevoegen om een omleiding van dynamische bindingen te maken

Soms is het wijzigen van uw eigen afhankelijkheids versie niet mogelijk of is het te moeilijk. Een andere optie is om een dynamische bindings omleiding in te stellen door een gebeurtenis-handler voor de gebeurtenis te registreren `AssemblyResolve` .

Net als bij een statische bindings omleiding is het punt om alle consumenten van een afhankelijkheid af te dwingen om dezelfde werkelijke assembly te gebruiken. U kunt aanroepen voor het laden van de afhankelijkheid onderscheppen en deze altijd omleiden naar de gewenste versie.

Dit ziet er ongeveer als volgt uit:

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

U kunt een script Block in Power shell technisch registreren voor het afhandelen van een `AssemblyResolve` gebeurtenis, maar:

- Een `AssemblyResolve` gebeurtenis kan worden geactiveerd voor elke thread, iets wat niet kan worden verwerkt met Power shell.
- Zelfs wanneer gebeurtenissen worden verwerkt op de juiste thread, betekenen de scope-concepten van Power shell dat de gebeurtenis-handler script Block zorgvuldig moet worden geschreven zodat deze niet afhankelijk zijn van variabelen die buiten het bereik zijn gedefinieerd.

Er zijn situaties waarin het omleiden naar een algemene versie niet werkt:

- Wanneer de afhankelijkheid wijzigingen heeft aangebracht tussen versies of wanneer afhankelijke code afhankelijk is van een functionaliteit die niet beschikbaar is in de versie waarnaar u omleidt.
- Als uw module niet is geladen vóór de conflicterende afhankelijkheid. Als u een gebeurtenis-handler registreert `AssemblyResolve` nadat de afhankelijkheid is geladen, wordt deze nooit gestart. Als u afhankelijkheids conflicten met een andere module wilt voor komen, is dit mogelijk een probleem omdat de andere module eerst kan worden geladen.

### <a name="use-the-dependency-out-of-process"></a>De afhankelijkheid uit het proces gebruiken

Deze oplossing is meer voor module gebruikers dan van module auteurs. Dit is een oplossing voor het gebruik van een module die niet werkt vanwege een bestaand afhankelijkheids conflict.

Afhankelijkheids conflicten treden op omdat twee versies van dezelfde assembly in hetzelfde .NET-proces worden geladen. Een eenvoudige oplossing is het laden van deze in verschillende processen, zolang u de functionaliteit van beide kunt gebruiken.

In Power shell zijn er verschillende manieren om dit te doen:

- Power shell als een subproces aanroepen

  Een eenvoudige manier om een Power shell-opdracht uit te voeren vanuit het huidige proces is door alleen een nieuw Power Shell-proces rechtstreeks te starten met de opdracht aanroep:

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  De belangrijkste beperking is dat de herstructurering het resultaat kan trickier of meer fout gevoelig is dan andere opties.

- Het Power shell-taak systeem

  Het Power shell-taak systeem voert ook opdrachten uit het proces uit, door opdrachten te verzenden naar een nieuw Power Shell-proces en de resultaten te retour neren:

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  In dit geval moet u er alleen voor zorgen dat alle variabelen en status correct worden door gegeven.

  Het taak systeem kan ook iets omslachtig zijn wanneer u kleine opdrachten uitvoert.

- Externe communicatie van powershell

  Wanneer het beschikbaar is, kan externe communicatie van Power shell op een handige manier worden uitgevoerd om opdrachten uit te voeren. Met externe toegang kunt u een nieuwe **PSSession** maken in een nieuw proces, de opdrachten aanroepen via Power shell remoting en vervolgens de resultaten lokaal gebruiken met de andere modules met de conflicterende afhankelijkheden.

  Een voor beeld kan er als volgt uitzien:

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- Impliciete externe toegang tot Windows Power shell

  Een andere optie in Power shell 7 is het gebruik `-UseWindowsPowerShell` van de vlag on `Import-Module` . Hiermee wordt de module via een lokale externe sessie in Windows Power shell geïmporteerd:

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  Houd er rekening mee dat modules mogelijk niet werken met of anders werken met Windows Power shell.

#### <a name="when-out-of-process-invocation-should-not-be-used"></a>Als out-of-process-aanroep niet kan worden gebruikt

Als module-auteur is het intrekken van de out-of-process-opdracht moeilijk te maken in een module en kunnen er ook rand cases zijn die problemen veroorzaken. Met name externe communicatie en taken zijn mogelijk niet beschikbaar in alle omgevingen waar de module moet worden gebruikt. Het algemene principe van het verplaatsen van de implementatie uit het proces en het toestaan van de Power shell-module als een smallere client, kan echter nog steeds van toepassing zijn.

Als module gebruiker zijn er gevallen waarin out-of-process-aanroep niet werkt:

- Wanneer externe communicatie van Power shell niet beschikbaar is, omdat u niet over de juiste bevoegdheden beschikt om deze te gebruiken of niet is ingeschakeld.
- Wanneer een bepaald .NET-type nodig is voor uitvoer als invoer naar een methode of een andere opdracht.
  Opdrachten die gebruikmaken van externe communicatie van Power shell, verzenden gedeserialiseerd objecten in plaats van sterk getypte .NET-objecten. Dit betekent dat methode aanroepen en sterk getypeerde Api's niet werken met de uitvoer van opdrachten die worden geïmporteerd over externe communicatie.

## <a name="more-robust-solutions"></a>Meer robuuste oplossingen

De vorige oplossingen bevatten allemaal scenario's en modules die niet werken. Ze hebben echter ook relatief eenvoudig te implementeren. De volgende oplossingen zijn robuuster, maar vereisen meer moeite om correct te implementeren en kunnen subtiele bugs introduceren als ze niet zorgvuldig worden geschreven.

### <a name="loading-through-net-core-assembly-load-contexts"></a>Contexten laden met behulp van .NET core assembly-belasting

[Assembly-contexten](/dotnet/api/system.runtime.loader.assemblyloadcontext) (ALCs) als een Implementeer bare API zijn geïntroduceerd in .net Core 1,0 om de nood zaak om meerdere versies van dezelfde assembly in dezelfde runtime te laden, te verhelpen.

Binnen .NET core en .NET 5 bieden ze de meest robuuste oplossing voor het probleem van het laden van conflicterende versies van een assembly. Aangepaste ALCs zijn echter niet beschikbaar in .NET Framework. Dit betekent dat deze oplossing alleen werkt in Power shell 6 en hoger.

Momenteel is het beste voor beeld van het gebruik van een ALC voor het isoleren van afhankelijkheden in Power shell in Power shell editor-Services, de taal server voor de Power shell-extensie voor Visual Studio code. Een [ALC wordt gebruikt](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs) om te voor komen dat de eigen afhankelijkheden van Power shell editor-Services conflicteren met die in Power shell-modules.

Het implementeren van module afhankelijkheids isolatie met een ALC is conceptueel moeilijk, maar we werken met een mini maal voor beeld. Stel dat er een eenvoudige module is die alleen is bedoeld voor gebruik in Power shell 7.
De bron code is als volgt ingedeeld:

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

De cmdlet-implementatie ziet er als volgt uit:

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

Het manifest (sterk vereenvoudigd), ziet er als volgt uit:

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

En het `csproj` ziet er als volgt uit:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

Bij het maken van deze module heeft de gegenereerde uitvoer de volgende indeling:

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

In dit voor beeld bevindt het probleem zich in de `Shared.Dependency.dll` Assembly. Dit is onze imaginaire conflicterende afhankelijkheid. Dit is de afhankelijkheid die we achter een ALC moeten plaatsen, zodat we de module-specifieke versie kunnen gebruiken.

We moeten de module opnieuw inbouwen zodat:

- Module-afhankelijkheden worden alleen in onze aangepaste ALC geladen en niet in de ALC van Power shell, zodat er geen conflict kan optreden. Omdat we meer afhankelijkheden aan ons project toevoegen, willen we niet continu meer code toevoegen om te blijven werken. In plaats daarvan willen we de algemene logica van afhankelijkheids oplossingen opnieuw gebruiken.
- Het laden van de module werkt nog steeds normaal in Power shell. Cmdlets en andere typen die nodig zijn voor de Power shell-module systeem, worden gedefinieerd in de eigen ALC van Power shell.

Om deze twee vereisten te kunnen bepalen, moeten we onze module opsplitsen in twee assembly's:

- Een cmdlets-assembly, `AlcModule.Cmdlets.dll` , die definities bevat van alle typen die het module systeem van Power shell nodig heeft om onze module correct te laden. Dat wil zeggen dat alle implementaties van de `Cmdlet` basis klasse en de klasse die deze implementeert `IModuleAssemblyInitializer` , de gebeurtenis-handler instellen `AssemblyLoadContext.Default.Resolving` om op de juiste wijze te worden geladen `AlcModule.Engine.dll` via onze aangepaste alc. Omdat Power shell 7 de typen die zijn gedefinieerd in assembly's die in andere ALCs zijn geladen, verbergt, moeten de typen die openbaar beschikbaar zijn voor Power shell ook hier worden gedefinieerd. Ten slotte moet onze aangepaste ALC-definitie worden gedefinieerd in deze assembly. Zo weinig mogelijk zou er in deze assembly kunnen worden opgenomen.
- Een engine-assembly, `AlcModule.Engine.dll` waarmee de daad werkelijke implementatie van de module wordt verwerkt.
  Typen van deze zijn beschikbaar in Power shell ALC, maar deze worden in eerste instantie geladen via onze aangepaste ALC. De afhankelijkheden worden alleen in de aangepaste ALC geladen. Effectief wordt dit een _brug_ tussen de twee ALCs.

Met dit brug concept ziet onze nieuwe assembly-situatie er als volgt uit:

![Diagram dat AlcModule.Engine.dll het overbruggen van de twee ALCs](./media/resolving-dependency-conflicts/alc-diagram.jpg)

Als u er zeker van wilt zijn dat de standaard-logica voor het afhankelijkheden van ALC de afhankelijkheden niet oplost die in de aangepaste ALC moeten worden geladen, moeten deze twee delen van de module in verschillende directory's worden gescheiden. De nieuwe module-indeling heeft de volgende structuur:

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

Om te zien hoe de implementatie verandert, beginnen we met de implementatie van `AlcModule.Engine.dll` :

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

Dit is een eenvoudige container voor de afhankelijkheid, `Shared.Dependency.dll` maar u moet er rekening mee houden als de .net API voor uw functionaliteit die door de cmdlets in de andere assembly voor Power shell wordt verpakt.

De cmdlet `AlcModule.Cmdlets.dll` ziet er als volgt uit:

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

Als we op dit moment **AlcModule** laden en uitvoeren `Test-AlcModule` , krijgen we een `FileNotFoundException` wanneer de standaard-ALC wordt geladen `Alc.Engine.dll` om uit te voeren `EndProcessing()` . Dit is goed, omdat dit betekent dat de standaard ALC geen afhankelijkheden kan vinden die we willen verbergen.

Nu moeten we code toevoegen `AlcModule.Cmdlets.dll` , zodat u weet hoe u deze kunt oplossen `AlcModule.Engine.dll` . Eerst moeten we onze aangepaste ALC definiëren waarmee de assembly's worden omgezet in de map van de module `Dependencies` :

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _depdendencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                s_dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

Vervolgens moeten we onze aangepaste ALC koppelen aan de standaard `Resolving` gebeurtenis alc. Dit is de ALC-versie van de `AssemblyResolve` gebeurtenis op toepassings domeinen. Deze gebeurtenis wordt geactiveerd `AlcModule.Engine.dll` wanneer deze `EndProcessing()` wordt aangeroepen.

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

Bekijk met de nieuwe implementatie de volg orde van de aanroepen die optreden wanneer de module wordt geladen en `Test-AlcModule` wordt uitgevoerd:

![Sequentie diagram van aanroepen met behulp van de aangepaste ALC voor het laden van afhankelijkheden](./media/resolving-dependency-conflicts/alc-sequence.png)

Enkele belang rijke punten zijn:

- De `IModuleAssemblyInitializer` wordt eerst uitgevoerd wanneer de module wordt geladen en de `Resolving` gebeurtenis wordt ingesteld.
- De afhankelijkheden worden pas geladen nadat het programma `Test-AlcModule` is uitgevoerd en de bijbehorende `EndProcessing()` methode is aangeroepen.
- Wanneer `EndProcessing()` wordt aangeroepen, kan de standaard opdracht ALC `AlcModule.Engine.dll` de gebeurtenis niet vinden en deze wordt geactiveerd `Resolving` .
- Onze gebeurtenis-handler koppelt de aangepaste ALC aan de standaard ALC en wordt `AlcModule.Engine.dll` alleen geladen.
- Wanneer `AlcEngine.Use()` wordt aangeroepen in `AlcModule.Engine.dll` , begint de aangepaste ALC opnieuw in om op te lossen `Shared.Dependency.dll` . Met name de oplossing wordt altijd door _ons_ geladen `Shared.Dependency.dll` omdat er nooit conflicten zijn in de standaard ALC en er alleen in onze Directory wordt gezocht `Dependencies` .

Het samen stellen van de implementatie, onze nieuwe indeling van de bron code ziet er als volgt uit:

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

AlcModule. cmdlets. csproj ziet er als volgt uit:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

AlcModule. engine. csproj ziet er als volgt uit:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

Als we de module bouwen, is onze strategie dus:

- PE `AlcModule.Engine`
- PE `AlcModule.Cmdlets`
- Kopieer alles vanuit `AlcModule.Engine` naar de `Dependencies` Directory en onthoud wat er is gekopieerd
- Kopieer alles van niet `AlcModule.Cmdlets` in `AlcModule.Engine` de map van de basis module

Omdat de module-indeling hier van cruciaal belang is voor schei ding van afhankelijkheden, is dit een bouw script dat u vanuit de hoofdmap van de bron kunt gebruiken:

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

Ten slotte hebben we een algemene manier om een assembly-laad context te gebruiken om de afhankelijkheden van de module te isoleren die gedurende een periode robuust blijven naarmate er meer afhankelijkheden worden toegevoegd.

Ga naar deze [github-opslag plaats](https://github.com/rjmholt/ModuleDependencyIsolationExample)voor een meer gedetailleerd voor beeld. In dit voor beeld ziet u hoe u een module migreert voor gebruik van een ALC, terwijl de module in .NET Framework werkt. Ook wordt uitgelegd hoe u .NET Standard en Power shell Standard kunt gebruiken om de kern implementatie te vereenvoudigen.

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a>Assembly-afhandelings-handler voor naast elkaar laden met `Assembly.LoadFile()`

Een andere, mogelijk eenvoudiger, manier om het laden van gelijktijdige assembly's te verzorgen, is door een `AssemblyResolve` gebeurtenis te koppelen aan `Assembly.LoadFile()` . Met `Assembly.LoadFile()` kunt u het voor deel doen van de eenvoudigste oplossing voor het implementeren en werken met .net core en .NET Framework.

Om dit weer te geven, gaan we een beknopt voor beeld bekijken van een implementatie waarbij ideeën worden gecombineerd in het voor beeld van dynamische bindings omleiding en het bovenstaande voor beeld van de assembly-belasting.

We noemen deze module **LoadFileModule**, die een trivial opdracht heeft `Test-LoadFile [-Path] <path>` . Deze module heeft een afhankelijkheid van de `CsvHelper` Assembly (versie 15.0.5).

Net als bij de module ALC moeten we eerst de module splitsen in twee delen.

Het eerste deel heeft de daad werkelijke implementatie `LoadFileModule.Engine` :

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

Het tweede deel is wat Power shell rechtstreeks laadt `LoadFileModule.Cmdlets` . We gebruiken een strategie die vergelijkbaar is met de module ALC, waar we afhankelijkheden in een afzonderlijke map isoleren. Maar deze keer laden we alle assembly's in met een oplossings gebeurtenis in plaats van alleen `LoadFileModule.Engine.dll` .

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

Ten slotte is de lay-out van de module ook vergelijkbaar met de module ALC:

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

Als deze structuur is geïmplementeerd, ondersteunt **LoadFileModule** nu naast andere modules met een afhankelijkheid van **CsvHelper**.

Omdat onze handler van toepassing is op **alle** `AssemblyResolve` gebeurtenissen in het toepassings domein, moeten we een aantal specifieke ontwerp opties hier maken:

- Om het venster te beperken waarin de gebeurtenis kan worden verstoord door andere belasting, beginnen we alleen de verwerking van algemene afhankelijkheden te verwerken nadat deze `LoadFileModule.Engine.dll` is geladen.
- Er `LoadFileModule.Engine.dll` wordt naar de map met afhankelijkheden gepusht, zodat deze wordt geladen door een `LoadFile()` aanroep in plaats van met Power shell. Dit betekent dat een eigen afhankelijkheids belasting altijd een `AssemblyResolve` gebeurtenis verhoogt, zelfs als een andere `CsvHelper.dll` (bijvoorbeeld) wordt geladen in Power shell.
  Dit geeft ons de mogelijkheid om de juiste afhankelijkheid te vinden.
- Omdat we alleen de specifieke afhankelijkheden voor onze module moeten omzetten, kunnen we een woorden lijst met namen en versies van afhankelijkheden in onze handler coderen. In ons bijzonder geval zou u de eigenschap kunnen gebruiken `ResolveEventArgs.RequestingAssembly` om te laten zien of de `CsvHelper` module wordt aangevraagd. Dit werkt echter niet voor afhankelijkheden van afhankelijkheden. bijvoorbeeld, als `CsvHelper` er een gebeurtenis optreedt `AssemblyResolve` . Er zijn andere en moeilijker manieren om dit te doen, zoals het vergelijken van aangevraagde assembly's met de meta gegevens van assembly's in de `Dependencies` map. Maar in dit voor beeld hebben we deze controle duidelijker gemaakt om het probleem te markeren en het voor beeld te vereenvoudigen.

Dit is het belangrijkste verschil tussen de `LoadFile()` strategie en de ALC-strategie: de `AssemblyResolve` gebeurtenis moet alle belastingen in het toepassings domein onderhouden, waardoor het veel moeilijker is om te zorgen dat de afhankelijkheids resolutie wordt Tangled met andere modules. Het ontbreken van ALCs in .NET Framework maakt deze optie echter een goed idee.

### <a name="custom-application-domains"></a>Aangepaste toepassings domeinen

De laatste en meest extreme optie voor het isoleren van de assembly is het gebruik van aangepaste toepassings domeinen.
Toepassings domeinen (gebruikt in het meervoud) zijn alleen beschikbaar in .NET Framework. Ze worden gebruikt om in-process-isolatie te bieden tussen onderdelen van een .NET-toepassing. Een van de toepassingen is het isoleren van assembly-belastingen van elkaar binnen hetzelfde proces.

Toepassings domeinen zijn echter boundary's voor serialisatie. Er kan niet naar objecten in één toepassings domein worden verwezen en deze kunnen niet rechtstreeks worden gebruikt door objecten in een ander toepassings domein. U kunt dit probleem omzeilen door de implementatie uit te voeren `MarshalByRefObject` . Maar wanneer u de typen niet beheert, net als bij afhankelijkheden, is het niet mogelijk om hier een implementatie af te dwingen. De enige oplossing is om grote architectuur wijzigingen te maken. De grens van de serialisatie heeft ook ernstige gevolgen voor de prestaties.

Omdat toepassings domeinen deze ernstige beperking hebben, gecompliceerd zijn om te implementeren en alleen werken in .NET Framework, geven we geen voor beeld van hoe u deze hier kunt gebruiken. Hoewel ze als een mogelijkheid worden vermeld, worden ze niet aanbevolen.

Als u geïnteresseerd bent in het gebruik van een aangepast toepassings domein, kunnen de volgende koppelingen helpen:

- [Conceptuele documentatie over toepassings domeinen](/dotnet/framework/app-domains/application-domains)
- [Voor beelden voor het gebruik van toepassings domeinen](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a>Oplossingen voor conflicten met afhankelijkheden die niet geschikt zijn voor Power shell

Tot slot gaan we een overzicht van een aantal mogelijkheden die beschikbaar zijn bij het zoeken naar .NET-afhankelijkheids conflicten in .NET die kunnen worden getoezegging, maar over het algemeen niet werken voor Power shell.

Deze oplossingen hebben het algemene thema dat ze wijzigen in implementatie configuraties voor een omgeving waar u de toepassing beheert en mogelijk de hele machine. Deze oplossingen zijn gericht op scenario's zoals webservers en andere toepassingen die worden geïmplementeerd in Server omgevingen, waarbij de omgeving bedoeld is voor het hosten van de toepassing en niet kan worden geconfigureerd door de implementatie gebruiker. Ze zijn ook vaak zeer veel .NET Framework gericht, wat betekent dat ze niet werken met Power shell 6 of hoger.

Als u weet dat uw module alleen wordt gebruikt in Windows Power shell 5,1-omgevingen waarvoor u de volledige controle hebt, zijn er mogelijk opties. In **het algemeen mogen modules de status van de globale machine zoals deze niet wijzigen**. Het kan configuraties verstoren die problemen veroorzaken in `powershell.exe` , andere modules of andere afhankelijke toepassingen die ervoor zorgen dat uw module op onverwachte wijze mislukt.

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a>Statische binding omleiding met app.config om te forceren met dezelfde afhankelijkheids versie

.NET Framework toepassingen kunnen gebruikmaken van een `app.config` bestand om een deel van het gedrag van de toepassing declaratief te configureren. Het is mogelijk om een vermelding te schrijven `app.config` die een assembly-binding configureert om assembly-belasting om te leiden naar een bepaalde versie.

Twee problemen met dit voor Power shell zijn:

- .NET core biedt geen ondersteuning `app.config` , dus deze oplossing is alleen van toepassing op `powershell.exe` .
- `powershell.exe` is een gedeelde toepassing die zich in de map bevindt `System32` . Waarschijnlijk is het niet mogelijk om de inhoud van uw module op veel systemen te wijzigen. Zelfs als dit mogelijk is, kan het wijzigen `app.config` van een bestaande configuratie verstoren of invloed hebben op het laden van andere modules.

### <a name="setting-codebase-with-appconfig"></a>Instellen `codebase` met app.config

Om dezelfde redenen voor het configureren `codebase` van de instelling in, `app.config` gaat u niet werken in Power shell-modules.

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a>Afhankelijkheden installeren in de GAC (globale assembly-cache)

Een andere manier om conflicten met de afhankelijkheids versie op te lossen in .NET Framework is door afhankelijkheden te installeren in de GAC, zodat verschillende versies naast elkaar kunnen worden geladen vanuit de GAC.

Opnieuw, voor Power shell-modules, zijn dit de belangrijkste problemen:

- De GAC is alleen van toepassing op .NET Framework, dus u kunt dit niet doen in Power shell 6 en hoger.
- Het installeren van assembly's in de GAC is een wijziging van de status van de globale machine en kan neven effecten in andere toepassingen of andere modules veroorzaken. Het kan ook lastig zijn om goed te kunnen werken, zelfs als uw module de vereiste toegangs rechten heeft. Het verkrijgen van een probleem kan ernstige problemen met de hele machine veroorzaken in andere .NET-toepassingen.

## <a name="further-reading"></a>Meer lezen

Er is nog veel meer informatie over de afhankelijkheids conflicten voor .NET-assembly-versies. Hier vindt u een aantal leuke plaatsen in de weg:

- [.NET: Assembly's in .NET](/dotnet/standard/assembly/)
- [.NET core: het algoritme voor het laden van beheerde assembly](/dotnet/core/dependency-loading/loading-managed)
- [.NET core: informatie over System. runtime. Loader. AssemblyLoadContext](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [.NET core: discussie over side-by-side-oplossingen voor het laden van assembly](https://github.com/dotnet/runtime/issues/13471)
- [.NET Framework: assembly-versies omleiden](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [.NET Framework: Aanbevolen procedures voor het laden van assembly](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [.NET Framework: hoe de runtime assembly's opzoekt](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [.NET Framework: ophalen van assembly laden](/dotnet/standard/assembly/resolve-loads)
- [Stack overflow: assembly-binding omleiding, hoe en waarom?](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why)
- [Power shell: discussie over het implementeren van AssemblyLoadContexts](https://github.com/PowerShell/PowerShell/issues/11571)
- [Power shell: `Assembly.LoadFile()` wordt niet in de standaard AssemblyLoadContext geladen](https://github.com/PowerShell/PowerShell/issues/12052)
- [Rick Strahl: wanneer wordt een .NET-assembly-afhankelijkheid geladen?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded)
- [Tjeerd skeet: overzicht van versie beheer in .NET](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)
- [Nate McMaster: dieper in .NET core-primitieven](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/)
