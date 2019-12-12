---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: De tweede hop maken voor externe communicatie met PowerShell
ms.openlocfilehash: 567d75009f7d53e9e95e5480b275ec3991cfb9f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417625"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>De tweede hop maken voor externe communicatie met PowerShell

Het ' tweede hop-probleem ' verwijst naar een situatie zoals de volgende:

1. U bent aangemeld bij _Servera_.
2. Vanuit _Servera_start u een externe Power shell-sessie om verbinding te maken met _ServerB_.
3. Een opdracht die u uitvoert op _ServerB_ via uw externe Power shell-sessie probeert toegang te krijgen tot een resource op _ServerC_.
4. De toegang tot de resource op _ServerC_ is geweigerd, omdat de referenties die u hebt gebruikt voor het maken van de externe Power shell-sessie niet zijn door gegeven van _ServerB_ naar _ServerC_.

Er zijn verschillende manieren om dit probleem op te lossen. In dit onderwerp bekijken we een aantal van de populairste oplossingen voor het probleem met de tweede hop.

## <a name="credssp"></a>CredSSP

U kunt de [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) gebruiken voor verificatie. CredSSP slaat de referenties op de externe server (_ServerB_) op, zodat u hiermee wordt gebruikgemaakt van aanvallen op referentie diefstal. Als de externe computer is aangetast, heeft de aanvaller toegang tot de referenties van de gebruiker. CredSSP is standaard uitgeschakeld op client-en Server computers. U moet CredSSP alleen inschakelen in de meest vertrouwde omgevingen. Bijvoorbeeld een domein beheerder die verbinding maakt met een domein controller omdat de domein controller zeer vertrouwd is.

