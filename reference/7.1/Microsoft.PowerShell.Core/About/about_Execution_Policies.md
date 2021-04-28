---
description: Hierin worden het PowerShell uitvoeringsbeleid beschreven en wordt uitgelegd hoe u deze beheert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 6c2d4b784c68649ea88e744a9cf5df6329ac897f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252444"
---
# <a name="about-execution-policies"></a>Over uitvoeringsbeleid

## <a name="short-description"></a>Korte beschrijving
Hierin worden het PowerShell uitvoeringsbeleid beschreven en wordt uitgelegd hoe u deze beheert.

## <a name="long-description"></a>Lange beschrijving

Het uitvoeringsbeleid van PowerShell is een veiligheidsfunctie die de voorwaarden bepaalt waaronder PowerShell configuratie bestanden laadt en scripts uitvoert. Deze functie helpt de uitvoering van schadelijke scripts te voorkomen.

Op een Windows-computer kunt u een uitvoeringsbeleid voor de lokale computer instellen, voor de huidige gebruiker of voor een bepaalde sessie. U kunt ook een groepsbeleid instelling gebruiken om uitvoeringsbeleid in te stellen voor computers en gebruikers.

Uitvoeringsbeleid voor de lokale computer en de huidige gebruiker worden opgeslagen in het Register. U hoeft geen uitvoeringsbeleid in te stellen in uw PowerShellprofiel.
Het uitvoeringsbeleid voor een bepaalde sessie wordt alleen in het geheugen opgeslagen en gaat verloren wanneer de sessie wordt gesloten.

Het uitvoeringsbeleid is geen beveiligingssysteem dat gebruikersacties beperkt. Gebruikers kunnen bijvoorbeeld eenvoudig een beleid overslaan door de inhoud van het script te typen op de opdrachtregel wanneer ze geen script kunnen uitvoeren. Het uitvoeringsbeleid helpt in plaats daarvan basisregels in te stellen en voor komt dat ze per ongeluk worden geschonden.

Op niet-Windows computers is het standaard uitvoeringsbeleid **onbeperkt** en kan het niet worden gewijzigd. De `Set-ExecutionPolicy` cmdlet is beschikbaar, maar in PowerShell wordt een consolebericht weergegeven dat niet wordt ondersteund. Hoewel `Get-ExecutionPolicy` retourneert **onbeperkt** op niet-Windows platforms, komt het gedrag werkelijk overeen met **bypass** , omdat deze platformen de Windows-beveiligings zones niet implementeren.

## <a name="powershell-execution-policies"></a>Power shell-uitvoerings beleid

Het afdwingen van deze beleidsregels vindt alleen plaats op Windows-platforms. Het PowerShell uitvoeringsbeleid is als volgt:

### <a name="allsigned"></a>Alles ondertekend

- Scripts kunnen worden uitgevoerd.
- Vereist dat alle scripts en configuratiebestanden worden ondertekend door een vertrouwde uitgever, met inbegrip van scripts die u op de lokale computer schrijft.
- Hiermee wordt u gevraagd of u scripts van uitgevers wilt uitvoeren die u nog niet hebt geclassificeerd als vertrouwd of niet-vertrouwde.
- Risico's die ondertekend zijn, maar schadelijke scripts.

### <a name="bypass"></a>Bypass

- Er is niets geblokkeerd en er zijn geen waarschuwingen of prompts.
- Dit uitvoeringsbeleid is ontworpen voor configuraties waarin een PowerShellscript is ingebouwd in een grotere toepassing of voor configuraties waarin PowerShell de basis vormt voor een programma dat een eigen beveiligingsmodel heeft.

### <a name="default"></a>Standaard

- Hiermee stelt u het standaard uitvoeringsbeleid in.
- **Beperkt** voor Windows-clients.
- **RemoteSigned** voor Windows-servers.

### <a name="remotesigned"></a>RemoteSigned

- Het standaard uitvoeringsbeleid voor Windows Server-computers.
- Scripts kunnen worden uitgevoerd.
- Vereist een digitale handtekening van een vertrouwde uitgever op scripts en configuratiebestanden die worden gedownload van het Internet, waaronder e-mail en chat Programma's.
- Vereist geen digitale handtekeningen voor scripts die zijn geschreven op de lokale computer en niet vanaf internet zijn gedownload.
- Voert scripts uit die zijn gedownload van het internet en niet zijn ondertekend, als de blokkering van de scripts is opgeheven, bijvoorbeeld door gebruik te maken van de `Unblock-File` cmdlet.
- Risico's voor het uitvoeren van niet-ondertekende scripts uit andere bronnen dan het internet en ondertekende scripts die schadelijk kunnen zijn.

