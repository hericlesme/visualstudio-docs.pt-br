---
title: Adicionando extensões a definições de DSL | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e3b8cb28edb6959511a0cfdf157e323d6706e5f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464518"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Adicionando extensões a definições de DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [adicionando extensões a definições de DSL](https://docs.microsoft.com/visualstudio/modeling/adding-extensions-to-dsl-definitions).  
  
Extensão de definição de DSL permite que você crie um pacote de extensões para uma linguagem específica de domínio (DSL). A extensão DSL, que está contida em um Visual Studio Integration VSIX (extensão), pode ser instalada no computador do usuário da mesma maneira como uma DSL. Os recursos adicionais podem ser habilitados e desabilitados em tempo de execução dinamicamente. DSLs não precisam ser explicitamente criado para a extensão e as extensões podem ser projetadas posteriormente ou por terceiros sem alterar a DSL estendida.  
  
 Os recursos adicionais podem incluir o seguinte:  
  
-   Propriedades de elementos de modelo e apresentação  
  
-   Decoradores de formas e conectores  
  
-   Classes, relações, formas e conectores  
  
-   Restrições de validação  
  
-   Guias e itens de caixa de ferramentas  
  
 Um usuário de uma DSL estendido pode criar e salvar um modelo que contém as instâncias dos recursos adicionais, e eles podem ser lidos por outros usuários que tenham instalado a extensão apropriada. Os usuários que não tem instalado a extensão não é possível usar os recursos adicionais, mas eles podem atualizar e salvar um modelo sem perder os recursos adicionais.  
  
 Para código de exemplo e obter mais informações sobre esse recurso, consulte o [visualização do Visual Studio e SDK de modelagem](http://go.microsoft.com/fwlink/?LinkID=186128) site da Web.  
  
## <a name="see-also"></a>Consulte também  
 [Visualização do Visual Studio e SDK de modelagem](http://go.microsoft.com/fwlink/?LinkID=186128)



