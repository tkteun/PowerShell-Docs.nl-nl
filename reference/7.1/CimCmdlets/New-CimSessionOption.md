---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 08e01b73e7e44ca6fc80920e4a2dfe8856ba317f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251387"
---
# <span data-ttu-id="0788b-103">New-CimSessionOption</span><span class="sxs-lookup"><span data-stu-id="0788b-103">New-CimSessionOption</span></span>

## <span data-ttu-id="0788b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0788b-104">SYNOPSIS</span></span>
<span data-ttu-id="0788b-105">Hiermee geeft u geavanceerde opties voor de cmdlet New-CimSession op.</span><span class="sxs-lookup"><span data-stu-id="0788b-105">Specifies advanced options for the New-CimSession cmdlet.</span></span>

## <span data-ttu-id="0788b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0788b-106">SYNTAX</span></span>

### <span data-ttu-id="0788b-107">ProtocolTypeSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="0788b-107">ProtocolTypeSet (Default)</span></span>

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### <span data-ttu-id="0788b-108">WSManParameterSet</span><span class="sxs-lookup"><span data-stu-id="0788b-108">WSManParameterSet</span></span>

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### <span data-ttu-id="0788b-109">DcomParameterSet</span><span class="sxs-lookup"><span data-stu-id="0788b-109">DcomParameterSet</span></span>

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## <span data-ttu-id="0788b-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0788b-110">DESCRIPTION</span></span>

<span data-ttu-id="0788b-111">`New-CimSessionOption`Met de cmdlet maakt u een instantie van een CIM-sessie opties-object.</span><span class="sxs-lookup"><span data-stu-id="0788b-111">The `New-CimSessionOption` cmdlet creates an instance of a CIM session options object.</span></span> <span data-ttu-id="0788b-112">U gebruikt een CIM-sessie opties object als invoer voor de `New-CimSession` cmdlet om de opties voor een CIM-sessie op te geven.</span><span class="sxs-lookup"><span data-stu-id="0788b-112">You use a CIM session options object as input to the `New-CimSession` cmdlet to specify the options for a CIM session.</span></span>

<span data-ttu-id="0788b-113">Deze cmdlet heeft twee parameter sets: één voor WsMan-opties en één voor opties voor gedistribueerde Component Object Model (DCOM).</span><span class="sxs-lookup"><span data-stu-id="0788b-113">This cmdlet has two parameter sets, one for WsMan options and one for Distributed Component Object Model (DCOM) options.</span></span> <span data-ttu-id="0788b-114">Afhankelijk van de para meters die u gebruikt, retourneert de cmdlet een exemplaar van DCOM-sessie opties of worden WsMan-sessie opties geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0788b-114">Depending on which parameters you use, the cmdlet returns either an instance of DCOM session options or returns WsMan session options.</span></span>

## <span data-ttu-id="0788b-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0788b-115">EXAMPLES</span></span>

### <span data-ttu-id="0788b-116">Voor beeld 1: een CIM-sessie opties-object maken voor DCOM</span><span class="sxs-lookup"><span data-stu-id="0788b-116">Example 1: Create a CIM session options object for DCOM</span></span>

