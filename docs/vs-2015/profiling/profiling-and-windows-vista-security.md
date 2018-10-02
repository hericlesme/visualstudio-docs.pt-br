---
title: Criação de perfil e segurança do Windows Vista | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 736e7a04813a6c56d6cab6d1886171e321d583cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474798"
---
# <a name="profiling-and-windows-vista-security"></a>Criação de perfil e segurança do Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [criação de perfil e segurança do Windows Vista](https://docs.microsoft.com/visualstudio/profiling/profiling-and-windows-vista-security).  
  
Dependendo das configurações de Permissões de Acesso do Usuário do [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] que um administrador de computador disponibilizou, um usuário individual pode ter a permissão de segurança para analisar um processo no computador. Os exemplos a seguir ilustram possíveis diferenças entre os usuários:  
  
-   Alguns usuários podem acessar recursos de criação de perfil avançados quando o administrador tiver configurado o início do driver e do serviço.  
  
-   Os usuários do domínio podem acessar apenas as amostras de criação de perfil.  
  
-   Alguns usuários podem negar acesso à criação de perfil para todos os outros usuários.  
  
 Para obter mais informações, consulte as opções de ADMIN em [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## <a name="cross-session-profiling"></a>Criação de perfil de sessão cruzada  
 *Criação de perfil de sessão cruzada* é a capacidade de analisar um processo que é executado em uma sessão de logon diferente. Por exemplo, a maioria dos serviços executados na sessão 0, os usuários não podem ser executados diretamente na sessão 0. Usando o botão **Anexar ao Processo** na barra de ferramentas do Gerenciador de Desempenho ou a opção /attach da ferramenta de linha de comando VSPerfCmd, você pode analisar a maioria dos processos em sessões de logon diferentes.  
  
 Você pode ver uma lista dos processos que estão disponíveis, definindo as opções de visibilidade de criação de perfil de processo cruzado. Essas opções estão disponíveis na janela **Anexar ao processo** que é exibida quando você clica em **Anexar ao Processo**:  
  
-   **Mostrar processos de todos os usuários**  
  
     Quando essa opção não estiver selecionada, a lista exibe apenas os processos pertencentes ao usuário atual. Quando **Mostrar processos de todos os usuários** é selecionado, a lista exibe os processos de todos os usuários.  
  
-   **Exibir processos em todas as sessões**  
  
     Quando essa opção não está selecionada, a lista exibe os processos na sessão atual. Quando essa opção está selecionada, a lista exibe os processos em todas as sessões.  
  
## <a name="see-also"></a>Consulte também  
 [Visões gerais](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Como anexar a um processo em execução](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)



