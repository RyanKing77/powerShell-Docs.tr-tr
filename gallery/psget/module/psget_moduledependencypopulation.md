---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galeri, powershell, cmdlet, psget
title: psget_moduledependencypopulation
ms.openlocfilehash: c4c9f203e9c526ff532c2388acb6334515d66934
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
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