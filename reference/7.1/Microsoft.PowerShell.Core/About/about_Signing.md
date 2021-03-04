---
description: Hierin wordt uitgelegd hoe u scripts ondertekent, zodat ze voldoen aan het Power shell-uitvoerings beleid.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 5ad2f417fc31c18f40e6ce823fe07883cb8367dc
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685631"
---
# <a name="about-signing"></a><span data-ttu-id="4c02d-104">Over ondertekening</span><span class="sxs-lookup"><span data-stu-id="4c02d-104">About Signing</span></span>

## <a name="short-description"></a><span data-ttu-id="4c02d-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="4c02d-105">Short description</span></span>
<span data-ttu-id="4c02d-106">Hierin wordt uitgelegd hoe u scripts ondertekent, zodat ze voldoen aan het Power shell-uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="4c02d-106">Explains how to sign scripts so that they comply with the PowerShell execution policies.</span></span>

## <a name="long-description"></a><span data-ttu-id="4c02d-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="4c02d-107">Long description</span></span>

<span data-ttu-id="4c02d-108">Het beperkte uitvoerings beleid staat niet toe dat er scripts worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c02d-108">The Restricted execution policy does not permit any scripts to run.</span></span> <span data-ttu-id="4c02d-109">Het uitvoerings beleid voor **Alles ondertekend** en **RemoteSigned** voor komt dat Power shell scripts uitvoert die geen digitale hand tekening hebben.</span><span class="sxs-lookup"><span data-stu-id="4c02d-109">The **AllSigned** and **RemoteSigned** execution policies prevent PowerShell from running scripts that do not have a digital signature.</span></span>

<span data-ttu-id="4c02d-110">In dit onderwerp wordt uitgelegd hoe u geselecteerde scripts kunt uitvoeren die niet zijn ondertekend, zelfs niet wanneer het uitvoerings beleid **RemoteSigned** is en hoe u scripts voor eigen gebruik kunt ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-110">This topic explains how to run selected scripts that are not signed, even while the execution policy is **RemoteSigned**, and how to sign scripts for your own use.</span></span>

<span data-ttu-id="4c02d-111">Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="4c02d-111">For more information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="to-permit-signed-scripts-to-run"></a><span data-ttu-id="4c02d-112">Toestaan dat ondertekende scripts worden uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="4c02d-112">To permit signed scripts to run</span></span>

<span data-ttu-id="4c02d-113">Wanneer u Power shell voor het eerst start op een computer, is het **beperkte** uitvoerings beleid (de standaard instelling) waarschijnlijk van kracht.</span><span class="sxs-lookup"><span data-stu-id="4c02d-113">When you start PowerShell on a computer for the first time, the **Restricted** execution policy (the default) is likely to be in effect.</span></span>

<span data-ttu-id="4c02d-114">Het **beperkte** beleid staat niet toe dat er scripts worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c02d-114">The **Restricted** policy does not permit any scripts to run.</span></span>

