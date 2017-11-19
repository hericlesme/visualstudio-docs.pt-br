---
title: "Ler modelos e diagramas em outras edições do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: "20"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: 704c69efa4e0495a1a4aa7545fa6ba100488afe9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Ler modelos e diagramas em outras edições do Visual Studio
Quando você abre um modelo em uma versão do Visual Studio que não dá suporte à criação de modelo, o modelo é aberto no modo somente leitura. Nesse modo, você pode alterar o layout dos diagramas, mas você não pode alterar o modelo.  
  
 Para ver quais versões do Visual Studio oferecem suporte a criação do modelo, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Como obter acesso a um modelo e diagramas  
 Para ler um diagrama de dependência, você deve primeiro usar o Visual Studio para abrir o projeto de modelagem e, em seguida, abra o diagrama dentro dele.  
  
 Por esse motivo, se você quiser ler um diagrama de dependência, deve também ter acesso ao projeto de modelagem no qual ele foi criado. Você pode fazer isso acessando o projeto de [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)], ou por meio de uma cópia dos arquivos de projeto.  
  
> [!NOTE]
>  Isso não se aplica ao código gerados a partir de código de diagramas de classe de mapas e .NET. Os diagramas podem ser exibidos independentemente de um projeto de modelagem.  
  
 Para ler um diagrama de dependência, o conjunto mínimo de arquivos que você precisa é o seguinte:  
  
-   Os dois arquivos para o diagrama que você deseja ler, por exemplo, de diagrama **MyDiagram.classdiagram e MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Diagramas de dependência, você também deve ter o arquivo chamado *MyDiagram***. layerdiagram.suppressions**.  
  
-   Arquivo de projeto de modelagem (**MyModel.modelproj**)  
  
-   O arquivo de modelo de raiz (**ModelDefinition\MyModel.uml**)  
  
-   Os arquivos de pacote para qualquer pacote referenciado no diagrama (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Alterações que você pode fazer no modo somente leitura  
 Se você abrir um modelo e seus diagramas em uma versão do Visual Studio que não dá suporte à criação de modelo, você não pode alterar o modelo. Ou seja, você não pode alterar os elementos e relações que são exibidas nos diagramas ou no Gerenciador de modelos. No entanto, você pode fazer algumas alterações no layout dos diagramas:  
  
-   Reorganize as formas e os conectores no diagrama.  
  
-   Expandir e recolher formas.  
  
 Você pode salvar essas alterações. Se você quiser fazer suas alterações visíveis para outros usuários, você deve, pelo menos, enviar atualizado **.layout** arquivos.  
  
##  <a name="RelatedTopics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)|Um diagrama de camada mostra a estrutura de uma arquitetura existente ou proposta. Quando o código é escrito, possam ser validado automaticamente em relação a um diagrama de camada.|  
  
## <a name="see-also"></a>Consulte também  
 [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)