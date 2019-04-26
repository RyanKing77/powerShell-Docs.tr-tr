---
title: Hata bilgileri görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068292"
---
# <a name="displaying-error-information"></a>Hata Bilgilerini Görüntüleme

Bu konuda, kullanıcılar hata bilgilerini görüntüleyebilir yolları açıklanmaktadır.

Hata bilgilerini sunumunu cmdlet'inize hatayla karşılaştığında, varsayılan olarak, aşağıdaki hata çıktıya benzer olacak.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Ancak, kullanıcıların hataları kategoriye göre ayarlayarak görüntüleyebileceği `$ErrorView` değişkenini `"CategoryView"`. Kategori Görünümü Serbest metin açıklamasını hata yerine hata kaydı belirli bilgileri görüntüler. Bu görünüm, tarama hataların uzun bir listeniz varsa yararlı olabilir. Kategori görünümünde, aşağıdaki gibi önceki hata iletisi görüntülenir.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Hata kategorileri hakkında daha fazla bilgi için bkz. [Windows PowerShell hata kaydı](./windows-powershell-error-records.md).

## <a name="see-also"></a>Ayrıca bkz:

[Windows PowerShell hata kaydı](./windows-powershell-error-records.md)

[Bir Windows PowerShell cmdlet'i yazma](./writing-a-windows-powershell-cmdlet.md)
