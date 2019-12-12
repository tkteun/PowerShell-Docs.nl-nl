---
title: Richt lijnen voor advies ontwikkeling | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359489"
---
# <a name="advisory-development-guidelines"></a>Geadviseerde richtlijnen voor de ontwikkeling

In deze sectie worden richt lijnen beschreven waarmee u rekening moet houden om te zorgen voor een goede ontwikkeling en gebruikers ervaring. Soms kunnen ze van toepassing zijn, en soms ook niet.

## <a name="design-guidelines"></a>Ontwerprichtlijnen

Bij het ontwerpen van cmdlets moet u rekening houden met de volgende richt lijnen. Als u een ontwerp richtlijn vindt die van toepassing is op uw situatie, raadpleegt u de code richtlijnen voor vergelijk bare richt lijnen.

### <a name="support-an-inputobject-parameter-ad01"></a>Een input object-para meter (AD01) ondersteunen

Omdat Windows Power shell rechtstreeks werkt met Microsoft .NET Framework-objecten, is een .NET Framework-object vaak beschikbaar dat exact overeenkomt met het type dat de gebruiker nodig heeft om een bepaalde bewerking uit te voeren. `InputObject` is de standaard naam voor een para meter waarmee zo'n object als invoer wordt gebruikt. De voor beeld van de cmdlet **Stop-proc** in de [zelf studie StopProc](./stopproc-tutorial.md) definieert een `InputObject` parameter van het type proces die de invoer van de pijp lijn ondersteunt. De gebruiker kan een set proces objecten ophalen, ze bewerken om de exacte objecten te selecteren die moeten worden gestopt en deze vervolgens rechtstreeks door geven aan de cmdlet **Stop-proc** .

### <a name="support-the-force-parameter-ad02"></a>Ondersteuning voor de para meter Force (AD02)

In sommige gevallen moet een cmdlet de gebruiker beveiligen tegen het uitvoeren van een aangevraagde bewerking. Een dergelijke cmdlet moet een `Force` para meter ondersteunen zodat de gebruiker die beveiliging kan onderdrukken als de gebruiker gemachtigd is om de bewerking uit te voeren.

De cmdlet [Remove-item](/powershell/module/microsoft.powershell.management/remove-item) verwijdert bijvoorbeeld Norma liter geen alleen-lezen bestand. Deze cmdlet ondersteunt echter een `Force` para meter, zodat een gebruiker het verwijderen van een alleen-lezen bestand kan afdwingen. Als de gebruiker al gemachtigd is om het kenmerk alleen-lezen te wijzigen en de gebruiker het bestand verwijdert, vereenvoudigt het gebruik van de para meter `Force` de bewerking. De para meter `Force` heeft echter geen effect als de gebruiker niet gemachtigd is om het bestand te verwijderen.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Referenties afhandelen via Windows Power shell (AD03)

Een cmdlet moet een `Credential` para meter definiëren om referenties weer te geven. Deze para meter moet van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) zijn en moet worden gedefinieerd met behulp van een referentie kenmerk declaratie. Deze ondersteuning vraagt de gebruiker automatisch om de gebruikers naam, het wacht woord of voor beide wanneer een volledige referentie niet rechtstreeks is opgegeven. Zie [Credential attribute Declaration](./credential-attribute-declaration.md)(Engelstalig) voor meer informatie over het referentie kenmerk.

### <a name="support-encoding-parameters-ad04"></a>Ondersteuning voor coderings parameters (AD04)

Als uw cmdlet tekst leest of schrijft naar of van een binaire vorm, zoals schrijven naar of lezen van een bestand in een bestands systeem, moet uw cmdlet de para meter encoding hebben die aangeeft hoe de tekst in de binaire vorm wordt gecodeerd.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Test-cmdlets moeten een Booleaanse waarde Retour neren (AD05)

Cmdlets die tests uitvoeren op basis van hun resources, moeten een [System. Boolean](/dotnet/api/System.Boolean) -type retour neren naar de pijp lijn zodat ze kunnen worden gebruikt in voorwaardelijke expressies.

## <a name="code-guidelines"></a>Code richtlijnen

U moet rekening houden met de volgende richt lijnen bij het schrijven van cmdlet-code. Als u een richt lijn vindt die van toepassing is op uw situatie, raadpleegt u de ontwerp richtlijnen voor vergelijk bare richt lijnen.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>De naamgevings conventies van de cmdlet-klasse (AC01) volgen

Door de volgende standaard naamgevings conventies te gebruiken, kunt u uw cmdlets beter detecteerbaar maken en de gebruiker helpen precies te begrijpen wat de cmdlets doen. Deze procedure is vooral belang rijk voor andere ontwikkel aars die gebruikmaken van Windows Power shell, omdat cmdlets open bare typen zijn.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Een cmdlet in de juiste naam ruimte definiëren

