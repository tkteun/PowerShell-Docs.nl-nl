---
title: Het juiste Power shell NuGet-pakket kiezen voor uw .NET-project
description: Naast de uitvoer bare pakketten die zijn gepubliceerd met elke Power shell-versie, houdt het Power shell-team ook meerdere pakketten bij die beschikbaar zijn op NuGet. Met deze pakketten kan Power shell als een API-platform in .NET worden gericht.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 39369ed872faa76ad2c41d813da5e0a98cf1c078
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85795423"
---
# <a name="choosing-the-right-powershell-nuget-package-for-your-net-project"></a>Het juiste Power shell NuGet-pakket kiezen voor uw .NET-project

Naast de `pwsh` uitvoer bare pakketten die zijn gepubliceerd met elke Power shell-versie, houdt het Power shell-team ook meerdere pakketten bij die beschikbaar zijn op [NuGet][]. Met deze pakketten kan Power shell als een API-platform in .NET worden gericht.

Als .NET-toepassing die Api's levert en verwacht .NET-bibliotheken te laden die zijn eigen (binaire modules) implementeren, is het essentieel dat Power shell beschikbaar is in de vorm van een NuGet-pakket.

Momenteel zijn er verschillende NuGet-pakketten die een weer gave van de Power shell-API surface area bieden. Welk pakket moet worden gebruikt met een bepaald project is niet altijd duidelijk gemaakt. In dit artikel wordt een lampje op enkele veelvoorkomende scenario's voor het Power shell-doel .NET-projecten uitgeschreven en wordt uitgelegd hoe u het juiste NuGet-pakket kunt kiezen voor het doel van uw Power shell-georiënteerd .NET-project.

## <a name="hosting-vs-referencing"></a>Hosting versus referentie

Sommige .NET-projecten proberen code te schrijven die moeten worden geladen in een bestaande Power shell-runtime (zoals `pwsh` , `powershell.exe` de Power Shell integrated console of de ISE), terwijl anderen Power shell in hun eigen toepassingen willen uitvoeren.

- **Verwijzingen** is voor wanneer een project, meestal een module, is bedoeld om te worden geladen in Power shell.
  Het moet worden gecompileerd op basis van de Api's die Power shell biedt om met de API te communiceren, maar de Power shell-implementatie wordt geleverd door het Power Shell-proces dat het laadt in. Voor het verwijzen naar een project kunnen [referentie-assembly's][] of de feitelijke runtime-assembly's Als compilatie doel worden gebruikt, maar moet er wel voor zorgen dat deze niet worden gepubliceerd met de build.
- **Hosting** is wanneer een project een eigen implementatie van Power shell nodig heeft, meestal omdat het een zelfstandige toepassing is die Power shell moet uitvoeren. In dit geval kunnen geen zuivere verwijzings-assembly's worden gebruikt. In plaats daarvan moet een concrete Power shell-implementatie zijn. Omdat een concrete Power shell-implementatie moet worden gebruikt, moet er een specifieke versie van Power shell worden gekozen voor hosting. een toepassing met één host kan geen Power shell-versies met meerdere doelen hebben.

### <a name="publishing-projects-that-target-powershell-as-a-reference"></a>Projecten publiceren die als doel-Power shell als referentie dienen

> [!NOTE]
> We gebruiken de term **Publish** in dit artikel om te verwijzen naar actief `dotnet publish` , waarmee een .net-bibliotheek wordt geplaatst in een map met alle afhankelijkheden, die gereed is voor implementatie naar een bepaalde runtime.

U wordt aangeraden het [kenmerk PrivateAssets][]in te stellen om te voor komen dat u Project afhankelijkheden publiceert die alleen worden gebruikt als compilatie referentie doelen:

```xml
<PackageReference Include="PowerShellStandard.Library" Version="5.1.0.0" PrivateAssets="all" />
```

Als u dit vergeet en een referentie-assembly als doel gebruikt, ziet u mogelijk problemen met betrekking tot het gebruik van de standaard implementatie van de referentie-assembly in plaats van de daad werkelijke implementatie. Dit kan de vorm van a `NullReferenceException` zijn, omdat referentie assemblages de implementatie-API regel matig door voeren `null` .

## <a name="key-kinds-of-powershell-targeting-net-projects"></a>Belangrijkste soorten Power shell-doelen voor .NET-projecten

