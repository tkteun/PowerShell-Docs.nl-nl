---
description: Beschrijft het Help-systeem dat kan worden bijgewerkt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: 03425aef93f3d4bbb06aee87d30f4a441c0b2d86
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252738"
---
# <a name="about-updatable-help"></a>Informatie over bijwerk bare Help

## <a name="short-description"></a>Korte beschrijving
Beschrijft het Help-systeem dat kan worden bijgewerkt in Power shell.

## <a name="long-description"></a>Lange beschrijving

Power shell biedt verschillende manieren om toegang te krijgen tot de meest recente Help-onderwerpen voor Power shell-cmdlets en-concepten.

Het bij te werken Help-systeem, geïntroduceerd in Power Shell 3,0, is ontworpen om ervoor te zorgen dat u altijd over de nieuwste Help-onderwerpen op uw lokale computer beschikt zodat u ze op de opdracht regel kunt lezen. Het is eenvoudig om Help-bestanden te downloaden en te installeren en ze bij te werken wanneer nieuwere Help-bestanden beschikbaar zijn.

Als u bijgewerkte hulp wilt bieden voor meerdere computers in een onderneming en voor computers die geen toegang tot internet hebben, kunt u met behulp van de Help-informatie Help-bestanden downloaden naar een bestandssysteem Directory of bestands share, en vervolgens de Help-bestanden installeren vanuit de bestands share.

