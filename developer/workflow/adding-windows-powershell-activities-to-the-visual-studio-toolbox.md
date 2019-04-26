---
title: Windows PowerShell etkinlikler Visual Studio araç kutusuna ekleme | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080484"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Visual Studio Toolbox’a Windows PowerShell Etkinlikleri Ekleme

PowerShell iş akışı Tasarımcısı kullanarak iş akışı yazmadan önce araç kutusundan bir Visual Studio iş akışı konsol uygulaması projesi için önce PowerShell etkinlikleri eklemeniz gerekir. Aşağıdaki yordam etkinlikleri Microsoft.PowerShell.Core.Activities derlemeden Visual Studio araç kutusuna ekleme gösterir.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Windows PowerShell etkinlikler Araç Kutusu'na ekleme

1. Visual Studio'da yeni bir iş akışı konsol uygulaması projesi oluşturun.

2. Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**.

3. Araç kutusu içinde sağ tıklatıp araç kutusunda yeni bir sekme eklemek **Sekme Ekle**ve yeni sekmenin "PowerShell etkinlikleri" gibi bir ad verin.

   Bir sekme ekleme, PowerShell etkinlikler araç kutusundaki başka araçlar ayrı gruplamanıza olanak sağlar.

4. Yeni araç kutusu sekmesine tıklayın **öğelerini Seç...** . **Araç kutusu öğelerini Seç** iletişim kutusu görüntülenir.

5. İçinde **araç kutusu öğelerini Seç** iletişim kutusunda, tıklayın **System.Activities** sekmesi.

6. Tıklayın **Gözat**.

7. %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e klasöre gidin ve Microsoft.PowerShell.Core.Activities.dll çift tıklayın.

8. **Tamam**’a tıklayın. Microsoft.PowerShell.Core.Activities derlemesi tarafından tanımlanan etkinlikler araç kutusundan kullanıma sunulmuştur.

## <a name="see-also"></a>Ayrıca bkz:

[Bir Windows PowerShell iş akışı yazma](./writing-a-windows-powershell-workflow.md)

[Windows PowerShell etkinlikleriyle iş akışı oluşturma](./creating-a-workflow-with-windows-powershell-activities.md)