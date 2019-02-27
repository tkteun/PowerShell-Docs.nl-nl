---
title: Richtlijnen voor advies ontwikkeling | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 97a2d3587f8f69edc92150474e94a620ff9a2f71
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845792"
---
# <a name="advisory-development-guidelines"></a>Geadviseerde richtlijnen voor de ontwikkeling

Deze sectie beschrijft richtlijnen waarmee u rekening houden moet om ervoor te zorgen goede ervaringen voor ontwikkeling en gebruikers. Soms ze mogelijk van toepassing zijn, en soms ze mogelijk niet.

## <a name="design-guidelines"></a>Richtlijnen voor het ontwerpen

- [Ondersteuning voor een InputObject Parameter (AD01)](./advisory-development-guidelines.md#AD01)

- [Ondersteuning voor de Parameter Force (AD02)](./advisory-development-guidelines.md#AD02)

- [Referenties via Windows PowerShell (AD03) verwerken](./advisory-development-guidelines.md#AD03)

- [Ondersteuning voor codering Parameters (AD04)](./advisory-development-guidelines.md#AD04)

- [Test-Cmdlets moet een Booleaanse waarde (AD05) retourneren](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a>Code-richtlijnen

- [Voer de Cmdlet-klasse Naming Conventions (AC01)](./advisory-development-guidelines.md#AC01)

- [Als er geen Pijpleidinginvoer de methode BeginProcessing (AC02 overschrijft)](./advisory-development-guidelines.md#AC02)

- [Voor het afhandelen van overschrijft verzoeken stoppen de StopProcessing-methode (AC03)](./advisory-development-guidelines.md#AC03)

- [De IDisposable-Interface (AC04) implementeren](./advisory-development-guidelines.md#AC04)

- [Serialisatie-vriendelijk parametertypen (AC05) gebruiken](./advisory-development-guidelines.md#AC05)

- [SecureString gebruiken voor gevoelige gegevens (AC06)](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a>Richtlijnen voor het ontwerpen

De volgende richtlijnen moeten worden overwogen bij het ontwerpen van cmdlets. Als u een ontwerp richtlijn die van toepassing op uw situatie is, moet u kijken naar de richtlijnen van de Code voor vergelijkbare richtlijnen.

### <a name="support-an-inputobject-parameter-ad01"></a>Ondersteuning voor een InputObject Parameter (AD01)

Omdat Windows PowerShell rechtstreeks met Microsoft .NET Framework-objecten werkt, is vaak een .NET Framework-object beschikbaar die exact overeenkomt met het type van de gebruiker moet een bepaalde bewerking uitvoeren. `InputObject` de standaardnaam voor een parameter die dergelijk object als invoer nodig is. Bijvoorbeeld, het voorbeeld **Stop-Proc** cmdlet in de [StopProc zelfstudie](./stopproc-tutorial.md) definieert een `InputObject` parameter van het type proces die ondersteuning biedt voor de invoer van de pijplijn. De gebruiker kan een set van proces-objecten ophalen, bewerken om de exacte objecten selecteren om te stoppen en vervolgens ze doorgeven aan de **Stop-Proc** rechtstreeks cmdlet.

### <a name="support-the-force-parameter-ad02"></a>Ondersteuning voor de Parameter Force (AD02)

Af en toe moet een cmdlet voor het beveiligen van de gebruiker uit te voeren een bewerking. Een dergelijke cmdlet moet ondersteuning bieden voor een `Force` parameter waarmee de gebruiker die beveiliging negeren als de gebruiker heeft machtigingen voor de bewerking uit te voeren.

Bijvoorbeeld, de [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet wordt een alleen-lezen bestand normaal gesproken niet verwijderd. Deze cmdlet ondersteunt echter een `Force` parameter, zodat een gebruiker afdwingen het verwijderen van een bestand alleen-lezen dat kunt. Als de gebruiker al machtiging heeft voor het aanpassen van het kenmerk alleen-lezen en de gebruiker wordt het bestand verwijderd, gebruikt u de `Force` parameter vereenvoudigt de bewerking. Echter, als de gebruiker heeft geen machtiging voor het verwijderen van het bestand, de `Force` parameter heeft geen effect.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Referenties via Windows PowerShell (AD03) verwerken

Er moet een cmdlet definieert een `Credential` parameter vertegenwoordigt referenties. Deze parameter moet van het type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) en moet worden gedefinieerd met behulp van een verklaring van referentie-kenmerk. Deze ondersteuning wordt de gebruiker voor de gebruikersnaam, het wachtwoord of voor beide automatisch gevraagd als een volledige referentie niet rechtstreeks wordt opgegeven. Zie voor meer informatie over het kenmerk referentie [referentie kenmerkdeclaratie](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Ondersteuning voor codering Parameters (AD04)

Als uw cmdlet leest of tekst schrijft naar of van een binaire vorm, zoals het schrijven naar of lezen uit een bestand in een bestandssysteem, klikt u vervolgens heeft de cmdlet Encoding-parameter die aangeeft hoe de tekst is gecodeerd in binaire vorm hebben.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Test-Cmdlets moet een Booleaanse waarde (AD05) retourneren

Cmdlets die het uitvoeren van tests op basis van hun resources moet retourneren een [System.Boolean](/dotnet/api/System.Boolean) Typ aan de pijplijn, zodat ze kunnen worden gebruikt in voorwaardelijke expressies.

## <a name="code-guidelines"></a>Code-richtlijnen

De volgende richtlijnen moeten worden overwogen bij het schrijven van code van de cmdlet. Als u een richtlijn die van toepassing op uw situatie is, moet u kijken naar de richtlijnen voor het ontwerpen voor vergelijkbare richtlijnen.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Voer de Cmdlet-klasse Naming Conventions (AC01)

Door de volgende standaardregels voor naamgeving, die u maakt uw cmdlets sneller wordt ontdekt, en u helpen de gebruiker weet precies wat de cmdlets voor moet doen. Met deze procedure is vooral belangrijk voor ontwikkelaars van Windows PowerShell met omdat-cmdlets openbare typen zijn.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Een Cmdlet in de juiste Namespace definiëren

Normaal gesproken definieert u de klasse voor een cmdlet in een .NET Framework-naamruimte die wordt toegevoegd '. -Opdrachten"aan de naamruimte die staat voor het product waarin de cmdlet wordt uitgevoerd. Bijvoorbeeld, de cmdlets die opgenomen in Windows PowerShell zijn zijn gedefinieerd in de `Microsoft.PowerShell.Commands` naamruimte.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Naam van de Cmdlet-klasse zodat deze overeenkomen met de Cmdlet-naam

Als u de .NET Framework-klasse die een cmdlet, naam van de klasse '*\<werkwoord >**\<zelfstandig naamwoord >**\<opdracht >*', waar u de vervangen *\<Werkwoord >* en  *\<zelfstandig naamwoord >* tijdelijke aanduidingen door de bewerking en zelfstandig naamwoord gebruikt voor de cmdlet-naam. Bijvoorbeeld, de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet wordt geïmplementeerd door een klasse genaamd `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Als er geen Pijpleidinginvoer de methode BeginProcessing (AC02 overschrijft)

Als de cmdlet geen invoer van de pijplijn accepteert, verwerking moet worden geïmplementeerd in de [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode. Gebruik van deze methode kunt Windows PowerShell om te onderhouden tussen cmdlets te bestellen. De eerste cmdlet in de pijplijn retourneert altijd de objecten voordat de resterende cmdlets in de pijplijn krijgen de kans om te beginnen de verwerking.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Voor het afhandelen van overschrijft verzoeken stoppen de StopProcessing-methode (AC03)

Overschrijf de [System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) methode zodat uw cmdlet stopsignaal kan verwerken. Sommige cmdlets erg lang duren om de bewerking te voltooien en ze laat een lange periode tussen aanroepen naar de Windows PowerShell-runtime, zoals wanneer de cmdlet Hiermee blokkeert u de thread in langlopende RPC-aanroepen. Dit bevat cmdlets die naar aanroepen de [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode, naar de [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode, en andere feedback mechanismen die erg lang duren kunnen om uit te voeren. Voor deze gevallen moet de gebruiker mogelijk een stopsignaal verzenden naar deze cmdlets.

### <a name="implement-the-idisposable-interface-ac04"></a>De IDisposable-Interface (AC04) implementeren

Als uw cmdlet objecten die niet worden verwijderd van (geschreven naar de pijplijn heeft) door de [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode, uw cmdlet mogelijk extra object verwijdering. Bijvoorbeeld, als de cmdlet wordt geopend de schuifknop van een bestand van de [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode en houdt de ingang openen voor gebruik door de [System.Management.Automation.Cmdlet.Processrecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode, deze ingang heeft aan het einde van de verwerking wordt gesloten.

De Windows PowerShell-runtime niet altijd aanroepen de [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode. Bijvoorbeeld, de [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode kan niet worden aangeroepen als de cmdlet halverwege via de bewerking is geannuleerd of als een afsluitende fout in een deel van de cmdlet optreedt. Daarom de .NET Framework-klasse voor een cmdlet waarvoor object opschoning moet implementeren de volledige [System.Idisposable](/dotnet/api/System.IDisposable) interface-patroon, waaronder de finalizer, zodat de Windows PowerShell-runtime kunt roept de [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) en [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) methoden aan het einde van de verwerking.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Serialisatie-vriendelijk parametertypen (AC05) gebruiken

Ter ondersteuning van de cmdlet wordt uitgevoerd op externe computers, typen die kunnen worden eenvoudig op de clientcomputer is geserialiseerd en klik vervolgens op de servercomputer gereactiveerd te gebruiken. De volgende typen zijn serialisatie-vriendelijk.

Primitieve typen:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 en UInt64.

- Booleaanse waarde, Guid, Byte [], duur, datum/tijd, Uri en versie.

- Char, String, XmlDocument.

Ingebouwde rehydratable typen:

- PSPrimitiveDictionary

- SwitchParmeter

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Andere typen:

- SecureString

- Containers (lijsten en woordenboeken van het bovenstaande type)

### <a name="use-securestring-for-sensitive-data-ac06"></a>SecureString gebruiken voor gevoelige gegevens (AC06)

Bij het verwerken van gevoelige gegevens altijd gebruik van de [System.Security.Securestring](/dotnet/api/System.Security.SecureString) gegevenstype. Dit omvat bijvoorbeeld de pijplijn-invoer voor de parameters, evenals het retourneren van gevoelige gegevens aan de pijplijn.

## <a name="see-also"></a>Zie ook

[Richtlijnen voor vereiste ontwikkeling](./required-development-guidelines.md)

[De richtlijnen ten zeerste aangeraden ontwikkeling](./strongly-encouraged-development-guidelines.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
