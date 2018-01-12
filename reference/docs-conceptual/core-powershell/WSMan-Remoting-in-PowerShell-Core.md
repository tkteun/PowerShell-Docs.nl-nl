# <a name="ws-management-wsman-remoting-in-powershell-core"></a>WS-Management (WSMan) voor externe toegang in PowerShell-kern 

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructies voor het maken van een eindpunt voor externe toegang

Het PowerShell-kern-pakket voor Windows bevat een WinRM-invoegtoepassing (`pwrshplugin.dll`) en een script voor installatie (`Install-PowerShellRemoting.ps1`) in `$PSHome`.
Deze bestanden inschakelen PowerShell te accepteren van binnenkomende PowerShell externe verbindingen wanneer het eindpunt is opgegeven.

### <a name="motivation"></a>Doel

Een installatie van PowerShell kan verbinding maken met PowerShell-sessies met externe computers met behulp van `New-PSSession` en `Enter-PSSession`.
De gebruiker moet een WinRM-eindpunt voor externe toegang maken zodat het accepteren van binnenkomende PowerShell externe verbindingen.
Dit is een expliciete opt-in-scenario waarin de gebruiker wordt uitgevoerd met Install-PowerShellRemoting.ps1 om de WinRM-eindpunt te maken.
Het script voor installatie is een oplossing op korte termijn totdat we toevoegen van aanvullende functionaliteit voor `Enable-PSRemoting` de dezelfde actie uit te voeren.
Zie voor meer informatie probleem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Scriptacties

Het script

1. Hiermee maakt u een map voor de invoegtoepassing binnen %windir%\System32\PowerShell
1. Pwrshplugin.dll naar die locatie opgehaald
1. Genereert een configuratiebestand
1. Registers dat invoegtoepassing met WinRM

### <a name="registration"></a>Registratie

Het script moet worden uitgevoerd binnen een beheerdersniveau PowerShell-sessie en wordt uitgevoerd in twee modi.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Uitgevoerd door het exemplaar van PowerShell die wordt geregistreerd

``` powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Uitgevoerd door een ander exemplaar van PowerShell namens het exemplaar dat wordt geregistreerd

``` powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Bijvoorbeeld:

``` powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**Opmerking:** wordt het script voor de registratie voor externe toegang opnieuw starten van WinRM, zodat alle bestaande PSRP-sessies wordt beëindigd onmiddellijk nadat het script wordt uitgevoerd. Als tijdens een externe sessie worden uitgevoerd, wordt deze de verbinding verbreken.

## <a name="how-to-connect-to-the-new-endpoint"></a>Verbinding maken met het nieuwe eindpunt

Een PowerShell-sessie met het nieuwe PowerShell-eindpunt maken door te geven `-ConfigurationName "some endpoint name"`. Maak verbinding met de PowerShell-exemplaar van het bovenstaande voorbeeld door een te gebruiken:

``` powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Houd er rekening mee dat `New-PSSession` en `Enter-PSSession` aanroepen die geen opgeeft `-ConfigurationName` heeft betrekking op het standaardeindpunt PowerShell `microsoft.powershell`.
