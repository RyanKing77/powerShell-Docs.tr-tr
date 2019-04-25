---
title: Bir Windows PowerShell ek bileşenini oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068003"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Windows PowerShell Ek Bileşeni Oluşturma

Bir Windows PowerShell ek bileşenini böylece Kabuk işlevselliğini genişletme Kabuk ile cmdlet'leri ve başka bir Windows PowerShell sağlayıcısını kaydetmek için bir mekanizma sağlar. Bir Windows PowerShell ek bileşenini tüm cmdlet'leri ve sağlayıcıları tek bir derleme kaydedebilirsiniz veya belirli bir liste cmdlet'leri ve sağlayıcıları kaydedebilirsiniz.

Yalnızca diğer işletim sistemlerinde olduğu gibi korumalı bir dizinde ek derlemeler yüklenmesi gerekir. Aksi takdirde, kötü amaçlı kullanıcıların bir bütünleştirilmiş kod güvenli olmayan kod ile değiştirebilirsiniz.

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell ek bileşeni sınıfları

Tüm Windows PowerShell ek bileşenini sınıflar türetilen [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) veya [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) sınıfları.

## <a name="examples"></a>Örnekler

[Bir Windows PowerShell ek bileşenini yazma](./writing-a-windows-powershell-snap-in.md): Bu örnek, bir derlemede tüm cmdlet'leri ve sağlayıcıları kaydetmek için kullanılan bir ek bileşenini oluşturma işlemi gösterilmektedir.

[Bir özel Windows PowerShell ek bileşenini yazma](./writing-a-custom-windows-powershell-snap-in.md): Bu örnek, bir özel cmdlet'lerini ve sağlayıcıları var olmayabilir veya belirli bir dizi tek bir derleme kaydetmek için kullanılan eklentisini oluşturma işlemi gösterilmektedir.

## <a name="see-also"></a>Ayrıca bkz:

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Cmdlet'leri kaydetme](./registering-cmdlets.md)

[Windows PowerShell Kabuk SDK'sı](../windows-powershell-reference.md)
