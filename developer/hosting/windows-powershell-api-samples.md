---
title: Windows PowerShell API örnekleri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850158"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API’si Örnekleri

Bu bölüm, işlevselliği kısıtlayabilir çalışma alanları oluşturma ve zaman uyumsuz olarak çalışma alanları sağlamak için bir çalışma alanı havuzu kullanarak komutları çalıştırma gösteren örnek kodu içerir. Microsoft Visual Studio, bir konsol uygulaması oluşturun ve ardından kodu bu bölümdeki konular ana uygulamanıza kopyalamak için kullanabilirsiniz.

## <a name="in-this-section"></a>Bu Bölümde

[PowerShell01 örnek](./windows-powershell01-sample.md) Bu örnek nasıl kullanılacağını gösterir. bir [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) işlevselliğinin bir çalışma alanı sınırlamak için nesne. Bu örnek çıktısı çalışma, bir cmdlet'in özel olarak işaretlemek nasıl, ekleme ve kaldırma cmdlet'leri ve sağlayıcıları, dil modunu kısıtlamak nasıl gösterir ve bir ara sunucu komutu ekleme.

[PowerShell02 örnek](./windows-powershell02-sample.md) Bu örnek, bir çalışma alanı havuzunun çalışma alanlarını kullanarak zaman uyumsuz olarak komutlarını çalıştırmak gösterilmektedir. Örnek komutların bir listesini oluşturur ve gerektiğinde Windows PowerShell altyapısı havuzdan bir çalışma alanı açılırken komutları çalıştırır.