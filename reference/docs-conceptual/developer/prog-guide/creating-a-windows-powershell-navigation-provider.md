---
title: Een Windows Power shell-navigatie provider maken | Microsoft Docs
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
ms.openlocfilehash: f73e732ca9416b906b3647c5090dfa04ad940484
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416192"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Een Windows PowerShell-navigatieprovider maken

In dit onderwerp wordt beschreven hoe u een Windows Power shell-navigatie provider maakt waarmee kan worden genavigeerd naar het gegevens archief. Dit type provider ondersteunt recursieve opdrachten, geneste containers en relatieve paden.

> [!NOTE]
> U kunt het C# bron bestand (AccessDBSampleProvider05.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
>
> De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.
>
> Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.

De provider die hier wordt beschreven, kan de gebruiker een Access-Data Base als een station afhandelen zodat de gebruiker naar de gegevens tabellen in de data base kan navigeren. Wanneer u uw eigen navigatie provider maakt, kunt u methoden implementeren die Stationspaden kunnen maken die geschikt zijn voor navigatie, relatieve paden normaliseren, items van het gegevens archief verplaatsen, evenals methoden die onderliggende namen ophalen, het bovenliggende pad van een item ophalen en testen om te bepalen of een item een container is.

> [!CAUTION]
> Houd er rekening mee dat in dit ontwerp wordt uitgegaan van een Data Base met een veld met de naam-ID en dat het type van het veld LongInteger is.

## <a name="define-the-windows-powershell-provider"></a>De Windows Power shell-provider definiëren

Een Windows Power shell-navigatie provider moet een .NET-klasse maken die is afgeleid van de basis klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Hier volgt de klassedefinitie voor de navigatie provider die in deze sectie wordt beschreven.

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Houd er rekening mee dat in deze provider het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) twee para meters bevat. De eerste para meter geeft u een beschrijvende naam op voor de provider die wordt gebruikt door Windows Power shell. Met de tweede para meter geeft u de specifieke Windows Power shell-mogelijkheden op die de provider beschikbaar maakt voor de Windows Power shell-runtime tijdens het verwerken van opdrachten. Voor deze provider zijn er geen specifieke Windows Power shell-functies die worden toegevoegd.

## <a name="defining-base-functionality"></a>Basis functionaliteit definiëren

Zoals beschreven in het [ontwerp van uw PS-provider](./designing-your-windows-powershell-provider.md), is de basis klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) afgeleid van verschillende andere klassen die een andere provider functionaliteit hebben gekregen. Voor een Windows Power shell-navigatie provider moet daarom alle functionaliteit worden gedefinieerd die door deze klassen wordt opgegeven.

Zie [een eenvoudige PS-provider maken](./creating-a-basic-windows-powershell-provider.md)voor informatie over het implementeren van de functionaliteit voor het toevoegen van toepassingsspecifieke initialisatie gegevens en voor het vrijgeven van resources die worden gebruikt door de provider. De meeste providers (met inbegrip van de hier beschreven provider) kunnen echter gebruikmaken van de standaard implementatie van deze functionaliteit van Windows Power shell.

Als u toegang wilt krijgen tot het gegevens archief via een Windows Power Shell-station, moet u de methoden van de basis klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) implementeren. Zie [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md)voor meer informatie over het implementeren van deze methoden.

Voor het bewerken van de items van een gegevens archief, zoals het ophalen, instellen en wissen van items, moet de provider de methoden implementeren die worden verschaft door de basis klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Zie [een Windows Power shell-item provider maken](./creating-a-windows-powershell-item-provider.md)voor meer informatie over het implementeren van deze methoden.

Als u de onderliggende items, of hun namen, van het gegevens archief wilt weer geven, evenals methoden waarmee items worden gemaakt, gekopieerd, hernoemd en verwijderd, moet u de methoden implementeren die zijn opgenomen in de basis klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Zie [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md)voor meer informatie over het implementeren van deze methoden.

## <a name="creating-a-windows-powershell-path"></a>Een Windows Power shell-pad maken

Windows Power shell-navigatie provider gebruiken een provider: intern Windows Power shell-pad om door de items van het gegevens archief te navigeren. Als u een provider-intern pad wilt maken, moet de provider de methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) implementeren om aanroepen van de cmdlet combine-pad te kunnen ondersteunen. Met deze methode wordt een bovenliggend en onderliggend pad gecombineerd in een provider-intern pad, met een providerspecifieke padscheidingsteken tussen de bovenliggende en onderliggende paden.

De standaard implementatie heeft paden met '/' of '\\' als padscheidingsteken, normaliseert het padscheidingsteken op '\\', combineert het bovenliggende en onderliggende pad met het scheidings teken ertussen en retourneert een teken reeks die de gecombineerde paden bevat.