### <a name="restricted"></a>Beperkt

- Het standaarduitvoerings beleid voor Windows-client computers.
- Maakt afzonderlijke opdrachten mogelijk, maar staat geen scripts toe.
- Hiermee wordt voor komen dat alle scriptbestanden worden uitgevoerd, inclusief opmaak- en configuratiebestanden ( `.ps1xml` ), module scriptbestanden ( `.psm1` ) en PowerShellprofielen ( `.ps1` ).

### <a name="undefined"></a>Undefined

- Er is geen uitvoeringsbeleid ingesteld in het huidige bereik.
- Als het uitvoeringsbeleid in alle bereiken niet is **gedefinieerd** , wordt het effectief uitvoeringsbeleid **beperkt** voor Windows-clients en **RemoteSigned** voor Windows Server.

### <a name="unrestricted"></a>Onbeperkt

- Het standaard uitvoeringsbeleid voor niet-Windows-computers en kan niet worden gewijzigd.
- Niet-ondertekende scripts kunnen worden uitgevoerd. Er is een risico op het uitvoeren van schadelijke scripts.
- Waarschuwt de gebruiker voordat scripts en configuratiebestanden worden uitgevoerd die niet afkomstig zijn uit de zone Lokaal intranet.

> [!NOTE]
> Op systemen die geen UNC-paden (Universal Naming Convention) van Internet paden onderscheiden, mogen scripts die door een UNC-pad worden geïdentificeerd, mogelijk niet worden uitgevoerd met het **RemoteSigned** -uitvoerings beleid.

## <a name="execution-policy-scope"></a>Bereik van uitvoerings beleid

U kunt een uitvoeringsbeleid instellen dat alleen effectief is in een bepaald bereik.

De geldige waarden voor **Scope** zijn **MachinePolicy** , **User Policy** , **process** , **CurrentUser** en **LocalMachine**. **LocalMachine** is de standaardinstelling bij het instellen van een uitvoeringsbeleid.

De **bereik**waarden worden weergegeven in volgorde van prioriteit. Het beleid dat prioriteit krijgt, is effectief in de huidige sessie, zelfs als een meer beperkend beleid is ingesteld op een lager niveau van prioriteit.

Zie [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)voor meer informatie.

### <a name="machinepolicy"></a>MachinePolicy

Ingesteld door een groepsbeleid voor alle gebruikers van de computer.

### <a name="userpolicy"></a>User Policy

Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.

### <a name="process"></a>Proces

Het **proces** bereik is alleen van invloed op de huidige Power shell-sessie. Het uitvoeringsbeleid wordt opgeslagen in de omgevings variabele in `$env:PSExecutionPolicyPreference` plaats van het Register. Wanneer de PowerShellsessie wordt gesloten, worden de variabele en de waarde verwijderd.

### <a name="currentuser"></a>CurrentUser

Het uitvoeringsbeleid is alleen van invloed op de huidige gebruiker. Deze wordt opgeslagen in de registersubsleutel **HKEY_CURRENT_USER** .

### <a name="localmachine"></a>LocalMachine

Het uitvoeringsbeleid is van invloed op alle gebruikers op de huidige computer. Deze wordt opgeslagen in de registersubsleutel **HKEY_LOCAL_MACHINE** .

## <a name="managing-the-execution-policy-with-powershell"></a>Het uitvoerings beleid beheren met Power shell

Gebruik de cmdlet om het effectief uitvoeringsbeleid voor de huidige Power shell-sessie te verkrijgen `Get-ExecutionPolicy` .

Met de volgende opdracht wordt het effectief uitvoeringsbeleid opgehaald:

```powershell
Get-ExecutionPolicy
```

Ga als volgt te werk om alle uitvoeringsbeleidsregels op te halen die van invloed zijn op de huidige sessie en deze weer te geven in volgorde:

```powershell
Get-ExecutionPolicy -List
```

Het resultaat ziet er ongeveer uit als in de volgende voorbeeld uitvoer:

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

In dit geval is het effectief uitvoeringsbeleid **RemoteSigned** omdat het uitvoerings beleid voor de huidige gebruiker voor rang heeft op het uitvoeringsbeleid dat is ingesteld voor de lokale computer.

Als u wilt ophalen van het uitvoeringsbeleid dat is ingesteld voor een bepaald bereik, gebruikt u de parameter **bereik** van `Get-ExecutionPolicy` .

Met de volgende opdracht wordt bijvoorbeeld het uitvoeringsbeleid voor het bereik **CurrentUser** opgehaald:

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a>Het uitvoeringsbeleid wijzigen

