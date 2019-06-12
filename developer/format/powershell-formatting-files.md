---
title: Windows PowerShell dosyaları biçimlendirme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830255"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell Biçimlendirme Dosyaları

Windows PowerShell, bazı biçimlendirme dosyaları sağlar (. format.ps1xml) yükleme dizininde bulunur (`$pshome`). Bu dosyaların her biri, .NET nesneleri belirli bir dizi varsayılan görünümünü tanımlar. Bu dosyaları hiçbir zaman değiştirilmelidir. Ancak, bunları bir başvuru olarak kendi özel biçimlendirme dosyaları oluşturmak için kullanabilirsiniz.

`Certificate.Format.ps1xml` X.509 sertifikaları gibi sertifika deposu ve sertifika depolarını nesneleri görüntüsünü tanımlar.

`DotNetTypes.Format.ps1xml` CultureInfo FileVersionInfo ve EventLogEntry nesneleri gibi çeşitli .NET nesneleri görüntüsünü tanımlar.

`FileSystem.Format.ps1xml` Dosya ve dizin nesneleri gibi dosya sistemi nesneleri görüntüsünü tanımlar.

`Help.Format.ps1xml` Tarafından kullanılan farklı görünümleri tanımlar [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet'in ayrıntılı, tam, parametreleri ve örnek görünümleri gibi.

`PowerShellCore.Format.ps1xml` Tarafından döndürülen nesne gibi Windows PowerShell core cmdlet'leri tarafından oluşturulan nesnelerin görünümünü tanımlar [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) ve [Get-geçmiş](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlet'leri.

`PowerShellTrace.Format.ps1xml` İzleme nesneleri tarafından oluşturulan olanlar gibi görüntüsünü tanımlar [izleme komut](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet'i.

`Registry.Format.ps1xml` Görüntü kayıt defteri anahtarı ve giriş nesneleri gibi nesnelerin tanımlar.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell cmdlet'i yazma](../cmdlet/writing-a-windows-powershell-cmdlet.md)
