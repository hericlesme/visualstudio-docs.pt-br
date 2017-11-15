---
title: Solucionando problemas de trechos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 80e5ba76a54b584e5eed74f507f1fb3b81e7f89e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-snippets"></a>Solucionando problemas de trechos
Normalmente, problemas com trechos de código IntelliSense são causados por dois problemas: um arquivo de trecho corrompido ou conteúdo inválido no arquivo de trecho.  
  
## <a name="common-problems"></a>Problemas comuns  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>O trecho não pode ser arrastado do Explorador de Arquivos para um arquivo de origem do Visual Studio  
  
-   Talvez o XML no arquivo de trecho esteja corrompido. O **Editor XML** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode localizar problemas na estrutura XML.  
  
-   Talvez o arquivo de trecho pode não estar em conformidade com o esquema de trecho. O **Editor XML** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode localizar problemas na estrutura XML.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>O código tem erros de compilador que não estão realçados  
  
-   Talvez esteja faltando uma referência de projeto. Examine a documentação sobre o trecho. Se a referência não for encontrada no computador, será necessário instalá-la. Inserir um trecho deve adicionar ao projeto quaisquer referências necessárias. Se o trecho estiver sem as informações de referência, isso pode ser relatado ao criador do trecho como um erro.  
  
-   Talvez uma variável esteja indefinida. Variáveis indefinidas em um trecho devem ser realçadas. Caso contrário, isso pode ser relatado ao criador do trecho como um erro.  
  
## <a name="see-also"></a>Consulte também  
 [Trechos de código](../ide/code-snippets.md)