Als u het PowerShell uitvoeringsbeleid wilt wijzigen op uw Windows-computer, gebruikt u de `Set-ExecutionPolicy` cmdlet. De wijziging is direct van kracht. U hoeft PowerShell niet opnieuw te starten.

Als u het uitvoeringsbeleid voor de scopes **LocalMachine** of de **CurrentUser** instelt, wordt de wijziging opgeslagen in het Register en blijft deze geldig totdat u deze opnieuw wijzigt.

Als u het uitvoeringsbeleid voor het **proces** bereik instelt, wordt het niet opgeslagen in het Register. Het uitvoeringsbeleid wordt bewaard totdat het huidige proces en alle onderliggende processen worden gesloten.

> [!NOTE]
> In Windows Vista en latere versies van Windows, voor het uitvoeren van opdrachten waarmee het uitvoeringsbeleid voor de lokale computer wordt gewijzigd, **LocalMachine** bereik, start Power shell met de optie **als administrator uitvoeren** .

Het uitvoeringsbeleid wijzigen:

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

Bijvoorbeeld:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

Het uitvoerings beleid instellen in een bepaald bereik:

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

Bijvoorbeeld:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Een opdracht voor het wijzigen van een uitvoeringsbeleid kan slagen, maar nog steeds niet het daad werkelijke uitvoeringsbeleid wijzigen.

Een opdracht waarmee het uitvoeringsbeleid voor de lokale computer wordt ingesteld, kan bijvoorbeeld slagen, maar worden overschreven door het uitvoeringsbeleid voor de huidige gebruiker.

### <a name="remove-the-execution-policy"></a>Het uitvoeringsbeleid verwijderen

Als u het uitvoeringsbeleid voor een bepaald bereik wilt verwijderen, stelt u het uitvoeringsbeleid in op **ongedefinieerd**.

U kunt bijvoorbeeld het uitvoeringsbeleid voor alle gebruikers van de lokale computer verwijderen:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

Het uitvoeringsbeleid voor een **Scope** verwijderen:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

Als er geen uitvoeringsbeleid is ingesteld in een bereik, wordt het effectief uitvoeringsbeleid **beperkt**. Dit is de standaardinstelling voor Windows-clients.

### <a name="set-a-different-policy-for-one-session"></a>Een ander beleid voor één sessie instellen

U kunt de parameter **ExecutionPolicy** van **pwsh.exe** gebruiken om een uitvoeringsbeleid voor een nieuwe PowerShellsessie in te stellen. Het beleid is alleen van invloed op de huidige sessie en onderliggende sessies.

Als u het uitvoeringsbeleid voor een nieuwe sessie wilt instellen, start u PowerShell op de opdracht regel, zoals **cmd.exe** of vanuit PowerShell. Vervolgens gebruikt u de parameter **ExecutionPolicy** van **pwsh.exe** om het uitvoeringsbeleid in te stellen.

Bijvoorbeeld:

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

Het uitvoeringsbeleid dat u instelt, wordt niet opgeslagen in het Register. In plaats daarvan wordt het opgeslagen in de `$env:PSExecutionPolicyPreference` omgevingsvariabele. De variabele wordt verwijderd wanneer u de sessie sluit waarin het beleid is ingesteld. U kunt het beleid niet wijzigen door de waarde van de variabele te bewerken.

Tijdens de sessie heeft het uitvoeringsbeleid dat is ingesteld voor de sessie voorrang op een uitvoeringsbeleid dat is ingesteld in het Register voor de lokale computer of de huidige gebruiker. Het heeft echter geen voorrang op het uitvoeringsbeleid dat is ingesteld met behulp van een groepsbeleid.

## <a name="use-group-policy-to-manage-execution-policy"></a>Het uitvoeringsbeleid beheren met groepsbeleid

U kunt de instelling **Script Execution Groepsbeleid inschakelen** gebruiken om het uitvoeringsbeleid van computers in uw onderneming te beheren. De instelling groepsbeleid overschrijft het uitvoeringsbeleid dat in PowerShell in alle bereiken is ingesteld.

De beleidsinstellingen **voor het uitvoeren van scripts** worden als volgt ingeschakeld:

- Als u het **uitvoeren van scripts** uitschakelt, worden scripts niet uitgevoerd. Dit is gelijk aan het beleid voor **beperkte** uitvoering.
- Als u het **uitvoeren van scripts** inschakelen inschakelt, kunt u een uitvoeringsbeleid selecteren. De groepsbeleidinstellingen zijn gelijk aan de volgende beleidsinstellingen voor uitvoering:

  | Groepsbeleid                                  | Uitvoeringsbeleid |
  | --------------------------------------------- | ---------------- |
  | Alle scripts toestaan                             | Onbeperkt     |
  | Lokale scripts en externe ondertekende scripts toestaan | RemoteSigned     |
  | Alleen ondertekende scripts toestaan                     | Alles ondertekend        |