Hoewel elke .NET-bibliotheek of-toepassing Power shell kan insluiten, zijn er enkele veelvoorkomende scenario's voor het gebruik van Power shell-Api's:

- **Een binaire Power shell-module implementeren**

  Binaire Power shell-modules zijn .NET-bibliotheken die worden geladen door Power shell en die Power shell-Api's moeten implementeren, zoals de [PSCmdlet][] -of [CmdletProvider][] -typen om cmdlets of providers respectievelijk te kunnen weer geven. Omdat ze zijn geladen in, kunnen modules worden gecompileerd op basis van verwijzingen naar Power shell zonder deze te publiceren in hun build. Het is ook gebruikelijk dat modules meerdere Power shell-versies en-platforms willen ondersteunen, in het ideale geval met een minimum aan overhead van schijf ruimte, complexiteit of herhaalde implementatie. Zie [about_Modules][] voor meer informatie over modules.

- **Een Power shell-host implementeren**

  Een Power shell-host biedt een interactie-laag voor de Power shell-runtime. Het is een specifieke vorm van _Hosting_, waarbij een [PSHost][] wordt geïmplementeerd als een nieuwe gebruikers interface voor Power shell. De Power shell-ConsoleHost biedt bijvoorbeeld een Terminal gebruikers interface voor uitvoer bare Power Shell-bestanden, terwijl de host van de Power shell-editor Services en de ISE-host beide een door een editor geïntegreerde, gedeeltelijk Graphical User Interface rond Power shell bieden. Hoewel het mogelijk is om een host te laden naar een bestaand Power Shell-proces, is het veel meer gebruikelijk voor een implementatie van een host om te fungeren als een zelfstandige Power shell-implementatie waarmee de Power shell-engine opnieuw wordt gedistribueerd.

- **Aanroepen van Power shell vanuit een andere .NET-toepassing**

  Net als bij elke toepassing kan Power shell worden aangeroepen als een subproces voor het uitvoeren van werk belastingen. Als .NET-toepassing is het ook mogelijk om Power shell in-process aan te roepen om een back-up te krijgen van volledige .NET-objecten voor gebruik binnen de aanroepende toepassing. Dit is een meer algemene vorm van _Hosting_, waarbij de toepassing een eigen Power shell-implementatie voor intern gebruik bevat. Voor beelden hiervan zijn een service of daemon met Power shell voor het beheren van de computer status of een webtoepassing die Power shell op aanvraag uitvoert om iets te doen, zoals het beheren van Cloud implementaties.

- **Eenheid voor het testen van Power shell-modules vanuit .NET**

  Hoewel modules en andere bibliotheken die zijn ontworpen om de functionaliteit van Power shell beschikbaar te maken, voornamelijk moeten worden getest vanuit Power shell (wij adviseren u de [ziekte][]te testen), is het soms nood zakelijk dat u test-api's voor een Power shell-module van .net bijvoegt. Deze situatie is afhankelijk van de code van de module die een aantal Power shell-versies probeert te richten, terwijl tests moeten worden uitgevoerd op specifieke, concrete implementaties.

## <a name="powershell-nuget-packages-at-a-glance"></a>Power shell NuGet-pakketten in één oogopslag

In dit artikel worden de volgende NuGet-pakketten besproken die Power shell-Api's beschikbaar maken:

- [PowerShellStandard. Library][], een referentie-assembly waarmee u één assembly kunt bouwen die door meerdere Power shell-Runtimes kan worden geladen.
- [Micro soft. Power shell. SDK][], de manier waarop u de hele Power shell SDK kunt richten en hosten
- Het [System. Management. Automation][] -pakket, de kern runtime van Power shell en Engine-implementatie, dat nuttig kan zijn bij minimale gehoste implementaties en voor versie-specifieke doel scenario's.
- De **Windows Power shell-referentie-assembly's**, de manier om Windows Power shell te richten en effectief opnieuw te hosten (Power shell-versies 5,1 en lager).

> [!NOTE]
> Het [Power shell NuGet][] -pakket is helemaal geen .net-bibliotheek pakket, maar voorziet in plaats daarvan de implementatie van het globale hulp programma van Power shell dotnet. Dit mag niet worden gebruikt door projecten, omdat deze alleen een uitvoerbaar bestand bevat.

## <a name="powershellstandardlibrary"></a>PowerShellStandard. Library

