---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: b8020f8b034ab24d79a96da3908e9b63bf017cd9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190380"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SAMENVATTING

Voegt een nieuwe autorisatieregel toe aan de Windows PowerShell® Web Access autorisatieregelset.

## <a name="syntax"></a>Syntaxis

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>BESCHRIJVING

De **Add-PswaAuthorizationRule** cmdlet voegt een nieuwe autorisatieregel toe aan de regelset van de Windows PowerShell® Web Access-autorisatie.

U moet de gebruikers, computers en Windows PowerShell-eindpunten voor deze regel opgeven. U kunt gebruikers en computers door afzonderlijke gebruikersaccounts en -computernamen of door op te geven groepen opgeven.

Voor een computer die is gekoppeld aan een Active Directory-domein, gebruikt de cmdlet de beveiligings-id (SID) van de computer om de regel te maken.
Hiermee kunt u een korte naam, een volledig gekwalificeerde domeinnaam (FQDN) of een IP-adres voor de **computernaam** op de aanmeldingspagina.

De cmdlet maakt voor een computer die niet is gekoppeld aan een Active Directory-domein, de regel met behulp van de computernaam die is verstrekt door de beheerder. Als u wilt verbinding maken met deze computer, moet de eindgebruiker de computernaam opgeven, precies zoals in de regel weergegeven.

Als er meerdere computers met dezelfde naam in het netwerk, kan korte naam omzetten in meer dan één computer. Dit kan leiden tot verwarring bij het maken van een verbinding. Bijvoorbeeld, als een regel bestaat voor de werkgroepcomputer met de naam '*Server1*' en een nieuwe computer met de naam *server1.contoso.com* is gekoppeld met het netwerk met behulp van de autorisatieregels voor validatie is geslaagd en Windows PowerShell Web Access probeert een verbinding maken met de computer met de naam '*Server1*'. Deze kan niet worden gegarandeerd dat de verbinding is gemaakt met de computer van de opgegeven werkgroep. de poging kan worden gemaakt op de werkgroep of de computer van het domein met de naam '*Server1*'. Als u dubbelzinnigheid, wordt het aanbevolen dat u de FQDN-naam voor de doelcomputer wanneer mogelijk te maken van een autorisatieregel.

De autorisatieregels evalueren van de primaire aanmelden referentie van de Windows PowerShell Web Access-gebruikers, niet de alternatieve referenties (de tweede set referenties die zijn gevonden in de **optionele verbindingsinstellingen** sectie van de aanmeldingspagina). Zie voor een voorbeeld van dit voorbeeld 6.

## <a name="parameters"></a>Parameters

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;tekenreeks&gt;

Hiermee geeft de naam van een computergroep in Active Directory Domain Services (AD DS) of het lokale groepen waarop deze regel toegang verleent.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;tekenreeks&gt;

Hiermee geeft u de naam van de computer waarop deze regel toegang verleent.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;tekenreeks&gt;

Geeft de naam van de configuratie van Windows PowerShell-sessie, ook wel bekend als runspace waarvoor deze regel toegang verleent.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u wilt gebruiken om Windows PowerShell-webtoegang autorisatieregels te wijzigen. Als u deze parameter niet toevoegt, gebruikt de cmdlet het account momenteel aangemelde gebruiker. Ophalen van een **PSCredential** -object, dat vereist is voor het op afstand autorisatieregels toevoegen, voert u de [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-force"></a>-Force

Hiermee wordt de opdracht uitgevoerd zonder gebruikersbevestiging. \
Bovendien ook wordt gevraagd om bevestiging wanneer u een eenvoudige of korte computernaam (zoals een naam die niet een domeinnaam of is geen volledig pad) opgeven. Bevestiging is aangevraagd uit veiligheidsoverwegingen, zodat u kunt de eenvoudige naam toevoegen van een computer alleen als de computer zich in een werkgroep.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | onjuist                                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;tekenreeks&gt;

Hiermee geeft u de beschrijvende naam voor deze regel.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | onjuist                                |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;tekenreeks\[\]&gt;

Hiermee geeft u de naam van een of meer gebruikersgroepen in AD DS of lokale groepen waarop deze regel toegang verleent.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | Met de naam                                |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByPropertyName)                |
| Jokertekens accepteren?          | onjuist                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;tekenreeks\[\]&gt;