<span data-ttu-id="0788b-117">In dit voor beeld wordt een CIM-sessie opties-object voor het DCOM-protocol gemaakt en opgeslagen in een variabele met de naam `$so` .</span><span class="sxs-lookup"><span data-stu-id="0788b-117">This example creates a CIM session options object for the DCOM protocol and stores it in a variable named `$so`.</span></span> <span data-ttu-id="0788b-118">De inhoud van de variabele wordt vervolgens door gegeven aan de `New-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0788b-118">The contents of the variable are then passed to the `New-CimSession` cmdlet.</span></span>
<span data-ttu-id="0788b-119">`New-CimSession` maakt vervolgens een nieuwe CIM-sessie met de externe server met de naam Server01, met behulp van de opties die zijn gedefinieerd in de variabele.</span><span class="sxs-lookup"><span data-stu-id="0788b-119">`New-CimSession` then creates a new CIM session with the remote server named Server01, using the options defined in the variable.</span></span>

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### <span data-ttu-id="0788b-120">Voor beeld 2: een CIM-sessie opties-object maken voor WsMan</span><span class="sxs-lookup"><span data-stu-id="0788b-120">Example 2: Create a CIM session options object for WsMan</span></span>

<span data-ttu-id="0788b-121">In dit voor beeld wordt een CIM-sessie opties-object gemaakt voor het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="0788b-121">This example creates a CIM session options object for the WsMan protocol.</span></span> <span data-ttu-id="0788b-122">Het object bevat configuratie voor de verificatie modus van **Kerberos** dat is opgegeven door de para meter **ProxyAuthentication** , de referenties die zijn opgegeven door de para meter **ProxyCredential** en geeft aan dat de opdracht de CA-controle moet overs Laan, de CN-controle overs Laan en SSL gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0788b-122">The object contains configuration for the authentication mode of **Kerberos** specified by the **ProxyAuthentication** parameter, the credentials specified by the **ProxyCredential** parameter, and specifies that the command is to skip the CA check, skip the CN check, and use SSL.</span></span>

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### <span data-ttu-id="0788b-123">Voor beeld 3: een CIM-sessie opties-object maken met de opgegeven cultuur</span><span class="sxs-lookup"><span data-stu-id="0788b-123">Example 3: Create a CIM session options object with the culture specified</span></span>

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

<span data-ttu-id="0788b-124">In dit voor beeld wordt de cultuur opgegeven die wordt gebruikt voor de CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="0788b-124">This example specifies the culture that is used for the CIM session.</span></span> <span data-ttu-id="0788b-125">Standaard wordt de cultuur van de client gebruikt voor het uitvoeren van bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="0788b-125">By default, the culture of the client is used when performing operations.</span></span> <span data-ttu-id="0788b-126">De standaard cultuur kan echter worden overschreven met behulp van de para meter **Culture** .</span><span class="sxs-lookup"><span data-stu-id="0788b-126">However, the default culture can be overridden using the **Culture** parameter.</span></span>

## <span data-ttu-id="0788b-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0788b-127">PARAMETERS</span></span>

### <span data-ttu-id="0788b-128">-Cultuur</span><span class="sxs-lookup"><span data-stu-id="0788b-128">-Culture</span></span>

<span data-ttu-id="0788b-129">Hiermee geeft u de gebruikersinterface cultuur op die voor de CIM-sessie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0788b-129">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="0788b-130">Geef de waarde voor deze para meter op met behulp van een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="0788b-130">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="0788b-131">Een cultuur naam in een `<languagecode2>-<country/regioncode2>` indeling zoals ' en-us '.</span><span class="sxs-lookup"><span data-stu-id="0788b-131">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="0788b-132">Een variabele die een **Culture info** -object bevat.</span><span class="sxs-lookup"><span data-stu-id="0788b-132">A variable that contains a **CultureInfo** object.</span></span>
- <span data-ttu-id="0788b-133">Een opdracht waarmee een **Culture info** -object wordt opgehaald, zoals [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)</span><span class="sxs-lookup"><span data-stu-id="0788b-133">A command that gets a **CultureInfo** object, such as [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-134">-EncodePortInServicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="0788b-134">-EncodePortInServicePrincipalName</span></span>

<span data-ttu-id="0788b-135">Geeft aan dat de Kerberos-verbinding verbinding maakt met een service waarvan de Service Principal Name (SPN) het service poort nummer bevat.</span><span class="sxs-lookup"><span data-stu-id="0788b-135">Indicates that the Kerberos connection is connecting to a service whose service principal name (SPN) includes the service port number.</span></span> <span data-ttu-id="0788b-136">Dit type verbinding is niet gebruikelijk.</span><span class="sxs-lookup"><span data-stu-id="0788b-136">This type of connection is not common.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-137">-Encoding</span><span class="sxs-lookup"><span data-stu-id="0788b-137">-Encoding</span></span>

<span data-ttu-id="0788b-138">Hiermee geeft u de code ring op die wordt gebruikt voor het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="0788b-138">Specifies the encoding used for the WsMan protocol.</span></span> <span data-ttu-id="0788b-139">De acceptabele waarden voor deze para meter zijn: **standaard** , **utf8** of **Utf16**.</span><span class="sxs-lookup"><span data-stu-id="0788b-139">The acceptable values for this parameter are: **Default** , **Utf8** , or **Utf16**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-140">-HttpPrefix</span><span class="sxs-lookup"><span data-stu-id="0788b-140">-HttpPrefix</span></span>

<span data-ttu-id="0788b-141">Hiermee geeft u het deel van de HTTP-URL achter de computer naam en het poort nummer op.</span><span class="sxs-lookup"><span data-stu-id="0788b-141">Specifies the part of the HTTP URL after the computer name and port number.</span></span> <span data-ttu-id="0788b-142">Het wijzigen van dit is niet gebruikelijk.</span><span class="sxs-lookup"><span data-stu-id="0788b-142">Changing this is not common.</span></span> <span data-ttu-id="0788b-143">Standaard is de waarde van deze para meter **/wsman**.</span><span class="sxs-lookup"><span data-stu-id="0788b-143">By default, the value of this parameter is **/wsman**.</span></span>

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-144">-Imitatie</span><span class="sxs-lookup"><span data-stu-id="0788b-144">-Impersonation</span></span>

<span data-ttu-id="0788b-145">Hiermee maakt u een DCOM-sessie naar Windows Management Instrumentation (WMI) met behulp van imitatie.</span><span class="sxs-lookup"><span data-stu-id="0788b-145">Creates a DCOM session to Windows Management Instrumentation (WMI) using impersonation.</span></span>

<span data-ttu-id="0788b-146">Geldige waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="0788b-146">Valid values for this parameter are:</span></span>

- <span data-ttu-id="0788b-147">Standaard: DCOM kan het imitatie niveau kiezen met behulp van het normale algoritme voor beveiligings onderhandeling.</span><span class="sxs-lookup"><span data-stu-id="0788b-147">Default: DCOM can choose the impersonation level using its normal security negotiation algorithm.</span></span>
- <span data-ttu-id="0788b-148">Geen: de client is anoniem voor de server.</span><span class="sxs-lookup"><span data-stu-id="0788b-148">None: The client is anonymous to the server.</span></span> <span data-ttu-id="0788b-149">Het Server proces kan de client imiteren, maar het imitatie token bevat geen informatie en kan niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0788b-149">The server process can impersonate the client, but the impersonation token does not contain any information and cannot be used.</span></span>
- <span data-ttu-id="0788b-150">Identify: Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="0788b-150">Identify: Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="0788b-151">Nabooten: Hiermee staat u toe dat objecten gebruikmaken van de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="0788b-151">Impersonate: Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="0788b-152">Gemachtigde: Hiermee kunnen objecten andere objecten de referenties van de aanroeper gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0788b-152">Delegate: Allows objects to permit other objects to use the credentials of the caller.</span></span>

<span data-ttu-id="0788b-153">Als **imitatie** niet is opgegeven, `New-CimSession` gebruikt de cmdlet de waarde **imiteren**.</span><span class="sxs-lookup"><span data-stu-id="0788b-153">If **Impersonation** is not specified, the `New-CimSession` cmdlet uses the value of **Impersonate**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-154">-MaxEnvelopeSizeKB</span><span class="sxs-lookup"><span data-stu-id="0788b-154">-MaxEnvelopeSizeKB</span></span>

<span data-ttu-id="0788b-155">Hiermee geeft u de maximale grootte van WsMan XML-berichten voor een van beide richtingen.</span><span class="sxs-lookup"><span data-stu-id="0788b-155">Specifies the size limit of WsMan XML messages for either direction.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-156">-Geen versleuteling</span><span class="sxs-lookup"><span data-stu-id="0788b-156">-NoEncryption</span></span>

<span data-ttu-id="0788b-157">Hiermee geeft u op dat gegevens versleuteling is uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="0788b-157">Specifies that data encryption is turned off.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-158">-PacketIntegrity</span><span class="sxs-lookup"><span data-stu-id="0788b-158">-PacketIntegrity</span></span>

<span data-ttu-id="0788b-159">Specificeert dat de DCOM-sessie die is gemaakt met WMI, gebruikmaakt van de _PacketIntegrity_ -functionaliteit van Component Object Model (com).</span><span class="sxs-lookup"><span data-stu-id="0788b-159">Specifies that the DCOM session created to WMI uses the Component Object Model (COM) _PacketIntegrity_ functionality.</span></span> <span data-ttu-id="0788b-160">Standaard hebben alle CIM-sessies die zijn gemaakt met DCOM, de para meter **PacketIntegrity** ingesteld op **True**.</span><span class="sxs-lookup"><span data-stu-id="0788b-160">By default, all CIM sessions created using DCOM have the **PacketIntegrity** parameter set to **True**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-161">-PacketPrivacy</span><span class="sxs-lookup"><span data-stu-id="0788b-161">-PacketPrivacy</span></span>

<span data-ttu-id="0788b-162">Hiermee maakt u een DCOM-sessie met WMI met behulp van de COM- _PacketPrivacy_.</span><span class="sxs-lookup"><span data-stu-id="0788b-162">Creates a DCOM session to WMI using the COM _PacketPrivacy_.</span></span> <span data-ttu-id="0788b-163">Standaard hebben alle CIM-sessies die zijn gemaakt met DCOM, de para meter **PacketPrivacy** ingesteld op **True**.</span><span class="sxs-lookup"><span data-stu-id="0788b-163">By default, all CIM sessions created using DCOM have the **PacketPrivacy** parameter set to **true**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-164">-Protocol</span><span class="sxs-lookup"><span data-stu-id="0788b-164">-Protocol</span></span>

<span data-ttu-id="0788b-165">Hiermee geeft u het protocol op dat moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0788b-165">Specifies the protocol to use.</span></span> <span data-ttu-id="0788b-166">De acceptabele waarden voor deze para meter zijn: **DCOM** , **default** of **Wsman**.</span><span class="sxs-lookup"><span data-stu-id="0788b-166">The acceptable values for this parameter are: **DCOM** , **Default** , or **Wsman**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-167">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="0788b-167">-ProxyAuthentication</span></span>

<span data-ttu-id="0788b-168">Hiermee geeft u de verificatie methode op die moet worden gebruikt voor het omzetten van de proxy.</span><span class="sxs-lookup"><span data-stu-id="0788b-168">Specifies the authentication method to use for proxy resolution.</span></span> <span data-ttu-id="0788b-169">De acceptabele waarden voor deze para meter zijn: **standaard** , **Digest** , **Negotiate** , **Basic** , **Kerberos** , **NtlmDomain** of **CredSsp**.</span><span class="sxs-lookup"><span data-stu-id="0788b-169">The acceptable values for this parameter are: **Default** , **Digest** , **Negotiate** , **Basic** , **Kerberos** , **NtlmDomain** , or **CredSsp**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-170">-ProxyCertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="0788b-170">-ProxyCertificateThumbprint</span></span>

<span data-ttu-id="0788b-171">Hiermee geeft u het (x. 509) digitale open bare-sleutel certificaat van een gebruikers account voor proxy verificatie.</span><span class="sxs-lookup"><span data-stu-id="0788b-171">Specifies the (x.509) digital public key certificate of a user account for proxy authentication.</span></span>
<span data-ttu-id="0788b-172">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="0788b-172">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="0788b-173">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="0788b-173">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="0788b-174">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts en ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="0788b-174">They can only be mapped to local user accounts and they do not work with domain accounts.</span></span>

<span data-ttu-id="0788b-175">Als u een certificaat vingerafdruk wilt ophalen, gebruikt u de `Get-Item` `Get-ChildItem` cmdlets in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="0788b-175">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-176">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="0788b-176">-ProxyCredential</span></span>

<span data-ttu-id="0788b-177">Hiermee geeft u de referenties op die moeten worden gebruikt voor proxy verificatie.</span><span class="sxs-lookup"><span data-stu-id="0788b-177">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="0788b-178">Voer een van de volgende handelingen uit:</span><span class="sxs-lookup"><span data-stu-id="0788b-178">Enter one of the following:</span></span>

- <span data-ttu-id="0788b-179">Een variabele die een PSCredential-object bevat.</span><span class="sxs-lookup"><span data-stu-id="0788b-179">A variable that contains a PSCredential object.</span></span>
- <span data-ttu-id="0788b-180">Een opdracht waarmee een PSCredential-object wordt opgehaald, zoals `Get-Credential`</span><span class="sxs-lookup"><span data-stu-id="0788b-180">A command that gets a PSCredential object, such as `Get-Credential`</span></span>

<span data-ttu-id="0788b-181">Als deze optie niet is ingesteld, kunt u geen referenties opgeven.</span><span class="sxs-lookup"><span data-stu-id="0788b-181">If this option is not set, then you cannot specify any credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-182">-ProxyType</span><span class="sxs-lookup"><span data-stu-id="0788b-182">-ProxyType</span></span>

<span data-ttu-id="0788b-183">Hiermee geeft u het mechanisme voor het omzetten van de naam van de host.</span><span class="sxs-lookup"><span data-stu-id="0788b-183">Specifies the host name resolution mechanism to use.</span></span> <span data-ttu-id="0788b-184">De acceptabele waarden voor deze para meter zijn: **none** , **WinHttp** , **auto** of **InternetExplorer**.</span><span class="sxs-lookup"><span data-stu-id="0788b-184">The acceptable values for this parameter are: **None** , **WinHttp** , **Auto** , or **InternetExplorer**.</span></span>

<span data-ttu-id="0788b-185">De standaard waarde van deze para meter is **InternetExplorer**.</span><span class="sxs-lookup"><span data-stu-id="0788b-185">The default value of this parameter is **InternetExplorer**.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-186">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="0788b-186">-SkipCACheck</span></span>

<span data-ttu-id="0788b-187">Geeft aan dat bij het maken van een verbinding via HTTPS door de client niet wordt gecontroleerd of het server certificaat is ondertekend door een vertrouwde certificerings instantie (CA).</span><span class="sxs-lookup"><span data-stu-id="0788b-187">Indicates that when connecting over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="0788b-188">Gebruik deze para meter alleen wanneer de externe computer wordt vertrouwd met een ander mechanisme, bijvoorbeeld wanneer de externe computer deel uitmaakt van een netwerk dat fysiek veilig en geïsoleerd is, of wanneer de externe computer wordt vermeld als een vertrouwde host in een WinRM-configuratie.</span><span class="sxs-lookup"><span data-stu-id="0788b-188">Use this parameter only when the remote computer is trusted using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated, or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-189">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="0788b-189">-SkipCNCheck</span></span>

<span data-ttu-id="0788b-190">Geeft aan dat de algemene naam (CN) van het certificaat van de server niet moet overeenkomen met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="0788b-190">Indicates that the certificate common name (CN) of the server does not need to match the hostname of the server.</span></span> <span data-ttu-id="0788b-191">Gebruik deze para meter alleen voor externe bewerkingen met vertrouwde computers die gebruikmaken van het HTTPS-protocol.</span><span class="sxs-lookup"><span data-stu-id="0788b-191">Use this parameter for remote operations only with trusted computers that use the HTTPS protocol.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-192">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="0788b-192">-SkipRevocationCheck</span></span>

<span data-ttu-id="0788b-193">Geeft aan dat de intrekkings controle voor server certificaten wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0788b-193">Indicates that the revocation check for server certificates is skipped.</span></span> <span data-ttu-id="0788b-194">Gebruik deze para meter alleen voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="0788b-194">Use this parameter only for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-195">-UICulture</span><span class="sxs-lookup"><span data-stu-id="0788b-195">-UICulture</span></span>

<span data-ttu-id="0788b-196">Hiermee geeft u de gebruikersinterface cultuur op die voor de CIM-sessie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0788b-196">Specifies the user interface culture to use for the CIM session.</span></span> <span data-ttu-id="0788b-197">Geef de waarde voor deze para meter op met behulp van een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="0788b-197">Specify the value for this parameter using one of the following formats:</span></span>

- <span data-ttu-id="0788b-198">Een cultuur naam in een `<languagecode2>-<country/regioncode2>` indeling zoals ' en-us '.</span><span class="sxs-lookup"><span data-stu-id="0788b-198">A culture name in `<languagecode2>-<country/regioncode2>` format such as "EN-US".</span></span>
- <span data-ttu-id="0788b-199">Een variabele die een Culture info-object bevat.</span><span class="sxs-lookup"><span data-stu-id="0788b-199">A variable that contains a CultureInfo object.</span></span>
- <span data-ttu-id="0788b-200">Een opdracht waarmee een Culture info-object wordt opgehaald, zoals `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="0788b-200">A command that gets a CultureInfo object, such as `Get-Culture`.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-201">-UseSsl</span><span class="sxs-lookup"><span data-stu-id="0788b-201">-UseSsl</span></span>