De standaard bibliotheek van Power shell is een referentie-assembly die het snij punt van de Api's van de Power shell-versie 7, 6 en 5,1 vastlegt. Dit biedt een API-Opper vlak met gecontroleerde compilaties om .NET-code te compileren, zodat .NET-projecten de Power shell-versie 7, 6 en 5,1 kunnen richten, zonder dat er sprake is van het aanroepen van een API.

Power shell Standard is bedoeld voor het schrijven van Power shell-modules of andere code die alleen is bedoeld om te worden uitgevoerd na het laden in een Power Shell-proces. Omdat het een referentie-assembly is, bevat Power shell Standard geen implementatie zelf, dus biedt geen functionaliteit voor zelfstandige toepassingen.

### <a name="using-powershell-standard-with-different-net-runtimes"></a>Power shell Standard gebruiken met verschillende .NET-Runtimes

Power shell Standard streeft naar de [.NET Standard 2,0][] -doel-runtime, een gevel-runtime die is ontworpen om een gemeen schappelijk Surface Area te bieden dat wordt gedeeld door .NET Framework en .net core. Dit maakt het mogelijk om één enkele runtime te maken die geschikt is voor meerdere Power shell-versies, maar heeft de volgende consequenties:

- Voor het laden van de module of bibliotheek in Power shell moet mini maal .NET 4.6.1; .net 4,6 en .NET 4.5.2 worden uitgevoerd. geen ondersteuning voor .NET Standard. Een nieuwere versie van Windows Power shell betekent geen nieuwere versie van .NET Framework. Windows Power shell 5,1 kan worden uitgevoerd op .NET 4.5.2.
- Als u wilt werken met een Power shell met .NET Framework 4.7.1 of lager, moet u de .NET 4.6.1 [netstandard. Library][] -implementatie nodig hebben om de netstandard.dll en andere Shim-assembly's in oudere .NET Framework versies op te geven.

Power shell 6 + bevat een eigen Shim-assembly voor type door sturen van .NET Framework 4.6.1 (en hoger) naar .NET core. Dit betekent dat als een module alleen Api's gebruikt die in .NET Core zijn opgenomen, Power shell 6 + kan worden geladen en uitgevoerd wanneer deze is gemaakt voor .NET Framework 4.6.1 (het `net461` runtime-doel).

Dit betekent dat binaire modules die gebruikmaken van Power shell Standard om meerdere Power shell-versies te richten met één gepubliceerd DLL-bestand twee opties hebben:

1. Publiceren van een assembly die is gemaakt voor de runtime van de `net461` doel groep. Dit omvat:
   - Het project voor de `net461` runtime publiceren
   - U kunt ook compileren op basis `netstandard2.0` van de runtime (zonder de build-uitvoer) te gebruiken om ervoor te zorgen dat alle gebruikte api's ook aanwezig zijn in .net core.

1. Een assembly-build publiceren voor de runtime van de `netstandard2.0` doel groep. Dit vereist:
   - Het project voor de `netstandard2.0` runtime publiceren
   - Het nemen `net461` van de afhankelijkheden van netstandard. Library en het kopiëren ervan naar de publicatie locatie van de assembly van het project, zodat de assembly met type-doorgestuurd is gecorrigeerd in .NET Framework.

Als u Power shell-modules of-bibliotheken wilt maken die zijn gericht op oudere versies van .NET Framework, is het wellicht beter om te richten op meerdere .NET-Runtimes. Hiermee wordt een assembly voor elke runtime-doel publicatie gepubliceerd en de juiste assembly moet worden geladen in de module laad tijd (bijvoorbeeld met een kleine psm1 als de hoofd module).

### <a name="testing-powershell-standard-projects-in-net"></a>Power shell Standard-projecten testen in .NET

Wanneer het gaat om uw module te testen in .NET test lopers zoals xUnit, moet u er rekening mee houden dat compilaties niet tot nu toe kunnen gaan. U moet uw module testen op de relevante Power shell-platforms.

Als u Api's wilt testen die zijn gebouwd op basis van Power shell Standard in .NET, moet u `Microsoft.Powershell.SDK` een test afhankelijkheid toevoegen met .net core (waarbij de versie is ingesteld op overeenkomen met de gewenste Power shell-versie) en de juiste Windows Power shell-referentie-assembly's met .NET Framework.

Zie [dit blog bericht][]voor meer informatie over Power shell Standard en het gebruik ervan om een binaire module te schrijven die in meerdere Power shell-versies kan worden gebruikt. Zie ook de [standaard opslagplaats voor Power shell][] op github.

