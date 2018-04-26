---
title: Como definir atributos CLR em um elemento
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ceca2556e269d554d40e025e5edcb91753149622
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
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

     `[` *AttributeName* `(` *ParameterName* `=` *tipo* `)]`

## <a name="see-also"></a>Consulte também

- [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)