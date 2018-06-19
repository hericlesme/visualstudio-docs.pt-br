---
title: SDK de acesso à Interface de depuração | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 644827f58172b86e774330fddd207ce9ea0ed99b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457440"
---
# <a name="debug-interface-access-sdk"></a>SDK de Acesso à Interface de Depuração
O Microsoft Debug Interface Access Software Development Kit (DIA SDK) fornece acesso para depurar a informações armazenadas em arquivos de banco de dados (. PDB) do programa gerados por ferramentas postcompiler da Microsoft. Porque o formato do arquivo. PDB gerado pelas ferramentas postcompiler sofre revisão constante, expondo o formato é muito prática. Usando a API do DIA, você pode desenvolver aplicativos que pesquisar e procurar informações de depuração armazenadas em um arquivo. PDB. Esses aplicativos podem, por exemplo, relatar informações de retorno de rastreamento de pilha e analisar dados de desempenho.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Fornece uma visão geral do SDK do DIA recursos e especifica onde o DIA SDK está instalado, bem como os arquivos de biblioteca e cabeçalho necessário.  
  
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fornece instruções sobre como usar a API do DIA para consultar o arquivo. PDB.  
  
 [Símbolos e marcações de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Discute como símbolos e marcações de símbolos são usadas na API do DIA.  
  
 [Referência](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contém as interfaces, métodos, enumerações e estruturas da API do DIA.  
  
 [Exemplo de Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Ilustra como usar a API do DIA para pesquisar e procurar informações de depuração.  
  
 [Arquivo de origem Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Usado do código-fonte [exemplo Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) para demonstrar a API do DIA.