Normaal gesp roken definieert u de klasse voor een cmdlet in een .NET Framework naam ruimte die wordt toegevoegd. Commands "naar de naam ruimte die het product vertegenwoordigt waarin de cmdlet wordt uitgevoerd. Cmdlets die zijn opgenomen in Windows Power shell, worden bijvoorbeeld gedefinieerd in de naam ruimte `Microsoft.PowerShell.Commands`.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Geef de cmdlet-klasse een naam die overeenkomt met de naam van de cmdlet

Wanneer u de .NET Framework klasse die een cmdlet implementeert, een naam Geef de klasse ' *\<term > **\<zelfstandignaam >** \<opdracht*> ', waarbij u het *\<woord* > en *\<* tijdelijke aanduidingen voor de naam van de cmdlet vervangt door de bewerking en het zelfstandige woord groep dat u hebt gebruikt voor de para-out. De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) wordt bijvoorbeeld geïmplementeerd door een klasse met de naam `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Als er geen invoer van de pijp lijn is, wordt de methode BeginProcessing (AC02) overschreven

Als uw cmdlet geen invoer van de pijp lijn accepteert, moet de verwerking worden geïmplementeerd in de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) . Met deze methode kan Windows Power shell de volg orde van de cmdlets behouden. De eerste cmdlet in de pijp lijn retourneert altijd de bijbehorende objecten voordat de resterende cmdlets in de pijp lijn de kans krijgen om hun verwerking te starten.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Voor het afhandelen van stop aanvragen wordt de methode StopProcessing (AC03) genegeerd

Overschrijf de methode [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) zodat uw cmdlet het stop signaal kan afhandelen. Sommige cmdlets nemen veel tijd in beslag voor het volt ooien van de bewerking, en ze kunnen een lange tijd passeren tussen aanroepen van de Windows Power shell-runtime, zoals wanneer de cmdlet de thread blokkeert in langlopende RPC-aanroepen. Dit zijn onder andere cmdlets die aanroepen naar de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) , naar de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) en naar andere feedback mechanismen die veel tijd in beslag kunnen nemen. In deze gevallen moet de gebruiker mogelijk een stop signaal verzenden naar deze cmdlets.

### <a name="implement-the-idisposable-interface-ac04"></a>De IDisposable-interface (AC04) implementeren

Als uw cmdlet objecten bevat die niet worden verwijderd van (geschreven naar de pijp lijn) door de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , moet uw cmdlet mogelijk extra objecten worden verwijderd. Als uw cmdlet bijvoorbeeld een bestands ingang opent in de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) en de ingang geopend heeft voor gebruik door de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , moet deze ingang worden gesloten aan het einde van de verwerking.

De Windows Power shell-runtime roept niet altijd de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) aan. Zo kan de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) niet worden aangeroepen als de cmdlet halverwege de bewerking wordt geannuleerd of als er een afsluit fout optreedt in een deel van de cmdlet. Daarom moet de klasse .NET Framework voor een cmdlet die het opruimen van objecten vereist, het volledige [System. IDisposable](/dotnet/api/System.IDisposable) -interface patroon implementeren, met inbegrip van de FINALIZE, zodat de Windows Power shell-runtime de methoden [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) en [System. IDisposable. Dispose *](/dotnet/api/System.IDisposable.Dispose) aan het einde van de verwerking kan aanroepen.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Gebruik een gebruiks vriendelijke parameter typen (AC05) voor serialisatie

Als u het uitvoeren van uw cmdlet op externe computers wilt ondersteunen, gebruikt u typen die eenvoudig kunnen worden geserialiseerd op de client computer en vervolgens op de Server computer worden gemigreerd. De volgende typen zijn geschikt voor serialisatie.

Primitieve typen:

- Byte, SByte, Decimal, single, double, Int16, Int32, Int64, Uint16, UInt32 en UInt64.

- Boolean, GUID, byte [], time span, DateTime, URI en version.

- Char, String, XmlDocument.

Ingebouwde rehydratable-typen:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IP-adres, mailAddress

- Variabele

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Andere typen:

- SecureString

- Containers (lijsten en woorden lijsten van het bovenstaande type)

### <a name="use-securestring-for-sensitive-data-ac06"></a>SecureString gebruiken voor gevoelige gegevens (AC06)

Gebruik voor het verwerken van gevoelige gegevens altijd het gegevens type [System. Security. Securestring](/dotnet/api/System.Security.SecureString) . Dit kan pijp lijn invoer aan para meters bevatten, evenals het retour neren van gevoelige gegevens naar de pijp lijn.

## <a name="see-also"></a>Zie ook

[Vereiste ontwikkel richtlijnen](./required-development-guidelines.md)

[Sterk aanbevolen ontwikkel richtlijnen](./strongly-encouraged-development-guidelines.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
