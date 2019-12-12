---
ms.date: 08/23/2017
keywords: Power shell, cmdlet
title: Windows Power shell-Internet toegang verwijderen
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058136"
---
# <a name="uninstall-windows-powershell-web-access"></a>Windows PowerShell-internettoegang verwijderen

Bijgewerkt: 24 juni 2013

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

Met de stappen in dit onderwerp wordt de Windows Power shell-website voor webtoegang en de bijbehorende toepassing verwijderd van de gateway server waarop deze is geïnstalleerd.

## <a name="notify-users"></a>Gebruikers op de hoogte stellen

Voordat u begint, moet u gebruikers van de webconsole laten weten dat u de website gaat verwijderen.

Als u Windows Power shell-webtoegang verwijdert, worden IIS of andere functies die automatisch zijn geïnstalleerd, niet verwijderd omdat deze door Windows Power shell Web Access moeten worden uitgevoerd.
Het verwijderings proces verlaat de functies die zijn geïnstalleerd waarbij Windows Power shell-webtoegang afhankelijk is. u kunt deze functies afzonderlijk verwijderen, indien nodig.

## <a name="recommended-quick-uninstallation"></a>Aanbevolen (snelle) verwijdering

In de procedures in deze sectie wordt beschreven hoe u beide kunt verwijderen:

- de Web Access-webtoepassing voor Windows Power shell en
- de functie voor Internet toegang van Windows Power shell

met behulp van Windows Power shell-cmdlets.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Stap 1: de webtoepassing verwijderen met behulp van cmdlets

1. Voer een van de volgende handelingen uit om een Windows Power shell-sessie te openen.

    -   Klik op het Windows-bureau blad met de rechter muisknop op **Windows Power shell** op de taak balk.

    -   Klik in het Windows- **Start** scherm op **Windows Power shell**.

2. Typ `Uninstall-PswaWebApplication`en druk vervolgens op **Enter**.
   1. Als u uw eigen aangepaste websitenaam hebt opgegeven, voegt u de parameter `-WebsiteName` toe aan de opdracht en geeft u de naam van de website op.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Als u een aangepaste webtoepassing hebt gebruikt (niet de standaard toepassing, **pswa**, voegt u de para meter `-WebApplicationName` toe aan de opdracht en geeft u de naam van de webtoepassing op.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Als u een testcertificaat gebruikt, voegt de parameter `DeleteTestCertificate` toe aan de cmdlet, zoals wordt aangegeven in het volgende voorbeeld.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Stap 2: Windows Power shell-Internet toegang verwijderen met behulp van cmdlets

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen. Als al een sessie is geopend, gaat u naar de volgende stap.

    -   Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.

    -   Klik op het Windows- **Start** scherm met de rechter muisknop op **Windows Power shell**en klik vervolgens op **als administrator uitvoeren**.

1. Typ het volgende en druk vervolgens op **Enter**, waarbij *computer_name* staat voor een externe server waarvan u Windows Power shell-Internet toegang wilt verwijderen. Met de parameter `-Restart` worden de doelservers zo nodig automatisch opnieuw opgestart.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Als u functies en onderdelen van een offline-VHD wilt verwijderen, voegt u zowel de parameter `-ComputerName` als de parameter `-VHD` toe. De parameter `-ComputerName` bevat de naam van de server waaraan de VHD moet worden gekoppeld en de parameter `-VHD` bevat het pad naar het VHD-bestand op de opgegeven server.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Als het verwijderen is voltooid, controleert u of u Windows Power shell-Internet toegang hebt verwijderd door de pagina **alle servers** in Serverbeheer te openen, een server te selecteren waarvan u de functie hebt verwijderd en de tegel **functies en onderdelen** op de pagina voor de geselecteerde server weer te geven.

    U kunt ook de `Get-WindowsFeature`-cmdlet uitvoeren die gericht is op de geselecteerde server (Get-WindowsFeature-ComputerName &lt;*computer_name*&gt;) om een lijst weer te geven met functies en onderdelen die op de server zijn geïnstalleerd.

## <a name="custom-uninstallation"></a>Aangepaste verwijdering

Met de procedures in deze sectie kunt u zowel de Windows Power shell Web Access-webtoepassing als de Windows Power shell Web Access-functie verwijderen met de wizard functies en onderdelen verwijderen in Serverbeheer en de IIS-beheer console.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Stap 1: de webtoepassing verwijderen met IIS-beheer


1. Open de IIS-beheerconsole op een van de volgende manieren. Als de console al is geopend, gaat u naar de volgende stap.

    -   Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Klik in het menu **extra** in Serverbeheer op **Internet Information Services (IIS) Manager**.

    -   Typ op het **Start** scherm van Windows een deel van de naam **Internet Information Services (IIS) Manager**. Klik op de snelkoppeling wanneer deze wordt weer gegeven in de **apps** -resultaten.

1. Selecteer in het structuur deel venster van de IIS-beheerder de website waarop de webtoepassing Windows Power shell Web Access wordt uitgevoerd.

1. Klik in het deel venster **acties** onder **website beheren**op **stoppen**.

1. Klik in het structuur deel venster met de rechter muisknop op de webtoepassing op de website met de webtoepassing Windows Power shell Web Access en klik vervolgens op **verwijderen**.

1. Selecteer **toepassings groepen**in het structuur venster, selecteer de map Windows Power shell Web Access-toepassings groep, klik op **stoppen** in het deel venster **acties** en klik vervolgens op **verwijderen** in het inhouds venster.

1. Sluit IIS-beheer.

> Opmerking voor ![](images/SecurityNote.jpeg)**Waarschuwing:**
>
> Het certificaat wordt hierbij niet verwijderd.
>
> Als u een zelfondertekend certificaat hebt gemaakt of een testcertificaat hebt gebruikt en dit wilt verwijderen, verwijdert u het certificaat in IIS-beheer.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Stap 2: Windows Power shell-Internet toegang verwijderen met de wizard functies en onderdelen verwijderen

1. Als Serverbeheer al geopend is, gaat u naar de volgende stap. Als Serverbeheer niet al geopend is, op een van de volgende manieren openen.

    -   Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows.

    -   Klik op **Serverbeheer**in het **Start** scherm van Windows.

1. Op de **beheren** menu, klikt u op **functies en onderdelen verwijderen**.

1. Selecteer op de pagina **doel server selecteren** de server of offline-VHD waarvan u de functie wilt verwijderen. Als u een offline-VHD wilt selecteren, kiest u eerst de server waaraan u de VHD wilt koppelen en selecteert u vervolgens het VHD-bestand. Nadat u de doelserver hebt geselecteerd, klikt u op **volgende**.

1. Klik nogmaals op **volgende** om naar de pagina **onderdelen verwijderen** te gaan.

1. Schakel het selectie vakje voor **Windows Power shell-Internet toegang**uit en klik op **volgende**.

1. Klik op de pagina **geselecteerde items voor verwijderen bevestigen** op **verwijderen**.

## <a name="see-also"></a>Zie ook

- [Windows Power shell-webtoegang installeren en gebruiken](install-and-use-windows-powershell-web-access.md)
- [Help voor IIS-beheer 7,0](https://technet.microsoft.com/library/cc732664.aspx)