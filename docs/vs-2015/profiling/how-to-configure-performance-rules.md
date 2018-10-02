---
title: Como configurar regras de desempenho | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d44958cc52be8d9a16d7600d74af6f68baa2e552
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475969"
---
# <a name="how-to-configure-performance-rules"></a>Como configurar regras de desempenho
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: configurar regras de desempenho](https://docs.microsoft.com/visualstudio/profiling/how-to-configure-performance-rules).  
  
Os avisos de desempenho das Ferramentas de Criação de Perfil do Visual Studio indicam problemas em um aplicativo analisado que podem causar lentidão na execução do programa. Os avisos também podem indicar que talvez seja necessário alterar os métodos de coleta para coletar dados mais úteis. Os avisos de desempenho são gerados automaticamente em uma sessão de criação de perfil e aparecem na janela **Lista de Erros** quando um arquivo de dados de criação de perfil é aberto no [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Alguns avisos podem não se aplicar aos cenários que você está interessado e alguns avisos podem ser gerados de forma imprecisa. Você pode configurar os avisos de desempenho para mostrar ou ocultar avisos específicos.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Para configurar avisos de desempenho do criador de perfil  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  Expanda **Ferramentas de Desempenho** e, em seguida, clique em **Regras**.  
  
3.  Para habilitar ou desabilitar um aviso, marque ou desmarque a caixa de seleção ao lado da **ID** e do nome do aviso.  
  
4.  Para especificar o nível de aviso de uma regra, clique na célula **Ação** ao lado da regra e, em seguida, clique em nível de aviso.  
  
    -   **Desabilitado** – desabilita a regra (isso é o mesmo que desmarcar a caixa de seleção ao lado da ID da regra).  
  
    -   **Aviso** – exibe a regra como um aviso.  
  
    -   **Erro** – interrompe a execução da criação de perfil e exibe a regra como um erro.  
  
    -   **Informação** – exibe a regra apenas como informação.



