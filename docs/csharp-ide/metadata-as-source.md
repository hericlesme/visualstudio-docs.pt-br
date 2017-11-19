---
title: Metadados como origem | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Go To Definition command
- Code Definition window, viewing metadata as source
- metadata as source [C#]
ms.assetid: 4945a07f-b3be-4f05-a587-fc29058aa8fa
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 118d19a1be813b0488503be86a316ccc82bd7b37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="metadata-as-source"></a>Metadados como origem
Metadados como origem permitem exibir os metadados que aparece como código-fonte c# em um buffer somente leitura. Isso permite que uma exibição das declarações dos tipos e membros (sem implementações). Você pode exibir metadados como origem executando o **ir para definição** comando para tipos ou membros cujo código-fonte não está disponível no seu projeto ou solução.  
  
> [!NOTE]
>  Quando você tenta executar o **ir para definição** comando para tipos ou membros que são marcados como internos, o ambiente de desenvolvimento integrado (IDE) não exibe seus metadados como origem, independentemente se o assembly de referência é um amigo ou não.  
  
 Você pode exibir metadados como origem em um Editor de códigos ou o **definição de código** janela.  
  
## <a name="viewing-metadata-as-source-in-the-code-editor"></a>Exibindo metadados como origem no Editor de códigos  
 Quando você executa o **ir para definição** comando de um item cujo código-fonte não estiver disponível, um documento com guias que contém uma exibição de metadados do item, exibido como fonte, é exibida no Editor de códigos. O nome do tipo, seguido por **[de metadados]**, aparece na guia do documento.  
  
 Por exemplo, se você executar o **ir para definição** comando <xref:System.Console>, metadados para <xref:System.Console> aparece no Editor de código c# código-fonte que se parece com sua declaração, mas sem uma implementação.  
  
 ![Metadados como origem](../csharp-ide/media/metadatasource.png "MetadataSource")  
  
## <a name="viewing-metadata-as-source-in-the-code-definition-window"></a>Exibindo metadados como origem na janela de definição de código  
 Quando o **definição de código** janela está ativa ou visíveis, o IDE executa automaticamente a **ir para definição** comando para itens sob o cursor no Editor de códigos e para os itens selecionados na  **Exibição de classe** ou **Pesquisador de objetos**. Se o código-fonte não está disponível para esse item, o IDE exibe os metadados do item como origem no **definição de código** janela.  
  
 Por exemplo, se você colocar o cursor dentro da palavra <xref:System.Console> no Editor de códigos, metadados para <xref:System.Console> aparece como origem no **definição de código** janela. A fonte é semelhante a <xref:System.Console> declaração, mas sem uma implementação.  
  
 Se você deseja ver a declaração de um item que aparece no **definição de código** janela, clique com o botão direito e clique em **ir para definição**.