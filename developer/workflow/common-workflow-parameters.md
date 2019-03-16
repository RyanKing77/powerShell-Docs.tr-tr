---
title: Ortak iş akışı parametreleri | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054807"
---
# <a name="common-workflow-parameters"></a>Ortak İş Akışı Parametreleri

Oluşturulan bir Windows PowerShell cmdlet'inden bir iş akışı etkinlik parametreleri, ortak bir dizi tüm etkinlikler için tanımlar. Bu parametre bir alt iş akışı yazarları etkinlikleri özelleştirebilmeniz için yazma zamanında belirtilebilir. Bu parametreleri başka bir alt kümesi, etkinlik çağrılırken kullanıcı tarafından belirtilebilir.

Genel iş akışı parametreleri gibi çeşitli kategorilerde gruplanır.

## <a name="connectivity-parameters"></a>Bağlantı parametreleri

|Adı|Tür|Açıklama|Yürütme zaman son kullanıcı tarafından belirtilen?|Yazma sırasında iş akışı yazar tarafından belirtilen?|Örnek oluşturma iş akışı yazar tarafından belirtilen?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|İşleri başlatmak istediğiniz bilgisayar adlarının listesi.|Evet|Evet|Evet|
|PSCredential|[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Kullanılacak kimlik doğrulaması kimlik bilgisini PSComputerName parametresi tarafından belirtilen bilgisayara oturum açmak için. Bu parametre yalnızca PSComputerName belirtilmezse geçerli değil.|Evet|Evet|Evet|
|PSPort|UInt32|İş akışını çalıştırmak için kullanılacak bağlantı noktası.|Evet|Evet|Evet|
|PSUseSSL|Boolean|İş akışını çalıştırmak için uzak bilgisayara güvenli bir bağlantı kurmak için Güvenli Yuva Katmanı (SSL) protokolünü kullanır.|Evet|Evet|Evet|
|PSConfigurationName|Dize|İş akışı çalıştırmak için kullanılan oturum yapılandırması.|Evet|Evet|Evet|
|PSApplicationName|Dize|' % S'bağlantı URI'si iş akışı yürütme için uygulama adı kısmı. Yalnızca ConnectionURI parametresi kullanmadığınızda, bu parametreyi kullanın.|Evet|Evet|Evet|
|PSThrottleLimit|UInt32|İş akışı çalıştırma kurulabilecek eş zamanlı bağlantı sayısı.|Evet|TBD|Evet|
|PSConnectionURI|String[]|İş akışı çalıştırmak için kullanılan etkileşimli oturumları için uç noktaları belirtin tam URI dizisi.|Evet|Evet|Evet|
|PSAllowRedirection|Boolean|Bu bağlantının iş akışını çalıştırmak için alternatif bir URI'ye yeniden yönlendirme izin verilip verilmeyeceğini belirtir.|Evet|Evet|Evet|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|İş akışını çalıştırmak için kullanılan oturum için Gelişmiş Seçenekleri.|Evet|Evet|Evet|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Değerini [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) kullanıcının kimlik bilgilerini doğrulamak için kullanılan kimlik doğrulama mekanizması belirten sabit listesi.|Evet|Evet|Evet|
|PSCertificateThumbprint|Dize|Dijital ortak anahtar sertifikası (X509) iş akışı çalıştırma izni olan bir kullanıcı hesabının.|Evet|Evet|Evet|

### <a name="behavior-parameters"></a>Davranış parametreleri