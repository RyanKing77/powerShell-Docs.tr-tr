---
title: Çalışma alanları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848149"
---
# <a name="creating-runspaces"></a>Çalışma Alanları Oluşturma

Bir çalışma alanı bir ana bilgisayar uygulaması tarafından çağrılan komutları için işletim ortamıdır. Bu ortam, komutlar ve şu anda mevcut olan verileri şu anda uygulanan herhangi bir dil kısıtlama içerir.

 Uygulamaları barındırmak tüm kullanılabilir çekirdek komutlar içeren Windows PowerShell tarafından sağlanan varsayılan çalışma alanı kullanabilir veya yalnızca bir alt kümesini kullanılabilir komutları içeren özel bir çalışma alanı oluşturun. Özelleştirilmiş bir çalışma alanı oluşturmak için oluşturduğunuz bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) nesne ve, bir çalışma atayın.

## <a name="runspace-tasks"></a>Çalışma alanı görevleri

1. [Bir InitialSessionState oluşturma](./creating-an-initialsessionstate.md)

2. [Kısıtlı bir çalışma alanı oluşturma](./creating-a-constrained-runspace.md)

3. [Birden çok çalışma alanları oluşturma](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Ayrıca bkz:
