---
title: "A propriedade &lt;nome da propriedade&gt; não pode ser excluída porque participa da associação &lt;nome da associação&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 150d176c105e8368fc97f36a19774824dcb91c3e
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>A propriedade &lt;nome da propriedade&gt; não pode ser excluída porque participa da associação &lt;nome da associação&gt;
A propriedade selecionada é definida como o **associação de propriedade** para a associação entre classes indicado na mensagem de erro. Propriedades não podem ser excluídas estão participando em uma associação entre classes de dados.  
  
 Definir o **propriedade associação** para outra propriedade da classe de dados para habilitar a exclusão bem-sucedida da propriedade desejada.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Selecione a linha de associação em object relational Designer de Objetos que conecta as classes de dados mencionadas na mensagem de erro.  
  
2.  Clique duas vezes na linha para abrir o **Editor de associação** caixa de diálogo.  
  
3.  Remova a propriedade do **propriedades de associação**.  
  
4.  Tente excluir novamente a propriedade.  
  
## <a name="see-also"></a>Consulte também
[Mensagens de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)