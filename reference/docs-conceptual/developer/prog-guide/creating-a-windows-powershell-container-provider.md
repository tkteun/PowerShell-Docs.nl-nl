---
title: Een Windows Power shell-container provider maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 69e45de4220a234783d35a877116ad5a5e47d182
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870775"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Een Windows PowerShell-containerprovider maken

In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt die kan worden gebruikt voor gegevens opslag met meerdere lagen. Voor dit type gegevens archief bevat het hoogste niveau van de Store de hoofd items en elk volgend niveau wordt een knoop punt van onderliggende items genoemd. Door de gebruiker toe te staan om deze onderliggende knoop punten te gebruiken, kan een gebruiker hiërarchisch communiceren via het gegevens archief.

Providers die kunnen werken op gegevens archieven met meerdere niveaus worden aangeduid als Windows Power shell-container providers. Houd er echter rekening mee dat een Windows Power shell-container provider alleen kan worden gebruikt als er één container (geen geneste containers) met items bevat. Als er geneste containers zijn, moet u een Windows Power shell-navigatie provider implementeren. Zie [een Windows Power shell-navigatie provider maken](./creating-a-windows-powershell-navigation-provider.md)voor meer informatie over het implementeren van een Windows Power shell-navigatie provider.

> [!NOTE]
> U kunt het C# bron bestand (AccessDBSampleProvider04.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map. Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.

De Windows Power shell-container provider die hier wordt beschreven, definieert de Data Base als één container, waarbij de tabellen en rijen van de Data Base zijn gedefinieerd als items van de container.

> [!CAUTION]
> Houd er rekening mee dat in dit ontwerp wordt uitgegaan van een Data Base met een veld met de naam-ID en dat het type van het veld LongInteger is.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Een Windows Power shell-container provider klasse definiëren

Een Windows Power shell-container provider moet een .NET-klasse definiëren die is afgeleid van de basis klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Hier volgt de klassedefinitie voor de Windows Power shell-container provider die in deze sectie wordt beschreven.

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Merk op dat in deze klassedefinitie, het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) twee para meters bevat. De eerste para meter geeft u een beschrijvende naam op voor de provider die wordt gebruikt door Windows Power shell. Met de tweede para meter geeft u de specifieke Windows Power shell-mogelijkheden op die de provider beschikbaar maakt voor de Windows Power shell-runtime tijdens het verwerken van opdrachten. Voor deze provider zijn er geen specifieke Windows Power shell-functies die worden toegevoegd.

## <a name="defining-base-functionality"></a>Basis functionaliteit definiëren

Zoals beschreven in het [ontwerpen van uw Windows Power shell-provider](./designing-your-windows-powershell-provider.md), is de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) afgeleid van verschillende andere klassen die een andere provider functionaliteit hebben verschaft. Voor een Windows Power shell-container provider moet daarom alle functionaliteit worden gedefinieerd die door deze klassen wordt opgegeven.

Zie [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md)voor informatie over het implementeren van de functionaliteit voor het toevoegen van toepassingsspecifieke initialisatie gegevens en voor het vrijgeven van resources die worden gebruikt door de provider.
De meeste providers (met inbegrip van de hier beschreven provider) kunnen echter gebruikmaken van de standaard implementatie van deze functionaliteit die wordt verschaft door Windows Power shell.

Om toegang te krijgen tot het gegevens archief, moet de provider de methoden van de basis klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) implementeren. Zie [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md)voor meer informatie over het implementeren van deze methoden.

Voor het bewerken van de items van een gegevens archief, zoals het ophalen, instellen en wissen van items, moet de provider de methoden implementeren die worden verschaft door de basis klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Zie [een Windows Power shell-item provider maken](./creating-a-windows-powershell-item-provider.md)voor meer informatie over het implementeren van deze methoden.

## <a name="retrieving-child-items"></a>Onderliggende items ophalen

