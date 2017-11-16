---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, powershell, yapılandırma, Kur"
title: "Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma"
ms.openlocfilehash: 75b494db4ee6e381491decb11d35b60105217a0f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2017
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="32977-103">Özel Windows PowerShell istenen durum yapılandırması kaynakları oluşturma</span><span class="sxs-lookup"><span data-stu-id="32977-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="32977-104">İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="32977-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="32977-105">Windows PowerShell istenen durum yapılandırması (DSC) ortamınızı yapılandırmak için kullanabileceğiniz yerleşik kaynaklara sahip.</span><span class="sxs-lookup"><span data-stu-id="32977-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="32977-106">(Daha fazla bilgi için bkz: [yerleşik Windows PowerShell istenen durum yapılandırması kaynakları](builtInResource.md).) Bu konu, kaynakları ve belirli bilgi ve örnekler ile konulara bağlantılar geliştirmeye genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="32977-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="32977-107">DSC kaynağı bileşenleri</span><span class="sxs-lookup"><span data-stu-id="32977-107">DSC resource components</span></span>

<span data-ttu-id="32977-108">DSC kaynağı bir Windows PowerShell modülüdür.</span><span class="sxs-lookup"><span data-stu-id="32977-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="32977-109">Modül kaynak için (yapılandırılabilir özellikleri tanımı) şema ve uygulama (yapılandırması tarafından belirtilen asıl işi yapan kod) içerir.</span><span class="sxs-lookup"><span data-stu-id="32977-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="32977-110">DSC kaynağı şeması MOF dosyası içinde tanımlanabilir ve uygulama betik modülü tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="32977-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="32977-111">Sürüm 5 PowerShell sınıflarda desteği ile başlayarak, şema ve uygulama hem de bir sınıfta tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="32977-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="32977-112">Aşağıdaki konularda, DSC kaynakları oluşturmak nasıl daha ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32977-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="32977-113">Özel bir DSC kaynağı MOF ile yazma</span><span class="sxs-lookup"><span data-stu-id="32977-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md) 
* [<span data-ttu-id="32977-114">DSC kaynağı C# ' ta uygulama</span><span class="sxs-lookup"><span data-stu-id="32977-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md) 
* [<span data-ttu-id="32977-115">PowerShell sınıfları içeren özel bir DSC kaynağı yazma</span><span class="sxs-lookup"><span data-stu-id="32977-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md) 
* [<span data-ttu-id="32977-116">Bileşik kaynaklar: DSC yapılandırması bir kaynak olarak kullanma</span><span class="sxs-lookup"><span data-stu-id="32977-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md) 
* [<span data-ttu-id="32977-117">Kaynak Tasarımcısı aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="32977-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md) 

