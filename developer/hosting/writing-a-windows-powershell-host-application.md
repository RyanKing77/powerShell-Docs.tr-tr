---
title: Bir Windows PowerShell konak uygulama yazma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 2df5a59833fcdd58c6b2afbb4882111592fb3d76
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056439"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="38276-102">Windows PowerShell Konak Uygulaması Yazma</span><span class="sxs-lookup"><span data-stu-id="38276-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="38276-103">Windows PowerShell, uygulamanızda barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38276-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="38276-104">Ana uygulama komutlarını çalıştırın, yerel veya uzak bir bilgisayarda oturum açın ve ya da zaman uyumlu veya zaman uyumsuz olarak uygulamanızın ihtiyaçlarına göre komutları çağırır olduğu çalışma tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38276-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="38276-105">Aşağıdaki konular barındıran bir uygulama oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="38276-105">The following topics explain how to create an application that hosts</span></span>

## <a name="in-this-section"></a><span data-ttu-id="38276-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="38276-106">In This Section</span></span>

<span data-ttu-id="38276-107">[Windows PowerShell konak hızlı](./windows-powershell-host-quickstart.md) yönergeleri sağlar ve kod örnekleri sağlamak için kullanmaya ana bilgisayar uygulamaları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="38276-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="38276-108">[Çalışma alanları oluşturma](./creating-runspaces.md) içinde bir ana bilgisayar uygulaması Windows PowerShell komutunu çalıştırmak için çalışma alanları oluşturma açıklayan konular bir dizi.</span><span class="sxs-lookup"><span data-stu-id="38276-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="38276-109">[Ekleme ve bunları çağırırken komutları](./adding-and-invoking-commands.md) oluşturun ve ana bilgisayar uygulamanızda komutunu çalıştırmasını açıklanmaktadır...</span><span class="sxs-lookup"><span data-stu-id="38276-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="38276-110">[Uzak çalışma alanları oluşturma](./creating-remote-runspaces.md) bir çalışma alanı bir uzak bilgisayara bağlanmak kullanılan nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38276-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="38276-111">[Özel bir kullanıcı arabirimi oluşturma](./creating-a-custom-user-interface.md) Introduces özel kullanıcı arabirimleri ve örnekler için bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="38276-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="38276-112">[Ana bilgisayar uygulaması örnekleri](./host-application-samples.md) Bu bölüm, tam konak uygulama örneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="38276-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="38276-113">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="38276-113">See Also</span></span>

[<span data-ttu-id="38276-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="38276-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)