Deze navigatie provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van de methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Wat u moet weten over implementatie van MakePath

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Uw implementatie van de methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) moet het pad niet valideren als een juridisch volledig pad in de naam ruimte van de provider. Houd er rekening mee dat elke para meter alleen een deel van een pad kan vertegenwoordigen en dat de gecombineerde onderdelen geen volledig pad genereren. De methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) voor de File System Provider kan bijvoorbeeld ' Windows\System32 ' in de para meter `parent` en ' ABC. dll ' in de para meter `child` ontvangen. De methode voegt deze waarden samen met het scheidings teken '\\' en retourneert ' windows\system32\abc.dll '. Dit is geen volledig gekwalificeerde bestandssysteempad.

  > [!IMPORTANT]
  > De pad-onderdelen die zijn opgenomen in de aanroep van [System. Management. Automation. provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) bevatten mogelijk tekens die niet zijn toegestaan in de naam ruimte van de provider. Deze tekens worden meestal gebruikt voor het uitbreiden van het Joker teken en de implementatie van deze methode mag ze niet verwijderen.

## <a name="retrieving-the-parent-path"></a>Het bovenliggende pad ophalen

Windows Power shell-navigatie providers implementeren de methode [System. Management. Automation. provider. Navigationcmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) om het bovenliggende deel van het aangegeven volledige of gedeeltelijke providerspecifieke pad op te halen. De methode verwijdert het onderliggende deel van het pad en retourneert het bovenliggende pad. Met de para meter `root` geeft u het volledige pad naar de hoofdmap van een station op. Deze para meter kan null of leeg zijn als een gekoppeld station niet in gebruik is voor de ophaal bewerking. Als er een root is opgegeven, moet de methode een pad retour neren naar een container in dezelfde boom structuur als de hoofdmap.

De voor beeld-navigatie provider overschrijft deze methode niet, maar gebruikt de standaard implementatie. Het accepteert paden die zowel '/'-als '\\' als padscheidingsteken gebruiken. Het pad wordt eerst genormaliseerd om alleen '\\' scheidings tekens te hebben, waarna het bovenliggende pad wordt gesplitst bij de laatste '\\' en het bovenliggende pad wordt geretourneerd.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Meer informatie over het implementeren van GetParentPath

Uw implementatie van de methode [System. Management. Automation. provider. Navigationcmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) moet het pad op een lexicale wijze splitsen op het padscheidingsteken voor de naam ruimte van de provider. De File System Provider gebruikt deze methode bijvoorbeeld om te zoeken naar de laatste '\\' en retourneert alles aan de linkerkant van het scheidings teken.

## <a name="retrieve-the-child-path-name"></a>De naam van het onderliggende pad ophalen

Uw navigatie provider implementeert de methode [System. Management. Automation. provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) om de naam (Leaf-element) van het onderliggende item op te halen dat zich bevindt in het opgegeven volledige of gedeeltelijke providerspecifieke pad.

De voor beeld-navigatie provider overschrijft deze methode niet. De standaard implementatie wordt hieronder weer gegeven. Het accepteert paden die zowel '/'-als '\\' als padscheidingsteken gebruiken. Eerst wordt het pad genormaliseerd om alleen "\\" scheidings tekens te hebben, waarna het bovenliggende pad wordt gesplitst bij de laatste "\\" en wordt de naam van het onderliggende padcomponent geretourneerd.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Wat u moet weten over implementatie van GetChildName

Uw implementatie van de methode [System. Management. Automation. provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) moet het pad op een lexicale wijze splitsen op het padscheidingsteken. Als het opgegeven pad geen padscheidingsteken bevat, zou de methode het pad moeten retour neren ongewijzigd.

> [!IMPORTANT]
> Het pad dat in de aanroep van deze methode is gegeven, kan tekens bevatten die ongeldig zijn in de naam ruimte van de provider. Deze tekens worden meestal gebruikt voor het vergelijken van joker tekens of reguliere expressies en de implementatie van deze methode mag deze niet verwijderen.

## <a name="determining-if-an-item-is-a-container"></a>Bepalen of een item een container is

De navigatie provider kan de methode [System. Management. Automation. provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementeren om te bepalen of het opgegeven pad een container aangeeft. Retourneert waar als het pad een container vertegenwoordigt en ONWAAR, anders false. De gebruiker heeft deze methode nodig om de `Test-Path`-cmdlet voor het opgegeven pad te kunnen gebruiken.

De volgende code toont de implementatie [System. Management. Automation. provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) in onze voor beeld-navigatie provider. De methode controleert of het opgegeven pad juist is en of de tabel bestaat en retourneert waar als het pad een container aangeeft.

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Wat u moet weten over implementatie van IsItemContainer

De .NET-klasse van uw navigatie provider declareert mogelijk provider mogelijkheden van ExpandWildcards, filter, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In dit geval moet de implementatie van [System. Management. Automation. provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) ervoor zorgen dat het opgegeven pad voldoet aan de vereisten. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschap [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) .

## <a name="moving-an-item"></a>Een item verplaatsen

Ter ondersteuning van de `Move-Item` cmdlet implementeert uw navigatie provider de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . Deze methode verplaatst het item dat is opgegeven door de para meter `path` naar de container op het pad dat is opgegeven in de para meter `destination`.

De voor beeld-navigatie provider overschrijft de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) niet. Hier volgt de standaard implementatie.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Wat u moet weten over implementatie van MoveItem

