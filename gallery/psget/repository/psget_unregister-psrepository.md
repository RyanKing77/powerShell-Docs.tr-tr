---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: "Kaydı PSRepository"
ms.openlocfilehash: 91380210f262208fce39d596bd6c2ad05a819fbf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="unregister-psrepository"></a>Kaydı PSRepository

Bir depo kaydını siler.

## <a name="description"></a>Açıklama

Unregister-PSRepository cmdlet'i geçerli kullanıcı için depo kaydını siler.
- Kayıt silme ve yeniden kayda PSGallery depo bir kuruluş için izin verilen ve senaryoları bağlantısı kesildi.
- Kullanıcılar PSGallery yalnızca çalıştırarak yeniden kaydolabilir`Register-PSRepository -Default`
- PSGallery varsayılan olduğundan deposu Yayımla modülü ve Yayımla-komut dosyası cmdlet'leri yayımlama, PSGallery kayıtlı deposu listesinde mevcut olmaması durumunda bir hata oluşturulur.

## <a name="cmdlet-syntax"></a>Cmdlet sözdizimi

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Cmdlet çevrimiçi Yardım başvurusu

[Kaydı PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Örnek komutlar

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>Kayıt silme ve yeniden kayda PSGallery depo bir kuruluş için izin verilen ve senaryoları bağlantısı kesildi.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

