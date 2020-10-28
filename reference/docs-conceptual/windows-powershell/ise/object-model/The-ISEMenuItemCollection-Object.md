---
ms.date: 12/31/2019
title: Het ISEMenuItemCollection-object
description: Een ISEMenuItemCollection-object is een verzameling ISEMenuItem-objecten.
ms.openlocfilehash: cd86768d13b1326a8f35c44f0391ab60669cee4f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655995"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="0e9f2-103">Het ISEMenuItemCollection-object</span><span class="sxs-lookup"><span data-stu-id="0e9f2-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="0e9f2-104">Een **ISEMenuItemCollection** -object is een verzameling **ISEMenuItem** -objecten.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="0e9f2-105">Het is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEMenuItemCollection** .</span><span class="sxs-lookup"><span data-stu-id="0e9f2-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection** class.</span></span> <span data-ttu-id="0e9f2-106">Een voor beeld is het `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` object dat wordt gebruikt voor het aanpassen van het **invoeg** menu in Windows Power shell &reg; Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="0e9f2-106">An example is the `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` object that is used to customize the **Add-On** menu in Windows PowerShell&reg; Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="0e9f2-107">Methode</span><span class="sxs-lookup"><span data-stu-id="0e9f2-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="0e9f2-108">\(Teken reeks DisplayName, System. Management. Automation. script block-actie, System. Windows. input. toets-beweging toevoegen\)</span><span class="sxs-lookup"><span data-stu-id="0e9f2-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="0e9f2-109">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0e9f2-110">Hiermee wordt een menu opdracht toegevoegd aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="0e9f2-111">**DisplayName** De weergave naam van het menu dat moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="0e9f2-112">**Actie** Het object **System. Management. Automation. script Block** dat de actie specificeert die is gekoppeld aan deze menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="0e9f2-113">**Snelkoppeling** De sneltoets voor de actie.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="0e9f2-114">**Retourneert** Het **ISEMenuItem** -object dat zojuist is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-114">**Returns** The **ISEMenuItem** object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="0e9f2-115">Maak\(\)</span><span class="sxs-lookup"><span data-stu-id="0e9f2-115">Clear\(\)</span></span>

<span data-ttu-id="0e9f2-116">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="0e9f2-117">Hiermee verwijdert u alle submenu's uit de menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="0e9f2-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="0e9f2-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0e9f2-118">See Also</span></span>

- [<span data-ttu-id="0e9f2-119">Het ISEMenuItem-object</span><span class="sxs-lookup"><span data-stu-id="0e9f2-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="0e9f2-120">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0e9f2-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="0e9f2-121">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="0e9f2-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
