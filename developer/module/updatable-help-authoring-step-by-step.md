---
title: 'Güncelleştirilebilir Yardım Yazma: Adım adım | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849836"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="f9dc1-102">Güncelleştirilebilir Yardım Yazma: Adım Adım</span><span class="sxs-lookup"><span data-stu-id="f9dc1-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="f9dc1-103">Bu belgeler güncelleştirilebilir Yardımı yazma işleminde adımları listelenir.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="f9dc1-104">Güncelleştirilebilir Yardımı yazma: Adım Adım</span><span class="sxs-lookup"><span data-stu-id="f9dc1-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="f9dc1-105">Güncelleştirilebilir Yardımı, son kullanıcılar için tasarlanmıştır ancak modül yazarları Ayrıca önemli avantajlar sağlar ve içerik ekleme olanağı dahil olmak üzere Yardım yazıcıları, hataları düzeltin, birden çok UI kültürde sunun ve uzun sonra kullanıcı yorumları ve istekleri, yanıt Modül sevk edildi.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="f9dc1-106">Bu konu nasıl paketini açıklar ve karşıya yükleme Yardım dosyaları ve böylece kullanıcılar indirebilir ve bunları kullanarak yükleyin [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) ve [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet'leri.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="f9dc1-107">Aşağıdaki adımlar, güncelleştirilebilir Yardımı destekleme sürecine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="f9dc1-108">Adım 1: Yardım dosyalarınız için bir Internet sitesini Bul</span><span class="sxs-lookup"><span data-stu-id="f9dc1-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="f9dc1-109">Güncelleştirilebilir Yardımı oluşturmanın ilk adımı, modülün Yardım dosyaları için bir Internet konum bulmaktır.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="f9dc1-110">Aslında, iki farklı konuma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="f9dc1-111">Modülün Yardım bilgi dosyası (HelpInfo XML - aşağıda açıklanmıştır), bir Internet konumu ve başka bir Internet konumda Yardım içeriği CAB dosyalarını tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="f9dc1-112">Tüm Yardım içerik CAB dosyaları bir modül için aynı konumda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="f9dc1-113">Farklı modüller için Yardım içeriği CAB dosyalarını aynı konuma yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="f9dc1-114">Adım 2: Modül bildiriminizi HelpInfoURI anahtar ekleme</span><span class="sxs-lookup"><span data-stu-id="f9dc1-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="f9dc1-115">Ekleme bir **HelpInfoURI** , modül bildirimine anahtar.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="f9dc1-116">Modülünüzün HelpInfo XML bilgi dosyasının konumu Tekdüzen Kaynak Tanımlayıcısı (URI) anahtar değeridir.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="f9dc1-117">Güvenlik için adres "http" veya "https" ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="f9dc1-118">URI bir Internet konumu belirtmeniz gerekir, ancak HelpInfo XML dosya adı içermemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="f9dc1-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f9dc1-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="f9dc1-120">Adım 3: HelpInfo XML dosyası oluşturun</span><span class="sxs-lookup"><span data-stu-id="f9dc1-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="f9dc1-121">Yardım dosyaları ve sürüm numaralarını, desteklenen her UI kültürü modülünde en yeni Yardım dosyaları, Internet konumunu URI HelpInfo XML bilgi dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="f9dc1-122">Her bir Windows PowerShell modülü bir HelpInfo XML dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="f9dc1-123">Yardım dosyaları güncelleştirdikten sonra düzenleme veya HelpInfo XML dosyasını değiştirin; başka bir eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="f9dc1-124">Daha fazla bilgi için [HelpInfo XML dosyasının nasıl oluşturulacağı](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="f9dc1-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="f9dc1-125">Adım 4: Yardım dosyaları oturum</span><span class="sxs-lookup"><span data-stu-id="f9dc1-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="f9dc1-126">Dijital imzalar gerekli değildir, ancak dosyaları paylaştığı her iyi öneri oldukları.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="f9dc1-127">Adım 5: CAB dosyaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9dc1-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="f9dc1-128">Oluşturulacak MakeCab.exe gibi dolap (.cab) dosya oluşturur aracını bir. Modülünüzün Yardım dosyaları içeren CAB dosyası.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="f9dc1-129">Yardım dosyaları için ayrı bir CAB dosyası içinde her desteklenen UI kültürü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="f9dc1-130">Daha fazla bilgi için [hazırlama güncelleştirilebilir Yardımı CAB dosyaları nasıl](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="f9dc1-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="f9dc1-131">Adım 6: Dosyalarınızı karşıya yükleyin</span><span class="sxs-lookup"><span data-stu-id="f9dc1-131">Step 6: Upload your files</span></span>

<span data-ttu-id="f9dc1-132">Yeni veya güncelleştirilmiş Yardım dosyaları yayımlamak için CAB dosyaları tarafından belirtilen Internet konuma karşıya yükleme **HelpContentUri** HelpInfo XML dosyasında öğe.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="f9dc1-133">Ardından, değeri tarafından belirtilen Internet konuma HelpInfo XML dosyasını karşıya **HelpInfoUri** modül bildirimindeki anahtar.</span><span class="sxs-lookup"><span data-stu-id="f9dc1-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
