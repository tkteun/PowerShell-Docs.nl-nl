---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="known-issues-and-limitations"></a>Bekende problemen en beperkingen

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>PowerShell snelkoppelingen worden verbroken wanneer voor de eerste keer gebruikt
------------------------------------------------------------

**Oplossing:** een van de volgende acties uitvoeren:

1.  Klik met de rechtermuisknop op de snelkoppeling PowerShell. Selecteer 'Windows PowerShell' om te starten in een modus zonder verhoogde bevoegdheden.
2.  Klik met de rechtermuisknop op de snelkoppeling PowerShell. Klik met de rechtermuisknop op de 'Windows PowerShell' en 'Als Administrator uitvoeren' om te starten in een modus met uitgebreide bevoegdheden selecteren.

Wanneer u een van de bovengenoemde stappen hebt uitgevoerd, werkt de PowerShell-snelkoppelingen. Deze acties moeten slechts één keer worden uitgevoerd.


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell-Modules en DSC-Resources fouten rapporteren over uitvoeringsbeleid in Windows 7
-------------------------------------------------------------------------------------
In Windows 7, het gebruik van PowerShell-modules en DSC-resources mogelijk fouten tot gevolg gerapporteerd over ExecutionPolicy.

**Oplossing:** het uitvoeringsbeleid instellen op RemoteSigned met de volgende opdracht in een verhoogde PowerShell-sessie (als Administrator uitvoeren):

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Verbinding maken met een oude externe Exchange-eindpunt zorgt ervoor dat een crash
------------------------------------------------------------

De oude Exchange-eindpunt wordt omgeleid naar een nieuw eindpunt. Er is een fout in de omleiding logica die als resultaat in een crash.

**Oplossing:** rechtstreeks verbinding maken met het nieuwe eindpunt.


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Functie voor logboekregistratie van inventaris van software wordt ten onrechte gestopt na de installatie van WMF 5.0 op Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

Bij het installeren van WMF 5.0 in Windows Server 2012 R2 waarop SIL al wordt uitgevoerd, wordt de functie logboekregistratie van Software-inventaris per ongeluk gestopt na de installatie.

**Oplossing:** voert u de cmdlet Start-SilLogging eenmaal na de installatie van WMF, zoals de installatie foutievelijk de functie logboekregistratie van Software-inventaris stopt.

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>Get-ChildItem werkt niet als LiteralPath - en - Recurse samen worden gebruikt
--------------------------------------------------------------------------

Als de directorynaam van een een ongeldige jokerteken bevat, vervolgens Get-ChildItem wordt niet verwacht resultaten opleveren wanneer zowel - LiteralPath en -Recurse samen worden gebruikt.

**Oplossing:** niet ideaal, maar de huidige tijdelijke oplossing is het implementeren van recursie in het script in plaats van afhankelijk zijn van de cmdlet.


<a name="sysprep-fails-after-wmf-50-installation"></a>Sysprep is mislukt nadat WMF 5.0-installatie
----------------------------------------

Er zijn twee oplossingen voor dit probleem, afhankelijk van de versie van Windows Server worden uitgevoerd.

**Oplossing:**
- Voor systemen met **Windows Server 2008 R2**
  1. Open Powershell als beheerder
  2. De volgende opdracht uitvoeren

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. Voer de opdracht en de fout negeren als ze worden geacht.

  ```powershell
    Publish-SilData
   ```
  4. Verwijder de bestanden in de map \Windows\System32\Logfiles\SIL\

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. Alle beschikbare belangrijke Windows-Updates installeren en de bewerking Sysyprep normaal.

- Voor systemen met **Windows Server 2012**
  1.    Na het installeren van WMF 5.0 op de server worden 'd Sysprep, meld u aan als beheerder.
  2.    Kopieer Generize.xml van directory \Windows\System32\Sysprep\ActionFiles\ naar een locatie buiten de Windows-map C:\ bijvoorbeeld.
  3.    Open uw Generalize.xml-exemplaar met Kladblok.
  4.    Zoeken en verwijderen van de volgende tekst, één exemplaar van elke moet worden verwijderd (ze zijn aan het einde van het document).

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    Sla de bewerkte kopie van Generalize.xml op en sluit het bestand.
  6.    Open een opdrachtprompt als beheerder
  7.    Voer de volgende opdracht eigenaar van het bestand Generalize.xml in de map system32:

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    Voer de volgende opdracht om de juiste machtigingen instellen voor het bestand:

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * Ja bij de prompt voor bevestiging.
      * Houd er rekening mee dat `<AdministratorUserName>` moet worden vervangen door de gebruikersnaam die beheerder is op de machine. Bijvoorbeeld 'Beheerder'.

  9.    Kopieer het bestand dat u bewerkt en opgeslagen naar de Sysprep-map met de volgende opdracht:

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * Ja (opmerking die wordt u niet gevraagd om te overschrijven, double Controleer in het opgegeven pad) overschrijven.
      * Wordt ervan uitgegaan dat de bewerkte kopie van Generalize.xml is gekopieerd naar C:\.

  10.   Generalize.XML is nu bijgewerkt met de tijdelijke oplossing. Voer Sysprep met de optie generalize is ingeschakeld.