## <a name="microsoftpowershellsdk"></a>Micro soft. Power shell. SDK

`Microsoft.PowerShell.SDK` is een meta pakket dat alle onderdelen van de Power shell-SDK ophaalt in één NuGet-pakket. Een op zichzelf staande .NET-toepassing kan micro soft. Power shell. SDK gebruiken om wille keurige Power shell-functionaliteit uit te voeren zonder dat dit afhankelijk is van externe Power shell-installaties of-bibliotheken.

> [!NOTE]
> De Power shell SDK verwijst alleen naar alle onderdeel pakketten waaruit Power shell is opgebouwd en die kan worden gebruikt voor .NET-ontwikkeling met Power shell.

Een bepaalde `Microsoft.Powershell.SDK` versie bevat de concrete implementatie van dezelfde versie van de Power shell-toepassing. versie 7,0 bevat de implementatie van Power shell 7,0 en het uitvoeren van opdrachten of scripts met de-service is grotendeels hetzelfde als het uitvoeren van deze in Power shell 7,0.

Het uitvoeren van Power shell-opdrachten uit de SDK is voornamelijk, maar niet volledig, hetzelfde als het uitvoeren van `pwsh` . [Begin-taak][] is bijvoorbeeld op dit moment afhankelijk van het `pwsh` uitvoer bare bestand dat beschikbaar is en werkt daarom niet `Microsoft.Powershell.SDK` standaard.

Door `Microsoft.Powershell.SDK` te richten op basis van een .NET-toepassing kunt u met alle implementatie-assembly's van Power shell, zoals `System.Management.Automation` , `Microsoft.PowerShell.Management` en andere module-assembly's, integreren.

Het publiceren van een toepassings doel `Microsoft.Powershell.SDK` bevat al deze assembly's en alle afhankelijkheden van Power shell zijn vereist. Het bevat ook andere assets die Power shell nodig heeft voor de build, zoals de module manifesten voor `Microsoft.PowerShell.*` modules en de `ref` map die is vereist door [add-type][].

Gezien de volledigheid van `Microsoft.Powershell.SDK` , is het het meest geschikt voor:

- Implementatie van Power shell-hosts.
- xUnit test van bibliotheken die zijn gericht op Power shell-referentie-assembly's.
- Power shell in-process aanroepen vanuit een .NET-toepassing.

`Microsoft.PowerShell.SDK` kan ook worden gebruikt als een referentie doel wanneer een .NET-project is bedoeld om te worden gebruikt als module of anderszins wordt geladen door Power shell, maar is afhankelijk van Api's die alleen in een bepaalde versie van Power shell aanwezig zijn. Houd er rekening mee dat een assembly die wordt gepubliceerd voor een specifieke versie van `Microsoft.PowerShell.SDK` , alleen veilig kan worden geladen en gebruikt in die versie van Power shell. Als u meerdere Power shell-versies met specifieke Api's wilt richten, zijn er meerdere builds vereist, waarbij elk een eigen versie van heeft `Microsoft.Powershell.SDK` .

> [!NOTE]
> De Power shell SDK is alleen beschikbaar voor Power shell versie 6 en hoger. Als u gelijkwaardige functionaliteit wilt bieden met Windows Power shell, gebruikt u de Windows Power shell-referentie-assembly's die hieronder worden beschreven.

## <a name="systemmanagementautomation"></a>System. Management. Automation

Het `System.Management.Automation` pakket is de kern van de Power shell-SDK. Deze bestaat op NuGet, voornamelijk als een Asset voor `Microsoft.Powershell.SDK` het intrekken van. Het kan echter ook rechtstreeks worden gebruikt als een pakket voor kleinere hosting scenario's en modules voor versie doelen.

Het is `System.Management.Automation` met name mogelijk dat het pakket een wille keurige provider van de Power shell-functionaliteit is wanneer:

- U wilt nu alleen de Power shell-taal functionaliteit (in de `System.Management.Automation.Language` naam ruimte) gebruiken, zoals de Power shell-parser, AST en de AST bezoekers api's (bijvoorbeeld voor statische analyse van Power shell).
- U wilt alleen specifieke opdrachten uitvoeren vanuit de `Microsoft.PowerShell.Core` module en deze uitvoeren in een sessie status die is gemaakt met de [CreateDefault2][] -standaard methode.

Daarnaast `System.Management.Automation` is een handige referentie-assembly als:

