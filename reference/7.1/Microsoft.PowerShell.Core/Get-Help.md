---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 1a4a3f7050c3da2a73ae0d5319938117284076b7
ms.sourcegitcommit: 05f578d3fca0d9663bb1e4f76e2f14604f5303ae
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/04/2020
ms.locfileid: "93251895"
---
# Get-Help

## SAMENVATTING
Geeft informatie weer over Power shell-opdrachten en-concepten.

## SYNTAXIS

### AllUsersView (standaard)

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### DetailedView

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### Voorbeelden

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### Parameters

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### Online

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### ShowWindow

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Help` cmdlet geeft informatie weer over Power shell-concepten en-opdrachten, waaronder cmdlets, functies, Common Information Model (CIM)-opdrachten, werk stromen, providers, aliassen en scripts.

Voor hulp bij een Power shell-cmdlet typt u `Get-Help` gevolgd door de naam van de cmdlet, zoals: `Get-Help Get-Process` .

Conceptuele Help-artikelen in Power shell beginnen met **about_** , zoals **about_Comparison_Operators**. Als u alle **about_** -artikelen wilt weer geven, typt u `Get-Help about_*` . Als u een bepaald artikel wilt bekijken, typt u bijvoorbeeld `Get-Help about_<article-name>` `Get-Help about_Comparison_Operators` .

Als u hulp wilt krijgen voor een Power shell-provider, typt u `Get-Help` gevolgd door de naam van de provider. Als u bijvoorbeeld hulp wilt krijgen voor de certificaat provider, typt u `Get-Help Certificate` .

U kunt ook typen `help` of `man` , waarin één scherm met tekst wordt weer gegeven. Of, `<cmdlet-name> -?` is gelijk aan `Get-Help` , maar werkt alleen voor cmdlets.

`Get-Help` Hiermee wordt de Help-inhoud opgehaald die wordt weer gegeven van Help-bestanden op uw computer. Zonder de Help-bestanden `Get-Help` wordt alleen basis informatie over cmdlets weer gegeven. Sommige Power shell-modules bevatten Help-bestanden. Vanaf Power Shell 3,0 zijn de modules die deel uitmaakt van het Windows-besturings systeem geen Help-bestanden. Als u de Help-bestanden voor een module in Power Shell 3,0 wilt downloaden of bijwerken, gebruikt u de `Update-Help` cmdlet.

U kunt de Power shell Help-documenten ook online bekijken in het Microsoft Docs. Als u de online versie van een Help-bestand wilt ophalen, gebruikt u de para meter **online** , zoals: `Get-Help Get-Process -Online` . Raadpleeg de Microsoft Docs [Power shell-documentatie](/powershell)voor meer informatie over de Power shell-documentatie.

Als u typt `Get-Help` gevolgd door de exacte naam van een Help-artikel of een woord dat uniek is voor een Help-artikel, `Get-Help` wordt de inhoud van het artikel weer gegeven. Als u de exacte naam van een opdracht alias opgeeft, `Get-Help` wordt de Help voor de oorspronkelijke opdracht weer gegeven. Als u een woord-of woord patroon opgeeft dat wordt weer gegeven in verschillende Help-artikel titels, `Get-Help` wordt een lijst met de overeenkomende titels weer gegeven. Als u tekst opgeeft die niet wordt weer gegeven in de titels van Help-artikelen, `Get-Help` wordt een lijst met artikelen weer gegeven die de tekst in de inhoud bevat.

`Get-Help` kan Help-artikelen voor alle ondersteunde talen en land instellingen ophalen. `Get-Help` eerst zoekt u naar Help-bestanden in de land instelling die voor Windows is ingesteld, vervolgens in de bovenliggende land instelling, bijvoorbeeld **PT** voor **pt-br** , en vervolgens in een terugval land instelling. Als er vanaf Power Shell 3,0 `Get-Help` geen hulp wordt gevonden in de terugval land instelling, zoekt het naar Help-artikelen in het Engels, **en-US** voordat een fout bericht wordt geretourneerd of automatisch gegenereerde Help wordt weer gegeven.

Zie about_Command_Syntax voor meer informatie over de symbolen die `Get-Help` worden weer gegeven in het [about_Command_Syntax](./About/about_Command_Syntax.md)opdracht syntaxis diagram.
Zie [about_Parameters](./About/about_Parameters.md)voor meer informatie over parameter kenmerken, zoals **vereist** en **positie**.

>[!NOTE]
> In Power Shell 3,0 en Power Shell 4,0 `Get-Help` kunt **About** u geen artikelen in modules vinden, tenzij de module in de huidige sessie is geïmporteerd. Dit is een bekend probleem. Als u wilt **weten over** artikelen in een module, importeert u de module, hetzij met behulp van de cmdlet, hetzij `Import-Module` door een cmdlet uit te voeren die is opgenomen in de module.

## VOORBEELDEN

### Voor beeld 1: Basic Help-informatie over een cmdlet weer geven

In deze voor beelden worden algemene Help-informatie over de cmdlet weer gegeven `Format-Table` .

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

`Get-Help <cmdlet-name>` is de eenvoudigste en standaard syntaxis van de `Get-Help` cmdlet. U kunt de para meter **name** weglaten.

De syntaxis `<cmdlet-name> -?` werkt alleen voor cmdlets.

### Voor beeld 2: basis informatie één pagina tegelijk weer geven

In deze voor beelden worden algemene Help-informatie over de `Format-Table` cmdlet per pagina weer gegeven.

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

`help` is een functie die `Get-Help` de cmdlet intern uitvoert en het resultaat één pagina per keer weergeeft.

`man` is een alias voor de `help` functie.

`Get-Help Format-Table` Hiermee wordt het object omlaag verzonden via de pijp lijn. `Out-Host -Paging` Hiermee wordt de uitvoer van de pijp lijn ontvangen en één pagina tegelijk weer gegeven. Zie [out-host](Out-Host.md)(Engelstalig) voor meer informatie.

### Voor beeld 3: meer informatie voor een cmdlet weer geven

In deze voor beelden wordt gedetailleerdere Help-informatie over de cmdlet weer gegeven `Format-Table` .

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

De **gedetailleerde** weer gave van het Help-artikel bevat para meters en voor beelden.

Met de **volledige** para meter wordt de volledige weer gave van het Help-artikel weer gegeven, inclusief parameter beschrijvingen, voor beelden, invoer-en uitvoer object typen en aanvullende notities.

De **gedetailleerde** en **volledige** para meters zijn alleen effectief voor de opdrachten met Help-bestanden die op de computer zijn geïnstalleerd. De para meters zijn niet effectief voor de conceptuele ( **about_** ) Help-artikelen.

### Voor beeld 4: geselecteerde onderdelen van een cmdlet weer geven met behulp van para meters

In deze voor beelden worden geselecteerde delen van de Help van de cmdlet weer gegeven `Format-Table` .

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

De **voor beelden** -para meters bevatten de secties **naam** en samen **vatting** van het Help-bestand en alle voor beelden. U kunt geen voorbeeld nummer opgeven, omdat de para meter **voor beelden** een switch parameter is.

Met de **parameter** parameter worden alleen de beschrijvingen van de opgegeven para meters weer gegeven. Als u alleen het sterretje ( `*` )-Joker teken opgeeft, worden de beschrijvingen van alle para meters weer gegeven.
Als de **para meter** een parameter naam opgeeft, zoals **GroupBy** , wordt informatie over die para meter weer gegeven.

Deze para meters zijn niet effectief voor de conceptuele ( **about_** ) Help-artikelen.

### Voor beeld 5: online versie van Help weer geven

In dit voor beeld wordt de online versie van het Help-artikel voor de `Format-Table` cmdlet in de standaard webbrowser weer gegeven.

```powershell
Get-Help Format-Table -Online
```

### Voor beeld 6: Help over het Help-systeem weer geven

De `Get-Help` cmdlet zonder para meters geeft informatie weer over het Help-systeem van Power shell.

```powershell
Get-Help
```

### Voor beeld 7: beschik bare Help-artikelen weer geven

In dit voor beeld wordt een lijst weer gegeven met alle Help-artikelen die op uw computer beschikbaar zijn.

```powershell
Get-Help *
```

### Voor beeld 8: een lijst met conceptuele artikelen weer geven

In dit voor beeld wordt een lijst weer gegeven met de conceptuele artikelen die in de Help van Power shell zijn opgenomen. Al deze artikelen beginnen met de tekens **about_**. Typ bijvoorbeeld om een bepaald Help-bestand weer te geven `Get-Help \<about_article-name\>` `Get-Help about_Signing` .

Alleen de conceptuele artikelen met Help-bestanden die op uw computer zijn geïnstalleerd, worden weer gegeven. Zie [Update-Help](Update-Help.md)voor informatie over het downloaden en installeren van Help-bestanden in power Shell 3,0.

```powershell
Get-Help about_*
```

### Voor beeld 9: zoeken naar een woord in cmdlet Help

In dit voor beeld ziet u hoe u naar een woord zoekt in een Help-artikel over cmdlets.

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

`Get-Help` gebruikt de **volledige** para meter voor het verkrijgen van Help-informatie voor `Add-Member` . Het **MamlCommandHelpInfo** -object wordt verzonden naar de pijp lijn. `Out-String` maakt gebruik van de para meter **Stream** om het object te converteren naar een teken reeks. `Select-String` maakt gebruik van de **patroon** parameter om te zoeken naar de teken reeks voor **Clixml**.

### Voor beeld 10: een lijst met artikelen weer geven die een woord bevatten

In dit voor beeld wordt een lijst weer gegeven met artikelen die het woord **externe toegang** bevatten.

Wanneer u een woord invoert dat niet wordt weer gegeven in een artikel titel, `Get-Help` wordt een lijst met artikelen weer gegeven waarin dat woord is opgenomen.

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### Voor beeld 11: specifieke Help voor de provider weer geven

In dit voor beeld ziet u twee manieren om de provider-specifieke Help voor te verkrijgen `Get-Item` . Met deze opdrachten krijgt u informatie over het gebruik van de `Get-Item` cmdlet in het **DataCollection** -knoop punt van de power shell-SQL server provider.

In het eerste voor beeld wordt de `Get-Help` para meter **Path** gebruikt om het pad van de SQL server provider op te geven.
Omdat het pad van de provider is opgegeven, kunt u de opdracht vanaf een wille keurige pad-locatie uitvoeren.

In het tweede voor beeld wordt gebruikgemaakt `Set-Location` van om naar het pad van de SQL server provider te navigeren. Vanaf die locatie is de para meter **Path** niet nodig `Get-Help` om de provider-specifieke hulp te verkrijgen.

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### Voor beeld 12: Help voor een script weer geven

In dit voor beeld wordt Help voor de `MyScript.ps1 script` . Zie [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)voor meer informatie over het schrijven van Help voor uw functies en scripts.

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## PARAMETERS

### -Categorie

Geeft alleen Help-informatie weer voor items in de opgegeven categorie en de bijbehorende aliassen. Conceptuele artikelen vindt u in de categorie **Help file** .

De acceptabele waarden voor deze para meter zijn als volgt:

- Alias
- Cmdlet
- Provider
- Algemeen
- Veelgestelde vragen
- Woordenlijst
- File
- ScriptCommand
- Functie
- Filteren
- ExternalScript
- Alles
- DefaultHelp
- Werkstroom
- Dscresource bieden
- Klasse
- Configuration

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Onderdeel

Geeft opdrachten weer met de opgegeven onderdeel waarde, zoals **Exchange**. Voer een onderdeel naam in.
Joker tekens zijn toegestaan. Deze para meter heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Gedetailleerd

Hiermee worden parameter beschrijvingen en voor beelden toegevoegd aan de Basic Help-weer gave. Deze para meter is alleen effectief als de Help-bestanden op de computer zijn geïnstalleerd. Dit heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Voor beelden

Alleen de naam, de samen vatting en de voor beelden worden weer gegeven. Als u alleen de voor beelden wilt weer geven, typt u `(Get-Help \<cmdlet-name\>).Examples` .

Deze para meter is alleen effectief als de Help-bestanden op de computer zijn geïnstalleerd. Dit heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Volledig

Hiermee wordt het volledige Help-artikel voor een cmdlet weer gegeven. **Volledige** bevat parameter beschrijvingen en kenmerken, voor beelden, invoer-en uitvoer object typen en aanvullende notities.

Deze para meter is alleen effectief als de Help-bestanden op de computer zijn geïnstalleerd. Dit heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Functionaliteit

Geeft Help weer voor items met de opgegeven functionaliteit. Voer de functionaliteit in. Joker tekens zijn toegestaan. Deze para meter heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Hiermee krijgt u hulp bij de opgegeven opdracht of het concept. Voer de naam in van een cmdlet, functie, provider, script of werk stroom, zoals `Get-Member` een conceptuele artikel naam, zoals `about_Objects` of een alias, zoals `ls` . Joker tekens zijn toegestaan in de namen van cmdlets en providers, maar u kunt geen joker tekens gebruiken om de namen te vinden van de Help-en Help-artikelen over functies.

Als u hulp nodig hebt voor een script dat zich niet in een pad bevindt dat wordt vermeld in de `$env:Path` omgevings variabele, typt u het pad en de bestands naam van het script.

Als u de exacte naam van een Help-artikel opgeeft, `Get-Help` wordt de inhoud van het artikel weer gegeven.

Als u een woord-of woord patroon opgeeft dat wordt weer gegeven in verschillende Help-artikel titels, `Get-Help` wordt een lijst met de overeenkomende titels weer gegeven.

Als u tekst invoert die niet overeenkomt met de titels van Help-artikelen, `Get-Help` wordt een lijst met artikelen weer gegeven die de tekst in de inhoud bevat.

De namen van conceptuele artikelen, zoals `about_Objects` , moeten worden ingevoerd in het Engels, zelfs in niet-Engelse versies van Power shell.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Online

Hiermee wordt de online versie van een Help-artikel in de standaard browser weer gegeven. Deze para meter is alleen geldig voor de Help-artikelen voor cmdlets, functies, werk stromen en scripts. U kunt de **online** para meter niet gebruiken `Get-Help` in een externe sessie.

Voor informatie over het ondersteunen van deze functie in Help-artikelen die u schrijft, raadpleegt u [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)en [ondersteunende online Help](/powershell/scripting/developer/module/supporting-online-help)en schrijft u de [Help voor Power shell-cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Para meter

Geeft alleen de gedetailleerde beschrijvingen van de opgegeven para meters weer. Joker tekens zijn toegestaan. Deze para meter heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Hiermee wordt informatie opgehaald over de werking van de cmdlet in het opgegeven pad van de provider. Voer een pad voor de Power shell-provider in.

Met deze para meter wordt een aangepaste versie van een Help-artikel van de cmdlet opgehaald waarin wordt uitgelegd hoe de cmdlet werkt in het opgegeven pad van de Power shell-provider. Deze para meter is alleen effectief voor Help over een provider-cmdlet en alleen wanneer de provider een aangepaste versie van het Help-artikel van de provider-cmdlet in het Help-bestand bevat. Als u deze para meter wilt gebruiken, installeert u het Help-bestand voor de module die de provider bevat.

Als u de Help voor aangepaste cmdlets voor een pad naar een provider wilt bekijken, gaat u naar de locatie van het provider pad en voert u een `Get-Help` opdracht in, of u kunt vanuit elke locatie de para meter **Path** van `Get-Help` opgeven om het pad naar de provider op te geven. U kunt ook een aangepaste cmdlet Help online vinden in de Help-sectie van de provider van de Help-artikelen.

Zie [about_Providers](./About/about_Providers.md)voor meer informatie over Power shell-providers.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Rol

Geeft Help aangepast voor de opgegeven gebruikersrol. Voer een rol in. Joker tekens zijn toegestaan.

Voer de rol in die de gebruiker in een organisatie speelt. Sommige cmdlets geven verschillende tekst in hun Help-bestanden weer op basis van de waarde van deze para meter. Deze para meter heeft geen effect op de Help voor de kern-cmdlets.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowWindow

Hiermee wordt het Help-onderwerp in een venster weer gegeven om gemakkelijker te kunnen lezen. Het venster bevat een zoek functie voor **zoeken** en een **instellingen** venster waarmee u opties voor de weer gave kunt instellen, inclusief opties voor het weer geven van alleen geselecteerde secties van een Help-onderwerp.

De **ShowWindow** -para meter ondersteunt Help-onderwerpen voor opdrachten (cmdlets, functies, CIM-opdrachten, scripts) en conceptuele **informatie over** artikelen. De Help van de provider wordt niet ondersteund.

Deze para meter is opnieuw geïntroduceerd in Power shell 7,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar beneden verplaatsen in de pijp lijn `Get-Help` .

## UITVOER

### ExtendedCmdletHelpInfo

Als u uitvoert `Get-Help` op een opdracht die geen Help-bestand heeft, `Get-Help` retourneert een **ExtendedCmdletHelpInfo** -object dat automatisch gegenereerde Help vertegenwoordigt.

### System. String

Als u een conceptueel Help-artikel krijgt, `Get-Help` retourneert dit als een teken reeks.

### MamlCommandHelpInfo

Als u een opdracht krijgt met een Help-bestand, `Get-Help` wordt een **MamlCommandHelpInfo** -object geretourneerd.

## OPMERKINGEN

Power Shell 3,0 bevat geen Help-bestanden. Als u de Help-bestanden wilt downloaden en installeren die `Get-Help` worden gelezen, gebruikt u de `Update-Help` cmdlet. U kunt de `Update-Help` cmdlet gebruiken om Help-bestanden te downloaden en te installeren voor de kern opdrachten die worden geleverd met Power shell en voor alle modules die u installeert. U kunt dit ook gebruiken om de Help-bestanden bij te werken, zodat de Help op uw computer nooit verouderd is.

U kunt ook de Help-artikelen lezen over de opdrachten die worden geleverd met Power shell online, vanaf aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

`Get-Help` geeft Help weer in de land instellingen die zijn ingesteld voor het Windows-besturings systeem of in de terugval taal voor die land instelling. Als u geen Help-bestanden hebt voor de primaire of terugval land instelling, `Get-Help` gedraagt zich alsof er geen Help-bestanden op de computer zijn. Als u hulp nodig hebt bij een andere land instelling, gebruikt u **regio** en **taal** in het configuratie scherm om de instellingen te wijzigen. In Windows 10, **instellingen** , **tijd & taal**.

De volledige weer gave van Help bevat een tabel met informatie over de para meters. De tabel bevat de volgende velden:

- **Vereist**. Hiermee wordt aangegeven of de para meter vereist is (true) of optioneel (false).

- **Positie**. Hiermee wordt aangegeven of de para meter een naam of positioneel (numeriek) is. Positionele para meters moeten worden weer gegeven in een opgegeven plaats in de opdracht.

- Met de **naam** geeft aan dat de parameter naam vereist is, maar dat de para meter overal in de opdracht kan worden weer gegeven.

- Een **numerieke** waarde geeft aan dat de parameter naam optioneel is, maar wanneer de naam wordt wegge laten, moet de para meter zich in de plaats bevinden die is opgegeven door het getal. `2`Geeft bijvoorbeeld aan dat wanneer de parameter naam wordt wegge laten, de para meter de tweede of enige niet-genaamde para meter in de opdracht moet zijn. Wanneer de parameter naam wordt gebruikt, kan de para meter in een wille keurige plaats in de opdracht worden weer gegeven.

- **Standaard waarde**. De parameter waarde of het standaard gedrag dat door Power shell wordt gebruikt als u de para meter niet in de opdracht opneemt.

- Accepteert invoer van de pijp lijn. Hiermee wordt aangegeven of u (true) of niet (false) objecten naar de para meter kunt verzenden via een pijp lijn. **Op naam van eigenschap** betekent dat het pipeline-object een eigenschap moet hebben die dezelfde naam heeft als de parameter naam.

- **Accepteert joker tekens**. Hiermee wordt aangegeven of de waarde van een para meter joker tekens kan bevatten, zoals een asterisk ( `*` ) of een vraag teken ( `?` ).

## GERELATEERDE KOPPELINGEN

[about_Command_Syntax](About/about_Command_Syntax.md)

[about_Comment_Based_Help](./About/about_Comment_Based_Help.md)

[Get-Command](Get-Command.md)

[Ondersteunende help die kan worden bijgewerkt](/powershell/scripting/developer/module/supporting-updatable-help)

[Update-Help](Update-Help.md)

[Help-onderwerpen op basis van opmerkingen schrijven](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[Help voor PowerShell-cmdlets schrijven](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

