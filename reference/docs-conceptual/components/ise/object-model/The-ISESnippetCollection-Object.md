---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: ISESnippetCollection Nesnesi
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086689"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="24808-103">ISESnippetCollection Nesnesi</span><span class="sxs-lookup"><span data-stu-id="24808-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="24808-104">**Isesnippetcollection** nesnedir koleksiyonu **ISESnippet** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="24808-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="24808-105">İle ilişkili dosyaları koleksiyonu bir **PowerShellTab** nesne bu sınıfın bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="24808-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="24808-106">Bir örnek **$psISE.CurrentPowerShellTab.Files** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="24808-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="24808-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="24808-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="24808-108">Yük\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="24808-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="24808-109">Desteklenen Windows PowerShell ISE 3.0 ve sonraki ve önceki sürümlerde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="24808-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="24808-110">Yükleri bir. kullanıcı tarafından tanımlanan kod parçacıkları içeren snippets.ps1xml dosyası.</span><span class="sxs-lookup"><span data-stu-id="24808-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="24808-111">Kod parçacıkları oluşturmak için en kolay yolu, bunları otomatik olarak profil klasörünüzde depolar ve böylece, Windows PowerShell ISE her başlattığınızda yüklenen yeni IseSnippet cmdlet'ini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="24808-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="24808-112">**FilePathName** - dize yolun ve dosya adı için bir. kod parçacığı tanımları içeren snippets.ps1xml dosyası.</span><span class="sxs-lookup"><span data-stu-id="24808-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="24808-113">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="24808-113">See Also</span></span>

- [<span data-ttu-id="24808-114">Isesnippet nesnesi</span><span class="sxs-lookup"><span data-stu-id="24808-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="24808-115">Windows PowerShell ISE betik oluşturma nesne modelinin amacı</span><span class="sxs-lookup"><span data-stu-id="24808-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="24808-116">ISE Nesne Modeli Hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="24808-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)