---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: De tweede hop maken voor externe communicatie met PowerShell
ms.openlocfilehash: 3a9db11726d4c02dc69e52c45da304f7422def39
ms.sourcegitcommit: 843756c8277e7afb874867703963248abc8a6c91
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83439373"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>De tweede hop maken voor externe communicatie met PowerShell

Het ' tweede hop-probleem ' verwijst naar een situatie zoals de volgende:

1. U bent aangemeld bij _Servera_.
2. Vanuit _Servera_start u een externe Power shell-sessie om verbinding te maken met _ServerB_.
3. Een opdracht die u uitvoert op _ServerB_ via uw externe Power shell-sessie probeert toegang te krijgen tot een resource op _ServerC_.
4. De toegang tot de resource op _ServerC_ is geweigerd, omdat de referenties die u hebt gebruikt voor het maken van de externe Power shell-sessie niet zijn door gegeven van _ServerB_ naar _ServerC_.

Er zijn verschillende manieren om dit probleem op te lossen. De volgende tabel bevat de methoden in volg orde van voor keur.

|                      Configuratie                       |                                  Notitie                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| CredSSP                                                  | Het gebruiks gemak en de beveiliging                                      |
| Op resources gebaseerde Kerberos-beperkte overdracht           | Betere beveiliging met een eenvoudigere configuratie                             |
| Beperkte Kerberos-overdracht                          | Hoge beveiliging, maar vereist domein beheerder                         |
| Kerberos-overdracht (onbeperkt)                      | Niet aanbevolen                                                        |
| Just Enough Administration (JEA)                         | Kan de beste beveiliging bieden, maar vereist een gedetailleerdere configuratie |
| PSSessionConfiguration met behulp van runas                       | Eenvoudiger te configureren, maar vereist referentie beheer                |
| Referenties in een `Invoke-Command` script blok door geven | Eenvoudig te gebruiken, maar u moet referenties opgeven                       |

## <a name="credssp"></a>CredSSP

U kunt de [Credential Security Support Provider (CredSSP)][credssp] gebruiken voor verificatie.
CredSSP slaat de referenties op de externe server (_ServerB_) op, zodat u hiermee wordt gebruikgemaakt van aanvallen op referentie diefstal. Als de externe computer is aangetast, heeft de aanvaller toegang tot de referenties van de gebruiker. CredSSP is standaard uitgeschakeld op client-en Server computers. U moet CredSSP alleen inschakelen in de meest vertrouwde omgevingen. Bijvoorbeeld een domein beheerder die verbinding maakt met een domein controller omdat de domein controller zeer vertrouwd is.

Voor meer informatie over beveiligings problemen bij het gebruik van CredSSP voor externe communicatie met Power shell raadpleegt u [Accidental sabotage: wees op de hoogte van CredSSP][beware].

Zie voor meer informatie over aanvallen op het weglaten van referentie dief stal [Pass-the-hash-aanvallen (PtH) en andere referentie diefstal][pth].

Voor een voor beeld van het inschakelen en gebruiken van CredSSP voor externe communicatie met Power shell, raadpleegt u [Power shell-functie voor tweede hop inschakelen met CredSSP][credssp-psblog].

**-Professionals**

- Het werkt voor alle servers met Windows Server 2008 of hoger.

**Nadelen**

- Bevat beveiligings problemen.
- Vereist configuratie van de client-en Server functies.
- Werkt niet met de groep met beveiligde gebruikers. Zie voor meer informatie [beveiligings groep voor beveiligde gebruikers][protected-users].

## <a name="kerberos-constrained-delegation"></a>Beperkte Kerberos-overdracht

U kunt verouderde, beperkte delegering (niet op basis van bronnen) gebruiken om de tweede hop te maken. Configureer beperkte Kerberos-delegering met de optie elk verificatie protocol gebruiken om protocol overgang toe te staan.

**-Professionals**

- Vereist geen speciale code ring
- De referenties zijn niet opgeslagen.

**Nadelen**

