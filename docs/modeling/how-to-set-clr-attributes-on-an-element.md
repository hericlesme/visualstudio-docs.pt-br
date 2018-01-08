---
title: 'Como: definir atributos CLR em um elemento | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.EditAttributesDialog
helpviewer_keywords: Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: d18a19debb8208c53d23bc5c187e0044a1303f08
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Como definir atributos CLR em um elemento
Atributos personalizados são atributos especiais que podem ser adicionados a diagramas, formas, conectores e elementos de domínio. Você pode adicionar qualquer atributo que herda de `System.Attribute` classe.  
  
### <a name="to-add-a-custom-attribute"></a>Para adicionar um atributo personalizado  
  
1.  No **DSL Explorer**, selecione o elemento ao qual você deseja adicionar um atributo personalizado.  
  
2.  No **propriedades** janela, ao lado de **atributos personalizados** propriedade, clique no botão Procurar (**...** ) ícone.  
  
     O **editar atributos** caixa de diálogo é aberta.  
  
3.  No **nome** coluna, clique em  **\<Adicionar atributo >** e digite o nome do seu atributo. Pressione ENTER.  
  
4.  A linha com o nome do atributo mostra parênteses. Nessa linha, digite um tipo de parâmetro para o atributo (por exemplo, `string`), e pressione ENTER.  
  
5.  No **nome de propriedade** coluna, digite um nome apropriado, por exemplo, `MyString`.  
  
6.  Clique em **OK**.  
  
     O **atributos personalizados** propriedade agora exibe o atributo no seguinte formato:  
  
     `[`*AttributeName* `(` *ParameterName* `=` *tipo*`)]`  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)