<span data-ttu-id="0788b-202">Hiermee wordt aangegeven dat SSL moet worden gebruikt om een verbinding met de externe computer tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="0788b-202">Indicates that SSL should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="0788b-203">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0788b-203">By default, SSL is not used.</span></span> <span data-ttu-id="0788b-204">Met WsMan wordt alle inhoud die via het netwerk wordt verzonden, versleuteld, zelfs wanneer HTTP wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0788b-204">WsMan encrypts all content that is transmitted over the network, even when using HTTP.</span></span>

<span data-ttu-id="0788b-205">Met deze para meter kunt u de aanvullende beveiliging van HTTPS in plaats van HTTP opgeven.</span><span class="sxs-lookup"><span data-stu-id="0788b-205">This parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="0788b-206">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0788b-206">If SSL is not available on the port used for the connection and you specify this parameter, then the command fails.</span></span>

<span data-ttu-id="0788b-207">U wordt aangeraden deze para meter alleen te gebruiken als de para meter **PacketPrivacy** niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="0788b-207">It is recommended that you use this parameter only when the **PacketPrivacy** parameter is not specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0788b-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0788b-208">CommonParameters</span></span>

<span data-ttu-id="0788b-209">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0788b-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0788b-210">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0788b-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0788b-211">INVOER</span><span class="sxs-lookup"><span data-stu-id="0788b-211">INPUTS</span></span>

