---
title: Managed Extensibility Framework no Editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4677b10d54a6c591c2f60e4c0b1f2978ad49a0ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework no Editor
O editor é criado usando componentes Managed Extensibility Framework (MEF). Você pode criar seus próprios componentes MEF para estender o editor, e seu código pode consumir também componentes do editor.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Visão geral do Managed Extensibility Framework  
 O MEF é uma biblioteca .NET que permite adicionar e modificar recursos de um aplicativo ou componente que segue o modelo de programação de MEF. Editor do Visual Studio pode fornecer e consumir componentes do MEF.  
  
 O MEF está contido no assembly do .NET Framework versão 4 System.ComponentModel.Composition.dll.  
  
 Para obter mais informações sobre o MEF, consulte [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>As partes do componente e os contêineres de composição  
 Uma parte do componente é uma classe ou um membro de uma classe que pode fazer uma (ou ambas) das seguintes opções:  
  
-   Consumir outro componente  
  
-   Ser consumido por outro componente  
  
 Por exemplo, considere um aplicativo de compra que tem um componente de entrada de ordem que depende de dados de disponibilidade do produto fornecidos por um componente de inventário do depósito. Em termos MEF, a parte de inventário pode *exportar* dados de disponibilidade do produto e o pode de parte de entrada de ordem *importar* os dados. A parte de entrada de ordem e a parte de inventário não precisa saber sobre outros; o *contêiner de composição* (fornecido pelo aplicativo host) é responsável por manter o conjunto de exportações e resolver o exporta e importa.  
  
 O contêiner de composição, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, normalmente é de propriedade de host. O contêiner de composição mantém um *catálogo* componentes exportado.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportando e importando componentes  
 Você pode exportar qualquer funcionalidade, como ele é implementado como uma classe pública ou um membro público de uma classe (propriedade ou método). Você não precisa derivar sua parte do componente de <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Em vez disso, você deve adicionar um <xref:System.ComponentModel.Composition.ExportAttribute> de atributo para a classe ou membro de classe que você deseja exportar. Esse atributo especifica a *contrato* pelo componente que outra parte pode importar sua funcionalidade.  
  
### <a name="the-export-contract"></a>O contrato de exportação  
 O <xref:System.ComponentModel.Composition.ExportAttribute> define a entidade (classe, interface ou estrutura) que está sendo exportada. Normalmente, o atributo de exportação usa um parâmetro que especifica o tipo da exportação.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Por padrão, o <xref:System.ComponentModel.Composition.ExportAttribute> atributo define um contrato que é o tipo de classe de exportação.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 No exemplo, o padrão `[Export]` atributo é equivalente a `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Você também pode exportar uma propriedade ou método, conforme mostrado no exemplo a seguir.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importando uma exportação MEF  
 Quando você deseja consumir uma exportação MEF, você deve saber o contrato (normalmente o tipo) pelo qual ele foi exportado e adicionar um <xref:System.ComponentModel.Composition.ImportAttribute> atributo que tem esse valor. Por padrão, o atributo de importação tem um parâmetro, que é o tipo da classe que ele modifica. As seguintes linhas de importação de código a <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> tipo.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Obtém a funcionalidade de Editor de uma parte do componente MEF  
 Se seu código existente é uma parte do componente MEF, você pode usar metadados MEF para consumir componentes do editor.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Para consumir a funcionalidade do editor de uma parte do componente MEF  
  
1.  Adicione referências para System.Composition.ComponentModel.dll, que está no cache de assembly global (GAC), e os assemblies do editor.  
  
2.  Adicionar o relevantes usando as instruções.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Adicionar o `[Import]` atributo à sua interface de serviço, da seguinte maneira.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Quando você tiver obtido o serviço, você pode usar qualquer um de seus componentes.  
  
5.  Quando você ter compilado seu assembly colocá-la em de... \Common7\IDE\Components\ a pasta de instalação do Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)