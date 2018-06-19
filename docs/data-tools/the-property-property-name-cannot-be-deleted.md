---
title: A propriedade não pode ser excluída.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 80b5e40900cd8912b727270a46ebcf119c324f53
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922861"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>A propriedade \<nome da propriedade > não pode ser excluído

A propriedade \<nome da propriedade > não pode ser excluído porque ele está definido como o **propriedade discriminatória** de herança entre \<nome de classe > e \<nome da classe >

A propriedade selecionada é definida como o **propriedade discriminatória** de herança entre classes indicado na mensagem de erro. Propriedades não podem ser excluídas estão participando na configuração de herança entre classes de dados.

Definir o **propriedade discriminatória** para outra propriedade da classe de dados para habilitar a exclusão bem-sucedida da propriedade desejada.

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Em object relational Designer de Objetos, selecione a linha de herança que conecta as classes de dados mencionadas na mensagem de erro.

2. Definir o **discriminador** propriedade a uma propriedade diferente.

3. Tente excluir novamente a propriedade.

## <a name="see-also"></a>Consulte também

- [Mensagens do O/R Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)