### <span data-ttu-id="0788b-212">Geen</span><span class="sxs-lookup"><span data-stu-id="0788b-212">None</span></span>

<span data-ttu-id="0788b-213">Deze cmdlet accepteert geen invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="0788b-213">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="0788b-214">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0788b-214">OUTPUTS</span></span>

### <span data-ttu-id="0788b-215">CIMSessionOption</span><span class="sxs-lookup"><span data-stu-id="0788b-215">CIMSessionOption</span></span>

<span data-ttu-id="0788b-216">Met deze cmdlet wordt een object geretourneerd dat informatie over CIM-sessie opties bevat.</span><span class="sxs-lookup"><span data-stu-id="0788b-216">This cmdlet returns an object that contains CIM session options information.</span></span>

## <span data-ttu-id="0788b-217">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0788b-217">NOTES</span></span>

## <span data-ttu-id="0788b-218">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0788b-218">RELATED LINKS</span></span>

[<span data-ttu-id="0788b-219">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="0788b-219">Get-ChildItem</span></span>](../microsoft.powershell.management/get-childitem.md)

[<span data-ttu-id="0788b-220">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="0788b-220">Get-Credential</span></span>](../microsoft.powershell.security/get-credential.md)

[<span data-ttu-id="0788b-221">Get-cultuur</span><span class="sxs-lookup"><span data-stu-id="0788b-221">Get-Culture</span></span>](../microsoft.powershell.utility/get-culture.md)

[<span data-ttu-id="0788b-222">Get-item</span><span class="sxs-lookup"><span data-stu-id="0788b-222">Get-Item</span></span>](../microsoft.powershell.management/get-item.md)

[<span data-ttu-id="0788b-223">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="0788b-223">New-CimSession</span></span>](New-CimSession.md)