Als u een onderliggend item wilt ophalen, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) overschrijven om aanroepen van de `Get-ChildItem`-cmdlet te ondersteunen. Deze methode haalt onderliggende items van het gegevens archief op en schrijft deze naar de pijp lijn als objecten. Als de para meter `recurse` van de cmdlet is opgegeven, haalt de methode alle onderliggende elementen op, ongeacht op welk niveau ze zich bevinden. Als de para meter `recurse` niet is opgegeven, haalt de methode slechts één niveau van onderliggende items op.

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) voor deze provider. U ziet dat met deze methode de onderliggende items in alle database tabellen worden opgehaald wanneer het pad de Access-Data Base aangeeft, en worden de onderliggende items opgehaald uit de rijen van de tabel als het pad een gegevens tabel aangeeft.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Wat u moet weten over implementatie van GetChildItems

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Voor de implementatie van deze methode moet rekening worden gehouden met elke vorm van toegang tot het item die het item mogelijk zichtbaar maakt voor de gebruiker. Bijvoorbeeld, als een gebruiker schrijf toegang heeft tot een bestand via de bestandssysteem provider (geleverd door Windows Power shell), maar geen lees toegang, het bestand nog bestaat en [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retourneert `true`. Voor uw implementatie moet mogelijk een bovenliggend item worden gecontroleerd om te zien of de onderliggende items kunnen worden geïnventariseerd.

- Bij het schrijven van meerdere items kan de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) enige tijd duren. U kunt uw provider zo ontwerpen dat de items met de methode [System. Management. Automation. provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) per keer worden geschreven. Met deze techniek worden de items aan de gebruiker in een stroom gepresenteerd.

- Uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) is verantwoordelijk voor het voor komen van oneindige recursie wanneer er circulaire koppelingen zijn en het soort gelijke. Er moet een geschikte afsluit uitzondering worden gegenereerd om een dergelijke voor waarde weer te geven.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Dynamische para meters aan de cmdlet Get-Child item koppelen

Soms moet de cmdlet `Get-ChildItem` die [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) aanroept, extra para meters zijn die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) implementeren. Met deze methode worden dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Get-ChildItem`-cmdlet.

Deze methode wordt niet door deze Windows Power shell-container provider geïmplementeerd. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Onderliggend item namen ophalen

Als u de namen van onderliggende items wilt ophalen, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) overschrijven om aanroepen van de `Get-ChildItem` cmdlet te ondersteunen wanneer de `Name`-para meter is opgegeven. Met deze methode worden de namen van de onderliggende items voor het opgegeven pad of onderliggende item namen voor alle containers opgehaald als de para meter `returnAllContainers` van de cmdlet is opgegeven. Een onderliggende naam is het Leaf-gedeelte van een pad. De onderliggende naam voor het pad c:\windows\system32\abc.dll is bijvoorbeeld ABC. dll. De onderliggende naam voor de map c:\Windows\System32 is ' system32 '.

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) voor deze provider. U ziet dat met de methode tabel namen worden opgehaald als in het opgegeven pad de Access-Data Base (station) en de rijnummers worden aangegeven als het pad een tabel aangeeft.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Wat u moet weten over implementatie van GetChildNames

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

  > [!NOTE]
  > Een uitzonde ring op deze regel treedt op wanneer de para meter `returnAllContainers` van de cmdlet is opgegeven. In dit geval moet de methode een onderliggende naam voor een container ophalen, zelfs als deze niet overeenkomt met de waarden van [System. Management. Automation. provider. Cmdletprovider. filter *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), System. Management. Automation. provider. [Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), of [System. beheer. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) eigenschappen.

- Standaard moeten onderdrukkingen van deze methode geen namen ophalen van objecten die doorgaans verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is opgegeven. Als het opgegeven pad een container aangeeft, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist.

- Uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) is verantwoordelijk voor het voor komen van oneindige recursie wanneer er circulaire koppelingen zijn en het soort gelijke. Er moet een geschikte afsluit uitzondering worden gegenereerd om een dergelijke voor waarde weer te geven.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Dynamische para meters aan de Get-Child item-cmdlet (naam) koppelen

Soms vereist de cmdlet `Get-ChildItem` (met de para meter `Name`) extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) implementeren. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Get-ChildItem`-cmdlet.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Naam van items wijzigen

Als u de naam van een item wilt wijzigen, moet een Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) overschrijven om aanroepen van de `Rename-Item`-cmdlet te ondersteunen. Met deze methode wordt de naam van het item op het opgegeven pad gewijzigd in de nieuwe naam die wordt opgegeven. De nieuwe naam moet altijd relatief zijn ten opzichte van het bovenliggende item (container).

Deze provider overschrijft de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) niet. Het volgende is echter de standaard implementatie.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Wat u moet weten over implementatie van RenameItem

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) is bedoeld voor het wijzigen van de naam van een item en niet voor move-bewerkingen.
  In uw implementatie van de methode moet een fout worden geschreven als de para meter `newName` paden bevat, of als de bovenliggende locatie van het item anders kan worden gewijzigd.

- Standaard moeten onderdrukkingen van deze methode de naam van objecten alleen wijzigen als de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is opgegeven. Als het opgegeven pad een container aangeeft, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist.

