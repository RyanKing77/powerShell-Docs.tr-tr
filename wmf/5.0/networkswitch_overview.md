---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2b6b81d250c3d745f3ab21ebadb9a657583638b0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="network-switch-management-with-powershell"></a>PowerShell ile Ağ Anahtarı Yönetimi

**Get-NetworkSwitchEthernetPort** cmdlet'i şimdi örnekleri aşağıdaki ek bilgilerle döndürür:

- IPADDRESS – bağlantı noktasıyla ilişkili IP adresi
- PortMode – bağlantı noktası modu: erişim, yönlendirme veya santral
- Bu bağlantı noktası erişim modunda VLAN kimliği AccessVLAN – ilişkili
- Bu bağlantı noktası santral modundaki kimlikleri VLAN'ları, listesini TrunkedVLANList – ilişkili

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Windows PowerShell ile temel ağ anahtarı yönetimi

WMF 5. 0'da, sunulan ağ geçiş cmdlet'leri anahtarı, sanal LAN (VLAN) ve temel Katman 2 ağ anahtarı bağlantı noktası yapılandırmasını Windows Server 2012 R2 logo sertifikalı ağ anahtarlara uygulamak sağlar. Microsoft destek kaydedilmiş kalır [veri merkezi soyutlama](http://technet.microsoft.com/cloud/dal.aspx) düzeyi (DAL) görme ve müşterilerimizin ve iş ortakları bu alan için değer göstermek için. Bu cmdlet'leri kullanarak şunları yapabilirsiniz:

- Genel yapılandırma, gibi anahtarı:
    - Küme ana bilgisayar adı
    - Set anahtar başlığı
    - Yapılandırma Sürdür
    - Etkinleştirmek veya özelliği devre dışı bırakma

- VLAN yapılandırması:
    - Oluşturma veya VLAN kaldırma
    - Etkinleştirmek veya VLAN devre dışı bırakma
    - VLAN listeleme
    - VLAN kolay adını ayarlama

- Katman 2 bağlantı noktası yapılandırması:
    - Bağlantı noktalarını listeleme
    - Etkinleştirmek veya devre dışı bağlantı noktaları
    - Set bağlantı noktası modları ve özellikleri
    - Ekleme veya VLAN santral veya bağlantı noktası erişimi ilişkilendirme

Tüm NetworkSwitch cmdlet'leri için bakarak keşfetmeye başlayın!

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

Daha fazla bilgi Gamze Snover'ın WMF 5.0 Önizleme Duyurusu blog postasına mevcuttur: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>