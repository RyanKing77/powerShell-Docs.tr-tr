---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kurulum
title: DSC kaynak yazmaC#
ms.openlocfilehash: 6f2bb4d411237f13e2735c2e5f630b4f40dc6842
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794238"
---
# <a name="authoring-a-dsc-resource-in-c"></a>C dilinde bir DSC kaynağı yazma\#

> Şunun için geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Genellikle, Windows PowerShell Desired State Configuration (DSC) özel bir kaynak bir PowerShell Betiği uygulanır. Ancak, ayrıca bir DSC özel kaynak işlevselliğini cmdlet'leri yazarak uygulayabilirsiniz C#. Cmdlet'lerinin yazılı olarak üzerinde giriş C#, bkz: [yazma bir Windows PowerShell cmdlet'i](/powershell/developer/windows-powershell).

Kaynak uygulama tarafından C# cmdlet'leri MOF şeması oluşturma, klasör yapısını oluşturma, alma ve özel DSC kaynağınızı kullanarak işlemi, aynı açıklandığı [MOFileözelbirDSCkaynağıyazma](authoringResourceMOF.md).

## <a name="writing-a-cmdlet-based-resource"></a>Cmdlet tabanlı bir kaynak yazma
Bu örnekte, biz bir metin dosyası ve içeriği yöneten basit bir kaynak uygular.

### <a name="writing-the-mof-schema"></a>MOF şemasını yazma

MOF kaynak tanımı aşağıda verilmiştir.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a>Visual Studio projesi ayarlama
#### <a name="setting-up-a-cmdlet-project"></a>Bir cmdlet proje ayarlama

1. Visual Studio'yu açın.
1. Oluşturma bir C# proje ve bir ad sağlayın.
1. Seçin **sınıf kitaplığı** kullanılabilir proje şablonları.
1. Tıklayın **Tamam**.
1. Bir bütünleştirilmiş kod başvurusu System.Automation.Management.dll projenize ekleyin.
1. Derleme adı, kaynak adıyla eşleşecek şekilde değiştirin. Bu durumda, derlemeyi adlandırılmalıdır **MSFT_XDemoFile**.

### <a name="writing-the-cmdlet-code"></a>Cmdlet kod yazma

Aşağıdaki C# uygulayan kod **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource** cmdlet'leri.

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a>Kaynak dağıtma

Betik tabanlı bir kaynak için benzer bir dosya yapısı içinde derlenmiş dll dosyasının kaydedilmesi gerekir. Bu kaynak için klasör yapısını verilmiştir.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a>Ayrıca bkz:
#### <a name="concepts"></a>Kavramlar
[MOF ile özel bir DSC kaynağı yazma](authoringResourceMOF.md)
#### <a name="other-resources"></a>Diğer Kaynaklar
[Bir Windows PowerShell cmdlet'i yazma](/powershell/developer/windows-powershell)