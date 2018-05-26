---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a6366e18b4b6478bfab89475bc6975e6491da9f7
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
---
# <a name="windows-management-framework-wmf-50-rtm-release-notes-overview"></a><span data-ttu-id="8063e-102">Windows Management Framework (WMF) 5.0 RTM sürüm notları genel bakış</span><span class="sxs-lookup"><span data-stu-id="8063e-102">Windows Management Framework (WMF) 5.0 RTM Release Notes Overview</span></span>

<span data-ttu-id="8063e-103">**WMF 5.0 WMF 5.1 tarafından superceeded ' dir. WMF 5.0 kullanıcılarla destek almak için WMF 5.1 sürümüne yükseltmeniz gerekir. Lütfen izleyin [WMF 5.1, yükleme intructions](../5.1/install-configure.md)**</span><span class="sxs-lookup"><span data-stu-id="8063e-103">**WMF 5.0 is superceeded by WMF 5.1. Users with WMF 5.0 must upgrade to WMF 5.1 to receive support. Please follow the [installation intructions of WMF 5.1](../5.1/install-configure.md)**</span></span>

<span data-ttu-id="8063e-104">Windows Management Framework (WMF) 5.0 RTM güncelleştirilmiş işlevsellik WMF 4.0 getirir.</span><span class="sxs-lookup"><span data-stu-id="8063e-104">Windows Management Framework (WMF) 5.0 RTM brings functionality that has been updated from WMF 4.0.</span></span> <span data-ttu-id="8063e-105">WMF 5.0 RTM yalnızca yükleme CD'sinde **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, ve **Windows 7 SP1** ve güncelleştirilmiş sürümleri veya giriş aşağıdaki özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8063e-105">WMF 5.0 RTM is available for installation only on **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, and **Windows 7 SP1** and contains updated versions or introduction of the following features:</span></span>

- <span data-ttu-id="8063e-106">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8063e-106">Windows PowerShell</span></span>
- <span data-ttu-id="8063e-107">Yeterli Yönetim (JEA)</span><span class="sxs-lookup"><span data-stu-id="8063e-107">Just Enough Administration (JEA)</span></span>
- <span data-ttu-id="8063e-108">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="8063e-108">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="8063e-109">Windows PowerShell Tümleşik Komut Dosyası Ortamı (ISE)</span><span class="sxs-lookup"><span data-stu-id="8063e-109">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
- <span data-ttu-id="8063e-110">Windows PowerShell Web Hizmetleri (Yönetim OData IIS uzantısı)</span><span class="sxs-lookup"><span data-stu-id="8063e-110">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="8063e-111">Windows Uzaktan Yönetim (WinRM)</span><span class="sxs-lookup"><span data-stu-id="8063e-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="8063e-112">Windows Yönetim Araçları (WMI)</span><span class="sxs-lookup"><span data-stu-id="8063e-112">Windows Management Instrumentation (WMI)</span></span>

<span data-ttu-id="8063e-113">WMF 5.0 RTM değiştirir [WMF 5.0 üretim Önizleme](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span><span class="sxs-lookup"><span data-stu-id="8063e-113">WMF 5.0 RTM replaces the [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span></span> <span data-ttu-id="8063e-114">WMF 5.0 RTM WMF 5.0 üretim Önizleme kaldırmadan yükleyebilirsiniz, ancak WMF 5.0 RTM yüklemeden önce tüm diğer eski sürümlerini WMF 5.0 önizlemeleri kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8063e-114">You can install WMF 5.0 RTM without uninstalling WMF 5.0 Production Preview, but you must uninstall all other older releases of WMF 5.0 previews before installing the WMF 5.0 RTM.</span></span>

<span data-ttu-id="8063e-115">*Not:* Windows 10 çalıştırıyorsanız, Windows 10 (sürüm 1511) Kasım güncelleştirmeye güncelleştirerek işlevsellik WMF 5.0 RTM içinde kullanılabilir aynı kümesini elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8063e-115">*Note:* If you are running Windows 10, you can get the same set of functionality available in WMF 5.0 RTM by updating to the November update of Windows 10 (Version 1511).</span></span> <span data-ttu-id="8063e-116">Windows 10 sisteminize zaten gerçekleştirmediyseniz Başlat düğmesine basın, sonra ayarları seçin > güncelleştirme ve Güvenlik > Windows Update > Güncelleştirmeleri denetle.</span><span class="sxs-lookup"><span data-stu-id="8063e-116">If you have not already updated your Windows 10 system, select the Start button, then select Settings > Update & security > Windows Update > Check for updates.</span></span>
