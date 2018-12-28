---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: windows powershell-internettoegang verwijderen
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404514"
---
# <a name="uninstall-windows-powershell-web-access"></a>Windows PowerShell-internettoegang verwijderen

Bijgewerkt: 24: juni 2013

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

De stappen in dit onderwerp worden de website van Windows PowerShell-webtoegang en de bijbehorende toepassing verwijderen van de gatewayserver waarop deze is geïnstalleerd.

## <a name="notify-users"></a>Gebruikers een melding ontvangen

Voordat u begint, moet u gebruikers van de webconsole laten weten dat u de website gaat verwijderen.

Windows PowerShell-webtoegang verwijderen, worden IIS of andere onderdelen die automatisch zijn geïnstalleerd omdat de Windows PowerShell-webtoegang vereist is om uit te voeren niet verwijderd.
De verwijdering blijven onderdelen geïnstalleerd waarop Windows PowerShell-webtoegang afhankelijke is; indien nodig, kunt u deze functies afzonderlijk verwijderen.

## <a name="recommended-quick-uninstallation"></a>Aanbevolen (snelle) verwijdering

Procedures in deze sectie kunt u beide verwijderen:

- de web-App van Windows PowerShell-webtoegang en
- de functie Windows PowerShell-webtoegang

met behulp van Windows PowerShell-cmdlets.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Stap 1: Verwijderen van de web-App met behulp van cmdlets

1. Doe het volgende om een Windows PowerShell-sessie te openen.

    -   Op het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk.

    -   Op de Windows **Start** scherm, klikt u op **Windows PowerShell**.

2. Type `Uninstall-PswaWebApplication`, en druk vervolgens op **Enter**.
   1. Als u uw eigen aangepaste websitenaam hebt opgegeven, voegt u de parameter `-WebsiteName` toe aan de opdracht en geeft u de naam van de website op.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Als u een aangepaste webtoepassing hebt gebruikt (niet de standaardtoepassing, **pswa**, voeg de `-WebApplicationName` parameter aan de opdracht en geeft u de naam van de web-App.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Als u een testcertificaat gebruikt, voegt de parameter `DeleteTestCertificate` toe aan de cmdlet, zoals wordt aangegeven in het volgende voorbeeld.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Stap 2: Windows PowerShell-internettoegang met behulp van cmdlets verwijderen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen. Als al een sessie is geopend, gaat u naar de volgende stap.

    -   Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.

    -   Op de Windows **Start** met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.

1. Typ het volgende en druk vervolgens op **Enter**, waarbij *computer_name* vertegenwoordigt een externe server van waaruit u wilt verwijderen van Windows PowerShell-webtoegang. Met de parameter `-Restart` worden de doelservers zo nodig automatisch opnieuw opgestart.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Als u functies en onderdelen van een offline-VHD wilt verwijderen, voegt u zowel de parameter `-ComputerName` als de parameter `-VHD` toe. De parameter `-ComputerName` bevat de naam van de server waaraan de VHD moet worden gekoppeld en de parameter `-VHD` bevat het pad naar het VHD-bestand op de opgegeven server.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Nadat de verwijdering is voltooid, controleert u of u Windows PowerShell-webtoegang verwijderd door het openen van de **alle Servers** pagina in Serverbeheer, een server waarvan u de functie verwijderd te selecteren en weergeven van de **rollen en Functies** tegel op de pagina voor de geselecteerde server.

    U kunt ook uitvoeren de `Get-WindowsFeature` cmdlet gericht op de geselecteerde server (Get-WindowsFeature - ComputerName &lt; *computer_name*&gt;) om een lijst met functies en onderdelen die zijn geïnstalleerd op de server weer te geven.

## <a name="custom-uninstallation"></a>Aangepaste verwijdering

Procedures in deze sectie kunt u verwijdert u de web-App voor Windows PowerShell-webtoegang en de Windows PowerShell Web Access-functie met behulp van de rollen verwijderen en onderdelen in Serverbeheer en de IIS-beheerconsole.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Stap 1: De web-App met behulp van IIS-beheer verwijderen


1. Open de IIS-beheerconsole op een van de volgende manieren. Als de console al is geopend, gaat u naar de volgende stap.

    -   Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Op de **extra** menu in Serverbeheer, klikt u op **Internet Information Services (IIS) Manager**.

    -   Op de Windows **Start** scherm, typt u een deel van de naam **Internet Information Services (IIS) Manager**. Klik op de snelkoppeling wanneer deze wordt weergegeven de **Apps** resultaten.

1. Selecteer de website waarop de web-App voor Windows PowerShell-webtoegang in het structuurdeelvenster van IIS-beheer.

1. In de **acties** deelvenster onder **Website beheren**, klikt u op **stoppen**.

1. In het structuurdeelvenster met de rechtermuisknop op de web-App in de website waarop de web-App voor Windows PowerShell-webtoegang en klik vervolgens op **verwijderen**.

1. Selecteer in het structuurdeelvenster **toepassingsgroepen**, selecteert u de map met de Windows PowerShell-webtoegang toepassingsgroep, klikt u op **stoppen** in de **acties** in het deelvenster en klik vervolgens op  **Verwijder** in het inhoudsvenster.

1. Sluit IIS-beheer.

> ![Waarschuwing Opmerking](images/SecurityNote.jpeg)**Opmerking**:
>
> Het certificaat wordt hierbij niet verwijderd.
>
> Als u een zelfondertekend certificaat hebt gemaakt of een testcertificaat hebt gebruikt en dit wilt verwijderen, verwijdert u het certificaat in IIS-beheer.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Stap 2: Windows PowerShell-internettoegang met behulp van de verwijderen Wizard functies en onderdelen verwijderen

1. Als Serverbeheer al geopend is, gaat u naar de volgende stap. Als Serverbeheer niet al geopend is, op een van de volgende manieren openen.

    -   Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows.

    -   Op de Windows **Start** scherm, klikt u op **Serverbeheer**.

1. Op de **beheren** menu, klikt u op **functies en onderdelen verwijderen**.

1. Op de **Selecteer doelserver** pagina, selecteert u de server of offline-VHD waarvan u wilt verwijderen van de functie. Als u een offline-VHD wilt selecteren, kiest u eerst de server waaraan u de VHD wilt koppelen en selecteert u vervolgens het VHD-bestand. Nadat u de doelserver hebt geselecteerd, klikt u op **volgende**.

1. Klik op **volgende** opnieuw om over te slaan naar de **onderdelen verwijderen** pagina.

1. Schakel het selectievakje voor **Windows PowerShell-webtoegang**, en klik vervolgens op **volgende**.

1. Op de **verwijdering selecties bevestigen** pagina, klikt u op **verwijderen**.

## <a name="see-also"></a>Zie ook

- [Installeren en gebruiken van Windows PowerShell-internettoegang](install-and-use-windows-powershell-web-access.md)
- [IIS 7.0 Manager Help](https://technet.microsoft.com/library/cc732664.aspx)