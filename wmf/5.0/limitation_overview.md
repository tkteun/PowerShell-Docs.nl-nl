---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186827"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="6e55a-102">Bekende problemen en beperkingen</span><span class="sxs-lookup"><span data-stu-id="6e55a-102">Known Issues and Limitations</span></span>

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="6e55a-103">PowerShell snelkoppelingen worden verbroken wanneer voor de eerste keer gebruikt</span><span class="sxs-lookup"><span data-stu-id="6e55a-103">PowerShell Shortcuts are broken when used for the first time</span></span>
------------------------------------------------------------

<span data-ttu-id="6e55a-104">**Oplossing:** een van de volgende acties uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="6e55a-104">**Resolution:** Perform one of the following actions:</span></span>

1.  <span data-ttu-id="6e55a-105">Klik met de rechtermuisknop op de snelkoppeling PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e55a-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="6e55a-106">Selecteer 'Windows PowerShell' om te starten in een modus zonder verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="6e55a-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2.  <span data-ttu-id="6e55a-107">Klik met de rechtermuisknop op de snelkoppeling PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e55a-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="6e55a-108">Klik met de rechtermuisknop op de 'Windows PowerShell' en 'Als Administrator uitvoeren' om te starten in een modus met uitgebreide bevoegdheden selecteren.</span><span class="sxs-lookup"><span data-stu-id="6e55a-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="6e55a-109">Wanneer u een van de bovengenoemde stappen hebt uitgevoerd, werkt de PowerShell-snelkoppelingen.</span><span class="sxs-lookup"><span data-stu-id="6e55a-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="6e55a-110">Deze acties moeten slechts één keer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6e55a-110">These actions need to be performed only once.</span></span>


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="6e55a-111">PowerShell-Modules en DSC-Resources fouten rapporteren over uitvoeringsbeleid in Windows 7</span><span class="sxs-lookup"><span data-stu-id="6e55a-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>
-------------------------------------------------------------------------------------
<span data-ttu-id="6e55a-112">In Windows 7, het gebruik van PowerShell-modules en DSC-resources mogelijk fouten tot gevolg gerapporteerd over ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="6e55a-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="6e55a-113">**Oplossing:** het uitvoeringsbeleid instellen op RemoteSigned met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):</span><span class="sxs-lookup"><span data-stu-id="6e55a-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="6e55a-114">Verbinding maken met een oude externe Exchange-eindpunt zorgt ervoor dat een crash</span><span class="sxs-lookup"><span data-stu-id="6e55a-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>
------------------------------------------------------------

<span data-ttu-id="6e55a-115">De oude Exchange-eindpunt wordt omgeleid naar een nieuw eindpunt.</span><span class="sxs-lookup"><span data-stu-id="6e55a-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="6e55a-116">Er is een fout in de omleiding logica die als resultaat in een crash.</span><span class="sxs-lookup"><span data-stu-id="6e55a-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="6e55a-117">**Oplossing:** rechtstreeks verbinding maken met het nieuwe eindpunt.</span><span class="sxs-lookup"><span data-stu-id="6e55a-117">**Resolution:** Connect directly to the new endpoint.</span></span>


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="6e55a-118">Functie voor logboekregistratie van inventaris van software wordt ten onrechte gestopt na de installatie van WMF 5.0 op Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6e55a-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>
-------------------------------------------------------------------------------------------------------------

<span data-ttu-id="6e55a-119">Bij het installeren van WMF 5.0 in Windows Server 2012 R2 waarop SIL al wordt uitgevoerd, wordt de functie logboekregistratie van Software-inventaris per ongeluk gestopt na de installatie.</span><span class="sxs-lookup"><span data-stu-id="6e55a-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="6e55a-120">**Oplossing:** voert u de cmdlet Start-SilLogging eenmaal na de installatie van WMF, zoals de installatie foutievelijk de functie logboekregistratie van Software-inventaris stopt.</span><span class="sxs-lookup"><span data-stu-id="6e55a-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="6e55a-121">Get-ChildItem werkt niet als LiteralPath - en - Recurse samen worden gebruikt</span><span class="sxs-lookup"><span data-stu-id="6e55a-121">Get-ChildItem does not work if -LiteralPath and -Recurse are used together</span></span>
--------------------------------------------------------------------------

<span data-ttu-id="6e55a-122">Als de directorynaam van een een ongeldige jokerteken bevat, vervolgens Get-ChildItem wordt niet verwacht resultaten opleveren wanneer zowel - LiteralPath en -Recurse samen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6e55a-122">If a directory name contains an invalid wildcard character, then Get-ChildItem will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="6e55a-123">**Oplossing:** niet ideaal, maar de huidige tijdelijke oplossing is het implementeren van recursie in het script in plaats van afhankelijk zijn van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e55a-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>


<a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="6e55a-124">Sysprep is mislukt nadat WMF 5.0-installatie</span><span class="sxs-lookup"><span data-stu-id="6e55a-124">Sysprep fails after WMF 5.0 installation</span></span>
----------------------------------------

