---
title: Registrar geradores de arquivo único | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9b7d16a9e473028d85540f4447d9981382be0fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132163"
---
# <a name="registering-single-file-generators"></a>Registrar geradores de arquivo único
Para disponibilizar uma ferramenta personalizada no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você deve registrá-lo assim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pode criar uma instância e o associa a um tipo de projeto específico.  
  
### <a name="to-register-a-custom-tool"></a>Para registrar uma ferramenta personalizada  
  
1.  Registrar a DLL de ferramenta personalizada ou no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro local ou no registro do sistema, em HKEY_CLASSES_ROOT.  
  
     Por exemplo, eis aqui as informações de registro para gerenciado MSDataSetGenerator ferramenta personalizada, que vem com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Criar uma chave do registro no desejado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hive em geradores\\*GUID* onde *GUID* é o GUID definido pelo sistema de projeto ou o serviço do idioma específico. O nome da chave se torna o nome programático do sua ferramenta personalizada. A chave de ferramenta personalizada tem os seguintes valores:  
  
    -   (Padrão)  
  
         Opcional. Fornece uma descrição amigável da ferramenta personalizada. Esse parâmetro é opcional, mas recomendada.  
  
    -   CLSID  
  
         Necessário. Especifica o identificador da biblioteca de classes do componente COM que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Necessário. Indica se os tipos de arquivos gerados por essa ferramenta personalizada ficam disponíveis para designers visuais. O valor desse parâmetro deve ser 0 (zero) tipos não disponíveis para designers visuais ou 1 (um) para os tipos disponíveis para designers visuais.  
  
    > [!NOTE]
    >  Você deve registrar a ferramenta personalizada separadamente para cada idioma para o qual você deseja que a ferramenta personalizada esteja disponível.  
  
     Por exemplo, o MSDataSetGenerator registrado uma vez para cada idioma:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementando geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)   
 [Expondo os tipos de Designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Introdução ao objeto BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)