<span data-ttu-id="4c02d-115">Als u wilt zoeken naar het effectief uitvoerings beleid op uw computer, typt u:</span><span class="sxs-lookup"><span data-stu-id="4c02d-115">To find the effective execution policy on your computer, type:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="4c02d-116">Als u niet-ondertekende scripts wilt uitvoeren die u op uw lokale computer en ondertekende scripts van andere gebruikers schrijft, start u Power shell met de optie als administrator uitvoeren en gebruikt u de volgende opdracht om het uitvoerings beleid op de computer te wijzigen in **RemoteSigned**:</span><span class="sxs-lookup"><span data-stu-id="4c02d-116">To run unsigned scripts that you write on your local computer and signed scripts from other users, start PowerShell with the Run as Administrator option and then use the following command to change the execution policy on the computer to **RemoteSigned**:</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="4c02d-117">Zie het Help-onderwerp voor de cmdlet voor meer informatie `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="4c02d-117">For more information, see the help topic for the `Set-ExecutionPolicy` cmdlet.</span></span>

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a><span data-ttu-id="4c02d-118">Niet-ondertekende scripts uitvoeren met het RemoteSigned-uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="4c02d-118">Running unsigned scripts using the RemoteSigned execution policy</span></span>

<span data-ttu-id="4c02d-119">Als uw Power shell-uitvoerings beleid **RemoteSigned** is, voert Power shell geen niet-ondertekende scripts uit die zijn gedownload van Internet, met inbegrip van niet-ondertekende scripts die u via e-mail en Program ma's voor chat berichten ontvangt.</span><span class="sxs-lookup"><span data-stu-id="4c02d-119">If your PowerShell execution policy is **RemoteSigned**, PowerShell will not run unsigned scripts that are downloaded from the internet, including unsigned scripts you receive through email and instant messaging programs.</span></span>

<span data-ttu-id="4c02d-120">Als u probeert een gedownload script uit te voeren, wordt het volgende fout bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="4c02d-120">If you try to run a downloaded script, PowerShell displays the following error message:</span></span>

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

<span data-ttu-id="4c02d-121">Voordat u het script uitvoert, moet u de code controleren om er zeker van te zijn dat u deze vertrouwt.</span><span class="sxs-lookup"><span data-stu-id="4c02d-121">Before you run the script, review the code to be sure that you trust it.</span></span>
<span data-ttu-id="4c02d-122">Scripts hebben hetzelfde effect als elk uitvoerbaar programma.</span><span class="sxs-lookup"><span data-stu-id="4c02d-122">Scripts have the same effect as any executable program.</span></span>

<span data-ttu-id="4c02d-123">Als u een niet-ondertekend script wilt uitvoeren, gebruikt u de cmdlet Unblock-File of gebruikt u de volgende procedure.</span><span class="sxs-lookup"><span data-stu-id="4c02d-123">To run an unsigned script, use the Unblock-File cmdlet or use the following procedure.</span></span>

1. <span data-ttu-id="4c02d-124">Sla het script bestand op uw computer op.</span><span class="sxs-lookup"><span data-stu-id="4c02d-124">Save the script file on your computer.</span></span>
2. <span data-ttu-id="4c02d-125">Klik op Start, klik op mijn computer en zoek het opgeslagen script bestand.</span><span class="sxs-lookup"><span data-stu-id="4c02d-125">Click Start, click My Computer, and locate the saved script file.</span></span>
3. <span data-ttu-id="4c02d-126">Klik met de rechter muisknop op het script bestand en klik vervolgens op Eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-126">Right-click the script file, and then click Properties.</span></span>
4. <span data-ttu-id="4c02d-127">Klik op blok kering opheffen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-127">Click Unblock.</span></span>

<span data-ttu-id="4c02d-128">Als een script dat is gedownload van Internet digitaal is ondertekend, maar u nog niet hebt gekozen voor het vertrouwen van de uitgever, wordt het volgende bericht weer gegeven in Power shell:</span><span class="sxs-lookup"><span data-stu-id="4c02d-128">If a script that was downloaded from the internet is digitally signed, but you have not yet chosen to trust its publisher, PowerShell displays the following message:</span></span>

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

<span data-ttu-id="4c02d-129">Als u de uitgever vertrouwt, selecteert u eenmaal uitvoeren of altijd uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4c02d-129">If you trust the publisher, select "Run once" or "Always run."</span></span> <span data-ttu-id="4c02d-130">Als u de uitgever niet vertrouwt, selecteert u nooit uitvoeren of niet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4c02d-130">If you do not trust the publisher, select either "Never run" or "Do not run."</span></span> <span data-ttu-id="4c02d-131">Als u nooit uitvoeren of altijd uitvoeren selecteert, vraagt Power shell u niet meer om deze uitgever.</span><span class="sxs-lookup"><span data-stu-id="4c02d-131">If you select "Never run" or "Always run," PowerShell will not prompt you again for this publisher.</span></span>

## <a name="methods-of-signing-scripts"></a><span data-ttu-id="4c02d-132">Methoden voor het ondertekenen van scripts</span><span class="sxs-lookup"><span data-stu-id="4c02d-132">Methods of signing scripts</span></span>

<span data-ttu-id="4c02d-133">U kunt de scripts die u schrijft, ondertekenen en de scripts die u uit andere bronnen ontvangt.</span><span class="sxs-lookup"><span data-stu-id="4c02d-133">You can sign the scripts that you write and the scripts that you obtain from other sources.</span></span> <span data-ttu-id="4c02d-134">Controleer voordat u een script gaat ondertekenen elke opdracht om te controleren of het veilig is om uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4c02d-134">Before you sign any script, examine each command to verify that it is safe to run.</span></span>

<span data-ttu-id="4c02d-135">Zie [Aanbevolen procedures voor het ondertekenen van code](/previous-versions/windows/hardware/design/dn653556(v=vs.85))voor aanbevolen procedures voor het ondertekenen van programma code.</span><span class="sxs-lookup"><span data-stu-id="4c02d-135">For best practices about code signing, see [Code-Signing Best Practices](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span></span>

<span data-ttu-id="4c02d-136">Zie [set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)voor meer informatie over het ondertekenen van een script bestand.</span><span class="sxs-lookup"><span data-stu-id="4c02d-136">For more information about how to sign a script file, see [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span></span>

<span data-ttu-id="4c02d-137">Met de `New-SelfSignedCertificate` cmdlet die is geïntroduceerd in de PKI-module in Power shell 3,0, wordt een zelfondertekend certificaat gemaakt dat geschikt is voor testen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-137">The `New-SelfSignedCertificate` cmdlet, introduced in the PKI module in PowerShell 3.0, creates a self-signed certificate that is Appropriate for testing.</span></span> <span data-ttu-id="4c02d-138">Zie het Help-onderwerp voor de cmdlet New-SelfSignedCertificate voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4c02d-138">For more information, see the help topic for the New-SelfSignedCertificate cmdlet.</span></span>

<span data-ttu-id="4c02d-139">Als u een digitale hand tekening aan een script wilt toevoegen, moet u deze ondertekenen met een certificaat voor ondertekening van programma code.</span><span class="sxs-lookup"><span data-stu-id="4c02d-139">To add a digital signature to a script, you must sign it with a code signing certificate.</span></span> <span data-ttu-id="4c02d-140">Twee typen certificaten zijn geschikt voor het ondertekenen van een script bestand:</span><span class="sxs-lookup"><span data-stu-id="4c02d-140">Two types of certificates are suitable for signing a script file:</span></span>

- <span data-ttu-id="4c02d-141">Certificaten die zijn gemaakt door een certificerings instantie: een open bare certificerings instantie verifieert uw identiteit en geeft u een certificaat voor ondertekening van programma code.</span><span class="sxs-lookup"><span data-stu-id="4c02d-141">Certificates that are created by a certification authority: For a fee, a public certification authority verifies your identity and gives you a code signing certificate.</span></span> <span data-ttu-id="4c02d-142">Wanneer u uw certificaat aanschaft bij een betrouw bare certificerings instantie, kunt u uw script delen met gebruikers op andere computers waarop Windows wordt uitgevoerd, omdat deze andere computers de certificerings instantie vertrouwen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-142">When you purchase your certificate from a reputable certification authority, you are able to share your script with users on other computers that are running Windows because those other computers trust the certification authority.</span></span>

- <span data-ttu-id="4c02d-143">Certificaten die u maakt: u kunt een zelfondertekend certificaat maken waarvoor uw computer de autoriteit is die het certificaat maakt.</span><span class="sxs-lookup"><span data-stu-id="4c02d-143">Certificates that you create: You can create a self-signed certificate for which your computer is the authority that creates the certificate.</span></span> <span data-ttu-id="4c02d-144">Dit certificaat is gratis en maakt het mogelijk om scripts op uw computer te schrijven, te ondertekenen en uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="4c02d-144">This certificate is free of charge and enables you to write, sign, and run scripts on your computer.</span></span> <span data-ttu-id="4c02d-145">Een script dat is ondertekend door een zelfondertekend certificaat kan echter niet worden uitgevoerd op andere computers.</span><span class="sxs-lookup"><span data-stu-id="4c02d-145">However, a script signed by a self-signed certificate will not run on other computers.</span></span>

<span data-ttu-id="4c02d-146">Normaal gesp roken gebruikt u een zelfondertekend certificaat alleen voor het ondertekenen van scripts die u voor eigen gebruik schrijft en voor het ondertekenen van scripts die u krijgt van andere bronnen die u hebt geverifieerd om veilig te zijn.</span><span class="sxs-lookup"><span data-stu-id="4c02d-146">Typically, you would use a self-signed certificate only to sign scripts that you write for your own use and to sign scripts that you get from other sources that you have verified to be safe.</span></span> <span data-ttu-id="4c02d-147">Het is niet geschikt voor scripts die worden gedeeld, zelfs binnen een onderneming.</span><span class="sxs-lookup"><span data-stu-id="4c02d-147">It is not appropriate for scripts that will be shared, even within an enterprise.</span></span>

<span data-ttu-id="4c02d-148">Als u een zelfondertekend certificaat maakt, zorg er dan voor dat u sterke beveiliging van persoonlijke sleutels op uw certificaat inschakelt.</span><span class="sxs-lookup"><span data-stu-id="4c02d-148">If you create a self-signed certificate, be sure to enable strong private key protection on your certificate.</span></span> <span data-ttu-id="4c02d-149">Zo voor komt u dat kwaad aardige Program ma's namens u scripts kunnen ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-149">This prevents malicious programs from signing scripts on your behalf.</span></span> <span data-ttu-id="4c02d-150">De instructies zijn aan het einde van dit onderwerp opgenomen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-150">The instructions are included at the end of this topic.</span></span>

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="4c02d-151">Een zelfondertekend certificaat maken</span><span class="sxs-lookup"><span data-stu-id="4c02d-151">Create a self-signed certificate</span></span>

<span data-ttu-id="4c02d-152">Als u een zelfondertekend certificaat wilt maken, gebruikt u de `New-SelfSignedCertificate` cmdlet in de PKI-module.</span><span class="sxs-lookup"><span data-stu-id="4c02d-152">To create a self-signed certificate, use the `New-SelfSignedCertificate` cmdlet in the PKI module.</span></span> <span data-ttu-id="4c02d-153">Deze module is geïntroduceerd in Power Shell 3,0 en is opgenomen in Windows 8 en Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="4c02d-153">This module is introduced in PowerShell 3.0 and is included in Windows 8 and Windows Server 2012.</span></span> <span data-ttu-id="4c02d-154">Zie het Help-onderwerp voor de cmdlet voor meer informatie `New-SelfSignedCertificate` .</span><span class="sxs-lookup"><span data-stu-id="4c02d-154">For more information, see the help topic for the `New-SelfSignedCertificate` cmdlet.</span></span>

<span data-ttu-id="4c02d-155">Gebruik het hulp programma voor het maken van certificaten om een zelfondertekend certificaat te maken in eerdere versies van Windows `MakeCert.exe` .</span><span class="sxs-lookup"><span data-stu-id="4c02d-155">To create a self-signed certificate in earlier versions of Windows, use the Certificate Creation tool `MakeCert.exe`.</span></span> <span data-ttu-id="4c02d-156">Dit hulp programma is opgenomen in de Microsoft .NET SDK (versie 1,1 en hoger) en in de Microsoft Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="4c02d-156">This tool is included in the Microsoft .NET SDK (versions 1.1 and later) and in the Microsoft Windows SDK.</span></span>

<span data-ttu-id="4c02d-157">Zie het [hulp programma voor het maken van certificaten (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80))voor meer informatie over de syntaxis en de parameter beschrijvingen van het hulp programma MakeCert.exe.</span><span class="sxs-lookup"><span data-stu-id="4c02d-157">For more information about the syntax and the parameter descriptions of the MakeCert.exe tool, see [Certificate Creation Tool (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span></span>

<span data-ttu-id="4c02d-158">Als u het hulp programma MakeCert.exe wilt gebruiken om een certificaat te maken, voert u de volgende opdrachten uit in een SDK-opdracht prompt venster.</span><span class="sxs-lookup"><span data-stu-id="4c02d-158">To use the MakeCert.exe tool to create a certificate, run the following commands in an SDK Command Prompt window.</span></span>

<span data-ttu-id="4c02d-159">Opmerking: met de eerste opdracht maakt u een lokale certificerings instantie voor uw computer.</span><span class="sxs-lookup"><span data-stu-id="4c02d-159">Note: The first command creates a local certification authority for your computer.</span></span> <span data-ttu-id="4c02d-160">Met de tweede opdracht wordt een persoonlijk certificaat van de certificerings instantie gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4c02d-160">The second command generates a personal certificate from the certification authority.</span></span>

<span data-ttu-id="4c02d-161">Opmerking: u kunt de opdrachten op exact dezelfde manier kopiëren of typen als ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c02d-161">Note: You can copy or type the commands exactly as they appear.</span></span> <span data-ttu-id="4c02d-162">Er zijn geen vervangingen nodig, maar u kunt de naam van het certificaat wijzigen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-162">No substitutions are necessary, although you can change the certificate name.</span></span>

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

<span data-ttu-id="4c02d-163">Het hulp programma MakeCert.exe vraagt u om een wacht woord voor een persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="4c02d-163">The MakeCert.exe tool will prompt you for a private key password.</span></span> <span data-ttu-id="4c02d-164">Het wacht woord zorgt ervoor dat niemand zonder uw toestemming het certificaat kan gebruiken of openen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-164">The password ensures that no one can use or access the certificate without your consent.</span></span>
<span data-ttu-id="4c02d-165">Maak een wacht woord en voer het in dat u kunt onthouden.</span><span class="sxs-lookup"><span data-stu-id="4c02d-165">Create and enter a password that you can remember.</span></span> <span data-ttu-id="4c02d-166">U gebruikt dit wacht woord later om het certificaat op te halen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-166">You will use this password later to retrieve the certificate.</span></span>

<span data-ttu-id="4c02d-167">Als u wilt controleren of het certificaat correct is gegenereerd, gebruikt u de volgende opdracht om het certificaat op te halen in het certificaat archief op de computer.</span><span class="sxs-lookup"><span data-stu-id="4c02d-167">To verify that the certificate was generated correctly, use the following command to get the certificate in the certificate store on the computer.</span></span> <span data-ttu-id="4c02d-168">Er wordt geen certificaat bestand gevonden in de map van het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="4c02d-168">You will not find a certificate file in the file system directory.</span></span>

<span data-ttu-id="4c02d-169">Typ het volgende bij de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="4c02d-169">At the PowerShell prompt, type:</span></span>

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

<span data-ttu-id="4c02d-170">Met deze opdracht wordt de Power shell-certificaat provider gebruikt voor het weer geven van informatie over het certificaat.</span><span class="sxs-lookup"><span data-stu-id="4c02d-170">This command uses the PowerShell Certificate provider to view information about the certificate.</span></span>

<span data-ttu-id="4c02d-171">Als het certificaat is gemaakt, toont de uitvoer de **vinger afdruk** die het certificaat identificeert in een weer gave die er ongeveer als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="4c02d-171">If the certificate was created, the output shows the **thumbprint** that identifies the certificate in a display that resembles the following:</span></span>

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a><span data-ttu-id="4c02d-172">Een script ondertekenen</span><span class="sxs-lookup"><span data-stu-id="4c02d-172">Sign a script</span></span>

<span data-ttu-id="4c02d-173">Nadat u een zelfondertekend certificaat hebt gemaakt, kunt u scripts ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-173">After you create a self-signed certificate, you can sign scripts.</span></span> <span data-ttu-id="4c02d-174">Als u het **Alles ondertekend** -uitvoerings beleid gebruikt, kunt u met het ondertekenen van een script het script uitvoeren op de computer.</span><span class="sxs-lookup"><span data-stu-id="4c02d-174">If you use the **AllSigned** execution policy, signing a script permits you to run the script on your computer.</span></span>

<span data-ttu-id="4c02d-175">Het volgende voorbeeld script, `Add-Signature.ps1` , tekent een script.</span><span class="sxs-lookup"><span data-stu-id="4c02d-175">The following sample script, `Add-Signature.ps1`, signs a script.</span></span> <span data-ttu-id="4c02d-176">Als u echter het **Alles ondertekend** -uitvoerings beleid gebruikt, moet u het script ondertekenen `Add-Signature.ps1` voordat u het uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4c02d-176">However, if you are using the **AllSigned** execution policy, you must sign the `Add-Signature.ps1` script before you run it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c02d-177">Het script moet worden opgeslagen met behulp van ASCII-of UTF8NoBOM-code ring.</span><span class="sxs-lookup"><span data-stu-id="4c02d-177">The script must be saved using ASCII or UTF8NoBOM encoding.</span></span> <span data-ttu-id="4c02d-178">U kunt een script bestand dat gebruikmaakt van een andere code ring ondertekenen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-178">You can sign a script file that uses a different encoding.</span></span> <span data-ttu-id="4c02d-179">Het script kan echter niet worden uitgevoerd of de module met het script kan niet worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="4c02d-179">But the script fails to run or the module containing the script fails to import.</span></span>

<span data-ttu-id="4c02d-180">Als u dit script wilt gebruiken, kopieert u de volgende tekst naar een tekst bestand en noemt u deze `Add-Signature.ps1` .</span><span class="sxs-lookup"><span data-stu-id="4c02d-180">To use this script, copy the following text into a text file, and name it `Add-Signature.ps1`.</span></span>

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

<span data-ttu-id="4c02d-181">Als u het `Add-Signature.ps1` script bestand wilt ondertekenen, typt u de volgende opdrachten bij de Power shell-opdracht prompt:</span><span class="sxs-lookup"><span data-stu-id="4c02d-181">To sign the `Add-Signature.ps1` script file, type the following commands at the PowerShell command prompt:</span></span>

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

<span data-ttu-id="4c02d-182">Nadat het script is ondertekend, kunt u het uitvoeren op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="4c02d-182">After the script is signed, you can run it on the local computer.</span></span> <span data-ttu-id="4c02d-183">Het script kan echter niet worden uitgevoerd op computers waarop het Power shell-uitvoerings beleid een digitale hand tekening van een vertrouwde instantie vereist.</span><span class="sxs-lookup"><span data-stu-id="4c02d-183">However, the script will not run on computers on which the PowerShell execution policy requires a digital signature from a trusted authority.</span></span> <span data-ttu-id="4c02d-184">Als u probeert, wordt het volgende fout bericht weer gegeven in Power shell:</span><span class="sxs-lookup"><span data-stu-id="4c02d-184">If you try, PowerShell displays the following error message:</span></span>

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

<span data-ttu-id="4c02d-185">Als in Power shell dit bericht wordt weer gegeven wanneer u een script uitvoert dat u niet hebt geschreven, behandelt u het bestand net zoals u een niet-ondertekend script zou behandelen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-185">If PowerShell displays this message when you run a script that you did not write, treat the file as you would treat any unsigned script.</span></span> <span data-ttu-id="4c02d-186">Controleer de code om te bepalen of u het script kunt vertrouwen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-186">Review the code to determine whether you can trust the script.</span></span>

## <a name="enable-strong-private-key-protection-for-your-certificate"></a><span data-ttu-id="4c02d-187">Sterke beveiliging van persoonlijke sleutels inschakelen voor uw certificaat</span><span class="sxs-lookup"><span data-stu-id="4c02d-187">Enable strong private key protection for your certificate</span></span>

<span data-ttu-id="4c02d-188">Als u een persoonlijk certificaat op uw computer hebt, kunnen kwaadwillende Program ma's namens u mogelijk scripts ondertekenen, waardoor Power shell deze kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4c02d-188">If you have a private certificate on your computer, malicious programs might be able to sign scripts on your behalf, which authorizes PowerShell to run them.</span></span>

<span data-ttu-id="4c02d-189">Gebruik certificaat beheer om `Certmgr.exe` uw handtekening certificaat te exporteren naar een bestand om te voor komen dat namens u automatisch wordt aangemeld `.pfx` .</span><span class="sxs-lookup"><span data-stu-id="4c02d-189">To prevent automated signing on your behalf, use Certificate Manager `Certmgr.exe` to export your signing certificate to a `.pfx` file.</span></span> <span data-ttu-id="4c02d-190">Certificaat beheer is opgenomen in de Microsoft .NET SDK, de Microsoft Windows SDK en in Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4c02d-190">Certificate Manager is included in the Microsoft .NET SDK, the Microsoft Windows SDK, and in internet Explorer.</span></span>

<span data-ttu-id="4c02d-191">Het certificaat exporteren:</span><span class="sxs-lookup"><span data-stu-id="4c02d-191">To export the certificate:</span></span>

1. <span data-ttu-id="4c02d-192">Start certificaat beheer.</span><span class="sxs-lookup"><span data-stu-id="4c02d-192">Start Certificate Manager.</span></span>
2. <span data-ttu-id="4c02d-193">Selecteer het certificaat dat is uitgegeven door de hoofdmap van het lokale Power shell-certificaat.</span><span class="sxs-lookup"><span data-stu-id="4c02d-193">Select the certificate issued by PowerShell Local Certificate Root.</span></span>
3. <span data-ttu-id="4c02d-194">Klik op exporteren om de wizard Certificaat exporteren te starten.</span><span class="sxs-lookup"><span data-stu-id="4c02d-194">Click Export to start the Certificate Export Wizard.</span></span>
4. <span data-ttu-id="4c02d-195">Selecteer Ja, de persoonlijke sleutel exporteren en klik op volgende.</span><span class="sxs-lookup"><span data-stu-id="4c02d-195">Select "Yes, export the private key", and then click Next.</span></span>
5. <span data-ttu-id="4c02d-196">Selecteer ' zware beveiliging inschakelen '.</span><span class="sxs-lookup"><span data-stu-id="4c02d-196">Select "Enable strong protection."</span></span>
6. <span data-ttu-id="4c02d-197">Typ een wacht woord en typ het nogmaals ter bevestiging.</span><span class="sxs-lookup"><span data-stu-id="4c02d-197">Type a password, and then type it again to confirm.</span></span>
7. <span data-ttu-id="4c02d-198">Typ een bestands naam met de extensie. pfx.</span><span class="sxs-lookup"><span data-stu-id="4c02d-198">Type a file name that has the .pfx file name extension.</span></span>
8. <span data-ttu-id="4c02d-199">Klik op Voltooien.</span><span class="sxs-lookup"><span data-stu-id="4c02d-199">Click Finish.</span></span>

<span data-ttu-id="4c02d-200">Het certificaat opnieuw importeren:</span><span class="sxs-lookup"><span data-stu-id="4c02d-200">To re-import the certificate:</span></span>

1. <span data-ttu-id="4c02d-201">Start certificaat beheer.</span><span class="sxs-lookup"><span data-stu-id="4c02d-201">Start Certificate Manager.</span></span>
2. <span data-ttu-id="4c02d-202">Klik op importeren om de wizard Certificaat importeren te starten.</span><span class="sxs-lookup"><span data-stu-id="4c02d-202">Click Import to start the Certificate Import Wizard.</span></span>
3. <span data-ttu-id="4c02d-203">Open op de locatie van het pfx-bestand dat u tijdens het export proces hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4c02d-203">Open to the location of the .pfx file that you created during the export process.</span></span>
4. <span data-ttu-id="4c02d-204">Selecteer op de pagina wacht woord sterke beveiliging met persoonlijke sleutel inschakelen en voer het wacht woord in dat u tijdens het export proces hebt toegewezen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-204">On the Password page, select "Enable strong private key protection", and then enter the password that you assigned during the export process.</span></span>
5. <span data-ttu-id="4c02d-205">Selecteer het persoonlijke certificaat archief.</span><span class="sxs-lookup"><span data-stu-id="4c02d-205">Select the Personal certificate store.</span></span>
6. <span data-ttu-id="4c02d-206">Klik op Voltooien.</span><span class="sxs-lookup"><span data-stu-id="4c02d-206">Click Finish.</span></span>

## <a name="prevent-the-signature-from-expiring"></a><span data-ttu-id="4c02d-207">Voor komen dat de hand tekening verloopt</span><span class="sxs-lookup"><span data-stu-id="4c02d-207">Prevent the signature from expiring</span></span>

<span data-ttu-id="4c02d-208">De digitale hand tekening in een script is geldig totdat het handtekening certificaat is verlopen of zolang een time stamp-server kan controleren of het script is ondertekend terwijl het handtekening certificaat geldig was.</span><span class="sxs-lookup"><span data-stu-id="4c02d-208">The digital signature in a script is valid until the signing certificate expires or as long as a timestamp server can verify that the script was signed while the signing certificate was valid.</span></span>

<span data-ttu-id="4c02d-209">Omdat de meeste handtekening certificaten slechts één jaar geldig zijn, zorgt u er met een tijds tempel server voor dat gebruikers uw script lang kunnen gebruiken om te komen.</span><span class="sxs-lookup"><span data-stu-id="4c02d-209">Because most signing certificates are valid for one year only, using a time stamp server ensures that users can use your script for many years to come.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c02d-210">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4c02d-210">See also</span></span>

[<span data-ttu-id="4c02d-211">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="4c02d-211">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="4c02d-212">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="4c02d-212">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="4c02d-213">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="4c02d-213">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="4c02d-214">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="4c02d-214">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="4c02d-215">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="4c02d-215">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

<span data-ttu-id="4c02d-216">[Inleiding tot hand tekening bij programma code](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4c02d-216">[Introduction to Code Signing](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span></span>