Voor meer informatie over beveiligings problemen bij het gebruik van CredSSP voor externe communicatie met Power shell raadpleegt u [Accidental sabotage: wees op de hoogte van CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Zie voor meer informatie over aanvallen op het weglaten van referentie dief stal [Pass-the-hash-aanvallen (PtH) en andere referentie diefstal](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Voor een voor beeld van het inschakelen en gebruiken van CredSSP voor externe communicatie met Power shell raadpleegt [u CredSSP gebruiken om het probleem met de tweede hop op te lossen](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Voordelen

- Het werkt voor alle servers met Windows Server 2008 of hoger.

### <a name="cons"></a>Nadelen

- Bevat beveiligings problemen.
- Vereist configuratie van de client-en Server functies.

## <a name="kerberos-delegation-unconstrained"></a>Kerberos-overdracht (onbeperkt)

U kunt ook Kerberos-onbeperkte overdracht gebruiken om de tweede hop te maken. Deze methode biedt echter geen controle over waar gedelegeerde referenties worden gebruikt.

>**Opmerking:** Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd. Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Hulpprogram ma's en instellingen voor Kerberos-verificatie](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) voor meer informatie.

### <a name="pros"></a>Voordelen

- Vereist geen speciale code ring.

### <a name="cons"></a>Nadelen

- Biedt geen ondersteuning voor de tweede hop voor WinRM.
- Biedt geen controle over waar referenties worden gebruikt, waardoor een beveiligings probleem wordt opgelost.

## <a name="kerberos-constrained-delegation"></a>Kerberos-beperkte overdracht

U kunt verouderde, beperkte delegering (niet op basis van bronnen) gebruiken om de tweede hop te maken. Configureer beperkte Kerberos-delegering met de optie elk verificatie protocol gebruiken om protocol overgang toe te staan.

> [!NOTE]
> Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd. Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Hulpprogram ma's en instellingen voor Kerberos-verificatie](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) voor meer informatie.

### <a name="pros"></a>Voordelen

- Vereist geen speciale code ring

### <a name="cons"></a>Nadelen

- Biedt geen ondersteuning voor de tweede hop voor WinRM.
- Moet worden geconfigureerd op het Active Directory-object van de externe server (_ServerB_).
- Beperkt tot één domein. Kan niet tussen domeinen of forests.
- Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.

## <a name="resource-based-kerberos-constrained-delegation"></a>Op resources gebaseerde Kerberos-beperkte overdracht

Met behulp van beperkte Kerberos-delegering (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het Server object waar de resources zich bevinden.
In het tweede hop-scenario dat hierboven wordt beschreven, configureert u _ServerC_ om op te geven waar de gedelegeerde referenties worden geaccepteerd.

>**Opmerking:** Active Directory accounts met het **account is vertrouwelijk en kan niet worden** overgedragen, kan niet worden gedelegeerd. Zie [Security Focus: analyse van het account is vertrouwelijk en kan niet worden gedelegeerd voor bevoegde accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Hulpprogram ma's en instellingen voor Kerberos-verificatie](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) voor meer informatie.

### <a name="pros"></a>Voordelen

- De referenties zijn niet opgeslagen.
- Relatief eenvoudig te configureren met behulp van Power shell-cmdlets--geen speciale code ring vereist.
- Er is geen speciale domein toegang vereist.
- Werkt in verschillende domeinen en forests.
- Power shell-code.

### <a name="cons"></a>Nadelen

- Vereist Windows Server 2012 of hoger.
- Biedt geen ondersteuning voor de tweede hop voor WinRM.
- Vereist rechten om objecten en Spn's (Service Principal Names) bij te werken.

### <a name="example"></a>Voorbeeld

We kijken naar een Power shell-voor beeld dat op resources gebaseerde beperkte delegering op _ServerC_ zodanig configureert dat gedelegeerde referenties van een _ServerB_worden toegestaan.
In dit voor beeld wordt ervan uitgegaan dat op alle servers Windows Server 2012 of hoger wordt uitgevoerd en dat er ten minste één domein controller met Windows Server 2012 elk domein is waarvan de servers deel uitmaken.

Voordat u beperkte delegering kunt configureren, moet u de functie `RSAT-AD-PowerShell` toevoegen om de Active Directory Power shell-module te installeren en deze module vervolgens in uw sessie te importeren:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Verschillende beschik bare cmdlets hebben nu een **PrincipalsAllowedToDelegateToAccount** -para meter:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

De para meter **PrincipalsAllowedToDelegateToAccount** stelt het Active Directory object kenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**in dat een toegangs beheer lijst (ACL) bevat die aangeeft welke accounts machtigingen hebben voor het delegeren van referenties aan het gekoppelde account (in dit voor beeld is dit het computer account voor de _Server_).

We gaan nu de variabelen instellen die we gebruiken om de servers aan te duiden:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (en dus externe communicatie van Power shell) wordt standaard uitgevoerd als het computer account. U kunt dit zien door te kijken naar de eigenschap **Start** naam van de `winrm`-service:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Voor _ServerC_ om delegering vanuit een externe Power shell-sessie toe te staan op _ServerB_, wordt de toegang verleend door de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in te stellen op het computer object van _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

De Kerberos [-Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches weigert toegangs pogingen (negatieve cache) gedurende 15 minuten. Als _ServerB_ eerder heeft geprobeerd toegang te krijgen tot _ServerC_, moet u de cache op _ServerB_ wissen door de volgende opdracht aan te roepen:

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

In dit voor beeld wordt de variabele `$using` gebruikt om de `$ServerC`-variabele zichtbaar te maken voor _ServerB_. Zie [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx)voor meer informatie over de variabele `$using`.

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

Als u de bevoegdheid voor het delegeren van referenties wilt verwijderen naar ServerC, stelt u de waarde van de para meter **PrincipalsAllowedToDelegateToAccount** op _ServerC_ in op `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informatie over op resources gebaseerde Kerberos-beperkte delegering

- [Wat is er nieuw in Kerberos-verificatie](https://technet.microsoft.com/library/hh831747.aspx)
- [Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 1, vereenvoudigt](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Hoe Windows Server 2012 de knel punt van Kerberos-beperkte overdracht, deel 2, vereenvoudigt](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Meer informatie over Kerberos-beperkte overdracht voor Azure Active Directory-toepassingsproxy-implementaties met geïntegreerde Windows-verificatie](https://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory schema kenmerken M 2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)
- [[MS-SFU]: Kerberos protocol Extensions: Service for User en congebonden delegering Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)
- [Op resources gebaseerde Kerberos-beperkte overdracht](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Extern beheer zonder beperkte delegering met behulp van PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration met behulp van runas

U kunt een sessie configuratie op _ServerB_ maken en de para meter **RunAsCredential** instellen.

Voor informatie over het gebruik van PSSessionConfiguration en Runas om het probleem met de tweede hop op te lossen, raadpleegt [u een andere oplossing voor externe communicatie met Power shell voor multi-hop](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Voordelen

- Werkt met een wille keurige server met WMF 3,0 of hoger.

### <a name="cons"></a>Nadelen

- Vereist de configuratie van **PSSessionConfiguration** en **runas** op elke tussenliggende server (_ServerB_).
- Vereist wachtwoord onderhoud bij gebruik van een **runas** -account van het domein

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

Met JEA kunt u de opdrachten die een beheerder tijdens een Power shell-sessie kan uitvoeren, beperken. Het kan worden gebruikt om het probleem met de tweede hop op te lossen.

Zie [net genoeg beheer](/powershell/scripting/learn/remoting/jea/overview)voor meer informatie over jea.

### <a name="pros"></a>Voordelen

- Geen wachtwoord onderhoud wanneer een virtueel account wordt gebruikt.

### <a name="cons"></a>Nadelen

- Vereist WMF 5,0 of hoger.
- Vereist configuratie op elke tussenliggende server (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Referenties binnen een invoke-opdracht-script blok door geven

U kunt referenties door geven binnen de para meter **script Block** van een aanroep naar de cmdlet [invoke-opdracht](/powershell/module/microsoft.powershell.core/invoke-command) .

### <a name="pros"></a>Voordelen

- Vereist geen speciale server configuratie.
- Werkt op elke server waarop WMF 2,0 of hoger wordt uitgevoerd.

### <a name="cons"></a>Nadelen

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
