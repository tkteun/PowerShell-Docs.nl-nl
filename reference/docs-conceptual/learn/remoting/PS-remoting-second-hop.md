---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De tweede hop maken in PowerShell voor externe toegang
ms.openlocfilehash: 06ca43e3e0524d89ec6f66f6553c4c75072beaf3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403989"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>De tweede hop maken in PowerShell voor externe toegang

Het "tweede hop '-probleem verwijst naar een situatie als volgt uit:

1. U bent aangemeld bij _ServerA_.
2. Van _ServerA_, u verbinding maken met een externe PowerShell-sessie starten _ServerB_.
3. Een opdracht die u uitvoert op _ServerB_ via uw externe communicatie van PowerShell sessie probeert te krijgen tot een resource op _ServerC_.
4. Toegang tot de resource op _ServerC_ is geweigerd omdat de referenties die u gebruikt voor het maken van de externe communicatie van PowerShell-sessie niet worden doorgegeven van _ServerB_ naar _ServerC_.

Er zijn verschillende manieren om dit probleem te verhelpen. In dit onderwerp bekijken we op verschillende van de meest populaire oplossingen voor het tweede hop-probleem.

## <a name="credssp"></a>CredSSP

U kunt de [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) voor verificatie. CredSSP in de cache opgeslagen referenties op de externe server (_ServerB_), zodat u maximaal referentie diefstal aanvallen met behulp van deze opent. Als de externe computer is geknoeid, heeft de aanvaller heeft toegang tot de referenties van de gebruiker. CredSSP is standaard uitgeschakeld in zowel client als server-computers. Alleen in de meest vertrouwde omgevingen moet u CredSSP inschakelen. Bijvoorbeeld, een domeinbeheerder verbinding te maken met een domeincontroller, omdat de domeincontroller zeer vertrouwd wordt.

