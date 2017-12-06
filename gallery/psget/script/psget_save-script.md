---
ms.date: 2017-10-17
contributor: keithb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: "Kaydet-komut dosyası"
ms.openlocfilehash: b54e8ba074b7cadd52df781c9021332ccc90f9fd
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2017
---
# <a name="save-script"></a><span data-ttu-id="6ccbc-103">Kaydet-komut dosyası</span><span class="sxs-lookup"><span data-stu-id="6ccbc-103">Save-Script</span></span>

<span data-ttu-id="6ccbc-104">Kaydet-komut dosyası cmdlet belirtilen bir konuma kaydederek komut dosyasını gözden geçirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ccbc-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="6ccbc-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ccbc-105">Description</span></span>

<span data-ttu-id="6ccbc-106">Kaydet-komut dosyası cmdlet'i belirtilen komut dosyası kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6ccbc-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="6ccbc-107">Cmdlet sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ccbc-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="6ccbc-108">Cmdlet çevrimiçi Yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="6ccbc-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="6ccbc-109">Kaydet-komut dosyası</span><span class="sxs-lookup"><span data-stu-id="6ccbc-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="6ccbc-110">Örnek komutlar</span><span class="sxs-lookup"><span data-stu-id="6ccbc-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="6ccbc-111">Örnek 1: bir depodan bir komut dosyasını kaydetme</span><span class="sxs-lookup"><span data-stu-id="6ccbc-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="6ccbc-112">Bu komut komut yerel klasörde C:\ScriptSharingDemo Fabrikam-ClientScript GalleryINT depodan en son sürümünü kaydeder</span><span class="sxs-lookup"><span data-stu-id="6ccbc-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="6ccbc-113">Örnek 2: yöneltme bulma komut dosyası cmdlet'inden tarafından bir komut dosyasının bir sürümünü kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6ccbc-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="6ccbc-114">İlk komut Fabrikam ClientScript GalleryINT depodan 1.5 sürümünü bulur ve C:\ScriptSharingDemo klasörüne kaydeder</span><span class="sxs-lookup"><span data-stu-id="6ccbc-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="6ccbc-115">İkinci komut kaydedilmiş komut dosyası meta verileri doğrular.</span><span class="sxs-lookup"><span data-stu-id="6ccbc-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="6ccbc-116">Örnek 3: bir depodan bir komut dosyası bir ön sürümünü Kaydet</span><span class="sxs-lookup"><span data-stu-id="6ccbc-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="6ccbc-117">Bu komut komut yerel klasörde C:\ScriptSharingDemo Fabrikam-ClientScript GalleryINT depodan en son sürümünü kaydeder</span><span class="sxs-lookup"><span data-stu-id="6ccbc-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```