- Uw implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen wanneer een wijziging wordt aangebracht in de systeem status, bijvoorbeeld het wijzigen van de naam van bestanden.
  [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime, waarbij rekening wordt gehouden met alle opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven.

  Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, moet de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) worden aangeroepen de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Met deze methode wordt een bericht met een bevestigings bericht verzonden naar de gebruiker om extra feedback te geven om te zeggen dat de bewerking moet worden voortgezet. Een provider moet [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) aanroepen als extra controle op mogelijk schadelijke systeem wijzigingen.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Dynamische para meters aan de cmdlet Rename-item koppelen

Soms vereist de `Rename-Item` cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet u de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) implementeren. Met deze methode worden de para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Rename-Item`-cmdlet.

Deze methode wordt niet door deze container provider geïmplementeerd. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Nieuwe items maken

Als u nieuwe items wilt maken, moet een container provider de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) implementeren ter ondersteuning van aanroepen van de `New-Item`-cmdlet. Met deze methode maakt u een gegevens item dat zich op het opgegeven pad bevindt. De para meter `type` van de cmdlet bevat het type dat door de provider is gedefinieerd voor het nieuwe item. De File System Provider gebruikt bijvoorbeeld een `type` para meter met de waarde "file" of "directory". Met de para meter `newItemValue` van de cmdlet wordt een providerspecifieke waarde voor het nieuwe item opgegeven.

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) voor deze provider.

```csharp
protected override void NewItem( string path, string type, object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Wat u moet weten over implementatie van NewItem mag

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- De methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) moet een niet-hoofdletter gevoelige vergelijking uitvoeren van de teken reeks die wordt door gegeven in de para meter `type`.
  Het moet ook ten minste ambigue overeenkomsten toestaan. Voor de typen ' bestand ' en ' Directory ' is alleen de eerste letter vereist voor dubbel zinnigheid. Als de para meter `type` een type aangeeft dat uw provider niet kan maken, moet de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) een ArgumentException schrijven met een bericht dat aangeeft welke typen de provider kan maken.

- Voor de para meter `newItemValue` wordt de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) aanbevolen om teken reeksen ten minste te accepteren. Ook moet het type object dat wordt opgehaald door de methode [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) worden geaccepteerd voor hetzelfde pad. De methode System. [Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) kan de methode [System. Management. Automation. Languageprimitives. ConvertTo *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) gebruiken om typen te converteren naar het gewenste type.

- Uw implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) is ingesteld op True, moet de [methode System](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) [. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) worden aangeroepen als extra controle op mogelijke schadelijke systeem wijzigingen.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Dynamische para meters aan de cmdlet New-item koppelen

Soms vereist de `New-Item` cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) implementeren. Met deze methode worden de para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `New-Item`-cmdlet.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Items verwijderen

Als u items wilt verwijderen, moet de Windows Power shell-provider de methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) overschrijven om aanroepen van de `Remove-Item`-cmdlet te ondersteunen. Met deze methode wordt een item uit het gegevens archief op het opgegeven pad verwijderd. Als de para meter `recurse` van de cmdlet `Remove-Item` is ingesteld op `true`, worden alle onderliggende items door de methode verwijderd, ongeacht hun niveau. Als de para meter is ingesteld op `false`, verwijdert de methode slechts één item op het opgegeven pad.

Deze provider biedt geen ondersteuning voor het verwijderen van items. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Wat u moet weten over het implementeren van RemoveItem

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen objecten verwijderen, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op True. Als het opgegeven pad een container aangeeft, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist.

- Uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) is verantwoordelijk voor het voor komen van oneindige recursie wanneer er circulaire koppelingen zijn en het soort gelijke. Er moet een geschikte afsluit uitzondering worden gegenereerd om een dergelijke voor waarde weer te geven.

- Uw implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Na het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, de methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) moet de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) aanroepen als een extra controle op mogelijk schadelijke systeem wijzigingen.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Dynamische para meters aan de Remove-item-cmdlet koppelen

