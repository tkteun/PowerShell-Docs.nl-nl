---
title: Het maken van een Windows PowerShell-Provider navigatie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081849"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Een Windows PowerShell-navigatieprovider maken

In dit onderwerp wordt beschreven hoe u een Windows PowerShell navigatie-provider die het gegevensarchief kunt gaan maken. Dit type provider biedt ondersteuning voor recursieve opdrachten, geneste containers en relatieve paden.

> [!NOTE]
> U kunt downloaden de C# bronbestand (AccessDBSampleProvider05.cs) voor deze provider met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.
>
> Zie voor meer informatie over andere Windows PowerShell-provider-implementaties, [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

De provider die hier worden beschreven Hiermee kunt u de ingang van de gebruiker een Access-database als een station zodat de gebruiker in de gegevenstabellen in de database navigeren kan. Bij het maken van uw eigen provider navigatie, kunt u methoden die u kunnen station gekwalificeerde paden die zijn vereist om de navigatie te maken, relatieve paden normaliseren, items van het gegevensarchief, evenals de methoden die namen van de onderliggende ophalen, ophalen van het bovenliggende pad van een item en te testen verplaatsen implementeren om te identificeren als een item een container is.

> [!CAUTION]
> Let erop dat dit ontwerp wordt ervan uitgegaan dat een database waarvoor een veld met de naam-ID en dat het type van het veld LongInteger is.

De volgende lijst bevat secties in dit onderwerp. Als u niet bekend bent met het schrijven van een Windows PowerShell-navigatie-provider, leest u deze informatie in de volgorde waarin deze wordt weergegeven. Echter, als u bekend bent met het schrijven van een Windows PowerShell-navigatie-provider, gaat u rechtstreeks naar de informatie die u nodig hebt.

- [Een klasse PS navigatie Provider definiëren](#Define-the-Windows-PowerShell-provider)

- [Basisfunctionaliteit definiëren](#Defining-Base-Functionality)

- [Het maken van een PS-pad](#Creating-a-Windows-PowerShell-Path)

- [Bij het ophalen van het bovenliggende pad](#Retrieving-the-Parent-Path)

- [Bij het ophalen van de naam van het onderliggende-pad](#Retrieve-the-Child-Path-Name)

- [Als een Item een Container is bepalen](#Determining-if-an-Item-is-a-Container)

- [Een Item verplaatst](#Moving-an-Item)

- [Bezig met koppelen van dynamische Parameters voor de `Move-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [Een relatief pad normaliseren](#Normalizing-a-Relative-Path)

- [Voorbeeld van code](#Code-Sample)

- [Objecttype definiëren en opmaak](#Defining-Object-Types-and-Formatting)

- [Het bouwen van de Windows PowerShell-Provider](#Building-the-Windows-PowerShell-provider)

- [De Windows PowerShell-Provider testen](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>De Windows PowerShell-provider definiëren

Een Windows PowerShell-navigatie-provider moet maakt u een .NET-klasse die is afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basisklasse. Hier volgt de definitie van de klasse voor de navigatie-provider in deze sectie beschreven.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Houd er rekening mee dat in deze provider, de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk bevat twee parameters. De eerste parameter geeft u een gebruiksvriendelijke naam voor de provider die wordt gebruikt door Windows PowerShell. De tweede parameter geeft u de Windows PowerShell-specifieke mogelijkheden die de provider wordt aangegeven in de Windows PowerShell-runtime tijdens de verwerking van de opdracht. Er zijn geen specifieke mogelijkheden van Windows PowerShell die worden toegevoegd voor deze provider.

## <a name="defining-base-functionality"></a>Basisfunctionaliteit definiëren

Zoals beschreven in [ontwerp uw PS mailprovider](./designing-your-windows-powershell-provider.md), wordt de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basisklasse is afgeleid van diverse andere klassen die andere provider -functionaliteit. Een Windows PowerShell-navigatie-provider, daarom moet definiëren van de functionaliteit van de bovenliggende klassen.

Zie voor het implementeren van de functionaliteit voor het toevoegen van informatie over de initialisatie van de sessie-specifieke en voor het vrijgeven van resources die worden gebruikt door de provider [het maken van een eenvoudige PS-Provider](./creating-a-basic-windows-powershell-provider.md). De meeste providers (met inbegrip van de provider die hier worden beschreven) kunnen echter de standaardimplementatie van deze functionaliteit verstrekt door de Windows PowerShell gebruiken.

Voor toegang tot het gegevensarchief via een Windows PowerShell-station, moet u de methoden voor het implementeren de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basisklasse. Zie voor meer informatie over het implementeren van deze methoden [het maken van een Windows PowerShell station Provider](./creating-a-windows-powershell-drive-provider.md).

Als u wilt bewerken van de items van een gegevensarchief, zoals ophalen, instellen en items wissen, de provider van de methoden die door moet implementeren de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basisklasse. Zie voor meer informatie over het implementeren van deze methoden [het maken van een Windows PowerShell-Provider Item](./creating-a-windows-powershell-item-provider.md).

Ga naar de onderliggende items of de namen van de gegevensopslag, evenals de methoden maken, kopiëren, wijzigen en verwijderen van items, moet u de methoden die door implementeren de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)basisklasse. Zie voor meer informatie over het implementeren van deze methoden [het maken van een Windows PowerShell-Provider Container](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Het maken van een Windows PowerShell-pad

Windows PowerShell-navigatie-provider een provider interne Windows PowerShell-pad gebruiken om te navigeren van de items van het gegevensarchief. Het maken van een provider interne pad de provider moeten implementeren de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) ondersteunt methode aanroepen van de cmdlet combineren-pad. Deze methode wordt een pad naar bovenliggende en onderliggende combineert in een provider interne pad, met behulp van een provider-specifieke padscheidingsteken tussen de bovenliggende en onderliggende paden.

De standaardimplementatie duurt paden met '/' of '\\'als het padscheidingsteken normaliseert scheidingsteken voor het pad naar'\\', worden de delen van de bovenliggende en onderliggende paden gecombineerd met het scheidingsteken tussen beide en retourneert een tekenreeks zijn met de gecombineerde paden.

Deze navigatie-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Om te onthouden over het implementeren van MakePath

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- De implementatie van de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) methode moet het pad als een juridische volledig gekwalificeerde pad in de naamruimte van de provider niet valideren. Let erop dat elke parameter alleen een deel van een pad vertegenwoordigen kan en de gecombineerde onderdelen mogelijk een volledig gekwalificeerde pad niet genereren. Bijvoorbeeld, de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) methode voor de provider bestandssysteem mogelijk 'windows\system32' de `parent` parameter en 'abc.dll' in de `child` parameter. De methode lid wordt van deze waarden met de '\\"scheidingsteken en retourneert 'windows\system32\abc.dll', die niet een volledig gekwalificeerde bestandssysteempad.

  > [!IMPORTANT]
  > De onderdelen van het bestandspad opgegeven in de aanroep naar [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) zijn niet toegestaan in de naamruimte van de provider kan bevatten. Deze tekens waarschijnlijk worden gebruikt voor jokertekens en de implementatie van deze methode moet niet verwijderd.

## <a name="retrieving-the-parent-path"></a>Bij het ophalen van het bovenliggende pad

Windows PowerShell navigatieproviders implementeert de [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) methode voor het ophalen van het bovenliggende onderdeel van de opgegeven volledige of gedeeltelijke Provider-specifieke pad. De methode verwijdert u de onderliggende deel van het pad en retourneert het bovenliggende onderdeel van het bestandspad. De `root` parameter geeft u de volledig gekwalificeerde pad naar de hoofdmap van een station. Deze parameter kan niet null of leeg zijn als een gekoppeld station niet gebruikt voor de bewerking voor het ophalen wordt. Als u een hoofdmap opgeeft, moet de methode een pad terugkeren naar een container in dezelfde structuur als de hoofdmap.

De provider van de navigatie voorbeeld wordt met deze methode niet overschreven, maar maakt gebruik van de standaardimplementatie. Deze paden die gebruikmaken van zowel accepteert '/' en '\\' als scheidingsteken in pad. Het eerst het pad dat alleen normaliseert "\\" scheidingstekens, splitst u vervolgens het bovenliggende pad uit op de laatste '\\' en retourneert het bovenliggende pad.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Om te weten over het implementeren van GetParentPath

De implementatie van de [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) methode moet het pad op het scheidingsteken in pad voor de naamruimte van de provider lexicaal opsplitsen. Bijvoorbeeld, de bestandssysteem-provider maakt gebruik van deze methode om te zoeken naar de laatste '\\"en wordt alles geretourneerd aan de linkerkant van het scheidingsteken.

## <a name="retrieve-the-child-path-name"></a>De naam van de onderliggende pad ophalen

Uw provider navigatie implementeert de [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) methode voor het ophalen van de naam (bladelement) van het onderliggende lid van het item dat zich bevindt in de aangegeven volledige of gedeeltelijke providerspecifiek pad.

Deze methode wordt niet door de voorbeeld-navigatie-provider worden overschreven. Hieronder ziet u de standaardimplementatie. Deze paden die gebruikmaken van zowel accepteert '/' en '\\' als scheidingsteken in pad. Het eerst het pad dat alleen normaliseert "\\" scheidingstekens, splitst u vervolgens het bovenliggende pad uit op de laatste '\\' en retourneert de naam van de onderliggende onderdeel van het bestandspad.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Om te onthouden over het implementeren van GetChildName

De implementatie van de [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) methode moet het pad op de padscheidingsteken lexicaal opsplitsen. Als het opgegeven pad geen padscheidingstekens bevat, moet het pad wijzigen door de methode worden geretourneerd.

> [!IMPORTANT]
> Het pad dat in de aanroep van deze methode kan bevat tekens die ongeldig zijn in de naamruimte van de provider. Deze tekens worden meestal gebruikt voor jokertekens of reguliere expressie die overeenkomt met en de implementatie van deze methode moet deze niet verwijderen.

## <a name="determining-if-an-item-is-a-container"></a>Als een Item een Container is bepalen

De navigatie-provider kunt implementeren om de [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) methode om te bepalen als het opgegeven pad geeft aan een container dat. Deze retourneert ' True ' als het pad naar een container en ONWAAR anders aangeeft. De gebruiker deze methode om te kunnen gebruiken, moet de `Test-Path` -cmdlet voor het opgegeven pad.

De volgende code toont de [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) -implementatie in ons voorbeeld navigatie-provider. De methode wordt gecontroleerd of het opgegeven pad juist is en of de tabel bestaat en ' True retourneert ' als het pad aangeeft een container dat.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Om te onthouden over het implementeren van IsItemContainer

Uw provider navigatie .NET-klasse kan gaan om mogelijkheden van de provider van ExpandWildcards, Filter, opnemen of uitsluiten, van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dit geval wordt de implementatie van [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) nodig om ervoor te zorgen dat het pad dat is doorgegeven aan de vereisten voldoet. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) eigenschap.

## <a name="moving-an-item"></a>Een Item verplaatst

Ter ondersteuning van de `Move-Item` cmdlet, uw provider navigatie implementeert de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) methode. Deze methode wordt verplaatst het item dat is opgegeven door de `path` parameter voor de container op het pad dat is opgegeven in de `destination` parameter.

De voorbeeld-navigatie-provider wordt niet overschreven de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) methode. Hier volgt de standaardimplementatie.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Om te onthouden over het implementeren van MoveItem

Uw provider navigatie .NET-klasse kan gaan om mogelijkheden van de provider van ExpandWildcards, Filter, opnemen of uitsluiten, van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dit geval wordt de implementatie van [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) moet ervoor zorgen dat het pad dat is doorgegeven aan de vereisten voldoet. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de **CmdletProvider.Exclude** eigenschap.

Standaard onderdrukkingen van deze methode moeten niet objecten verplaatsen via bestaande objecten, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Bijvoorbeeld, de provider van het bestandssysteem worden niet gekopieerd c:\temp\abc.txt via een bestaand c:\bar.txt-bestand, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Als het pad opgegeven in de `destination` parameter bestaat en een container, is de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is niet vereist. In dit geval [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) moet verplaatsen van het item dat wordt aangegeven door de `path` parameter voor de container aangegeven door de `destination` parameter als een onderliggend element.

De implementatie van de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) en controleer de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Deze methode wordt gebruikt om te bevestigen van de uitvoering van een bewerking wanneer een wijziging wordt aangebracht in de systeemstatus, bijvoorbeeld: verwijderen van bestanden. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource moet worden gewijzigd voor de gebruiker met de Windows PowerShell-runtime rekening houdend met instellingen vanaf de opdrachtregel of voorkeursvariabelen in bepalen wat de gebruiker moet worden weergegeven.

Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, wordt de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode. Deze methode verzendt een bericht naar de gebruiker om toe te staan feedback in te spreken als de bewerking moet worden voortgezet. Uw provider moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) als een aanvullende controle voor wijzigingen die mogelijk schadelijke system.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Move-Item

Soms de `Move-Item` cmdlet extra parameters die dynamisch worden verstrekt tijdens runtime is vereist. Voor deze dynamische parameters, de navigatie-provider moet implementeren de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) methode voor het ophalen van de vereiste parameterwaarden van het item aan het opgegeven pad en retourneren een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.

Deze navigatie-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Een relatief pad normaliseren

Uw provider navigatie implementeert de [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) methode voor het normaliseren van het volledige pad zijn aangegeven in de `path` parameter Als het wordt ten opzichte van het pad dat is opgegeven door de `basePath` parameter. De methode wordt een tekenreeksweergave van het genormaliseerde pad. Er wordt een fout geschreven als de `path` parameter geeft u een niet-bestaande pad.

Deze methode wordt niet door de voorbeeld-navigatie-provider worden overschreven. Hier volgt de standaardimplementatie.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Om te onthouden over het implementeren van NormalizeRelativePath

De implementatie van [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) moet parseren de `path` parameter, maar dit hoeft niet te gebruiken puur syntactische parseren. U wordt aangeraden deze methode de pad gebruiken om te controleren of de padinformatie in het gegevensarchief en een pad maken die overeenkomt met het hoofdlettergebruik ontwerp en gestandaardiseerd syntaxis.

## <a name="code-sample"></a>Voorbeeld van code

Zie voor een compleet voorbeeld van code, [AccessDbProviderSample05 codevoorbeeld](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Objecttype definiëren en opmaak

Het is mogelijk voor een provider moet leden toevoegen aan bestaande objecten of nieuwe objecten worden gedefinieerd. Zie voor meer informatie,[objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Het bouwen van de Windows PowerShell-provider

Zie voor meer informatie, [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>De Windows PowerShell-provider testen

Als uw Windows PowerShell-provider is geregistreerd met Windows PowerShell, kunt u deze testen door het uitvoeren van de ondersteunde cmdlets op de opdrachtregel, inclusief cmdlets beschikbaar gesteld door afleiding. In dit voorbeeld wordt de voorbeeld-navigatie-provider testen.

1. Voer uw nieuwe shell en gebruik de `Set-Location` cmdlet om in te stellen van het pad om aan te geven van de Access-database.

   ```powershell
   Set-Location mydb:
   ```

2. Voer nu de `Get-Childitem` cmdlet voor het ophalen van een lijst van de database-items, die de beschikbare database-tabellen zijn. Dit smdlet haalt ook het aantal rijen voor elke tabel.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Gebruik de `Set-Location` cmdlet opnieuw uit om in te stellen van de locatie van de tabel met werknemers.

   ```powershell
   Set-Location Employees
   ```

4. We gaan nu gebruiken de `Get-Location` cmdlet voor het ophalen van het pad naar de tabel Employees.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Gebruik nu de `Get-Childitem` cmdlet, doorgesluisd naar de `Format-Table` cmdlet. Deze reeks cmdlets wordt de items voor de tabel met werknemers, waarmee de rijen worden opgehaald. Ze worden ingedeeld zoals opgegeven door de `Format-Table` cmdlet.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. U kunt nu uitvoeren de `Get-Item` cmdlet voor het ophalen van de items voor rij 0 van de tabel met werknemers.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Gebruik de `Get-Item` cmdlet opnieuw uit voor het ophalen van de gegevens van werknemers voor de items in de rij 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Zie ook

[Het maken van Windows PowerShell-providers](./how-to-create-a-windows-powershell-provider.md)

[Ontwerp uw Windows PowerShell-provider](./designing-your-windows-powershell-provider.md)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementeer een Container Windows PowerShell-provider](./creating-a-windows-powershell-container-provider.md)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)