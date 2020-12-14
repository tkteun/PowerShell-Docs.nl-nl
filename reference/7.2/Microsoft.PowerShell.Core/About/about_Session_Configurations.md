---
description: Hierin worden de sessie configuraties beschreven, waarmee wordt bepaald welke gebruikers op afstand verbinding kunnen maken met de computer en welke opdrachten ze kunnen uitvoeren.
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 4c6d5494f49bc271a7fe128fbce7b27c9d1f675f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706080"
---
# <a name="about-session-configurations"></a>Over sessie configuraties

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de sessie configuraties beschreven, waarmee wordt bepaald welke gebruikers op afstand verbinding kunnen maken met de computer en welke opdrachten ze kunnen uitvoeren.

## <a name="long-description"></a>LANGE BESCHRIJVING

Een sessie configuratie, ook wel een ' eind punt ' genoemd, is een groep instellingen op de lokale computer die de omgeving definiëren voor de Power shell-sessies die worden gemaakt wanneer externe of lokale gebruikers verbinding maken met Power shell op de lokale computer.

Beheerders van de computer kunnen sessie configuraties gebruiken om de computer te beveiligen en aangepaste omgevingen te definiëren voor gebruikers die verbinding maken met de computer.

Beheerders kunnen ook sessie configuraties gebruiken om de machtigingen te bepalen die nodig zijn om op afstand verbinding te maken met de computer. Standaard hebben alleen leden van de groep Administrators toestemming om de sessie configuratie te gebruiken om extern verbinding te maken, maar u kunt de standaard instellingen wijzigen zodat alle gebruikers of geselecteerde gebruikers extern verbinding kunnen maken met uw computer.

