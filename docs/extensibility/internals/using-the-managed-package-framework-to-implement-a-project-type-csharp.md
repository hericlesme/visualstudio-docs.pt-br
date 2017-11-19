---
title: Usando a estrutura de pacote gerenciado para um tipo de projeto (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16e1d301e5a3977f656c52f9c97eb43ee216075f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Usando a estrutura de pacote gerenciado para implementar um tipo de projeto (c#)
Estrutura de pacote gerenciado (MPF) fornece classes c# você pode usar ou herdar para implementar seus próprios tipos de projeto. MPF implementa a muitas das interfaces do que Visual Studio espera um tipo de projeto para fornecer, deixando-o livre para se concentrar em Implementando as particularidades do seu tipo de projeto.  
  
## <a name="using-the-mpf-project-source-code"></a>Usando o código-fonte MPF projeto  
 A estrutura de pacote gerenciado para projetos (MPFProj) fornece classes auxiliares para criar e gerenciar o novo sistema de projeto. Ao contrário de outras classes no MPF, as classes de projeto não são incluídas nos assemblies do fornecido com o Visual Studio. Em vez disso, as classes de projeto são fornecidas como código-fonte em [MPF de projetos 2013](http://mpfproj12.codeplex.com).  
  
 Para adicionar este projeto à solução VSPackage, faça o seguinte:  
  
1.  Baixar os arquivos de MPFProj *MPFProjectDir*.  
  
2.  No *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, altere o seguinte bloco:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Crie um projeto de VSPackage.  
  
2.  Descarregue o projeto VSPackage.  
  
3.  Editar o arquivo. csproj VSPackage adicionando o seguinte bloco antes de outros `<Import>` blocos:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Salvar o projeto.  
  
2.  Feche e reabra a solução VSPackage.  
  
3.  Reabra o projeto VSPackage. Você verá um novo diretório chamado ProjectBase.  
  
4.  Adicione a seguinte referência ao projeto VSPackage:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Compile o projeto.  
  
## <a name="hierarchy-classes"></a>Hierarquia de Classes  
 A tabela a seguir resume as classes no MPFProj que dão suporte a hierarquias de projeto. Para obter mais informações, consulte [hierarquias e seleção](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Classes de manuseio de documentos  
 A tabela a seguir lista as classes no MPF que dão suporte ao processamento de documentos. Para obter mais informações, consulte [abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Configuração e Classes de saída  
 A tabela a seguir lista as classes no MPF que permitem que os tipos de projeto dão suporte a várias configurações, como coleções de saída do projeto, debug e release. Para obter mais informações, consulte [gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md).  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Classes de suporte de automação  
 A tabela a seguir lista as classes que oferecem suporte a automação para que os usuários do seu tipo de projeto podem escrever suplementos no MPF.  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Classes de propriedades  
 A tabela a seguir lista as classes que permitem que os tipos de projeto MPF adicionar propriedades que os usuários podem procurar e modificar em um navegador de propriedade.  
  
|Nome da classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|