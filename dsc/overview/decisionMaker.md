---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: Karar Verenler için İstenen Durum Yapılandırmasına Genel Bakış
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405744"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Karar Verenler için İstenen Durum Yapılandırmasına Genel Bakış

Bu belgede, Windows PowerShell Desired State Configuration (DSC) kullanarak iş avantajları açıklanmaktadır. Bu teknik bir kılavuz değildir.

## <a name="what-is-desired-state-configuration"></a>Nedir Desired State Configuration?

PowerShell Desired State Configuration açık standartları temel alan Windows yerleşik bir yapılandırma yönetim platformudur. DSC (geliştirme, test, üretim öncesi ve üretim) dağıtım yaşam döngüsünün yanı sıra ölçek genişletme sırasında her aşamasında güvenilir ve tutarlı bir şekilde çalışması için yeterince esnektir.

DSC merkezleri etrafında [yapılandırmaları](../configurations/configurations.md).
("Düğüm") belirli özelliklere sahip bilgisayarlardan oluşan bir ortamı tanımlayan bir kolay okunur belgesi bir yapılandırmadır.
Bu özelliklere, belirli bir Windows özelliği etkin veya SharePoint dağıtımı gibi karmaşık sunulmasını sağlarken diğer yandan olarak basit olabilir.

DSC ayrıca sahip izleme ve raporlama yerleşik olarak bulunur.
Bir sistem artık uyumlu değilse, DSC bir uyarı oluşturmalı ve sistem düzeltmek için harekete geçin.

## <a name="benefits-of-using-desired-state-configuration"></a>Desired State Configuration ' ı kullanmanın avantajları

Yapılandırmaları kolayca okuyun, güncelleştirilen ve depolanacak şekilde tasarlanmıştır.
Yapılandırmaları durumu hedef cihazlar durumundaki koymak yönergeleri yazmak yerine olması bildirin.
Bu, benimseme, uygulamak ve aracılığıyla DSC yapılandırması korumak daha az yüke neden olur.

Yapılandırmaları oluşturma, tek bir konumda bir "tek gerçeklik kaynağı" karmaşık dağıtım adımları yakalanan anlamına gelir.
Bu yinelenen dağıtımlar, belirli makineler kümesinden çok daha az hata yapmaya açık hale getirir.
Buna karşılık, karmaşık dağıtımları üzerinde hızlı bir döngü sağlayan dağıtımları daha hızlı ve daha güvenilir yapılıyor.

Yapılandırmaları aracılığıyla paylaşılabilir ayrıca [PowerShell Galerisi](https://powershellgallery.com) yaygın senaryolar ve en iyi anlamına zaten var olabilecek için yapılması gereken çalışmayı.


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration ve DevOps

DSC ile tasarlanmış [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) göz önünde bulundurun, kişileri, süreçleri ve hızlı dağıtım ve yineleme izin araçları birleşimi odaklanmış iç veya dış değeri son kullanıcılara sunmaya.
Geliştiriciler kendi yapılandırma gereksinimleri kodlama, kaynak denetimine bu yapılandırmayı kontrol edin ve işlem ekipleri bir ortam tanımlayabilme tek bir yapılandırma kolayca kod hataya Git gerek kalmadan dağıtabilirsiniz el ile gerçekleştirilen işlemleri.

Yapılandırmalarıdır ayrıca [verilerle](../configurations/configData.md), kolaylaştırır tanımlamak ve geliştirici müdahalesi olmadan ortamları değiştirmek ops için.

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>Şirket içi ve şirket dışı Desired State Configuration
DSC, hem şirket içi hem de kapalı içi dağıtımlarını yönetmek için kullanılabilir.
Şirket içi çözümler için DSC sahip bir [çekme sunucusu](../pull-server/pullServer.md) makinelerin yönetimini merkezileştirme ve bunların durumunu raporlamak için kullanılabilir.
Bulut çözümleri için DSC Windows kullanılabilir her yerde kullanılabilir.
Azure Desired State Configuration ' üzerinde gibi yerleşik belirli teklifleri de vardır [Azure Otomasyonu](https://azure.microsoft.com/en-us/documentation/services/automation/), DSC raporlama merkezileştirir.

## <a name="dsc-and-compatibility"></a>DSC ve uyumluluk

DSC, Windows Server 2012 R2'de kullanılmaya başlanan olsa da, alt düzey işletim sistemleri için Windows Management Framework (WMF) paketi aracılığıyla kullanılabilir.
WMF hakkında daha fazla bilgi bulunabilir [PowerShell giriş sayfası](/powershell/).

DSC, Linux'ı yönetmek için de kullanılabilir. Daha fazla bilgi için [Linux için DSC ile çalışmaya başlama](../getting-started/lnxGettingStarted.md).
