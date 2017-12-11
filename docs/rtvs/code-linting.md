---
title: "Fazendo linting do código R com as Ferramentas do R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
f1_keywords: vs.toolsoptionspages.text_editor.r.lint
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 3c84424f052f8ba150c47a72048d4782b7c2a8de
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2017
---
# <a name="linting-r-code-in-visual-studio"></a>Fazendo linting do código R no Visual Studio

O linting é um processo que analisa o código para revelar eventuais erros, tais como problemas de formatação e outros ruídos nos arquivos de código (como espaço em branco falso). O linting também ajuda a incentivar certas convenções de codificação como a maneira pela qual os identificadores são nomeados, o que é muito útil dentro de equipes e de outras situações colaborativas.

As RTVS (Ferramentas do R para Visual Studio) fornecem linting interno para R, cujo comportamento é controlado por meio de uma variedade de opções. Essas opções são encontradas em **Ferramenta > Opções > Editor de texto > R > Lint**.

O linting está desabilitado por padrão. Para habilitar o linting, defina a opção **Tudo > Habilitar lint** como true. As seções a seguir neste tópico descrevem todas as outras opções de linting:

Quando habilitado, o linting é aplicado no editor enquanto você digita. Os problemas são exibidos como rabiscos verdes. No gráfico a seguir, por exemplo, as RTVS identificaram seis problemas de linting, incluindo o uso de `=` em vez de `<-` para uma atribuição, falta de espaçamento em torno de argumentos da função, uso de identificadores em Pascal e em maiúsculas e uso de um ponto e vírgula. Passar o mouse sobre um problema fornece uma descrição.

![Exemplos de linting para o código R](media/linting-01.png)

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