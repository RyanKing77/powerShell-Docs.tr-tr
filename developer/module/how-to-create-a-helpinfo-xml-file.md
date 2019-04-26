---
title: HelpInfo XML dosyasının nasıl oluşturulacağı | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082422"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="69711-102">HelpInfo XML Dosyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="69711-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="69711-103">Bu bölümdeki konular, oluşturma ve bir "HelpInfo XML dosyası olarak" Windows PowerShell güncelleştirilebilir Yardımı özelliği için yaygın olarak bilinen bir Yardım bilgileri dosyası doldurmak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69711-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="69711-104">HelpInfo XML dosyasını genel bakış</span><span class="sxs-lookup"><span data-stu-id="69711-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="69711-105">Modül için güncelleştirilebilir Yardımı hakkında bilgi birincil kaynağı HelpInfo XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="69711-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="69711-106">Bu modüller, desteklenen UI kültürü ve kullanıcının en yeni Yardım dosyaları olup olmadığını belirlemek için güncelleştirilebilir Yardımı'nı kullanan sürüm numaraları için Yardım dosyalarının konumunu içerir.</span><span class="sxs-lookup"><span data-stu-id="69711-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="69711-107">Birden çok UI kültürü için birden çok Yardım dosyası modül içerse bile her modülü yalnızca bir HelpInfo XML dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="69711-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="69711-108">Modül yazarı HelpInfo XML dosyası oluşturur ve tarafından belirtilen Internet konumda yerleştirir **HelpInfoUri** modül bildirimindeki anahtar.</span><span class="sxs-lookup"><span data-stu-id="69711-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="69711-109">Modül Yardım dosyaları güncelleştirilmiş ve karşıya yüklenen modül yazarı HelpInfo XML dosyasını güncelleştirir ve orijinal HelpInfo XML dosyasını yeni sürüm ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="69711-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="69711-110">HelpInfo XML dosyasını dikkatli bir şekilde korunur önemlidir.</span><span class="sxs-lookup"><span data-stu-id="69711-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="69711-111">Güncelleştirilebilir Yardımı yeni dosyaları karşıya yükleme, ancak sürüm numaralarının artırılıp unutursanız, yeni dosyalar kullanıcıların bilgisayarlarına yüklemez.</span><span class="sxs-lookup"><span data-stu-id="69711-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="69711-112">Güncelleştirilebilir Yardımı için yeni bir kullanıcı Arabirimi kültürünü Yardım dosyalarını eklemek ancak HelpInfo XML dosyasını güncelleştirin veya yoksa onu doğru konuma yerleştirmek, yeni dosyalar yüklemez.</span><span class="sxs-lookup"><span data-stu-id="69711-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="69711-113">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="69711-113">In this section</span></span>

<span data-ttu-id="69711-114">Bu bölüm aşağıdaki konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="69711-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="69711-115">HelpInfo XML Şeması</span><span class="sxs-lookup"><span data-stu-id="69711-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="69711-116">HelpInfo XML örnek dosya</span><span class="sxs-lookup"><span data-stu-id="69711-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="69711-117">Nasıl HelpInfo XML dosya adı</span><span class="sxs-lookup"><span data-stu-id="69711-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="69711-118">HelpInfo XML sürüm numaraları ayarlama</span><span class="sxs-lookup"><span data-stu-id="69711-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="69711-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="69711-119">See Also</span></span>

[<span data-ttu-id="69711-120">Güncelleştirilebilir Yardımı destekleme</span><span class="sxs-lookup"><span data-stu-id="69711-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)