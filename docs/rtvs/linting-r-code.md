---
title: "Fazendo linting do código R com as Ferramentas do R para Visual Studio | Microsoft Docs"
description: "Como trabalhar com o suporte de lint interno do Visual Studio para R, incluindo opções de lint."
ms.custom: 
ms.date: 01/15/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.text_editor.r.lint
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 34094aee7563c9f0715702ada5bdd7a0df99c4a7
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="linting-r-code-in-visual-studio"></a>Fazendo linting do código R no Visual Studio

O linting é um processo que analisa o código para revelar possíveis erros, problemas de formatação e outros ruídos no código, como espaço em branco falso. O linting também ajuda a incentivar certas convenções de codificação como a maneira pela qual os identificadores são nomeados, o que é muito útil dentro de equipes e de outras situações colaborativas.

As RTVS (Ferramentas do R para Visual Studio) fornecem linting interno para R, cujo comportamento é controlado por meio de várias opções descritas neste artigo. Essas opções são encontradas em **Ferramenta > Opções > Editor de texto > R > Lint**.

O linting está desabilitado por padrão. Para habilitar o linting, defina a opção **Tudo > Habilitar lint** como true.

Quando habilitado, o linting é aplicado no editor enquanto você digita. Os problemas são exibidos como rabiscos verdes. No gráfico a seguir, por exemplo, as RTVS identificaram seis problemas de linting, incluindo o uso de `=` em vez de `<-` para uma atribuição, falta de espaçamento em torno de argumentos da função, uso de identificadores em Pascal e em maiúsculas e uso de um ponto e vírgula. Passar o mouse sobre um problema fornece uma descrição.

![Exemplos de linting para o código R](media/linting-01.png)

Geralmente, você altera as opções de linting dependendo das necessidades de um arquivo ou projeto. Por exemplo, o código de exemplo de um curso online pode usar `=` em vez de `<-`, junto com identificadores de formatação Pascal. Esse código mostraria avisos frequentes de linting, pois as opções padrão de linting sinalizam esses casos. Ao trabalhar com esse código, você pode simplesmente desabilitar as opções em vez de gastar tempo corrigindo cada instância.

## <a name="assignment-group"></a>Grupo de atribuição

| Opção | Valor padrão | Efeito Linting |
| --- | --- | --- |
| Impor \<- | `True` | Identifica quando `<-` não é usado para a atribuição. |

## <a name="naming-group"></a>Grupo de nomenclatura

Essas opções sinalizam identificadores que usam diferentes convenções de nomenclatura:

| Opção | Valor padrão | Efeito Linting |
| --- | --- | --- |
| Sinalizador camelCase | `False` | Sinaliza identificadores que usam camelCase. |
| Nomes de sinalizador longos | `False` | Sinaliza identificadores cujos nomes excedem a configuração "Comprimento máximo do nome". |
| Sinalizar vários pontos | `True` | Sinaliza identificadores que usam vários pontos. |
| Sinalizar PascalCase | `True` | Sinaliza identificadores que usam PascalCase. |
| Sinalizar snake_case | `False` | Sinaliza identificadores que usam sublinhados. |
| Sinalizar MAIÚSCULAS | `True` | Sinaliza identificadores que usam todas maiúsculas. |
| Comprimento máximo do nome | 32 | O comprimento aplicado com a configuração "Nomes de sinalizador longos". |

## <a name="spacing-group"></a>Grupo de espaçamento

Essas opções, definidas como `True` por padrão, controlam o local em que o linter identifica problemas de espaçamento: após nomes de função, em torno de vírgulas, em torno de operadores, posições da chave de abertura e de fechamento, espaço antes (, e espaço interno ().

## <a name="statements-group"></a>Grupo de instruções

| Opção | Valor padrão | Efeito Linting |
| --- | --- | --- |
| Múltiplo | `True` | Identifica quando várias instruções estão na mesma linha. |
| Ponto e vírgulas | `True` | Identifica os usos de ponto e vírgula. |

## <a name="text-group"></a>Grupo de texto

| Opção | Valor padrão | Efeito Linting |
| --- | --- | --- |
| Limite de comprimento da linha | `False` | Define se o linter sinaliza linhas maiores que a opção "Comprimento máximo da linha". |
| Comprimento máximo da linha | 80 | Define o comprimento da linha aplicado pela opção "Limite de comprimento da linha". |

## <a name="whitespace-group"></a>Grupo de espaços em branco

Essas opções, definidas como `True` por padrão, controlam o local em que o linter identifica problemas de espaço em branco: uso de tabulações, uso de aspas duplas, linhas vazias à direita e espaço em branco à direita.