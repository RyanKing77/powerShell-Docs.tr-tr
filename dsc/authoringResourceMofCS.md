---
ms.date: 06/12/2017
keywords: DSC, powershell, yapılandırma, Kur
title: DSC kaynağı C# geliştirme
ms.openlocfilehash: e8d3561f197950137877fc902063e43cbfc258ad
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="authoring-a-dsc-resource-in-c"></a>DSC kaynağı C# geliştirme

> İçin geçerlidir: Windows PowerShell 4.0, Windows PowerShell 5.0

Genellikle, Windows PowerShell istenen durum yapılandırması (DSC) özel bir kaynağı bir PowerShell Betiği uygulanır. Ancak, C# ' ta cmdlet'leri yazarak DSC özel kaynak işlevselliğini de uygulayabilirsiniz. Cmdlet'leri C# dilinde yazma giriş için bkz [bir Windows PowerShell Cmdlet yazma](https://technet.microsoft.com/library/dd878294.aspx).

C# cmdlet'leriyle kaynak uygulama yanı sıra MOF şema oluşturma, klasör yapısını oluşturma, alma ve özel DSC kaynağı kullanma sürecini aynıdır açıklandığı gibi [MOFileözelbirDSCkaynağıyazma](authoringResourceMOF.md).

## <a name="writing-a-cmdlet-based-resource"></a>Cmdlet tabanlı bir kaynak yazma
Bu örnekte, biz bir metin dosyası ve içeriği yöneten basit bir kaynak gerçekleştireceksiniz.

### <a name="writing-the-mof-schema"></a>MOF şema yazma

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
#### <a name="setting-up-a-cmdlet-project"></a>Bir cmdlet projesi ayarlama

1. Visual Studio'yu açın.
1. Bir C# projesi oluşturun ve adını belirtin.
1. Seçin **sınıf kitaplığı** kullanılabilir proje şablonları.
1. Click **Ok**.
1. Bir derleme başvurusu System.Automation.Management.dll projenize ekleyin.
1. Derleme adı kaynak adı ile eşleşmesi için değiştirin. Derleme adlı bu durumda, **MSFT_XDemoFile**.

### <a name="writing-the-cmdlet-code"></a>Cmdlet kod yazma

Aşağıdaki C# kodu uygulayan **Get-TargetResource**, **kümesi TargetResource**, ve **Test TargetResource** cmdlet'leri.

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

Betik tabanlı bir kaynak için benzer bir dosya yapısı içinde derlenmiş dll dosyasını yeniden kaydedilmesi gerekir. Bu kaynak için klasör yapısı verilmiştir.

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
[Özel bir DSC kaynağı MOF ile yazma](authoringResourceMOF.md)
#### <a name="other-resources"></a>Diğer Kaynaklar
[Bir Windows PowerShell Cmdlet yazma](https://msdn.microsoft.com/library/dd878294.aspx)