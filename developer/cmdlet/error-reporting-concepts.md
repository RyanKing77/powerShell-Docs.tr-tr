---
title: Hata Raporlama kavramları | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846168"
---
# <a name="error-reporting-concepts"></a>Hata Raporlama Kavramları

Windows PowerShell, hata raporlama için iki mekanizma sağlar: bir mekanizma *hataları sonlandıran* ve başka bir mekanizma *Sonlandırıcı olmayan hatalara*. Cmdlet'lerinizi çalıştıran ana bilgisayar uygulaması uygun bir şekilde tepki verebilir böylece doğru cmdlet'inize hatalarını raporlamak için önemlidir.

Cmdlet'inize çağırmalıdır [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) bir hata oluştuğunda yöntemi yok ya da giriş nesnelerini işlemeye devam etmek cmdlet izin vermemelidir. Cmdlet'inize çağırmalıdır [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) cmdlet giriş nesneleri işleme devam ederken Sonlandırıcı olmayan hatalara bildirmek için yöntemi. Her iki yöntem de konak uygulama hatanın nedenini araştırmak için kullanabileceğiniz bir hata kaydı sağlar.

Bir sonlandırıcı bir hata olup veya Sonlandırıcı olmayan hata belirlemek için aşağıdaki kılavuzları kullanın.

- Bir hata hatası ise, geçerli nesne işlenmeye devam veya başarıyla içeriklerini bağımsız olarak herhangi bir ek giriş nesne işleme cmdlet'inize engeller.

- Geçerli nesne ya da içeriklerini bağımsız olarak herhangi bir ek giriş nesne işleme devam etmek için cmdlet istemiyorsanız bir sonlandırmalı hata hatadır.

- Bir sonlandırma hatası kabul edin veya nesne döndüren bir cmdlet oluşursa veya kabul eder ya da yalnızca bir nesne döndürür bir cmdlet'i gerçekleşirse hatadır.

- Cmdlet'inize geçerli nesne ve tüm ek giriş nesnelerin işleme devam etmek istiyorsanız, bir sonlandırıcı olmayan hata hatadır.

- Belirli giriş nesnesi ya da alt giriş nesnelerinin ilgiliyse bir sonlandırıcı olmayan hata hatadır.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell hata kaydı](./windows-powershell-error-records.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