Soms vereist de `Remove-Item` cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) implementeren om deze para meters af te handelen. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Remove-Item`-cmdlet.

Deze methode wordt niet door deze container provider geïmplementeerd. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Query's uitvoeren op onderliggende items

Als u wilt controleren of onderliggende items bestaan op het opgegeven pad, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) overschrijven. Deze methode retourneert `true` als het item onderliggende items heeft en `false` anderszins. Voor een null-of lege pad, de methode beschouwt alle items in het gegevens archief als onderliggend item en retourneert `true`.

Dit is de onderdrukking voor de methode [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Als er meer dan twee padcomponenten zijn gemaakt door de ChunkPath-helper-methode, retourneert de methode `false`, omdat er alleen een database container en een tabel container zijn gedefinieerd. Zie voor meer informatie over deze Help-methode de methode ChunkPath wordt besproken in [een Windows Power shell-item provider maken](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Wat u moet weten over implementatie van HasChildItems

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Als de container provider een hoofdmap aanbiedt die interessante koppel punten bevat, moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) `true` retour neren wanneer er een null-waarde of een lege teken reeks wordt door gegeven voor het pad.

## <a name="copying-items"></a>Items kopiëren

Voor het kopiëren van items moet de container provider [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -methode implementeren ter ondersteuning van aanroepen van de `Copy-Item`-cmdlet. Met deze methode wordt een gegevens item gekopieerd van de locatie die wordt aangegeven door de para meter `path` van de cmdlet naar de locatie die wordt aangegeven door de para meter `copyPath`. Als de para meter `recurse` is opgegeven, kopieert de methode alle subcontainers. Als de para meter niet is opgegeven, wordt slechts één niveau van items gekopieerd met de methode.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Wat u moet weten over implementatie van CopyItem

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen objecten kopiëren over bestaande objecten tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true`. De File System Provider kopieert bijvoorbeeld geen c:\temp\abc.txt over een bestaand c:\Abc.txt-bestand, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true`. Als het pad dat is opgegeven in de para meter `copyPath` bestaat en een container aangeeft, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist. In dit geval moet [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) het item kopiëren dat wordt aangegeven door de para meter `path` naar de container die wordt aangegeven door de para meter `copyPath` als onderliggend element.

- Uw implementatie van [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) is verantwoordelijk voor het voor komen van oneindige recursie wanneer er circulaire koppelingen zijn en het soort gelijke. Er moet een geschikte afsluit uitzondering worden gegenereerd om een dergelijke voor waarde weer te geven.

- Uw implementatie van de methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) is ingesteld op True, moet de methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) aanroepen als een extra controle op mogelijk schadelijke systeem wijzigingen. Zie [items van een andere naam wijzigen](#renaming-items)voor meer informatie over het aanroepen van deze methoden.

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Dynamische para meters aan de copy-item-cmdlet koppelen

Soms vereist de `Copy-Item` cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) implementeren om deze para meters af te handelen. Met deze methode worden de para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Copy-Item`-cmdlet.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Code voorbeeld

Zie [AccessDbProviderSample04 code sample](./accessdbprovidersample04-code-sample.md)voor een volledige voorbeeld code.

## <a name="building-the-windows-powershell-provider"></a>De Windows Power shell-provider bouwen

Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>De Windows Power shell-provider testen

Wanneer uw Windows Power shell-provider is geregistreerd bij Windows Power shell, kunt u deze testen door de ondersteunde cmdlets uit te voeren op de opdracht regel. Houd er rekening mee dat de volgende voorbeeld uitvoer een fictieve Access-data base gebruikt.

1. Voer de cmdlet `Get-ChildItem` uit om de lijst met onderliggende items uit een tabel klanten in de Access-Data Base op te halen.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   De volgende uitvoer wordt weer gegeven.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Voer de `Get-ChildItem` cmdlet opnieuw uit om de gegevens van een tabel op te halen.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   De volgende uitvoer wordt weer gegeven.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Gebruik nu de cmdlet `Get-Item` om de items op rij 0 in de gegevens tabel op te halen.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   De volgende uitvoer wordt weer gegeven.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. `Get-Item` opnieuw gebruiken om de gegevens voor de items in rij 0 op te halen.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   De volgende uitvoer wordt weer gegeven.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Gebruik nu de `New-Item` cmdlet om een rij toe te voegen aan een bestaande tabel. Met de para meter `Path` geeft u het volledige pad naar de rij op en moet u een rijnummer opgeven dat groter is dan het bestaande aantal rijen in de tabel. De para meter `Type` geeft aan dat het type item dat moet worden toegevoegd moet worden opgegeven.
   Ten slotte specificeert de para meter `Value` een door komma's gescheiden lijst met kolom waarden voor de rij.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Controleer als volgt of de bewerking voor het nieuwe item juist is.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   De volgende uitvoer wordt weer gegeven.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Zie ook

[Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md)

[Uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)

[Een Windows Power shell-provider voor het implementeren van een item](./creating-a-windows-powershell-item-provider.md)

[Een Windows Power shell-provider voor navigatie implementeren](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))

[Windows Power shell SDK](../windows-powershell-reference.md)

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)
