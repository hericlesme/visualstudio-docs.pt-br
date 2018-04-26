---
title: A propriedade não pode ser excluída porque participa da associação
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 98f95c489758b808ae7a210f7d83332f84571d1f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>A propriedade &lt;nome da propriedade&gt; não pode ser excluída porque participa da associação &lt;nome da associação&gt;

A propriedade selecionada é definida como o **associação de propriedade** para a associação entre classes indicado na mensagem de erro. Propriedades não podem ser excluídas estão participando em uma associação entre classes de dados.

Definir o **propriedade associação** para outra propriedade da classe de dados para habilitar a exclusão bem-sucedida da propriedade desejada.

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Selecione a linha de associação em object relational Designer de Objetos que conecta as classes de dados mencionadas na mensagem de erro.

2. Clique duas vezes na linha para abrir o **Editor de associação** caixa de diálogo.

3. Remova a propriedade do **propriedades de associação**.

4. Tente excluir novamente a propriedade.

## <a name="see-also"></a>Consulte também

- [Mensagens do O/R Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)