---
title: Bir Cmdlet açıklama ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083527"
---
# <a name="how-to-add-a-cmdlet-description"></a>Cmdlet Açıklaması Ekleme

Bu bölümde, cmdlet Yardım Açıklama bölümünde görüntülenen içerik eklemeyi açıklar. Yardım dosyasında, bu içerik, her cmdlet için komut düğümüne eklenir.

> [!NOTE]
> Dll Help.xml dosyalardan biri Windows PowerShell yükleme dizininde bulunan bir Yardım dosyasını açın tam görünümü için. Örneğin, Microsoft.PowerShell.Commands.Management.dll Help.xml dosya içeriği birçok Windows PowerShell cmdlet'lerini içerir.

### <a name="to-add-a-description"></a>Bir açıklama eklemek için

- Daha ayrıntılı cmdlet temel özelliklerini açıklayarak başlayın. Çoğu durumda, cmdlet adı kullanılan terimler açıklanmaktadır ve bir örnek ile bilinmeyen kavramları göstermek. Cmdlet'i bir dosyaya veri ekler, örneğin, bu veri, varolan bir dosyanın sonuna ekler açıklanmaktadır.

- Tüm cmdlet özelliklerini bulmak için parametre listesini gözden geçirin. Birincil işlevi cmdlet'inin açıklayan ve sonra diğer işlevleri ve özellikleri içerir. Örneğin, bir özelliği değiştirmek için cmdlet main işlevi olduğu, ancak cmdlet tüm özelliklerini değiştirebilirsiniz, bunu ayrıntılı bir açıklama varsayalım. Cmdlet parametrelerini bilgi farklı şekillerde irtibat kullanıcılara izin vermek istiyorsanız, onu açıklayın.

- Kullanıcılar belirgin kullandığı ek cmdlet kullanabileceğiniz yollar hakkında bilgi içerir. Örneğin, nesne kullanabilirsiniz, `Get-Host` Windows PowerShell komut penceresinde metnin rengini değiştirmek için cmdlet'i alır.

  Örnek:  " `Get-Acl` Cmdlet'i, bir dosyanın veya kaynağın güvenlik tanımlayıcısı temsil eden nesneleri alır. Kaynak erişim denetim listelerini (ACL'ler) güvenlik tanımlayıcısını içerir. ACL kaynağa erişmek için kullanıcıların ve kullanıcı gruplarının sahip izinleri belirtir."

- Ayrıntılı bir açıklama cmdlet açıklaması gerekir, ancak cmdlet'ini kullanır kavramları açıklamak değildir. Kavram tanımları içinde ek notlar yerleştirin.

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell SDK'sı](../windows-powershell-reference.md)
