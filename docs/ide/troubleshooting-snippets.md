---
title: Solução de problemas de trechos de código
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dea93f5c575afc96af188ab2e92e2ee12b929549
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="troubleshoot-snippets"></a>Solução de problemas de trechos de código

Normalmente, problemas com trechos de código IntelliSense são causados por dois problemas: um arquivo de trecho corrompido ou conteúdo inválido no arquivo de trecho.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Não é possível arrastar o trecho do Explorador de Arquivos para um arquivo de origem do Visual Studio

-   Talvez o XML no arquivo de trecho esteja corrompido. O **Editor XML** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode localizar problemas na estrutura XML.

-   Talvez o arquivo de trecho pode não estar em conformidade com o esquema de trecho. O **Editor XML** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode localizar problemas na estrutura XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>O código tem erros de compilador que não estão realçados

-   Talvez esteja faltando uma referência de projeto. Examine a documentação sobre o trecho. Se a referência não for encontrada no computador, será necessário instalá-la. Inserir um trecho deve adicionar ao projeto quaisquer referências necessárias. Se o trecho estiver sem as informações de referência, isso pode ser relatado ao criador do trecho como um erro.

-   Talvez uma variável esteja indefinida. Variáveis indefinidas em um trecho devem ser realçadas. Caso contrário, isso pode ser relatado ao criador do trecho como um erro.

## <a name="see-also"></a>Consulte também

- [Trechos de código](../ide/code-snippets.md)
