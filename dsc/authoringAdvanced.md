# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a>Geavanceerde DSC ontwerpen voor de samenstelling en samenwerking

Dit artikel beschrijft de soorten methoden voor het combineren van configuraties en resources.
Het doel voor elk scenario is hetzelfde, te verminderen van complexiteit wanneer meerdere configuraties voorkeur een server end Implementatiestatus bereiken.
Een voorbeeld hiervan is meerdere teams die bijdragen aan het resultaat van een server-implementatie, zoals de eigenaar van een toepassing status van de toepassing en een centraal team brengt wijzigingen aan basisbeveiliging gehandhaafd blijft.
De aspecten van elke methode met inbegrip van de voordelen en risico's, worden hier beschreven.

![Pijplijn](images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Typen gezamenlijke Authoring technieken

Er zijn twee oplossingen die zijn ingebouwd in Local Configuration Manager zodat dit concept:

| Concept | Gedetailleerde informatie
|-|-
| Gedeeltelijke configuraties | [Documentatie](partialconfigs.md)
| Samengestelde Resources | [Documentatie](authoringresourcecomposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>De invloed van elke methode

Een van deze oplossingen kan worden gebruikt voor het beheren van de uitkomst van een server-implementatie.
Er is echter aanzienlijk verschil zijn in de gevolgen van het gebruik van elke methode.

## <a name="partial-configurations"></a>Gedeeltelijke configuraties

Bij het gebruik van gedeeltelijke configuraties worden Local Configuration Manager is geconfigureerd voor het beheren van configuraties met meerdere onafhankelijk van elkaar.
Configuraties worden gecompileerd onafhankelijk en vervolgens toegewezen aan het knooppunt.
Dit vereist LCM vooraf worden geconfigureerd met de naam van elke configuratie.

![PartialConfiguration](images/PartialConfiguration.jpg)

Gedeeltelijke configuraties bieden twee of meer teams volledige controle over configuratie van een server, vaak zonder het voordeel van de communicatieservices of samenwerkingsservices.

Feedback die dit tot bronconflicten, onbedoelde onderdrukkingen en uiteindelijk verlies van true Configuratiebeheer van de activa leiden kan van klanten hebt gegeven.

Bovendien hebben klanten feedback dat wanneer u dit model, elke beheren teams configuratiewijzigingen waarschijnlijk niet volledig worden getest via een release-pijplijn, die leiden tot onverwachte resultaten in de productieomgeving.

**Het is essentieel dat één pijplijn worden gebruikt voor het evalueren van alle wijzigingen release op servers.**

In de onderstaande afbeelding Team B hun Team A. Team een gedeeltelijke configuratie worden vrijgegeven en vervolgens wordt de tests uitgevoerd op een server met beide configuraties toegepast.
In dit model is slechts één instantie gemachtigd wijzigingen aanbrengen in de productieomgeving.

![PartialSinglePipeline](images/PartialSinglePipeline.jpg)

Wanneer er wijzigingen nodig uit de B-Team zijn, dienen ze een Pull-aanvragen op basis van Team van een besturingselement bronomgeving.
Team een zou vervolgens Bekijk de wijzigingen met behulp van test automation en vrijgeven naar productie wanneer er vertrouwen te geven dat de wijzigingen niet leiden fouten in de toepassingen of services die worden gehost door de server tot.

## <a name="composite-resources"></a>Samengestelde Resources

Een samengestelde resource is gewoon een DSC-configuratie die zijn verpakt als een resource.
Er zijn geen speciale vereisten voor het configureren van LCM samengestelde resources accepteren.
De resources worden gebruikt in een nieuwe configuratie en een enkele compilatie resulteert in een MOF-bestand.

![CompositeResource](images/CompositeResource.jpg)

Er zijn twee algemene scenario's voor samengestelde resources.
De eerste is complex en abstracte unieke concepten te verminderen.
De tweede is om toe te staan basislijnen om te worden verpakt voor een team van toepassing voor het veilig implementeren via hun release-pijplijn naar productie nadat alle tests zijn geslaagd.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Samengestelde resources bevordering van zowel de samenstelling en de samenwerking met behulp van een pijplijn tijdens het maken van operationele vervaldatum

U mogelijk al gebruikt samengestelde resources gerust.
Een voorbeeld is **ServiceSet**.
Deze resource beheert de status van meerdere Windows-Services zonder dat ze afzonderlijk.
De eigenschap Name accepteert een matrix met tekenreeksen met de naam van elke service op te geven.
Wanneer de configuratie wordt gecompileerd, bevat het MOF voor elk van de namen die is doorgegeven aan ServiceSet een unieke Service-sectie.

Organisaties mogelijk 'agents' of 'middleware' die moet worden geïnstalleerd op elke server.
Een samengestelde resource is het beste antwoord voor het beheren van de afhankelijkheden, instellingen en configuratie van deze hulpprogramma's en hulpprogramma's.

De persoon die of het team dat verantwoordelijk is voor oplossingen waarbij meerdere servers omvatten ontwikkelt een configuratie met de vereisten.
Vervolgens zou de configuratie worden geleverd als een samengestelde resource met behulp van instructies hiervoor vindt u in de documentatie van samengestelde resource.
Ten slotte de nieuwe samengestelde resource moet worden gepubliceerd naar een locatie zoals een bestandsshare of NuGet feed toepassingsteams waar deze kan gebruiken in hun configuraties.

Telkens wanneer die het team een nieuwe versie geeft, zouden ze Verhoog het versienummer in de module-manifest voor de samengestelde resource.
De App-teams omvatten de samengestelde resource in de configuratie die ze zelf voor het beheren van afhankelijkheden voor toepassingen.
Wanneer de Operations-/ beveiligingsteams een nieuwe versie van de resource kennis ze de App-teams van een nieuwe wijziging.

De App-teams mogelijk een release naar productie waarop de enige wijziging basislijnen wordt geactiveerd.
Dit biedt echter een kans om te evalueren van invloed op toepassingen voordat het risico van een serviceonderbreking.

Houd er rekening mee - Feedback over het gebruik van samengestelde resources is kritiek dat u wijzigingen vereist compileren en het vrijgeven van een nieuwe MOF opgenomen.
Dit vindt standaard plaats.
Elke nieuwe versie van de configuratie van een statische verwijzing naar een specifieke versie van elke resource moet bevatten en moet worden gevalideerd door testen alvorens productie serverknooppunten.
Het proces van het testen en brengt wijzigingen vanuit broncodebeheer Hiermee maakt u een veilige omgeving voor het vrijgeven van de wijziging in kleine, maar vaak batches.

Zie voor meer informatie over het gebruik van de release-pijplijnen voor het beheren van infrastructuur, het technische document: [de Release-pijplijn Model](http://aka.ms/thereleasepipelinemodel).
