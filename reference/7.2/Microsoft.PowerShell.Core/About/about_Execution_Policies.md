---
description: Hierin worden het Power shell-uitvoerings beleid beschreven en wordt uitgelegd hoe u deze beheert.
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 1a2b8458b39233f96d47a52e3fea21b31e9b3c42
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706104"
---
# <a name="about-execution-policies"></a>Over uitvoerings beleid

## <a name="short-description"></a>Korte beschrijving
Hierin worden het Power shell-uitvoerings beleid beschreven en wordt uitgelegd hoe u deze beheert.

## <a name="long-description"></a>Lange beschrijving

Het uitvoerings beleid van Power shell is een veiligheids functie die de voor waarden bepaalt waaronder Power shell configuratie bestanden laadt en scripts uitvoert. Deze functie helpt de uitvoering van schadelijke scripts te voor komen.

Op een Windows-computer kunt u een uitvoerings beleid voor de lokale computer instellen, voor de huidige gebruiker of voor een bepaalde sessie. U kunt ook een groepsbeleid instelling gebruiken om uitvoerings beleid in te stellen voor computers en gebruikers.

Uitvoerings beleid voor de lokale computer en de huidige gebruiker worden opgeslagen in het REGI ster. U hoeft geen uitvoerings beleid in te stellen in uw Power shell-profiel.
Het uitvoerings beleid voor een bepaalde sessie wordt alleen in het geheugen opgeslagen en gaat verloren wanneer de sessie wordt gesloten.

Het uitvoerings beleid is geen beveiligings systeem dat gebruikers acties beperkt. Gebruikers kunnen bijvoorbeeld eenvoudig een beleid overs Laan door de inhoud van het script te typen op de opdracht regel wanneer ze geen script kunnen uitvoeren. Het uitvoerings beleid helpt in plaats daarvan basis regels in te stellen en voor komt dat ze per ongeluk worden geschonden.

Op niet-Windows-computers is het standaard uitvoerings beleid **onbeperkt** en kan het niet worden gewijzigd. De `Set-ExecutionPolicy` cmdlet is beschikbaar, maar in Power shell wordt een console bericht weer gegeven dat niet wordt ondersteund. Hoewel `Get-ExecutionPolicy` retourneert **onbeperkt** op niet-Windows-platforms, komt het gedrag werkelijk overeen met **bypass** , omdat deze platformen de Windows-beveiligings zones niet implementeren.

## <a name="powershell-execution-policies"></a>Power shell-uitvoerings beleid

Het afdwingen van deze beleids regels vindt alleen plaats op Windows-platforms. Het Power shell-uitvoerings beleid is als volgt:

### <a name="allsigned"></a>Alles ondertekend

- Scripts kunnen worden uitgevoerd.
- Vereist dat alle scripts en configuratie bestanden worden ondertekend door een vertrouwde uitgever, met inbegrip van scripts die u op de lokale computer schrijft.
- Hiermee wordt u gevraagd of u scripts van uitgevers wilt uitvoeren die u nog niet hebt geclassificeerd als vertrouwd of niet-vertrouwde.
- Risico's die ondertekend zijn, maar schadelijke scripts.

### <a name="bypass"></a>Bypass

- Er is niets geblokkeerd en er zijn geen waarschuwingen of prompts.
- Dit uitvoerings beleid is ontworpen voor configuraties waarin een Power shell-script is ingebouwd in een grotere toepassing of voor configuraties waarin Power shell de basis vormt voor een programma dat een eigen beveiligings model heeft.

### <a name="default"></a>Standaard

- Hiermee stelt u het standaard uitvoerings beleid in.
- **Beperkt** voor Windows-clients.
- **RemoteSigned** voor Windows-servers.

### <a name="remotesigned"></a>RemoteSigned

- Het standaard uitvoerings beleid voor Windows Server-computers.
- Scripts kunnen worden uitgevoerd.
- Vereist een digitale hand tekening van een vertrouwde uitgever op scripts en configuratie bestanden die worden gedownload van het Internet, waaronder e-mail en chat Programma's.
- Vereist geen digitale hand tekeningen voor scripts die zijn geschreven op de lokale computer en niet vanaf internet zijn gedownload.
- Voert scripts uit die zijn gedownload van het internet en niet zijn ondertekend, als de blok kering van de scripts is opgeheven, bijvoorbeeld door gebruik te maken van de `Unblock-File` cmdlet.
- Risico's voor het uitvoeren van niet-ondertekende scripts uit andere bronnen dan het internet en ondertekende scripts die schadelijk kunnen zijn.

