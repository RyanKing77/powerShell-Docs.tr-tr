---
title: Özel bir kullanıcı arabirimi oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083051"
---
# <a name="creating-a-custom-user-interface"></a>Özel bir kullanıcı arabirimi oluşturma

Windows PowerShell, soyut sınıflar ve Windows PowerShell altyapısını barındıran özel bir etkileşimli kullanıcı oluşturmanıza izin arabirimleri sağlar. Özel bir kullanıcı Arabirimi oluşturmak için uygulamanız gereken [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) sınıfı. İsteğe bağlı olarak, aynı zamanda uygulayabileceğiniz [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)ve [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) sınıfları ve [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) ve [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) arabirimleri.