<span data-ttu-id="6e55a-125">Er zijn twee oplossingen voor dit probleem, afhankelijk van de versie van Windows Server worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6e55a-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="6e55a-126">**Oplossing:**</span><span class="sxs-lookup"><span data-stu-id="6e55a-126">**Resolution:**</span></span>
- <span data-ttu-id="6e55a-127">Voor systemen met **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="6e55a-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="6e55a-128">Open Powershell als beheerder</span><span class="sxs-lookup"><span data-stu-id="6e55a-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="6e55a-129">De volgende opdracht uitvoeren</span><span class="sxs-lookup"><span data-stu-id="6e55a-129">Run the following command</span></span>

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. <span data-ttu-id="6e55a-130">Voer de opdracht en de fout negeren als ze worden geacht.</span><span class="sxs-lookup"><span data-stu-id="6e55a-130">Run the command and ignore the error, as they are expected.</span></span>

  ```powershell
    Publish-SilData
   ```
  4. <span data-ttu-id="6e55a-131">Verwijder de bestanden in de map \Windows\System32\Logfiles\SIL\\</span><span class="sxs-lookup"><span data-stu-id="6e55a-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. <span data-ttu-id="6e55a-132">Alle beschikbare belangrijke Windows-Updates installeren en de bewerking Sysyprep normaal.</span><span class="sxs-lookup"><span data-stu-id="6e55a-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="6e55a-133">Voor systemen met **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="6e55a-133">For systems running **Windows Server 2012**</span></span>
  1.    <span data-ttu-id="6e55a-134">Na het installeren van WMF 5.0 op de server worden 'd Sysprep, meld u aan als beheerder.</span><span class="sxs-lookup"><span data-stu-id="6e55a-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2.    <span data-ttu-id="6e55a-135">Kopieer Generize.xml van directory \Windows\System32\Sysprep\ActionFiles\ naar een locatie buiten de Windows-map C:\ bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="6e55a-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3.    <span data-ttu-id="6e55a-136">Open uw Generalize.xml-exemplaar met Kladblok.</span><span class="sxs-lookup"><span data-stu-id="6e55a-136">Open your Generalize.xml copy with notepad.</span></span>
  4.    <span data-ttu-id="6e55a-137">Zoeken en verwijderen van de volgende tekst, één exemplaar van elke moet worden verwijderd (ze zijn aan het einde van het document).</span><span class="sxs-lookup"><span data-stu-id="6e55a-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    <span data-ttu-id="6e55a-138">Sla de bewerkte kopie van Generalize.xml op en sluit het bestand.</span><span class="sxs-lookup"><span data-stu-id="6e55a-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6.    <span data-ttu-id="6e55a-139">Open een opdrachtprompt als beheerder</span><span class="sxs-lookup"><span data-stu-id="6e55a-139">Open a command prompt as administrator</span></span>
  7.    <span data-ttu-id="6e55a-140">Voer de volgende opdracht eigenaar van het bestand Generalize.xml in de map system32:</span><span class="sxs-lookup"><span data-stu-id="6e55a-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    <span data-ttu-id="6e55a-141">Voer de volgende opdracht om de juiste machtigingen instellen voor het bestand:</span><span class="sxs-lookup"><span data-stu-id="6e55a-141">Run the following command to set appropriate permission on the file:</span></span>

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * <span data-ttu-id="6e55a-142">Ja bij de prompt voor bevestiging.</span><span class="sxs-lookup"><span data-stu-id="6e55a-142">Answer Yes at the prompt for confirmation.</span></span>
      * <span data-ttu-id="6e55a-143">Houd er rekening mee dat `<AdministratorUserName>` moet worden vervangen door de gebruikersnaam die beheerder is op de machine.</span><span class="sxs-lookup"><span data-stu-id="6e55a-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="6e55a-144">Bijvoorbeeld 'Beheerder'.</span><span class="sxs-lookup"><span data-stu-id="6e55a-144">For example, "Administrator".</span></span>

  9.    <span data-ttu-id="6e55a-145">Kopieer het bestand dat u bewerkt en opgeslagen naar de Sysprep-map met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="6e55a-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * <span data-ttu-id="6e55a-146">Ja (opmerking die wordt u niet gevraagd om te overschrijven, double Controleer in het opgegeven pad) overschrijven.</span><span class="sxs-lookup"><span data-stu-id="6e55a-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
      * <span data-ttu-id="6e55a-147">Wordt ervan uitgegaan dat de bewerkte kopie van Generalize.xml is gekopieerd naar C:\.</span><span class="sxs-lookup"><span data-stu-id="6e55a-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10.   <span data-ttu-id="6e55a-148">Generalize.XML is nu bijgewerkt met de tijdelijke oplossing.</span><span class="sxs-lookup"><span data-stu-id="6e55a-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="6e55a-149">Voer Sysprep met de optie generalize is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="6e55a-149">Please run Sysprep with the generalize option enabled.</span></span>
