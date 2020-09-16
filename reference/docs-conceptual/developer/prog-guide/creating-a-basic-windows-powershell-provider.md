---
title: Een eenvoudige Windows Power shell-provider maken | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.openlocfilehash: 16cadb6099bb4f315bacda4aea617b89f9af5626
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787220"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Een eenvoudige Windows PowerShell-provider ontwerpen

Dit onderwerp is het begin punt voor het leren van het maken van een Windows Power shell-provider. De hier beschreven basis provider biedt methoden voor het starten en stoppen van de provider, maar deze provider biedt geen manier om toegang te krijgen tot een gegevens archief of om gegevens op te halen of in te stellen in het gegevens archief, maar biedt de basis functionaliteit die is vereist voor alle providers.

Zoals eerder vermeld, implementeert de Basic-provider die hier wordt beschreven, methoden voor het starten en stoppen van de provider. De Windows Power shell-runtime roept deze methoden aan om de provider te initialiseren en op te starten.

> [!NOTE]
> U kunt een voor beeld van deze provider vinden in het AccessDBSampleProvider01.cs-bestand van Windows Power shell.

## <a name="defining-the-windows-powershell-provider-class"></a>De Windows Power shell-provider klasse definiëren

De eerste stap bij het maken van een Windows Power shell-provider is het definiëren van de .NET-klasse. Deze basis provider definieert een klasse `AccessDBProvider` met de naam die is afgeleid van de basis klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

Het is raadzaam om uw provider klassen in een `Providers` naam ruimte van uw API-naam ruimte te plaatsen, bijvoorbeeld xxx. Power shell. providers. Deze provider maakt gebruik `Microsoft.Samples.PowerShell.Provider` van de naam ruimte, waarin alle voor beelden van Windows Power shell-providers worden uitgevoerd.

> [!NOTE]
> De klasse voor een Windows Power shell-provider moet expliciet als openbaar worden gemarkeerd. Klassen die niet als openbaar zijn gemarkeerd, zijn standaard intern en worden niet gevonden door de Windows Power shell-runtime.

Dit is de klassedefinitie voor deze basis provider:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="23-24":::

Rechts voor de klassedefinitie moet u het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) declareren met de syntaxis [CmdletProvider ()].

U kunt kenmerk trefwoorden instellen om de klasse zo nodig verder te declareren. U ziet dat het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) dat hier is gedeclareerd, twee para meters bevat. De eerste kenmerk parameter geeft de beschrijvende naam op voor de provider, die de gebruiker later kan wijzigen. Met de tweede para meter geeft u de door Windows Power shell gedefinieerde mogelijkheden op die de provider beschikbaar maakt voor de Windows Power shell-runtime tijdens het verwerken van opdrachten. De mogelijke waarden voor de provider mogelijkheden worden gedefinieerd door de inventarisatie [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Omdat dit een basis provider is, ondersteunt deze geen mogelijkheden.

> [!NOTE]
> De volledig gekwalificeerde naam van de Windows Power shell-provider bevat de assembly naam en andere kenmerken die door Windows Power shell worden bepaald na registratie van de provider.

## <a name="defining-provider-specific-state-information"></a>Provider-specifieke status informatie definiëren

De basis klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) en alle afgeleide klassen worden beschouwd als stateless omdat de Windows Power shell-runtime alleen provider instanties maakt als dat nodig is. Als uw provider echter volledig beheer en status onderhoud voor providerspecifieke gegevens vereist, moet een klasse worden afgeleid van de klasse [System. Management. Automation. Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) . Uw afgeleide klasse moet de leden definiëren die nodig zijn om de status te behouden, zodat de providerspecifieke gegevens kunnen worden geopend wanneer de Windows Power shell-runtime de methode [System. Management. Automation. provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) aanroept om de provider te initialiseren.

Een Windows Power shell-provider kan ook de status op basis van een verbinding onderhouden. Zie [een Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md)voor meer informatie over het onderhouden van de verbindings status.

## <a name="initializing-the-provider"></a>De provider initialiseren

Voor het initialiseren van de provider roept Windows Power shell runtime de methode [System. Management. Automation. provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) aan wanneer Windows Power shell wordt gestart. De provider kan de standaard implementatie van deze methode echter gebruiken. dit retourneert eenvoudigweg het object [System. Management. Automation. Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) dat uw provider beschrijft. In het geval dat u aanvullende initialisatie gegevens wilt toevoegen, moet u echter uw eigen [System. Management. Automation. provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) -methode implementeren die een gewijzigde versie retourneert van het object [System. Management. Automation. Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) dat wordt door gegeven aan uw provider. Over het algemeen moet deze methode het opgegeven [System. Management. Automation. Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) -object retour neren dat hieraan is door gegeven of een aangepast [System. Management. Automation. Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) -object dat andere initialisatie gegevens bevat.

Deze basis provider overschrijft deze methode niet. De volgende code toont echter de standaard implementatie van deze methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

De provider kan de status van providerspecifieke informatie onderhouden, zoals wordt beschreven in [provider-specifieke gegevens status definiëren](#defining-provider-specific-state-information). In dit geval moet uw implementatie de methode [System. Management. Automation. provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) overschrijven om een exemplaar van de afgeleide klasse te retour neren.

## <a name="start-dynamic-parameters"></a>Dynamische para meters starten

Voor de implementatie van de provider van de methode [System. Management. Automation. provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) zijn mogelijk extra para meters vereist. In dit geval moet de provider de methode [System. Management. Automation. provider. Cmdletprovider. Startdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) overschrijven en een object retour neren met eigenschappen en velden met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object.

Deze basis provider overschrijft deze methode niet. De volgende code toont echter de standaard implementatie van deze methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>De initialisatie van de provider ongedaan te doen

Als u resources wilt vrijmaken die worden gebruikt door de Windows Power shell-provider, moet uw provider zijn eigen [System. Management. Automation. provider. Cmdletprovider. stop *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) -methode implementeren. Deze methode wordt aangeroepen door de Windows Power shell-runtime om de initialisatie van de provider bij het sluiten van een sessie ongedaan te maakt.

Deze basis provider overschrijft deze methode niet. De volgende code toont echter de standaard implementatie van deze methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Code voorbeeld

Zie [AccessDbProviderSample01 code sample](./accessdbprovidersample01-code-sample.md)voor een volledige voorbeeld code.

## <a name="testing-the-windows-powershell-provider"></a>De Windows Power shell-provider testen

Als uw Windows Power shell-provider is geregistreerd bij Windows Power shell, kunt u deze testen door de ondersteunde cmdlets uit te voeren op de opdracht regel. Voor deze Basic-provider voert u de nieuwe shell uit en gebruikt `Get-PSProvider` u de cmdlet om de lijst met providers op te halen en ervoor te zorgen dat de AccessDb-provider aanwezig is.

```powershell
Get-PSProvider
```

De volgende uitvoer wordt weergegeven:

```Output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Zie ook

[Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md)

[Uw Windows PowerShell-provider ontwerpen](./designing-your-windows-powershell-provider.md)
