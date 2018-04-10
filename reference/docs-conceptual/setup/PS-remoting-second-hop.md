---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Maken van de tweede hop in PowerShell voor externe toegang
ms.openlocfilehash: 893b4353c4244dc96c4b234bb4062b583a5cd36d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Maken van de tweede hop in PowerShell voor externe toegang

De 'tweede hop '-probleem verwijst naar een situatie als volgt:

1. U bent aangemeld bij _ServerA_.
2. Van _ServerA_, u verbinding maken met een externe PowerShell-sessie starten _ServerB_.
3. Een opdracht die u uitvoert op _ServerB_ via uw externe communicatie van PowerShell sessie probeert te krijgen tot een bron op _ServerC_.
4. Toegang tot de resource op _ServerC_ is geweigerd omdat de referenties die u gebruikt voor het maken van de externe communicatie van PowerShell-sessie niet worden doorgegeven van _ServerB_ naar _ServerC_.

Er zijn verschillende manieren om dit probleem te verhelpen. In dit onderwerp, zullen we verschillende van de meest populaire oplossingen voor het tweede hop probleem.

## <a name="credssp"></a>CredSSP

U kunt de [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) voor verificatie. CredSSP in de cache opgeslagen referenties op de externe server (_ServerB_), zodat deze wordt geopend u maximaal credential theft aanvallen. Als de externe computer is geknoeid, heeft de aanvaller toegang tot de referenties van de gebruiker. CredSSP is standaard uitgeschakeld in zowel client- en servercomputers. Alleen in de meest vertrouwde omgevingen, moet u CredSSP inschakelen. Bijvoorbeeld, een domeinbeheerder verbinding te maken met een domeincontroller, omdat de domeincontroller uiterst vertrouwde is.

Zie voor meer informatie over de beveiligingsoverwegingen wanneer u CredSSP voor externe communicatie van PowerShell [onbedoeld Sabotage: Houd er rekening mee van CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).

