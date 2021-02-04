---
description: Hierin wordt uitgelegd hoe u scripts ondertekent, zodat ze voldoen aan het Power shell-uitvoerings beleid.
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 560ecc385e970224a23af7a1195c99d8423f503f
ms.sourcegitcommit: 021ea294327dec542ec040619dac0d2171397a90
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/29/2020
ms.locfileid: "97804157"
---
# <a name="about-signing"></a>Over ondertekening

## <a name="short-description"></a>Korte beschrijving
Hierin wordt uitgelegd hoe u scripts ondertekent, zodat ze voldoen aan het Power shell-uitvoerings beleid.

## <a name="long-description"></a>Lange beschrijving

Het beperkte uitvoerings beleid staat niet toe dat er scripts worden uitgevoerd. Het uitvoerings beleid voor **Alles ondertekend** en **RemoteSigned** voor komt dat Power shell scripts uitvoert die geen digitale hand tekening hebben.

In dit onderwerp wordt uitgelegd hoe u geselecteerde scripts kunt uitvoeren die niet zijn ondertekend, zelfs niet wanneer het uitvoerings beleid **RemoteSigned** is en hoe u scripts voor eigen gebruik kunt ondertekenen.

Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid.

## <a name="to-permit-signed-scripts-to-run"></a>Toestaan dat ondertekende scripts worden uitgevoerd

Wanneer u Power shell voor het eerst start op een computer, is het **beperkte** uitvoerings beleid (de standaard instelling) waarschijnlijk van kracht.

Het **beperkte** beleid staat niet toe dat er scripts worden uitgevoerd.

Als u wilt zoeken naar het effectief uitvoerings beleid op uw computer, typt u:

```powershell
Get-ExecutionPolicy
```

Als u niet-ondertekende scripts wilt uitvoeren die u op uw lokale computer en ondertekende scripts van andere gebruikers schrijft, start u Power shell met de optie als administrator uitvoeren en gebruikt u de volgende opdracht om het uitvoerings beleid op de computer te wijzigen in **RemoteSigned**:

```powershell
Set-ExecutionPolicy RemoteSigned
```

Zie het Help-onderwerp voor de cmdlet voor meer informatie `Set-ExecutionPolicy` .

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a>Niet-ondertekende scripts uitvoeren met het RemoteSigned-uitvoerings beleid

Als uw Power shell-uitvoerings beleid **RemoteSigned** is, voert Power shell geen niet-ondertekende scripts uit die zijn gedownload van Internet, met inbegrip van niet-ondertekende scripts die u via e-mail en Program ma's voor chat berichten ontvangt.

Als u probeert een gedownload script uit te voeren, wordt het volgende fout bericht weer gegeven:

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

Voordat u het script uitvoert, moet u de code controleren om er zeker van te zijn dat u deze vertrouwt.
Scripts hebben hetzelfde effect als elk uitvoerbaar programma.

Als u een niet-ondertekend script wilt uitvoeren, gebruikt u de cmdlet Unblock-File of gebruikt u de volgende procedure.

1. Sla het script bestand op uw computer op.
2. Klik op Start, klik op mijn computer en zoek het opgeslagen script bestand.
3. Klik met de rechter muisknop op het script bestand en klik vervolgens op Eigenschappen.
4. Klik op blok kering opheffen.

Als een script dat is gedownload van Internet digitaal is ondertekend, maar u nog niet hebt gekozen voor het vertrouwen van de uitgever, wordt het volgende bericht weer gegeven in Power shell:

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

Als u de uitgever vertrouwt, selecteert u eenmaal uitvoeren of altijd uitvoeren. Als u de uitgever niet vertrouwt, selecteert u nooit uitvoeren of niet uitvoeren. Als u nooit uitvoeren of altijd uitvoeren selecteert, vraagt Power shell u niet meer om deze uitgever.

## <a name="methods-of-signing-scripts"></a>Methoden voor het ondertekenen van scripts

U kunt de scripts die u schrijft, ondertekenen en de scripts die u uit andere bronnen ontvangt. Controleer voordat u een script gaat ondertekenen elke opdracht om te controleren of het veilig is om uit te voeren.

Zie [Aanbevolen procedures voor het ondertekenen van code](/previous-versions/windows/hardware/design/dn653556(v=vs.85))voor aanbevolen procedures voor het ondertekenen van programma code.

