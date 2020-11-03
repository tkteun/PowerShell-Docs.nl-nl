---
description: Hierin wordt beschreven hoe u kunt werken met opdracht parameters in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: 7cc5c071116df8d3326a4ea13802227d350bfac3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252774"
---
# <a name="about-parameters"></a>Over para meters

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u kunt werken met opdracht parameters in Power shell.

## <a name="long-description"></a>Lange beschrijving

De meeste Power shell-opdrachten, zoals cmdlets, functies en scripts, zijn afhankelijk van para meters waarmee gebruikers opties kunnen selecteren of invoer kunnen opgeven. De para meters volgen de naam van de opdracht en hebben de volgende vorm:

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

De naam van de para meter wordt voorafgegaan door een koppel teken (-), waarmee wordt gesignaleerd naar Power shell dat het woord na het afbreek streepje een parameter naam is. De naam en waarde van de para meter kunnen worden gescheiden door een spatie of een punt komma. Sommige para meters vereisen of accepteren geen parameter waarde. Andere para meters hebben een waarde nodig, maar de parameter naam is niet vereist in de opdracht.

Het type para meters en de vereisten voor die para meters kunnen verschillen. Als u informatie wilt vinden over de para meters van een opdracht, gebruikt u de `Get-Help` cmdlet. Als u bijvoorbeeld informatie zoekt over de para meters van de `Get-ChildItem` cmdlet, typt u:

```powershell
Get-Help Get-ChildItem
```

Als u informatie wilt vinden over de para meters van een script, gebruikt u het volledige pad naar het script bestand. Bijvoorbeeld:

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

De `Get-Help` cmdlet retourneert verschillende details over de opdracht, met inbegrip van een beschrijving, de syntaxis van de opdracht, informatie over de para meters en voor beelden die laten zien hoe u de para meters in een opdracht kunt gebruiken.

U kunt ook de para meter parameter van de `Get-Help` cmdlet gebruiken om informatie te zoeken over een bepaalde para meter. Of u kunt de para meter **parameter** met de waarde Joker teken ( `*` ) gebruiken om informatie te zoeken over alle para meters van de opdracht. Met de volgende opdracht wordt bijvoorbeeld informatie over alle para meters van de `Get-Member` cmdlet opgehaald:

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a>Standaard parameter waarden

Optionele para meters hebben een standaard waarde. Dit is de waarde die wordt gebruikt of wordt aangenomen wanneer de para meter niet is opgegeven in de opdracht.

De standaard waarde van de para meter **ComputerName** van veel cmdlets is bijvoorbeeld de naam van de lokale computer. Als gevolg hiervan wordt de naam van de lokale computer in de opdracht gebruikt, tenzij u de para meter **ComputerName** opgeeft.

Zie het Help-onderwerp voor de cmdlet om de standaard parameter waarde te vinden. De parameter beschrijving moet de standaard waarde bevatten.

U kunt ook een aangepaste standaard waarde instellen voor elke para meter van een cmdlet of een geavanceerde functie. Zie [about_Parameters_Default_Values](about_Parameters_Default_Values.md)voor meer informatie over het instellen van aangepaste standaard waarden.

### <a name="parameter-attribute-table"></a>Parameter kenmerk tabel

Wanneer u de para meters **Full** , **para meter** of **online** van de `Get-Help` cmdlet gebruikt, `Get-Help` wordt een tabel met parameter kenmerken weer gegeven met gedetailleerde informatie over de para meter.

Deze informatie bevat de details die u moet kennen om de para meter te gebruiken.
Het Help-onderwerp voor de `Get-ChildItem` cmdlet bevat bijvoorbeeld de volgende gegevens over de para meter Path:

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

De parameter informatie bevat de syntaxis van de para meter, een beschrijving van de para meter en de parameter kenmerken. In de volgende secties worden de parameter kenmerken beschreven.

#### <a name="parameter-required"></a>Para meter vereist

Met deze instelling geeft u aan of de para meter verplicht is, dat wil zeggen of alle opdrachten die gebruikmaken van deze cmdlet deze para meter moeten bevatten. Als de waarde **True** is en de para meter in de opdracht ontbreekt, vraagt Power shell u om een waarde voor de para meter.

#### <a name="parameter-position"></a>Parameter positie

Als de `Position` instelling is ingesteld op een positief geheel getal, is de parameter naam niet vereist. Dit type para meter wordt aangeduid als positionele para meter en het nummer geeft de positie aan waarin de para meter moet worden weer gegeven in verhouding tot andere positie parameters. Een benoemde para meter kan worden weer gegeven op elke positie na de naam van de cmdlet. Als u de parameter naam voor een positionele para meter toevoegt, kan de para meter op elke positie na de naam van de cmdlet worden weer gegeven.

