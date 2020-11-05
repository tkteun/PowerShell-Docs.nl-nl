---
title: Referentieondersteuning toevoegen aan PowerShell-functies
description: Referentie parameters toevoegen aan uw Power shell-scripts,-functies en-cmdlets.
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: 3e4a3f41ccbca1cf97f2e96fd60f22d89be7bc5a
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354623"
---
# <a name="add-credential-support-to-powershell-functions"></a>Referentieondersteuning toevoegen aan PowerShell-functies

> [!NOTE]
> De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@joshduffney][] . Dit artikel is bewerkt voor opname op deze site. De Power shell-team dank Josh voor het delen van deze inhoud met ons. Raadpleeg zijn blog op [duffney.io][].

In dit artikel leest u hoe u referentie parameters kunt toevoegen aan Power shell-functies en waarom u dat wilt. Een referentie parameter is het toestaan van de functie of cmdlet als een andere gebruiker uit te voeren. Het meest voorkomende gebruik is het uitvoeren van de functie of cmdlet als een gebruikers account met verhoogde bevoegdheden.

De cmdlet heeft bijvoorbeeld de `New-ADUser` para meter **Credential** , die u domein beheerders referenties kunt opgeven voor het maken van een account in een domein. Ervan uitgaande dat uw normale account dat de Power shell-sessie uitvoert, deze toegang niet al heeft.

## <a name="creating-credential-object"></a>Referentie object maken

Het [PSCredential][] -object vertegenwoordigt een set beveiligings referenties, zoals een gebruikers naam en wacht woord. Het object kan worden door gegeven als een para meter voor een functie die wordt uitgevoerd als het gebruikers account in dat referentie object. Er zijn een paar manieren waarop u een referentie object kunt maken. De eerste manier om een referentie object te maken, is met behulp van de Power shell-cmdlet `Get-Credential` . Wanneer u zonder para meters uitvoert, wordt u gevraagd om een gebruikers naam en wacht woord. U kunt de cmdlet ook aanroepen met enkele optionele para meters.

Als u de domein naam en gebruikers naam van tevoren wilt opgeven, kunt u de para meters **referentie** of **gebruikers naam** gebruiken. Wanneer u de para meter **username** gebruikt, moet u ook een **bericht** waarde opgeven. De volgende code laat zien hoe u de cmdlet gebruikt. U kunt het referentie object ook opslaan in een variabele, zodat u de referentie meerdere keren kunt gebruiken. In het onderstaande voor beeld wordt het referentie object opgeslagen in de variabele `$Cred` .

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

Soms is het niet mogelijk om de interactieve methode voor het maken van referentie objecten te gebruiken die in het vorige voor beeld worden weer gegeven. Voor de meeste hulpprogram ma's voor automatisering is een niet-interactieve methode vereist. Als u een referentie wilt maken zonder tussen komst van de gebruiker, maakt u een veilige teken reeks met het wacht woord. Geef vervolgens de beveiligde teken reeks en gebruikers naam door aan de- `System.Management.Automation.PSCredential()` methode.

Gebruik de volgende opdracht om een beveiligde teken reeks te maken met het wacht woord:

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

Zowel de para meters **AsPlainText** als **Force** zijn vereist. Zonder deze para meters ontvangt u een bericht waarin wordt gemeld dat u geen tekst zonder opmaak in een beveiligde teken reeks hoeft door te geven. Power shell retourneert deze waarschuwing omdat het wacht woord voor onbewerkte tekst in verschillende logboeken wordt vastgelegd. Zodra u een beveiligde teken reeks hebt gemaakt, moet u deze door geven aan de `PSCredential()` methode voor het maken van het referentie object. In het volgende voor beeld bevat de variabele de `$password` beveiligde teken reeks `$Cred` bevat het referentie object.

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

Nu u weet hoe u referentie objecten maakt, kunt u referentie parameters toevoegen aan uw Power shell-functies.

## <a name="adding-a-credential-parameter"></a>Een referentie parameter toevoegen

Net als bij andere para meters, kunt u beginnen met het toevoegen in het `param` blok van uw functie.
Het is raadzaam om de para meter een naam te benoemen, `$Credential` omdat dat de bestaande Power shell-cmdlets gebruikt. Het type van de para meter moet zijn `[System.Management.Automation.PSCredential]` .