Zie [set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)voor meer informatie over het ondertekenen van een script bestand.

Met de `New-SelfSignedCertificate` cmdlet die is geïntroduceerd in de PKI-module in Power shell 3,0, wordt een zelfondertekend certificaat gemaakt dat geschikt is voor testen. Zie het Help-onderwerp voor de cmdlet New-SelfSignedCertificate voor meer informatie.

Als u een digitale hand tekening aan een script wilt toevoegen, moet u deze ondertekenen met een certificaat voor ondertekening van programma code. Twee typen certificaten zijn geschikt voor het ondertekenen van een script bestand:

- Certificaten die zijn gemaakt door een certificerings instantie: een open bare certificerings instantie verifieert uw identiteit en geeft u een certificaat voor ondertekening van programma code. Wanneer u uw certificaat aanschaft bij een betrouw bare certificerings instantie, kunt u uw script delen met gebruikers op andere computers waarop Windows wordt uitgevoerd, omdat deze andere computers de certificerings instantie vertrouwen.

- Certificaten die u maakt: u kunt een zelfondertekend certificaat maken waarvoor uw computer de autoriteit is die het certificaat maakt. Dit certificaat is gratis en maakt het mogelijk om scripts op uw computer te schrijven, te ondertekenen en uit te voeren. Een script dat is ondertekend door een zelfondertekend certificaat kan echter niet worden uitgevoerd op andere computers.

Normaal gesp roken gebruikt u een zelfondertekend certificaat alleen voor het ondertekenen van scripts die u voor eigen gebruik schrijft en voor het ondertekenen van scripts die u krijgt van andere bronnen die u hebt geverifieerd om veilig te zijn. Het is niet geschikt voor scripts die worden gedeeld, zelfs binnen een onderneming.

Als u een zelfondertekend certificaat maakt, zorg er dan voor dat u sterke beveiliging van persoonlijke sleutels op uw certificaat inschakelt. Zo voor komt u dat kwaad aardige Program ma's namens u scripts kunnen ondertekenen. De instructies zijn aan het einde van dit onderwerp opgenomen.

## <a name="create-a-self-signed-certificate"></a>Een zelfondertekend certificaat maken

Als u een zelfondertekend certificaat wilt maken, gebruikt u de `New-SelfSignedCertificate` cmdlet in de PKI-module. Deze module is geïntroduceerd in Power Shell 3,0 en is opgenomen in Windows 8 en Windows Server 2012. Zie het Help-onderwerp voor de cmdlet voor meer informatie `New-SelfSignedCertificate` .

Gebruik het hulp programma voor het maken van certificaten om een zelfondertekend certificaat te maken in eerdere versies van Windows `MakeCert.exe` . Dit hulp programma is opgenomen in de Microsoft .NET SDK (versie 1,1 en hoger) en in de Microsoft Windows SDK.

Zie het [hulp programma voor het maken van certificaten (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80))voor meer informatie over de syntaxis en de parameter beschrijvingen van het hulp programma MakeCert.exe.

Als u het hulp programma MakeCert.exe wilt gebruiken om een certificaat te maken, voert u de volgende opdrachten uit in een SDK-opdracht prompt venster.

Opmerking: met de eerste opdracht maakt u een lokale certificerings instantie voor uw computer. Met de tweede opdracht wordt een persoonlijk certificaat van de certificerings instantie gegenereerd.

Opmerking: u kunt de opdrachten op exact dezelfde manier kopiëren of typen als ze worden weer gegeven. Er zijn geen vervangingen nodig, maar u kunt de naam van het certificaat wijzigen.

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

Het hulp programma MakeCert.exe vraagt u om een wacht woord voor een persoonlijke sleutel. Het wacht woord zorgt ervoor dat niemand zonder uw toestemming het certificaat kan gebruiken of openen.
Maak een wacht woord en voer het in dat u kunt onthouden. U gebruikt dit wacht woord later om het certificaat op te halen.

Als u wilt controleren of het certificaat correct is gegenereerd, gebruikt u de volgende opdracht om het certificaat op te halen in het certificaat archief op de computer. Er wordt geen certificaat bestand gevonden in de map van het bestands systeem.

Typ het volgende bij de Power shell-prompt:

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

Met deze opdracht wordt de Power shell-certificaat provider gebruikt voor het weer geven van informatie over het certificaat.

