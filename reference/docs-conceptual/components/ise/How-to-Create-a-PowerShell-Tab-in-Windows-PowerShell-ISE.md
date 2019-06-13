---
ms.date: 06/05/2017
keywords: PowerShell cmdlet'i
title: Windows PowerShell ISE’de bir PowerShell Sekmesi Oluşturma
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030595"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Windows PowerShell ISE’de bir PowerShell Sekmesi Oluşturma

Sekmeler, Windows PowerShell Tümleşik komut dosyası ortamı (ISE) aynı anda oluşturmak ve aynı uygulama içinde birden çok yürütme ortamları kullanma olanak sağlar.
Her bir PowerShell sekmesi, bir ayrı yürütme ortamı veya oturumu karşılık gelir.

> [!NOTE]
> Değişkenler, İşlevler ve bir sekmede oluşturma diğer adları diğerine taşınmaz. Farklı Windows PowerShell oturumları değildirler.

Windows PowerShell'de bir sekmesini kapatın veya aşağıdaki adımları kullanın.
Bir sekme yeniden adlandırmak için ayarlanmış [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) özelliği Windows PowerShell sekme betik oluşturma nesne.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Yeni bir PowerShell sekmesi oluşturma ve

Üzerinde **dosya** menüsünü tıklatın **yeni bir PowerShell sekmesi**. Yeni bir PowerShell sekmesi, her zaman etkin pencere açılır.
PowerShell sekme, bunlar açık olan dosyalardaki sırayla artımlı olarak numaralandırılır.
Her sekme, kendi Windows PowerShell konsol penceresi ile ilişkilidir.
32 adede kadar PowerShell sekmelerle kendi oturumu açma (8, Windows PowerShell ISE 2.0 üzerinde sınırlı budur.) bir zaman olabilir.

Sonuçlandığını unutmayın **yeni** veya **açık** araç çubuğundaki simgeler ayrı bir oturum ile yeni bir sekme oluşturmaz.
Bunun yerine, bu düğmeler şu anda etkin sekmede bir yeni veya mevcut bir komut dosyası ile bir oturumu açın.
Birden çok betik dosyaları her bir sekme ve oturum açma olabilir.
İlişkili oturum etkin olduğunda bir oturum için betik sekmeleri yalnızca oturumu sekmeleri görüntülenir.

Bir PowerShell sekmesi etkin hale getirmek için sekmesinde tıklayın. Açık olan tüm PowerShell sekmeler aralarından seçim yapabileceğiniz **görünümü** menüsünde, kullanmak istediğiniz PowerShell sekmesine tıklayın.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Oluşturma ve yeni bir uzak PowerShell sekme kullanma

Üzerinde **dosya** menüsünde tıklatın **yeni uzak PowerShell sekme** uzak bir bilgisayarda oturum oluşturmak için.
Bir iletişim kutusu görünür ve uzak bağlantı kurmak için gerekli ayrıntıları girmenizi ister.
Uzak sekmesinin işlevleri yalnızca yerel bir PowerShell sekmesi gibi ancak uzak bilgisayarda komutlar ve komut dosyaları çalıştırılır.

## <a name="to-close-a-powershell-tab"></a>Bir PowerShell sekmesi kapatmak için

Bir sekme kapatmak için aşağıdaki tekniklerden birini kullanabilirsiniz:

- Kapatmak istediğiniz sekmesine tıklayın.

- Üzerinde **dosya** menüsünde tıklatın **PowerShell sekmeyi Kapat**, ya da Kapat düğmesine tıklayın (**X**) etkin sekmede sekmesini kapatmak için.

Kaydedilmemiş değişiklikleriniz var, dosyaları PowerShell sekmede aç kapatmak, kaydetmek veya atmak istenir.
Bir komut dosyası kaydetme hakkında daha fazla bilgi için bkz. [kaydetmek bir komut dosyasına nasıl](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Ayrıca bkz:

- [Windows PowerShell ISE Tanıtımı](Introducing-the-Windows-PowerShell-ISE.md)
- [Windows PowerShell ISE'de konsol bölmesini kullanma](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
