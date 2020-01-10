---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISEMenuItemCollection-object
ms.openlocfilehash: 39e8547c9b19ba323d4b224a46eda416542b2807
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736169"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="ca132-103">Het ISEMenuItemCollection-object</span><span class="sxs-lookup"><span data-stu-id="ca132-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="ca132-104">Een **ISEMenuItemCollection** -object is een verzameling **ISEMenuItem** -objecten.</span><span class="sxs-lookup"><span data-stu-id="ca132-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="ca132-105">Het is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEMenuItemCollection** .</span><span class="sxs-lookup"><span data-stu-id="ca132-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection** class.</span></span> <span data-ttu-id="ca132-106">Een voor beeld is het `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus`-object dat wordt gebruikt voor het aanpassen van het **invoeg** menu in Windows power shell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="ca132-106">An example is the `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="ca132-107">Methode</span><span class="sxs-lookup"><span data-stu-id="ca132-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="ca132-108">\(teken reeks weergave naam, System. Management. Automation. script block-actie, System. Windows. input. toets-beweging toevoegen \)</span><span class="sxs-lookup"><span data-stu-id="ca132-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="ca132-109">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ca132-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ca132-110">Hiermee wordt een menu opdracht toegevoegd aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="ca132-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="ca132-111">**DisplayName** De weergave naam van het menu dat moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="ca132-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="ca132-112">**Actie** Het object **System. Management. Automation. script Block** dat de actie specificeert die is gekoppeld aan deze menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="ca132-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="ca132-113">**Snelkoppeling** De sneltoets voor de actie.</span><span class="sxs-lookup"><span data-stu-id="ca132-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="ca132-114">**Retourneert** Het **ISEMenuItem** -object dat zojuist is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="ca132-114">**Returns** The **ISEMenuItem** object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="ca132-115">\(\) wissen</span><span class="sxs-lookup"><span data-stu-id="ca132-115">Clear\(\)</span></span>

<span data-ttu-id="ca132-116">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ca132-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ca132-117">Hiermee verwijdert u alle submenu's uit de menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="ca132-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="ca132-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ca132-118">See Also</span></span>

- [<span data-ttu-id="ca132-119">Het ISEMenuItem-object</span><span class="sxs-lookup"><span data-stu-id="ca132-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="ca132-120">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="ca132-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ca132-121">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="ca132-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
