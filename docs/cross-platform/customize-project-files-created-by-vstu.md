---
title: Como personalizar os arquivos de projeto criados por VSTU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-unity-tools
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d051210849f33794ace3aba9786bab3c0156fa74
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="customize-project-files-created-by-vstu"></a>Personalizar os arquivos de projeto criados pelo VSTU
As ferramentas do Visual Studio para Unity fornecem um retorno de chamada de estilo Unity durante a geração do arquivo de projeto. Registre com o evento `VisualStudioIntegration.ProjectFileGeneration` para modificar o arquivo de projeto sempre que ele for gerado novamente.

## <a name="demonstrates"></a>Demonstra
 Como personalizar os arquivos de projeto do Visual Studio gerados pelas Ferramentas do Visual Studio para Unity.

## <a name="example"></a>Exemplo

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
```

## <a name="see-also"></a>Consulte também
 [Exemplo: retorno de chamada de log](../cross-platform/share-the-unity-log-callback-with-vstu.md)
