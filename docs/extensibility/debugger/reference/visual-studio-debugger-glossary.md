---
title: "Glossário de depurador do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c4b91633c94b899157cef5418be0ac8a4d784f1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-debugger-glossary"></a>Glossário de depurador do Visual Studio
Estes são os termos usados no [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de depuração.  
  
## <a name="terms"></a>Termos  
 ponto de interrupção associado  
 Defina uma abstração para um ponto de interrupção no código. Há uma relação um para um entre um ponto de interrupção associado e uma instrução de ponto de interrupção no fluxo de código. Quando o código descarrega, pontos de interrupção associados podem desassociar.  
  
 causalidade  
 Fornece a capacidade de acompanhar um segmento lógico de execução em vários segmentos físicos, processos e máquinas e para reconstruir a pilha de chamadas desse thread lógico em qualquer ponto no tempo de vida do thread.  
  
 contexto de código  
 Fornece uma abstração de uma posição no código conhecida para o mecanismo de depuração. Para a maioria das arquiteturas de tempo de execução, um contexto de código é um endereço no fluxo de instrução do programa. Para idiomas não tradicionais, em que o código não pode ser representado por instruções, um contexto de código pode ser representado por outros meios.  
  
 caminho de código  
 Representa um ponto de execução no código onde uma ramificação é obtida ou é feita uma chamada de função. Um rastreamento de pilha é essencialmente uma lista de caminhos de código de chamada de função.  
  
 mecanismo de depuração (DE)  
 Um componente que permite a depuração de uma arquitetura de tempo de execução. Um mecanismo de depuração funciona em conjunto com o sistema operacional ou o interpretador e fornece serviços de depuração, como avaliação de expressão, os pontos de interrupção e controle de execução.  
  
 contexto de documento  
 Fornece uma abstração de uma posição em um documento do arquivo de origem conhecida para o mecanismo de depuração. Na maioria dos idiomas, um contexto de documento é uma posição em um arquivo de origem. Para idiomas não tradicionais, para que o arquivo de origem não pode ser texto, um contexto de documento pode ser representado por outros meios. Consulte também *de posição de documento*.  
  
 posição do documento  
 Fornece uma abstração de uma posição em um arquivo de origem conhecida para o IDE. Na maioria dos idiomas, uma posição do documento é uma posição em um arquivo de origem. Para idiomas não tradicionais, uma posição de documento pode ser representada de outras maneiras. Consulte também *contexto de documento*.  
  
 ponto de interrupção de erro  
 Uma abstração para descrever um erro em um ponto de interrupção pendente. Um ponto de interrupção de erro pode descrever um erro no local do ponto de interrupção pendente, a expressão associada com o ponto de interrupção pendente, ou outras informações que impede que o ponto de interrupção pendente de associação para um local de código.  
  
 contexto de avaliação  
 Fornece uma abstração de um contexto de programação para a avaliação da expressão. Normalmente, um contexto de avaliação é um escopo. Ao fazer a avaliação da expressão em um contexto de expressão, o contexto de expressão fornece regras de escopo que correspondem a seu ponto de criação. Por exemplo, um contexto de expressão criado em um quadro de pilha fornecem o contexto para avaliar as variáveis locais, parâmetros de método, membros de classe (se aplicável) e variáveis globais.  
  
 exceção interceptada  
 Uma exceção que é interceptada por um mecanismo de depuração, mesmo se nenhum mecanismo de tratamento de exceção está em vigor no quadro de pilhas atual.  
  
 JustMyCode  
 O conceito de depuração somente o código que pertence a um usuário e ignorando todo o código intermediário, como o código do sistema — mesmo se o código-fonte está disponível para esse código de sistema.  
  
 ponto de interrupção pendente  
 Fornece uma abstração para pontos de interrupção antes, durante e após o código é carregado e a maneira como a virtualização de pontos de interrupção. Um ponto de interrupção:  
  
-   Contém todas as informações necessárias para associar um ponto de interrupção no código em um ou mais programas.  
  
-   Pode associar a vários locais de código em um ou mais programas.  
  
-   Nunca vincular-se ao código.  
  
 Carrega cada código de tempo, todos os pontos de interrupção pendentes em um programa são verificados para ver se eles podem associar. Um ponto de interrupção pendente deve conter todos os pontos de interrupção associados que ela está associada.  
  
 process  
 Um processo Win32 físico. Um processo pode conter vários programas. Consulte também *programa*.  
  
 programa  
 Um único namespace em execução dentro de uma arquitetura de tempo de execução específica. Consulte também *processo*.  
  
 Gerenciador de sessão de depuração (SDM)  
 Gerencia qualquer número de mecanismos de depuração depuração qualquer número de programas em vários processos em qualquer número de máquinas. O nível básico, o SDM é Multiplexador de mecanismos de depuração. Além disso, o SDM fornece uma exibição unificada da sessão de depuração para o IDE.  
  
 registro de ativação  
 Representa o estado de computação em um quadro específico e um nível específico de chamadas de função aninhada.  
  
 thread  
 A noção generalizada de execução de instruções em pilha em execução em pelo menos um programa.  
  
 ponto de interrupção de aviso  
 Uma abstração para descrever um aviso em um ponto de interrupção pendente. Um ponto de interrupção de aviso descreve um motivo por que o ponto de interrupção pendente não tiver ainda associado a um local de código. Isso pode ser que o código ainda não carregada para o local descrito pelo ponto de interrupção pendente, ou por algum outro motivo.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)