Zie voor meer informatie over problemen met de beveiliging bij het gebruik van CredSSP voor externe communicatie van PowerShell, [per ongeluk Sabotage: Houd er rekening mee CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Zie voor meer informatie over referenties diefstal aanvallen [Mitigating Pass-the-Hash (PtH) aanvallen en andere diefstal van referenties](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Zie voor een voorbeeld van hoe u kunt inschakelen en gebruiken van CredSSP voor externe communicatie van PowerShell, [CredSSP met behulp van de tweede hop-probleem op te lossen](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Voordelen

- Dit werkt voor alle servers met Windows Server 2008 of hoger.

### <a name="cons"></a>Nadelen

- Beveiligingsproblemen heeft.
- Configuratie van de client- en -functies vereist.

## <a name="kerberos-delegation-unconstrained"></a>Kerberos-overdracht (een)

U kunt ook een Kerberos-overdracht gebruikt om de tweede hop maken. Deze methode biedt echter geen controle over waarop gedelegeerde referenties worden gebruikt.

>**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden gedelegeerd. Zie voor meer informatie, [Focus van de beveiliging: Analyse van 'Account is vertrouwelijk en kan niet worden overgedragen' voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Voordelen

- Vereist geen speciale codering.

### <a name="cons"></a>Nadelen

- Biedt geen ondersteuning voor de tweede hop voor WinRM.
- Biedt geen controle over waarop referenties worden gebruikt, het maken van een beveiligingsprobleem.

## <a name="kerberos-constrained-delegation"></a>Kerberos-beperkte overdracht

Verouderde beperkte delegering (geen resource-indeling) kunt u de tweede hop maken.

>**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden gedelegeerd. Zie voor meer informatie, [Focus van de beveiliging: Analyse van 'Account is vertrouwelijk en kan niet worden overgedragen' voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Voordelen

- Vereist geen speciale codering

### <a name="cons"></a>Nadelen

- Biedt geen ondersteuning voor de tweede hop voor WinRM.
- Moet worden geconfigureerd op de Active Directory-object van de externe server (_ServerB_).
- Beperkt tot één domein. Kan niet meerdere domeinen of forests.
- Rechten voor het bijwerken van objecten en Service Principal Names (SPN's) vereist.

## <a name="resource-based-kerberos-constrained-delegation"></a>Bronnen gebaseerde beperkte Kerberos-overdracht

Met behulp van de resource op basis van Kerberos-beperkte overdracht (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het object van de server waar de resources zich bevinden.
In de tweede hop-scenario die hierboven worden beschreven, configureert u _ServerC_ om op te geven van waar het accepteert gedelegeerde referenties.

>**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden gedelegeerd. Zie voor meer informatie, [Focus van de beveiliging: Analyse van 'Account is vertrouwelijk en kan niet worden overgedragen' voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Voordelen

- Referenties worden niet opgeslagen.
- Betrekkelijk eenvoudig te configureren met behulp van PowerShell-cmdlets--er zijn geen speciale codering vereist.
- Er zijn geen speciale domeintoegang is vereist.
- Werk met domeinen en forests.
- PowerShell-code.

### <a name="cons"></a>Nadelen

- WindowsServer 2012 of hoger vereist.
- Biedt geen ondersteuning voor de tweede hop voor WinRM.
- Rechten voor het bijwerken van objecten en Service Principal Names (SPN's) vereist.

### <a name="example"></a>Voorbeeld

We bekijken een voorbeeld waarmee resources worden geconfigureerd op basis van beperkte delegering van PowerShell _ServerC_ waarmee gedelegeerde referenties van een _ServerB_.
In dit voorbeeld wordt ervan uitgegaan dat alle servers worden uitgevoerd met WindowsServer 2012 of hoger, en of er ten minste één Windows Server 2012-domeincontroller die een van de servers elk domein behoren.

Voordat u beperkte delegering configureren kunt, moet u toevoegen de `RSAT-AD-PowerShell` functie als de Active Directory PowerShell-module wilt installeren, en vervolgens importeren die module in uw sessie:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Verschillende beschikbare cmdlets hebben nu een **PrincipalsAllowedToDelegateToAccount** parameter:

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

De **PrincipalsAllowedToDelegateToAccount** parameter stelt het Active Directory-object-kenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**, die een toegangsbeheerlijst (ACL) bevat die Hiermee geeft u welke accounts hebben een machtiging voor het overdragen van referenties voor het gekoppelde account (in ons voorbeeld is dit het computeraccount voor _Server_).

Nu gaan we de variabelen die we gebruiken om weer te geven van de servers instellen:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (en dus PowerShell voor externe toegang) wordt uitgevoerd als het computeraccount standaard. U kunt dit zien door te kijken de **%{StartName/** eigenschap van de `winrm` service:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Voor _ServerC_ om toe te staan van de delegatie van een PowerShell-sessie voor externe toegang op _ServerB_, er wordt nu toegang verleend door in te stellen de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ voor het computerobject van _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

De Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches geweigerd toegangspogingen (negatieve cache) gedurende 15 minuten. Als _ServerB_ eerder heeft geprobeerd toegang te _ServerC_, moet u de cache wissen op _ServerB_ door het aanroepen van de volgende opdracht uit:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

U kunt ook de computer opnieuw opstarten of wacht ten minste 15 minuten om de cache te wissen.

Na de cache wissen, kunt u met succes-code uitvoeren _ServerA_ via _ServerB_ naar _ServerC_:

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

In dit voorbeeld wordt de `$using` variabele wordt gebruikt om de `$ServerC` zichtbaar voor variabele _ServerB_. Voor meer informatie over de `$using` variabele, Zie [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).

Om toe te staan van meerdere servers om te delegeren referenties _ServerC_, stel de waarde van de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ naar een matrix:

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

Als u maken van de tweede hop in meerdere domeinen wilt, volledig gekwalificeerde domeinnaam (FQDN) van de domeincontroller van het domein aan toevoegen die _ServerB_ behoort:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Als u wilt verwijderen van de mogelijkheid om te delegeren referenties ServerC, stel de waarde van de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ naar `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Meer informatie over bronnen gebaseerde beperkte Kerberos-overdracht

- [Wat is er nieuw in Kerberos-verificatie](https://technet.microsoft.com/library/hh831747.aspx)
- [Hoe Windows Server 2012 versnellingen de last van het Kerberos-beperkte overdracht, deel 1](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Hoe Windows Server 2012 versnellingen de last van het Kerberos-beperkte overdracht, deel 2](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Informatie over Kerberos-beperkte overdracht voor Azure Active Directory Application Proxy-implementaties met geïntegreerde Windows-verificatie](https://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory-Schema kenmerken M2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: Kerberos Protocol Extensions: Service for User and beperkte delegering Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)
- [Resource op basis van Kerberos-beperkte overdracht](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Extern beheer zonder beperkte delegering met PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>Met RunAs-PSSessionConfiguration

U kunt een sessieconfiguratie maken op _ServerB_ en stel de **RunAsCredential** parameter.

Zie voor meer informatie over het gebruik van PSSessionConfiguration en uitvoeren als de tweede hop-probleem op te lossen [andere oplossing voor externe communicatie van PowerShell Multihop](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Voordelen

- Als u werkt met een server met WMF 3.0 of hoger.

### <a name="cons"></a>Nadelen

- Configuratie van vereist **PSSessionConfiguration** en **RunAs** op elke tussenliggende server (_ServerB_).
- Wachtwoord onderhoud moet worden uitgevoerd bij het gebruik van een domein **RunAs** account

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA kunt u beperken welke opdrachten die een beheerder kan worden uitgevoerd tijdens een PowerShell-sessie. Het kan worden gebruikt om de tweede hop-probleem te verhelpen.

Zie voor meer informatie over JEA [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).

### <a name="pros"></a>Voordelen

- Er is geen wachtwoord onderhoud bij het gebruik van een virtueel account.

### <a name="cons"></a>Nadelen

- WMF 5.0 of hoger vereist.
- Moet worden geconfigureerd op elke tussenliggende server (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Doorgeven van referenties in een scriptblok Invoke-opdracht

U kunt doorgeven van referenties in de **ScriptBlock** parameter van een aanroep naar de [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.

### <a name="pros"></a>Voordelen

- Geen vereist speciale configuratie.
- Werkt op elke server met WMF 2.0 of hoger.

### <a name="cons"></a>Nadelen

- Een techniek onhandige code vereist.
- Als met WMF 2.0, moet andere syntaxis voor het doorgeven van argumenten met een externe sessie.

### <a name="example"></a>Voorbeeld

Het volgende voorbeeld laat zien hoe doorgeven van referenties in een **Invoke-Command** scriptblok:

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