### <a name="restricted"></a>Beperkt

- Het standaard uitvoerings beleid voor Windows-client computers.
- Maakt afzonderlijke opdrachten mogelijk, maar staat geen scripts toe.
- Hiermee wordt voor komen dat alle script bestanden worden uitgevoerd, inclusief opmaak-en configuratie bestanden ( `.ps1xml` ), module script bestanden ( `.psm1` ) en Power shell-profielen ( `.ps1` ).

### <a name="undefined"></a>Undefined

- Er is geen uitvoerings beleid ingesteld in het huidige bereik.
- Als het uitvoerings beleid in alle bereiken niet is **gedefinieerd**, wordt het effectief uitvoerings beleid **beperkt** voor Windows-clients en **RemoteSigned** voor Windows Server.

### <a name="unrestricted"></a>Onbeperkt

- Het standaard uitvoerings beleid voor niet-Windows-computers en kan niet worden gewijzigd.
- Niet-ondertekende scripts kunnen worden uitgevoerd. Er is een risico op het uitvoeren van schadelijke scripts.
- Waarschuwt de gebruiker voordat scripts en configuratie bestanden worden uitgevoerd die niet afkomstig zijn uit de zone Lokaal intranet.

> [!NOTE]
> Op systemen die geen UNC-paden (Universal Naming Convention) van Internet paden onderscheiden, mogen scripts die door een UNC-pad worden geïdentificeerd, mogelijk niet worden uitgevoerd met het **RemoteSigned** -uitvoerings beleid.

## <a name="execution-policy-scope"></a>Bereik van uitvoerings beleid

U kunt een uitvoerings beleid instellen dat alleen effectief is in een bepaald bereik.

De geldige waarden voor **Scope** zijn **MachinePolicy**, **User Policy**, **process**, **CurrentUser** en **LocalMachine**. **LocalMachine** is de standaard instelling bij het instellen van een uitvoerings beleid.

De **bereik** waarden worden weer gegeven in volg orde van prioriteit. Het beleid dat prioriteit krijgt, is effectief in de huidige sessie, zelfs als een meer beperkend beleid is ingesteld op een lager niveau van prioriteit.

Zie [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)voor meer informatie.

### <a name="machinepolicy"></a>MachinePolicy

Ingesteld door een groepsbeleid voor alle gebruikers van de computer.

### <a name="userpolicy"></a>User Policy

Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.

### <a name="process"></a>Proces

Het **proces** bereik is alleen van invloed op de huidige Power shell-sessie. Het uitvoerings beleid wordt opgeslagen in de omgevings variabele in `$env:PSExecutionPolicyPreference` plaats van het REGI ster. Wanneer de Power shell-sessie wordt gesloten, worden de variabele en de waarde verwijderd.

### <a name="currentuser"></a>CurrentUser

Het uitvoerings beleid is alleen van invloed op de huidige gebruiker. Deze wordt opgeslagen in de registersubsleutel **HKEY_CURRENT_USER** .

### <a name="localmachine"></a>LocalMachine

Het uitvoerings beleid is van invloed op alle gebruikers op de huidige computer. Deze wordt opgeslagen in de registersubsleutel **HKEY_LOCAL_MACHINE** .

## <a name="managing-the-execution-policy-with-powershell"></a>Het uitvoerings beleid beheren met Power shell

Gebruik de cmdlet om het effectief uitvoerings beleid voor de huidige Power shell-sessie te verkrijgen `Get-ExecutionPolicy` .

Met de volgende opdracht wordt het effectief uitvoerings beleid opgehaald:

```powershell
Get-ExecutionPolicy
```

Ga als volgt te werk om alle uitvoerings beleidsregels op te halen die van invloed zijn op de huidige sessie en deze weer te geven in volg orde:

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

In dit geval is het effectief uitvoerings beleid **RemoteSigned** omdat het uitvoerings beleid voor de huidige gebruiker voor rang heeft op het uitvoerings beleid dat is ingesteld voor de lokale computer.

Als u wilt ophalen van het uitvoerings beleid dat is ingesteld voor een bepaald bereik, gebruikt u de para meter **bereik** van `Get-ExecutionPolicy` .

Met de volgende opdracht wordt bijvoorbeeld het uitvoerings beleid voor het bereik **CurrentUser** opgehaald:

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a>Het uitvoerings beleid wijzigen