In het volgende voor beeld ziet u het parameter blok voor een functie met de naam `Get-Something` . Er zijn twee para meters: `$Name` en `$Credential` .

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

De code in dit voor beeld is voldoende om een para meter voor een werk referentie te hebben, maar er zijn een aantal dingen die u kunt toevoegen om het betrouwbaarder te maken.

- Voeg het `[ValidateNotNull()]` validatie kenmerk toe om te controleren of de waarde wordt door gegeven aan de **referentie**. Als de waarde van de para meter null is, voor komt dit kenmerk dat de functie wordt uitgevoerd met ongeldige referenties.

- Toevoegen `[System.Management.Automation.Credential()]` . Zo kunt u een gebruikers naam door geven als een teken reeks en een interactieve prompt voor het wacht woord hebben.

- Stel een standaard waarde voor de `$Credential` para meter in op `[System.Management.Automation.PSCredential]::Empty` . Uw functie kunt u dit object door geven `$Credential` aan bestaande Power shell-cmdlets. Als u een null-waarde opgeeft voor de cmdlet die in de functie wordt aangeroepen, treedt er een fout op. Deze fout wordt voor komen door een leeg referentie object op te geven.

> [!TIP]
> Sommige cmdlets die een referentie parameter accepteren, bieden geen ondersteuning `[System.Management.Automation.PSCredential]::Empty` . Zie de sectie [omgaan met verouderde cmdlets](#dealing-with-legacy-cmdlets) voor een tijdelijke oplossing.

## <a name="using-credential-parameters"></a>Referentie parameters gebruiken

In het volgende voor beeld ziet u hoe u referentie parameters kunt gebruiken. In dit voor beeld ziet u een functie `Set-RemoteRegistryValue` met de naam, die buiten [het inpests Book][]valt. Deze functie definieert de referentie parameter met behulp van de technieken die in de vorige sectie worden beschreven. De functie aanroepen `Invoke-Command` met behulp van de `$Credential` variabele die door de functie is gemaakt. Hiermee kunt u de gebruiker wijzigen die wordt uitgevoerd `Invoke-Command` . Omdat de standaard waarde van `$Credential` is een lege referentie, kan de functie worden uitgevoerd zonder referenties op te geven.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

In de volgende secties worden verschillende methoden voor het opgeven van referenties weer gegeven `Set-RemoteRegistryValue` .

### <a name="prompting-for-credentials"></a>Vragen om referenties

`Get-Credential`Als u tussen haakjes tijdens runtime gebruikt, wordt `()` de `Get-credential` om eerst uitgevoerd. U wordt gevraagd om een gebruikers naam en wacht woord. U kunt de **referenties** of de para meters van de **gebruikers naam** van gebruiken `Get-credential` om de gebruikers naam en het domein vooraf in te vullen. In het volgende voor beeld wordt een techniek gebruikt met de naam splatting om para meters door te geven aan de `Set-RemoteRegistryValue` functie. Raadpleeg het [about_Splatting][] -artikel voor meer informatie over splatting.

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![Een referentie tijdens runtime ophalen](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

Gebruiken is zeer `(Get-Credential)` omslachtig. Normaal gesp roken wordt de cmdlet automatisch gevraagd naar het wacht woord wanneer u de para meter **Credential** gebruikt met alleen een gebruikers naam. `[System.Management.Automation.Credential()]`Dit gedrag kan worden ingeschakeld met het kenmerk.

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![Vragen om referenties](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> In deze voor beelden wordt ervan uitgegaan dat u de **webserver** functies van Windows hebt geïnstalleerd om de weer gegeven register waarde in te stellen. Voer uit `Install-WindowsFeature Web-Server` en `Install-WindowsFeature web-mgmt-tools` indien nodig.

### <a name="provide-credentials-in-a-variable"></a>Referenties opgeven in een variabele

U kunt ook een referentie variabele vooraf invullen en deze door geven aan de para meter **Credential** van de `Set-RemoteRegistryValue` functie. Gebruik deze methode met doorlopende hulpprogram ma's voor integratie/doorlopende implementatie (CI/CD) zoals Jenkins, TeamCity en Octopus Deploy. Voor een voor beeld van het gebruik van Jenkins raadpleegt u het blog bericht van Hodge [met Jenkins en Power shell in Windows-deel 2][].

In dit voor beeld wordt de .NET-methode gebruikt om het referentie object te maken en een beveiligde teken reeks om het wacht woord door te geven.

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

Voor dit voor beeld wordt de beveiligde teken reeks gemaakt met een wacht woord met een lees bare tekst. Alle eerder genoemde CI/CD hebben een veilige methode voor het opgeven van het wacht woord tijdens runtime. Wanneer u deze hulpprogram ma's gebruikt, vervangt u het wacht woord voor onbewerkte tekst door de variabele die is gedefinieerd in het CI/CD-hulp programma dat u gebruikt.

### <a name="run-without-credentials"></a>Zonder referenties uitvoeren

Omdat `$Credential` de standaard instelling is ingesteld op een leeg referentie object, kunt u de opdracht zonder referenties uitvoeren, zoals wordt weer gegeven in dit voor beeld:

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a>Omgaan met verouderde cmdlets

Niet alle cmdlets ondersteunen referentie objecten of lege referenties toestaan. In plaats daarvan wil de cmdlet gebruikers naam-en wachtwoord parameters als teken reeksen. Er zijn enkele manieren om deze beperking te omzeilen.

### <a name="using-if-else-to-handle-empty-credentials"></a>Een if-else gebruiken voor het verwerken van lege referenties

In dit scenario accepteert de cmdlet die u wilt uitvoeren geen leeg referentie object. In dit voor beeld wordt de para meter **Credential** `Invoke-Command` alleen toegevoegd als deze niet leeg is. Anders wordt de `Invoke-Command` para meter zonder **referenties** uitgevoerd.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a>Splatting gebruiken voor het afhandelen van lege referenties

In dit voor beeld wordt de para meter splatting gebruikt om de verouderde cmdlet aan te roepen. Het `$Credential` object wordt voorwaardelijk toegevoegd aan de hashtabel voor splatting en voor komt dat het script blok moet worden herhaald `Invoke-Command` . Zie het blog bericht [splatting para meters in Advanced functions][] (Engelstalig) voor meer informatie over splatting binnen functions.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a>Werken met wacht woorden voor teken reeksen

De `Invoke-Sqlcmd` cmdlet is een voor beeld van een cmdlet waarmee een teken reeks als wacht woord wordt geaccepteerd.
`Invoke-Sqlcmd` met kunt u eenvoudige SQL INSERT-, update-en DELETE-instructies uitvoeren. `Invoke-Sqlcmd` vereist een gebruikers naam en wacht woord met een lees bare tekst in plaats van een veiliger referentie object. In dit voor beeld ziet u hoe u de gebruikers naam en het wacht woord uitpakt uit een referentie object.

Met de `Get-AllSQLDatabases` functie in dit voor beeld wordt de `Invoke-Sqlcmd` cmdlet aangeroepen om een query uit te voeren op een SQL-Server voor alle data bases. De functie definieert een **referentie** parameter met hetzelfde kenmerk dat in de vorige voor beelden wordt gebruikt. Omdat de gebruikers naam en het wacht woord in de `$Credential` variabele bestaan, kunt u deze waarden extra heren voor gebruik met `Invoke-Sqlcmd` .

De gebruikers naam is beschikbaar via de eigenschap **username** van de `$Credential` variabele. Om het wacht woord te verkrijgen, moet u de `GetNetworkCredential()` methode van het `$Credential` object gebruiken. De waarden worden geëxtraheerd in variabelen die worden toegevoegd aan een hash-tabel die wordt gebruikt voor splatting-para meters voor `Invoke-Sqlcmd` .

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a>Voortgezet leer referentie beheer

Het is veilig om referentie objecten te maken en op te slaan. De volgende bronnen kunnen u helpen bij het onderhouden van Power shell-referenties.

- [BetterCredentials][]
- [Azure Key Vault][]
- [Kluis project][]
- [SecretManagement-module][]

<!-- link references -->
[oorspronkelijke versie]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Kluis project]: https://www.vaultproject.io/
[Splatting-para meters in geavanceerde functies]: https://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Automatiseren met Jenkins en Power shell in Windows-deel 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[Het ziekte-boek]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[SecretManagement-module]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
