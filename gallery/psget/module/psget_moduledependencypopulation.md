---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>Yayımlama işlemi sırasında modülü bağımlılıkları hazırlığı mantığı
1.  RequiredModules bir parçası olarak listelenen modülleri bağımlılıklar olarak kabul edilir.
2.  Modülleri, modül taban Belirtilen modül taban değil, NestedModules bir parçası olarak listelenen bağımlılıklar olarak kabul edilir.

3.  Bağımlılıkları aynı hedef Havuzda kullanılabilir, aksi takdirde yayımlama işlemi bir hata neden olur.
    Örneğin: 'SnippetPx' Havuzda kullanılabilir durumda değilse, hata oluşur.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Bazı modülü bağımlılıklar harici olarak yönetilebilir, bu durumda bunlar modülü bildiriminin PSData bölümündeki ExternalModuleDependencies girişi eklenmelidir.
    Bir bölümünü yukarıdaki hata iletisi
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Modül yükleme sırasında üzerinde hazırlanmış bağımlılıkları listesi bağımlılıklarını yüklemek için kullanılır.*

*Lütfen, modülün bağımlılıklarını $env altında kullanılabilir olduğundan emin olun: PSModulePath sırasında sisteminizdeki yayımlama işlemi.*

