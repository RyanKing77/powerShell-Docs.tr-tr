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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851691"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Biçimlendirme Dosyası Oluşturma (.format.ps1xml)

Bu konuda bir biçimlendirme dosyası oluşturmayı açıklar (. format.ps1xml).

> [!NOTE]
> Bir Windows PowerShell tarafından sağlanan dosyalarının bir kopyasını yaparak, biçimlendirme dosyası da oluşturabilirsiniz. Varolan bir dosyanın bir kopyasını yaparsanız, var olan bir dijital imza silin ve yeni dosyaya kendi imza ekleyin.

### <a name="to-create-a-formatps1xml-file"></a>Oluşturmak için bir. format.ps1xml dosya.

1. Düzenleyici Not Defteri gibi bir metin kullanarak bir metin dosyası (.txt) oluşturun.

2. Aşağıdaki satırları biçimlendirme dosyaya kopyalayın.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - \<Yapılandırma >\</Configuration > etiketlerini tanımlayın kök `Configuration` düğümü. Tüm ek XML etiketleri içinde bu düğümü içine alınabilir.

   - <ViewDefinitions> </ViewDefinitions> Etiketleri tanımlamak `ViewDefinitions` düğümü. Tüm görünümler bu düğümün içinde tanımlanır.

3. Dosyayı Windows PowerShell yükleme klasörüne, modül klasörünüze veya modül klasörünün bir alt klasöre kaydedin. Dosyayı kaydettiğinizde aşağıdaki ad biçimi kullanın: `MyFile.format.ps1xml`. Biçimlendirme dosyaları kullanmalıdır `.format.ps1xml` uzantısı.

   Görünümleri biçimlendirme dosyasına eklemek artık hazırsınız. Bir biçimlendirme dosyasında tanımlanan görünümleri sayısı sınırı yoktur. Her nesne, aynı nesne için birden çok görünüm veya birden çok nesne tarafından kullanılan tek bir görünüm için tek bir görünümde ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz:

[Biçimlendirme bir Windows PowerShell yazma ve dosya türleri](./writing-a-powershell-formatting-file.md)
