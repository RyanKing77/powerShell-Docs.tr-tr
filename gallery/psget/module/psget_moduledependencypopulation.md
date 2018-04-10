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
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="9572a-103">Yayımlama işlemi sırasında modülü bağımlılıkları hazırlığı mantığı</span><span class="sxs-lookup"><span data-stu-id="9572a-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="9572a-104">RequiredModules bir parçası olarak listelenen modülleri bağımlılıklar olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9572a-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="9572a-105">Modülleri, modül taban Belirtilen modül taban değil, NestedModules bir parçası olarak listelenen bağımlılıklar olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9572a-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="9572a-106">Bağımlılıkları aynı hedef Havuzda kullanılabilir, aksi takdirde yayımlama işlemi bir hata neden olur.</span><span class="sxs-lookup"><span data-stu-id="9572a-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="9572a-107">Örneğin: 'SnippetPx' Havuzda kullanılabilir durumda değilse, hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="9572a-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="9572a-108">Bazı modülü bağımlılıklar harici olarak yönetilebilir, bu durumda bunlar modülü bildiriminin PSData bölümündeki ExternalModuleDependencies girişi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9572a-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="9572a-109">Bir bölümünü yukarıdaki hata iletisi</span><span class="sxs-lookup"><span data-stu-id="9572a-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="9572a-110">*Modül yükleme sırasında üzerinde hazırlanmış bağımlılıkları listesi bağımlılıklarını yüklemek için kullanılır.*</span><span class="sxs-lookup"><span data-stu-id="9572a-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="9572a-111">*Lütfen, modülün bağımlılıklarını $env altında kullanılabilir olduğundan emin olun: PSModulePath sırasında sisteminizdeki yayımlama işlemi.*</span><span class="sxs-lookup"><span data-stu-id="9572a-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>