Als u het Power shell-uitvoerings beleid wilt wijzigen op uw Windows-computer, gebruikt u de `Set-ExecutionPolicy` cmdlet. De wijziging is direct van kracht. U hoeft Power shell niet opnieuw te starten.

Als u het uitvoerings beleid voor de scopes **LocalMachine** of de **CurrentUser** instelt, wordt de wijziging opgeslagen in het REGI ster en blijft deze geldig totdat u deze opnieuw wijzigt.

Als u het uitvoerings beleid voor het **proces** bereik instelt, wordt het niet opgeslagen in het REGI ster. Het uitvoerings beleid wordt bewaard totdat het huidige proces en alle onderliggende processen worden gesloten.

> [!NOTE]
> In Windows Vista en latere versies van Windows, voor het uitvoeren van opdrachten waarmee het uitvoerings beleid voor de lokale computer wordt gewijzigd, **LocalMachine** bereik, start Power shell met de optie **als administrator uitvoeren** .

Het uitvoerings beleid wijzigen:

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

Een opdracht voor het wijzigen van een uitvoerings beleid kan slagen, maar nog steeds niet het daad werkelijke uitvoerings beleid wijzigen.

Een opdracht waarmee het uitvoerings beleid voor de lokale computer wordt ingesteld, kan bijvoorbeeld slagen, maar worden overschreven door het uitvoerings beleid voor de huidige gebruiker.

### <a name="remove-the-execution-policy"></a>Het uitvoerings beleid verwijderen

Als u het uitvoerings beleid voor een bepaald bereik wilt verwijderen, stelt u het uitvoerings beleid in op **ongedefinieerd**.

U kunt bijvoorbeeld het uitvoerings beleid voor alle gebruikers van de lokale computer verwijderen:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

Het uitvoerings beleid voor een **Scope** verwijderen:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

Als er geen uitvoerings beleid is ingesteld in een bereik, wordt het effectief uitvoerings beleid **beperkt**. Dit is de standaard instelling voor Windows-clients.

### <a name="set-a-different-policy-for-one-session"></a>Een ander beleid voor één sessie instellen

U kunt de para meter **ExecutionPolicy** van **pwsh.exe** gebruiken om een uitvoerings beleid voor een nieuwe Power shell-sessie in te stellen. Het beleid is alleen van invloed op de huidige sessie en onderliggende sessies.

Als u het uitvoerings beleid voor een nieuwe sessie wilt instellen, start u Power shell op de opdracht regel, zoals **cmd.exe** of vanuit Power shell. vervolgens gebruikt u de para meter **ExecutionPolicy** van **pwsh.exe** om het uitvoerings beleid in te stellen.

Bijvoorbeeld:

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

Het uitvoerings beleid dat u instelt, wordt niet opgeslagen in het REGI ster. In plaats daarvan wordt het opgeslagen in de `$env:PSExecutionPolicyPreference` omgevings variabele. De variabele wordt verwijderd wanneer u de sessie sluit waarin het beleid is ingesteld. U kunt het beleid niet wijzigen door de waarde van de variabele te bewerken.

Tijdens de sessie heeft het uitvoerings beleid dat is ingesteld voor de sessie voor rang op een uitvoerings beleid dat is ingesteld in het REGI ster voor de lokale computer of de huidige gebruiker. Het heeft echter geen voor rang op het uitvoerings beleid dat is ingesteld met behulp van een groepsbeleid.

## <a name="use-group-policy-to-manage-execution-policy"></a>Het uitvoerings beleid beheren met groepsbeleid

U kunt de instelling **Script Execution Groepsbeleid inschakelen** gebruiken om het uitvoerings beleid van computers in uw onderneming te beheren. De instelling groepsbeleid overschrijft het uitvoerings beleid dat in Power shell in alle bereiken is ingesteld.

De beleids instellingen **voor het uitvoeren van scripts** worden als volgt ingeschakeld:

- Als u het **uitvoeren van scripts** uitschakelt, worden scripts niet uitgevoerd. Dit is gelijk aan het beleid voor **beperkte** uitvoering.
- Als u het **uitvoeren van scripts** inschakelen inschakelt, kunt u een uitvoerings beleid selecteren. De groepsbeleid-instellingen zijn gelijk aan de volgende beleids instellingen voor uitvoering:

  | Groepsbeleid                                  | Uitvoerings beleid |
  | --------------------------------------------- | ---------------- |
  | Alle scripts toestaan                             | Onbeperkt     |
  | Lokale scripts en externe ondertekende scripts toestaan | RemoteSigned     |
  | Alleen ondertekende scripts toestaan                     | Alles ondertekend        |

