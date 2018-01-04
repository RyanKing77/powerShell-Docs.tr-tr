---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Durum yapılandırmasına genel bakış karar alıcılar için istenen"
ms.openlocfilehash: 1800acfa9edae4f65e34db380ff719ad4c034921
ms.sourcegitcommit: 60f06a06c2fce63024f3f4cbd7657b1dfe7fcb1a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2018
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Durum yapılandırmasına genel bakış karar alıcılar için istenen

Bu belge PowerShell istenen durum yapılandırması (DSC) kullanarak iş yararlarını açıklar. Teknik Kılavuzu değil.

## <a name="what-is-desired-state-configuration"></a>İstenen durum Yapılandırması nedir?

Windows PowerShell istenen durum yapılandırması (DSC), yerleşik açık standartlar temelinde Windows yapılandırma bir yönetim platformudur. DSC her bir aşamada (geliştirme, test, ön üretim, üretim) dağıtım yaşam döngüsünün yanı sıra genişletme sırasında güvenilir ve tutarlı bir şekilde çalışabilmesi için yeterince esnektir. 

DSC merkezleri geçici "[yapılandırmaları](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)".
("Düğümler") belirli özelliklere sahip bilgisayarlardan oluşan bir ortama açıklayan bir kolay okunur belge bir yapılandırmadır. Bu özelliklere belirli bir Windows özelliği etkinleştirilmiş veya SharePoint dağıtma kadar karmaşık olduğundan olmanın olarak kadar basit olabilir. 

DSC de sahip izleme ve raporlama yerleşik olarak bulunur. Bir sistem artık uyumlu değilse, DSC bir uyarı oluştur ve sistem düzeltmek için hareket. 

## <a name="benefits-of-using-desired-state-configuration"></a>İstenen durum yapılandırması kullanmanın yararları

Yapılandırmaları kolayca okuma, depolanan güncelleştirildi ve için tasarlanmıştır. Yapılandırmaları durumu hedef cihazlar, bu durumda yerleştirilecek hakkında yönergeler yazmak yerine olması gerektiğini bildirin. Bu bilgi, benimsemeyi, uygulama ve yapılandırma DSC aracılığıyla koruma daha az maliyetli kılar. 

Yapılandırmaları oluşturma karmaşık dağıtım adımları "tek bir kaynağı gerçekte" tek bir konumda yakalanır anlamına gelir. Bu makinelerin belirli bir kümesinin yinelenen dağıtımları daha az hataya hale getirir. Buna karşılık, hızlı bir döngü karmaşık dağıtımlarda sağlayan dağıtımları daha hızlı ve daha güvenilir yapılıyor.

Yapılandırmaları aracılığıyla paylaşılabilir de [PowerShell Galerisi](https://powershellgallery.com) yaygın senaryolar ve en iyi yöntemler anlamına zaten var olabilecek ihtiyacınız çalışmanın için.


## <a name="desired-state-configuration-and-devops"></a>İstenen durum yapılandırması ve aygıt kullanıcıları

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) kişiler, işlem ve hızlı dağıtım ve son kullanıcılara değeri sunmaya odaklanır odaklanmış yineleme için iç veya dış izin araçları birleşimidir. DSC ile DevOps göz önünde tasarlanmıştır. Tek bir yapılandırmasına sahip bir ortamda tanımlamak geliştiriciler kendi yapılandırma gereksinimlerini kodlamak, kaynak denetimine bu yapılandırmasını denetleyin ve işletim ekipleri kolayca dağıtabilirsiniz kod hataya yatkın üzerinden geçmek zorunda kalmadan anlamına gelir el ile işlemler. 

Bağlantılardır de [verilere](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), hangi kolaylaştırır ops ekiplerin tanımlamak ve geliştirici müdahalesi olmadan ortamları değiştirin. 

## <a name="desired-state-configuration-on--and-off-premises"></a>İstenen durum yapılandırması üzerinde - ve şirket dışı

DSC, şirket içi ve şirket dışı dağıtımlarını yönetmek için kullanılabilir. Şirket içi çözümler için DSC sahip bir [çekme sunucu](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver) makinelerin yönetimini merkezileştirme ve bunların durumunu raporlamak için kullanılabilir. Bulut çözümleri için Windows yerde kullanılabilir, DSC kullanılabilir durumda değil. Ayrıca belirli teklifleri istenen durum yapılandırması gibi yerleşik azure'dan olan [Azure Otomasyonu](https://azure.microsoft.com/en-us/documentation/services/automation/), hangi merkezi hale getirir DSC raporlama. 

## <a name="dsc-and-compatibility"></a>DSC ve uyumluluk

DSC Windows Server 2012 R2'de tanıtılan karşın, Windows Management Framework (WMF) paket aracılığıyla alt düzey işletim sistemleri için kullanılabilir. WMF hakkında daha fazla bilgi bulunabilir [PowerShell giriş sayfası](https://msdn.microsoft.com/en-us/powershell/). 

DSC, Linux yönetmek için de kullanılabilir. Daha fazla bilgi için bkz: [Linux DSC ile çalışmaya başlama](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).