- Als het **uitvoeren van scripts** niet is geconfigureerd, heeft dit geen effect. Het uitvoerings beleid dat is ingesteld in Power shell is effectief.

De bestanden PowerShellExecutionPolicy. adm en PowerShellExecutionPolicy. ADMX Voeg het beleid **voor het uitvoeren van scripts** voor de computerconfiguratie en gebruikersconfiguratie knooppunten in Groepsbeleid editor in de volgende paden toe.

Voor Windows XP en Windows Server 2003:

Gebruikersconfiguratie\beheersjablonen\windows-onderdelen\Windows Power shell voor beheer

Voor Windows Vista en latere versies van Windows:

Beheer Templates\Classic Beheersjablonen \
Windows Gebruikersconfiguratie\beheersjablonen\windows-onderdelen\Windows Power shell

Beleidsregels die in het knooppunt computerconfiguratie zijn ingesteld, hebben voorrang op beleidsregels die zijn ingesteld in het knooppunt gebruikersconfiguratie.

Zie [about_Group_Policy_Settings](about_Group_Policy_Settings.md)voor meer informatie.

### <a name="execution-policy-precedence"></a>Prioriteit van uitvoeringsbeleid

Bij het bepalen van het effectief uitvoeringsbeleid voor een sessie, evalueert PowerShell het uitvoeringsbeleid in de volgende volgorde:

- Groepsbeleid: MachinePolicy
- Groepsbeleid: User Policy
- Uitvoeringsbeleid: proces (of `pwsh.exe -ExecutionPolicy` )
- Uitvoeringsbeleid: CurrentUser
- Uitvoeringsbeleid: LocalMachine

## <a name="manage-signed-and-unsigned-scripts"></a>Ondertekende en niet-ondertekende scripts beheren

In Windows kunnen Programma's zoals Internet Explorer en Microsoft Edge een alternatieve gegevensstroom toevoegen aan bestanden die worden gedownload. Hiermee markeert u het bestand als ' afkomstig van Internet '. Als uw PowerShell uitvoeringsbeleid **RemoteSigned** is, voert PowerShell geen niet-ondertekende scripts uit die zijn gedownload van Internet en die e-mail-en chat Programma's bevatten.

U kunt het script ondertekenen of ervoor kiezen om een niet-ondertekend script uit te voeren zonder het uitvoeringsbeleid te wijzigen.

Vanaf Power Shell 3,0 kunt u de **Stream** -parameter van de `Get-Item` cmdlet gebruiken om bestanden te detecteren die zijn geblokkeerd omdat deze zijn gedownload van het internet. Gebruik de `Unblock-File` cmdlet voor het blok keren van de scripts zodat u deze in Power shell kunt uitvoeren.

Zie [about_Signing](about_Signing.md), [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)en [deblokkering-bestand](xref:Microsoft.PowerShell.Utility.Unblock-File)voor meer informatie.

> [!NOTE]
> Andere methoden voor het downloaden van bestanden kunnen de bestanden niet markeren als afkomstig van de zone Internet. Voorbeelden zijn:
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a>Uitvoerings beleid op Windows Server Core en Window nano server

Wanneer PowerShell 6 onder bepaalde voor waarden wordt uitgevoerd op Windows Server Core of Windows nano server, kan het uitvoeringsbeleid mislukken met de volgende fout:

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

PowerShell gebruikt Api's in Windows-Desktopshell ( `explorer.exe` ) om de zone van een scriptbestand te valideren. De Windows-shell is niet beschikbaar op Windows Server Core en Windows nano server.

U kunt deze fout ook vinden op elk Windows systeem als de Windows Desktopshell niet beschikbaar is of niet meer reageert. Tijdens het aanmelden kan bijvoorbeeld een PowerShell aanmeldingsscript worden gestart voordat het Windows bureaublad gereed is, wat een fout heeft veroorzaakt.

Voor het uitvoeren van een uitvoeringsbeleid voor **bypass** of **Alles ondertekend** is geen zone controle vereist waarmee het probleem wordt voor komen.

## <a name="see-also"></a>Zie ook

[about_Environment_Variables](about_Environment_Variables.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Signing](about_Signing.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Get-item](xref:Microsoft.PowerShell.Management.Get-Item)

[Help bij Pwsh-console](about_pwsh.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Blok kering van bestand opheffen](xref:Microsoft.PowerShell.Utility.Unblock-File)