Hiermee geeft u een of meer gebruikers waarop deze regel toegang verleent. De gebruikersnaam mag een lokale gebruikersaccount op de gatewaycomputer of een gebruiker in AD DS.
De indeling is `domain\user` of `computer\user`.

|||
|-|-|
| Aliassen                              | geen                                 |
| Nodig?                            | De waarde True                                 |
| Positie?                            | 1                                    |
| Standaardwaarde                        | geen                                 |
| Pijplijn-invoer accepteren?               | True (ByValue, ByPropertyName)       |
| Jokertekens accepteren?          | onjuist                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.
Zie voor meer informatie [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>INVOER

### <a name="string"></a>Tekenreeks

Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.

### <a name="string"></a>Tekenreeks\[\]

Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.

## <a name="outputs"></a>Resultaten

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Deze cmdlet retourneert de autorisatie-regelobject.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1"></a>VOORBEELD 1

In dit voorbeeld verleent toegang tot de sessieconfiguratie *Pswaeindpunt*, wordt er een beperkte runspace op *srv2* voor gebruikers in de *SMAdmins* groep. \
**Opmerking**: naam van de computer moet een volledig gekwalificeerde domeinnaam (FQDN). Beheerders definiëren een beperkte sessieconfiguratie of een runspace, dit is een beperkt aantal cmdlets en taken die eindgebruikers kunnen worden uitgevoerd. Het definiëren van een beperkte runspace kan voorkomen dat gebruikers toegang krijgen tot andere computers die niet in de toegestane Windows PowerShell® runspace, dus een beter beveiligde verbinding bieden. Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) of de [installeren en gebruik Windows PowerShell-webtoegang](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>VOORBEELD 2

In dit voorbeeld verleent toegang tot de Windows PowerShell-sessie standaardconfiguratie `Microsoft.PowerShell`op *srv2* voor gebruikers in de gebruikers met de naam contoso\\gebruiker1, contoso\\Gebruiker2 bevat, en contoso\\user3. Deze cmdlet maakt drie regels (1 per persoon).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>VOORBEELD 3

In dit voorbeeld laat zien hoe voor het invoeren van waarden van de naam van gebruiker via de pijplijn.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>VOORBEELD 4

In dit voorbeeld ziet u hoe u alle parameters waaruit waarden pijplijn naam van de eigenschap.

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>VOORBEELD 5

In dit voorbeeld wordt een regel met de naam van de lokale gebruiker toe om *PswaServer\\ChrisLocal* toegang tot de server met de naam *srv1.contoso.com*.

In dit voorbeeld ziet u een scenario waarbij de gateway in een werkgroep en de doelcomputer zich in een domein. De autorisatieregel is van toepassing op de lokale gebruikers op de gateway. Klik op de pagina Windows PowerShell-webtoegang aanmelden om te verifiëren, moet de gebruiker leveren een tweede set referenties in de **optionele verbindingsinstellingen** gebied. De gatewayserver de aanvullende set referenties gebruikt voor het verifiëren van de gebruiker op de doelcomputer, een server met de naam *srv1.contoso.com*.

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>VOORBEELD 6

In dit voorbeeld kan alle gebruikers toegang tot alle eindpunten op alle computers.
Hierdoor wordt het in feite uitgeschakeld autorisatieregels. \
**Opmerking**: het gebruik van de `*` jokerteken wordt niet aanbevolen voor implementaties van de beveiliging van gevoelige en moet alleen worden beschouwd voor testomgevingen of gebruikt in implementaties waarbij de beveiliging kan worden versoepeld.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Zie ook

- [Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)
- [Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)
- [Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)
- [Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)
- [Voeg lid](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)