- Biedt geen ondersteuning voor de tweede hop voor WinRM.
- Vereist dat domein beheerder toegang heeft om te configureren.
- Moet worden geconfigureerd op het Active Directory-object van de externe server (_ServerB_).
- Beperkt tot één domein. Kan niet tussen domeinen of forests.
- Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.
- U kunt met _ServerB_ een Kerberos-ticket verkrijgen voor _ServerC_ namens de gebruiker zonder tussen komst van de gebruiker.

> [!NOTE]
> Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd. Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts][blog] en [Hulpprogram ma's en instellingen voor Kerberos-verificatie][ktools]voor meer informatie.

## <a name="resource-based-kerberos-constrained-delegation"></a>Op resources gebaseerde Kerberos-beperkte overdracht

Met behulp van beperkte Kerberos-delegering (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het Server object waar de resources zich bevinden. In het tweede hop-scenario dat hierboven wordt beschreven, configureert u _ServerC_ om op te geven waar de gedelegeerde referenties worden geaccepteerd.

**-Professionals**

- De referenties zijn niet opgeslagen.
- Geconfigureerd met Power shell-cmdlets. Er is geen speciale code vereist.
- Vereist geen domein beheerders toegang om te configureren.
- Werkt in verschillende domeinen en forests.

**Nadelen**

- Vereist Windows Server 2012 of hoger.
- Biedt geen ondersteuning voor de tweede hop voor WinRM.
- Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.

> [!NOTE]
> Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd. Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts][blog] en [Hulpprogram ma's en instellingen voor Kerberos-verificatie][ktools]voor meer informatie.

### <a name="example"></a>Voorbeeld

Laten we eens kijken naar een Power shell-voor beeld voor het configureren van beperkte delegering op basis van resources op _ServerC_ om gedelegeerde referenties van een _ServerB_toe te staan. In dit voor beeld wordt ervan uitgegaan dat op alle servers Windows Server 2012 of hoger wordt uitgevoerd en dat er ten minste één domein controller met Windows Server 2012 elk domein is waarvan de servers deel uitmaken.

Voordat u beperkte delegering kunt configureren, moet u de `RSAT-AD-PowerShell` functie toevoegen om de Active Directory Power shell-module te installeren en deze module vervolgens in uw sessie te importeren:

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

Verschillende beschik bare cmdlets hebben nu een **PrincipalsAllowedToDelegateToAccount** -para meter:

```Output
CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

De para meter **PrincipalsAllowedToDelegateToAccount** stelt het Active Directory object kenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**in dat een toegangs beheer lijst (ACL) bevat die aangeeft welke accounts machtigingen hebben voor het delegeren van referenties aan het gekoppelde account (in dit voor beeld is dit het computer account voor _Servera_).

We gaan nu de variabelen instellen die we gebruiken om de servers aan te duiden:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (en dus externe communicatie van Power shell) wordt standaard uitgevoerd als het computer account. U kunt dit zien door te kijken naar de eigenschap **Start** naam van de `winrm` service:

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

Voor _ServerC_ voor het toestaan van delegering vanuit een externe Power shell-sessie op _ServerB_, moeten we de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ instellen op het computer object van _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

De Kerberos- [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches geweigerd-toegangs pogingen (negatieve cache) gedurende 15 minuten. Als _ServerB_ eerder heeft geprobeerd toegang te krijgen tot _ServerC_, moet u de cache op _ServerB_ wissen door de volgende opdracht aan te roepen:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

U kunt de computer ook opnieuw opstarten of u moet ten minste 15 minuten wachten om de cache te wissen.

Nadat u de cache hebt gewist, kunt u code uitvoeren vanuit _Servera_ tot en met _ServerB_ tot _ServerC_:

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

In dit voor beeld `$using` wordt de variabele gebruikt om de `$ServerC` variabele zichtbaar te maken voor _ServerB_.
Zie about_Remote_Variables voor meer informatie over de `$using` variabele [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).

Als u wilt toestaan dat meerdere servers referenties delegeren naar _ServerC_, stelt u de waarde van de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in op een matrix:

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Als u de tweede hop tussen domeinen wilt maken, voegt u een volledig gekwalificeerde domein naam (FQDN) toe van de domein controller van het domein waartoe _ServerB_ behoort:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Als u de bevoegdheid voor het delegeren van referenties wilt verwijderen naar ServerC, stelt u de waarde van de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in op `$null` :

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informatie over op resources gebaseerde Kerberos-beperkte delegering

- [Wat is nieuw in Kerberos-verificatie][whats-new]
- [Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 1, vereenvoudigt][kcd2012-1]
- [Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 2, vereenvoudigt][kcd2012-2]
- [Meer informatie over Kerberos-beperkte overdracht voor Azure Active Directory-toepassingsproxy-implementaties met geïntegreerde Windows-verificatie][kcdpaper]
- [[MS-ADA2] Active Directory schema kenmerken M 2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]
- [[MS-SFU] Kerberos-protocol uitbreidingen: service voor gebruiker en beperkt delegering Protocol 1.3.2 S4U2proxy][MS-SFU]
- [Extern beheer zonder beperkte delegering met behulp van PrincipalsAllowedToDelegateToAccount][remote-admin]

## <a name="kerberos-delegation-unconstrained"></a>Kerberos-overdracht (onbeperkt)

U kunt ook Kerberos-onbeperkte overdracht gebruiken om de tweede hop te maken. Net als alle Kerberos-scenario's worden referenties niet opgeslagen. Deze methode biedt geen ondersteuning voor de tweede hop voor WinRM.

> [!WARNING]
> Deze methode biedt geen controle over waar gedelegeerde referenties worden gebruikt. Het is minder veilig dan CredSSP. Deze methode mag alleen worden gebruikt voor test scenario's.

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

Met JEA kunt u de opdrachten die een beheerder tijdens een Power shell-sessie kan uitvoeren, beperken. Het kan worden gebruikt om het probleem met de tweede hop op te lossen.

Zie [net genoeg beheer](/powershell/scripting/learn/remoting/jea/overview)voor meer informatie over jea.

**-Professionals**

- Geen wachtwoord onderhoud wanneer een virtueel account wordt gebruikt.

**Nadelen**

- Vereist WMF 5,0 of hoger.
- Vereist configuratie op elke tussenliggende server (_ServerB_).

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration met behulp van runas

U kunt een sessie configuratie op _ServerB_ maken en de para meter **RunAsCredential** instellen.

Voor informatie over het gebruik van **PSSessionConfiguration** en **runas** om het probleem met de tweede hop op te lossen, raadpleegt [u een andere oplossing voor externe communicatie met Power shell voor multi-hop][pssessionconfig].

**-Professionals**

- Werkt met een wille keurige server met WMF 3,0 of hoger.

**Nadelen**

- Vereist de configuratie van **PSSessionConfiguration** en **runas** op elke tussenliggende server (_ServerB_).
- Vereist wachtwoord onderhoud bij gebruik van een **runas** -account van het domein

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Referenties binnen een invoke-opdracht-script blok door geven

U kunt referenties door geven binnen de para meter **script Block** van een aanroep naar de cmdlet [invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command) .

**-Professionals**

- Vereist geen speciale server configuratie.
- Werkt op elke server waarop WMF 2,0 of hoger wordt uitgevoerd.

**Nadelen**

- Hiervoor is een vreemd-code techniek vereist.
- Bij het uitvoeren van WMF 2,0 is een andere syntaxis vereist voor het door geven van argumenten aan een externe sessie.

### <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe de referenties worden door gegeven in een script blok voor de **opdracht invoke** :

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>Zie ook

[Beveiligingsoverwegingen bij externe communicatie met PowerShell](WinRMSecurity.md)

<!-- link references -->
[blog]: /archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts
[ktools]: /previous-versions/windows/it-pro/windows-server-2003/cc738673(v=ws.10)
[credssp]: /windows/win32/secauthn/credential-security-support-provider
[beware]: https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp
[pth]: https://www.microsoft.com/download/details.aspx?id=36036
[credssp-psblog]: https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/
[whats-new]: /previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11)
[kcd2012-1]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1
[kcd2012-2]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2
[kcdpaper]: https://aka.ms/kcdpaper
[MS-ADA2]: /openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405
[MS-SFU]: /openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a
[remote-admin]: /archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount
[pssessionconfig]: /archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting
[protected-users]: /windows-server/security/credentials-protection-and-management/protected-users-security-group