De `Get-ChildItem` cmdlet heeft bijvoorbeeld Path-en exclude-para meters. De `Position` instelling voor het **pad** is **0** , wat betekent dat het een positionele para meter is. De `Position` instelling voor **uitsluiten** heet **named**.

Dit betekent dat voor het **pad** geen parameter naam is vereist, maar de parameter waarde moet de eerste of enige niet-genaamde parameter waarde in de opdracht zijn.
Omdat de exclude-para meter echter een benoemde para meter is, kunt u deze op een wille keurige positie in de opdracht plaatsen.

Als gevolg van de `Position` instellingen voor deze twee para meters, kunt u een van de volgende opdrachten gebruiken:

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

Als u een andere positionele para meter zou gebruiken zonder de parameter naam op te nemen, moet deze para meter worden geplaatst in de volg orde die is opgegeven door de `Position` instelling.

#### <a name="parameter-type"></a>Parameter type

Met deze instelling geeft u het type Microsoft .NET Framework van de parameter waarde. Als het type bijvoorbeeld **Int32** is, moet de waarde van de para meter een geheel getal zijn. Als het type een teken reeks is, moet de waarde van de para meter een teken reeks zijn. Als de teken reeks spaties bevat, moet de waarde tussen aanhalings tekens worden geplaatst of moeten de spaties worden voorafgegaan door het escape teken (').

#### <a name="default-value"></a>Standaardwaarde

Met deze instelling geeft u de waarde op die door de para meter wordt aangenomen als er geen andere waarde is opgegeven. Zo is de standaard waarde van de para meter Path vaak de huidige map. De vereiste para meters hebben nooit een standaard waarde.
Voor veel optionele para meters is er geen standaard waarde omdat de para meter geen effect heeft als deze niet wordt gebruikt.

#### <a name="accepts-multiple-values"></a>Accepteert meerdere waarden

Met deze instelling geeft u aan of een para meter meerdere parameter waarden accepteert.
Als een para meter meerdere waarden accepteert, kunt u een door komma's gescheiden lijst als waarde van de para meter in de opdracht typen of een door komma's gescheiden lijst (een matrix) in een variabele opslaan en vervolgens de variabele als parameter waarde opgeven.

De para meter ServiceName van de `Get-Service` cmdlet accepteert bijvoorbeeld meerdere waarden. De volgende opdrachten zijn beide geldig:

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a>Invoer van pijp lijn accepteren

Met deze instelling geeft u aan of u de pijplijn operator ( `|` ) kunt gebruiken om een waarde te verzenden naar de para meter.

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

Als een para meter ' True (per waarde) ' is, probeert Power shell alle sluis waarden met die para meter te koppelen voordat andere methoden proberen de opdracht te interpreteren.

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

U kunt bijvoorbeeld een waarde alleen door sluizen naar een **naam** parameter wanneer de waarde een eigenschap genaamd **name** heeft.

> [!NOTE]
> Een getypeerde para meter die pijplijn invoer ( `by Value` ) of () accepteert, `by PropertyName` maakt het gebruik van script blokken met **vertragings bindingen** mogelijk voor de para meter.
>
> Het script blok voor de **vertragings binding** wordt automatisch uitgevoerd tijdens **ParameterBinding**. Het resultaat is gebonden aan de para meter. De vertraagde binding werkt **niet** voor para meters die zijn gedefinieerd als type `ScriptBlock` of `System.Object` , het script blok wordt door gegeven **zonder** dat dit wordt aangeroepen.
>
> U kunt hier meer lezen over de script blokken **met vertragings bindingen** [about_Script_Blocks. MD](about_Script_Blocks.md)

#### <a name="accepts-wildcard-characters"></a>Joker tekens accepteren

Deze instelling geeft aan of de waarde van de para meter joker tekens kan bevatten zodat de parameter waarde kan worden gekoppeld aan meer dan één bestaand item in de doel container.

#### <a name="common-parameters"></a>Algemene para meters

Algemene para meters zijn para meters die u met een wille keurige cmdlet kunt gebruiken. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over algemene para meters.

## <a name="see-also"></a>Zie ook

[about_Command_syntax](about_Command_syntax.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Parameters_Default_Values](about_Parameters_Default_Values.md)

[about_Pipelines](about_Pipelines.md)

[about_Wildcards](about_Wildcards.md)