Zie voor meer informatie over credential theft aanvallen [Mitigating Pass-the-Hash (PtH) aanvallen en andere Referentiediefstal](https://www.microsoft.com/en-us/download/details.aspx?id=36036).

Zie voor een voorbeeld van hoe u inschakelen en gebruiken van CredSSP voor externe communicatie van PowerShell [CredSSP met behulp van de tweede hop probleem op te lossen](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).

### <a name="pros"></a>Voordelen

- De Tool werkt voor alle servers met Windows Server 2008 of hoger.

### <a name="cons"></a>Nadelen

- Beveiligingsproblemen heeft.
- Configuratie van functies voor zowel client als server vereist.

## <a name="kerberos-delegation-unconstrained"></a>Kerberos-overdracht (een)

U kunt ook een Kerberos-overdracht gebruikt voor het maken van de tweede hop. Deze methode biedt echter geen controle van waar de gedelegeerde referenties worden gebruikt.

>**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden overgedragen. Zie voor meer informatie [beveiliging Focus: 'Account is vertrouwelijk en kan niet worden overgedragen' analyseren voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Voordelen

- Vereist geen speciale coderen.

### <a name="cons"></a>Nadelen

- Biedt de tweede hop geen ondersteuning voor WinRM.
- Biedt geen controle over waar de referenties worden gebruikt, het maken van een beveiligingsprobleem.

## <a name="kerberos-constrained-delegation"></a>Kerberos-beperkte overdracht

Verouderde beperkte delegering (geen resource gebaseerde) kunt u de tweede hop maken.

>**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden overgedragen. Zie voor meer informatie [beveiliging Focus: 'Account is vertrouwelijk en kan niet worden overgedragen' analyseren voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Voordelen

- Vereist geen speciale coderen

### <a name="cons"></a>Nadelen

- Biedt de tweede hop geen ondersteuning voor WinRM.
- Moet worden geconfigureerd op de Active Directory-object van de externe server (_ServerB_).
- Beperkt tot één domein. Kan niet meerdere domeinen of forests.
- Rechten voor het bijwerken van objecten en Service Principal Names (SPN's) vereist.

## <a name="resource-based-kerberos-constrained-delegation"></a>Bronnen gebaseerde beperkte Kerberos-overdracht

Met behulp van Kerberos bronnen gebaseerde beperkte delegering (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het object van de server waar de bronnen zich bevinden.
In het tweede hop-scenario die hierboven worden beschreven, configureert u _ServerC_ om op te geven van waar worden geaccepteerd overgedragen referenties.

>**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden overgedragen. Zie voor meer informatie [beveiliging Focus: 'Account is vertrouwelijk en kan niet worden overgedragen' analyseren voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>Voordelen

- Referenties worden niet opgeslagen.
- Betrekkelijk eenvoudig te configureren met behulp van PowerShell-cmdlets--er is geen speciale codering vereist.
- Er is geen speciale domeintoegang is vereist.
- Deze optie werkt in domeinen en forests.
- PowerShell-code.

### <a name="cons"></a>Nadelen

- WindowsServer 2012 of later vereist.
- Biedt de tweede hop geen ondersteuning voor WinRM.
- Rechten voor het bijwerken van objecten en Service Principal Names (SPN's) vereist.

### <a name="example"></a>Voorbeeld

Bekijk een voorbeeld van de resource configureert u beperkte delegering op basis van PowerShell _ServerC_ waarmee gedelegeerde referenties van een _ServerB_.
In dit voorbeeld wordt ervan uitgegaan dat alle servers worden uitgevoerd met WindowsServer 2012 of later, en of er ten minste één Windows Server 2012-domeincontroller waarop elke van de servers elk domein behoren.

Voordat u beperkte delegering configureren kunt, moet u toevoegen de `RSAT-AD-PowerShell` om te installeren van de Active Directory PowerShell-module en vervolgens importeren die module in uw sessie:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Verschillende beschikbare cmdlets hebt nu een **PrincipalsAllowedToDelegateToAccount** parameter:

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

De **PrincipalsAllowedToDelegateToAccount** parameter stelt het Active Directory-objectkenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**, die een toegangsbeheerlijst (ACL) bevat die Hiermee geeft u op welke accounts gemachtigd voor het overdragen van referenties voor de gekoppelde account (in ons voorbeeld dient de computeraccount voor _Server_).

Nu gaan we instellen van de variabelen die we gebruiken om weer te geven van de servers:

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (en dus PowerShell voor externe toegang) wordt uitgevoerd als het computeraccount standaard. U kunt dit zien door te kijken naar de **StartName** eigenschap van de `winrm` service:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Voor _ServerC_ waarmee de overdracht van een PowerShell-sessie voor externe toegang op _ServerB_, zullen we toegang verlenen door in te stellen de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ voor het computerobject van _ServerB_:

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Het Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches geweigerd toegangspogingen (negatieve cache) gedurende 15 minuten. Als _ServerB_ eerder heeft geprobeerd toegang te _ServerC_, moet u de cache wissen op _ServerB_ door het aanroepen van de volgende opdracht:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

U kunt ook de computer opnieuw opstarten of wacht ten minste 15 minuten om de cache te wissen.

Na het uitschakelen van de cache kunt u de code van uitgevoerd _ServerA_ via _ServerB_ naar _ServerC_:

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

In dit voorbeeld wordt de `$using` variabele wordt gebruikt om de `$ServerC` variabele zichtbaar is voor _ServerB_. Voor meer informatie over de `$using` variabele, Zie [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).

Op meerdere servers te delegeren referenties _ServerC_, stel de waarde van de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ om in een matrix:

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

Als u maken van de tweede hop tussen domeinen wilt, volledig gekwalificeerde domeinnaam (FQDN) van de domeincontroller van het domein aan toevoegen die _ServerB_ behoort:

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Als u wilt verwijderen van de mogelijkheid overdragen van referenties voor ServerC, stel de waarde van de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ naar `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Informatie over bronnen gebaseerde beperkte Kerberos-overdracht

- [Wat is er nieuw in Kerberos-verificatie](https://technet.microsoft.com/library/hh831747.aspx)
- [Hoe Windows Server 2012 versnellingen de last van het Kerberos-beperkte overdracht, deel 1](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [Hoe Windows Server 2012 versnellingen de last van het Kerberos-beperkte overdracht, deel 2](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [Informatie over Kerberos-beperkte overdracht voor Azure Active Directory Application Proxy implementaties met geïntegreerde Windows-verificatie](http://aka.ms/kcdpaper)
- [[MS-ADA2]: Active Directory-Schema kenmerken M2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)
- [[MS-SFU]: Kerberos Protocol Extensions: Service for User and beperkte delegering Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)
- [Resource op basis van Kerberos-beperkte overdracht](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Extern beheer zonder beperkte delegering PrincipalsAllowedToDelegateToAccount gebruiken](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a>Met RunAs-PSSessionConfiguration

U kunt een sessieconfiguratie maken op _ServerB_ en stel de **RunAsCredential** parameter.

Zie voor meer informatie over het gebruik van PSSessionConfiguration en RunAs voor het oplossen van de tweede hop probleem [andere oplossing voor externe communicatie van PowerShell Multihop](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).

### <a name="pros"></a>Voordelen

- Als u werkt met een server met WMF 3.0 of hoger.

### <a name="cons"></a>Nadelen

- Configuratie van vereist **PSSessionConfiguration** en **RunAs** op elke server tussenliggende (_ServerB_).
- Wachtwoord onderhoud is vereist bij het gebruik van een domein **RunAs** account

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA kunt u beperken welke opdrachten die een beheerder kan worden uitgevoerd tijdens een PowerShell-sessie. Het kan worden gebruikt voor het oplossen van de tweede hop probleem.

Zie voor meer informatie over JEA [net genoeg beheer](https://docs.microsoft.com/en-us/powershell/jea/overview).

### <a name="pros"></a>Voordelen

- Er is geen wachtwoord onderhoud bij gebruik van een virtueel account.

### <a name="cons"></a>Nadelen

- WMF 5.0 of hoger vereist.
- Moet worden geconfigureerd op elke server tussenliggende (_ServerB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Referenties in een scriptblok Invoke-Command doorgeven

U kunt doorgeven referenties binnen de **ScriptBlock** parameter van een aanroep naar de [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.

### <a name="pros"></a>Voordelen

- Is geen speciale configuratie vereist.
- Werkt op elke server waarop WMF 2.0 of hoger wordt uitgevoerd.

### <a name="cons"></a>Nadelen

- Vereist een techniek onhandige code.
- Als WMF 2.0 wordt uitgevoerd, moet andere syntaxis voor het doorgeven van de argumenten voor een externe sessie.

### <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u kunt doorgeven van referenties in een **Invoke-Command** scriptblok:

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