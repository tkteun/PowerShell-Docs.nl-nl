---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Bekende problemen in WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145129"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="eb0c2-103">Bekende problemen in WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="eb0c2-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="eb0c2-104">Power shell-snelkoppelingen worden verbroken wanneer deze voor de eerste keer worden gebruikt</span><span class="sxs-lookup"><span data-stu-id="eb0c2-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="eb0c2-105">**Opgelost** Voer een van de volgende acties uit:</span><span class="sxs-lookup"><span data-stu-id="eb0c2-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="eb0c2-106">Klik met de rechter muisknop op de Power shell-snelkoppeling.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="eb0c2-107">Selecteer Windows Power shell om in een niet-verhoogde modus te starten.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="eb0c2-108">Klik met de rechter muisknop op de Power shell-snelkoppeling.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="eb0c2-109">Klik met de rechter muisknop op Windows Power shell en selecteer als administrator uitvoeren om in een verhoogde modus te starten.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="eb0c2-110">Wanneer u een van de bovenstaande acties hebt uitgevoerd, werken de Power shell-sneltoetsen.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="eb0c2-111">Deze acties moeten slechts één keer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="eb0c2-112">Power shell-modules en DSC-Resources rapporteren fouten over ExecutionPolicy in Windows 7</span><span class="sxs-lookup"><span data-stu-id="eb0c2-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="eb0c2-113">In Windows 7 kan het gebruik van Power shell-modules en DSC-resources leiden tot fouten die zijn gerapporteerd over ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="eb0c2-114">**Opgelost** Stel de ExecutionPolicy in op **RemoteSigned** door de volgende opdracht uit te voeren in een Power shell-sessie met verhoogde bevoegdheden (als administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="eb0c2-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="eb0c2-115">Verbinding maken met een oud extern Exchange-eind punt veroorzaakt een crash</span><span class="sxs-lookup"><span data-stu-id="eb0c2-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="eb0c2-116">Het oude Exchange-eind punt wordt omgeleid naar een nieuw eind punt.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="eb0c2-117">Er is een fout in de omleidings logica die resulteert in een crash.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="eb0c2-118">**Opgelost** Maak rechtstreeks verbinding met het nieuwe eind punt.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="eb0c2-119">De functie logboek registratie van software-inventarisatie is foutief gestopt na de installatie van WMF 5,0 op Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="eb0c2-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="eb0c2-120">Bij de installatie van WMF 5,0 op een Windows Server 2012 R2 waarop SIL al wordt uitgevoerd, wordt de functie logboek registratie van software-inventarisatie na installatie foutief gestopt.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="eb0c2-121">**Opgelost** Voer de `Start-SilLogging` cmdlet eenmaal na de WMF-installatie uit, terwijl het installatie proces de functie voor logboek registratie van software-inventarisatie foutievelijk stoppen.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="eb0c2-122">`Get-ChildItem`werkt niet als-LiteralPath en-recursieve samen worden gebruikt</span><span class="sxs-lookup"><span data-stu-id="eb0c2-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="eb0c2-123">Als een mapnaam een ongeldig Joker teken bevat, `Get-ChildItem` worden er geen verwachte resultaten gegenereerd wanneer zowel LiteralPath als-recursief worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="eb0c2-124">**Opgelost** Niet ideaal, maar de huidige tijdelijke oplossing is het implementeren van recursie in het script in plaats van te vertrouwen op de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="eb0c2-125">Sysprep mislukt na installatie van WMF 5,0</span><span class="sxs-lookup"><span data-stu-id="eb0c2-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="eb0c2-126">Er zijn twee tijdelijke oplossingen voor dit probleem, afhankelijk van de versie van Windows Server die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="eb0c2-127">**Opgelost**</span><span class="sxs-lookup"><span data-stu-id="eb0c2-127">**Resolution:**</span></span>

- <span data-ttu-id="eb0c2-128">Voor systemen met **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="eb0c2-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="eb0c2-129">Power shell openen als beheerder</span><span class="sxs-lookup"><span data-stu-id="eb0c2-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="eb0c2-130">Voer de volgende opdracht uit</span><span class="sxs-lookup"><span data-stu-id="eb0c2-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="eb0c2-131">Voer de opdracht uit en negeer de fout, zoals ze worden verwacht.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="eb0c2-132">De bestanden in de map \Windows\System32\Logfiles\SIL\ verwijderen</span><span class="sxs-lookup"><span data-stu-id="eb0c2-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="eb0c2-133">Installeer alle beschik bare belang rijke Windows-updates en start de Sysyprep-bewerking normaal.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="eb0c2-134">Voor systemen met **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="eb0c2-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="eb0c2-135">Meld u aan als beheerder nadat u WMF 5,0 op de server hebt geïnstalleerd als Sysprep.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="eb0c2-136">Kopieer Generize. XML vanuit een `\Windows\System32\Sysprep\ActionFiles\` map naar een locatie buiten de Windows-map `C:\` , bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="eb0c2-137">Open uw generaliseer. XML-kopie met Klad blok.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="eb0c2-138">Zoek en verwijder de volgende tekst, één exemplaar van elke moet worden verwijderd (ze worden bijna het einde van het document).</span><span class="sxs-lookup"><span data-stu-id="eb0c2-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="eb0c2-139">Sla de bewerkte kopie van generaliseer. XML op en sluit het bestand.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="eb0c2-140">Open een opdracht prompt als beheerder</span><span class="sxs-lookup"><span data-stu-id="eb0c2-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="eb0c2-141">Voer de volgende opdracht uit om eigenaar te worden van het bestand generalize. XML in de map System32:</span><span class="sxs-lookup"><span data-stu-id="eb0c2-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="eb0c2-142">Voer de volgende opdracht uit om de juiste machtigingen voor het bestand in te stellen:</span><span class="sxs-lookup"><span data-stu-id="eb0c2-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="eb0c2-143">Beantwoord Ja bij de vraag om bevestiging.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="eb0c2-144">Houd er `<AdministratorUserName>` rekening mee dat moet worden vervangen door de gebruikers naam die beheerder is op de computer.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="eb0c2-145">Bijvoorbeeld ' Administrator '.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="eb0c2-146">Kopieer het bestand dat u hebt bewerkt en opgeslagen naar de Sysprep-map met behulp van de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="eb0c2-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="eb0c2-147">Antwoord Ja om te overschrijven (Houd er rekening mee dat als er geen prompt is om te overschrijven, Controleer het ingevoerde pad).</span><span class="sxs-lookup"><span data-stu-id="eb0c2-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="eb0c2-148">Er wordt van uitgegaan dat uw bewerkte kopie van generalize. XML is gekopieerd naar C:\.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="eb0c2-149">Generalize. XML wordt nu bijgewerkt met de tijdelijke oplossing.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="eb0c2-150">Voer Sysprep uit met de optie generalize ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-150">Please run Sysprep with the generalize option enabled.</span></span>