Vanaf Power Shell 3,0 kunt u een configuratie bestand voor de sessie gebruiken om de elementen van een sessie configuratie te definiëren. Met deze functie kunt u eenvoudig sessies aanpassen zonder code te schrijven en de eigenschappen van een sessie configuratie detecteren. Gebruik de cmdlet New-PSSessionConfiguration om een sessie configuratie bestand te maken. Zie [about_Session_Configuration_Files](about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.

Sessie configuraties zijn een functie van webservices voor beheer op basis van Power shell voor externe toegang. Ze worden alleen gebruikt wanneer u de cmdlets New-PSSession, Invoke-Command of Enter-PSSession gebruikt om verbinding te maken met een externe computer.

Opmerking: als u de sessie configuraties wilt beheren, start u Power shell met de optie als administrator uitvoeren.

Over sessie configuraties

Elke Power shell-sessie gebruikt een sessie configuratie. Dit omvat permanente sessies die u maakt met behulp van de New-PSSession-of Enter-PSSession-cmdlets en de tijdelijke sessies die Power Shell maakt wanneer u de para meter ComputerName gebruikt van een cmdlet die gebruikmaakt van op WS-Management gebaseerde externe technologieën, zoals invoke-Command.

Beheerders kunnen sessie configuraties gebruiken om de bronnen van de computer te beveiligen en om aangepaste omgevingen te maken voor gebruikers die verbinding maken met de computer. U kunt bijvoorbeeld een sessie configuratie gebruiken om de grootte van objecten die de computer ontvangt in de sessie te beperken, om de taal modus van de sessie te definiëren en om de cmdlets, providers en functies op te geven die beschikbaar zijn in de sessie.

Door de security descriptor van een sessie configuratie te configureren, bepaalt u wie de sessie configuratie kan gebruiken om verbinding te maken met de computer.
Gebruikers moeten beschikken over de machtiging uitvoeren voor een sessie configuratie om deze te gebruiken in een sessie. Als een gebruiker niet over de vereiste machtigingen beschikt om een van de sessie configuraties op een computer te gebruiken, kan de gebruiker niet op afstand verbinding maken met de computer.

Standaard hebben alleen beheerders van de computer toestemming om de standaard sessie configuraties te gebruiken. Maar u kunt de security descriptors wijzigen zodat iedereen, niemand, of alleen geselecteerde gebruikers de sessie configuraties op uw computer kunnen gebruiken.

Ingebouwde sessie configuraties

Power Shell 3,0 bevat ingebouwde sessie configuraties met de naam micro soft. Power shell en micro soft. Power shell. workflow. Op computers met 64-bits versies van Windows biedt Power shell ook micro soft. PowerShell32, een 32-bits sessie configuratie.

De configuratie van de micro soft. Power shell-sessie wordt standaard gebruikt voor sessies, dat wil zeggen, wanneer een opdracht voor het maken van een sessie niet de para meter configuratiepad van de cmdlet New-PSSession, Enter-PSSession of Invoke-Command bevat.

Met de security descriptors voor de standaard sessie configuraties kunnen alleen leden van de groep Administrators op de lokale computer deze gebruiken. Als zodanig kunnen alleen leden van de groep Administrators op afstand verbinding maken met de computer, tenzij u de standaard instellingen wijzigt.

U kunt de standaard sessie configuraties wijzigen met behulp van de voorkeurs variabele $PSSessionConfigurationName. Zie about_Preference_Variables voor meer informatie.

Sessie configuraties weer geven op de lokale computer

Gebruik de cmdlet Get-PSSessionConfiguration om de sessie configuraties op uw lokale computer op te halen.

Typ bijvoorbeeld:

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

Het sessie configuratie object wordt uitgevouwen in Power Shell 3,0 om de eigenschappen van de sessie configuratie weer te geven die zijn geconfigureerd met behulp van een configuratie bestand voor de sessie.

Als u bijvoorbeeld alle eigenschappen van een sessie configuratie object wilt weer geven, typt u:

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

U kunt ook de WSMan-provider in Power shell gebruiken om de sessie configuraties weer te geven. De WSMan-provider maakt een WSMAN:-station in uw sessie.

In het WSMAN: station bevinden de sessie configuraties zich in het knoop punt van de invoeg toepassing. (Alle sessie configuraties bevinden zich in het knoop punt van de invoeg toepassing, maar er zijn items in het knoop punt van de invoeg toepassing die geen sessie configuraties zijn.)

Als u bijvoorbeeld de sessie configuraties op de lokale computer wilt weer geven, typt u:

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

Sessie configuraties weer geven op een externe computer

Als u de sessie configuraties op een externe computer wilt weer geven, gebruikt u de Connect-WSMan-cmdlet om een notitie voor de externe computer toe te voegen aan het WSMAN:-station op uw lokale computer en vervolgens het WSMAN:-station te gebruiken om de sessie configuraties weer te geven.

Met de volgende opdracht wordt bijvoorbeeld een knoop punt voor de externe computer Server01 toegevoegd aan het WSMAN:-station op de lokale computer.

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

Wanneer de opdracht is voltooid, kunt u naar het knoop punt voor de Server01-computer navigeren om de sessie configuraties weer te geven.

Bijvoorbeeld:

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

De security descriptor van een sessie configuratie wijzigen

In Windows Server 2012 en nieuwere versies van Windows Server worden de ingebouwde sessie configuraties standaard ingeschakeld voor externe gebruikers. In andere ondersteunde versies van Windows moet u de security descriptors van de sessie configuraties wijzigen om externe toegang toe te staan.

Gebruik de cmdlet Enable-PSRemoting om externe toegang tot de sessie configuraties op de computer in te scha kelen. Met deze cmdlet worden twee sessie configuraties gemaakt:

- met de naam die is gedefinieerd als: Power shell. + "huidige Power shell-versie"
- met de naam Power shell. 6, die niet is gekoppeld aan een specifieke Power shell-versie.

Standaard hebben alleen leden van de groep Administrators op de computer de machtiging uitvoeren voor de standaard sessie configuraties, maar u kunt de security descriptors wijzigen op de standaard sessie configuraties en op de sessie configuraties die u maakt.

Als u andere gebruikers toestemming wilt geven om op afstand verbinding te maken met de computer, gebruikt u de cmdlet Set-PSSessionConfiguration om ' Execute ' machtigingen voor die gebruikers toe te voegen aan de security descriptors van de micro soft. Power shell-en micro soft. PowerShell32-sessie configuraties.

Met de volgende opdracht wordt bijvoorbeeld een eigenschappen pagina geopend waarmee u de security descriptor voor de standaard sessie configuratie van micro soft. Power shell kunt wijzigen.

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

Als u iedereen toestemming wilt verlenen voor alle sessie configuraties op de computer, gebruikt u de cmdlet Disable-PSSessionConfiguration. Met de volgende opdracht worden bijvoorbeeld de standaard sessie configuraties op de computer uitgeschakeld.

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

Als u wilt voor komen dat externe gebruikers verbinding maken met de computer, maar lokale gebruikers verbinding laten maken, gebruikt u de cmdlet Disable-PSRemoting. Disable-PSRemoting voegt een vermelding ' Network_Deny_All ' toe aan alle sessie configuraties op de computer.

```powershell
PS C:> Disable-PSRemoting
```

Als u wilt dat externe gebruikers alle sessie configuraties op de computer kunnen gebruiken, gebruikt u de cmdlet Enable-PSRemoting of Enable-PSSessionConfiguration. Met de volgende opdracht wordt bijvoorbeeld externe toegang tot de ingebouwde sessie configuraties ingeschakeld.

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

Gebruik de Set-PSSessionConfiguration-cmdlet om andere wijzigingen aan te brengen in de security descriptor van een sessie configuratie. Gebruik de para meter SecurityDescriptorSDDL om een SDDL-teken reeks waarde in te dienen. Gebruik de para meter ShowSecurityDescriptorUI om een eigenschappen venster van de gebruikers interface weer te geven waarmee u een nieuwe SDDL kunt maken.

Bijvoorbeeld:

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

Een nieuwe sessie configuratie maken

Als u een nieuwe sessie configuratie wilt maken op de lokale computer, gebruikt u de cmdlet Register-PSSessionConfiguration. Als u de nieuwe sessie configuratie wilt definiëren, kunt u een C#-assembly, een Power shell-script en de para meters van de cmdlet Register-PSSessionConfiguration gebruiken.

Met de volgende opdracht maakt u bijvoorbeeld een sessie configuratie die identiek is aan de configuratie van de micro soft. Power shell-sessie, met uitzonde ring van de gegevens die zijn ontvangen van een externe opdracht tot 20 Mega bytes (MB). (De standaard waarde is 50 MB).

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

Wanneer u een sessie configuratie maakt, kunt u deze beheren met behulp van de andere sessie configuratie-cmdlets en deze wordt weer gegeven in het station WSMAN:.

Zie REGI ster-PSSessionConfiguration voor meer informatie.

Een sessie configuratie verwijderen

Als u een sessie configuratie wilt verwijderen van de lokale computer, gebruikt u de cmdlet Unregister-PSSessionConfiguration. Met de volgende opdracht wordt bijvoorbeeld de NewConfig-sessie configuratie van de computer verwijderd.

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

Zie unregister-PSSessionConfiguration voor meer informatie.

Een sessie configuratie herstellen

Als u een standaard sessie configuratie wilt herstellen die per ongeluk is verwijderd (niet geregistreerd), gebruikt u de Enable-PSRemoting-cmdlet.

Met de cmdlet Enable-PSRemoting worden alle standaard-sessie configuraties die niet bestaan op de computer opnieuw gemaakt. De eigenschaps waarden van bestaande sessie configuraties worden niet overschreven of gewijzigd.

Als u de oorspronkelijke eigenschaps waarden van een standaard sessie configuratie wilt herstellen, gebruikt u de Unregister-PSSessionConfiguration om de sessie configuratie te verwijderen en gebruikt u vervolgens de Enable-PSRemoting cmdlet om deze opnieuw te maken.

Een sessie configuratie selecteren

Als u een bepaalde sessie configuratie voor een sessie wilt selecteren, gebruikt u de para meter configuratiepad van New-PSSession, Enter-PSSession of invoke-Command.

Met deze opdracht wordt bijvoorbeeld de cmdlet New-PSSession gebruikt om een PSSession op de Server01-computer te starten. De opdracht gebruikt de para meter configuratiepad om de WithProfile-configuratie op de Server01-computer te selecteren.

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

Deze opdracht kan alleen worden uitgevoerd als de huidige gebruiker gemachtigd is om de WithProfile-sessie configuratie te gebruiken of de referenties op te geven van een gebruiker die de vereiste machtigingen heeft.

U kunt ook de $PSSessionConfigurationName voorkeurs variabele gebruiken om de standaard sessie configuratie op de computer te wijzigen. Zie about_Preference_Variables voor meer informatie over de $PSSessionConfigurationName voorkeurs variabele.

## <a name="keywords"></a>WOORD

about_Endpoints about_SessionConfigurations

## <a name="see-also"></a>ZIE OOK

[about_Preference_Variables](about_Preference_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Session_Configuration_Files](about_Session_Configuration_Files.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Registratie ongedaan maken-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

