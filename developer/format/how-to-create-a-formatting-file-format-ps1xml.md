---
title: Biçimlendirme dosyasının nasıl oluşturulacağı (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065515"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="14716-102">Biçimlendirme Dosyası Oluşturma (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="14716-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="14716-103">Bu konuda bir biçimlendirme dosyası oluşturmayı açıklar (. format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="14716-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="14716-104">Bir Windows PowerShell tarafından sağlanan dosyalarının bir kopyasını yaparak, biçimlendirme dosyası da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14716-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="14716-105">Varolan bir dosyanın bir kopyasını yaparsanız, var olan bir dijital imza silin ve yeni dosyaya kendi imza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="14716-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="14716-106">Oluşturmak için bir. format.ps1xml dosya.</span><span class="sxs-lookup"><span data-stu-id="14716-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="14716-107">Düzenleyici Not Defteri gibi bir metin kullanarak bir metin dosyası (.txt) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="14716-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="14716-108">Aşağıdaki satırları biçimlendirme dosyaya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="14716-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="14716-109">\<Yapılandırma >\</Configuration > etiketlerini tanımlayın kök `Configuration` düğümü.</span><span class="sxs-lookup"><span data-stu-id="14716-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="14716-110">Tüm ek XML etiketleri içinde bu düğümü içine alınabilir.</span><span class="sxs-lookup"><span data-stu-id="14716-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="14716-111"><ViewDefinitions> </ViewDefinitions> Etiketleri tanımlamak `ViewDefinitions` düğümü.</span><span class="sxs-lookup"><span data-stu-id="14716-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="14716-112">Tüm görünümler bu düğümün içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="14716-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="14716-113">Dosyayı Windows PowerShell yükleme klasörüne, modül klasörünüze veya modül klasörünün bir alt klasöre kaydedin.</span><span class="sxs-lookup"><span data-stu-id="14716-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="14716-114">Dosyayı kaydettiğinizde aşağıdaki ad biçimi kullanın: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="14716-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="14716-115">Biçimlendirme dosyaları kullanmalıdır `.format.ps1xml` uzantısı.</span><span class="sxs-lookup"><span data-stu-id="14716-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="14716-116">Görünümleri biçimlendirme dosyasına eklemek artık hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="14716-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="14716-117">Bir biçimlendirme dosyasında tanımlanan görünümleri sayısı sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="14716-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="14716-118">Her nesne, aynı nesne için birden çok görünüm veya birden çok nesne tarafından kullanılan tek bir görünüm için tek bir görünümde ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14716-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="14716-119">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="14716-119">See Also</span></span>

[<span data-ttu-id="14716-120">Biçimlendirme bir Windows PowerShell yazma ve dosya türleri</span><span class="sxs-lookup"><span data-stu-id="14716-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