- Als het **uitvoeren van scripts** niet is geconfigureerd, heeft dit geen effect. Het uitvoerings beleid dat is ingesteld in Power shell is effectief.

De bestanden PowerShellExecutionPolicy. adm en PowerShellExecutionPolicy. ADMX Voeg het beleid **voor het uitvoeren van scripts** voor de computer configuratie en gebruikers configuratie knooppunten in Groepsbeleid editor in de volgende paden toe.

Voor Windows XP en Windows Server 2003:

Gebruikersconfiguratie\beheersjablonen\windows-onderdelen\Windows Power shell voor beheer

Voor Windows Vista en latere versies van Windows:

Beheer Templates\Classic Beheersjablonen \
Windows Gebruikersconfiguratie\beheersjablonen\windows-onderdelen\Windows Power shell

Beleids regels die in het knoop punt computer configuratie zijn ingesteld, hebben voor rang op beleids regels die zijn ingesteld in het knoop punt gebruikers configuratie.

Zie [about_Group_Policy_Settings](about_Group_Policy_Settings.md)voor meer informatie.

### <a name="execution-policy-precedence"></a>Prioriteit van uitvoerings beleid

Bij het bepalen van het effectief uitvoerings beleid voor een sessie, evalueert Power shell het uitvoerings beleid in de volgende volg orde:

- Groepsbeleid: MachinePolicy
- Groepsbeleid: User Policy
- Uitvoerings beleid: proces (of `pwsh.exe -ExecutionPolicy` )
- Uitvoerings beleid: CurrentUser
- Uitvoerings beleid: LocalMachine

## <a name="manage-signed-and-unsigned-scripts"></a>Ondertekende en niet-ondertekende scripts beheren

In Windows kunnen Program ma's zoals Internet Explorer en micro soft Edge een alternatieve gegevens stroom toevoegen aan bestanden die worden gedownload. Hiermee markeert u het bestand als ' afkomstig van Internet '. Als uw Power shell-uitvoerings beleid **RemoteSigned** is, voert Power shell geen niet-ondertekende scripts uit die zijn gedownload van Internet en die e-mail-en chat Programma's bevatten.

U kunt het script ondertekenen of ervoor kiezen om een niet-ondertekend script uit te voeren zonder het uitvoerings beleid te wijzigen.

Vanaf Power Shell 3,0 kunt u de **Stream** -para meter van de `Get-Item` cmdlet gebruiken om bestanden te detecteren die zijn geblokkeerd omdat deze zijn gedownload van het internet. Gebruik de `Unblock-File` cmdlet voor het blok keren van de scripts zodat u deze in Power shell kunt uitvoeren.

Zie [about_Signing](about_Signing.md), [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)en [deblokkering-bestand](xref:Microsoft.PowerShell.Utility.Unblock-File)voor meer informatie.

> [!NOTE]
> Andere methoden voor het downloaden van bestanden kunnen de bestanden niet markeren als afkomstig van de zone Internet. Voorbeelden zijn:
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a>Uitvoerings beleid op Windows Server Core en Window nano server

Wanneer Power shell 6 onder bepaalde voor waarden wordt uitgevoerd op Windows Server Core of Windows nano server, kan het uitvoerings beleid mislukken met de volgende fout:

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

Power shell gebruikt Api's in Windows Desktop shell ( `explorer.exe` ) om de zone van een script bestand te valideren. De Windows-shell is niet beschikbaar op Windows Server Core en Windows nano server.

U kunt deze fout ook vinden op elk Windows-systeem als de Windows Desktop shell niet beschikbaar is of niet meer reageert. Tijdens het aanmelden kan bijvoorbeeld een Power shell-aanmeldings script worden gestart voordat het Windows-bureau blad gereed is, wat een fout heeft veroorzaakt.

Voor het uitvoeren van een uitvoerings beleid voor **bypass** of **Alles ondertekend** is geen zone controle vereist waarmee het probleem wordt voor komen.

## <a name="see-also"></a>Zie ook

[about_Environment_Variables](about_Environment_Variables.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Signing](about_Signing.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Get-item](xref:Microsoft.PowerShell.Management.Get-Item)

[Help bij Pwsh-console](about_pwsh.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Blok kering van bestand opheffen](xref:Microsoft.PowerShell.Utility.Unblock-File)

