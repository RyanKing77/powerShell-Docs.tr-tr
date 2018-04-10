---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de bir PowerShell Sekmesi Oluşturma
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Windows PowerShell ISE’de bir PowerShell Sekmesi Oluşturma

Sekmeleri içinde Windows PowerShell Tümleşik komut dosyası ortamı (ISE), aynı anda oluşturmak ve aynı uygulama içinde birden fazla yürütme ortamlarında kullanmak izin verir.
Her PowerShell sekmesinde ayrı yürütme ortamı ya da oturum karşılık gelir.

> **NOT**:
>
> Değişkenler, İşlevler ve bir sekmede oluşturduğunuz diğer adlar diğerine taşınmaz. Farklı Windows PowerShell oturumlarınızı oldukları.

Açmak veya Windows PowerShell'de sekmesini kapatmak için aşağıdaki adımları kullanın.
Sekme yeniden adlandırmak için ayarlanmış [DisplayName](The-PowerShellTab-Object.md#displayname) Windows PowerShell sekme komut dosyası nesnesinde özelliği.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Oluşturma ve yeni bir PowerShell sekmesi kullanma

Üzerinde **dosya** menüsünde tıklatın **yeni PowerShell sekme**. Yeni bir PowerShell sekmesi her zaman etkin pencereyi açar.
PowerShell sekmeleri artımlı olarak açılmış sırayla numaralandırılır.
Her sekme kendi Windows PowerShell konsol penceresi ile ilişkilidir.
Kendi oturumu açma (Bu Windows PowerShell ISE 2.0 üzerinde 8 sınırlıdır.) bir seferde en fazla 32 PowerShell sekmelerle olabilir

Bu tıklatarak Not **yeni** veya **açık** araç çubuğundaki simgelerin yeni bir sekme ayrı bir oturumla oluşturmaz.
Bunun yerine, bu düğmeleri yeni veya var olan komut dosyası şu anda etkin sekmede ile oturum açın.
Birden çok komut dosyalarını her sekmesi ve oturum açma olabilir.
İlişkili oturum etkin olduğunda, bir oturum için komut dosyası sekmeleri yalnızca oturum sekmeler görüntülenir.

Bir PowerShell sekmesi etkin hale getirmek için sekmesini tıklatın. Açık olan tüm PowerShell sekmeleri aralarından seçim yapabileceğiniz **Görünüm** menüsünde, kullanmak istediğiniz PowerShell sekmesini tıklatın.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Oluşturma ve yeni bir uzaktan PowerShell sekmesi kullanma

Üzerinde **dosya** menüsünde tıklatın **yeni uzak PowerShell sekme** uzak bir bilgisayarda oturum oluşturmak için.
Bir iletişim kutusu görünür ve uzak bağlantı kurmak için gerekli ayrıntıları girmenizi ister.
Uzak sekmesinin işlevleri yerel bir PowerShell sekmesi olduğu gibi ancak uzak bilgisayarda komutları ve komut dosyaları çalıştırılır.

## <a name="to-close-a-powershell-tab"></a>PowerShell sekmesini kapatmak için

Bir sekmeyi kapatmak için aşağıdaki tekniklerden herhangi birini kullanabilirsiniz:

- Kapatmak istediğiniz sekmesini tıklatın.

- Üzerinde **dosya** menüsünde tıklatın **PowerShell sekmeyi Kapat**, veya Kapat düğmesini tıklatın (**X**) etkin bir sekmede sekmesini kapatmak için.

Kaydedilmemiş değişiklikleriniz varsa PowerShell sekmesindeki açık dosyalar kapatmak, kaydedin veya bunları atmanız istenir.
Bir komut dosyasını kaydetme hakkında daha fazla bilgi için bkz: [bir komut dosyası kaydetmek için nasıl](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE Tanıtımı](Introducing-the-Windows-PowerShell-ISE.md)
- [Konsol bölmesinde Windows PowerShell ISE kullanma](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)