Als het certificaat is gemaakt, toont de uitvoer de **vinger afdruk** die het certificaat identificeert in een weer gave die er ongeveer als volgt uitziet:

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a>Een script ondertekenen

Nadat u een zelfondertekend certificaat hebt gemaakt, kunt u scripts ondertekenen. Als u het **Alles ondertekend** -uitvoerings beleid gebruikt, kunt u met het ondertekenen van een script het script uitvoeren op de computer.

Het volgende voorbeeld script, `Add-Signature.ps1` , tekent een script. Als u echter het **Alles ondertekend** -uitvoerings beleid gebruikt, moet u het script ondertekenen `Add-Signature.ps1` voordat u het uitvoert.

> [!IMPORTANT]
> Het script moet worden opgeslagen met behulp van ASCII-of UTF8NoBOM-code ring. U kunt een script bestand dat gebruikmaakt van een andere code ring ondertekenen. Het script kan echter niet worden uitgevoerd of de module met het script kan niet worden geïmporteerd.

Als u dit script wilt gebruiken, kopieert u de volgende tekst naar een tekst bestand en noemt u deze `Add-Signature.ps1` .

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

Als u het `Add-Signature.ps1` script bestand wilt ondertekenen, typt u de volgende opdrachten bij de Power shell-opdracht prompt:

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

Nadat het script is ondertekend, kunt u het uitvoeren op de lokale computer. Het script kan echter niet worden uitgevoerd op computers waarop het Power shell-uitvoerings beleid een digitale hand tekening van een vertrouwde instantie vereist. Als u probeert, wordt het volgende fout bericht weer gegeven in Power shell:

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

Als in Power shell dit bericht wordt weer gegeven wanneer u een script uitvoert dat u niet hebt geschreven, behandelt u het bestand net zoals u een niet-ondertekend script zou behandelen. Controleer de code om te bepalen of u het script kunt vertrouwen.

## <a name="enable-strong-private-key-protection-for-your-certificate"></a>Sterke beveiliging van persoonlijke sleutels inschakelen voor uw certificaat

Als u een persoonlijk certificaat op uw computer hebt, kunnen kwaadwillende Program ma's namens u mogelijk scripts ondertekenen, waardoor Power shell deze kan uitvoeren.

Gebruik certificaat beheer om `Certmgr.exe` uw handtekening certificaat te exporteren naar een bestand om te voor komen dat namens u automatisch wordt aangemeld `.pfx` . Certificaat beheer is opgenomen in de Microsoft .NET SDK, de Microsoft Windows SDK en in Internet Explorer.

Het certificaat exporteren:

1. Start certificaat beheer.
2. Selecteer het certificaat dat is uitgegeven door de hoofdmap van het lokale Power shell-certificaat.
3. Klik op exporteren om de wizard Certificaat exporteren te starten.
4. Selecteer Ja, de persoonlijke sleutel exporteren en klik op volgende.
5. Selecteer ' zware beveiliging inschakelen '.
6. Typ een wacht woord en typ het nogmaals ter bevestiging.
7. Typ een bestands naam met de extensie. pfx.
8. Klik op Voltooien.

Het certificaat opnieuw importeren:

1. Start certificaat beheer.
2. Klik op importeren om de wizard Certificaat importeren te starten.
3. Open op de locatie van het pfx-bestand dat u tijdens het export proces hebt gemaakt.
4. Selecteer op de pagina wacht woord sterke beveiliging met persoonlijke sleutel inschakelen en voer het wacht woord in dat u tijdens het export proces hebt toegewezen.
5. Selecteer het persoonlijke certificaat archief.
6. Klik op Voltooien.

## <a name="prevent-the-signature-from-expiring"></a>Voor komen dat de hand tekening verloopt

De digitale hand tekening in een script is geldig totdat het handtekening certificaat is verlopen of zolang een time stamp-server kan controleren of het script is ondertekend terwijl het handtekening certificaat geldig was.

Omdat de meeste handtekening certificaten slechts één jaar geldig zijn, zorgt u er met een tijds tempel server voor dat gebruikers uw script lang kunnen gebruiken om te komen.

## <a name="see-also"></a>Zie ook

[about_Execution_Policies](about_Execution_Policies.md)

[about_Profiles](about_Profiles.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Inleiding tot hand tekening bij programma code](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))
