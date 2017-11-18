---
title: Exemplo de Dia2dump | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a3166065680c193875c451626846a090e50cbc1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="dia2dump-sample"></a>Exemplo de Dia2dump
O exemplo de Dia2dump é instalado com o Visual Studio e contém a origem dia2dump.cpp. O executável compilado é executado na linha de comando e exibe o conteúdo de um arquivo de banco de dados (. PDB) do programa inteiro.  
  
### <a name="to-install-the-sample"></a>Para instalar o exemplo  
  
1.  Verifique se o sistema atende a todos os requisitos de instalação descritos na página de início de instalação do Visual Studio.  
  
2.  Instalar o Visual Studio e siga todas as instruções de instalação e configuração para os exemplos incluídos.  
  
#### <a name="to-build-the-sample"></a>Para criar o exemplo  
  
1.  Abra o arquivo Dia2dump.sln no Visual Studio. (Se necessário, o Visual Studio primeiro ajudará você atualizar o projeto Dia2dump.)  
  
2.  Nas páginas de propriedades de projeto, no **C/C++** &#124; **Geral** &#124; **Diretórios de inclusão adicionais** propriedade, especifique o `..\DIA SDK\include` directory. Isso garante que o compilador pode encontrar o arquivo dia2.h.  
  
3.  Sobre o **criar** menu, clique em **recompilar solução**.  
  
4.  Feche o Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra um prompt de comando e digite o seguinte:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Origem Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Portar, migrar e atualizar projetos do Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)