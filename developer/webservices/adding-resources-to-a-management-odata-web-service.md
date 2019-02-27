---
title: Bir yönetim OData Web hizmeti için kaynak ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848471"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Yönetim OData Web Hizmetine Kaynaklar Ekleme

Bu örnek, bir kaynak yönetimi OData şema Tasarımcısı kullanarak mevcut bir yönetim OData web hizmetini eklemek gösterilmiştir. [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) örnek işlem hem de sunucu kaynaklarınızın gösteren bir web hizmeti oluşturur. Bu örnekte, web hizmetine bir sanal makine (VM) kaynak ekleyeceksiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu konu, indirdiğinizi ve yüklediğinizi olduğunu varsayar [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) örnek bölümünde anlatıldığı gibi [Windows PowerShell Web servisi yaratmak](./creating-a-management-odata-web-service.md), ve indirmiş ve yüklü [Yönetim OData şema Tasarımcısı](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). Bu konu, ayrıca Yönetim Odata uç noktasını ayarladığınız bilgisayarda yüklü Hyper-V Windows PowerShell modülünü sahip olduğunuzu varsayar.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>VM bir kaynak olarak Web hizmetine ekleme

İlk adım, şema Tasarımcısı'na mevcut yönetim OData uç noktasından şema aktarmaktır. Aşağıdaki yordam bunun nasıl yapılacağını açıklar.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Var olan bir şema şema Tasarımcısı'na aktarma

1. Management OData şema Tasarımcısı'nı açın.

2. Gelen **dosya** menüsünde **dosya** ; **Yeni** ; **Dosya**. **Yeni dosya** iletişim kutusu görüntülenir.

3. Tıklayın **Yönetimi OData modeline**ve ardından **açık**.

4. Ana penceresinde sağ tıklayın ve **şema dosyası** ; **Alma**. **Açık** iletişim kutusu görüntülenir.

5. Management OData web hizmeti için ayarlandığında klasöre gidin [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) örnek. Betik değiştirmeden uç noktasını ayarlamak için bu örnek ile sağlanan Windows PowerShell Betiği kullandıysanız, bu klasördür **C:\inetpub\wwwroot\Modata**. Schema.MOF seçip tıklayın **açık**.

   Bu noktada, Schema.mof ve Schema.xml dosyalar bir metin düzenleyicisinde açın ve işlem ve hizmet kaynaklarınız için eşlemelerini içermediğine dikkat edin. Schema.mof dosyasını kullanan [Distributed Management Task Force](https://www.dmtf.org/) (DTMF) Yönetilen Nesne (MOF) standart. Schema.xml dosya açıklanan bir XML şeması kullanır [kaynak eşleme şeması](./resource-mapping-schema.md).

   Aşağıdaki yordam, Hyper-V cmdlet'leri için şema modeli içe aktarmayı açıklar.

#### <a name="importing-cmdlets-into-the-schema"></a>Cmdlet'leri içine alma

1. Şema Tasarımcısı penceresinin boş bir alana sağ tıklayın ve **içeri aktarma cmdlet'leri**. **Cmdlet'i İçeri Aktarma Sihirbazı** iletişim kutusu görüntülenir.

2. Emin **yerel bilgisayar** seçilir ve tıklayın **sonraki**.

3. Yüklü olan Windows PowerShell modülleri'nin seçili olduğundan emin olun ve Hyper-V aşağı açılan listeden seçin. Tıklayın **sonraki**. **İleri**’ye tıklayın.

4. İçinde **cmdlet'i isim** listesinden **VM**. **İleri**’ye tıklayın.

5. Bu örnekte, biz yalnızca Get ve Delete komutlarını cmdlet'leri ile bağlayın. Temizle **Oluştur** ve **güncelleştirme** onay kutusunu ve emin olun **alma** ve **Sil** onay kutularını denetlenir. Emin olun `Get-VM` cmdlet'i için seçilen **alma**ve `Remove-VM` cmdlet'i için seçilen **Sil**.

6. Meta veriler VM cmdlet'ler için çıktı türü belirtmediğinden çıktı türü belirtmek için bu cmdlet'i çalıştırmak gerekir. Seçin **sağlama çıktı türü** tıklatıp **cmdlet'ini çalıştırın**. **Cmdlet'ini çalıştırmak** iletişim kutusu görüntülenir. **Çalıştır**’a tıklayın. **CLR türü** kutusu ile doldurulur `VirtualMachine` türü. Tıklayın **Tamam**, ardından **sonraki**.

7. Varsayılan olarak, tüm VirtualMachine nesnenin özelliklerini seçilir. Bu kaynak web hizmetinden istediğinde döndürülen veriler bir parçası olarak istemediğiniz herhangi bir özelliği temizleyebilirsiniz. **İleri**’ye tıklayın.

8. Bir anahtar olarak kullanılacak en az bir özellik seçmeniz gerekir. Seçin **adı** listesi seçeneğine tıklayıp **sonraki**.

9. Sonraki Pencere Yönetimi OData kaynak özelliklerini temel alınan cmdlet'lerin özelliklerine eşlemenizi sağlar. Sihirbaz aynı adlara sahip özellikler varsayılan olarak eşler. Örneğin, `ComputerName` özelliği kaynağı eşlenmiş durumda `ComputerName` cmdlet'lerinin özelliği.  Bu sayede belirtmek `ComputerName` web hizmeti isteğine bir özellik ve belirttiğiniz değerle geçirilir `Get-VM` cmdlet'i. `Id` ve `Name` de varsayılan olarak eşleştirilir.

   10. Tıklayın **sonraki**, ardından **son**.

       VM kaynağı artık şema tasarımcı penceresi açılır. Özellikler ve kaynak ile ilişkilendirilmiş işlemler inceleyebilirsiniz. Ardından, sanal dizine web hizmeti için güncelleştirilmiş şema dosyalarını verecektir.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Şema Tasarımcısı'ndan şema dosyalarını dışarı aktarma

1. Şema Tasarımcısı penceresinin boş bir alana sağ tıklayın ve **şema dosyası** ; **Dışarı**. **Kaydet** iletişim kutusu görüntülenir.

2. MOF dosyası alındığı burada aynı dizine gidin. Dosyanın özgün MOF dosyası (varsayılan olarak Schema.mof) ile aynı ad ve tıklayın **Kaydet**. Varolan dosyanın üzerine yazmak istediğinizi onaylayın.

   Bu açıkça içinde belirtilmese **Kaydet** iletişim kutusunda, bu dosyaları Schema.mof hem Schema.xml değiştirir.

## <a name="next-steps"></a>Sonraki Adımlar

Management OData web hizmetinden yeni VM kaynağa erişim önce açıklandığı gibi Hyper-V Windows PowerShell modülünü erişime izin vermek için RbacConfiguration.xml dosyasını güncelleştirmeniz gerekir [yapılandırma rol tabanlı yetkilendirme](./configuring-role-based-authorization.md), ve web hizmetini yeniden başlatmanız gerekir.