- U wilt Api's richten die alleen aanwezig zijn in een specifieke Power shell-versie
- U bent niet afhankelijk van typen buiten de `System.Management.Automation` Assembly (bijvoorbeeld typen geëxporteerd door cmdlets in `Microsoft.PowerShell.*` modules).

## <a name="windows-powershell-reference-assemblies"></a>Windows Power shell-referentie-assembly's

Voor Power shell versie 5,1 en ouder (Windows Power shell) is er geen SDK voor het leveren van een implementatie van Power shell, omdat de implementatie van Windows Power shell deel uitmaakt van Windows.

In plaats daarvan bieden de referentie-assembly's van Windows Power shell zowel referentie doelen als een manier om Windows Power shell opnieuw te hosten. dit doet hetzelfde als de Power shell SDK voor versie 6 en hoger.

Windows Power shell-referentie-assembly's hebben in plaats van onderscheid te maken met versie een ander pakket voor elke versie van Windows Power shell:

- [PowerShell 5.1](https://www.nuget.org/packages/Microsoft.PowerShell.5.ReferenceAssemblies/)
- [Power Shell 4](https://www.nuget.org/packages/Microsoft.PowerShell.4.ReferenceAssemblies/)
- [Power Shell 3](https://www.nuget.org/packages/Microsoft.PowerShell.3.ReferenceAssemblies/)

Informatie over het gebruik van de Windows Power shell-referentie-assembly's vindt u in de [Windows Power shell-SDK][].

## <a name="real-world-examples-using-these-nuget-packages"></a>Praktijk voorbeelden die gebruikmaken van deze NuGet-pakketten

Verschillende Power shell-hulp programma projecten richten zich op verschillende Power shell NuGet-pakketten, afhankelijk van hun behoeften. Hieronder vindt u enkele voor beelden.

### <a name="psreadline"></a>PSReadLine

[PSReadLine][], de Power shell-module die een groot deel van de veelzijdige console-ervaring van Power shell biedt, streeft naar een Power Shell-standaard als afhankelijkheid in plaats van een specifieke Power shell-versie en streeft naar de `net461` .NET-runtime in de [csproj][].

Power shell 6 + levert een eigen Shim-assembly waarmee een DLL kan `net461` worden gebruikt voor het uitvoeren van ' alleen werk ' in (door het omleiden van bindingen met .NET Framework `mscorlib.dll` naar de relevante .net core-Assembly).

Dit vereenvoudigt de lay-out van de module en de levering aanzienlijk, omdat Power Shell-standaard garandeert dat alleen de gebruikte Api's aanwezig zijn in Power shell 5,1 en Power shell 6 +, terwijl de module ook kan verzenden met slechts één assembly.

Het .NET 4.6.1-doel houdt in dat Windows Power shell die wordt uitgevoerd op .NET 4.5.2 en .NET 4,6, echter niet wordt ondersteund.

### <a name="powershell-editor-services"></a>Power shell editor-Services

[Power shell editor Services][] (PSES) is de back-end voor de [Power shell-extensie][] voor [Visual Studio code][]en is in feite een vorm van Power shell-module die wordt geladen door een uitvoerbaar bestand van Power shell

PSES biedt concrete implementatie doelen voor de `netcoreapp2.1` doel-Power shell 6 + (omdat runtime van Power shell 7 `netcoreapp3.1` achterwaarts compatibel is) en `net461` op Windows Power shell 5,1, maar bevat het meren deel van de logica in een tweede assembly die is gericht op `netstandard2.0` en Power shell Standard. Hierdoor kunnen ze afhankelijkheden ophalen die vereist zijn voor .NET core-en .NET Framework-platformen, terwijl het grootste deel van de code base nog steeds wordt vereenvoudigd bij een uniforme abstractie.

Omdat het is gebouwd op basis van Power shell Standard, vereist PSES een runtime-implementatie van Power shell om correct te kunnen worden getest. Om dit te doen, nemen [de xUnit-tests van PSES][] door `Microsoft.PowerShell.SDK` en om `Microsoft.PowerShell.5.ReferenceAssemblies` een Power shell-implementatie in de test omgeving te bieden.

Net als bij PSReadLine biedt PSES geen ondersteuning voor .NET 4,6 en lager, maar wordt er tijdens runtime [een controle uitgevoerd][] voordat een van de api's wordt aangeroepen die een crash ondervindt in de lagere .NET Framework Runtimes.

### <a name="psscriptanalyzer"></a>PSScriptAnalyzer

[PSScriptAnalyzer][], de pluisie voor Power shell, moet doel syntactische elementen zijn die alleen in bepaalde versies van Power shell zijn geïntroduceerd. Omdat herkenning van deze syntactische elementen wordt uitgevoerd door een [AstVisitor2][]te implementeren, is het niet mogelijk om PowerShellStandard te gebruiken en ook AST-methoden te implementeren voor nieuwere Power shell-syntaxis.

In plaats daarvan [bedoelt PSScriptAnalyzer elke Power shell-versie][] als een bouw configuratie en produceert deze een afzonderlijke dll voor elk van deze versies. Dit verhoogt de bouw grootte en complexiteit, maar maakt het volgende mogelijk:

- Versie-specifieke API-doel items
- Versie-specifieke functionaliteit die moet worden geïmplementeerd zonder dat er runtime kosten in rekening worden gebracht
- Het totale aantal ondersteuning voor Windows Power shell is helemaal naar .NET Framework 4.5.2

## <a name="summary"></a>Samenvatting

In dit artikel hebben we de NuGet-pakketten die beschikbaar zijn voor het doel van de implementatie van een .NET-project dat Power shell gebruikt, vermeld en besproken, en de redenen voor het gebruik ervan.

Als u de samen vatting hebt overgeslagen, zijn er enkele algemene aanbevelingen:

- Power shell- **modules** moeten worden gecompileerd op basis van Power shell Standard als alleen api's voor verschillende Power shell-versies hoeven te worden gebruikt.
- Power shell- **hosts en-toepassingen** die Power shell intern moeten uitvoeren, moeten gericht zijn op de Power shell SDK voor Power shell 6 + of de relevante Windows Power shell-referentie-Assembly's voor Windows Power shell.
- Power shell-modules die **Version-specifieke api's** nodig hebben, moeten zijn gericht op de Power shell SDK of Windows Power shell-referentie-assembly's voor de vereiste Power shell-versies, met behulp van deze als referentie-assembly's (dat wil zeggen, de Power shell-afhankelijkheden niet publiceren

<!--link references -->

[.NET Standard 2,0]: /dotnet/standard/net-standard
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[Add-type]: /powershell/module/microsoft.powershell.utility/add-type
[AstVisitor2]: /dotnet/api/system.management.automation.language.astvisitor2
[CmdletProvider]: /dotnet/api/system.management.automation.provider.cmdletprovider
[CreateDefault2]: /dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2
[csproj]: https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/PSReadLine.csproj
[Micro soft. Power shell. SDK]: https://www.nuget.org/packages/Microsoft.PowerShell.SDK/
[Netstandaard. Library]: https://www.nuget.org/packages/NETStandard.Library/
[NuGet]: https://www.nuget.org/
[Hiermee wordt een controle uitgevoerd]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/src/PowerShellEditorServices.Hosting/EditorServicesLoader.cs#L231-L251
[Pester]: https://github.com/Pester/Pester
[Power shell editor-Services]: https://github.com/PowerShell/PowerShellEditorServices/
[Power shell-uitbrei ding]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[Power shell-NuGet]: https://www.nuget.org/packages/PowerShell/
[Standaard-Power shell-opslag]: https://github.com/PowerShell/PowerShellStandard
[PowerShellStandard. Library]: https://www.nuget.org/packages/PowerShellStandard.Library/
[PSCmdlet]: /dotnet/api/system.management.automation.pscmdlet
[XUnit van PSES]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/test/PowerShellEditorServices.Test/PowerShellEditorServices.Test.csproj#L15-L20
[PSHost]: /dotnet/api/system.management.automation.host.pshost
[PrivateAssets-kenmerk]: /dotnet/core/tools/csproj#packagereference
[PSReadLine]: https://github.com/PowerShell/PSReadLine
[PSScriptAnalyzer]: https://github.com/powershell/psscriptanalyzer
[Referentie-assembly's]: https://github.com/dotnet/standard/blob/master/docs/history/evolution-of-design-time-assemblies.md#definitions
[Begin taak]: /powershell/module/microsoft.powershell.core/start-job
[System. Management. Automation]: https://www.nuget.org/packages/System.Management.Automation/
[streeft elke Power shell-versie]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/Engine/Engine.csproj
[Dit blog bericht]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[Visual Studio Code]: https://code.visualstudio.com/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell
