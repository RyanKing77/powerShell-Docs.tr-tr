---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085163"
---
# <a name="network-switch-management-with-powershell"></a>PowerShell ile Ağ Anahtarı Yönetimi

**Get-NetworkSwitchEthernetPort** cmdlet örnekleri aşağıdaki ek bilgilerle artık döndürür:

- IPADDRESS: bağlantı noktası ile ilişkili IP adresi
- PortMode – bağlantı noktası modu: erişim, yönlendirme veya santral
- Bu bağlantı noktası erişim modunda VLAN kimliği AccessVLAN – ilişkili
- Bu bağlantı noktası santral modunda, kimlikleri VLAN'ların listesini TrunkedVLANList – ilişkili

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Windows PowerShell ile temel ağ anahtarı yönetimi

WMF 5. 0'da, sunulan ağ anahtarı cmdlet'leri Windows Server 2012 R2 logo sertifikalı ağ anahtarları için anahtar ve sanal LAN (VLAN) temel Katman 2 ağ anahtarı bağlantı noktası yapılandırması uygulamanıza imkan sağlar. Microsoft kalır desteklemeye [veri merkezi soyutlama](http://technet.microsoft.com/cloud/dal.aspx) düzeyi (DAL) işleme ve müşterilerimiz ve iş ortakları bu alandaki değer göstermek için. Bu cmdlet'leri kullanarak şunları yapabilirsiniz:

- Genel yapılandırma, aşağıdaki gibi geçin:
    - Kümesi konak adı
    - Set anahtar başlığı
    - Yapılandırma
    - Etkinleştirmek veya devre dışı özelliği

- VLAN yapılandırması:
    - Oluşturma veya VLAN'ı kaldırma
    - Etkinleştirmek veya VLAN devre dışı
    - VLAN listeleme
    - VLAN kolay adı ayarlayın

- Katman 2 bağlantı noktası yapılandırması:
    - Bağlantı noktalarını Listele
    - Etkinleştirmek veya devre dışı bağlantı noktaları
    - Küme bağlantı modları ve özellikleri
    - Ekleme veya VLAN santral veya numaralı bağlantı noktasında ilişkilendirin

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

Daha fazla bilgi Jeffrey Snover'ın WMF 5.0 Önizleme Duyurusu blog gönderisinde bulabilirsiniz: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
