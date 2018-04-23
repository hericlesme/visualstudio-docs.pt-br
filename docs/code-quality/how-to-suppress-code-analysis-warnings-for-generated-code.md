---
title: Como suprimir avisos de análise do código para código gerenciado
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29f7bdd3e29f5e45d487377f228ad965ac6e0be6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Como suprimir avisos de análise do código para código gerenciado
Compiladores de código gerenciado geralmente geram código que é adicionado a um projeto para facilitar o desenvolvimento rápido de código. Além disso, os desenvolvedores geralmente usam ferramentas de terceiros para ajudar a desenvolver aplicativos rapidamente. Essas ferramentas também geram código que é adicionado ao projeto.

 Deseja ver as violações de regra da análise de código descobre no código gerado. No entanto, não deseja vê-los se você não pode exibir e manter o código que contém a violação.

 O **Suprimir resultados do código gerado** caixa de seleção na página de propriedades de análise de código de um projeto permite que você selecione se você deseja ver avisos de análise de código do código gerado por uma ferramenta de terceiros.

> [!NOTE]
>  Essa opção suprime erros de análise de código e avisos do código gerado quando os erros e avisos aparecem em formulários e modelos. Você pode exibir e manter o código-fonte para um formulário ou um modelo.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir avisos para código gerenciado em um projeto

1.  Clique com botão direito no projeto no Gerenciador de soluções e, em seguida, clique em **propriedades**.

2.  Clique em **de análise de código**.

3.  Selecione o **Suprimir resultados do código gerado** caixa de seleção.