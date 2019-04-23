---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3cfc2f042234f682599bb67eac592ea3f77b31b6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984111"
---
# <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="7aa90-102">Geliştirilmiş öğe cmdlet'leri kullanarak simgesel bağlantılar ile etkileşim kurma</span><span class="sxs-lookup"><span data-stu-id="7aa90-102">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="7aa90-103">Sembolik bağlantıları desteklemek için  **\*-öğesi** ve birkaç ilgili cmdlet'lerle genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7aa90-103">To support symbolic links, **\*-Item** and a few related cmdlets have been extended.</span></span> <span data-ttu-id="7aa90-104">Sembolik bağlantılar ile basit, tek bir satır oluşturabileceğiniz artık **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="7aa90-104">Now you can create symbolic links in a single, simple line with **New-Item**.</span></span> <span data-ttu-id="7aa90-105">Olduğunu fark edeceksiniz öğesi ile ilgili cmdlet'ler (**Kaldır öğesini, Get-Childıtem**) için önce çok benzer şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="7aa90-105">You’ll notice that the Item-related cmdlets (**Remove-Item, Get-ChildItem**) behave very similarly to before.</span></span>

<span data-ttu-id="7aa90-106">Aşağıdaki yeni özelliklerin bazı kullanım gösterir:</span><span class="sxs-lookup"><span data-stu-id="7aa90-106">The following shows some use cases of the new capabilities:</span></span>

## <a name="new-item"></a><span data-ttu-id="7aa90-107">Yeni öğe</span><span class="sxs-lookup"><span data-stu-id="7aa90-107">New-Item</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="7aa90-108">Sembolik bağlantıyı dosyaları</span><span class="sxs-lookup"><span data-stu-id="7aa90-108">Symbolic link files</span></span>

```powershell
# Create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1
cd C:\Temp
New-Item -ItemType SymbolicLink -Name MySymLinkFile.txt -Target $pshome\profile.ps1

# Target is an alias to the Value parameter
# All 3 commands below are equivalent to above
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="7aa90-109">Sembolik bağlantıyı dizinleri</span><span class="sxs-lookup"><span data-stu-id="7aa90-109">Symbolic link directories</span></span>

```powershell
# Create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder
# ItemType is the same for files and directories - autodetect based on specified target
cd C:\Temp
New-Item -ItemType SymbolicLink -Name MySymLinkDir -Target $pshome

# Target is an alias to the Value parameter
# Similar to above, any combination of Path and Name also works
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="7aa90-110">Sabit bağlantılar</span><span class="sxs-lookup"><span data-stu-id="7aa90-110">Hard links</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
# Same combinations of Path and Name allowed as described above
```

### <a name="directory-junctions"></a><span data-ttu-id="7aa90-111">Dizin merkezleriyle</span><span class="sxs-lookup"><span data-stu-id="7aa90-111">Directory junctions</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
# Same combinations of Path and Name allowed as described above
```

## <a name="get-childitem"></a><span data-ttu-id="7aa90-112">Get-Childıtem</span><span class="sxs-lookup"><span data-stu-id="7aa90-112">Get-ChildItem</span></span>

```powershell
# Append link type column to Mode property and display with Get-ChildItem
# Use 'l' for all link types
# Increase the width of the Length column by 4 (from 10 to 14)
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode LastWriteTime Length Name
---- ------------- ------ ----
-a---- 6/13/2014 3:00 PM 16 File.txt
-a---- 6/13/2014 3:00 PM 98956046499840 My90TB.vhd
d----- 6/13/2014 3:00 PM Directory
-a---l 6/13/2014 3:21 PM 0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM MySymLinkDir
-a---l 6/13/2014 3:23 PM 23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM MyJunctionDir

# New Target property works with any link type
# Not displayed in the default table view, but displayed in the default list view

# New LinkType property with values: SymbolicLink
Get-ChildItem C:\Temp\MySymLinkFile.txt | Format-List

Directory: C:\Temp

Name : MySymLinkFile.txt
Length : 0
Mode : -a---l
LinkType : SymbolicLink
Target : C:\Windows\System32\WindowsPowerShell\v1.0\profile.ps1
CreationTime : 6/16/2014 3:21:01 PM
LastWriteTime : 6/16/2014 3:21:01 PM
LastAccessTime : 6/16/2014 3:21:01 PM
VersionInfo : File: C:\Temp\MySymLinkFile.txt
InternalName:
OriginalFilename:
FileVersion:
FileDescription:
Product:
ProductVersion:
Debug: False
Patched: False
PreRelease: False
PrivateBuild: False
SpecialBuild: False
Language:
```

## <a name="remove-item"></a><span data-ttu-id="7aa90-113">Remove öğesi</span><span class="sxs-lookup"><span data-stu-id="7aa90-113">Remove-Item</span></span>

```powershell
# Works like any other item type
# Removes MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkFile.txt

# Returns an error as this is a reparse point.
Remove-Item C:\Temp\MySymLinkDir

# Removes the files in the target directory and MySymLinkDir
Remove-Item C:\Temp\MySymLinkDir -Force
```
