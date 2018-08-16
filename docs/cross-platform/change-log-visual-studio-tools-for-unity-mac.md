---
title: Log de alterações (Ferramentas do Visual Studio para Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: f2bea6bca74fa3c97e6501a44f7d9ea950369d6c
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639719"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Log de alterações (Ferramentas do Visual Studio para Unity, Mac)
Log de alterações de Ferramentas do Visual Studio para Unity.

## <a name="1602"></a>1.6.0.2
 Lançado em 24 de julho de 2018

### <a name="bug-fixes"></a>Correções de bug

-   **Integração:**

     -   Solução alternativa de reversão para um bug de desempenho do Unity (como o Unity corrigiu esse problema).
     
## <a name="1601"></a>1.6.0.1
 Lançado em 10 de julho de 2018

### <a name="bug-fixes"></a>Correções de bug

-   **Integração:**

     -   Suporte à coloração de código de Sombreador corrigido.
     
## <a name="1600"></a>1.6.0.0
 Lançado em 26 de junho de 2018

### <a name="bug-fixes"></a>Correções de bug

-   **Assistentes:**

    -   Erro de digitação corrigido com a mensagem OnApplicationFocus.

-   **Geração do Projeto:**

     -   Solução alternativa temporária para um bug de desempenho do Unity: armazenar em cache MonoIslands ao gerar projetos.
     
     -   Não converta mais um pdb portátil para mdb ao usar o novo tempo de execução do Unity.
     
## <a name="1502"></a>1.5.0.2
 Lançado em 18 de abril de 2018
 
### <a name="new-features"></a>Novos recursos

-   **Integração:**

    -   Adicionado suporte para a conclusão de código básico do Sombreador.
    
    -   Adicionado suporte para ativar/desativar comentários em arquivos do Sombreador.

## <a name="1501"></a>1.5.0.1
 Lançado em 28 de março de 2018
 
### <a name="new-features"></a>Novos recursos

-   **Integração:**

    -   Adicionado suporte para modelos adicionais no Explorador de Projeto do Unity.

## <a name="1500"></a>1.5.0.0
 Lançado em 21 de março de 2018
 
### <a name="new-features"></a>Novos recursos

-   **Integração:**

    -   Adicionado suporte para detectar e anexar a players Android conectados por USB.

## <a name="1403"></a>1.4.0.3
 Lançado em 5 de março de 2018
 
### <a name="new-features"></a>Novos recursos

-   **Geração do Projeto:**

    -   Adicionado o suporte para o gerador de projeto novo no Unity 2018.1.

-   **Integração:**

    -   Adicionado painel de opções para configurações dedicadas.

## <a name="1402"></a>1.4.0.2
 Lançado em 24 de janeiro de 2018
 
### <a name="bug-fixes"></a>Correções de bug

-   **Geração do Projeto:**

    -   Correção da detecção de versão Mono.

-   **Integração:**

    -   Correção dos problemas de timing com 2018.1 e ativação de plug-in.

    -   Corrigidas as notificações ao detectar um novo player.

## <a name="1401"></a>1.4.0.1
 Lançado em 23 de janeiro de 2018
 
### <a name="bug-fixes"></a>Correções de bug

-   **Integração:**

    -   Corrigida a funcionalidade de Expandir/Recolher pastas ao clicar duas vezes

## <a name="1400"></a>1.4.0.0
 Lançado em 13 de dezembro de 2017
 
### <a name="new-features"></a>Novos recursos

-   **Geração do Projeto:**

    -   Suporte adicionado para o .NET Standard.

### <a name="bug-fixes"></a>Correções de bug

-   **Integração:**

    -   Correção de pdb automático para conversão de símbolo de depuração de mdb.

## <a name="1301"></a>1.3.0.1
 Lançado em 12 de dezembro de 2017
 
### <a name="bug-fixes"></a>Correções de bug

-   **Integração:**

    -   Correção de chamada indireta para EditorPrefs.GetBool afetando o inspetor ao tentar alterar o tamanho da matriz.

-   **Assistentes:**

    -   Atualize o contexto do roslyn antes de inserir o método.

## <a name="1300"></a>1.3.0.0
 Lançado em 20 de novembro de 2017
 
### <a name="new-features"></a>Novos recursos

-   **Assistentes:**

    -   Adicionado o assistente "Implementar mensagem do Unity".

    -   Adicionado suporte para nova API de conclusão no VS para Mac 7.4.

## <a name="1200"></a>1.2.0.0
 Lançado em 23 de outubro de 2017
 
### <a name="new-features"></a>Novos recursos

-   **Depurador:**

    -   Suporte adicionado para arquivos de símbolo de depuração portátil.

### <a name="bug-fixes"></a>Correções de bug

-   **Geração do Projeto:**

    -   Correção da extensão .dll extra adicionada por engano ao arquivo do assembly.

    -   Não force o sinalizador AllowAttachedDebuggingOfEditor do Unity, uma vez que o padrão agora é ‘true’.

## <a name="1103"></a>1.1.0.3
 Lançado em 23 de outubro de 2017
 
### <a name="new-features"></a>Novos recursos

-   **Geração do Projeto:**

    -   Suporte adicionado para o perfil do .NET 4.6.

## <a name="1102"></a>1.1.0.2
 Lançado em 8 de agosto de 2017
 
### <a name="new-features"></a>Novos recursos

-   **Depurador:**

    -   Iniciar a caixa de diálogo Anexar ao processo se não souber a qual Unity anexar.

-   **Geração do Projeto:**

    -   Sempre habilite a opção de compilação não segura quando o Unity 5.6 for usado.

## <a name="1101"></a>1.1.0.1
 Lançado em 20 de julho de 2017
 
### <a name="new-features"></a>Novos recursos

-   **Integração:**

    -   Adicionado suporte para recursos localizados.

## <a name="1100"></a>1.1.0.0
 Lançado em 12 de julho de 2017
 
### <a name="new-features"></a>Novos recursos

-   **Integração:**

    -   Adicionado suporte para anexar a players e editores por meio da janela Anexar ao processo.

-   **Geração do Projeto:**

    -   Corrigidas referências de nome de assembly com arquivos mcs.rsp.

    -   Adicionado suporte para unidades de compilação assembly.json.    

    -   Corrigidas definições com níveis de API.    

### <a name="bug-fixes"></a>Correções de bug

-   **Integração:**

    -   Corrigida mensagem de erro do sombreador ao compilar.

## <a name="1001"></a>1.0.0.1
 Lançado em 4 de maio de 2017
 
### <a name="bug-fixes"></a>Correções de bug

-   **Integração:**

    -   Corrigido acompanhamento de documento ativo com projetos regulares e híbridos.

## <a name="1000"></a>1.0.0.0
 Lançado em 3 de maio de 2017