In Power Shell 4,0 wordt de eigenschap **HelpInfoUri** overgenomen van Windows Power shell Remoting, waarmee `Save-Help` u kunt werken met modules die zijn geïnstalleerd op een externe computer, maar niet per se geïnstalleerd zijn op de lokale computer. U kunt een **PSModuleInfo** -object opslaan op schijf of verwissel bare media (zoals een USB-station) door uit te voeren `Export-Clixml` op een computer die geen toegang heeft tot internet, het **PSModuleInfo** -object te importeren op een computer die toegang heeft tot internet en vervolgens wordt uitgevoerd `Save-Help` op het **PSModuleInfo** -object. De opgeslagen Help kan worden gekopieerd naar de externe, niet-verbonden computer met behulp van Verwissel bare media en vervolgens worden geïnstalleerd door te worden uitgevoerd `Update-Help` . Met deze verbeteringen in `Save-Help` functionaliteit kunt u Help installeren op computers die geen netwerk toegang zijn. Voor een voor beeld van het gebruik van de nieuwe `Save-Help` functionaliteit raadpleegt [u Help bijwerken vanuit een bestands share](#how-to-update-help-from-a-file-share) in dit onderwerp.

Bij te werken Help kan ook online toegang worden geboden tot de nieuwste Help-onderwerpen en de Basic-Help voor cmdlets, zelfs wanneer er geen Help-bestanden op de computer staan.

Power Shell 3,0 wordt niet geleverd met Help-bestanden. U kunt de Help-functie die kan worden bijgewerkt gebruiken om de Help-bestanden te installeren voor alle opdrachten die standaard zijn opgenomen in Power shell en voor alle Windows-modules.

## <a name="updatable-help-cmdlets"></a>Help-cmdlets die kunnen worden bijgewerkt

- `Update-Help`: Downloadt de nieuwste Help-bestanden van Internet of een bestands share en installeert ze op de lokale computer.

- `Save-Help`: Downloadt de nieuwste Help-bestanden van Internet en slaat ze op in een bestandssysteem Directory of bestands share. Als u de Help-bestanden op computers wilt installeren, gebruikt u `Update-Help` .

- `Get-Help`: De Help-onderwerpen worden weer gegeven op de opdracht regel. Hiermee krijgt u hulp van de Help-bestanden op de computer. Hiermee wordt automatisch gegenereerde Help weer gegeven voor cmdlets en functies die geen Help-bestanden hebben. Hiermee opent u online Help-onderwerpen voor cmdlets, functies, scripts en werk stromen in uw standaard Internet browser.

## <a name="update-help-in-the-powershell-ise"></a>Help-informatie bijwerken in Power shell ISE

U kunt de Help ook bijwerken met behulp van het Help-item **Power shell bijwerken** in het menu Help in Power shell Integrated Scripting Environment (ISE).

Het **Help-item update Power shell** voert een `Update-Help` opdracht zonder para meters uit.

## <a name="auto-generated-help-help-without-help-files"></a>Automatisch gegenereerde Help: Help zonder Help-bestanden

Als u niet beschikt over het Help-bestand voor een cmdlet, functie of werk stroom op de computer, `Get-Help` wordt door de cmdlet automatisch gegenereerde Help weer gegeven en wordt u gevraagd om de Help-bestanden te downloaden of ze online te lezen.

Automatisch gegenereerde Help omvat syntaxis en aliassen, en opmerkingen met uitleg over het gebruik van de Help-cmdlets die kunnen worden bijgewerkt en voor toegang tot de online Help-onderwerpen.

De volgende opdracht wordt bijvoorbeeld Basic-Help voor de `Get-Culture` cmdlet. De uitvoer toont de `Get-Help` weer gave wanneer er geen Help-bestanden op de computer staan.

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a>Help-bestanden voor modules

De kleinste eenheid van de Help die kan worden bijgewerkt is een hulp voor een module. De Help van module bevat hulp voor alle cmdlets, functies, werk stromen, providers, scripts en concepten in een module. U kunt de Help bijwerken voor alle modules die op de computer zijn geïnstalleerd, zelfs als deze niet in de huidige sessie zijn geïmporteerd.

U kunt de Help-informatie voor de hele module bijwerken, maar u kunt geen Help bijwerken voor afzonderlijke cmdlets.

Als u de module wilt vinden die een bepaalde cmdlet bevat, gebruikt u de volgende opdracht indeling:

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

Als u bijvoorbeeld de module wilt vinden die de `Set-ExecutionPolicy` cmdlet bevat, typt u:

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

Als u de Help voor een bepaalde module wilt bijwerken, typt u:

```powershell
Update-Help -Module <ModuleName>
```

Als u bijvoorbeeld Help wilt bijwerken voor de module met de cmdlet Set-ExecutionPolicy, typt u:

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a>Machtigingen voor Help die kan worden bijgewerkt

Als u de Help voor de modules in de map wilt bijwerken `$pshome/Modules` , moet u lid zijn van de groep Administrators op de computer.

Als u geen lid bent van de groep Administrators, kunt u de Help voor deze modules niet bijwerken. maar als u toegang hebt tot internet, kunt u Help online bekijken.

Bij het bijwerken van de Help voor modules in de Directory `$home/Documents/PowerShell/Modules` of modules in andere submappen van de `$home` Directory zijn geen speciale machtigingen vereist.

De `Update-Help` `Save-Help` cmdlets en hebben een **UseDefaultCredentials** -para meter waarmee de expliciete referenties van de huidige gebruiker worden verstrekt. Deze para meter is ontworpen voor toegang tot beveiligde Internet locaties.

De `Update-Help` `Save-Help` cmdlets en hebben ook de para meter **Credential** waarmee u de opdracht kunt uitvoeren op een externe computer en toegang hebt tot een bestands share op een derde computer. De para meter **Credential** is alleen geldig als u de para meter SourcePath of **LiteralPath** van `Update-Help` en de **doelpad** -of **LiteralPath** -para meters van gebruikt `Save-Help` .

## <a name="how-to-install-and-update-help-files"></a>Help-bestanden installeren en bijwerken

Gebruik de cmdlet om Help-bestanden voor de eerste keer te downloaden en te installeren, of om de Help-bestanden op uw computer bij te werken `Update-Help` .

`Update-Help`Met de cmdlet worden alle vaste werk voor u uitgevoerd, met inbegrip van de volgende taken.

- Hiermee wordt bepaald welke modules kunnen worden bijgewerkt.
- Hiermee wordt gezocht naar de Internet locatie waar elke module de bij te werken Help-bestanden opslaat.
- Vergelijkt de Help-bestanden voor elke module op uw computer met de nieuwste Help-bestanden die voor elke module beschikbaar zijn.
- Downloadt de nieuwe bestanden van het internet.
- In wordt het pakket met de Help-bestanden uitgepakt.
- Verifieert of de bestanden geldige Help-bestanden zijn.
- Installeert de Help-bestanden in de taalspecifieke submap van de module directory.

Gebruik de cmdlet om toegang te krijgen tot de nieuwe Help-onderwerpen `Get-Help` . U hoeft Power shell niet opnieuw op te starten.

Als u de Help wilt installeren of bijwerken voor alle modules op de computer die de Help-informatie die kan worden bijgewerkt ondersteunt, typt u:

```powershell
Update-Help
```

Als u de Help voor bepaalde modules wilt bijwerken, voegt u de **module** parameter van toe `Update-Help` . Joker tekens zijn toegestaan in de module naam.

Als u bijvoorbeeld de Help voor de module Server Manager wilt bijwerken, typt u:

```powershell
Update-Help -Module ServerManager
```

Zonder para meters `Update-Help` helpt updates voor alle modules in de sessie en voor alle geïnstalleerde modules die kunnen worden bijgewerkt met ondersteuning. Om te worden opgenomen, moeten modules worden geïnstalleerd in mappen die worden vermeld in de waarde van de omgevings variabele PSModulePath. Dit zijn ook modules die worden geretourneerd door de opdracht Get-Help-ListAvailable.

Als de waarde van de **module** parameter is `*` (alle), wordt `Update-Help` geprobeerd om de Help bij te werken voor alle geïnstalleerde modules, inclusief modules die geen ondersteuning bieden voor bijwerk bare Help. Met deze opdracht worden doorgaans veel fouten gegenereerd, omdat de cmdlet modules detecteert die geen ondersteuning bieden voor Help.

## <a name="how-to-update-help-from-a-file-share"></a>Help van een bestands share bijwerken

Gebruik de cmdlet om computers te ondersteunen die niet zijn verbonden met internet, of om het bijwerken van de Help in een onderneming te beheren of te stroom lijnen `Save-Help` . De `Save-Help` cmdlet downloadt Help-bestanden van Internet en slaat ze op in een bestandssysteem Directory die u opgeeft.

`Save-Help` de Help-bestanden in de opgegeven map worden vergeleken met de nieuwste Help-bestanden die beschikbaar zijn voor elke module. Als de Directory geen Help-bestanden of nieuwere Help-bestanden voor de module beschikbaar heeft, `Save-Help` downloadt de cmdlet de nieuwe bestanden van het internet. De Help-bestanden worden echter niet uitgepakt of geïnstalleerd.

Als u de Help-bestanden op een computer wilt installeren of bijwerken vanuit Help-bestanden die zijn opgeslagen in een bestandssysteem Directory, gebruikt u de para meter **SourcePath** van de `Update-Help` cmdlet. Met de `Update-Help` cmdlet worden de nieuwste Help-bestanden geïdentificeerd, worden deze teruggestuurd en gevalideerd en worden deze in de taalspecifieke submappen van de module mappen geïnstalleerd.

Als u bijvoorbeeld Help wilt opslaan voor alle geïnstalleerde modules in de `\\Server\Share` map, typt u:

```powershell
Save-Help -DestinationPath \\Server\Share
```

Als u de Help vanuit de map wilt bijwerken `\\Server\Share` , typt u:

```powershell
Update-Help -SourcePath \\Server\Share
```

In de volgende voor beelden ziet u het gebruik van `Save-Help` om Help op te slaan voor modules die niet op de lokale computer zijn geïnstalleerd. In dit voor beeld wordt de-beheerder uitgevoerd `Save-Help` om de Help voor de DHCP-module op te slaan vanaf een client computer met Internet verbinding, zonder dat u de DHCP-module DHCP-server of de-serverrol op de lokale computer hoeft te installeren.

Optie 1: Voer uit `Invoke-Command` om het **PSModuleInfo** -object voor de externe module op te halen, op te slaan in een variabele, `$m` en voer vervolgens uit `Save-Help` op het **PSModuleInfo** -object door de variabele op te geven `$m` als de module naam.

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

Optie 2: Open een PSSession die is gericht op de computer waarop de DHCP-server module wordt uitgevoerd, om het **PSModuleInfo** -object voor de module op te halen, op te slaan in een variabele `$m` en vervolgens uit te voeren `Save-Help` op het object dat is opgeslagen in de `$m` variabele.

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

Optie 3: Open een CIM-sessie, gericht op de computer waarop de DHCP-server module wordt uitgevoerd, om het **PSModuleInfo** -object voor de module op te halen, op te slaan in een variabele `$m` en vervolgens uit te voeren `Save-Help` op het object dat is opgeslagen in de `$m` variabele.

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

In het volgende voor beeld installeert de beheerder Help voor de module DHCP-server op een computer die geen netwerk toegang heeft.

Voer eerst uit `Export-Clixml` om het **PSModuleInfo** -object te exporteren naar een gedeelde map of naar een verwisselbaar medium.

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

Transport vervolgens de Verwissel bare media naar een computer met Internet toegang en importeer vervolgens het **PSModuleInfo** -object met `Import-Clixml` . Voer uit `Save-Help` om de Help voor het geïmporteerde DHCP-module **PSModuleInfo** -object op te slaan.

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

Transport vervolgens de Verwissel bare media Terug naar de computer die geen netwerk toegang heeft en installeer vervolgens de Help door uit te voeren `Update-Help` .

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

Zonder para meters, `Save-Help` down loads Help voor alle modules in de sessie en voor alle geïnstalleerde modules die kunnen worden bijgewerkt met ondersteuning. Om te worden opgenomen, moeten modules worden geïnstalleerd in mappen die worden vermeld in de waarde van de `$env:PSModulePath` omgevings variabele, op de lokale computer of op een externe computer waarvoor u de Help wilt opslaan. Dit zijn ook modules die worden geretourneerd door een opdracht uit te voeren `Get-Help -ListAvailable` .

## <a name="how-to-update-help-files-in-different-languages"></a>Help-bestanden in verschillende talen bijwerken

Standaard `Update-Help` `Save-Help` downloaden de cmdlets en Help-informatie in de UI-cultuur en taal die is ingesteld voor Windows op de lokale computer. Als de Help-bestanden voor de opgegeven modules niet beschikbaar zijn in de lokale GEBRUIKERSINTERFACE cultuur `Update-Help` en `Save-Help` de Windows-taal terugval regels gebruiken om de best ondersteunde taal te vinden.

U kunt echter de **uiCulture** -para meters van de- `Update-Help` en- `Save-Help` cmdlets gebruiken om Help-bestanden te downloaden en te installeren in alle gebruikersinterface culturen waarin deze beschikbaar zijn.

Als u bijvoorbeeld de nieuwste Help-bestanden voor alle modules in de sessie in het Japans (ja-JP) en Frans (fr-FR) wilt opslaan, typt u:

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

Als Help-bestanden voor de modules niet beschikbaar zijn in de talen die u hebt opgegeven, `Update-Help` retour neren de-en- `Save-Help` cmdlets een fout bericht met een lijst met de talen waarin de Help voor elke module beschikbaar is, zodat u het alternatief kunt kiezen dat het beste aan uw behoeften voldoet.

> [!NOTE]
> Op dit moment wordt Help-inhoud die kan worden bijgewerkt, alleen in het Engels gepubliceerd (en-US).

## <a name="how-to-use-online-help"></a>Online-Help gebruiken

Als u de Help-bestanden op uw lokale computer niet kunt of niet wilt bijwerken, kunt u nog steeds de nieuwste Help-bestanden online ophalen.

Als u het online-Help-onderwerp voor een cmdlet of functie wilt openen, gebruikt u de para meter **online** van de `Get-Help` cmdlet.

Met de volgende opdracht wordt bijvoorbeeld het online-Help-onderwerp voor de `Get-Job` cmdlet in de standaard browser van Internet geopend:

```powershell
Get-Help Get-Job -Online
```

Als u online-Help voor een script wilt krijgen, gebruikt u de para meter **online** en het volledige pad naar het script.

De para meter **online** werkt niet met informatie over onderwerpen. Zie [Power shell about topics](about.md)(Engelstalig) voor een overzicht van de onderwerpen over Power shell, inclusief Help-onderwerpen over de Power shell-taal.

## <a name="how-to-minimize-or-prevent-internet-downloads"></a>Internet downloads minimaliseren of voor komen

Gebruik de-cmdlet om Internet downloads te minimaliseren en Help-informatie te bieden voor gebruikers die niet zijn verbonden met internet `Save-Help` . Down load de Help van Internet en sla deze op een netwerk share op. Maak vervolgens een groepsbeleid-instelling of een geplande taak die een `Update-Help` opdracht op alle computers uitvoert. Stel de waarde van de para meter **SourcePath** van de `Update-Help` cmdlet in op de netwerk share.

Als u wilt voor komen dat gebruikers met Internet toegang via internet kunnen worden gedownload, gebruikt u de instelling **het standaard bronpad instellen voor update-Help** Groepsbeleid.

Met deze groepsbeleid instelling wordt impliciet de para meter **SourcePath** toegevoegd, met de locatie van het bestands systeem dat u opgeeft, voor elke `Update-Help` opdracht op elke betrokken computer. Gebruikers kunnen de para meter **SourcePath** expliciet gebruiken om een andere bestandssysteem locatie op te geven, maar ze kunnen de para meter **SourcePath** niet uitsluiten en de Help van Internet niet downloaden.

> [!NOTE]
> De instelling **het standaard bronpad instellen voor bijwerken-Help** groeps beleid wordt weer gegeven onder **computer configuratie** en **gebruikers configuratie**. De beleids instelling onder **computer configuratie** is echter alleen effectief. De beleids instelling onder **gebruikers configuratie** wordt genegeerd.

Zie [about_Group_Policy_Settings](about_Group_Policy_Settings.md)voor meer informatie.

## <a name="how-to-update-help-for-non-standard-modules"></a>Help voor niet-standaard modules bijwerken

Als u Help wilt bijwerken of opslaan voor een module die niet wordt geretourneerd door de para meter **ListAvailable** van de `Get-Module` cmdlet, importeert u de module in de huidige sessie voordat u een `Update-Help` of-opdracht uitvoert `Save-Help` . Importeer op een externe computer voordat u de `Save-Help` opdracht uitvoert de module in de huidige sessie, of het `Invoke-Command` script blok, dat is verbonden met de externe computer.

Wanneer de module zich in de huidige sessie bevindt, voert `Update-Help` `Save-Help` u de cmdlets en zonder para meters uit of gebruikt u de **module** parameter om de module naam op te geven.

De **module** parameters van de `Update-Help` `Save-Help` cmdlets en accepteren alleen een module naam. Het pad naar een module bestand wordt niet geaccepteerd.

Gebruik deze techniek om hulp bij te werken of bij te houden voor een module die niet wordt geretourneerd door de para meter **ListAvailable** van de `Get-Module` cmdlet, zoals een module die is geïnstalleerd op een locatie die niet wordt vermeld in de `$env:PSModulePath` omgevings variabele, of een module die niet juist is opgemaakt (de module directory bevat niet ten minste één bestand waarvan base naam gelijk is aan de mapnaam).

## <a name="how-to-support-updatable-help"></a>Ondersteunende Help ondersteunen

Als u een module ontwerpt, kunt u online-Help en Help-informatie voor uw modules ondersteunen. Zie [ondersteunende Help](/powershell/scripting/developer/help/supporting-updatable-help) en [ondersteunende online help](/powershell/scripting/developer/module/supporting-online-help) in de Microsoft docs voor meer informatie.

Help-informatie die kan worden bijgewerkt, is niet beschikbaar voor Power shell-modules of Help op basis van opmerkingen.

## <a name="remarks"></a>Opmerkingen

De `Update-Help` `Save-Help` cmdlets en worden niet ondersteund op Windows Preinstallation Environment (Windows PE).

## <a name="see-also"></a>Zie ook

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Opslaan-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
