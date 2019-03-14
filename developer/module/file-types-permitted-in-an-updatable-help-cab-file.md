---
title: Güncelleştirilebilir bir izin verilen dosya türleri Yardım CAB dosyası | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794255"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="79eed-102">Güncelleştirilebilir CAB Dosyasında İzin Verilen Dosya Türleri</span><span class="sxs-lookup"><span data-stu-id="79eed-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="79eed-103">Bu konular, listeler ve içerik için güncelleştirilebilir Yardımı CAB dosyaları gereksinimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="79eed-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="79eed-104">Güncelleştirilebilir Yardımı CAB dosyası gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="79eed-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="79eed-105">Sıkıştırılmamış CAB dosya içeriği varsayılan olarak 1 GB ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="79eed-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="79eed-106">Bu sınırı atlamak için kullanılacak kullanıcınız **zorla** parametresinin [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="79eed-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="79eed-107">Internet'ten indirilen Yardım dosyaları güvenliğini sağlamak için güncelleştirilebilir Yardımı CAB dosyası yalnızca aşağıda listelenen dosya türlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="79eed-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="79eed-108">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet Yardım konusu şemaları karşı tüm dosyaları doğrular.</span><span class="sxs-lookup"><span data-stu-id="79eed-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="79eed-109">Varsa `Update-Help` cmdlet'i geçersiz veya izin verilen bir tür değil bir dosyayı karşılaştığında, geçersiz dosya yüklemez ve kullanıcının bilgisayarında CAB dosyaları yükleme durdurur.</span><span class="sxs-lookup"><span data-stu-id="79eed-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="79eed-110">Cmdlet'leri için XML tabanlı Yardım konuları.</span><span class="sxs-lookup"><span data-stu-id="79eed-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="79eed-111">Betik ve işlevlerde için XML tabanlı Yardım konuları.</span><span class="sxs-lookup"><span data-stu-id="79eed-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="79eed-112">Windows PowerShell sağlayıcıları için XML tabanlı Yardım konuları.</span><span class="sxs-lookup"><span data-stu-id="79eed-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="79eed-113">Metin tabanlı Yardım konuları, gibi ilgili konular.</span><span class="sxs-lookup"><span data-stu-id="79eed-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="79eed-114">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) CAB ayıklar CAB içeriği doğrular.</span><span class="sxs-lookup"><span data-stu-id="79eed-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="79eed-115">Varsa `Update-Help` bulur uyumlu olmayan dosya türlerini bir güncelleştirilebilir Yardımı CAB dosyası, bir sonlandırma hatası oluşturur ve işlemi durdurur.</span><span class="sxs-lookup"><span data-stu-id="79eed-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="79eed-116">Yardım dosyaları CAB, bile bu uyumlu bir dosya türlerinin yüklemez.</span><span class="sxs-lookup"><span data-stu-id="79eed-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>