De .NET-klasse van uw navigatie provider declareert mogelijk provider mogelijkheden van ExpandWildcards, filter, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In dit geval moet de implementatie van [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) ervoor zorgen dat het opgegeven pad voldoet aan de vereisten. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschap **CmdletProvider. exclude** .

Standaard moeten onderdrukkingen van deze methode geen objecten verplaatsen over bestaande objecten tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true`. De File System Provider kopieert bijvoorbeeld geen c:\temp\abc.txt over een bestaand c:\bar.txt-bestand, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true`. Als het pad dat is opgegeven in de para meter `destination` bestaat en een container is, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist. In dit geval moet [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) het item dat door de para meter `path` wordt aangegeven, verplaatsen naar de container die wordt aangegeven door de para meter `destination` als onderliggend element.

Uw implementatie van de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen wanneer een wijziging wordt aangebracht in de systeem status, bijvoorbeeld het verwijderen van bestanden. [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime, waarbij rekening wordt gehouden met alle opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven voor de gebruiker.

Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, moet de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) worden aangeroepen de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Met deze methode wordt een bericht verzonden naar de gebruiker om feedback te geven als de bewerking moet worden voortgezet. Uw provider moet [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) aanroepen als extra controle op mogelijk schadelijke systeem wijzigingen.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Dynamische para meters aan de cmdlet Move-item koppelen

Soms vereist de `Move-Item` cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de navigatie provider de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) implementeren om de vereiste parameter waarden van het item op het aangegeven pad op te halen en een object retour neren met eigenschappen en velden met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object.

Deze navigatie provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Een relatief pad normaliseren

Uw navigatie provider implementeert de methode [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) om het volledig gekwalificeerde pad dat wordt aangegeven in de para meter `path`, te normaliseren als relatief aan het pad dat is opgegeven door de para meter `basePath`. De methode retourneert een teken reeks weergave van het gestandaardiseerde pad. Er wordt een fout bericht geschreven als de para meter `path` een niet-bestaand pad opgeeft.

De voor beeld-navigatie provider overschrijft deze methode niet. Hier volgt de standaard implementatie.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Wat u moet weten over implementatie van NormalizeRelativePath

Voor de implementatie van [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) moet de para meter `path` worden geparseerd, maar het is niet nodig om uitsluitend syntactische parsering te gebruiken. U wordt aangeraden deze methode te ontwerpen om het pad op te zoeken in de gegevens opslag en een pad te maken dat overeenkomt met het hoofdletter gebruik en de syntaxis van het gestandaardiseerde pad.

## <a name="code-sample"></a>Code voorbeeld

Zie [AccessDbProviderSample05 code sample](./accessdbprovidersample05-code-sample.md)voor een volledige voorbeeld code.

## <a name="defining-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Een provider kan leden toevoegen aan bestaande objecten of nieuwe objecten definiëren. Zie[object typen en opmaak uitbreiden](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)voor meer informatie.

## <a name="building-the-windows-powershell-provider"></a>De Windows Power shell-provider bouwen

Zie voor meer informatie [cmdlets, providers en hosttoepassingen registreren](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>De Windows Power shell-provider testen

Als uw Windows Power shell-provider is geregistreerd bij Windows Power shell, kunt u deze testen door de ondersteunde cmdlets uit te voeren op de opdracht regel, inclusief de cmdlets die beschikbaar zijn gemaakt door afleiding. In dit voor beeld wordt de voor beeld-navigatie provider getest.

1. Voer uw nieuwe shell uit en gebruik de cmdlet `Set-Location` om het pad in te stellen om de Access-data base aan te geven.

   ```powershell
   Set-Location mydb:
   ```

2. Voer nu de `Get-Childitem` cmdlet uit om een lijst op te halen van de database-items, die de beschik bare database tabellen zijn. Voor elke tabel haalt deze cmdlet ook het aantal tabel rijen op.

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

3. Gebruik de `Set-Location` cmdlet opnieuw om de locatie van de gegevens tabel werk nemers in te stellen.

   ```powershell
   Set-Location Employees
   ```

4. We gaan nu de cmdlet `Get-Location` gebruiken om het pad naar de tabel Employees op te halen.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Gebruik nu de `Get-Childitem`-cmdlet pipet naar de `Format-Table`-cmdlet. Met deze set cmdlets worden de items opgehaald voor de gegevens tabel werk nemers, die de tabel rijen zijn. Ze zijn ingedeeld zoals opgegeven door de cmdlet `Format-Table`.

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

6. U kunt nu de `Get-Item` cmdlet uitvoeren om de items voor rij 0 van de gegevens tabel werk nemers op te halen.

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

7. Gebruik de `Get-Item` cmdlet opnieuw om de werknemers gegevens voor de items in rij 0 op te halen.

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

[Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md)

[Uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)

[Object typen en-opmaak uitbreiden](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Een container Windows Power shell-provider implementeren](./creating-a-windows-powershell-container-provider.md)

[Cmdlets, providers en hosttoepassingen registreren](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
