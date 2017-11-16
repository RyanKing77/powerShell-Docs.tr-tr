---
ms.date: 2017-06-05
keywords: PowerShell cmdlet'i
title: ISESnippetCollection nesnesi
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="6c181-103">ISESnippetCollection nesnesi</span><span class="sxs-lookup"><span data-stu-id="6c181-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="6c181-104">**ISESnippetCollection** nesnesidir koleksiyonu **ISESnippet** nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6c181-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="6c181-105">İle ilişkili dosyaları koleksiyonu bir **PowerShellTab** nesne bu sınıfın bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="6c181-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="6c181-106">Örnek **$psISE.CurrentPowerShellTab.Files** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6c181-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="6c181-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6c181-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="6c181-108">Yük\( FilePathName\)</span><span class="sxs-lookup"><span data-stu-id="6c181-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="6c181-109">Desteklenen Windows PowerShell ISE 3.0 ve üstü ve önceki sürümlerindeki mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="6c181-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="6c181-110">Yükleri bir. kullanıcı tanımlı parçacıkları içeren snippets.ps1xml dosyası.</span><span class="sxs-lookup"><span data-stu-id="6c181-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="6c181-111">Parçacıkları oluşturmak için en kolay yolu, otomatik olarak bunları profili klasörünüzde depolar ve böylece Windows PowerShell ISE her başlattığınızda yüklenen yeni IseSnippet cmdlet'ini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="6c181-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="6c181-112">**FilePathName** - dize yolun ve dosya adı için bir. parçacığı tanımları içeren snippets.ps1xml dosyası.</span><span class="sxs-lookup"><span data-stu-id="6c181-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="6c181-113">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="6c181-113">See Also</span></span>
- [<span data-ttu-id="6c181-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="6c181-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="6c181-115">Windows PowerShell ISE nesne modeli komut dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="6c181-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="6c181-116">Windows PowerShell ISE nesne modeli başvurusu</span><span class="sxs-lookup"><span data-stu-id="6c181-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="6c181-117">ISE nesne modeli hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="6c181-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
